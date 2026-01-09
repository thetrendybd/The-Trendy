# The-Trendy
Daraz-style hybrid marketplace website 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Trendy - Marketplace</title>

<!-- ===== CSS ===== -->
<style>
body{
    margin:0;
    font-family: Arial, sans-serif;
    background:#f5f5f5;
}

/* ==== HEADER / NAVBAR ==== */
header{
    background:#f85606;
    padding:15px 0;
    color:#fff;
}
header .navbar{
    display:flex;
    justify-content:space-between;
    align-items:center;
    max-width:1200px;
    margin:auto;
}
header .logo{
    font-size:24px;
    font-weight:bold;
}
header .search-bar input{
    padding:6px 10px;
    border-radius:4px 0 0 4px;
    border:none;
    width:200px;
}
header .search-bar button{
    padding:6px 10px;
    border:none;
    background:#fff;
    color:#f85606;
    border-radius:0 4px 4px 0;
    cursor:pointer;
}
header .nav-links button{
    background:none;
    border:none;
    color:#fff;
    margin-left:10px;
    cursor:pointer;
    font-weight:bold;
}

/* ==== CATEGORY MENU ==== */
.category-menu{
    display:flex;
    gap:15px;
    background:#fff;
    padding:10px 20px;
    color:#333;
    flex-wrap:wrap;
}
.category-menu .category:hover{
    cursor:pointer;
    color:#f85606;
    font-weight:bold;
}

/* ==== PRODUCT GRID ==== */
.products{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:10px;
    padding:10px;
    max-width:1200px;
    margin:auto;
}
.product-card{
    border:1px solid #ddd;
    border-radius:6px;
    background:#fff;
    padding:10px;
    position:relative;
}
.product-card h3{
    margin:5px 0;
}
.product-card .price{
    color:#f85606;
    font-weight:bold;
}
.product-images{
    position:relative;
    height:180px;
    overflow:hidden;
}
.product-images img{
    width:100%;
    height:180px;
    object-fit:cover;
    display:none;
    border-radius:6px;
}
.product-images img.active{
    display:block;
}
.product-images .prev,
.product-images .next{
    position:absolute;
    top:50%;
    transform:translateY(-50%);
    background: rgba(0,0,0,0.5);
    color:#fff;
    padding:5px 10px;
    cursor:pointer;
    border-radius:50%;
}
.product-images .prev{left:10px;}
.product-images .next{right:10px;}
.product-images .dots{
    text-align:center;
    position:absolute;
    bottom:8px;
    width:100%;
}
.product-images .dot{
    display:inline-block;
    width:8px;
    height:8px;
    margin:0 3px;
    background:rgba(255,255,255,0.7);
    border-radius:50%;
    cursor:pointer;
}
.product-images .dot.active{
    background:#f85606;
}

/* ==== CART SIDEBAR ==== */
.cart-sidebar{
    position:fixed;
    top:0;
    right:-400px;
    width:350px;
    height:100%;
    background:#fff;
    box-shadow:-3px 0 10px rgba(0,0,0,.2);
    transition:right 0.4s ease;
    padding:20px;
    z-index:999;
    overflow-y:auto;
}
.cart-sidebar.active{
    right:0;
}
.cart-sidebar button{
    margin-top:10px;
}

/* ==== DASHBOARDS ==== */
.dashboard{
    display:grid;
    grid-template-columns:260px 1fr;
    gap:20px;
    max-width:1200px;
    margin:20px auto;
}
.sidebar{
    background:#fff;
    border-radius:8px;
    padding:15px;
    height:fit-content;
}
.main-content{
    background:#fff;
    border-radius:8px;
    padding:20px;
}

/* ==== TABLES ==== */
table{
    width:100%;
    border-collapse:collapse;
}
table th, table td{
    border:1px solid #ddd;
    padding:6px;
    font-size:14px;
}

/* ==== RESPONSIVE ==== */
@media(max-width:1023px){
    .products{grid-template-columns:repeat(1,1fr);}
    .dashboard{grid-template-columns:1fr;}
    .search-bar input{width:120px;}
    .navbar{flex-direction:column; gap:10px;}
}
@media(min-width:1024px){
    .products{grid-template-columns:repeat(5,1fr);}
    .product-images img{height:220px;}
    #cartSection,#checkoutSection{max-width:600px;margin:auto;}
}
</style>
</head>
<body>

<!-- ===== HEADER / NAVBAR ===== -->
<header>
    <div class="navbar container">
        <div class="logo">The Trendy</div>
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Search products...">
            <button onclick="searchProducts()">Search</button>
        </div>
        <div class="nav-links">
            <button onclick="showHome()">Home</button>
            <button onclick="showCategories()">Categories</button>
            <button onclick="openCart()">Cart</button>
            <button onclick="logout()">Logout</button>
        </div>
    </div>
</header>

