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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ff9999'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3Eエビフライ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23e6e6fa'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23333'%3E白身魚フライ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ffd700'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23333'%3Eイカリング%3C/text%3E%3C/svg%3E",
                expiryDate: "2025/06/28",
                weight: 0.5,
                description: "サクサク衣のイカリング。ビールのおつまみにも最適。",
                nutrition: "エネルギー: 188kcal/100g、たんぱく質: 10g、脂質: 9g"
            },
            {
                id: 11,
                name: "カキフライ（16個）",
                category: "seafood",
                originalPrice: 1600,
                salePrice: "○○○",
                discount: 45,
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23d3d3d3'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23333'%3Eカキフライ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23fff5e6'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23333'%3Eクリームコロッケ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ff8c00'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23fff'%3Eかぼちゃコロッケ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%2390ee90'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23333'%3E野菜コロッケ%3C/text%3E%3C/svg%3E",
                expiryDate: "2025/06/30",
                weight: 0.5,
                description: "7種類の野菜を使用したヘルシーコロッケ。",
                nutrition: "エネルギー: 185kcal/100g、たんぱく質: 5g、脂質: 9g"
            },
            {
                id: 15,
                name: "ポテトコロッケ（12個）",
                category: "vegetable",
                originalPrice: 720,
                salePrice: "○○○",
                discount: 30,
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23f0e68c'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23333'%3Eポテトコロッケ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ffa500'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3E春巻き%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23deb887'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23333'%3E餃子%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ffe4c4'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23333'%3Eシュウマイ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23bc8f8f'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23fff'%3Eチキンロール%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%238b0000'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23fff'%3Eミートボール%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%236b4423'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23fff'%3Eビーフコロッケ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ff6347'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23fff'%3Eタコ焼き%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23cd5c5c'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23fff'%3Eお好み焼き%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23dc143c'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3Eピザ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ffd700'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23333'%3Eグラタン%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23f5deb3'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23333'%3Eドリア%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ff8c00'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3Eラザニア%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23daa520'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23fff'%3Eチャーハン%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%238b4513'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3E焼きそば%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23f5f5dc'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23333'%3Eうどん%3C/text%3E%3C/svg%3E",
                expiryDate: "2025/07/15",
                weight: 2.0,
                description: "もちもち食感の讃岐うどん。つゆ付き。",
                nutrition: "エネルギー: 105kcal/100g、たんぱく質: 3g、脂質: 1g"
            },
            {
                id: 31,
                name: "パスタセット（5食）",
                category: "other",
                originalPrice: 1000,
                salePrice: "○○○",
                discount: 40,
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23ffa500'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23fff'%3Eパスタセット%3C/text%3E%3C/svg%3E",
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
