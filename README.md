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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23f4e4c1'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='16' fill='%23333'%3Eチキンナゲット%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23daa520'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23fff'%3Eチキンカツ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23d4a574'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3Eとんかつ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%238b4513'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3Eメンチカツ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23654321'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='20' fill='%23fff'%3Eハンバーグ%3C/text%3E%3C/svg%3E",
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
                image: "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Crect width='200' height='200' fill='%23a0522d'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' dy='.3em' font-size='18' fill='%23fff'%3E豚ヒレカツ%3C/text%3E%3C/svg%3E",
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
