<!doctype html>
<html lang="en">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Youth Fashion Store</title>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      box-sizing: border-box;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    .page {
      display: none;
    }

    .page.active {
      display: block;
    }

    .hero-gradient {
      background: linear-gradient(135deg, var(--bg-color) 0%, var(--surface-color) 100%);
    }

    .product-card {
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .product-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
    }

    .nav-link {
      position: relative;
      transition: color 0.3s ease;
    }

    .nav-link::after {
      content: '';
      position: absolute;
      bottom: -4px;
      left: 0;
      width: 0;
      height: 2px;
      background-color: var(--primary-action);
      transition: width 0.3s ease;
    }

    .nav-link:hover::after,
    .nav-link.active::after {
      width: 100%;
    }

    .btn-primary {
      background-color: var(--primary-action);
      transition: all 0.3s ease;
    }

    .btn-primary:hover {
      background-color: var(--primary-action-hover);
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }

    .btn-secondary {
      background-color: var(--secondary-action);
      transition: all 0.3s ease;
    }

    .btn-secondary:hover {
      background-color: var(--secondary-action-hover);
    }

    .cart-badge {
      background-color: var(--primary-action);
    }

    @media (max-width: 768px) {
      .mobile-menu {
        display: none;
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        background-color: var(--surface-color);
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        z-index: 50;
      }

      .mobile-menu.active {
        display: block;
      }
    }

    .size-option {
      border: 2px solid var(--secondary-surface);
      transition: all 0.3s ease;
    }

    .size-option:hover,
    .size-option.selected {
      border-color: var(--primary-action);
      background-color: var(--primary-action);
      color: white;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body>
  <div id="app" style="min-height: 100%; width: 100%; background-color: var(--bg-color); font-family: var(--font-family), -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;"><!-- Navigation -->
   <nav style="width: 100%; background-color: var(--surface-color); box-shadow: 0 2px 8px rgba(0,0,0,0.1); position: sticky; top: 0; z-index: 100;">
    <div style="max-width: 1200px; margin: 0 auto; padding: 1.25rem 1.5rem;">
     <div style="display: flex; justify-content: space-between; align-items: center;">
      <div style="display: flex; align-items: center; gap: 0.5rem;">
       <svg width="32" height="32" viewbox="0 0 32 32" style="fill: var(--primary-action);"><path d="M16 2L4 8v8c0 7.732 5.16 14.984 12 16.836C22.84 30.984 28 23.732 28 16V8L16 2zm0 4.236L24 10v6c0 5.96-3.876 11.524-8 13.164C11.876 27.524 8 21.96 8 16v-6l8-3.764z" /> <circle cx="16" cy="16" r="4" />
       </svg>
       <h1 id="site-name" style="font-size: 1.5rem; font-weight: 700; color: var(--text-color);">VIBE</h1>
      </div><!-- Desktop Menu -->
      <div class="hidden md:flex" style="gap: 2rem; align-items: center;"><a href="#home" class="nav-link active" data-page="home" style="color: var(--text-color); text-decoration: none; font-weight: 500; padding-bottom: 0.25rem;">Home</a> <a href="#shop" class="nav-link" data-page="shop" style="color: var(--text-color); text-decoration: none; font-weight: 500; padding-bottom: 0.25rem;">Shop</a> <a href="#collections" class="nav-link" data-page="collections" style="color: var(--text-color); text-decoration: none; font-weight: 500; padding-bottom: 0.25rem;">Collections</a> <a href="#about" class="nav-link" data-page="about" style="color: var(--text-color); text-decoration: none; font-weight: 500; padding-bottom: 0.25rem;">About</a> <a href="#contact" class="nav-link" data-page="contact" style="color: var(--text-color); text-decoration: none; font-weight: 500; padding-bottom: 0.25rem;">Contact</a>
      </div>
      <div style="display: flex; gap: 1rem; align-items: center;"><button id="cart-btn" style="position: relative; background: none; border: none; cursor: pointer;">
        <svg width="24" height="24" viewbox="0 0 24 24" fill="none" stroke="var(--text-color)" stroke-width="2"><path d="M9 2L7 6H3L5 18h14l2-12h-4l-2-4H9z" /> <circle cx="9" cy="21" r="1" /> <circle cx="17" cy="21" r="1" />
        </svg><span id="cart-count" class="cart-badge" style="position: absolute; top: -8px; right: -8px; width: 20px; height: 20px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 0.75rem; font-weight: 700; color: white;">0</span> </button> <!-- Mobile Menu Toggle --> <button id="mobile-menu-btn" class="md:hidden" style="background: none; border: none; cursor: pointer;">
        <svg width="24" height="24" viewbox="0 0 24 24" fill="none" stroke="var(--text-color)" stroke-width="2"><path d="M3 12h18M3 6h18M3 18h18" />
        </svg></button>
      </div>
     </div><!-- Mobile Menu -->
     <div id="mobile-menu" class="mobile-menu">
      <div style="display: flex; flex-direction: column; padding: 1rem 0;"><a href="#home" class="nav-link" data-page="home" style="color: var(--text-color); text-decoration: none; padding: 0.75rem 1rem; font-weight: 500;">Home</a> <a href="#shop" class="nav-link" data-page="shop" style="color: var(--text-color); text-decoration: none; padding: 0.75rem 1rem; font-weight: 500;">Shop</a> <a href="#collections" class="nav-link" data-page="collections" style="color: var(--text-color); text-decoration: none; padding: 0.75rem 1rem; font-weight: 500;">Collections</a> <a href="#about" class="nav-link" data-page="about" style="color: var(--text-color); text-decoration: none; padding: 0.75rem 1rem; font-weight: 500;">About</a> <a href="#contact" class="nav-link" data-page="contact" style="color: var(--text-color); text-decoration: none; padding: 0.75rem 1rem; font-weight: 500;">Contact</a>
      </div>
     </div>
    </div>
   </nav><!-- Home Page -->
   <div id="page-home" class="page active"><!-- Hero Section -->
    <section class="hero-gradient" style="width: 100%; padding: 4rem 1.5rem; text-align: center;">
     <div style="max-width: 800px; margin: 0 auto;">
      <h2 id="hero-title" style="font-size: 3rem; font-weight: 800; color: var(--text-color); margin-bottom: 1rem; line-height: 1.2;">Your Style, Your Vibe</h2>
      <p id="hero-subtitle" style="font-size: 1.25rem; color: var(--text-color); margin-bottom: 2rem; opacity: 0.9;">Discover the latest trends in streetwear and express yourself</p><button id="cta-button" class="btn-primary" style="padding: 1rem 2.5rem; border: none; border-radius: 50px; font-size: 1.125rem; font-weight: 600; color: white; cursor: pointer;"> Shop Now </button>
     </div>
    </section><!-- Featured Products -->
    <section style="width: 100%; padding: 4rem 1.5rem;">
     <div style="max-width: 1200px; margin: 0 auto;">
      <h3 style="font-size: 2rem; font-weight: 700; color: var(--text-color); margin-bottom: 2rem; text-align: center;">Featured Drops</h3>
      <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 2rem;"><!-- Product 1 -->
       <div class="product-card" style="background-color: var(--surface-color); border-radius: 16px; overflow: hidden; cursor: pointer;">
        <div style="width: 100%; height: 300px; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); display: flex; align-items: center; justify-content: center;">
         <svg width="120" height="120" viewbox="0 0 120 120" fill="white" opacity="0.9"><path d="M60 10L40 30v60l20 20 20-20V30L60 10zm0 10l10 10v50l-10 10-10-10V30l10-10z" /> <text x="60" y="70" text-anchor="middle" font-size="24" fill="white" font-weight="bold">
           HOODIE
          </text>
         </svg>
        </div>
        <div style="padding: 1.5rem;">
         <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Classic Hoodie</h4>
         <p style="color: var(--text-color); opacity: 0.7; margin-bottom: 1rem;">Premium cotton blend</p>
         <div style="display: flex; justify-content: space-between; align-items: center;"><span style="font-size: 1.5rem; font-weight: 700; color: var(--primary-action);">$59</span> <button class="add-to-cart btn-secondary" data-product="Classic Hoodie" data-price="59" style="padding: 0.5rem 1.25rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">Add to Cart</button>
         </div>
        </div>
       </div><!-- Product 2 -->
       <div class="product-card" style="background-color: var(--surface-color); border-radius: 16px; overflow: hidden; cursor: pointer;">
        <div style="width: 100%; height: 300px; background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); display: flex; align-items: center; justify-content: center;">
         <svg width="120" height="120" viewbox="0 0 120 120" fill="white" opacity="0.9"><rect x="30" y="20" width="60" height="80" rx="8" stroke="white" stroke-width="3" fill="none" /> <text x="60" y="70" text-anchor="middle" font-size="24" fill="white" font-weight="bold">
           TEE
          </text>
         </svg>
        </div>
        <div style="padding: 1.5rem;">
         <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Graphic Tee</h4>
         <p style="color: var(--text-color); opacity: 0.7; margin-bottom: 1rem;">Bold statement piece</p>
         <div style="display: flex; justify-content: space-between; align-items: center;"><span style="font-size: 1.5rem; font-weight: 700; color: var(--primary-action);">$35</span> <button class="add-to-cart btn-secondary" data-product="Graphic Tee" data-price="35" style="padding: 0.5rem 1.25rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">Add to Cart</button>
         </div>
        </div>
       </div><!-- Product 3 -->
       <div class="product-card" style="background-color: var(--surface-color); border-radius: 16px; overflow: hidden; cursor: pointer;">
        <div style="width: 100%; height: 300px; background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); display: flex; align-items: center; justify-content: center;">
         <svg width="120" height="120" viewbox="0 0 120 120" fill="white" opacity="0.9"><path d="M40 30h40v15H40zM35 45h50v50H35z" /> <text x="60" y="75" text-anchor="middle" font-size="20" fill="white" font-weight="bold">
           JOGGERS
          </text>
         </svg>
        </div>
        <div style="padding: 1.5rem;">
         <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Comfort Joggers</h4>
         <p style="color: var(--text-color); opacity: 0.7; margin-bottom: 1rem;">Ultimate comfort fit</p>
         <div style="display: flex; justify-content: space-between; align-items: center;"><span style="font-size: 1.5rem; font-weight: 700; color: var(--primary-action);">$49</span> <button class="add-to-cart btn-secondary" data-product="Comfort Joggers" data-price="49" style="padding: 0.5rem 1.25rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">Add to Cart</button>
         </div>
        </div>
       </div>
      </div>
     </div>
    </section><!-- Why Choose Us -->
    <section style="width: 100%; padding: 4rem 1.5rem; background-color: var(--secondary-surface);">
     <div style="max-width: 1200px; margin: 0 auto;">
      <h3 style="font-size: 2rem; font-weight: 700; color: var(--text-color); margin-bottom: 3rem; text-align: center;">Why VIBE?</h3>
      <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 2rem;">
       <div style="text-align: center; padding: 2rem;">
        <div style="width: 80px; height: 80px; margin: 0 auto 1rem; background-color: var(--primary-action); border-radius: 50%; display: flex; align-items: center; justify-content: center;"><span style="font-size: 2.5rem;">🚀</span>
        </div>
        <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Fast Shipping</h4>
        <p style="color: var(--text-color); opacity: 0.7;">Get your order in 2-3 days</p>
       </div>
       <div style="text-align: center; padding: 2rem;">
        <div style="width: 80px; height: 80px; margin: 0 auto 1rem; background-color: var(--primary-action); border-radius: 50%; display: flex; align-items: center; justify-content: center;"><span style="font-size: 2.5rem;">✨</span>
        </div>
        <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Premium Quality</h4>
        <p style="color: var(--text-color); opacity: 0.7;">Only the best materials</p>
       </div>
       <div style="text-align: center; padding: 2rem;">
        <div style="width: 80px; height: 80px; margin: 0 auto 1rem; background-color: var(--primary-action); border-radius: 50%; display: flex; align-items: center; justify-content: center;"><span style="font-size: 2.5rem;">💯</span>
        </div>
        <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">100% Authentic</h4>
        <p style="color: var(--text-color); opacity: 0.7;">Original designs guaranteed</p>
       </div>
      </div>
     </div>
    </section>
   </div><!-- Shop Page -->
   <div id="page-shop" class="page">
    <section style="width: 100%; padding: 4rem 1.5rem;">
     <div style="max-width: 1200px; margin: 0 auto;">
      <h2 style="font-size: 2.5rem; font-weight: 700; color: var(--text-color); margin-bottom: 1rem;">Shop All</h2>
      <p style="font-size: 1.125rem; color: var(--text-color); opacity: 0.8; margin-bottom: 3rem;">Explore our complete collection</p><!-- Filter Buttons -->
      <div style="display: flex; gap: 1rem; margin-bottom: 3rem; flex-wrap: wrap;"><button class="filter-btn active btn-secondary" data-filter="all" style="padding: 0.75rem 1.5rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">All</button> <button class="filter-btn btn-secondary" data-filter="tops" style="padding: 0.75rem 1.5rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer; opacity: 0.7;">Tops</button> <button class="filter-btn btn-secondary" data-filter="bottoms" style="padding: 0.75rem 1.5rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer; opacity: 0.7;">Bottoms</button> <button class="filter-btn btn-secondary" data-filter="accessories" style="padding: 0.75rem 1.5rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer; opacity: 0.7;">Accessories</button>
      </div>
      <div id="shop-products" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 2rem;"><!-- Products will be rendered here -->
      </div>
     </div>
    </section>
   </div><!-- Collections Page -->
   <div id="page-collections" class="page">
    <section style="width: 100%; padding: 4rem 1.5rem;">
     <div style="max-width: 1200px; margin: 0 auto;">
      <h2 style="font-size: 2.5rem; font-weight: 700; color: var(--text-color); margin-bottom: 1rem;">Collections</h2>
      <p style="font-size: 1.125rem; color: var(--text-color); opacity: 0.8; margin-bottom: 3rem;">Curated styles for every mood</p>
      <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 2rem;"><!-- Collection 1 -->
       <div style="background-color: var(--surface-color); border-radius: 16px; overflow: hidden; cursor: pointer; transition: transform 0.3s ease;">
        <div style="width: 100%; height: 250px; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); display: flex; align-items: center; justify-content: center; flex-direction: column; padding: 2rem;">
         <h3 style="font-size: 2rem; font-weight: 700; color: white; margin-bottom: 0.5rem;">Summer Vibes</h3>
         <p style="color: white; opacity: 0.9; text-align: center;">Bright colors and breezy styles</p>
        </div>
        <div style="padding: 1.5rem;"><button class="btn-primary" style="width: 100%; padding: 0.75rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">View Collection</button>
        </div>
       </div><!-- Collection 2 -->
       <div style="background-color: var(--surface-color); border-radius: 16px; overflow: hidden; cursor: pointer; transition: transform 0.3s ease;">
        <div style="width: 100%; height: 250px; background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); display: flex; align-items: center; justify-content: center; flex-direction: column; padding: 2rem;">
         <h3 style="font-size: 2rem; font-weight: 700; color: white; margin-bottom: 0.5rem;">Street Style</h3>
         <p style="color: white; opacity: 0.9; text-align: center;">Urban edge meets comfort</p>
        </div>
        <div style="padding: 1.5rem;"><button class="btn-primary" style="width: 100%; padding: 0.75rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">View Collection</button>
        </div>
       </div><!-- Collection 3 -->
       <div style="background-color: var(--surface-color); border-radius: 16px; overflow: hidden; cursor: pointer; transition: transform 0.3s ease;">
        <div style="width: 100%; height: 250px; background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); display: flex; align-items: center; justify-content: center; flex-direction: column; padding: 2rem;">
         <h3 style="font-size: 2rem; font-weight: 700; color: white; margin-bottom: 0.5rem;">Athleisure</h3>
         <p style="color: white; opacity: 0.9; text-align: center;">Performance meets style</p>
        </div>
        <div style="padding: 1.5rem;"><button class="btn-primary" style="width: 100%; padding: 0.75rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">View Collection</button>
        </div>
       </div>
      </div>
     </div>
    </section>
   </div><!-- About Page -->
   <div id="page-about" class="page">
    <section style="width: 100%; padding: 4rem 1.5rem;">
     <div style="max-width: 900px; margin: 0 auto;">
      <h2 id="about-title" style="font-size: 2.5rem; font-weight: 700; color: var(--text-color); margin-bottom: 1rem; text-align: center;">About VIBE</h2>
      <p id="about-description" style="font-size: 1.25rem; color: var(--text-color); opacity: 0.8; margin-bottom: 3rem; text-align: center;">Where style meets individuality</p>
      <div style="background-color: var(--surface-color); border-radius: 16px; padding: 3rem; margin-bottom: 3rem;">
       <h3 style="font-size: 1.75rem; font-weight: 600; color: var(--text-color); margin-bottom: 1rem;">Our Story</h3>
       <p style="font-size: 1.125rem; color: var(--text-color); opacity: 0.8; line-height: 1.8; margin-bottom: 1.5rem;">Founded in 2024, VIBE started with a simple mission: to create fashion that speaks to the next generation. We believe clothing is more than just fabric – it's a form of self-expression, a way to show the world who you are.</p>
       <p style="font-size: 1.125rem; color: var(--text-color); opacity: 0.8; line-height: 1.8;">Every piece in our collection is designed with you in mind. From bold graphics to minimalist essentials, we've got the pieces you need to create your perfect look. We're committed to quality, sustainability, and keeping our designs fresh and exciting.</p>
      </div>
      <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 2rem;">
       <div style="background-color: var(--surface-color); border-radius: 16px; padding: 2rem; text-align: center;">
        <div style="font-size: 3rem; margin-bottom: 1rem;">
         🌍
        </div>
        <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Sustainable</h4>
        <p style="color: var(--text-color); opacity: 0.7;">Eco-friendly materials and ethical production</p>
       </div>
       <div style="background-color: var(--surface-color); border-radius: 16px; padding: 2rem; text-align: center;">
        <div style="font-size: 3rem; margin-bottom: 1rem;">
         💪
        </div>
        <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Quality First</h4>
        <p style="color: var(--text-color); opacity: 0.7;">Premium fabrics built to last</p>
       </div>
       <div style="background-color: var(--surface-color); border-radius: 16px; padding: 2rem; text-align: center;">
        <div style="font-size: 3rem; margin-bottom: 1rem;">
         🎨
        </div>
        <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Creative</h4>
        <p style="color: var(--text-color); opacity: 0.7;">Unique designs you won't find anywhere else</p>
       </div>
      </div>
     </div>
    </section>
   </div><!-- Contact Page -->
   <div id="page-contact" class="page">
    <section style="width: 100%; padding: 4rem 1.5rem;">
     <div style="max-width: 800px; margin: 0 auto;">
      <h2 style="font-size: 2.5rem; font-weight: 700; color: var(--text-color); margin-bottom: 1rem; text-align: center;">Get In Touch</h2>
      <p style="font-size: 1.125rem; color: var(--text-color); opacity: 0.8; margin-bottom: 3rem; text-align: center;">We'd love to hear from you!</p>
      <div style="background-color: var(--surface-color); border-radius: 16px; padding: 3rem; margin-bottom: 2rem;">
       <form id="contact-form">
        <div style="margin-bottom: 1.5rem;"><label for="contact-name" style="display: block; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Name</label> <input type="text" id="contact-name" required style="width: 100%; padding: 0.75rem 1rem; border: 2px solid var(--secondary-surface); border-radius: 8px; font-size: 1rem; background-color: var(--bg-color); color: var(--text-color);">
        </div>
        <div style="margin-bottom: 1.5rem;"><label for="contact-email-input" style="display: block; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Email</label> <input type="email" id="contact-email-input" required style="width: 100%; padding: 0.75rem 1rem; border: 2px solid var(--secondary-surface); border-radius: 8px; font-size: 1rem; background-color: var(--bg-color); color: var(--text-color);">
        </div>
        <div style="margin-bottom: 1.5rem;"><label for="contact-message" style="display: block; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">Message</label> <textarea id="contact-message" rows="5" required style="width: 100%; padding: 0.75rem 1rem; border: 2px solid var(--secondary-surface); border-radius: 8px; font-size: 1rem; background-color: var(--bg-color); color: var(--text-color); resize: vertical;"></textarea>
        </div><button type="submit" class="btn-primary" style="width: 100%; padding: 1rem; border: none; border-radius: 25px; font-size: 1.125rem; font-weight: 600; color: white; cursor: pointer;">Send Message</button>
       </form>
       <div id="form-success" style="display: none; margin-top: 1rem; padding: 1rem; background-color: var(--primary-action); color: white; border-radius: 8px; text-align: center;">
        Thanks! We'll get back to you soon! 🎉
       </div>
      </div>
      <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 2rem;">
       <div style="text-align: center; padding: 1.5rem; background-color: var(--surface-color); border-radius: 12px;">
        <div style="font-size: 2.5rem; margin-bottom: 0.5rem;">
         📧
        </div>
        <h4 style="font-size: 1rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.25rem;">Email</h4>
        <p id="contact-email" style="color: var(--text-color); opacity: 0.7;">hello@vibe.fashion</p>
       </div>
       <div style="text-align: center; padding: 1.5rem; background-color: var(--surface-color); border-radius: 12px;">
        <div style="font-size: 2.5rem; margin-bottom: 0.5rem;">
         📱
        </div>
        <h4 style="font-size: 1rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.25rem;">Phone</h4>
        <p id="contact-phone" style="color: var(--text-color); opacity: 0.7;">+1 (555) 123-4567</p>
       </div>
       <div style="text-align: center; padding: 1.5rem; background-color: var(--surface-color); border-radius: 12px;">
        <div style="font-size: 2.5rem; margin-bottom: 0.5rem;">
         💬
        </div>
        <h4 style="font-size: 1rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.25rem;">Social</h4>
        <p style="color: var(--text-color); opacity: 0.7;">@vibefashion</p>
       </div>
      </div>
     </div>
    </section>
   </div><!-- Cart Modal -->
   <div id="cart-modal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.5); z-index: 1000; align-items: center; justify-content: center;">
    <div style="background-color: var(--surface-color); border-radius: 16px; padding: 2rem; max-width: 500px; width: 90%; max-height: 80%; overflow-y: auto;">
     <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
      <h3 style="font-size: 1.5rem; font-weight: 700; color: var(--text-color);">Your Cart</h3><button id="close-cart" style="background: none; border: none; font-size: 1.5rem; cursor: pointer; color: var(--text-color);">✕</button>
     </div>
     <div id="cart-items" style="margin-bottom: 1.5rem;"><!-- Cart items will be rendered here -->
     </div>
     <div style="border-top: 2px solid var(--secondary-surface); padding-top: 1rem; margin-bottom: 1rem;">
      <div style="display: flex; justify-content: space-between; align-items: center;"><span style="font-size: 1.25rem; font-weight: 600; color: var(--text-color);">Total:</span> <span id="cart-total" style="font-size: 1.5rem; font-weight: 700; color: var(--primary-action);">$0</span>
      </div>
     </div><button class="btn-primary" style="width: 100%; padding: 1rem; border: none; border-radius: 25px; font-size: 1.125rem; font-weight: 600; color: white; cursor: pointer;">Checkout</button>
    </div>
   </div><!-- Footer -->
   <footer style="width: 100%; background-color: var(--surface-color); padding: 3rem 1.5rem; margin-top: 4rem;">
    <div style="max-width: 1200px; margin: 0 auto; text-align: center;">
     <div style="display: flex; align-items: center; justify-content: center; gap: 0.5rem; margin-bottom: 1rem;">
      <svg width="32" height="32" viewbox="0 0 32 32" style="fill: var(--primary-action);"><path d="M16 2L4 8v8c0 7.732 5.16 14.984 12 16.836C22.84 30.984 28 23.732 28 16V8L16 2zm0 4.236L24 10v6c0 5.96-3.876 11.524-8 13.164C11.876 27.524 8 21.96 8 16v-6l8-3.764z" /> <circle cx="16" cy="16" r="4" />
      </svg>
      <h3 id="footer-site-name" style="font-size: 1.5rem; font-weight: 700; color: var(--text-color);">VIBE</h3>
     </div>
     <p id="tagline" style="color: var(--text-color); opacity: 0.7; margin-bottom: 1.5rem;">Express yourself, be unique</p>
     <div style="display: flex; gap: 1.5rem; justify-content: center; margin-bottom: 1.5rem; flex-wrap: wrap;"><a href="#home" style="color: var(--text-color); text-decoration: none; opacity: 0.8;">Home</a> <a href="#shop" style="color: var(--text-color); text-decoration: none; opacity: 0.8;">Shop</a> <a href="#collections" style="color: var(--text-color); text-decoration: none; opacity: 0.8;">Collections</a> <a href="#about" style="color: var(--text-color); text-decoration: none; opacity: 0.8;">About</a> <a href="#contact" style="color: var(--text-color); text-decoration: none; opacity: 0.8;">Contact</a>
     </div>
     <p style="color: var(--text-color); opacity: 0.6; font-size: 0.875rem;">© 2024 VIBE Fashion. All rights reserved.</p>
    </div>
   </footer>
  </div>
  <script>
    const defaultConfig = {
      background_color: '#f8f9fa',
      surface_color: '#ffffff',
      secondary_surface_color: '#f0f0f0',
      text_color: '#1a1a1a',
      primary_action_color: '#ff6b6b',
      secondary_action_color: '#4ecdc4',
      font_family: 'Inter',
      font_size: 16,
      site_name: 'VIBE',
      tagline: 'Express yourself, be unique',
      hero_title: 'Your Style, Your Vibe',
      hero_subtitle: 'Discover the latest trends in streetwear and express yourself',
      cta_button: 'Shop Now',
      about_title: 'About VIBE',
      about_description: 'Where style meets individuality',
      contact_email: 'hello@vibe.fashion',
      contact_phone: '+1 (555) 123-4567'
    };

    // Product database
    const products = [
      { id: 1, name: 'Classic Hoodie', price: 59, category: 'tops', gradient: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)', icon: 'HOODIE' },
      { id: 2, name: 'Graphic Tee', price: 35, category: 'tops', gradient: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)', icon: 'TEE' },
      { id: 3, name: 'Comfort Joggers', price: 49, category: 'bottoms', gradient: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)', icon: 'JOGGERS' },
      { id: 4, name: 'Oversized Sweatshirt', price: 65, category: 'tops', gradient: 'linear-gradient(135deg, #a8edea 0%, #fed6e3 100%)', icon: 'SWEAT' },
      { id: 5, name: 'Cargo Pants', price: 69, category: 'bottoms', gradient: 'linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%)', icon: 'CARGO' },
      { id: 6, name: 'Bucket Hat', price: 29, category: 'accessories', gradient: 'linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%)', icon: 'HAT' },
      { id: 7, name: 'Zip Hoodie', price: 62, category: 'tops', gradient: 'linear-gradient(135deg, #fbc2eb 0%, #a6c1ee 100%)', icon: 'ZIP' },
      { id: 8, name: 'Track Pants', price: 54, category: 'bottoms', gradient: 'linear-gradient(135deg, #fdcbf1 0%, #e6dee9 100%)', icon: 'TRACK' },
      { id: 9, name: 'Crossbody Bag', price: 45, category: 'accessories', gradient: 'linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 100%)', icon: 'BAG' }
    ];

    let cart = [];
    let currentFilter = 'all';

    function updateCSSVariables(config) {
      const root = document.documentElement;
      root.style.setProperty('--bg-color', config.background_color || defaultConfig.background_color);
      root.style.setProperty('--surface-color', config.surface_color || defaultConfig.surface_color);
      root.style.setProperty('--secondary-surface', config.secondary_surface_color || defaultConfig.secondary_surface_color);
      root.style.setProperty('--text-color', config.text_color || defaultConfig.text_color);
      root.style.setProperty('--primary-action', config.primary_action_color || defaultConfig.primary_action_color);
      root.style.setProperty('--secondary-action', config.secondary_action_color || defaultConfig.secondary_action_color);
      root.style.setProperty('--font-family', config.font_family || defaultConfig.font_family);
      
      const primaryHover = adjustColor(config.primary_action_color || defaultConfig.primary_action_color, -20);
      const secondaryHover = adjustColor(config.secondary_action_color || defaultConfig.secondary_action_color, -20);
      root.style.setProperty('--primary-action-hover', primaryHover);
      root.style.setProperty('--secondary-action-hover', secondaryHover);
    }

    function adjustColor(color, amount) {
      const num = parseInt(color.replace('#', ''), 16);
      const r = Math.max(0, Math.min(255, (num >> 16) + amount));
      const g = Math.max(0, Math.min(255, ((num >> 8) & 0x00FF) + amount));
      const b = Math.max(0, Math.min(255, (num & 0x0000FF) + amount));
      return '#' + ((r << 16) | (g << 8) | b).toString(16).padStart(6, '0');
    }

    function applyFontSize(config) {
      const baseSize = config.font_size || defaultConfig.font_size;
      document.body.style.fontSize = `${baseSize}px`;
    }

    function renderShopProducts(filter = 'all') {
      const container = document.getElementById('shop-products');
      const filteredProducts = filter === 'all' ? products : products.filter(p => p.category === filter);
      
      container.innerHTML = filteredProducts.map(product => `
        <div class="product-card" style="background-color: var(--surface-color); border-radius: 16px; overflow: hidden; cursor: pointer;">
          <div style="width: 100%; height: 300px; background: ${product.gradient}; display: flex; align-items: center; justify-content: center;">
            <svg width="120" height="120" viewBox="0 0 120 120" fill="white" opacity="0.9">
              <text x="60" y="70" text-anchor="middle" font-size="20" fill="white" font-weight="bold">${product.icon}</text>
            </svg>
          </div>
          <div style="padding: 1.5rem;">
            <h4 style="font-size: 1.25rem; font-weight: 600; color: var(--text-color); margin-bottom: 0.5rem;">${product.name}</h4>
            <p style="color: var(--text-color); opacity: 0.7; margin-bottom: 1rem;">Premium quality</p>
            <div style="display: flex; justify-content: space-between; align-items: center;">
              <span style="font-size: 1.5rem; font-weight: 700; color: var(--primary-action);">$${product.price}</span>
              <button class="add-to-cart btn-secondary" data-product="${product.name}" data-price="${product.price}" style="padding: 0.5rem 1.25rem; border: none; border-radius: 25px; font-weight: 600; color: white; cursor: pointer;">Add to Cart</button>
            </div>
          </div>
        </div>
      `).join('');

      attachCartListeners();
    }

    function updateCartCount() {
      const count = cart.reduce((sum, item) => sum + item.quantity, 0);
      document.getElementById('cart-count').textContent = count;
    }

    function renderCart() {
      const container = document.getElementById('cart-items');
      
      if (cart.length === 0) {
        container.innerHTML = '<p style="text-align: center; color: var(--text-color); opacity: 0.7; padding: 2rem;">Your cart is empty</p>';
        document.getElementById('cart-total').textContent = '$0';
        return;
      }

      container.innerHTML = cart.map((item, index) => `
        <div style="display: flex; justify-content: space-between; align-items: center; padding: 1rem; background-color: var(--bg-color); border-radius: 8px; margin-bottom: 0.75rem;">
          <div>
            <h4 style="font-weight: 600; color: var(--text-color);">${item.name}</h4>
            <p style="color: var(--text-color); opacity: 0.7;">$${item.price} × ${item.quantity}</p>
          </div>
          <div style="display: flex; align-items: center; gap: 0.75rem;">
            <button class="decrease-qty" data-index="${index}" style="width: 30px; height: 30px; border: none; border-radius: 50%; background-color: var(--secondary-surface); color: var(--text-color); cursor: pointer; font-weight: 600;">-</button>
            <span style="color: var(--text-color); font-weight: 600;">${item.quantity}</span>
            <button class="increase-qty" data-index="${index}" style="width: 30px; height: 30px; border: none; border-radius: 50%; background-color: var(--secondary-surface); color: var(--text-color); cursor: pointer; font-weight: 600;">+</button>
            <button class="remove-item" data-index="${index}" style="background: none; border: none; color: var(--text-color); opacity: 0.5; cursor: pointer; font-size: 1.25rem; margin-left: 0.5rem;">✕</button>
          </div>
        </div>
      `).join('');

      const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
      document.getElementById('cart-total').textContent = `$${total}`;

      attachCartItemListeners();
    }

    function attachCartListeners() {
      document.querySelectorAll('.add-to-cart').forEach(btn => {
        btn.addEventListener('click', function(e) {
          e.stopPropagation();
          const productName = this.dataset.product;
          const price = parseInt(this.dataset.price);
          
          const existingItem = cart.find(item => item.name === productName);
          if (existingItem) {
            existingItem.quantity++;
          } else {
            cart.push({ name: productName, price, quantity: 1 });
          }
          
          updateCartCount();
          
          this.textContent = 'Added! ✓';
          this.style.backgroundColor = 'var(--primary-action)';
          setTimeout(() => {
            this.textContent = 'Add to Cart';
            this.style.backgroundColor = '';
          }, 1000);
        });
      });
    }

    function attachCartItemListeners() {
      document.querySelectorAll('.increase-qty').forEach(btn => {
        btn.addEventListener('click', function() {
          const index = parseInt(this.dataset.index);
          cart[index].quantity++;
          updateCartCount();
          renderCart();
        });
      });

      document.querySelectorAll('.decrease-qty').forEach(btn => {
        btn.addEventListener('click', function() {
          const index = parseInt(this.dataset.index);
          if (cart[index].quantity > 1) {
            cart[index].quantity--;
          } else {
            cart.splice(index, 1);
          }
          updateCartCount();
          renderCart();
        });
      });

      document.querySelectorAll('.remove-item').forEach(btn => {
        btn.addEventListener('click', function() {
          const index = parseInt(this.dataset.index);
          cart.splice(index, 1);
          updateCartCount();
          renderCart();
        });
      });
    }

    // Navigation
    document.querySelectorAll('.nav-link').forEach(link => {
      link.addEventListener('click', function(e) {
        e.preventDefault();
        const page = this.dataset.page;
        
        document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
        document.getElementById(`page-${page}`).classList.add('active');
        
        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
        document.querySelectorAll(`.nav-link[data-page="${page}"]`).forEach(l => l.classList.add('active'));
        
        if (page === 'shop') {
          renderShopProducts(currentFilter);
        }
        
        const mobileMenu = document.getElementById('mobile-menu');
        mobileMenu.classList.remove('active');
        
        window.scrollTo({ top: 0, behavior: 'smooth' });
      });
    });

    // Mobile menu toggle
    document.getElementById('mobile-menu-btn').addEventListener('click', function() {
      document.getElementById('mobile-menu').classList.toggle('active');
    });

    // CTA button
    document.getElementById('cta-button').addEventListener('click', function() {
      document.querySelector('.nav-link[data-page="shop"]').click();
    });

    // Filter buttons
    document.querySelectorAll('.filter-btn').forEach(btn => {
      btn.addEventListener('click', function() {
        const filter = this.dataset.filter;
        currentFilter = filter;
        
        document.querySelectorAll('.filter-btn').forEach(b => {
          b.classList.remove('active');
          b.style.opacity = '0.7';
        });
        this.classList.add('active');
        this.style.opacity = '1';
        
        renderShopProducts(filter);
      });
    });

    // Cart modal
    document.getElementById('cart-btn').addEventListener('click', function() {
      document.getElementById('cart-modal').style.display = 'flex';
      renderCart();
    });

    document.getElementById('close-cart').addEventListener('click', function() {
      document.getElementById('cart-modal').style.display = 'none';
    });

    document.getElementById('cart-modal').addEventListener('click', function(e) {
      if (e.target === this) {
        this.style.display = 'none';
      }
    });

    // Contact form
    document.getElementById('contact-form').addEventListener('submit', function(e) {
      e.preventDefault();
      document.getElementById('form-success').style.display = 'block';
      this.reset();
      setTimeout(() => {
        document.getElementById('form-success').style.display = 'none';
      }, 3000);
    });

    // Initialize
    attachCartListeners();
    updateCSSVariables(defaultConfig);
    applyFontSize(defaultConfig);

    // Element SDK Implementation
    async function onConfigChange(config) {
      updateCSSVariables(config);
      applyFontSize(config);
      
      const customFont = config.font_family || defaultConfig.font_family;
      const baseFontStack = '-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif';
      document.body.style.fontFamily = `${customFont}, ${baseFontStack}`;
      
      document.getElementById('site-name').textContent = config.site_name || defaultConfig.site_name;
      document.getElementById('footer-site-name').textContent = config.site_name || defaultConfig.site_name;
      document.getElementById('tagline').textContent = config.tagline || defaultConfig.tagline;
      document.getElementById('hero-title').textContent = config.hero_title || defaultConfig.hero_title;
      document.getElementById('hero-subtitle').textContent = config.hero_subtitle || defaultConfig.hero_subtitle;
      document.getElementById('cta-button').textContent = config.cta_button || defaultConfig.cta_button;
      document.getElementById('about-title').textContent = config.about_title || defaultConfig.about_title;
      document.getElementById('about-description').textContent = config.about_description || defaultConfig.about_description;
      document.getElementById('contact-email').textContent = config.contact_email || defaultConfig.contact_email;
      document.getElementById('contact-phone').textContent = config.contact_phone || defaultConfig.contact_phone;
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => {
                config.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => config.surface_color || defaultConfig.surface_color,
              set: (value) => {
                config.surface_color = value;
                window.elementSdk.setConfig({ surface_color: value });
              }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => {
                config.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            },
            {
              get: () => config.primary_action_color || defaultConfig.primary_action_color,
              set: (value) => {
                config.primary_action_color = value;
                window.elementSdk.setConfig({ primary_action_color: value });
              }
            },
            {
              get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
              set: (value) => {
                config.secondary_action_color = value;
                window.elementSdk.setConfig({ secondary_action_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => config.font_family || defaultConfig.font_family,
            set: (value) => {
              config.font_family = value;
              window.elementSdk.setConfig({ font_family: value });
            }
          },
          fontSizeable: {
            get: () => config.font_size || defaultConfig.font_size,
            set: (value) => {
              config.font_size = value;
              window.elementSdk.setConfig({ font_size: value });
            }
          }
        }),
        mapToEditPanelValues: (config) => new Map([
          ['site_name', config.site_name || defaultConfig.site_name],
          ['tagline', config.tagline || defaultConfig.tagline],
          ['hero_title', config.hero_title || defaultConfig.hero_title],
          ['hero_subtitle', config.hero_subtitle || defaultConfig.hero_subtitle],
          ['cta_button', config.cta_button || defaultConfig.cta_button],
          ['about_title', config.about_title || defaultConfig.about_title],
          ['about_description', config.about_description || defaultConfig.about_description],
          ['contact_email', config.contact_email || defaultConfig.contact_email],
          ['contact_phone', config.contact_phone || defaultConfig.contact_phone]
        ])
      });
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9a399e2967313eb1',t:'MTc2Mzk5NDc2OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
