# cookdelivery
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>クック・デリバリー | 食品ロスを減らして、家計も助ける</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Noto Sans JP', sans-serif;
            background-color: #f0f8f0;
            color: #333;
            position: relative;
        }

        /* 環境貢献背景アニメーション */
        .eco-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .eco-particle {
            position: absolute;
            width: 20px;
            height: 20px;
            background: radial-gradient(circle, rgba(46, 204, 113, 0.3) 0%, transparent 70%);
            border-radius: 50%;
            animation: float 15s infinite;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
        }

        /* ヘッダー */
        header {
            background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 2rem;
            align-items: center;
        }

        nav a {
            color: white;
            text-decoration: none;
            transition: opacity 0.3s;
        }

        nav a:hover {
            opacity: 0.8;
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background-color: #ff6b6b;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
        }

        /* ヒーローセクション */
        .hero {
            background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
            color: white;
            padding: 3rem 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            animation: pulse 3s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            position: relative;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            position: relative;
        }

        .cta-button {
            background-color: #ff6b6b;
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 25px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
            position: relative;
            box-shadow: 0 4px 15px rgba(255,107,107,0.3);
        }

        .cta-button:hover {
            background-color: #ee5a54;
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255,107,107,0.4);
        }

        /* 環境貢献メーター（改良版） */
        .impact-section {
            background: linear-gradient(to bottom, #ffffff 0%, #f0f8f0 100%);
            padding: 3rem 0;
            position: relative;
        }

        .impact-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .impact-box {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s;
            position: relative;
            overflow: hidden;
        }

        .impact-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, #2ecc71, #27ae60);
            animation: loading 2s ease-in-out infinite;
        }

        @keyframes loading {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .impact-box:hover {
            transform: translateY(-5px);
        }

        .impact-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .impact-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #2ecc71;
            margin-bottom: 0.5rem;
        }

        .impact-label {
            color: #666;
            font-size: 1rem;
        }

        /* 検索・フィルターセクション */
        .search-filter-section {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 20px;
        }

        .search-bar {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .search-input {
            flex: 1;
            padding: 0.8rem 1.5rem;
            border: 2px solid #ddd;
            border-radius: 25px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .search-input:focus {
            outline: none;
            border-color: #2ecc71;
        }

        .search-button {
            background-color: #2ecc71;
            color: white;
            padding: 0.8rem 2rem;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .search-button:hover {
            background-color: #27ae60;
        }

        .filter-buttons {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .filter-button {
            padding: 0.5rem 1rem;
            border: 2px solid #ddd;
            background-color: white;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .filter-button:hover {
            border-color: #2ecc71;
        }

        .filter-button.active {
            background-color: #2ecc71;
            color: white;
            border-color: #2ecc71;
        }

        /* AIレコメンドセクション */
        .ai-recommend {
            background-color: #fff5e6;
            padding: 2rem 0;
            margin: 2rem 0;
        }

        .ai-recommend-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .ai-title {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            color: #ff6b6b;
        }

        /* 商品セクション */
        .products-section {
            max-width: 1200px;
            margin: 0 auto;
            padding: 3rem 20px;
        }

        .section-title {
            text-align: center;
            font-size: 2rem;
            margin-bottom: 2rem;
            color: #2c3e50;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            overflow: hidden;
            transition: all 0.3s;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        .product-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .product-info {
            padding: 1rem;
        }

        .product-name {
            font-size: 1.1rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .product-category {
            display: inline-block;
            background-color: #e8f5e9;
            color: #2ecc71;
            padding: 0.2rem 0.8rem;
            border-radius: 15px;
            font-size: 0.8rem;
            margin-bottom: 0.5rem;
        }

        .product-prices {
            margin-bottom: 1rem;
        }

        .original-price {
            color: #999;
            text-decoration: line-through;
            font-size: 0.9rem;
        }

        .sale-price {
            color: #e74c3c;
            font-size: 1.3rem;
            font-weight: bold;
        }

        .discount-badge {
            display: inline-block;
            background-color: #ff6b6b;
            color: white;
            padding: 0.2rem 0.5rem;
            border-radius: 3px;
            font-size: 0.8rem;
            margin-left: 0.5rem;
        }

        .expiry-date {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .add-to-cart {
            width: 100%;
            background-color: #2ecc71;
            color: white;
            padding: 0.8rem;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .add-to-cart:hover {
            background-color: #27ae60;
        }

        /* 商品詳細モーダル */
        .product-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            z-index: 300;
            align-items: center;
            justify-content: center;
        }

        .product-modal-content {
            background-color: white;
            padding: 2rem;
            border-radius: 15px;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
        }

        .close-modal {
            position: absolute;
            top: 1rem;
            right: 1rem;
            font-size: 2rem;
            cursor: pointer;
            color: #999;
        }

        .modal-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin-top: 1rem;
        }

        .modal-image {
            width: 100%;
            border-radius: 10px;
        }

        .modal-info h2 {
            margin-bottom: 1rem;
            color: #2c3e50;
        }

        .modal-description {
            margin: 1rem 0;
            line-height: 1.6;
        }

        .nutrition-info {
            background-color: #f8f9fa;
            padding: 1rem;
            border-radius: 8px;
            margin: 1rem 0;
        }

        /* カートモーダル */
        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 200;
        }

        .cart-content {
            position: absolute;
            right: 0;
            top: 0;
            width: 400px;
            max-width: 90%;
            height: 100%;
            background-color: white;
            box-shadow: -2px 0 10px rgba(0,0,0,0.2);
            overflow-y: auto;
        }

        .cart-header {
            padding: 1.5rem;
            background-color: #2ecc71;
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .close-cart {
            font-size: 1.5rem;
            cursor: pointer;
        }

        .cart-items {
            padding: 1rem;
        }

        .cart-item {
            display: flex;
            gap: 1rem;
            padding: 1rem;
            border-bottom: 1px solid #eee;
        }

        .cart-item-image {
            width: 60px;
            height: 60px;
            object-fit: cover;
            border-radius: 5px;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            font-weight: bold;
        }

        .cart-item-price {
            color: #e74c3c;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-top: 0.5rem;
        }

        .quantity-btn {
            background-color: #f0f0f0;
            border: none;
            padding: 0.2rem 0.5rem;
            cursor: pointer;
            border-radius: 3px;
        }

        .cart-total {
            padding: 1.5rem;
            border-top: 2px solid #eee;
        }

        .total-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
        }

        .total-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #e74c3c;
        }

        .checkout-button {
            width: 100%;
            background-color: #ff6b6b;
            color: white;
            padding: 1rem;
            border: none;
            border-radius: 5px;
            font-size: 1.1rem;
            cursor: pointer;
            margin-top: 1rem;
        }

        /* 会員機能 */
        .member-section {
            background-color: white;
            padding: 2rem;
            border-radius: 15px;
            margin: 2rem auto;
            max-width: 800px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .member-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .member-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: #2ecc71;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
        }

        .member-stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1rem;
        }

        .stat-box {
            text-align: center;
            padding: 1rem;
            background-color: #f8f9fa;
            border-radius: 8px;
        }

        /* 配送モーダル */
        .delivery-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 250;
            align-items: center;
            justify-content: center;
        }

        .delivery-content {
            background-color: white;
            padding: 2rem;
            border-radius: 15px;
            width: 500px;
            max-width: 90%;
        }

        .delivery-header h3 {
            margin-bottom: 1.5rem;
            color: #2c3e50;
        }

        .delivery-options {
            margin-bottom: 1.5rem;
        }

        .delivery-option {
            padding: 1rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            margin-bottom: 1rem;
            cursor: pointer;
            transition: all 0.3s;
        }

        .delivery-option:hover {
            border-color: #2ecc71;
        }

        .delivery-option.selected {
            border-color: #2ecc71;
            background-color: #e8f5e9;
        }

        .time-slots {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 0.5rem;
            margin-top: 1rem;
        }

        .time-slot {
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .time-slot:hover {
            border-color: #2ecc71;
        }

        .time-slot.selected {
            background-color: #2ecc71;
            color: white;
            border-color: #2ecc71;
        }

        /* 決済モーダル */
        .payment-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 260;
            align-items: center;
            justify-content: center;
        }

        .payment-content {
            background-color: white;
            padding: 2rem;
            border-radius: 15px;
            width: 500px;
            max-width: 90%;
        }

        .payment-methods {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
            margin: 1.5rem 0;
        }

        .payment-method {
            padding: 1rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .payment-method:hover {
            border-color: #2ecc71;
        }

        .payment-method.selected {
            border-color: #2ecc71;
            background-color: #e8f5e9;
        }

        /* 通知 */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background-color: #2ecc71;
            color: white;
            padding: 1rem 2rem;
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            z-index: 400;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        /* レスポンシブ */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 1.8rem;
            }

            .products-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
                gap: 1rem;
            }

            .modal-grid {
                grid-template-columns: 1fr;
            }

            nav ul {
                gap: 1rem;
            }

            .filter-buttons {
                overflow-x: auto;
                flex-wrap: nowrap;
                -webkit-overflow-scrolling: touch;
            }
        }
    </style>
</head>
<body>
    <!-- 環境貢献背景 -->
    <div class="eco-background" id="eco-background"></div>

    <!-- ヘッダー -->
    <header>
        <div class="header-container">
            <div class="logo">
                <span>🌱</span>
                <span>クック・デリバリー</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#products">商品一覧</a></li>
                    <li><a href="#" onclick="showMemberSection()">マイページ</a></li>
                    <li><a href="#" onclick="showLoginModal()">ログイン</a></li>
                    <li>
                        <div class="cart-icon" onclick="showCart()">
                            🛒
                            <span class="cart-count" id="cart-count">0</span>
                        </div>
                    </li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- ヒーローセクション -->
    <section class="hero">
        <h1>食品ロスを減らして、家計も助ける</h1>
        <p>3分の1ルールで廃棄される食品を、最大50%OFFでお届け！</p>
        <button class="cta-button" onclick="showLoginModal()">今すぐ会員登録して始める</button>
    </section>

    <!-- 環境貢献メーター -->
    <section class="impact-section">
        <div class="impact-container">
            <div class="impact-box">
                <div class="impact-icon">🌍</div>
                <div class="impact-number" id="food-saved">12,456</div>
                <div class="impact-label">kg 食品ロス削減</div>
            </div>
            <div class="impact-box">
                <div class="impact-icon">🌱</div>
                <div class="impact-number" id="co2-saved">8,234</div>
                <div class="impact-label">kg CO2削減</div>
            </div>
            <div class="impact-box">
                <div class="impact-icon">👥</div>
                <div class="impact-number" id="users-count">1,892</div>
                <div class="impact-label">人 参加者数</div>
            </div>
            <div class="impact-box">
                <div class="impact-icon">💰</div>
                <div class="impact-number" id="money-saved">¥2,345,678</div>
                <div class="impact-label">節約総額</div>
            </div>
        </div>
    </section>

    <!-- 検索・フィルターセクション -->
    <section class="search-filter-section">
        <div class="search-bar">
            <input type="text" class="search-input" id="search-input" placeholder="商品を検索...">
            <button class="search-button" onclick="searchProducts()">検索</button>
        </div>
        <div class="filter-buttons">
            <button class="filter-button active" onclick="filterProducts('all')">すべて</button>
            <button class="filter-button" onclick="filterProducts('chicken')">チキン系</button>
            <button class="filter-button" onclick="filterProducts('pork')">ポーク系</button>
            <button class="filter-button" onclick="filterProducts('seafood')">シーフード系</button>
            <button class="filter-button" onclick="filterProducts('vegetable')">野菜系</button>
            <button class="filter-button" onclick="filterProducts('other')">その他</button>
        </div>
    </section>

    <!-- AIレコメンドセクション -->
    <section class="ai-recommend">
        <div class="ai-recommend-container">
            <h3 class="ai-title">
                <span>🤖</span>
                <span>あなたへのおすすめ商品</span>
            </h3>
            <div class="products-grid" id="ai-recommendations">
                <!-- AIレコメンド商品 -->
            </div>
        </div>
    </section>

    <!-- 商品セクション -->
    <section class="products-section" id="products">
        <h2 class="section-title">本日の救済商品</h2>
        <div class="products-grid" id="products-grid">
            <!-- 商品カードはJavaScriptで動的に生成 -->
        </div>
    </section>

    <!-- 会員セクション -->
    <section class="member-section" id="member-section" style="display: none;">
        <div class="member-info">
            <div style="display: flex; align-items: center; gap: 1rem;">
                <div class="member-avatar">会</div>
                <div>
                    <h3>会員名: ゲストユーザー</h3>
                    <p>会員ランク: ブロンズ</p>
                </div>
            </div>
            <div>
                <p>ポイント: 1,250 pt</p>
            </div>
        </div>
        <div class="member-stats">
            <div class="stat-box">
                <h4>累計削減量</h4>
                <p style="font-size: 1.5rem; color: #2ecc71;">15.3 kg</p>
            </div>
            <div class="stat-box">
                <h4>累計節約額</h4>
                <p style="font-size: 1.5rem; color: #e74c3c;">¥12,450</p>
            </div>
            <div class="stat-box">
                <h4>購入回数</h4>
                <p style="font-size: 1.5rem; color: #3498db;">8 回</p>
            </div>
        </div>
    </section>

    <!-- 商品詳細モーダル -->
    <div class="product-modal" id="product-modal">
        <div class="product-modal-content">
            <span class="close-modal" onclick="hideProductModal()">×</span>
            <div id="product-modal-body">
                <!-- 商品詳細内容 -->
            </div>
        </div>
    </div>

    <!-- カートモーダル -->
    <div class="cart-modal" id="cart-modal">
        <div class="cart-content">
            <div class="cart-header">
                <h3>ショッピングカート</h3>
                <span class="close-cart" onclick="hideCart()">×</span>
            </div>
            <div class="cart-items" id="cart-items">
                <!-- カート内商品 -->
            </div>
            <div class="cart-total">
                <div class="total-row">
                    <span>削減貢献度</span>
                    <span id="cart-impact">0 kg</span>
                </div>
                <div class="total-row">
                    <span>節約額</span>
                    <span id="cart-savings">¥0</span>
                </div>
                <div class="total-row">
                    <span>合計</span>
                    <span class="total-price" id="cart-total">¥0</span>
                </div>
                <button class="checkout-button" onclick="showDeliveryModal()">配送方法を選択</button>
            </div>
        </div>
    </div>

    <!-- 配送モーダル -->
    <div class="delivery-modal" id="delivery-modal">
        <div class="delivery-content">
            <div class="delivery-header">
                <h3>配送方法の選択</h3>
            </div>
            <div class="delivery-options">
                <div class="delivery-option" onclick="selectDelivery('standard')">
                    <h4>通常配送</h4>
                    <p>配送料: ¥500</p>
                    <p>お届け日: 翌日〜3日以内</p>
                </div>
                <div class="delivery-option" onclick="selectDelivery('express')">
                    <h4>エクスプレス配送</h4>
                    <p>配送料: ¥800</p>
                    <p>お届け日: 当日〜翌日</p>
                </div>
                <div class="delivery-option" onclick="selectDelivery('pizza')">
                    <h4>ピザクック配送網</h4>
                    <p>配送料: ¥300</p>
                    <p>お届け日: 2時間以内</p>
                </div>
            </div>
            <div id="time-slot-selection" style="display: none;">
                <h4>配送時間帯を選択</h4>
                <div class="time-slots">
                    <div class="time-slot" onclick="selectTimeSlot('9-12')">9:00-12:00</div>
                    <div class="time-slot" onclick="selectTimeSlot('12-15')">12:00-15:00</div>
                    <div class="time-slot" onclick="selectTimeSlot('15-18')">15:00-18:00</div>
                    <div class="time-slot" onclick="selectTimeSlot('18-21')">18:00-21:00</div>
                </div>
            </div>
            <button class="checkout-button" onclick="showPaymentModal()">決済方法へ進む</button>
        </div>
    </div>

    <!-- 決済モーダル -->
    <div class="payment-modal" id="payment-modal">
        <div class="payment-content">
            <h3>決済方法の選択</h3>
            <div class="payment-methods">
                <div class="payment-method" onclick="selectPayment('credit')">
                    <h4>💳</h4>
                    <p>クレジットカード</p>
                </div>
                <div class="payment-method" onclick="selectPayment('paypay')">
                    <h4>📱</h4>
                    <p>PayPay</p>
                </div>
                <div class="payment-method" onclick="selectPayment('konbini')">
                    <h4>🏪</h4>
                    <p>コンビニ払い</p>
                </div>
                <div class="payment-method" onclick="selectPayment('atodene')">
                    <h4>📋</h4>
                    <p>後払い</p>
                </div>
            </div>
            <button class="checkout-button" onclick="completeOrder()">注文を確定する</button>
        </div>
    </div>

    <!-- ログインモーダル -->
    <div class="login-modal" id="login-modal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.5); z-index: 200; align-items: center; justify-content: center;">
        <div class="login-content" style="background-color: white; padding: 2rem; border-radius: 10px; width: 400px; max-width: 90%;">
            <div class="login-header" style="text-align: center; margin-bottom: 1.5rem;">
                <h2>ログイン / 会員登録</h2>
                <p>環境に優しい買い物を始めましょう</p>
            </div>
            <form onsubmit="handleLogin(event)">
                <div class="form-group" style="margin-bottom: 1rem;">
                    <label style="display: block; margin-bottom: 0.5rem; color: #666;">メールアドレス</label>
                    <input type="email" required placeholder="example@email.com" style="width: 100%; padding: 0.8rem; border: 1px solid #ddd; border-radius: 5px; font-size: 1rem;">
                </div>
                <div class="form-group" style="margin-bottom: 1rem;">
                    <label style="display: block; margin-bottom: 0.5rem; color: #666;">パスワード</label>
                    <input type="password" required placeholder="パスワード" style="width: 100%; padding: 0.8rem; border: 1px solid #ddd; border-radius: 5px; font-size: 1rem;">
                </div>
                <button type="submit" class="login-button" style="width: 100%; background-color: #2ecc71; color: white; padding: 0.8rem; border: none; border-radius: 5px; font-size: 1rem; cursor: pointer; margin-top: 1rem;">ログイン</button>
                <button type="button" class="login-button" style="width: 100%; background-color: #3498db; color: white; padding: 0.8rem; border: none; border-radius: 5px; font-size: 1rem; cursor: pointer; margin-top: 0.5rem;">新規会員登録</button>
            </form>
            <p style="text-align: center; margin-top: 1rem; cursor: pointer; color: #666;" onclick="hideLoginModal()">閉じる</p>
        </div>
    </div>

    <!-- フッター -->
    <footer>
        <div class="footer-content">
            <p>&copy; 2025 クック・デリバリー by 岩田産業グループ × 九州情報大学</p>
            <p>食を通じて九州を元気に！</p>
        </div>
    </footer>

    <script>
        // 商品データ（31商品）
        const products = [
            // チキン系
            {
                id: 1,
                name: "国産鶏チキンナゲット（1kg）",
                category: "chicken",
                originalPrice: 1200,
                salePrice: "○○○",
                discount: 50,
                image: "data:image/jpeg;base64,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",
                expiryDate: "2025/07/15",
                weight: 1.0,
                description: "ジューシーな国産鶏肉を使用した本格チキンナゲット。お子様のお弁当にも最適です。",
                nutrition: "エネルギー: 280kcal/100g、たんぱく質: 13g、脂質: 17g"
            },
            {
                id: 2,
                name: "から揚げ（業務用2kg）",
                category: "chicken",
                originalPrice: 2200,
                salePrice: "○○○",
                discount: 50,
                image: "https://imgcp.aacdn.jp/img-a/auto/auto/aa/gm/article/4/8/7/0/2/8/202103111020/800__topimg_original.jpeg",
                expiryDate: "2025/07/20",
                weight: 2.0,
                description: "外はカリッと、中はジューシーな本格から揚げ。業務用サイズでお得です。",
                nutrition: "エネルギー: 290kcal/100g、たんぱく質: 16g、脂質: 18g"
            },
            {
                id: 3,
                name: "チキンカツ（10枚）",
                category: "chicken",
                originalPrice: 1500,
                salePrice: "○○○",
                discount: 45,
                image: "data:image/jpeg;base64,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",
                expiryDate: "2025/07/10",
                weight: 1.0,
                description: "サクサクの衣と柔らかな鶏肉の絶妙なハーモニー。",
                nutrition: "エネルギー: 265kcal/100g、たんぱく質: 15g、脂質: 16g"
            },
            // ポーク系
            {
                id: 4,
                name: "ロースとんかつ（10枚入）",
                category: "pork",
                originalPrice: 2400,
                salePrice: "○○○",
                discount: 45,
                image: "data:image/jpeg;base64,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",
                expiryDate: "2025/06/30",
                weight: 1.2,
                description: "厳選された豚ロースを使用した本格とんかつ。サクサクの衣が自慢です。",
                nutrition: "エネルギー: 320kcal/100g、たんぱく質: 20g、脂質: 22g"
            },
            {
                id: 5,
                name: "メンチカツ（8枚）",
                category: "pork",
                originalPrice: 1400,
                salePrice: "○○○",
                discount: 45,
                image: "data:image/jpeg;base64,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",
                expiryDate: "2025/07/05",
                weight: 0.8,
                description: "ジューシーな肉汁があふれる手作り風メンチカツ。",
                nutrition: "エネルギー: 285kcal/100g、たんぱく質: 12g、脂質: 19g"
            },
            {
                id: 6,
                name: "ハンバーグ（10個入）",
                category: "pork",
                originalPrice: 1600,
                salePrice: "○○○",
                discount: 45,
                image: "https://makeshop-multi-images.akamaized.net/nakayamafood/shopimages/62/11/6_000000001162.jpg?1678209904",
                expiryDate: "2025/07/12",
                weight: 1.0,
                description: "肉汁たっぷりの本格ハンバーグ。お子様にも大人気です。",
                nutrition: "エネルギー: 223kcal/100g、たんぱく質: 13g、脂質: 15g"
            },
            {
                id: 7,
                name: "豚ヒレカツ（8枚）",
                category: "pork",
                originalPrice: 2000,
                salePrice: "○○○",
                discount: 40,
                image: "data:image/jpeg;base64,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",
                expiryDate: "2025/07/08",
                weight: 0.8,
                description: "柔らかな豚ヒレ肉を使用した上質なカツ。",
                nutrition: "エネルギー: 240kcal/100g、たんぱく質: 22g、脂質: 14g"
            },
            // シーフード系
            {
                id: 8,
                name: "エビフライ（20尾）",
                category: "seafood",
                originalPrice: 1800,
                salePrice: "○○○",
                discount: 40,
                image: "https://www.m-mart.co.jp/ootusuisan/ireg/tmp/ootusuisan_20221127144219.jpg",
                expiryDate: "2025/07/10",
                weight: 0.8,
                description: "プリプリの大エビを使用した贅沢なエビフライ。特別な日の食卓に。",
                nutrition: "エネルギー: 215kcal/100g、たんぱく質: 12g、脂質: 10g"
            },
            {
                id: 9,
                name: "白身魚フライ（12枚）",
                category: "seafood",
                originalPrice: 1200,
                salePrice: "○○○",
                discount: 35,
                image: "https://item-shopping.c.yimg.jp/i/n/amicashop_x21112063006",
                expiryDate: "2025/07/05",
                weight: 0.6,
                description: "さっぱりとした白身魚のフライ。タルタルソースとの相性抜群。",
                nutrition: "エネルギー: 200kcal/100g、たんぱく質: 15g、脂質: 8g"
            },
            {
                id: 10,
                name: "イカリング（500g）",
                category: "seafood",
                originalPrice: 900,
                salePrice: "○○○",
                discount: 40,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ2nAB-AX_wFBiDEj1mMo5tmnSNEdPP0r7gBw&s",
                expiryDate: "2025/06/28",
                weight: 0.5,
                description: "サクサク衣のイカリング。ビールのおつまみにも最適。",
                nutrition: "エネルギー: 188kcal/100g、たんぱく質: 10g、脂質: 9g"
            },
            {
                id: 11,
                name: "カキフライ（12個）",
                category: "seafood",
                originalPrice: 1600,
                salePrice: "○○○",
                discount: 45,
                image: "https://www.super-every.co.jp/wp-content/uploads/2021/08/a2998e33e309548f6b8a870f5b09403c.jpg",
                expiryDate: "2025/07/02",
                weight: 0.6,
                description: "濃厚な旨味のカキフライ。レモンを絞ってどうぞ。",
                nutrition: "エネルギー: 196kcal/100g、たんぱく質: 9g、脂質: 11g"
            },
            // 野菜系
            {
                id: 12,
                name: "クリームコロッケ（12個）",
                category: "vegetable",
                originalPrice: 960,
                salePrice: "○○○",
                discount: 35,
                image: "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxITEhUTEhIVFRMXFxUYGRgYFhcfGBgYGhcYGBgYFRsYHSggGRolGxkXITEhJSkrLi4uFx8zODMtNygtLisBCgoKDg0OGhAQGC0dHR0tKy0rLS0tLSstKy0tLSstLS0tLS0rLSstLS0tLS0tLS0tLSstKy0rLS03NystLS0tLf/AABEIALEBHQMBIgACEQEDEQH/xAAcAAACAwEBAQEAAAAAAAAAAAAABQMEBgECBwj/xABBEAABAwIEAggEBAQEBQUAAAABAAIRAyEEBRIxQVEGEyJhcYGRoTKxwdFCUuHwByNy8RRigrIWM0OS0hVEosLi/8QAGAEBAAMBAAAAAAAAAAAAAAAAAAECAwT/xAAfEQEBAAIDAQEAAwAAAAAAAAAAAQIRAyExEkEEE1H/2gAMAwEAAhEDEQA/APuKEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCEIQCFwuCibiqZMB7SeWoT6IJkLhKNQ5oOoXNQ5o1Dmg6heesHMeq51jeY9UHtC8Gq38w9QvJxDBu5vqEEqFD/i6f52f9wUsoOoQqWZ5iyizU652DRuTy/VBNWxdNhAc9rSb3MWUjKjTcEEdxlYrB1n1jUe+CSR5AcAvfVRt6jcKdK7bWULGf4nEMuys4jke181YodIMQ0S+m14/yhzT9QoWatCSU+kjCL0awPLSPnKkZn7D/ANKt/wBg/wDJA3Qk46Q0506KgJ4Fo+667pDSG7avjoP0QN0JfQzqg+wqAHk4Fv8AuAV4PB2I9UHpCEtzjO6OGA61xkzDWiXGNyByQMkLMYjpf2QaWHe+RI1FrZHPikWP6aYyDopU2dxlx9Zj2QfREKtlmL62jTqwW62NdBFxIBgzyVlAIQuBB1CEIBUc2xhps7N3mzR9T3D7K6SsNmGY9dWLhdrey3wG58z9FMm6irGMwRfT1udLhzPqo8uoNA7Qur1ASAXDhbkrjsEGtG1+5TnlqLSFeIwziYa3w1HglZoVGGXENE7RYfotFWw8HckcvLfvVR2EGgiJJGw3I891x/35TLVi/wATSrhmU/iNQEK02mHC0xwt8pSmgwy0NO5Ppt9FoqY0yAZAAlbZcnW4rMeyxuXt3Dneen/xXgFjXQd+8fYJyKVh3bJPjq5E2+IxMXG3pKyx5cpe1rhPxYNenMdn3spmsDriNO033SrAlzqrmO2ufXvCdhttPDu4LXLl1FZiir0+DogWExf1VilTlo/mPAHBrj97Je8kEtE+KKeILZkzbzUcfL9GWOlxmCDz2iYkR2iZ5ySVLm2Gp9S5rANjyNwJiVQwmIe/ZscBO8fRQf4xxdp5vDB3kkN9JK3Z1Qy/U14Y5pGoudHIHZN22MTPE22/VR1sE+kdLyALlhm1txe4391FhGHW6TJNzyU7NLL2PJBYeJ9IH3XrVUi8eZ/VS4OiRuf3Cm/wsxIEd4481hnyWeNJiUvxLm/GN+IJ+6mZUkiIk7XXirTAEEWInjIPA3hV8tYHObB2Jg+W375Kk5U/JrTytr51zJuIJ7Jkx5rOY6nUY4zO5t3cwtTQpmSCbD68/dQ5jhgWk777rP7yt2t8xn6DmvAAJnxN+7xVF1YagGhxPirGIpmm6Ii8zwPgSmmVYdt3Na03P7J4rS8vSvwTUWV5trHfqhWatVumK4L3ggNJMxN7u3juTyvhmlvDVF0tx+AmnJgHnxtsqzl7TcENGmHNsT2fkST9So6jW22JPNGBsD3j1tKUGm4EgGe0YJ3gm3tC6cbuMrH03o9QezDsa9rWuE2YSWwSSIJJPumKw/8ADvNqr3PoVTOhuppm8aoI9wtwiQuBdXAg6hCECTpdiyygWtMOqdjyPxR5W81lsqwwAib/AHTbpi4l7fyNF/6je/kAoMopammp+EceZ4AfNXiNmjmANty+qmpV+0CbiY/uq2q1+JHopm0AdEzc8ljy3pfFMaRc8SQIkgcwqOY1ercbGwEcjx4q+KYbN7Djt7rLdLn9ZSllWwLXSJiNQBFuN5XJnWsifJajaj3EAkENIPEElxIjzT8U9IMxfcJb0fpMDSQS4kNkkRMCw7ufmmrqYLe8+o8Vr+IQ1DY7TCzubYhrCxokkkE3MX+yfYh2mzhPkspj2TXJIgHQbmBYX+I34bLK95RMM+jbQQX7uc42+UJ8Q6JIjf8AZVTorUmkDbjcRFuUcE4xLbEeey0s2rvsl7LtRBlwHvyKp4adRJEFoA8599ipsXVLWOgBxJsPHmq+W03O1NEAlpNz47+SrxXeSc/FzPcwDJY3g0zGwJ289kh6JVOtxLLWaSR3BoN/VVsTWOkloLi5xG5Mgbm/p5rQdBcF2nVYjs6R5mT8l2bYaOekVMaWOj4XEeo/RUWFrA7mdvqfBO8zoh1MggkC9u5Zxl5PGfQTsp/EmGCBEc4U7n3J3Xmg6Gidzt4KWiyJtvv++K5crdtYW5k4FrpAFxHPvHgqOFZoqXAiBAnbsgSfQqTP2luot8SPks/0NfqFUneW8Dx6wf8A1XPu7sX102gefXwXMS6GGf7rxTaQNQHH6L3VMsJWk8VZ7MgHNdqgadpsAbEGeSvZU4hkc5uPFU8+INOo0dl+nffwkKTJsQ4UW3AAFzzJ2We1jPqiATuSocbLmHYEfZXHOsDP4ZVGs2QSYmJ8gZG6v4gjw7+2Bw0g+d5+ioZ5XFMdn4iB7CCYTAAgtJFjse8b/RK8zpy8u3cDbaPC/DgurC9McvVroWKrMbRqEfyqzagDh8N2l0HkQ5sQvqS+V9G8+dh6dKj1TyzrJLyDABfa8EL6otVYFwLq4FCXVwrq4Qgw1Kg7FVarhVHVF3aB4D8Md8BWMZiWjTSZ2WM4c+8+KlzqoWVG0KLWMJh0mBvaSfJIsyp1DXbSeZgj8oDgLnaCQtIo0mCOp0dycN2E2NyPuspVxRouDgJA3F9rhN6mbtLA7YR+qw5NT1tiuYqhrMRYDyWQzeh1bRSa2WyJmQO6eYFrbLSVs2AaY+Ii207cufikVZnb1uILpBgnaOHj4LCYY27absh9kVD+WCQ0gyZCvVWQS4b2+SSZXinNOnVxLo5zcxw8k3q4gQC76+StlpWFubYnSzUIN47xNlierNXGyIcIcRe06SeHpHNPGvu5o7bdUzO25EIwOVBzy5jdJIIF9p3KwwlyyaZakPOi+HiiADO7p7ydvLZNMS4xJJG/6rOZbm/UvNMjTedPBrjuPCdimubVtbA4bePr3LbPxnO6V5i8CTB348Rp4KLInuc2oTYhjgPDtfRdpUJpvLjNzExtwE7T4L3lYDaL3kRLHfUT6n2VP4/d2nk6KsOdD9IjS1gB/qcdR9oW8ybD6KTRFyJPmvnmS1TVrVBO7mu+Yj2X03Dulonddf6xeyFlsThyys8cCJHhvK1SU5w0amnjpd+/cqRSysy0knZ5A8kxDgSblJslaaetlT8xcPMWPgmFB2kvquMNAHtOy5suq1nhXnztQa6AA6I8PDxWbyxrqdZ5gOuOZJE8gIAv43THOsQXGL6uA/C1qq4Eua7Vvz5kA3PcNljj3dr3qNmxxdpmBbYfXyheNMOiLJZhczB1OB+Hn7AKTEY8bzYbnn3eqnZpS6Ut1BzQJhloNyb7n0VLo9V7DGBkuDRcyBMbgHZVsbiHsIl0F0wTeDw7O/muZW5zXjU4AgkEwNwBedzvxJsqZS2bTGqxFfshws74Y3Hr+91Ur19LRLo4QeIN+C7iMSeqBcIJ3B7+KSZpimgNGo7kzxN9vCVS3v1OlTG4l4c0C7GyTfadrT5KTEsDnMAHZcCSRwiZmSAIF0rbhzqFQuJdUiJHZYwG+9gTA9+5WMdmfVgNgaTZ0g3+GQ0AiNgZXfxeOfP1RrYt1GsDSf2ZaSODmm9wfNfagvkWEyD/ABryKVQU3NY13aEyCeEcreq+utFlqq6uBdXAg6hC4UGAz8062Ne17w1rQGye5sn3JVHJ6DhUcTEAW9wCP3xSzMK+urVqDZ1RxHhqJHsmuRWa49/6rRT9XMxcS4NH4QJPIAXlWcAxz29sQLQCBw2VzAUOsiwmA423JvdX3MbO1+C5ebJvhGexdN9MOcDMzf8AFJ5BUMsqy86hqgEidgOJI4rS4iC5zXWtbvPM9yR4mhTpF0TdsHlBIJIPlt3rLDKTxazbw7FVH/8AKGmT+WSe+9greIy/EGwq9nnBn0V/J8K3TOoyRuTw7hCZuDmt7MHxU56pj0xeLpVMPT7MuMwRFnTaw4bD0TWhmv8AKGkGmQO1JEg/vipM5qNLXNdIcBvMb8UhwOVyzsk9p7fCBqJ+nos+Pkkuk5Y7egytVFmAhxO/De4J43KtYnC4ljImZkxfT3AcJ7+QWly6jDA0gfvkpq7yQRB25X97K3JkiPm78xfSqNbXbqabs/yn8QA2nvM8FrcwxDOoY6ncFp3vx496pZ3lbKjRzHHiHDivGEwbxFJ1xM2NoLQVfgymtRXN56O4ZrcVbi1piZ/FfviSf2F9HaFkspwgZitolpjwkfWVrl0RmEizphc/fYbfvinVZ8NJ5AlJ24hrrcpPjaZJ5qQkzPO2scKYbqIt/STv5KkK2IqNMMcC2oIExqaZvflA9VHhstL3ucTG4mbku3jylaXBYQjsydt4+a5+TVaY3TIdIcRVo1WkAPDhcEWa4xZp8gvdDMGvpu1NLSLuHy8v15rR5tl4cyHgEczt+iyVSkb0y+ToeG6jcWsNXFsgKmFk6WvZP/xAQ4tEiZFtyCNk8mtVADW6KYILi/4nHfbeFc6LZDTpkvIDnm2oxb+laSphWxcQq2RO2EoZu5jn66QN/iLe0bwZO/8AZeMfiZktBDXOLw72iBsN1qM0yemYc4ntTfbhx5+ay/U6nup9ow83F94nYC1lH3JNI1+p8LiMZVpl1EU3FkAh5cJHJtokKDFUcRUcHVaMhsmGmZceZF9K2+WYQaQ1oEAb7eS81MLvYAg8FlljL3VvrT53Wx9YntNduAJadNrw3hPcpelYcIOwFUx/S67fYgLRdIcA/SQw3s8W35jxSfOqPWUHD8WhhH9QaCPku3iy60xz9SdFs06vEYd8w0uNN/g6QPK7D/pX15fnfD1nAATBnUJ4G0R3r7/lmI6yjTqfnY13qAVsqsrgXVwIOqrmeI6ujUf+Vjj6Aq0kPTfEaMHU/wA2lo83D6Sg+ZtaGx3WWlyenNIRYlx9I/usy0SLrY5HTIY3+k+8/otKrieYIgMtbYeghHWEAF1/JemjsgTYjhw7/FSsaA3STI23uTzC4OTdronhRmel4ls7QIPGeXDzSjN3NJZPEtaY7hHmpM6x7XENpk6iYNxHLtfdVAyTSaQS3rG3227NuPNc/HlvJrZ02NGk3SIJgeCmY8cPE+S7phoC8U2mDC6Nds2czmsHk27V99pAMR4KvgK7zRcbFwcGgHjIi9+UrrNWskuBa5xAHGZMz3KTKwQCQNEvIcC/c79kRtERdcfDlbnbWmc1Gmwg4ch+i65ovN7RPd3LzSqdmQOX7717qmBz8B811+xl+s3m1aAQGlsXmNxzsq+T49zw55tp1NHgNlJnNZpfpdO0wO+YnzVXLQA08Bqkgna8fdOD1GZ/hKjnV6f+VoG3jP0WnCzmU1mms+SIsR6AfMFP6VUEwF1xk5iz2HeBWdpPOsyZhrlo8UJY4dxWap7k85A8AEojy5nxGASNu7mU0oiCS0ku2M8t7JPltaXOHGJn/UbJ3hmyAQIkXniVz3daxTzvEEUzYDUY74hYvEvdr07AzbkI4Lb5nSDwQRMX3tKx+MaxryXPhxsOMjci8ey5crfrbSeNVktNrKTSSJgHs8ZO8x5K84bSb8f2Ui6L1w5jNJ1RqaeX72Ka44wFpvpXXZdmoL27nSCdllabS3EOZB7WlwBtfjuti4DTBIAvefXzssjmTv51MaxBMTx3sVjb2vGwwdSppAcLja+w5KVxO0KNtWHlsjs894VqpAi82F/FWx7/AFFJs9YdAcAOyRfiJEfNZhuIlzmm94vvYRf29O9azOWu06dtdgfuVjKjHsq1GkfhY70lp+QPmt+G9s8/GRx9R9MiW3vG0EcC0+XBfav4aY01cuoOO4DmH/S9wHtC+PZdiW1K1XC1j2BUc6m6JLC50uHe03tzuvrH8NcFUw9KtQqAaRV103NnS6m9ogtJ72m3ArsZNiuBdXAg6sx07ptdSYHGGh5d6NIHzWnSvPMvFdhbxG379FM9RXytoYSIDiZAF438itzgOyCIsGifkBPkVkKOCLcUKRF2ET5f2Wyw/Zc6QZ7Pyn6q+XhiZVHFsQRBHK68VnBwLRMwpabHOg8TxO/h3L1UbpaXOZAG8XtzXBnhbW8rNNYzrQ4i49yPsqtRpNdkWk8BwN5CsYinLi4iziS0dxvP74lT4Oh/MYQJAkkzxiAPSSo4uORfKtBpkAQbR7LpdA4xspg0ui0BUc2e5tJ2hsPg6ZEieBPBXy6m1J3WZqYSKsNu2XE34m8gK3VpkvpsLSI1Ol1idhPkrOGxEjt6dTQQbXEbz91QwuLd1rQZeBtzAcd/CFlx8Mm7/q+VaigIA5eC5UdDXSQAF1ocYiYje9rKDEsv6Ta3yV7LFWczfMGNOoRBBnaSAY8yqVeqX4ZxAjU9seGrj5KzmGVsOtxALgRse1B2HgJUVLDE0NAmQ4b77pwY5b7RyaXcqqFsEDuK1GAeBdxiVSy3LOrYNQg8uJPfyU2Jou1mLRsYt5rr0wMq9duh0GYBWWovOqOQd9FecxzZLgO+49IBVGp8RI/KfmFFSgwVngXlzZPd2itDhrWk+tkmwGLDo1RrAF+JE3V2q83DbQQRv5rlyum0m3MfiAGOme/cbwsTn9BrqTdN3B7Tc7WE/P8AcLWZg4aXuI3BaJ9fLZYbpENVOnD4IewgSJPC/gIXPljbk0nUafojVaGAG0xPCDYGeWyeY58gQQe0AN9r7rF9EazocxzpGoi5uFr6/ZA57X2Cm7kC/NGtOltQ9ngAQNR5OJ4WWH6SPLcRQtBnbiBw+i1eY4ktvGpwnjYX5FZDPA6pUbUDXGXCD+UWHaPALnneTT8fRMFVa86y68CBxIiLq7rHZLTM+0c0gyKhUc2bOgnj6T803e4U+0SAGhxdystMdxSzbzntVjWAufAbvPEG3ksDiMW51cEGzhUHiBp4lO8/xgxHZpvnYm1rX+SVtq0nVGgQJaAJ4B27vUN8lvx5S5qZY6jDZ291LFGo3ifovqn8Hs9fWFag92oNDajZ3GokO8pj1WD6RZaXVC0i4AdHgeaY/wAH67aOZGnsKlJ7BPEgtfHo1y7ZWD7suBdXArIdWFHSjRia0nsayB3BvZ+nutnjq4p031DsxrnegJXwnrC8k3Mkq+MRX0QUqdTFnEMcNLwxw8hBHjIKYdeGvOntEukkkC8RYeSxmUVNDYaTIuY58k5yTMRUc5jm9oCbcRzHerfPSY2TsSIBj9FXr4kmncAk7pa7NA0wWn1H2Uf/AKyD+Fvm5Z3jq309VGN7z393IAcFE0CQ4Aj97r23NhtoaPP9V7q5oGHtUtJ5x8uaTDRcjOjiyOV/dV8ZUBkkcDYHdVm5vI7Ak7RBUtarVb2nBrWcefkovHsmRFicM5zjAIpnfm77qfCYbth2kgiw8FZGetJhrR6fopXY8i5pgeISceoXM3w2NIER5KtiqpuW3B+L/KfsVR/9UdpLg0QPFKqvSobCnJ43Kj+un0vYgEnVAA4DjtEABVX4poIaLjj3me7yVN+eagf5Mef7hQ4Z7ybMj3j2V8MPlGV2+i4eoxwERYBV8W4O2MRMrN4eu8G7jF9rfRS0Mz/luG5kN9pTSqWpV1Ex/dUi+HwRwg+YhehW8vv3Jrk2DFQO62kYtpc6QfAce+VFSoYWkA6TPlHzCKOLAc7VL94gHfgFezLKq1OTQHWN/ITBHgTushjs9xVL/wBnp/qDhPsssuPfjSZ6TZ/ji9kMlpMDciAPHcyPdK8PgtTm1KrdbgLCIE8zzjlsqOI6Z4gGDhqIPe0/dW8J0jrObLm0h/SCPqqzh1d2pvJuaMKNPqiXhpLjeBwV9+JJGouixcJNrc0kb0hrbUzQY/lVYS13KHA9nzChxWIzh930MCRzL3CyjPhmU0Y8mlxuJL2QWzEHVN3E72G0fQJLjK5rGHDRRpuMNEa3G1j9+F1foYus0fzqmEZG7WFzj5REqDE5yfwNa7xtPeAs8f48xTeTabLcyq0/+W4tmJB+kq5mWcAt0ye0Dsd/Hu3spaGBxLqYqGi0NIkEkAx3iLLM4vpI1riypTFuBAjxbIv4hRnwb/U48i2wdrUTp4GNvMJPUwpfiTpdpZYB3p7SrP8AxDSJB0GfD9V4dmtMX0m/d9pUcfDcanPPcMseWkjtFzmt39bHx34XHeslhcc4YllakQ19N+pnKxuD47HxK1WOwIDKOIFGocO/UHVmk6WFpI7QHwiRuRHqqFbIwyq6o1pcwtLrCYfYHbgTfzXUxfccgzdmKotqstNnNm7XDdp8PlCYBfHugNfGUK006FWpRqEdYA0x3OaTYEe4svsIVlSPptXLMFVixcAwf6nAH2lfLsOxrQCQCeZmfmvsWa5czEUzSqCWn1BGxCzGH6AU5/m1XubNmtAb6uuT5QtMctIYtuL7WlsQbQxtyfAXK0OVdFMSatOs0ikGmTrBkjiNPEETuRutvlmT0KAijSa3viXHxcbn1V9TczRTXyCm+SS7yIju4XVFvQ+lMue4jgBA991pEKn1UkzujOH4NcP9R+sqc5NTLAwkkN2lMkJuhVhshp036mFwH5dx73U+YZY2q3SS4DuKvITYT4bo7RZtqJ5kifkpHZDRO4cfFxTRCbFBmUUQw0w3smZuZ9Upr9DMOfhc9p8QR7haVCbGRPQwj4aw82f/AKV6p0eIaBTc0HiTP0WgQmwgZ0fdF3ifAn6quOiPb1dcRzAYL+pK06E2jSngctp0vgbfmbn32CuIQoSEIQg89WOQ9FDUwVJ29Nh8Wt+ysIQKcR0Zwb/iw1PybH+2F3EdHsM8NDqQOkQLmY8QbpquIEbuiODP/S/+b/urWDyDD0vgpjzv/ulMkIKgyujOrq26ucX9V4xeTYeqZq0KVQxEvY1xjlJCvriDKYz+HWXvJLaJpOPGm4j0aZb7JW3+FtHVfEVC3lpbPr+i36FGobVcty6nQpNo02xTaNIBvbjM7yvVDAUmfDTY3waArCFI6uBCAg6hCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEAhCEH/2Q==",
                expiryDate: "2025/06/25",
                weight: 0.6,
                description: "とろ〜りクリーミーな味わい。カニクリームコロッケ風。",
                nutrition: "エネルギー: 245kcal/100g、たんぱく質: 7g、脂質: 16g"
            },
            {
                id: 13,
                name: "かぼちゃコロッケ（10個）",
                category: "vegetable",
                originalPrice: 850,
                salePrice: "○○○",
                discount: 40,
                image: "https://item-shopping.c.yimg.jp/i/n/ootuki_60834251",
                expiryDate: "2025/06/28",
                weight: 0.5,
                description: "甘みたっぷりのかぼちゃコロッケ。ヘルシーで栄養満点。",
                nutrition: "エネルギー: 198kcal/100g、たんぱく質: 4g、脂質: 10g"
            },
            {
                id: 14,
                name: "野菜コロッケ（10個）",
                category: "vegetable",
                originalPrice: 800,
                salePrice: "○○○",
                discount: 35,
                image: "data:image/jpeg;base64,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",
                expiryDate: "2025/06/30",
                weight: 0.5,
                description: "7種類の野菜を使用したヘルシーコロッケ。",
                nutrition: "エネルギー: 185kcal/100g、たんぱく質: 5g、脂質: 9g"
            },
            {
                id: 15,
                name: "ポテトコロッケ（20個）",
                category: "vegetable",
                originalPrice: 720,
                salePrice: "○○○",
                discount: 30,
                image: "https://www.amicashop.com/upload/product/20250412141446_67f9f6c6c0025.jpg",
                expiryDate: "2025/07/05",
                weight: 0.6,
                description: "ホクホクのじゃがいもがたっぷり。定番の味。",
                nutrition: "エネルギー: 210kcal/100g、たんぱく質: 4g、脂質: 12g"
            },
            // その他
            {
                id: 16,
                name: "春巻き（10本）",
                category: "other",
                originalPrice: 900,
                salePrice: "○○○",
                discount: 35,
                image: "https://makeshop-multi-images.akamaized.net/nakayamafood/itemimages/000000000508_7AxG8Ln.jpg",
                expiryDate: "2025/06/25",
                weight: 0.5,
                description: "パリパリの皮と具材の絶妙なハーモニー。",
                nutrition: "エネルギー: 220kcal/100g、たんぱく質: 8g、脂質: 12g"
            },
            {
                id: 17,
                name: "餃子（50個）",
                category: "other",
                originalPrice: 1200,
                salePrice: "○○○",
                discount: 40,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSLa39me8rMWi21McPnRHC3mCSIc7NyZ6uBBw&s",
                expiryDate: "2025/07/10",
                weight: 1.0,
                description: "肉汁たっぷりの本格餃子。焼いても水餃子でも美味。",
                nutrition: "エネルギー: 235kcal/100g、たんぱく質: 10g、脂質: 13g"
            },
            {
                id: 18,
                name: "シュウマイ（30個）",
                category: "other",
                originalPrice: 1000,
                salePrice: "○○○",
                discount: 35,
                image: "data:image/jpeg;base64,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",
                expiryDate: "2025/07/08",
                weight: 0.6,
                description: "ジューシーな豚肉と海老の旨味が凝縮。",
                nutrition: "エネルギー: 215kcal/100g、たんぱく質: 12g、脂質: 11g"
            },
            {
                id: 19,
                name: "チキンロール（5本）",
                category: "chicken",
                originalPrice: 1100,
                salePrice: "○○○",
                discount: 40,
                image: "https://www.coop-kobe.net/ito/product/02331/800/009/0233180000984/0233180000984_0001_l.jpg",
                expiryDate: "2025/06/30",
                weight: 0.5,
                description: "野菜を巻いたヘルシーチキンロール。",
                nutrition: "エネルギー: 195kcal/100g、たんぱく質: 16g、脂質: 9g"
            },
            {
                id: 20,
                name: "ミートボール（20個）",
                category: "pork",
                originalPrice: 850,
                salePrice: "○○○",
                discount: 35,
                image: "https://img.benesse-cms.jp/thank-you/item/image/normal/b44b4df3-4a6b-4caa-a430-757661bfddb3.jpg?w=720&h=540&resize_type=cover&resize_mode=force",
                expiryDate: "2025/07/12",
                weight: 0.6,
                description: "トマトソースとの相性抜群のミートボール。",
                nutrition: "エネルギー: 228kcal/100g、たんぱく質: 14g、脂質: 15g"
            },
            {
                id: 21,
                name: "ビーフコロッケ（8個）",
                category: "other",
                originalPrice: 1300,
                salePrice: "○○○",
                discount: 45,
                image: "https://m.media-amazon.com/images/I/61eCo5f3shL._AC_UF894,1000_QL80_.jpg",
                expiryDate: "2025/07/03",
                weight: 0.6,
                description: "牛肉の旨味が詰まった贅沢コロッケ。",
                nutrition: "エネルギー: 258kcal/100g、たんぱく質: 11g、脂質: 17g"
            },
            {
                id: 22,
                name: "タコ焼き（20個）",
                category: "seafood",
                originalPrice: 800,
                salePrice: "○○○",
                discount: 30,
                image: "https://unimarche.jp/store/Images.aspx?fname=%2Fstore%2Fimages%2Fproducts%2F50262_1.jpg&size=M",
                expiryDate: "2025/06/28",
                weight: 0.5,
                description: "本場大阪風のタコ焼き。とろとろ食感が魅力。",
                nutrition: "エネルギー: 175kcal/100g、たんぱく質: 7g、脂質: 6g"
            },
            {
                id: 23,
                name: "お好み焼き（5枚）",
                category: "other",
                originalPrice: 1000,
                salePrice: "○○○",
                discount: 35,
                image: "https://item-shopping.c.yimg.jp/i/n/amicashop_x54925019006",
                expiryDate: "2025/07/01",
                weight: 1.0,
                description: "具だくさんの関西風お好み焼き。",
                nutrition: "エネルギー: 205kcal/100g、たんぱく質: 9g、脂質: 8g"
            },
            {
                id: 24,
                name: "ピザ（マルゲリータ）",
                category: "other",
                originalPrice: 1200,
                salePrice: "○○○",
                discount: 40,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSdCEx9FiPU9tAe6mN_zDwfnwvLG-fFHLEsOg&s",
                expiryDate: "2025/06/25",
                weight: 0.5,
                description: "本格的なマルゲリータピザ。チーズたっぷり。",
                nutrition: "エネルギー: 268kcal/100g、たんぱく質: 12g、脂質: 11g"
            },
            {
                id: 25,
                name: "グラタン（4個）",
                category: "other",
                originalPrice: 1100,
                salePrice: "○○○",
                discount: 35,
                image: "https://img.dinos.co.jp/kp/defaultMall/images/goods/NSH/0019/enl/NH0396f1.jpg?Mode=main2",
                expiryDate: "2025/06/30",
                weight: 0.8,
                description: "濃厚なホワイトソースのグラタン。",
                nutrition: "エネルギー: 195kcal/100g、たんぱく質: 8g、脂質: 12g"
            },
            {
                id: 26,
                name: "ドリア（4個）",
                category: "other",
                originalPrice: 1000,
                salePrice: "○○○",
                discount: 30,
                image: "https://item-shopping.c.yimg.jp/i/n/rihga_bdt-32_1",
                expiryDate: "2025/07/05",
                weight: 0.8,
                description: "チーズたっぷりのミートドリア。",
                nutrition: "エネルギー: 210kcal/100g、たんぱく質: 9g、脂質: 10g"
            },
            {
                id: 27,
                name: "ラザニア（2個）",
                category: "other",
                originalPrice: 900,
                salePrice: "○○○",
                discount: 35,
                image: "https://tshop.r10s.jp/syokusai-shop/cabinet/item/mainimg5/18801_1.jpg?fitin=720%3A720",
                expiryDate: "2025/06/28",
                weight: 0.6,
                description: "本格的なイタリアンラザニア。",
                nutrition: "エネルギー: 225kcal/100g、たんぱく質: 11g、脂質: 13g"
            },
            {
                id: 28,
                name: "チャーハン（5食）",
                category: "other",
                originalPrice: 800,
                salePrice: "○○○",
                discount: 30,
                image: "https://www.micreed.co.jp/shop/cms/images/0000/catalog/147123/147123_common_sp.jpg",
                expiryDate: "2025/07/10",
                weight: 1.0,
                description: "パラパラに仕上げた本格チャーハン。",
                nutrition: "エネルギー: 168kcal/100g、たんぱく質: 6g、脂質: 5g"
            },
            {
                id: 29,
                name: "焼きそば（5食）",
                category: "other",
                originalPrice: 700,
                salePrice: "○○○",
                discount: 30,
                image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRBg_ppCmxIBCqu4KjmatlFOd4LFNX0TCzX_Q&s",
                expiryDate: "2025/07/08",
                weight: 1.0,
                description: "ソース香る本格焼きそば。野菜もたっぷり。",
                nutrition: "エネルギー: 155kcal/100g、たんぱく質: 5g、脂質: 4g"
            },
            {
                id: 30,
                name: "うどん（10食）",
                category: "other",
                originalPrice: 900,
                salePrice: "○○○",
                discount: 35,
                image: "https://makeshop-multi-images.akamaized.net/nakayamafood/shopimages/76/24/1_000000002476.jpg?1700564037",
                expiryDate: "2025/07/15",
                weight: 2.0,
                description: "もちもち食感の讃岐うどん。つゆ付き。",
                nutrition: "エネルギー: 105kcal/100g、たんぱく質: 3g、脂質: 1g"
            },
            {
                id: 31,
                name: "パスタセット（14食）",
                category: "other",
                originalPrice: 1000,
                salePrice: "○○○",
                discount: 40,
                image: "https://tshop.r10s.jp/fm-sourire/cabinet/biiino/item/main-image/1697000409080_1.jpg?fitin=720%3A720",
                expiryDate: "2025/07/12",
                weight: 1.0,
                description: "3種類のソースが楽しめるパスタセット。",
                nutrition: "エネルギー: 185kcal/100g、たんぱく質: 7g、脂質: 6g"
            }
        ];

        // カート
        let cart = [];
        let currentFilter = 'all';
        let selectedDelivery = null;
        let selectedTimeSlot = null;
        let selectedPayment = null;
        let isLoggedIn = false;

        // 環境貢献背景アニメーション
        function createEcoBackground() {
            const bg = document.getElementById('eco-background');
            for (let i = 0; i < 20; i++) {
                const particle = document.createElement('div');
                particle.className = 'eco-particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 15 + 's';
                particle.style.animationDuration = (15 + Math.random() * 10) + 's';
                bg.appendChild(particle);
            }
        }

        // 商品表示
        function displayProducts(productsToShow = products) {
            const grid = document.getElementById('products-grid');
            grid.innerHTML = productsToShow.map(product => `
                <div class="product-card" onclick="showProductDetail(${product.id})">
                    <img src="${product.image}" alt="${product.name}" class="product-image">
                    <div class="product-info">
                        <span class="product-category">${getCategoryName(product.category)}</span>
                        <h3 class="product-name">${product.name}</h3>
                        <div class="product-prices">
                            <div class="original-price">定価: ¥${product.originalPrice}</div>
                            <div>
                                <span class="sale-price">¥${product.salePrice}</span>
                                <span class="discount-badge">${product.discount}% OFF!</span>
                            </div>
                        </div>
                        <div class="expiry-date">賞味期限: ${product.expiryDate}</div>
                        <button class="add-to-cart" onclick="event.stopPropagation(); addToCart(${product.id})">カートに追加</button>
                    </div>
                </div>
            `).join('');
        }

        // AIレコメンド表示
        function displayRecommendations() {
            const recommendedIds = [1, 4, 8, 12]; // 仮のレコメンドID
            const recommendedProducts = products.filter(p => recommendedIds.includes(p.id));
            const container = document.getElementById('ai-recommendations');
            
            container.innerHTML = recommendedProducts.map(product => `
                <div class="product-card" onclick="showProductDetail(${product.id})">
                    <img src="${product.image}" alt="${product.name}" class="product-image">
                    <div class="product-info">
                        <span class="product-category">${getCategoryName(product.category)}</span>
                        <h3 class="product-name">${product.name}</h3>
                        <div class="product-prices">
                            <div class="original-price">定価: ¥${product.originalPrice}</div>
                            <div>
                                <span class="sale-price">¥${product.salePrice}</span>
                                <span class="discount-badge">${product.discount}% OFF!</span>
                            </div>
                        </div>
                        <div class="expiry-date">賞味期限: ${product.expiryDate}</div>
                        <button class="add-to-cart" onclick="event.stopPropagation(); addToCart(${product.id})">カートに追加</button>
                    </div>
                </div>
            `).join('');
        }

        // カテゴリ名取得
        function getCategoryName(category) {
            const categories = {
                chicken: 'チキン',
                pork: 'ポーク',
                seafood: 'シーフード',
                vegetable: '野菜',
                other: 'その他'
            };
            return categories[category] || 'その他';
        }

        // 商品詳細表示
        function showProductDetail(productId) {
            const product = products.find(p => p.id === productId);
            const modal = document.getElementById('product-modal');
            const modalBody = document.getElementById('product-modal-body');
            
            modalBody.innerHTML = `
                <div class="modal-grid">
                    <div>
                        <img src="${product.image}" alt="${product.name}" class="modal-image">
                    </div>
                    <div class="modal-info">
                        <h2>${product.name}</h2>
                        <span class="product-category">${getCategoryName(product.category)}</span>
                        <div class="product-prices" style="margin: 1rem 0;">
                            <div class="original-price">定価: ¥${product.originalPrice}</div>
                            <div>
                                <span class="sale-price">¥${product.salePrice}</span>
                                <span class="discount-badge">${product.discount}% OFF!</span>
                            </div>
                        </div>
                        <p class="modal-description">${product.description}</p>
                        <div class="nutrition-info">
                            <h4>栄養成分表示（100gあたり）</h4>
                            <p>${product.nutrition}</p>
                        </div>
                        <div class="expiry-date" style="margin: 1rem 0;">賞味期限: ${product.expiryDate}</div>
                        <div style="margin: 1rem 0;">
                            <p>🌱 この商品を購入すると <strong>${product.weight}kg</strong> の食品ロス削減に貢献できます！</p>
                        </div>
                        <button class="add-to-cart" style="width: 100%; margin-top: 1rem;" onclick="addToCart(${product.id}); hideProductModal();">カートに追加</button>
                    </div>
                </div>
            `;
            
            modal.style.display = 'flex';
        }

        // 商品詳細モーダルを閉じる
        function hideProductModal() {
            document.getElementById('product-modal').style.display = 'none';
        }

        // 検索機能
        function searchProducts() {
            const searchTerm = document.getElementById('search-input').value.toLowerCase();
            const filtered = products.filter(product => 
                product.name.toLowerCase().includes(searchTerm) ||
                getCategoryName(product.category).toLowerCase().includes(searchTerm)
            );
            displayProducts(filtered);
        }

        // フィルター機能
        function filterProducts(category) {
            currentFilter = category;
            
            // フィルターボタンのアクティブ状態を更新
            document.querySelectorAll('.filter-button').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // 商品をフィルター
            if (category === 'all') {
                displayProducts();
            } else {
                const filtered = products.filter(p => p.category === category);
                displayProducts(filtered);
            }
        }

        // カートに追加
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existingItem = cart.find(item => item.id === productId);
            
            if (existingItem) {
                existingItem.quantity++;
            } else {
                cart.push({...product, quantity: 1});
            }
            
            updateCartCount();
            showNotification('商品をカートに追加しました！');
            
            // AIレコメンドを更新（仮実装）
            updateRecommendations(productId);
        }

        // カート数更新
        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cart-count').textContent = count;
        }

        // カート表示
        function showCart() {
            const modal = document.getElementById('cart-modal');
            const itemsContainer = document.getElementById('cart-items');
            
            if (cart.length === 0) {
                itemsContainer.innerHTML = '<p style="text-align: center; padding: 2rem;">カートは空です</p>';
            } else {
                itemsContainer.innerHTML = cart.map(item => `
                    <div class="cart-item">
                        <img src="${item.image}" alt="${item.name}" class="cart-item-image">
                        <div class="cart-item-info">
                            <div class="cart-item-name">${item.name}</div>
                            <div class="cart-item-price">¥${item.salePrice}</div>
                            <div class="quantity-controls">
                                <button class="quantity-btn" onclick="updateQuantity(${item.id}, -1)">-</button>
                                <span>${item.quantity}</span>
                                <button class="quantity-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
                                <button class="quantity-btn" style="margin-left: 1rem;" onclick="removeFromCart(${item.id})">削除</button>
                            </div>
                        </div>
                    </div>
                `).join('');
            }
            
            // 合計計算
            const totalWeight = cart.reduce((sum, item) => sum + (item.weight * item.quantity), 0);
            const totalSavings = cart.reduce((sum, item) => {
                const originalTotal = item.originalPrice * item.quantity;
                return sum + (originalTotal * item.discount / 100);
            }, 0);
            
            document.getElementById('cart-impact').textContent = `${totalWeight.toFixed(1)} kg`;
            document.getElementById('cart-savings').textContent = `¥${Math.floor(totalSavings).toLocaleString()}`;
            document.getElementById('cart-total').textContent = `¥○○○`;
            
            modal.style.display = 'block';
        }

        // カート数量更新
        function updateQuantity(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    showCart();
                    updateCartCount();
                }
            }
        }

        // カートから削除
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            showCart();
            updateCartCount();
        }

        // カート非表示
        function hideCart() {
            document.getElementById('cart-modal').style.display = 'none';
        }

        // 配送モーダル表示
        function showDeliveryModal() {
            if (cart.length === 0) {
                showNotification('カートが空です');
                return;
            }
            
            if (!isLoggedIn) {
                showNotification('ログインが必要です');
                showLoginModal();
                return;
            }
            
            hideCart();
            document.getElementById('delivery-modal').style.display = 'flex';
        }

        // 配送方法選択
        function selectDelivery(type) {
            selectedDelivery = type;
            document.querySelectorAll('.delivery-option').forEach(opt => {
                opt.classList.remove('selected');
            });
            event.target.closest('.delivery-option').classList.add('selected');
            
            // 時間帯選択を表示
            document.getElementById('time-slot-selection').style.display = 'block';
        }

        // 時間帯選択
        function selectTimeSlot(slot) {
            selectedTimeSlot = slot;
            document.querySelectorAll('.time-slot').forEach(slot => {
                slot.classList.remove('selected');
            });
            event.target.classList.add('selected');
        }

        // 決済モーダル表示
        function showPaymentModal() {
            if (!selectedDelivery || !selectedTimeSlot) {
                showNotification('配送方法と時間帯を選択してください');
                return;
            }
            
            document.getElementById('delivery-modal').style.display = 'none';
            document.getElementById('payment-modal').style.display = 'flex';
        }

        // 決済方法選択
        function selectPayment(method) {
            selectedPayment = method;
            document.querySelectorAll('.payment-method').forEach(method => {
                method.classList.remove('selected');
            });
            event.target.closest('.payment-method').classList.add('selected');
        }

        // 注文完了
        function completeOrder() {
            if (!selectedPayment) {
                showNotification('決済方法を選択してください');
                return;
            }
            
            // 環境貢献データを更新
            const totalWeight = cart.reduce((sum, item) => sum + (item.weight * item.quantity), 0);
            updateEnvironmentData(totalWeight);
            
            showNotification('注文が完了しました！ご利用ありがとうございます。');
            
            // リセット
            cart = [];
            updateCartCount();
            selectedDelivery = null;
            selectedTimeSlot = null;
            selectedPayment = null;
            
            // モーダルを閉じる
            document.getElementById('payment-modal').style.display = 'none';
        }

        // 環境貢献データ更新
        function updateEnvironmentData(weight) {
            const foodSaved = document.getElementById('food-saved');
            const currentValue = parseInt(foodSaved.textContent.replace(/,/g, ''));
            const newValue = currentValue + weight;
            foodSaved.textContent = newValue.toLocaleString();
            
            // CO2削減量も更新（仮計算: 1kg = 0.66kg CO2）
            const co2Saved = document.getElementById('co2-saved');
            const currentCO2 = parseInt(co2Saved.textContent.replace(/,/g, ''));
            const newCO2 = currentCO2 + Math.floor(weight * 0.66);
            co2Saved.textContent = newCO2.toLocaleString();
        }

        // AIレコメンド更新
        function updateRecommendations(productId) {
            // 仮実装: カテゴリーに基づいてレコメンド
            const product = products.find(p => p.id === productId);
            if (product) {
                const similarProducts = products.filter(p => 
                    p.category === product.category && p.id !== productId
                ).slice(0, 4);
                
                if (similarProducts.length > 0) {
                    displayRecommendations();
                }
            }
        }

        // 会員セクション表示
        function showMemberSection() {
            if (!isLoggedIn) {
                showNotification('ログインが必要です');
                showLoginModal();
                return;
            }
            
            const section = document.getElementById('member-section');
            section.style.display = section.style.display === 'none' ? 'block' : 'none';
        }

        // ログインモーダル表示
        function showLoginModal() {
            document.getElementById('login-modal').style.display = 'flex';
        }

        // ログインモーダル非表示
        function hideLoginModal() {
            document.getElementById('login-modal').style.display = 'none';
        }

        // ログイン処理
        function handleLogin(event) {
            event.preventDefault();
            isLoggedIn = true;
            showNotification('ログインしました！');
            hideLoginModal();
        }

        // 通知表示
        function showNotification(message) {
            const notification = document.createElement('div');
            notification.className = 'notification';
            notification.textContent = message;
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }

        // カウンターアニメーション
        function animateCounter(elementId, target) {
            const element = document.getElementById(elementId);
            const duration = 2000;
            const start = 0;
            const increment = target / (duration / 16);
            let current = start;
            
            const timer = setInterval(() => {
                current += increment;
                if (current >= target) {
                    current = target;
                    clearInterval(timer);
                }
                
                if (elementId === 'money-saved') {
                    element.textContent = `¥${Math.floor(current).toLocaleString()}`;
                } else {
                    element.textContent = Math.floor(current).toLocaleString();
                }
            }, 16);
        }

        // 初期化
        window.onload = function() {
            createEcoBackground();
            displayProducts();
            displayRecommendations();
            
            // カウンターアニメーション
            animateCounter('food-saved', 12456);
            animateCounter('co2-saved', 8234);
            animateCounter('users-count', 1892);
            animateCounter('money-saved', 2345678);
        };

        // モーダル外クリックで閉じる
        window.onclick = function(event) {
            const cartModal = document.getElementById('cart-modal');
            const loginModal = document.getElementById('login-modal');
            const productModal = document.getElementById('product-modal');
            const deliveryModal = document.getElementById('delivery-modal');
            const paymentModal = document.getElementById('payment-modal');
            
            if (event.target === cartModal) {
                hideCart();
            }
            if (event.target === loginModal) {
                hideLoginModal();
            }
            if (event.target === productModal) {
                hideProductModal();
            }
            if (event.target === deliveryModal) {
                document.getElementById('delivery-modal').style.display = 'none';
            }
            if (event.target === paymentModal) {
                document.getElementById('payment-modal').style.display = 'none';
            }
        };

        // Enter キーで検索
        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('search-input').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    searchProducts();
                }
            });
        });
    </script>
</body>
</html>