<!-- ===== CATEGORY MENU ===== -->
<div class="category-menu" id="categoryMenu">
    <div class="category" onclick="filterByCategory('Electronics')">Electronics</div>
    <div class="category" onclick="filterByCategory('Clothes')">Clothes</div>
    <div class="category" onclick="filterByCategory('Shoes')">Shoes</div>
    <div class="category" onclick="filterByCategory('Accessories')">Accessories</div>
    <div class="category" onclick="filterByCategory('Others')">Others</div>
</div>

<!-- ===== PRODUCT LIST ===== -->
<div class="products" id="productList"></div>

<!-- ===== CART SIDEBAR ===== -->
<div id="cartSidebar" class="cart-sidebar">
    <h2>Cart</h2>
    <div id="cartItems"></div>
    <p>Total: <span id="cartTotal">0</span> Tk</p>
    <button onclick="checkout()">Buy Now</button>
    <button onclick="closeCart()">Close</button>
</div>

<!-- ===== DASHBOARD PLACEHOLDER ===== -->
<div id="dashboardContainer"></div>

<!-- ===== SCRIPT ===== -->
<script>
// ===== LOGIN SYSTEM =====
let loggedInUser = JSON.parse(localStorage.getItem('loggedInUser')) || null;
if(!loggedInUser){
    loggedInUser = {email:'admin@trendy.com', password:'admin123', role:'admin', storeName:'The Trendy'};
    localStorage.setItem('users', JSON.stringify([loggedInUser]));
    localStorage.setItem('loggedInUser', JSON.stringify(loggedInUser));
}

// ===== PRODUCTS =====
function saveProduct(name, category, price, stock, desc, images){
    let products = JSON.parse(localStorage.getItem('products')) || [];
    const id = Date.now();
    const storeName = (loggedInUser.role==='admin')?'The Trendy':loggedInUser.storeName;
    products.push({id,name,category,price,stock,desc,images,storeName});
    localStorage.setItem('products',JSON.stringify(products));
    displayProducts();
}
function displayProducts(){
    const container = document.getElementById('productList');
    container.innerHTML='';
    const products = JSON.parse(localStorage.getItem('products')) || [];
    products.forEach(p=>{
        const imgHTML = p.images.map(img=>`<img src="${img}" class="product-image">`).join('');
        container.innerHTML+=`
        <div class="product-card">
            <div class="product-images">${imgHTML}</div>
            <h3>${p.name}</h3>
            <p>${p.category}</p>
            <p class="price">${p.price} Tk</p>
            <p>${p.desc}</p>
        </div>`;
    });
    setupProductSliders();
}

// ===== PRODUCT SLIDER + DOTS =====
function setupProductSliders(){
    const cards = document.querySelectorAll('.product-card');
    cards.forEach(card=>{
        const imgs = card.querySelectorAll('.product-images img');
        if(imgs.length===0) return;
        let current = 0;
        imgs[current].classList.add('active');

        if(imgs.length>1){
            const prev=document.createElement('div');
            prev.className='prev'; prev.innerText='<';
            const next=document.createElement('div');
            next.className='next'; next.innerText='>';
            card.querySelector('.product-images').appendChild(prev);
            card.querySelector('.product-images').appendChild(next);
            prev.onclick=()=>changeSlide(-1);
            next.onclick=()=>changeSlide(1);

            const dotsContainer=document.createElement('div');
            dotsContainer.className='dots';
            card.querySelector('.product-images').appendChild(dotsContainer);

            imgs.forEach((img,idx)=>{
                const dot=document.createElement('span');
                dot.className='dot';
                if(idx===0) dot.classList.add('active');
                dot.onclick=()=>{
                    imgs[current].classList.remove('active');
                    dotsContainer.children[current].classList.remove('active');
                    current=idx;
                    imgs[current].classList.add('active');
                    dotsContainer.children[current].classList.add('active');
                };
                dotsContainer.appendChild(dot);
            });

            function changeSlide(step){
                imgs[current].classList.remove('active');
                dotsContainer.children[current].classList.remove('active');
                current=(current+step+imgs.length)%imgs.length;
                imgs[current].classList.add('active');
                dotsContainer.children[current].classList.add('active');
            }
        }
    });
}

// ===== CART SYSTEM =====
let cart = JSON.parse(localStorage.getItem('cart')) || [];
function openCart(){document.getElementById('cartSidebar').classList.add('active'); updateCartDisplay();}
function closeCart(){document.getElementById('cartSidebar').classList.remove('active');}
function updateCartDisplay(){/* Implement cart display logic */}

// ===== SEARCH / FILTER =====
function searchProducts(){/* Implement search logic */};
function filterByCategory(cat){/* Implement category filter */}

// ===== DASHBOARD PLACEHOLDERS =====
function showHome(){/* Implement homepage logic */};
function showCategories(){/* Implement categories page logic */};
function logout(){alert('Logged out!'); localStorage.removeItem('loggedInUser'); location.reload();}

// ===== INIT =====
displayProducts();
</script>
</body>
</html>
