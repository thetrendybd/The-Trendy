<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Trendy - Online Shop</title>
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  /* Reset */
  * { margin:0; padding:0; box-sizing:border-box; font-family: 'Roboto', sans-serif; }
  body { background-color: #fff; color: #333; }

  /* Header */
  header { display:flex; justify-content: space-between; align-items:center; padding: 15px 30px; background: #f0f8ff; position: sticky; top:0; z-index: 1000; }
  header img { height:50px; }
  .nav-menu { display:flex; gap:15px; }
  .nav-menu a { text-decoration:none; color:#333; font-weight:500; padding:8px 12px; border-radius:4px; transition: 0.3s; }
  .nav-menu a:hover { background-color: #87cefa; color:white; }

  /* Search */
  .search-bar { flex:1; margin:0 20px; display:flex; }
  .search-bar input { width:100%; padding:8px 12px; border-radius:4px 0 0 4px; border:1px solid #ccc; outline:none; }
  .search-bar button { padding:8px 12px; border:none; background:#87cefa; color:white; border-radius:0 4px 4px 0; cursor:pointer; }
  .search-bar button:hover { background:#00bfff; }

  /* Banner */
  .banner { width:100%; margin:20px 0; }
  .banner img { width:100%; border-radius:8px; }

  /* Categories */
  .categories { display:grid; grid-template-columns: repeat(auto-fit,minmax(120px,1fr)); gap:15px; padding: 20px 30px; }
  .category-card { display:flex; flex-direction: column; align-items:center; padding:15px; border:1px solid #ddd; border-radius:8px; transition:0.3s; cursor:pointer; background:#f8f8ff; }
  .category-card:hover { background:#87cefa; color:white; }
  .category-card img { width:50px; height:50px; margin-bottom:10px; }

  /* Products */
  .products { padding:20px 30px; }
  .products h2 { margin-bottom:15px; color:#00bfff; }
  .product-grid { display:grid; grid-template-columns: repeat(auto-fit,minmax(180px,1fr)); gap:15px; }
  .product-card { border:1px solid #ddd; border-radius:8px; padding:10px; text-align:center; transition:0.3s; background:#f8f8ff; }
  .product-card:hover { box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
  .product-card img { width:100%; height:150px; object-fit:cover; border-radius:6px; margin-bottom:10px; }
  .product-card h3 { font-size:16px; margin-bottom:5px; }
  .product-card p { font-size:14px; color:#555; }
  .product-card .price { color:#00bfff; font-weight:700; margin-top:5px; }

  /* Footer */
  footer { background:#f0f8ff; text-align:center; padding:20px 10px; margin-top:30px; }
  footer p { margin-bottom:5px; }
  footer a { text-decoration:none; color:#00bfff; margin:0 5px; }
  footer a:hover { text-decoration:underline; }

  /* Responsive */
  @media(max-width:768px){
    .nav-menu { display:none; }
    .search-bar { margin:0 10px; }
  }
</style>
</head>
<body>

<!-- Header -->
<header>
  <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEge-2F98_7-oylBgR7bcq0eihQAh5MySjhiGGu7lV6-_EcCEHmz7lan0EG8Jhk6H6rm0uG0z45zSnYdRQqWiir77fpHLwlcQzydliYqtcxLsuyvl_LOzGRPi8TmrxUS4cU4VJyHxTzvUT8MfoeYYQkn0Lifn5IEfhN8D0q2MLnp6s8AEdxgcczKUph-LNM6/s500/Modern%20Luxe%20Logo%20for%20'The%20Trendy'_20260104_143746_0000.png" alt="The Trendy Logo">
  
  <div class="search-bar">
    <input type="text" placeholder="Search products...">
    <button>Search</button>
  </div>

  <nav class="nav-menu">
    <a href="#">Mobiles & Tablets</a>
    <a href="#">TVs & Appliances</a>
    <a href="#">Computing</a>
    <a href="#">Fashion</a>
    <a href="#">Health & Beauty</a>
    <a href="#">Groceries & Pets</a>
    <a href="#">Baby & Kids</a>
    <a href="#">Motors</a>
    <a href="#">Sports & Outdoor</a>
    <a href="#">Home & Lifestyle</a>
    <a href="#">Global Collection</a>
  </nav>
</header>

<!-- Banner -->
<section class="banner">
  <img src="https://via.placeholder.com/1200x400.png?text=Your+Banner+Here" alt="Banner">
</section>

<!-- Categories -->
<section class="categories">
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Mobile" alt="Mobiles">
    <span>Mobiles</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=TV" alt="TVs">
    <span>TVs & Appliances</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Computing" alt="Computing">
    <span>Computing</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Fashion" alt="Fashion">
    <span>Fashion</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Health" alt="Health">
    <span>Health & Beauty</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Groceries" alt="Groceries">
    <span>Groceries & Pets</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Kids" alt="Baby & Kids">
    <span>Baby & Kids</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Motors" alt="Motors">
    <span>Motors</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Sports" alt="Sports">
    <span>Sports & Outdoor</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Home" alt="Home">
    <span>Home & Lifestyle</span>
  </div>
  <div class="category-card">
    <img src="https://via.placeholder.com/50.png?text=Global" alt="Global">
    <span>Global Collection</span>
  </div>
</section>

<!-- Products -->
<section class="products">
  <h2>Featured Products</h2>
  <div class="product-grid">
    <!-- Empty products ready to add -->
    <div class="product-card">
      <img src="https://via.placeholder.com/150" alt="Product 1">
      <h3>Product Name</h3>
      <p>Description here</p>
      <div class="price">$0.00</div>
    </div>
    <div class="product-card">
      <img src="https://via.placeholder.com/150" alt="Product 2">
      <h3>Product Name</h3>
      <p>Description here</p>
      <div class="price">$0.00</div>
    </div>
    <div class="product-card">
      <img src="https://via.placeholder.com/150" alt="Product 3">
      <h3>Product Name</h3>
      <p>Description here</p>
      <div class="price">$0.00</div>
    </div>
    <div class="product-card">
      <img src="https://via.placeholder.com/150" alt="Product 4">
      <h3>Product Name</h3>
      <p>Description here</p>
      <div class="price">$0.00</div>
    </div>
  </div>
</section>

<!-- Footer -->
<footer>
  <p>Contact us: +8801XXXXXXXXX</p>
  <p>
    Follow us: 
    <a href="#">Instagram</a> | 
    <a href="#">Facebook</a> | 
    <a href="#">WhatsApp</a>
  </p>
  <p>&copy; 2026 The Trendy. All Rights Reserved.</p>
</footer>

</body>
</html>
