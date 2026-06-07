# shopping.demo
This is my first website
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ShopKart</title>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@700;800&family=Hind:wght@400;500;600&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{--p:#F26522;--pd:#d4541a;--s:#2874F0;--g:#388E3C;--bg:#F1F3F6;--text:#212121;--muted:#717171;--border:#E0E0E0;}
body{font-family:'Hind',sans-serif;background:var(--bg);color:var(--text);}

/* PAGE SYSTEM */
.page{display:none;}
.page.active{display:block;}

/* NAV */
nav{background:#2874F0;padding:0 2rem;display:flex;align-items:center;gap:1.2rem;height:60px;position:sticky;top:0;z-index:100;box-shadow:0 2px 8px rgba(0,0,0,0.2);}
.logo{font-family:'Baloo 2',cursive;font-size:1.6rem;font-weight:800;color:#fff;cursor:pointer;}
.logo span{color:#FFD700;}
.search-bar{flex:1;display:flex;max-width:500px;}
.search-bar input{width:100%;padding:0.5rem 1rem;border:none;font-size:0.9rem;outline:none;border-radius:4px 0 0 4px;}
.search-bar button{background:var(--p);border:none;padding:0 1rem;cursor:pointer;border-radius:0 4px 4px 0;font-size:1rem;color:#fff;}
.nav-btns{display:flex;gap:0.8rem;margin-left:auto;align-items:center;}
.nav-btn{background:rgba(255,255,255,0.15);border:1px solid rgba(255,255,255,0.3);color:#fff;padding:0.4rem 0.9rem;border-radius:4px;cursor:pointer;font-size:0.82rem;font-weight:600;display:flex;align-items:center;gap:0.3rem;white-space:nowrap;}
.nav-btn:hover{background:rgba(255,255,255,0.25);}
.nav-btn .cnt{background:var(--p);border-radius:50%;font-size:0.65rem;padding:1px 5px;margin-left:2px;}

/* CAT BAR */
.cat-bar{background:#fff;border-bottom:1px solid var(--border);padding:0 1rem;display:flex;overflow-x:auto;scrollbar-width:none;}
.cat-bar::-webkit-scrollbar{display:none;}
.cat-item{padding:0.55rem 1rem;font-size:0.82rem;font-weight:600;cursor:pointer;white-space:nowrap;border-bottom:3px solid transparent;display:flex;flex-direction:column;align-items:center;gap:3px;}
.cat-item:hover,.cat-item.active{color:var(--s);border-bottom-color:var(--s);}

/* OFFERS */
.offers{background:var(--p);display:flex;}
.offer{flex:1;padding:0.5rem;text-align:center;color:#fff;font-size:0.78rem;font-weight:600;border-right:1px solid rgba(255,255,255,0.2);}
.offer:last-child{border:none;}

/* HERO */
.hero{background:linear-gradient(135deg,#1a237e,#1565C0);padding:2rem;position:relative;overflow:hidden;}
.hero h1{font-family:'Baloo 2',cursive;font-size:2rem;font-weight:800;color:#fff;}
.hero h1 span{color:#FFD700;}
.hero p{color:rgba(255,255,255,0.8);margin:0.5rem 0 1rem;}
.hero-badges{display:flex;gap:0.7rem;flex-wrap:wrap;margin-bottom:1rem;}
.hbadge{background:rgba(255,255,255,0.15);border:1px solid rgba(255,255,255,0.3);color:#fff;padding:0.3rem 0.8rem;border-radius:20px;font-size:0.78rem;}
.shop-btn{background:var(--p);color:#fff;border:none;padding:0.65rem 1.5rem;border-radius:4px;font-size:0.95rem;font-weight:700;cursor:pointer;}

/* SECTION */
.sec{padding:1.2rem 2rem;}
.sec-hd{display:flex;align-items:center;justify-content:space-between;margin-bottom:0.8rem;}
.sec-hd h2{font-family:'Baloo 2',cursive;font-size:1.3rem;font-weight:700;}
.sec-hd a{color:var(--s);font-size:0.82rem;font-weight:600;text-decoration:none;cursor:pointer;}

/* CAT CARDS */
.cat-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(100px,1fr));gap:0.8rem;}
.cat-card{background:#fff;border-radius:8px;overflow:hidden;cursor:pointer;border:1px solid var(--border);text-align:center;transition:transform 0.2s;}
.cat-card:hover{transform:translateY(-2px);box-shadow:0 4px 12px rgba(0,0,0,0.1);}
.cat-card img{width:100%;height:70px;object-fit:cover;}
.cat-card p{font-size:0.75rem;font-weight:600;padding:0.35rem;}

/* PRODUCT GRID */
.prod-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(185px,1fr));gap:1rem;}
.prod-card{background:#fff;border-radius:8px;overflow:hidden;border:1px solid var(--border);transition:box-shadow 0.2s,transform 0.2s;}
.prod-card:hover{box-shadow:0 4px 16px rgba(0,0,0,0.12);transform:translateY(-2px);}
.prod-img-wrap{position:relative;}
.prod-img{width:100%;aspect-ratio:1;object-fit:cover;display:block;background:#f0f0f0;}
.wl-btn{position:absolute;top:7px;right:7px;background:#fff;border:none;border-radius:50%;width:30px;height:30px;display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:0.95rem;box-shadow:0 1px 4px rgba(0,0,0,0.2);}
.prod-info{padding:0.7rem;}
.prod-brand{font-size:0.75rem;color:var(--muted);margin-bottom:0.15rem;}
.prod-name{font-size:0.85rem;font-weight:600;line-height:1.3;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;}
.rating-row{display:flex;align-items:center;gap:0.3rem;margin-top:0.3rem;}
.rbadge{background:var(--g);color:#fff;font-size:0.7rem;font-weight:700;padding:2px 5px;border-radius:3px;}
.rcnt{font-size:0.72rem;color:var(--muted);}
.price-row{display:flex;align-items:center;gap:0.4rem;flex-wrap:wrap;margin-top:0.3rem;}
.price{font-size:0.95rem;font-weight:700;}
.mrp{font-size:0.78rem;color:var(--muted);text-decoration:line-through;}
.disc{font-size:0.75rem;font-weight:700;color:var(--g);}
.add-btn{width:100%;margin-top:0.5rem;background:var(--p);color:#fff;border:none;padding:0.42rem;border-radius:4px;font-size:0.82rem;font-weight:600;cursor:pointer;}
.add-btn:hover{background:var(--pd);}

/* FILTER BAR */
.filter-bar{display:flex;gap:0.5rem;flex-wrap:wrap;margin-bottom:0.8rem;}
.fbtn{background:#fff;border:1px solid var(--border);padding:0.3rem 0.8rem;border-radius:20px;font-size:0.78rem;font-weight:600;cursor:pointer;}
.fbtn:hover,.fbtn.active{background:var(--s);color:#fff;border-color:var(--s);}

/* BANNER ROW */
.banner-row{display:grid;grid-template-columns:1fr 1fr;gap:1rem;}
.mini-banner{border-radius:8px;padding:1.3rem;display:flex;flex-direction:column;gap:0.4rem;cursor:pointer;}
.mini-banner h3{font-family:'Baloo 2',cursive;font-size:1.1rem;color:#fff;}
.mini-banner p{font-size:0.8rem;color:rgba(255,255,255,0.85);}
.mini-banner .tag{background:rgba(255,255,255,0.25);color:#fff;padding:2px 9px;border-radius:12px;font-size:0.75rem;font-weight:600;width:fit-content;}

/* ===== LOGIN PAGE ===== */
.auth-page{min-height:100vh;background:linear-gradient(135deg,#1a237e,#1565C0);display:flex;align-items:center;justify-content:center;padding:1rem;}
.auth-box{background:#fff;border-radius:12px;padding:2rem;width:100%;max-width:400px;box-shadow:0 8px 32px rgba(0,0,0,0.2);}
.auth-logo{font-family:'Baloo 2',cursive;font-size:1.8rem;font-weight:800;color:#2874F0;text-align:center;margin-bottom:0.3rem;}
.auth-logo span{color:var(--p);}
.auth-tabs{display:flex;margin-bottom:1.5rem;border-bottom:2px solid var(--border);}
.auth-tab{flex:1;padding:0.6rem;text-align:center;font-weight:600;cursor:pointer;font-size:0.9rem;border-bottom:3px solid transparent;margin-bottom:-2px;}
.auth-tab.active{color:var(--s);border-bottom-color:var(--s);}
.auth-form{display:none;}
.auth-form.active{display:block;}
.form-group{margin-bottom:1rem;}
.form-group label{display:block;font-size:0.82rem;font-weight:600;margin-bottom:0.3rem;color:var(--text);}
.form-group input{width:100%;padding:0.6rem 0.9rem;border:1.5px solid var(--border);border-radius:6px;font-size:0.9rem;outline:none;font-family:'Hind',sans-serif;}
.form-group input:focus{border-color:var(--s);}
.auth-submit{width:100%;background:var(--p);color:#fff;border:none;padding:0.7rem;border-radius:6px;font-size:1rem;font-weight:700;cursor:pointer;margin-top:0.5rem;}
.auth-submit:hover{background:var(--pd);}
.auth-divider{text-align:center;color:var(--muted);font-size:0.82rem;margin:1rem 0;position:relative;}
.auth-divider::before{content:'';position:absolute;left:0;top:50%;width:43%;height:1px;background:var(--border);}
.auth-divider::after{content:'';position:absolute;right:0;top:50%;width:43%;height:1px;background:var(--border);}
.social-btns{display:flex;gap:0.8rem;}
.social-btn{flex:1;border:1.5px solid var(--border);background:#fff;padding:0.55rem;border-radius:6px;cursor:pointer;font-size:0.85rem;font-weight:600;display:flex;align-items:center;justify-content:center;gap:0.4rem;}
.social-btn:hover{background:var(--bg);}
.auth-skip{text-align:center;margin-top:1rem;font-size:0.82rem;color:var(--muted);}
.auth-skip a{color:var(--s);cursor:pointer;font-weight:600;}

/* ===== WISHLIST PAGE ===== */
.wl-empty{text-align:center;padding:4rem 1rem;color:var(--muted);}
.wl-empty .big{font-size:4rem;display:block;margin-bottom:1rem;}
.wl-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(185px,1fr));gap:1rem;}

/* ===== CART/CHECKOUT PAGE ===== */
.cart-page-wrap{display:grid;grid-template-columns:1fr 360px;gap:1.5rem;padding:1.5rem 2rem;max-width:1200px;margin:0 auto;}
.cart-items-list{}
.cart-item-row{background:#fff;border-radius:8px;border:1px solid var(--border);padding:1rem;display:flex;gap:1rem;margin-bottom:1rem;align-items:flex-start;}
.cart-item-row img{width:90px;height:90px;object-fit:cover;border-radius:6px;flex-shrink:0;background:#f0f0f0;}
.ci-info{flex:1;}
.ci-name{font-size:0.9rem;font-weight:600;margin-bottom:0.2rem;}
.ci-brand{font-size:0.78rem;color:var(--muted);margin-bottom:0.5rem;}
.ci-price{font-size:1rem;font-weight:700;}
.ci-mrp{font-size:0.8rem;color:var(--muted);text-decoration:line-through;margin-left:0.4rem;}
.ci-disc{font-size:0.78rem;font-weight:700;color:var(--g);margin-left:0.4rem;}
.ci-qty{display:flex;align-items:center;gap:0.6rem;margin-top:0.6rem;}
.qbtn{background:var(--bg);border:1px solid var(--border);width:28px;height:28px;border-radius:4px;cursor:pointer;font-size:1rem;display:flex;align-items:center;justify-content:center;font-weight:700;}
.qnum{font-size:0.9rem;font-weight:700;min-width:22px;text-align:center;}
.ci-remove{background:none;border:none;color:var(--muted);font-size:0.8rem;cursor:pointer;margin-top:0.4rem;display:block;}
.ci-remove:hover{color:#d32f2f;}
/* ORDER SUMMARY */
.order-summary{background:#fff;border-radius:8px;border:1px solid var(--border);padding:1.2rem;position:sticky;top:70px;height:fit-content;}
.order-summary h3{font-family:'Baloo 2',cursive;font-size:1.1rem;font-weight:700;margin-bottom:1rem;padding-bottom:0.8rem;border-bottom:1px solid var(--border);}
.summary-row{display:flex;justify-content:space-between;font-size:0.88rem;margin-bottom:0.6rem;}
.summary-row.total{font-weight:700;font-size:1rem;border-top:1px solid var(--border);padding-top:0.8rem;margin-top:0.8rem;}
.summary-row .green{color:var(--g);font-weight:600;}
.promo-row{display:flex;gap:0.5rem;margin:1rem 0;}
.promo-row input{flex:1;padding:0.5rem 0.8rem;border:1.5px solid var(--border);border-radius:4px;font-size:0.85rem;outline:none;}
.promo-row button{background:var(--s);color:#fff;border:none;padding:0.5rem 0.9rem;border-radius:4px;font-size:0.82rem;font-weight:600;cursor:pointer;}
.place-btn{width:100%;background:var(--p);color:#fff;border:none;padding:0.75rem;border-radius:6px;font-size:1rem;font-weight:700;cursor:pointer;margin-top:0.5rem;}
.place-btn:hover{background:var(--pd);}
.safe-pay{text-align:center;font-size:0.75rem;color:var(--muted);margin-top:0.6rem;}
/* CHECKOUT STEPS */
.checkout-steps{display:flex;align-items:center;justify-content:center;gap:0;padding:1rem 2rem;background:#fff;border-bottom:1px solid var(--border);}
.step{display:flex;align-items:center;gap:0.4rem;font-size:0.82rem;font-weight:600;color:var(--muted);}
.step.active{color:var(--s);}
.step.done{color:var(--g);}
.step-num{width:24px;height:24px;border-radius:50%;border:2px solid currentColor;display:flex;align-items:center;justify-content:center;font-size:0.75rem;font-weight:700;}
.step-line{width:40px;height:2px;background:var(--border);margin:0 0.4rem;}
.step-line.done{background:var(--g);}
/* ADDRESS FORM */
.address-section{background:#fff;border-radius:8px;border:1px solid var(--border);padding:1.2rem;margin-bottom:1rem;}
.address-section h3{font-family:'Baloo 2',cursive;font-size:1rem;font-weight:700;margin-bottom:1rem;}
.form-2col{display:grid;grid-template-columns:1fr 1fr;gap:0.8rem;}
.fg{margin-bottom:0.8rem;}
.fg label{display:block;font-size:0.78rem;font-weight:600;margin-bottom:0.25rem;}
.fg input,.fg select{width:100%;padding:0.5rem 0.8rem;border:1.5px solid var(--border);border-radius:4px;font-size:0.85rem;outline:none;font-family:'Hind',sans-serif;}
.fg input:focus,.fg select:focus{border-color:var(--s);}
.payment-opts{display:flex;flex-direction:column;gap:0.6rem;margin-top:0.5rem;}
.pay-opt{display:flex;align-items:center;gap:0.8rem;padding:0.8rem;border:1.5px solid var(--border);border-radius:6px;cursor:pointer;}
.pay-opt.selected{border-color:var(--s);background:#f0f5ff;}
.pay-opt input[type=radio]{accent-color:var(--s);}
.pay-opt-info{flex:1;}
.pay-opt-title{font-size:0.88rem;font-weight:600;}
.pay-opt-sub{font-size:0.75rem;color:var(--muted);}
/* SUCCESS */
.success-page{text-align:center;padding:3rem 1rem;}
.success-page .big-icon{font-size:5rem;display:block;margin-bottom:1rem;}
.success-page h2{font-family:'Baloo 2',cursive;font-size:1.8rem;color:var(--g);margin-bottom:0.5rem;}
.success-page p{color:var(--muted);margin-bottom:1.5rem;}
.order-id{background:#f0fff4;border:1px solid #c3e6cb;padding:0.8rem 1.5rem;border-radius:6px;font-weight:700;color:var(--g);display:inline-block;margin-bottom:1.5rem;}

/* TOAST */
.toast{position:fixed;bottom:2rem;left:50%;transform:translateX(-50%) translateY(100px);background:#323232;color:#fff;padding:0.65rem 1.3rem;border-radius:4px;font-size:0.88rem;z-index:999;transition:transform 0.3s;white-space:nowrap;}
.toast.show{transform:translateX(-50%) translateY(0);}

/* USER BADGE */
.user-badge{background:rgba(255,255,255,0.2);color:#fff;padding:0.3rem 0.7rem;border-radius:20px;font-size:0.78rem;font-weight:600;}

/* FOOTER */
footer{background:#172337;color:rgba(255,255,255,0.7);padding:1.5rem 2rem;margin-top:2rem;}
.footer-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:1.5rem;margin-bottom:1rem;}
.footer-col h4{color:#fff;font-size:0.82rem;font-weight:700;margin-bottom:0.6rem;text-transform:uppercase;}
.footer-col a{display:block;font-size:0.78rem;color:rgba(255,255,255,0.6);text-decoration:none;margin-bottom:0.3rem;}
.footer-bottom{border-top:1px solid rgba(255,255,255,0.1);padding-top:0.8rem;text-align:center;font-size:0.75rem;}

@media(max-width:768px){
  nav{padding:0 0.8rem;gap:0.6rem;}
  .logo{font-size:1.3rem;}
  .nav-btn .nav-label{display:none;}
  .search-bar{max-width:none;}
  .sec{padding:1rem;}
  .banner-row{grid-template-columns:1fr;}
  .cart-page-wrap{grid-template-columns:1fr;padding:1rem;}
  .order-summary{position:static;}
  .form-2col{grid-template-columns:1fr;}
  .offers{flex-wrap:wrap;}
  .offer{width:50%;flex:none;}
}
</style>
</head>
<body>

<!-- ========== NAV ========== -->
<nav id="mainNav">
  <div class="logo" onclick="showPage('home')">Shop<span>Kart</span></div>
  <div class="search-bar">
    <input type="text" id="searchInput" placeholder="Search products, brands..." oninput="searchProducts()">
    <button>🔍</button>
  </div>
  <div class="nav-btns">
    <span id="userBadge" style="display:none" class="user-badge">👤 <span id="userName"></span></span>
    <button class="nav-btn" onclick="showPage('login')" id="loginBtn">👤 Login</button>
    <button class="nav-btn" onclick="showPage('wishlist')">❤️ <span class="cnt" id="wlCount">0</span></button>
    <button class="nav-btn" onclick="showPage('cart')">🛒 Cart <span class="cnt" id="cartCount">0</span></button>
  </div>
</nav>

<!-- ========== HOME PAGE ========== -->
<div class="page active" id="page-home">
  <div class="cat-bar">
    <div class="cat-item active" onclick="filterCat('all',this)">🛍️<br>All</div>
    <div class="cat-item" onclick="filterCat('women',this)">👗<br>Women</div>
    <div class="cat-item" onclick="filterCat('men',this)">👔<br>Men</div>
    <div class="cat-item" onclick="filterCat('kids',this)">🧒<br>Kids</div>
    <div class="cat-item" onclick="filterCat('shoes',this)">👟<br>Shoes</div>
    <div class="cat-item" onclick="filterCat('electronics',this)">📱<br>Electronics</div>
    <div class="cat-item" onclick="filterCat('beauty',this)">💄<br>Beauty</div>
    <div class="cat-item" onclick="filterCat('bags',this)">👜<br>Bags</div>
  </div>
  <div class="offers">
    <div class="offer">🚚 Free Delivery ₹499+</div>
    <div class="offer">🔄 7-Day Returns</div>
    <div class="offer">💳 10% First Order</div>
    <div class="offer">⭐ 1Cr+ Customers</div>
  </div>
  <div class="hero">
    <div class="hero-text">
      <h1>Big Sale is <span>LIVE!</span> 🎉</h1>
      <p>Upto 80% off on Fashion, Electronics & more</p>
      <div class="hero-badges">
        <span class="hbadge">👗 Fashion 70% off</span>
        <span class="hbadge">📱 Electronics 50% off</span>
        <span class="hbadge">👟 Shoes 60% off</span>
      </div>
      <button class="shop-btn" onclick="document.getElementById('prodSec').scrollIntoView({behavior:'smooth'})">Shop Now →</button>
    </div>
  </div>

  <div class="sec">
    <div class="sec-hd"><h2>Shop by Category</h2></div>
    <div class="cat-grid">
      <div class="cat-card" onclick="filterCat('women',document.querySelectorAll('.cat-item')[1])"><img src="https://images.unsplash.com/photo-1583391733956-3750e0ff4e8b?w=200&h=70&fit=crop" alt="Women"><p>👗 Women</p></div>
      <div class="cat-card" onclick="filterCat('men',document.querySelectorAll('.cat-item')[2])"><img src="https://images.unsplash.com/photo-1617137968427-85924c800a22?w=200&h=70&fit=crop" alt="Men"><p>👔 Men</p></div>
      <div class="cat-card" onclick="filterCat('kids',document.querySelectorAll('.cat-item')[3])"><img src="https://images.unsplash.com/photo-1622290291468-a28f7a7dc6a8?w=200&h=70&fit=crop" alt="Kids"><p>🧒 Kids</p></div>
      <div class="cat-card" onclick="filterCat('shoes',document.querySelectorAll('.cat-item')[4])"><img src="https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=200&h=70&fit=crop" alt="Shoes"><p>👟 Shoes</p></div>
      <div class="cat-card" onclick="filterCat('electronics',document.querySelectorAll('.cat-item')[5])"><img src="https://images.unsplash.com/photo-1498049794561-7780e7231661?w=200&h=70&fit=crop" alt="Electronics"><p>📱 Electronics</p></div>
      <div class="cat-card" onclick="filterCat('beauty',document.querySelectorAll('.cat-item')[6])"><img src="https://images.unsplash.com/photo-1596462502278-27bfdc403348?w=200&h=70&fit=crop" alt="Beauty"><p>💄 Beauty</p></div>
      <div class="cat-card" onclick="filterCat('bags',document.querySelectorAll('.cat-item')[7])"><img src="https://images.unsplash.com/photo-1590874103328-eac38a683ce7?w=200&h=70&fit=crop" alt="Bags"><p>👜 Bags</p></div>
    </div>
  </div>

  <div class="sec" style="padding-top:0">
    <div class="banner-row">
      <div class="mini-banner" style="background:linear-gradient(135deg,#6A1B9A,#9C27B0)"><span class="tag">Women's Special</span><h3>Kurties & Sarees 👗</h3><p>Starting ₹299 | Upto 75% off</p></div>
      <div class="mini-banner" style="background:linear-gradient(135deg,#0D47A1,#1976D2)"><span class="tag">Men's Fashion</span><h3>Shirts & Jeans 👔</h3><p>Starting ₹499 | Upto 70% off</p></div>
    </div>
  </div>

  <div class="sec" id="prodSec">
    <div class="sec-hd"><h2 id="prodTitle">All Products</h2></div>
    <div class="filter-bar" id="filterBar"></div>
    <div class="prod-grid" id="prodGrid"></div>
  </div>

  <footer>
    <div class="footer-grid">
      <div class="footer-col"><h4>About</h4><a href="#">About ShopKart</a><a href="#">Careers</a><a href="#">Press</a></div>
      <div class="footer-col"><h4>Help</h4><a href="#">Payments</a><a href="#">Shipping</a><a href="#">Returns</a></div>
      <div class="footer-col"><h4>Policy</h4><a href="#">Return Policy</a><a href="#">Privacy</a><a href="#">Terms</a></div>
      <div class="footer-col"><h4>Social</h4><a href="#">📘 Facebook</a><a href="#">📸 Instagram</a><a href="#">▶️ YouTube</a></div>
    </div>
    <div class="footer-bottom">© 2025 ShopKart. Made with ❤️</div>
  </footer>
</div>

<!-- ========== LOGIN PAGE ========== -->
<div class="page" id="page-login">
  <div class="auth-page">
    <div class="auth-box">
      <div class="auth-logo">Shop<span>Kart</span></div>
      <p style="text-align:center;color:var(--muted);font-size:0.82rem;margin-bottom:1.2rem;">India's Best Online Shopping</p>
      <div class="auth-tabs">
        <div class="auth-tab active" onclick="switchTab('login')">Login</div>
        <div class="auth-tab" onclick="switchTab('signup')">Sign Up</div>
      </div>

      <!-- LOGIN FORM -->
      <div class="auth-form active" id="loginForm">
        <div class="form-group">
          <label>Email or Mobile</label>
          <input type="text" id="loginEmail" placeholder="Enter email or mobile number">
        </div>
        <div class="form-group">
          <label>Password</label>
          <input type="password" id="loginPass" placeholder="Enter password">
        </div>
        <button class="auth-submit" onclick="doLogin()">Login Securely →</button>
        <div class="auth-divider">or continue with</div>
        <div class="social-btns">
          <button class="social-btn" onclick="socialLogin('Google')">🌐 Google</button>
          <button class="social-btn" onclick="socialLogin('Facebook')">📘 Facebook</button>
        </div>
      </div>

      <!-- SIGNUP FORM -->
      <div class="auth-form" id="signupForm">
        <div class="form-group">
          <label>Full Name</label>
          <input type="text" id="signupName" placeholder="Enter your full name">
        </div>
        <div class="form-group">
          <label>Email</label>
          <input type="email" id="signupEmail" placeholder="Enter email">
        </div>
        <div class="form-group">
          <label>Mobile Number</label>
          <input type="tel" id="signupMobile" placeholder="10-digit mobile number">
        </div>
        <div class="form-group">
          <label>Password</label>
          <input type="password" id="signupPass" placeholder="Create password (min 6 chars)">
        </div>
        <button class="auth-submit" onclick="doSignup()">Create Account →</button>
        <div class="auth-divider">or continue with</div>
        <div class="social-btns">
          <button class="social-btn" onclick="socialLogin('Google')">🌐 Google</button>
          <button class="social-btn" onclick="socialLogin('Facebook')">📘 Facebook</button>
        </div>
      </div>

      <div class="auth-skip"><a onclick="showPage('home')">← Continue without login</a></div>
    </div>
  </div>
</div>

<!-- ========== WISHLIST PAGE ========== -->
<div class="page" id="page-wishlist">
  <div class="sec">
    <div class="sec-hd">
      <h2>❤️ My Wishlist (<span id="wlTitleCount">0</span> items)</h2>
      <a onclick="showPage('home')">← Continue Shopping</a>
    </div>
    <div id="wlContent"></div>
  </div>
</div>

<!-- ========== CART PAGE ========== -->
<div class="page" id="page-cart">
  <div class="checkout-steps">
    <div class="step active" id="step1"><span class="step-num">1</span> Cart</div>
    <div class="step-line" id="line1"></div>
    <div class="step" id="step2"><span class="step-num">2</span> Address</div>
    <div class="step-line" id="line2"></div>
    <div class="step" id="step3"><span class="step-num">3</span> Payment</div>
    <div class="step-line" id="line3"></div>
    <div class="step" id="step4"><span class="step-num">4</span> Confirm</div>
  </div>

  <!-- STEP 1: CART -->
  <div id="cartStep1">
    <div id="cartEmpty" style="display:none" class="wl-empty">
      <span class="big">🛒</span>
      <h3 style="margin-bottom:0.5rem">Your cart is empty!</h3>
      <p>Add items to get started</p>
      <button class="shop-btn" style="margin-top:1rem" onclick="showPage('home')">Shop Now →</button>
    </div>
    <div id="cartFull">
      <div class="cart-page-wrap">
        <div>
          <div class="sec-hd" style="margin-bottom:1rem"><h2>🛒 My Cart (<span id="cartItemCount">0</span> items)</h2><a onclick="showPage('home')">← Shop More</a></div>
          <div id="cartItemsList"></div>
        </div>
        <div class="order-summary">
          <h3>Price Details</h3>
          <div class="summary-row"><span>Price (<span id="sumCount">0</span> items)</span><span id="sumMrp">₹0</span></div>
          <div class="summary-row"><span>Discount</span><span class="green" id="sumDisc">-₹0</span></div>
          <div class="summary-row"><span>Delivery</span><span class="green">FREE</span></div>
          <div class="summary-row total"><span>Total Amount</span><span id="sumTotal">₹0</span></div>
          <div class="promo-row"><input type="text" id="promoInput" placeholder="Enter promo code"><button onclick="applyPromo()">Apply</button></div>
          <button class="place-btn" onclick="goToStep(2)">Proceed to Address →</button>
          <p class="safe-pay">🔒 Safe & Secure Payments</p>
        </div>
      </div>
    </div>
  </div>

  <!-- STEP 2: ADDRESS -->
  <div id="cartStep2" style="display:none">
    <div class="cart-page-wrap">
      <div>
        <div class="sec-hd" style="margin-bottom:1rem"><h2>📍 Delivery Address</h2></div>
        <div class="address-section">
          <h3>Add New Address</h3>
          <div class="form-2col">
            <div class="fg"><label>Full Name</label><input type="text" id="adName" placeholder="Your full name"></div>
            <div class="fg"><label>Mobile Number</label><input type="tel" id="adMobile" placeholder="10-digit number"></div>
          </div>
          <div class="fg"><label>Address Line 1</label><input type="text" id="adLine1" placeholder="House/Flat No, Building, Street"></div>
          <div class="fg"><label>Address Line 2</label><input type="text" id="adLine2" placeholder="Area, Colony, Landmark"></div>
          <div class="form-2col">
            <div class="fg"><label>City</label><input type="text" id="adCity" placeholder="City"></div>
            <div class="fg"><label>State</label>
              <select id="adState">
                <option value="">Select State</option>
                <option>Maharashtra</option><option>Delhi</option><option>Karnataka</option>
                <option>Tamil Nadu</option><option>Gujarat</option><option>Rajasthan</option>
                <option>West Bengal</option><option>Uttar Pradesh</option><option>Punjab</option>
                <option>Madhya Pradesh</option><option>Telangana</option><option>Kerala</option>
              </select>
            </div>
          </div>
          <div class="fg" style="max-width:200px"><label>PIN Code</label><input type="text" id="adPin" placeholder="6-digit PIN"></div>
        </div>
      </div>
      <div class="order-summary">
        <h3>Price Details</h3>
        <div class="summary-row"><span>Price (<span id="sumCount2">0</span> items)</span><span id="sumMrp2">₹0</span></div>
        <div class="summary-row"><span>Discount</span><span class="green" id="sumDisc2">-₹0</span></div>
        <div class="summary-row"><span>Delivery</span><span class="green">FREE</span></div>
        <div class="summary-row total"><span>Total Amount</span><span id="sumTotal2">₹0</span></div>
        <button class="place-btn" onclick="goToStep(3)">Continue to Payment →</button>
        <p class="safe-pay">🔒 Safe & Secure Payments</p>
      </div>
    </div>
  </div>

  <!-- STEP 3: PAYMENT -->
  <div id="cartStep3" style="display:none">
    <div class="cart-page-wrap">
      <div>
        <div class="sec-hd" style="margin-bottom:1rem"><h2>💳 Payment Method</h2></div>
        <div class="address-section">
          <h3>Choose Payment Method</h3>
          <div class="payment-opts">
            <div class="pay-opt selected" onclick="selectPay(this,'upi')">
              <input type="radio" name="pay" checked>
              <div class="pay-opt-info"><div class="pay-opt-title">📱 UPI</div><div class="pay-opt-sub">Google Pay, PhonePe, Paytm, BHIM</div></div>
            </div>
            <div class="pay-opt" onclick="selectPay(this,'card')">
              <input type="radio" name="pay">
              <div class="pay-opt-info"><div class="pay-opt-title">💳 Credit / Debit Card</div><div class="pay-opt-sub">Visa, Mastercard, RuPay</div></div>
            </div>
            <div class="pay-opt" onclick="selectPay(this,'netbanking')">
              <input type="radio" name="pay">
              <div class="pay-opt-info"><div class="pay-opt-title">🏦 Net Banking</div><div class="pay-opt-sub">All major banks supported</div></div>
            </div>
            <div class="pay-opt" onclick="selectPay(this,'emi')">
              <input type="radio" name="pay">
              <div class="pay-opt-info"><div class="pay-opt-title">📅 EMI</div><div class="pay-opt-sub">No cost EMI on select cards</div></div>
            </div>
            <div class="pay-opt" onclick="selectPay(this,'cod')">
              <input type="radio" name="pay">
              <div class="pay-opt-info"><div class="pay-opt-title">💵 Cash on Delivery</div><div class="pay-opt-sub">Pay when you receive</div></div>
            </div>
          </div>
        </div>
      </div>
      <div class="order-summary">
        <h3>Price Details</h3>
        <div class="summary-row"><span>Price (<span id="sumCount3">0</span> items)</span><span id="sumMrp3">₹0</span></div>
        <div class="summary-row"><span>Discount</span><span class="green" id="sumDisc3">-₹0</span></div>
        <div class="summary-row"><span>Delivery</span><span class="green">FREE</span></div>
        <div class="summary-row total"><span>Total Amount</span><span id="sumTotal3">₹0</span></div>
        <button class="place-btn" onclick="placeOrder()">🎉 Place Order →</button>
        <p class="safe-pay">🔒 Safe & Secure Payments. 100% Authentic Products.</p>
      </div>
    </div>
  </div>

  <!-- STEP 4: SUCCESS -->
  <div id="cartStep4" style="display:none">
    <div class="success-page">
      <span class="big-icon">🎉</span>
      <h2>Order Placed Successfully!</h2>
      <p>Thank you for shopping with ShopKart!</p>
      <div class="order-id" id="orderId">Order #SK00000</div>
      <br>
      <p style="color:var(--muted);font-size:0.9rem;margin-bottom:1.5rem">Estimated delivery: <strong>3-5 business days</strong><br>You'll receive a confirmation SMS shortly.</p>
      <button class="shop-btn" onclick="showPage('home')">Continue Shopping →</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ===== DATA =====
const products = [
  // WOMEN
  {id:1,name:"Floral Anarkali Kurti",brand:"Jaipur Ethnic",price:399,mrp:1299,discount:69,rating:4.3,reviews:2845,img:"https://images.unsplash.com/photo-1583391733956-3750e0ff4e8b?w=400&h=400&fit=crop",category:"women",sub:"Kurti"},
  {id:2,name:"Banarasi Silk Saree",brand:"KalaBharat",price:1299,mrp:4999,discount:74,rating:4.5,reviews:2100,img:"https://images.unsplash.com/photo-1610030469983-98e550d6193c?w=400&h=400&fit=crop",category:"women",sub:"Saree"},
  {id:3,name:"Georgette Lehenga Choli",brand:"EthnicWear",price:1799,mrp:5999,discount:70,rating:4.4,reviews:1543,img:"https://images.unsplash.com/photo-1618932260643-eee4a2f652a6?w=400&h=400&fit=crop",category:"women",sub:"Lehenga"},
  {id:4,name:"Cotton Printed Kurti",brand:"FabIndia",price:599,mrp:1799,discount:67,rating:4.2,reviews:3210,img:"https://images.unsplash.com/photo-1564670153519-7b4417c304f0?w=400&h=400&fit=crop",category:"women",sub:"Kurti"},
  {id:5,name:"Women's Palazzo Pants",brand:"StyleZone",price:349,mrp:999,discount:65,rating:4.1,reviews:1890,img:"https://images.unsplash.com/photo-1509631179647-0177331693ae?w=400&h=400&fit=crop",category:"women",sub:"Bottom"},
  {id:6,name:"Party Wear Gown",brand:"GlamDiva",price:1499,mrp:4999,discount:70,rating:4.6,reviews:980,img:"https://images.unsplash.com/photo-1566174053879-31528523f8ae?w=400&h=400&fit=crop",category:"women",sub:"Gown"},
  {id:7,name:"Women's Crop Top",brand:"TrendyLook",price:299,mrp:799,discount:63,rating:4.0,reviews:3450,img:"https://images.unsplash.com/photo-1552902865-b72c031ac5ea?w=400&h=400&fit=crop",category:"women",sub:"Top"},
  {id:8,name:"Flared Skirt Cotton",brand:"StyleMe",price:399,mrp:1099,discount:64,rating:4.1,reviews:2100,img:"https://images.unsplash.com/photo-1583496661160-fb5886a0aaaa?w=400&h=400&fit=crop",category:"women",sub:"Skirt"},
  {id:9,name:"Women's Winter Jacket",brand:"Zara",price:1999,mrp:5999,discount:67,rating:4.5,reviews:1230,img:"https://images.unsplash.com/photo-1548624313-0396c75e4b1a?w=400&h=400&fit=crop",category:"women",sub:"Jacket"},
  {id:10,name:"Churidar Suit Set",brand:"EthnicStyle",price:899,mrp:2799,discount:68,rating:4.4,reviews:2340,img:"https://images.unsplash.com/photo-1513094775335-3b5b2a97c1f6?w=400&h=400&fit=crop",category:"women",sub:"Suit"},
  // MEN
  {id:11,name:"Men's Slim Fit Jeans",brand:"Levi's",price:799,mrp:2499,discount:68,rating:4.1,reviews:5621,img:"https://images.unsplash.com/photo-1542272604-787c3835535d?w=400&h=400&fit=crop",category:"men",sub:"Jeans"},
  {id:12,name:"Men's Formal Shirt",brand:"Arrow",price:699,mrp:1999,discount:65,rating:4.3,reviews:4320,img:"https://images.unsplash.com/photo-1596755094514-f87e34085b2c?w=400&h=400&fit=crop",category:"men",sub:"Shirt"},
  {id:13,name:"Men's Polo T-Shirt",brand:"US Polo",price:499,mrp:1499,discount:67,rating:4.2,reviews:7890,img:"https://images.unsplash.com/photo-1618354691373-d851c5c3a990?w=400&h=400&fit=crop",category:"men",sub:"T-Shirt"},
  {id:14,name:"Men's Casual Kurta",brand:"Manyavar",price:799,mrp:2199,discount:64,rating:4.4,reviews:3210,img:"https://images.unsplash.com/photo-1617137968427-85924c800a22?w=400&h=400&fit=crop",category:"men",sub:"Kurta"},
  {id:15,name:"Men's Hoodie",brand:"Nike",price:1299,mrp:3499,discount:63,rating:4.5,reviews:5430,img:"https://images.unsplash.com/photo-1556821840-3a63f15732ce?w=400&h=400&fit=crop",category:"men",sub:"Hoodie"},
  {id:16,name:"Men's Blazer",brand:"Raymond",price:2499,mrp:6999,discount:64,rating:4.6,reviews:1230,img:"https://images.unsplash.com/photo-1507679799987-c73779587ccf?w=400&h=400&fit=crop",category:"men",sub:"Blazer"},
  {id:17,name:"Men's Track Pants",brand:"Adidas",price:899,mrp:2499,discount:64,rating:4.3,reviews:6540,img:"https://images.unsplash.com/photo-1592878904946-b3cd8ae243d0?w=400&h=400&fit=crop",category:"men",sub:"Track Pant"},
  {id:18,name:"Men's Ethnic Sherwani",brand:"Manyavar",price:3999,mrp:9999,discount:60,rating:4.7,reviews:890,img:"https://images.unsplash.com/photo-1609902726285-00668009f004?w=400&h=400&fit=crop",category:"men",sub:"Sherwani"},
  {id:19,name:"Men's Denim Jacket",brand:"Pepe Jeans",price:1499,mrp:3999,discount:63,rating:4.3,reviews:3210,img:"https://images.unsplash.com/photo-1601333144130-8cbb312386b6?w=400&h=400&fit=crop",category:"men",sub:"Jacket"},
  {id:20,name:"Men's Printed T-Shirt",brand:"H&M",price:399,mrp:999,discount:60,rating:4.0,reviews:8900,img:"https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=400&h=400&fit=crop",category:"men",sub:"T-Shirt"},
  // KIDS
  {id:21,name:"Girls Party Frock",brand:"KidsFashion",price:449,mrp:1299,discount:65,rating:4.5,reviews:2100,img:"https://images.unsplash.com/photo-1622290291468-a28f7a7dc6a8?w=400&h=400&fit=crop",category:"kids",sub:"Girls"},
  {id:22,name:"Boys Denim Jeans",brand:"KidsWear",price:399,mrp:999,discount:60,rating:4.2,reviews:1870,img:"https://images.unsplash.com/photo-1519238263530-99bdd11df2ea?w=400&h=400&fit=crop",category:"kids",sub:"Boys"},
  {id:23,name:"Kids Cartoon T-Shirt",brand:"HappyKids",price:249,mrp:599,discount:58,rating:4.3,reviews:3450,img:"https://images.unsplash.com/photo-1578662996442-48f60103fc96?w=400&h=400&fit=crop",category:"kids",sub:"T-Shirt"},
  {id:24,name:"Kids Winter Jacket",brand:"WarmKids",price:799,mrp:2199,discount:64,rating:4.5,reviews:1450,img:"https://images.unsplash.com/photo-1503944583220-79d8926ad5e2?w=400&h=400&fit=crop",category:"kids",sub:"Jacket"},
  {id:25,name:"Girls Leggings",brand:"TinyTots",price:199,mrp:499,discount:60,rating:4.1,reviews:2890,img:"https://images.unsplash.com/photo-1471286174890-9c112ac6476d?w=400&h=400&fit=crop",category:"kids",sub:"Girls"},
  {id:26,name:"Boys Shorts Pack 3",brand:"WearMore",price:349,mrp:899,discount:61,rating:4.2,reviews:1340,img:"https://images.unsplash.com/photo-1555274175-6cbf6f3b137b?w=400&h=400&fit=crop",category:"kids",sub:"Boys"},
  // SHOES
  {id:27,name:"Women's Heels Sandals",brand:"Inc.5",price:899,mrp:2499,discount:64,rating:4.3,reviews:3210,img:"https://images.unsplash.com/photo-1543163521-1bf539c55dd2?w=400&h=400&fit=crop",category:"shoes",sub:"Women"},
  {id:28,name:"Men's Running Shoes",brand:"Nike",price:2499,mrp:5999,discount:58,rating:4.5,reviews:8920,img:"https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=400&h=400&fit=crop",category:"shoes",sub:"Men"},
  {id:29,name:"Women's Casual Flats",brand:"Bata",price:599,mrp:1499,discount:60,rating:4.2,reviews:4320,img:"https://images.unsplash.com/photo-1603487742131-4160ec999306?w=400&h=400&fit=crop",category:"shoes",sub:"Women"},
  {id:30,name:"Men's Formal Shoes",brand:"Clarks",price:1999,mrp:4999,discount:60,rating:4.4,reviews:2100,img:"https://images.unsplash.com/photo-1614252369475-531eba835eb1?w=400&h=400&fit=crop",category:"shoes",sub:"Men"},
  {id:31,name:"Kids Sneakers",brand:"Keds",price:699,mrp:1799,discount:61,rating:4.3,reviews:1890,img:"https://images.unsplash.com/photo-1551107696-a4b0c5a0d9a2?w=400&h=400&fit=crop",category:"shoes",sub:"Kids"},
  {id:32,name:"Men's Sports Shoes",brand:"Adidas",price:1999,mrp:4999,discount:60,rating:4.6,reviews:7650,img:"https://images.unsplash.com/photo-1608231387042-66d1773070a5?w=400&h=400&fit=crop",category:"shoes",sub:"Men"},
  {id:33,name:"Women's Boots",brand:"Catwalk",price:1799,mrp:4499,discount:60,rating:4.3,reviews:1230,img:"https://images.unsplash.com/photo-1608256246200-53e635b5b65f?w=400&h=400&fit=crop",category:"shoes",sub:"Women"},
  {id:34,name:"Women's Block Heels",brand:"Steve Madden",price:1299,mrp:3499,discount:63,rating:4.1,reviews:1560,img:"https://images.unsplash.com/photo-1515347619252-60a4bf4fff4f?w=400&h=400&fit=crop",category:"shoes",sub:"Women"},
  // ELECTRONICS
  {id:35,name:"Wireless Earbuds",brand:"boAt",price:999,mrp:3999,discount:75,rating:4.4,reviews:12430,img:"https://images.unsplash.com/photo-1606220588913-b3aacb4d2f46?w=400&h=400&fit=crop",category:"electronics",sub:"Audio"},
  {id:36,name:"Smartphone 6GB 128GB",brand:"Realme",price:9999,mrp:19999,discount:50,rating:4.2,reviews:8932,img:"https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?w=400&h=400&fit=crop",category:"electronics",sub:"Mobile"},
  {id:37,name:"Smart Watch",brand:"Fire-Boltt",price:1999,mrp:6999,discount:71,rating:4.1,reviews:5430,img:"https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=400&h=400&fit=crop",category:"electronics",sub:"Wearable"},
  {id:38,name:"Laptop 15.6 i5",brand:"HP",price:45999,mrp:69999,discount:34,rating:4.5,reviews:3210,img:"https://images.unsplash.com/photo-1496181133206-80ce9b88a853?w=400&h=400&fit=crop",category:"electronics",sub:"Laptop"},
  {id:39,name:"Bluetooth Speaker",brand:"JBL",price:1499,mrp:3999,discount:63,rating:4.6,reviews:9870,img:"https://images.unsplash.com/photo-1608043152269-423dbba4e7e1?w=400&h=400&fit=crop",category:"electronics",sub:"Audio"},
  {id:40,name:"Wireless Mouse",brand:"Logitech",price:799,mrp:1999,discount:60,rating:4.5,reviews:6780,img:"https://images.unsplash.com/photo-1527864550417-7fd91fc51a46?w=400&h=400&fit=crop",category:"electronics",sub:"Accessories"},
  // BEAUTY
  {id:41,name:"Vitamin C Face Serum",brand:"Minimalist",price:349,mrp:999,discount:65,rating:4.3,reviews:6750,img:"https://images.unsplash.com/photo-1570194065650-d99fb4bedf0a?w=400&h=400&fit=crop",category:"beauty",sub:"Skincare"},
  {id:42,name:"Lipstick Set 12 Colors",brand:"Maybelline",price:299,mrp:899,discount:67,rating:4.1,reviews:4320,img:"https://images.unsplash.com/photo-1596462502278-27bfdc403348?w=400&h=400&fit=crop",category:"beauty",sub:"Makeup"},
  {id:43,name:"Hair Straightener",brand:"Philips",price:1299,mrp:3499,discount:63,rating:4.4,reviews:5430,img:"https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?w=400&h=400&fit=crop",category:"beauty",sub:"Hair"},
  {id:44,name:"Perfume 100ml",brand:"Engage",price:499,mrp:1299,discount:62,rating:4.2,reviews:3210,img:"https://images.unsplash.com/photo-1541643600914-78b084683702?w=400&h=400&fit=crop",category:"beauty",sub:"Fragrance"},
  {id:45,name:"Eye Shadow Palette",brand:"NYX",price:599,mrp:1499,discount:60,rating:4.4,reviews:3890,img:"https://images.unsplash.com/photo-1512496015851-a90fb38ba796?w=400&h=400&fit=crop",category:"beauty",sub:"Makeup"},
  // BAGS
  {id:46,name:"Women's Handbag",brand:"Caprese",price:999,mrp:2999,discount:67,rating:4.3,reviews:3210,img:"https://images.unsplash.com/photo-1590874103328-eac38a683ce7?w=400&h=400&fit=crop",category:"bags",sub:"Women"},
  {id:47,name:"Men's Backpack 30L",brand:"Wildcraft",price:1299,mrp:3499,discount:63,rating:4.5,reviews:5430,img:"https://images.unsplash.com/photo-1553062407-98eeb64c6a62?w=400&h=400&fit=crop",category:"bags",sub:"Men"},
  {id:48,name:"Travel Trolley Bag",brand:"Safari",price:2999,mrp:6999,discount:57,rating:4.4,reviews:2100,img:"https://images.unsplash.com/photo-1565026057447-bc90a3dceb87?w=400&h=400&fit=crop",category:"bags",sub:"Travel"},
  {id:49,name:"College Backpack",brand:"Skybags",price:799,mrp:1999,discount:60,rating:4.2,reviews:7890,img:"https://images.unsplash.com/photo-1491637639811-60e2756cc1c7?w=400&h=400&fit=crop",category:"bags",sub:"College"},
  {id:50,name:"Clutch Bag",brand:"Lavie",price:599,mrp:1499,discount:60,rating:4.1,reviews:2340,img:"https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=400&h=400&fit=crop",category:"bags",sub:"Women"},
];

let cart=[], wishlist=new Set(), currentUser=null, currentCat='all', currentSub='all';

// ===== PAGE SYSTEM =====
function showPage(p){
  document.querySelectorAll('.page').forEach(x=>x.classList.remove('active'));
  document.getElementById('page-'+p).classList.add('active');
  window.scrollTo(0,0);
  if(p==='wishlist') renderWishlist();
  if(p==='cart') renderCartPage();
}

// ===== AUTH =====
function switchTab(t){
  document.querySelectorAll('.auth-tab').forEach(x=>x.classList.remove('active'));
  document.querySelectorAll('.auth-form').forEach(x=>x.classList.remove('active'));
  document.querySelector(`.auth-tab:${t==='login'?'first':'last'}-child`).classList.add('active');
  document.getElementById(t+'Form').classList.add('active');
}
function doLogin(){
  const e=document.getElementById('loginEmail').value.trim();
  const p=document.getElementById('loginPass').value;
  if(!e||!p){showToast('Please fill all fields ⚠️');return;}
  const name=e.split('@')[0]||e;
  loginSuccess(name);
}
function doSignup(){
  const n=document.getElementById('signupName').value.trim();
  const e=document.getElementById('signupEmail').value.trim();
  const m=document.getElementById('signupMobile').value.trim();
  const p=document.getElementById('signupPass').value;
  if(!n||!e||!m||!p){showToast('Please fill all fields ⚠️');return;}
  if(m.length!==10){showToast('Enter valid 10-digit mobile ⚠️');return;}
  if(p.length<6){showToast('Password must be 6+ characters ⚠️');return;}
  loginSuccess(n);
}
function socialLogin(s){loginSuccess(s+' User');}
function loginSuccess(name){
  currentUser=name;
  document.getElementById('userBadge').style.display='flex';
  document.getElementById('userName').textContent=name;
  document.getElementById('loginBtn').style.display='none';
  showToast('Welcome, '+name+'! 🎉');
  showPage('home');
}

// ===== PRODUCTS =====
function renderProducts(list){
  const g=document.getElementById('prodGrid');
  if(!list.length){g.innerHTML='<div style="grid-column:1/-1;text-align:center;padding:3rem;color:var(--muted)">No products found 😔</div>';return;}
  g.innerHTML=list.map(p=>`
    <div class="prod-card">
      <div class="prod-img-wrap">
        <img class="prod-img" src="${p.img}" alt="${p.name}" loading="lazy" onerror="this.style.background='#f0f0f0';this.src='https://via.placeholder.com/400x400?text=${encodeURIComponent(p.name)}'">
        <button class="wl-btn" onclick="toggleWL(${p.id},this)" title="Wishlist">${wishlist.has(p.id)?'❤️':'🤍'}</button>
      </div>
      <div class="prod-info">
        <div class="prod-brand">${p.brand}</div>
        <div class="prod-name">${p.name}</div>
        <div class="rating-row"><span class="rbadge">⭐ ${p.rating}</span><span class="rcnt">(${p.reviews.toLocaleString()})</span></div>
        <div class="price-row">
          <span class="price">₹${p.price.toLocaleString()}</span>
          <span class="mrp">₹${p.mrp.toLocaleString()}</span>
          <span class="disc">${p.discount}% off</span>
        </div>
        <button class="add-btn" onclick="addCart(${p.id})">🛒 Add to Cart</button>
      </div>
    </div>
  `).join('');
}

function renderFilters(cat){
  const bar=document.getElementById('filterBar');
  const subs=[...new Set(products.filter(p=>cat==='all'||p.category===cat).map(p=>p.sub))];
  if(subs.length<2){bar.innerHTML='';return;}
  bar.innerHTML='<button class="fbtn active" onclick="filterSub(\'all\',this)">All</button>'+
    subs.map(s=>`<button class="fbtn" onclick="filterSub('${s}',this)">${s}</button>`).join('');
  currentSub='all';
}

function filterCat(cat,el){
  currentCat=cat;
  document.querySelectorAll('.cat-item').forEach(e=>e.classList.remove('active'));
  if(el)el.classList.add('active');
  const titles={all:'All Products',women:"Women's Fashion",men:"Men's Fashion",kids:'Kids Wear',shoes:'Footwear',electronics:'Electronics',beauty:'Beauty & Care',bags:'Bags'};
  document.getElementById('prodTitle').textContent=titles[cat]||'Products';
  renderFilters(cat);
  renderProducts(cat==='all'?products:products.filter(p=>p.category===cat));
  document.getElementById('prodSec').scrollIntoView({behavior:'smooth'});
}

function filterSub(sub,el){
  currentSub=sub;
  document.querySelectorAll('.fbtn').forEach(e=>e.classList.remove('active'));
  el.classList.add('active');
  let list=currentCat==='all'?products:products.filter(p=>p.category===currentCat);
  if(sub!=='all')list=list.filter(p=>p.sub===sub);
  renderProducts(list);
}

function searchProducts(){
  const q=document.getElementById('searchInput').value.toLowerCase();
  document.getElementById('prodTitle').textContent=q?`Results for "${q}"`:'All Products';
  document.getElementById('filterBar').innerHTML='';
  renderProducts(products.filter(p=>p.name.toLowerCase().includes(q)||p.brand.toLowerCase().includes(q)||p.category.toLowerCase().includes(q)));
}

// ===== WISHLIST =====
function toggleWL(id,btn){
  if(wishlist.has(id)){wishlist.delete(id);btn.textContent='🤍';showToast('Removed from wishlist');}
  else{wishlist.add(id);btn.textContent='❤️';showToast('Added to wishlist ❤️');}
  document.getElementById('wlCount').textContent=wishlist.size;
}

function renderWishlist(){
  document.getElementById('wlCount').textContent=wishlist.size;
  document.getElementById('wlTitleCount').textContent=wishlist.size;
  const c=document.getElementById('wlContent');
  if(!wishlist.size){
    c.innerHTML='<div class="wl-empty"><span class="big">❤️</span><h3>Your wishlist is empty</h3><p style="margin:0.5rem 0 1rem">Save items you love here</p><button class="shop-btn" onclick="showPage(\'home\')">Start Shopping →</button></div>';
    return;
  }
  const items=products.filter(p=>wishlist.has(p.id));
  c.innerHTML='<div class="prod-grid">'+items.map(p=>`
    <div class="prod-card">
      <div class="prod-img-wrap">
        <img class="prod-img" src="${p.img}" alt="${p.name}" loading="lazy">
        <button class="wl-btn" onclick="removeWL(${p.id})" title="Remove">❤️</button>
      </div>
      <div class="prod-info">
        <div class="prod-brand">${p.brand}</div>
        <div class="prod-name">${p.name}</div>
        <div class="price-row">
          <span class="price">₹${p.price.toLocaleString()}</span>
          <span class="mrp">₹${p.mrp.toLocaleString()}</span>
          <span class="disc">${p.discount}% off</span>
        </div>
        <button class="add-btn" onclick="addCart(${p.id});removeWL(${p.id})">🛒 Move to Cart</button>
      </div>
    </div>
  `).join('')+'</div>';
}

function removeWL(id){
  wishlist.delete(id);
  document.getElementById('wlCount').textContent=wishlist.size;
  renderWishlist();
  showToast('Removed from wishlist');
  // update heart buttons on home page
  document.querySelectorAll('.wl-btn').forEach(b=>{
    if(b.getAttribute('onclick')&&b.getAttribute('onclick').includes(id))b.textContent='🤍';
  });
}

// ===== CART =====
function addCart(id){
  const p=products.find(x=>x.id===id);
  const ex=cart.find(x=>x.id===id);
  if(ex){ex.qty++;}else{cart.push({...p,qty:1});}
  updateCartCount();
  showToast(`${p.name} added to cart! 🛒`);
}

function removeCart(id){cart=cart.filter(x=>x.id!==id);renderCartPage();}

function changeCartQty(id,d){
  const item=cart.find(x=>x.id===id);
  if(!item)return;
  item.qty+=d;
  if(item.qty<=0){removeCart(id);}else{renderCartPage();}
}

function updateCartCount(){
  const n=cart.reduce((s,x)=>s+x.qty,0);
  document.getElementById('cartCount').textContent=n;
}

function getSummary(){
  const count=cart.reduce((s,x)=>s+x.qty,0);
  const mrp=cart.reduce((s,x)=>s+x.mrp*x.qty,0);
  const total=cart.reduce((s,x)=>s+x.price*x.qty,0);
  const disc=mrp-total;
  return{count,mrp,total,disc};
}

function setSummaryUI(suffix=''){
  const {count,mrp,total,disc}=getSummary();
  const s=suffix;
  if(document.getElementById('sumCount'+s))document.getElementById('sumCount'+s).textContent=count;
  if(document.getElementById('sumMrp'+s))document.getElementById('sumMrp'+s).textContent='₹'+mrp.toLocaleString();
  if(document.getElementById('sumDisc'+s))document.getElementById('sumDisc'+s).textContent='-₹'+disc.toLocaleString();
  if(document.getElementById('sumTotal'+s))document.getElementById('sumTotal'+s).textContent='₹'+total.toLocaleString();
}

function renderCartPage(){
  updateCartCount();
  if(!cart.length){
    document.getElementById('cartEmpty').style.display='block';
    document.getElementById('cartFull').style.display='none';
    return;
  }
  document.getElementById('cartEmpty').style.display='none';
  document.getElementById('cartFull').style.display='block';
  document.getElementById('cartItemCount').textContent=cart.reduce((s,x)=>s+x.qty,0);
  document.getElementById('cartItemsList').innerHTML=cart.map(item=>`
    <div class="cart-item-row">
      <img src="${item.img}" alt="${item.name}" onerror="this.style.background='#f0f0f0'">
      <div class="ci-info">
        <div class="ci-name">${item.name}</div>
        <div class="ci-brand">${item.brand}</div>
        <div style="display:flex;align-items:center">
          <span class="ci-price">₹${item.price.toLocaleString()}</span>
          <span class="ci-mrp">₹${item.mrp.toLocaleString()}</span>
          <span class="ci-disc">${item.discount}% off</span>
        </div>
        <div class="ci-qty">
          <button class="qbtn" onclick="changeCartQty(${item.id},-1)">−</button>
          <span class="qnum">${item.qty}</span>
          <button class="qbtn" onclick="changeCartQty(${item.id},1)">+</button>
        </div>
        <button class="ci-remove" onclick="removeCart(${item.id})">🗑 Remove</button>
      </div>
    </div>
  `).join('');
  setSummaryUI('');
  setSummaryUI('2');
  setSummaryUI('3');
}

function applyPromo(){
  const v=document.getElementById('promoInput').value.toUpperCase();
  if(v==='SAVE10'||v==='SHOPKART'){showToast('Promo applied! Extra 10% off 🎉');}
  else{showToast('Invalid promo code ❌');}
}

function goToStep(n){
  [1,2,3,4].forEach(i=>{
    document.getElementById('cartStep'+i).style.display=i===n?'block':'none';
    const s=document.getElementById('step'+i);
    if(s){s.className='step'+(i<n?' done':i===n?' active':'');}
    const l=document.getElementById('line'+i);
    if(l){l.className='step-line'+(i<n?' done':'');}
  });
  setSummaryUI('2');
  setSummaryUI('3');
  window.scrollTo(0,0);
}

function selectPay(el){
  document.querySelectorAll('.pay-opt').forEach(x=>{x.classList.remove('selected');x.querySelector('input').checked=false;});
  el.classList.add('selected');
  el.querySelector('input').checked=true;
}

function placeOrder(){
  const oid='SK'+Math.floor(100000+Math.random()*900000);
  document.getElementById('orderId').textContent='Order #'+oid;
  cart=[];
  updateCartCount();
  goToStep(4);
  showToast('Order placed successfully! 🎉');
}

// ===== TOAST =====
let toastT;
function showToast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg;t.classList.add('show');
  clearTimeout(toastT);
  toastT=setTimeout(()=>t.classList.remove('show'),2500);
}

// ===== INIT =====
renderProducts(products);
renderFilters('all');
</script>
</body>
</html>
<a href="product.html?id=1">Product</a>
<div id="product-details"></div>

<script>
const products = [
{
id: 1,
name: "T-Shirt",
price: "₹499",
image: "https://via.placeholder.com/300"
},
{
id: 2,
name: "Jeans",
price: "₹999",
image: "https://via.placeholder.com/300"
}
];

const params = new URLSearchParams(window.location.search);
const productId = parseInt(params.get("id"));

const product = products.find(p => p.id === productId);

if(product){
document.getElementById("product-details").innerHTML = `
<img src="${product.image}" width="300">
<h2>${product.name}</h2>
<p>${product.price}</p>
<button>Buy Now</button>
<button>Add To Cart</button>
`;
}else{
document.getElementById("product-details").innerHTML =
"<h2>Product Not Found</h2>";
}
</script>

