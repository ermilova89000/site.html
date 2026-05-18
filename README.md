<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ФармаМед — Информационная система аптеки</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;500;600;700;800&family=Rubik:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --deep-teal: #0D3B3B;
            --teal: #145A5A;
            --mint: #A7D0CD;
            --soft-mint: #EFF7F5;
            --coral: #F97B5C;
            --coral-light: #FFE8E0;
            --cream: #FFF9F5;
            --white: #FFFFFF;
            --gray-soft: #F2F4F8;
            --gray-border: #E0E4EA;
            --text-dark: #1C2B36;
            --text-mid: #4F5B66;
            --text-light: #8896A3;
            --shadow-card: 0 8px 24px rgba(13, 59, 59, 0.06), 0 2px 8px rgba(13, 59, 59, 0.04);
            --shadow-hover: 0 16px 32px rgba(13, 59, 59, 0.10), 0 4px 12px rgba(13, 59, 59, 0.06);
            --radius-blob: 30% 70% 50% 50% / 30% 30% 70% 70%;
            --transition-smooth: 0.25s cubic-bezier(0.2, 0.9, 0.4, 1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Nunito', sans-serif;
            background: linear-gradient(165deg, #F6FAF9 0%, #F2F6F5 30%, #EDF4F2 100%);
            color: var(--text-dark);
            line-height: 1.5;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            background-attachment: fixed;
        }

        body::before {
            content: '';
            position: fixed;
            top: -300px;
            right: -200px;
            width: 800px;
            height: 800px;
            background: radial-gradient(circle at 30% 40%, rgba(167, 208, 205, 0.15) 0%, transparent 70%);
            border-radius: 50%;
            z-index: 0;
            pointer-events: none;
        }

        .header {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border-bottom: 1px solid rgba(255,255,255,0.4);
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 20px rgba(13, 59, 59, 0.04);
            padding: 0 24px;
            height: 70px;
            display: flex;
            align-items: center;
            font-family: 'Rubik', sans-serif;
        }
        .header-inner {
            max-width: 1300px;
            margin: 0 auto;
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 24px;
        }
        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.6rem;
            font-weight: 700;
            color: var(--deep-teal);
            text-decoration: none;
            cursor: pointer;
            letter-spacing: -0.5px;
        }
        .logo-icon {
            width: 44px;
            height: 44px;
            background: linear-gradient(135deg, var(--teal), var(--deep-teal));
            border-radius: 14px 4px 14px 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
            box-shadow: 0 4px 10px rgba(20, 90, 90, 0.3);
            transform: rotate(-3deg);
        }
        .nav {
            display: flex;
            gap: 4px;
            flex-wrap: wrap;
        }
        .nav-btn {
            padding: 10px 18px;
            border: none;
            background: transparent;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.95rem;
            font-weight: 600;
            color: var(--text-mid);
            transition: all var(--transition-smooth);
            white-space: nowrap;
            font-family: inherit;
        }
        .nav-btn:hover {
            background: rgba(167, 208, 205, 0.25);
            color: var(--teal);
        }
        .nav-btn.active {
            background: var(--deep-teal);
            color: white;
            box-shadow: 0 4px 12px rgba(13, 59, 59, 0.3);
        }
        .cart-badge {
            background: var(--coral);
            color: white;
            border-radius: 50%;
            padding: 2px 7px;
            font-size: 0.7rem;
            font-weight: 800;
            margin-left: 4px;
            display: inline-block;
            min-width: 20px;
            text-align: center;
        }
        .header-actions {
            display: flex;
            align-items: center;
            gap: 16px;
        }
        .btn-icon {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            border: 2px solid var(--mint);
            background: var(--white);
            cursor: pointer;
            font-size: 1.2rem;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all var(--transition-smooth);
            position: relative;
            color: var(--teal);
        }
        .btn-icon:hover {
            background: var(--soft-mint);
            border-color: var(--teal);
            transform: translateY(-2px);
        }
        .cart-count {
            position: absolute;
            top: -6px;
            right: -6px;
            background: var(--coral);
            color: white;
            border-radius: 50%;
            width: 22px;
            height: 22px;
            font-size: 0.75rem;
            font-weight: 800;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 2px solid white;
        }
        .user-greeting {
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 600;
            font-size: 0.9rem;
            color: var(--deep-teal);
            background: var(--soft-mint);
            padding: 6px 16px;
            border-radius: 40px;
        }
        .user-greeting .user-name {
            color: var(--deep-teal);
            font-weight: 700;
        }
        .btn-logout {
            background: none;
            border: none;
            color: var(--coral);
            cursor: pointer;
            font-size: 0.85rem;
            font-weight: 700;
            padding: 4px 10px;
            border-radius: 20px;
            transition: background var(--transition-smooth);
            margin-left: 4px;
        }
        .btn-logout:hover {
            background: var(--coral-light);
        }
        .btn-auth {
            padding: 10px 22px;
            background: var(--coral);
            color: white;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 700;
            font-size: 0.9rem;
            transition: all var(--transition-smooth);
            font-family: inherit;
            box-shadow: 0 4px 10px rgba(249, 123, 92, 0.3);
        }
        .btn-auth:hover {
            background: #E8694B;
            transform: translateY(-2px);
        }

        .main {
            flex: 1;
            max-width: 1300px;
            margin: 0 auto;
            padding: 40px 24px;
            width: 100%;
            position: relative;
            z-index: 1;
        }
        .page {
            display: none;
            animation: fadeSlideIn 0.4s cubic-bezier(0.2, 0.9, 0.4, 1);
        }
        .page.active { display: block; }
        @keyframes fadeSlideIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .hero {
            background: linear-gradient(125deg, #0D3B3B 0%, #1A5C5C 50%, #217575 100%);
            border-radius: 60px 20px 60px 20px;
            padding: 56px 48px;
            color: white;
            margin-bottom: 48px;
            display: flex;
            gap: 40px;
            align-items: center;
            flex-wrap: wrap;
            position: relative;
            overflow: hidden;
            box-shadow: 0 30px 50px rgba(13, 59, 59, 0.25);
        }
        .hero::before {
            content: '';
            position: absolute;
            right: -80px;
            bottom: -80px;
            width: 350px;
            height: 350px;
            background: rgba(255,255,255,0.03);
            border-radius: var(--radius-blob);
            pointer-events: none;
        }
        .hero::after {
            content: '';
            position: absolute;
            left: -40px;
            top: -40px;
            width: 180px;
            height: 180px;
            background: rgba(255,255,255,0.05);
            border-radius: 50%;
            pointer-events: none;
        }
        .hero-text { flex: 1; min-width: 250px; position: relative; z-index: 1; }
        .hero h1 {
            font-family: 'Rubik', sans-serif;
            font-size: 2.8rem;
            font-weight: 700;
            margin-bottom: 16px;
            letter-spacing: -0.8px;
            line-height: 1.2;
        }
        .hero p { font-size: 1.15rem; opacity: 0.9; margin-bottom: 32px; max-width: 500px; font-weight: 500; }
        .hero-search { display: flex; gap: 12px; max-width: 480px; }
        .hero-search input {
            flex: 1;
            padding: 16px 22px;
            border: none;
            border-radius: 30px;
            font-size: 1rem;
            outline: none;
            font-family: inherit;
            background: rgba(255,255,255,0.95);
            box-shadow: 0 8px 20px rgba(0,0,0,0.1);
        }
        .hero-search button {
            padding: 16px 28px;
            background: var(--coral);
            color: white;
            border: none;
            border-radius: 30px;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            transition: all var(--transition-smooth);
            font-family: inherit;
            white-space: nowrap;
            box-shadow: 0 6px 18px rgba(249, 123, 92, 0.4);
        }
        .hero-search button:hover { background: #E8694B; transform: translateY(-2px); }
        .hero-img {
            flex: 0 0 180px;
            text-align: center;
            font-size: 8rem;
            position: relative;
            z-index: 1;
            filter: drop-shadow(0 20px 30px rgba(0,0,0,0.25));
        }

        .section-title {
            font-family: 'Rubik', sans-serif;
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 28px;
            color: var(--deep-teal);
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .section-title .icon { color: var(--coral); font-size: 2rem; }

        .categories { display: flex; gap: 10px; flex-wrap: wrap; margin-bottom: 32px; }
        .category-chip {
            padding: 12px 24px;
            border-radius: 40px;
            border: 2px solid var(--mint);
            background: var(--white);
            cursor: pointer;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all var(--transition-smooth);
            font-family: inherit;
            color: var(--text-mid);
        }
        .category-chip:hover { border-color: var(--teal); color: var(--teal); }
        .category-chip.active {
            background: var(--deep-teal);
            color: white;
            border-color: var(--deep-teal);
            box-shadow: 0 6px 14px rgba(13, 59, 59, 0.25);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 24px;
            margin-bottom: 40px;
        }
        .product-card {
            background: var(--white);
            border-radius: 28px 12px 28px 12px;
            padding: 24px 20px 20px;
            border: 1px solid rgba(167, 208, 205, 0.3);
            transition: all var(--transition-smooth);
            cursor: pointer;
            display: flex;
            flex-direction: column;
            gap: 12px;
            position: relative;
            box-shadow: var(--shadow-card);
            overflow: hidden;
        }
        .product-card::after {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 80px;
            height: 80px;
            background: radial-gradient(circle at top right, rgba(167, 208, 205, 0.2), transparent 70%);
            border-radius: 50%;
            pointer-events: none;
        }
        .product-card:hover {
            transform: translateY(-6px) scale(1.02);
            box-shadow: var(--shadow-hover);
            border-color: var(--mint);
        }
        .product-badge {
            position: absolute;
            top: 16px;
            left: 16px;
            padding: 5px 14px;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 800;
            background: var(--coral-light);
            color: #C13F27;
            z-index: 1;
        }
        .product-badge.promo { background: #FFF2D9; color: #B45309; }
        /* Изображение товара */
        .product-img {
            width: 100%;
            height: 160px;
            object-fit: cover;
            border-radius: 20px 8px 20px 8px;
            background: #F0F6F5; /* фон на случай, если фото не загрузится */
            transition: transform var(--transition-smooth);
        }
        .product-card:hover .product-img { transform: scale(1.03); }
        .product-name {
            font-weight: 700;
            font-size: 1.05rem;
            color: var(--text-dark);
            line-height: 1.3;
            font-family: 'Rubik', sans-serif;
        }
        .product-meta { font-size: 0.8rem; color: var(--text-light); font-weight: 500; }
        .product-price-row { display: flex; align-items: center; justify-content: space-between; gap: 8px; }
        .product-price { font-size: 1.3rem; font-weight: 800; color: var(--deep-teal); }
        .product-old-price { font-size: 0.8rem; color: #B0BEC5; text-decoration: line-through; font-weight: 500; }
        .btn-add {
            padding: 10px 18px;
            background: var(--deep-teal);
            color: white;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 700;
            font-size: 0.8rem;
            transition: all var(--transition-smooth);
            font-family: inherit;
            white-space: nowrap;
            box-shadow: 0 4px 10px rgba(13, 59, 59, 0.2);
        }
        .btn-add:hover { background: var(--teal); transform: scale(1.04); }
        .btn-add.in-cart { background: #C8E6E0; color: var(--deep-teal); box-shadow: none; }

        .cart-empty { text-align: center; padding: 80px 20px; color: var(--text-light); }
        .cart-empty .icon { font-size: 5rem; display: block; margin-bottom: 20px; opacity: 0.8; }
        .cart-list { display: flex; flex-direction: column; gap: 16px; margin-bottom: 32px; }
        .cart-item {
            background: var(--white);
            border-radius: 24px 8px 24px 8px;
            padding: 18px 22px;
            display: flex;
            align-items: center;
            gap: 20px;
            border: 1px solid var(--gray-border);
            box-shadow: var(--shadow-card);
            flex-wrap: wrap;
        }
        .cart-item-img {
            width: 70px;
            height: 70px;
            object-fit: cover;
            border-radius: 18px 6px 18px 6px;
            background: var(--soft-mint);
            flex-shrink: 0;
        }
        .cart-item-info { flex: 1; min-width: 150px; }
        .cart-item-name { font-weight: 700; color: var(--text-dark); font-family: 'Rubik', sans-serif; }
        .cart-item-price { color: var(--text-mid); font-size: 0.9rem; }
        .cart-item-qty { display: flex; align-items: center; gap: 12px; }
        .cart-item-qty button {
            width: 36px; height: 36px; border-radius: 50%; border: 2px solid var(--mint);
            background: white; cursor: pointer; font-size: 1.1rem; transition: all var(--transition-smooth);
            color: var(--teal); font-weight: 700;
        }
        .cart-item-qty button:hover { background: var(--soft-mint); }
        .cart-item-qty span { font-weight: 700; min-width: 24px; text-align: center; }
        .cart-item-remove { background: none; border: none; color: var(--coral); cursor: pointer; font-size: 1.4rem; padding: 6px; }
        .cart-summary {
            background: var(--white); border-radius: 30px 10px 30px 10px; padding: 28px;
            border: 1px solid var(--gray-border); display: flex; justify-content: space-between;
            align-items: center; flex-wrap: wrap; gap: 20px; box-shadow: var(--shadow-card);
        }
        .cart-total { font-size: 1.6rem; font-weight: 800; color: var(--deep-teal); }
        .btn-checkout {
            padding: 16px 36px; background: var(--coral); color: white; border: none;
            border-radius: 40px; font-weight: 700; font-size: 1rem; cursor: pointer;
            transition: all var(--transition-smooth); font-family: inherit;
            box-shadow: 0 8px 20px rgba(249, 123, 92, 0.35);
        }
        .btn-checkout:hover { background: #E8694B; transform: translateY(-2px); }
        .btn-clear {
            padding: 12px 24px; background: #F0F4F4; color: var(--text-mid); border: 1px solid #D0D9D8;
            border-radius: 40px; cursor: pointer; font-weight: 600; transition: all var(--transition-smooth);
        }

        .about-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 24px; margin-bottom: 40px; }
        .about-card {
            background: var(--white); border-radius: 30px 12px 30px 12px; padding: 32px 24px;
            border: 1px solid rgba(167, 208, 205, 0.4); text-align: center;
            transition: all var(--transition-smooth); box-shadow: var(--shadow-card);
            position: relative; overflow: hidden;
        }
        .about-card::before {
            content: ''; position: absolute; top: -20px; right: -20px; width: 80px; height: 80px;
            background: var(--soft-mint); border-radius: 50%; opacity: 0.5; z-index: 0;
        }
        .about-card:hover { transform: translateY(-5px); box-shadow: var(--shadow-hover); }
        .about-card .icon { font-size: 3rem; margin-bottom: 16px; position: relative; z-index: 1; }
        .about-card h3 { font-weight: 700; margin-bottom: 10px; color: var(--text-dark); position: relative; }
        .about-card p { color: var(--text-mid); font-size: 0.95rem; position: relative; }

        .contacts-block {
            background: var(--white); border-radius: 30px 12px 30px 12px; padding: 32px;
            box-shadow: var(--shadow-card); display: flex; gap: 32px; flex-wrap: wrap;
        }
        .contacts-block .info h3 { font-weight: 700; margin-bottom: 16px; }
        .contacts-block .info p { margin-bottom: 8px; color: var(--text-mid); }

        .profile-card {
            background: var(--white); border-radius: 30px 12px 30px 12px; padding: 48px;
            max-width: 500px; margin: 0 auto; text-align: center; box-shadow: var(--shadow-card);
        }
        .profile-avatar { font-size: 5rem; margin-bottom: 16px; }
        .profile-name { font-size: 2rem; font-weight: 800; color: var(--deep-teal); }
        .profile-email { color: var(--text-mid); margin-bottom: 28px; }

        .modal-overlay {
            position: fixed; inset: 0; background: rgba(13, 36, 36, 0.5); backdrop-filter: blur(4px);
            z-index: 200; display: flex; align-items: center; justify-content: center; animation: fadeIn 0.2s;
        }
        .modal {
            background: var(--white); border-radius: 32px 16px 32px 16px; padding: 36px;
            max-width: 500px; width: 90%; box-shadow: 0 30px 50px rgba(0,0,0,0.25);
            animation: scaleIn 0.3s cubic-bezier(0.2, 0.9, 0.4, 1);
        }
        .auth-tabs { display: flex; gap: 12px; margin-bottom: 28px; }
        .auth-tab { padding: 10px 22px; border: none; background: #F0F4F4; border-radius: 30px; font-weight: 700; cursor: pointer; }
        .auth-tab.active { background: var(--deep-teal); color: white; }
        .auth-form input {
            width: 100%; padding: 14px 18px; border: 2px solid #E0E8E6; border-radius: 16px; margin-bottom: 12px;
            font-family: inherit; font-size: 1rem;
        }
        /* Изображение в модальном окне */
        .modal-img {
            width: 100%;
            height: 240px;
            object-fit: contain;
            border-radius: 20px;
            background: #F0F6F5;
            margin-bottom: 20px;
        }
        .toast {
            position: fixed; bottom: 32px; right: 32px; background: var(--deep-teal); color: white;
            padding: 14px 28px; border-radius: 40px; font-weight: 600; z-index: 300;
            animation: slideUp 0.3s, fadeOut 0.3s 2.2s forwards; box-shadow: 0 12px 24px rgba(0,0,0,0.2);
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes scaleIn { from { opacity: 0; transform: scale(0.92); } to { opacity: 1; transform: scale(1); } }
        @keyframes slideUp { from { transform: translateY(20px); opacity: 0; } }
        @keyframes fadeOut { to { opacity: 0; transform: translateY(10px); } }

        .footer {
            background: rgba(255,255,255,0.6); backdrop-filter: blur(8px);
            text-align: center; padding: 24px; color: var(--text-light); font-weight: 500;
            margin-top: auto; border-top: 1px solid rgba(167,208,205,0.3);
        }

        @media (max-width: 768px) {
            .header-inner { flex-wrap: wrap; height: auto; padding: 12px 0; gap: 12px; }
            .hero { padding: 32px 20px; flex-direction: column; }
            .hero h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>
    <header class="header">
        <div class="header-inner">
            <div class="logo" onclick="navigateTo('home')"><div class="logo-icon"></div>ФармаМед</div>
            <nav class="nav">
                <button class="nav-btn active" data-page="home" onclick="navigateTo('home')">Главная</button>
                <button class="nav-btn" data-page="catalog" onclick="navigateTo('catalog')">Каталог</button>
                <button class="nav-btn" data-page="cart" onclick="navigateTo('cart')">Корзина <span class="cart-badge" id="cartBadge">0</span></button>
                <button class="nav-btn" data-page="about" onclick="navigateTo('about')">О системе</button>
            </nav>
            <div class="header-actions">
                <div id="userBlock"></div>
                <button class="btn-icon" onclick="navigateTo('cart')">🛒<span class="cart-count" id="cartCountIcon">0</span></button>
            </div>
        </div>
    </header>

    <main class="main">
        <div class="page active" id="page-home">
            <div class="hero">
                <div class="hero-text">
                    <h1>Забота о вашем здоровье</h1>
                    <p>Быстрый поиск лекарств, удобный заказ и профессиональная консультация — всё в одной системе.</p>
                    <div class="hero-search">
                        <input type="text" id="heroSearchInput" placeholder="Поиск лекарств..." onkeydown="if(event.key=='Enter')heroSearch()">
                        <button onclick="heroSearch()">Найти</button>
                    </div>
                </div>
                <div class="hero-img"></div>
            </div>
            <h2 class="section-title"><span class="icon">🔥</span> Популярные товары</h2>
            <div class="products-grid" id="popularProducts"></div>
            <div style="text-align:center;margin-top:16px;">
                <button class="btn-add" style="background:var(--coral);font-size:1rem;padding:14px 32px;" onclick="navigateTo('catalog')">Смотреть весь каталог →</button>
            </div>
        </div>

        <div class="page" id="page-catalog">
            <h2 class="section-title"><span class="icon"></span> Каталог лекарств</h2>
            <div style="display:flex;gap:12px;flex-wrap:wrap;margin-bottom:24px;">
                <input type="text" id="catalogSearch" placeholder="Поиск по названию..." style="flex:1;min-width:200px;padding:14px 20px;border:2px solid var(--mint);border-radius:30px;font-size:0.95rem;font-family:inherit;" oninput="filterCatalog()">
            </div>
            <div class="categories" id="categoryFilters">
                <button class="category-chip active" data-cat="all" onclick="setCategory('all', this)">Все</button>
                <button class="category-chip" data-cat="pain" onclick="setCategory('pain', this)">Обезболивающие</button>
                <button class="category-chip" data-cat="cold" onclick="setCategory('cold', this)">От простуды</button>
                <button class="category-chip" data-cat="allergy" onclick="setCategory('allergy', this)">Антигистаминные</button>
                <button class="category-chip" data-cat="vitamins" onclick="setCategory('vitamins', this)">Витамины</button>
                <button class="category-chip" data-cat="heart" onclick="setCategory('heart', this)">Сердечные</button>
            </div>
            <div class="products-grid" id="catalogProducts"></div>
            <p id="noResults" style="display:none;text-align:center;color:var(--text-light);padding:40px;">Ничего не найдено. Попробуйте изменить запрос.</p>
        </div>

        <div class="page" id="page-cart">
            <h2 class="section-title"><span class="icon"></span> Корзина</h2>
            <div id="cartContent"></div>
        </div>

        <div class="page" id="page-about">
            
            <h2 class="section-title" style="margin-top:40px;"><span class="icon"></span> Наши контакты</h2>
            <div class="contacts-block">
                <div class="info">
                    <h3>Аптека «ФармаМед»</h3>
                    <p>Адрес: г. Нижний Новгород, ул. пушкина, д. 15</p>
                    <p>Контакт: +7 (495) 123-45-67</p>
                    <p>Email: info@pharmamed.ru</p>
                    <p>График работы: Ежедневно: 08:00 – 22:00</p>
                </div>
                <div style="flex:1;min-width:200px;height:200px;background:var(--soft-mint);border-radius:16px;display:flex;align-items:center;justify-content:center;font-size:4rem;">🗺️</div>
            </div>
            <h2 class="section-title"><span class="icon"></span> Об информационной системе</h2>
            <div class="about-grid">
                <div class="about-card"><div class="icon"></div><h3>Централизованная БД</h3><p>Все данные о лекарствах, поставщиках и заказах хранятся в единой базе данных под управлением СУБД.</p></div>
                <div class="about-card"><div class="icon"></div><h3>Умный поиск</h3><p>Мгновенный поиск по названию, категории и активному веществу с фильтрацией в реальном времени.</p></div>
                <div class="about-card"><div class="icon"></div><h3>Аналитика</h3><p>Система отслеживает продажи, остатки на складе и формирует отчёты для управления аптекой.</p></div>
                <div class="about-card"><div class="icon"></div><h3>Безопасность</h3><p>Разграничение ролей: администратор, фармацевт, покупатель. Защита персональных данных.</p></div>
                <div class="about-card"><div class="icon"></div><h3>Адаптивный дизайн</h3><p>Интерфейс оптимизирован для ПК, планшетов и мобильных устройств.</p></div>
                <div class="about-card"><div class="icon"></div><h3>Интеграция</h3><p>Возможность подключения к системам учёта 1С, маркировки лекарств и онлайн-кассам.</p></div>
            </div>
        </div>

        <div class="page" id="page-profile">
            <h2 class="section-title"><span class="icon"></span> Личный кабинет</h2>
            <div id="profileContent"></div>
        </div>
    </main>

    <div class="modal-overlay" id="modalOverlay" style="display:none;" onclick="closeModal(event)">
        <div class="modal" id="modalContent" onclick="event.stopPropagation()"></div>
    </div>
    <div class="modal-overlay" id="authModalOverlay" style="display:none;" onclick="closeAuthModal(event)">
        <div class="modal" id="authModalContent" onclick="event.stopPropagation()">
            <button class="modal-close" onclick="closeAuthModalDirect()" style="position:absolute;top:16px;right:20px;background:none;border:none;font-size:1.8rem;cursor:pointer;color:var(--text-light);">✕</button>
            <div class="auth-tabs">
                <button class="auth-tab active" id="tabLogin" onclick="switchAuthTab('login')">Вход</button>
                <button class="auth-tab" id="tabRegister" onclick="switchAuthTab('register')">Регистрация</button>
            </div>
            <div id="authFormContainer"></div>
        </div>
    </div>
    <div id="toastContainer"></div>
    <footer class="footer">© 2026 ФармаМед — Информационная система аптеки. Курсовая работа.</footer>

    <script>
        
        const products = [
            { id: 1, name: 'Парацетамол', category: 'pain', price: 120, oldPrice: 150, 
              img: 'https://cdn.rigla.ru/media/catalog/product/cache/afad95d7734d2fa6d0a8ba78597182b7/7/9/79688-5-6-f-5-56f5305f6ecc5d81f197f7cc26dce5368f03a0c0_79688.jpg', 
              desc: 'Жаропонижающее и обезболивающее средство. 500 мг, 20 таблеток.', badge: 'хит' },
            { id: 2, name: 'Ибупрофен', category: 'pain', price: 180, oldPrice: null, 
              img: 'https://cdn.rigla.ru/media/catalog/product/cache/afad95d7734d2fa6d0a8ba78597182b7/4/6/46046-7-b-9-b-7b9b9ce202e9809c754fd50a2c9ffae417912c4d_46046.jpg', 
              desc: 'Противовоспалительное и обезболивающее. 400 мг, 20 таблеток.', badge: null },
            { id: 3, name: 'Анальгин', category: 'pain', price: 65, oldPrice: 80, 
              img: 'https://media.uteka.ru/media/1024/e/04/e046e3b1d293bdbedcb652a8c3a07bad.jpg', 
              desc: 'Анальгетик. 500 мг, 10 таблеток.', badge: 'акция' },
            { id: 4, name: 'Терафлю', category: 'cold', price: 350, oldPrice: 420, 
              img: 'https://avatars.mds.yandex.net/i?id=e9fa116ba155507705aadaeb00f0faf3_l-5233664-images-thumbs&n=13', 
              desc: 'Порошки от простуды и гриппа. 10 пакетиков.', badge: 'популярное' },
            { id: 5, name: 'Колдрекс', category: 'cold', price: 290, oldPrice: null, 
              img: 'https://avatars.mds.yandex.net/i?id=73a85a242e53c718ac348e230fa1c62f1e7ad509-5424943-images-thumbs&n=13', 
              desc: 'Горячий напиток от простуды. Лимон, 10 пакетиков.', badge: null },
            { id: 6, name: 'Граммидин', category: 'cold', price: 310, oldPrice: 350, 
              img: 'https://media.uteka.ru/media/big/b/6c/b6c2f16cc7820443eb5fb11adf4f45a4.jpg', 
              desc: 'Таблетки для рассасывания от боли в горле. 18 шт.', badge: null },
            { id: 7, name: 'Цетрин', category: 'allergy', price: 220, oldPrice: null, 
              img: 'https://skladlekarstv.ru/upload/iblock/474/47h9xadun6p2mnr5lxo2mndl1sf634rx.jpeg', 
              desc: 'Антигистаминное средство. 10 мг, 20 таблеток.', badge: null },
            { id: 8, name: 'Супрастин', category: 'allergy', price: 160, oldPrice: 190, 
              img: 'https://media.uteka.ru/media/big/9/89/989092d5b1f96b8d64d178af887f5a46.jpg', 
              desc: 'Противоаллергическое. 25 мг, 20 таблеток.', badge: 'акция' },
            { id: 9, name: 'Витамин С', category: 'vitamins', price: 90, oldPrice: null, 
              img: 'https://media.uteka.ru/media/big/6/ea/6eaf3b8a59a0eebf0fd5c90327340dd5.jpg', 
              desc: 'Аскорбиновая кислота. 500 мг, 30 таблеток.', badge: null },
            { id: 10, name: 'Компливит', category: 'vitamins', price: 450, oldPrice: 520, 
              img: 'https://zdesapteka.ru/upload/iblock/6c4/6c4f8223b9fe14f17c67062d89681089.jpg', 
              desc: 'Витаминно-минеральный комплекс. 60 таблеток.', badge: 'популярное' },
            { id: 11, name: 'Валидол', category: 'heart', price: 55, oldPrice: null, 
              img: 'https://avatars.mds.yandex.net/i?id=51a33d493ddee850e6511518bbe4b5ec_l-5294324-images-thumbs&n=13', 
              desc: 'Успокаивающее средство. 60 мг, 10 таблеток.', badge: null },
            { id: 12, name: 'Корвалол', category: 'heart', price: 130, oldPrice: 155, 
              img: 'https://avatars.mds.yandex.net/i?id=7d9a5619398bcc80e2f4e0a981f30f8b_l-5886522-images-thumbs&n=13', 
              desc: 'Сосудорасширяющее и успокаивающее. 25 мл.', badge: 'хит' },
            { id: 13, name: 'Нурофен', category: 'pain', price: 200, oldPrice: null, 
              img: 'https://cdn.budzdorov.ru/media/catalog/product/cache/afad95d7734d2fa6d0a8ba78597182b7/9/8/98621-c-1-8-9-c18936c12348634ef1a461c1a5eaf5048708f94c_98621_1.jpeg', 
              desc: 'Ибупрофен 200 мг. 12 таблеток, покрытых оболочкой.', badge: null },
            { id: 14, name: 'Ацц', category: 'cold', price: 380, oldPrice: 430, 
              img: 'https://images-foodtech.magnit.ru/4hfda6xB-q1sHM19dSvSzjZfVo2fF2M1fF8-sxJeSQY/rs:fit:1600:1600/plain/s3:/img-dostavka/uf/992/9928ac49d6021d701bd5f912a6a69df4/688923a63a1c78c52ed0201d3425c774.png@webp', 
              desc: 'Отхаркивающее средство. Шипучие таблетки, 20 шт.', badge: 'акция' },
            { id: 15, name: 'Лоратадин', category: 'allergy', price: 140, oldPrice: null, 
              img: 'https://avatars.mds.yandex.net/i?id=91d8270b4ea8d6997027e87e0a7dbe917f2a5383-5233239-images-thumbs&n=13', 
              desc: 'Антигистаминное. 10 мг, 10 таблеток.', badge: null },
            { id: 16, name: 'Омега-3', category: 'vitamins', price: 600, oldPrice: 700, 
              img: 'https://cdn.eapteka.ru/upload/offer_photo/480/818/1_9abce83e2cd235544c3762cc2ba2a0c5.png?t=1772016955&_cvc=1775123725', 
              desc: 'Рыбий жир. Капсулы, 90 шт.', badge: 'популярное' }
        ];

        let currentUser=JSON.parse(localStorage.getItem('pharmaCurrentUser'))||null;
        function getUsers(){return JSON.parse(localStorage.getItem('pharmaUsers'))||[]}
        function saveUsers(u){localStorage.setItem('pharmaUsers',JSON.stringify(u))}
        function loginUser(user){currentUser=user;localStorage.setItem('pharmaCurrentUser',JSON.stringify(user));updateAuthUI();closeAuthModalDirect();showToast(`Добро пожаловать, ${user.name}!`);if(document.getElementById('page-profile').classList.contains('active'))renderProfile();reloadCartForUser();}
        function logoutUser(){currentUser=null;localStorage.removeItem('pharmaCurrentUser');updateAuthUI();if(document.getElementById('page-profile').classList.contains('active'))navigateTo('home');reloadCartForUser();showToast('Вы вышли из аккаунта');}
        function updateAuthUI(){const ub=document.getElementById('userBlock');if(!ub)return;if(currentUser){ub.innerHTML=`<div class="user-greeting"><span></span><span class="user-name">${currentUser.name}</span><button class="btn-logout" onclick="logoutUser()">Выйти</button></div>`;if(!document.querySelector('.nav-btn[data-page="profile"]')){const nb=document.createElement('button');nb.className='nav-btn';nb.setAttribute('data-page','profile');nb.textContent='Профиль';nb.onclick=()=>navigateTo('profile');document.querySelector('.nav').appendChild(nb);}}else{ub.innerHTML='<button class="btn-auth" onclick="openAuthModal()">Войти</button>';const pb=document.querySelector('.nav-btn[data-page="profile"]');if(pb)pb.remove();}}
        function getCartKey(){return currentUser?`pharmaCart_${currentUser.email}`:'pharmaCart_guest';}
        function loadCart(){return JSON.parse(localStorage.getItem(getCartKey()))||[];}
        function saveCartToStorage(arr){localStorage.setItem(getCartKey(),JSON.stringify(arr));}
        let cart=loadCart();
        function reloadCartForUser(){cart=loadCart();updateCartUI();if(document.getElementById('page-cart').classList.contains('active'))renderCart();renderCatalog();renderPopular();}
        function updateCartUI(){const t=cart.reduce((s,i)=>s+i.qty,0);document.getElementById('cartBadge').textContent=t;document.getElementById('cartCountIcon').textContent=t;}
        function addToCart(pid){const ex=cart.find(i=>i.id===pid);if(ex)ex.qty++;else cart.push({id:pid,qty:1});saveCartToStorage(cart);updateCartUI();showToast('Товар добавлен в корзину');renderCatalog();renderPopular();if(document.getElementById('page-cart').classList.contains('active'))renderCart();}
        function removeFromCart(pid){cart=cart.filter(i=>i.id!==pid);saveCartToStorage(cart);updateCartUI();renderCart();renderCatalog();renderPopular();showToast('Товар удалён');}
        function changeQty(pid,d){const item=cart.find(i=>i.id===pid);if(!item)return;item.qty+=d;if(item.qty<=0){removeFromCart(pid);return;}saveCartToStorage(cart);updateCartUI();renderCart();renderCatalog();renderPopular();}
        function getProductById(id){return products.find(p=>p.id===id);}
        function isInCart(pid){return cart.some(i=>i.id===pid);}
        function getCartQty(pid){const i=cart.find(i=>i.id===pid);return i?i.qty:0;}
        function getCartTotal(){return cart.reduce((t,i)=>{const p=getProductById(i.id);return t+(p?p.price*i.qty:0);},0);}
        function createProductCard(p){
            const inCart=isInCart(p.id),qty=getCartQty(p.id);
            let badge=''; if(p.badge){ const bc=p.badge==='акция'?'promo':''; badge=`<span class="product-badge ${bc}">${p.badge}</span>`; }
            let priceHTML=`<span class="product-price">${p.price} ₽</span>`;
            if(p.oldPrice) priceHTML=`<span class="product-old-price">${p.oldPrice} ₽</span>`+priceHTML;
            const btnClass=inCart?'btn-add in-cart':'btn-add';
            const btnText=inCart?`✓ В корзине (${qty})`:'В корзину';
            return `<div class="product-card" onclick="openProductModal(${p.id})">${badge}<img src="${p.img}" alt="${p.name}" class="product-img" onerror="this.src='https://placehold.co/400x300/E0E8E6/666?text=Нет+фото'"><div class="product-name">${p.name}</div><div class="product-meta">${p.desc.substring(0,40)}...</div><div class="product-price-row"><div>${priceHTML}</div><button class="${btnClass}" onclick="event.stopPropagation();addToCart(${p.id})">${btnText}</button></div></div>`;
        }
        function renderPopular(){const c=document.getElementById('popularProducts');if(!c)return;const pop=products.filter(p=>p.badge==='популярное'||p.badge==='хит').slice(0,4);if(pop.length<4){const rem=products.filter(p=>!pop.includes(p)).slice(0,4-pop.length);pop.push(...rem);}c.innerHTML=pop.map(p=>createProductCard(p)).join('');}
        function renderCatalog(){const c=document.getElementById('catalogProducts'),nr=document.getElementById('noResults');if(!c)return;let f=products;if(currentCategory!=='all')f=f.filter(p=>p.category===currentCategory);if(catalogSearchQuery.trim()){const q=catalogSearchQuery.toLowerCase().trim();f=f.filter(p=>p.name.toLowerCase().includes(q)||p.desc.toLowerCase().includes(q));}if(f.length===0){c.innerHTML='';nr.style.display='block';}else{nr.style.display='none';c.innerHTML=f.map(p=>createProductCard(p)).join('');}}
        function renderCart(){const c=document.getElementById('cartContent');if(!c)return;if(cart.length===0){c.innerHTML=`<div class="cart-empty"><span class="icon">🛒</span><h3>Корзина пуста</h3><button class="btn-add" style="margin-top:16px;" onclick="navigateTo('catalog')">Перейти в каталог</button></div>`;return;}let h='<div class="cart-list">';cart.forEach(i=>{const p=getProductById(i.id);if(!p)return;h+=`<div class="cart-item"><img src="${p.img}" alt="${p.name}" class="cart-item-img" onerror="this.src='https://placehold.co/70x70/E0E8E6/666?text=?'"><div class="cart-item-info"><div class="cart-item-name">${p.name}</div><div class="cart-item-price">${p.price} ₽ × ${i.qty} = <strong>${p.price*i.qty} ₽</strong></div></div><div class="cart-item-qty"><button onclick="changeQty(${i.id},-1)">−</button><span>${i.qty}</span><button onclick="changeQty(${i.id},1)">+</button></div><button class="cart-item-remove" onclick="removeFromCart(${i.id})"></button></div>`;});h+='</div>';h+=`<div class="cart-summary"><div><span>Итого:</span><span class="cart-total">${getCartTotal()} ₽</span></div><div style="display:flex;gap:10px;"><button class="btn-clear" onclick="clearCart()">Очистить</button><button class="btn-checkout" onclick="checkout()">Оформить заказ</button></div></div>`;c.innerHTML=h;}
        function renderProfile(){const c=document.getElementById('profileContent');if(!c)return;if(!currentUser){c.innerHTML=`<div class="cart-empty"><span class="icon"></span><h3>Вы не вошли</h3><button class="btn-add" onclick="openAuthModal()">Войти</button></div>`;return;}c.innerHTML=`<div class="profile-card"><div class="profile-avatar">👤</div><div class="profile-name">${currentUser.name}</div><div class="profile-email">${currentUser.email}</div><div style="background:#F0F6F5;border-radius:20px;padding:20px;text-align:left;"><p><strong>Регистрация:</strong> ${currentUser.registered||'неизв.'}</p><p><strong>Товаров в корзине:</strong> ${cart.reduce((s,i)=>s+i.qty,0)}</p></div><button class="btn-logout" style="margin-top:24px;padding:12px 28px;font-size:1rem;" onclick="logoutUser()">Выйти</button></div>`;}
        function clearCart(){if(!cart.length)return;if(confirm('Очистить корзину?')){cart=[];saveCartToStorage(cart);updateCartUI();renderCart();renderCatalog();renderPopular();showToast('Корзина очищена');}}
        function checkout(){if(!cart.length)return;if(!currentUser){showToast('Необходимо войти');openAuthModal();return;}alert(`Спасибо, ${currentUser.name}! Сумма: ${getCartTotal()} ₽`);cart=[];saveCartToStorage(cart);updateCartUI();renderCart();renderCatalog();renderPopular();navigateTo('home');showToast('Заказ оформлен!');}
        function openProductModal(pid){const p=getProductById(pid);if(!p)return;document.getElementById('modalContent').innerHTML=`<button class="modal-close" onclick="closeModalDirect()">✕</button><img src="${p.img}" alt="${p.name}" class="modal-img" onerror="this.src='https://placehold.co/400x300/E0E8E6/666?text=Нет+фото'"><h2>${p.name}</h2><p>${p.desc}</p><div style="font-size:1.8rem;color:var(--deep-teal);font-weight:800;margin-bottom:20px;">${p.price} ₽</div><button class="btn-add" style="width:100%;" onclick="addToCart(${p.id});closeModalDirect();">В корзину</button>`;document.getElementById('modalOverlay').style.display='flex';document.body.style.overflow='hidden';}
        function closeModal(e){if(e.target===document.getElementById('modalOverlay'))closeModalDirect();}
        function closeModalDirect(){document.getElementById('modalOverlay').style.display='none';document.body.style.overflow='';}
        function openAuthModal(){document.getElementById('authModalOverlay').style.display='flex';document.body.style.overflow='hidden';switchAuthTab('login');}
        function closeAuthModal(e){if(e.target===document.getElementById('authModalOverlay'))closeAuthModalDirect();}
        function closeAuthModalDirect(){document.getElementById('authModalOverlay').style.display='none';document.body.style.overflow='';}
        function switchAuthTab(t){document.getElementById('tabLogin').classList.toggle('active',t==='login');document.getElementById('tabRegister').classList.toggle('active',t==='register');const c=document.getElementById('authFormContainer');if(t==='login')c.innerHTML=`<form class="auth-form" onsubmit="handleLogin(event)"><input type="email" id="loginEmail" placeholder="Email" required><input type="password" id="loginPassword" placeholder="Пароль" required><div class="auth-error" id="loginError" style="color:var(--coral);"></div><button class="btn-auth" type="submit">Войти</button></form>`;else c.innerHTML=`<form class="auth-form" onsubmit="handleRegister(event)"><input type="text" id="regName" placeholder="Имя" required><input type="email" id="regEmail" placeholder="Email" required><input type="password" id="regPassword" placeholder="Пароль (мин. 4 символа)" minlength="4" required><div class="auth-error" id="regError" style="color:var(--coral);"></div><button class="btn-auth" type="submit">Зарегистрироваться</button></form>`;}
        function handleLogin(e){e.preventDefault();const email=document.getElementById('loginEmail').value.trim().toLowerCase();const pass=document.getElementById('loginPassword').value;const users=getUsers();const user=users.find(u=>u.email===email&&u.password===pass);if(!user){document.getElementById('loginError').textContent='Неверный email или пароль';return;}loginUser({name:user.name,email:user.email,registered:user.registered});}
        function handleRegister(e){e.preventDefault();const name=document.getElementById('regName').value.trim();const email=document.getElementById('regEmail').value.trim().toLowerCase();const pass=document.getElementById('regPassword').value;const err=document.getElementById('regError');if(!name||!email||!pass){err.textContent='Заполните все поля';return;}if(pass.length<4){err.textContent='Пароль минимум 4 символа';return;}const users=getUsers();if(users.find(u=>u.email===email)){err.textContent='Пользователь уже существует';return;}const newUser={name,email,password:pass,registered:new Date().toLocaleDateString('ru-RU')};users.push(newUser);saveUsers(users);loginUser({name:newUser.name,email:newUser.email,registered:newUser.registered});}
        function navigateTo(page){document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));const pg=document.getElementById('page-'+page);if(pg)pg.classList.add('active');const nb=document.querySelector(`.nav-btn[data-page="${page}"]`);if(nb)nb.classList.add('active');if(page==='catalog')renderCatalog();if(page==='cart')renderCart();if(page==='home')renderPopular();if(page==='profile')renderProfile();window.scrollTo({top:0,behavior:'smooth'});closeModalDirect();closeAuthModalDirect();}
        let currentCategory='all',catalogSearchQuery='';
        function setCategory(cat,btn){currentCategory=cat;document.querySelectorAll('#categoryFilters .category-chip').forEach(b=>b.classList.remove('active'));if(btn)btn.classList.add('active');renderCatalog();}
        function filterCatalog(){catalogSearchQuery=document.getElementById('catalogSearch')?.value||'';renderCatalog();}
        function heroSearch(){const q=document.getElementById('heroSearchInput')?.value||'';navigateTo('catalog');setTimeout(()=>{const inp=document.getElementById('catalogSearch');if(inp){inp.value=q;catalogSearchQuery=q;renderCatalog();}},100);}
        function showToast(msg){const c=document.getElementById('toastContainer');const t=document.createElement('div');t.className='toast';t.textContent=msg;c.appendChild(t);setTimeout(()=>t.remove(),2600);}
        document.addEventListener('keydown',e=>{if(e.key==='Escape'){closeModalDirect();closeAuthModalDirect();}});
        updateAuthUI();updateCartUI();renderPopular();renderCatalog();renderCart();
    </script>
</body>
</html>
