!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Blinkart Stationery App</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: radial-gradient(circle at top, #2d0f5c 0%, #0b0223 35%, #050411 100%);
      color: #f6f7ff;
      min-height: 100vh;
      position: relative;
      overflow-x: hidden;
    }
    /* Planets Background */
    .planets-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
    }
    .planet {
      position: absolute;
      border-radius: 50%;
    }
    .planet-1 {
      width: 120px;
      height: 120px;
      background: linear-gradient(135deg, #ff6b6b, #c44569);
      top: 10%;
      left: 5%;
      box-shadow: 0 0 60px rgba(255, 107, 107, 0.4);
    }
    .planet-2 {
      width: 80px;
      height: 80px;
      background: linear-gradient(135deg, #4ecdc4, #44a08d);
      top: 60%;
      right: 10%;
      box-shadow: 0 0 40px rgba(78, 205, 196, 0.4);
    }
    .planet-3 {
      width: 60px;
      height: 60px;
      background: linear-gradient(135deg, #f9d423, #e65c00);
      bottom: 20%;
      left: 15%;
      box-shadow: 0 0 30px rgba(249, 212, 35, 0.4);
    }
    .planet-4 {
      width: 100px;
      height: 100px;
      background: linear-gradient(135deg, #a8e063, #56ab2f);
      top: 30%;
      right: 20%;
      box-shadow: 0 0 50px rgba(168, 224, 99, 0.4);
    }
    .planet-5 {
      width: 50px;
      height: 50px;
      background: linear-gradient(135deg, #667eea, #764ba2);
      top: 70%;
      left: 30%;
      box-shadow: 0 0 25px rgba(102, 126, 234, 0.4);
    }
    .stars {
      position: absolute;
      width: 100%;
      height: 100%;
      background-image: 
        radial-gradient(2px 2px at 20px 30px, #fff, rgba(0,0,0,0)),
        radial-gradient(2px 2px at 40px 70px, #fff, rgba(0,0,0,0)),
        radial-gradient(1px 1px at 90px 40px, #fff, rgba(0,0,0,0)),
        radial-gradient(2px 2px at 130px 80px, #fff, rgba(0,0,0,0)),
        radial-gradient(1px 1px at 160px 120px, #fff, rgba(0,0,0,0));
      background-repeat: repeat;
      background-size: 200px 200px;
      animation: twinkle 3s ease-in-out infinite;
    }
    @keyframes twinkle {
      0%, 100% { opacity: 0.8; }
      50% { opacity: 1; }
    }
    .app-shell {
      min-height: 100vh;
      padding: 20px;
      background: linear-gradient(135deg, rgba(137, 19, 230, 0.4), rgba(14, 235, 215, 0.2));
      box-sizing: border-box;
      position: relative;
      z-index: 1;
    }
    header {
      text-align: left;
      margin-bottom: 25px;
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
    }
    header h1 {
      margin: 0;
      font-size: 3rem;
      letter-spacing: 1px;
      color: #ffd700;
      text-shadow: 0 0 20px rgba(255, 215, 0, 0.5), 0 0 40px rgba(255, 215, 0, 0.3);
    }
    .add-to-cart-btn {
      background: linear-gradient(135deg, #ffd700, #ffaa00);
      color: #1a1a2e;
      padding: 14px 28px;
      border-radius: 999px;
      font-size: 1rem;
      font-weight: 700;
      cursor: pointer;
      border: none;
      box-shadow: 0 4px 20px rgba(255, 215, 0, 0.4);
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .add-to-cart-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 30px rgba(255, 215, 0, 0.6);
    }
    header p {
      margin: 8px auto 0;
      max-width: 760px;
      font-size: 1rem;
      color: #dfe4ff;
    }
    .banner {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 12px;
      margin: 18px 0 35px;
    }
    .badge {
      background: rgba(255,255,255,0.12);
      border: 1px solid rgba(255,255,255,0.16);
      border-radius: 999px;
      padding: 10px 16px;
      color: #fdfcff;
      font-size: 0.95rem;
    }
    .controls {
      display: grid;
      grid-template-columns: 1fr auto;
      gap: 14px;
      max-width: 980px;
      margin: 0 auto 24px;
    }
    .controls input {
      width: 100%;
      border: none;
      border-radius: 999px;
      padding: 14px 18px;
      font-size: 1rem;
      outline: none;
    }
    .controls button {
      border: none;
      background: #ffb703;
      color: #090b1a;
      padding: 14px 22px;
      border-radius: 999px;
      font-size: 1rem;
      cursor: pointer;
      transition: transform 0.2s ease;
    }
    .controls button:hover {
      transform: scale(1.02);
    }
    .main-grid {
      display: grid;
      grid-template-columns: 1.6fr 0.9fr;
      gap: 22px;
      max-width: 1260px;
      margin: 0 auto;
    }
    .product-list,
    .cart-panel {
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: 22px;
      padding: 20px;
      box-shadow: 0 18px 40px rgba(0, 0, 0, 0.22);
    }
    .product-list h2,
    .cart-panel h2 {
      margin-top: 0;
    }
    .product-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 18px;
    }
    /* School Bag Items - Amazon Stationery */
    .school-items {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 15px;
      margin: 20px 0;
    }
    .school-item-card {
      background: rgba(255,255,255,0.1);
      border: 1px solid rgba(255,215,0,0.3);
      border-radius: 16px;
      padding: 15px;
      text-align: center;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
    .school-item-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 30px rgba(255,215,0,0.2);
    }
    .school-item-card .item-icon {
      font-size: 2.5rem;
      margin-bottom: 10px;
    }
    .school-item-card h4 {
      margin: 8px 0;
      font-size: 0.95rem;
      color: #ffd700;
    }
    .school-item-card .item-price {
      font-size: 1.1rem;
      font-weight: 700;
      color: #00c7ff;
      margin: 8px 0;
    }
    .school-item-card button {
      background: #ffd700;
      color: #1a1a2e;
      border: none;
      padding: 8px 16px;
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
      transition: background 0.2s ease;
    }
    .school-item-card button:hover {
      background: #ffaa00;
    }
    @media (max-width: 900px) {
      .school-items {
        grid-template-columns: repeat(3, 1fr);
      }
    }
    @media (max-width: 600px) {
      .school-items {
        grid-template-columns: repeat(2, 1fr);
      }
    }
    .product-card {
      border-radius: 18px;
      background: rgba(14, 8, 42, 0.75);
      padding: 16px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      min-height: 220px;
    }
    .product-card h3 {
      margin: 0;
      font-size: 1.05rem;
      line-height: 1.3;
    }
    .product-card p {
      margin: 0;
      color: #cfd4ff;
      font-size: 0.95rem;
    }
    .product-card .price {
      font-weight: 700;
      font-size: 1.05rem;
      color: #ffd166;
    }
    .product-card button {
      margin-top: auto;
      border: none;
      background: #00c7ff;
      color: #050816;
      padding: 12px 14px;
      border-radius: 14px;
      cursor: pointer;
      transition: background 0.2s ease;
    }
    .product-card button:hover {
      background: #00a8d8;
    }
    .cart-panel .section {
      margin-bottom: 20px;
    }
    .cart-panel label {
      display: block;
      margin-bottom: 6px;
      font-size: 0.95rem;
    }
    .cart-panel input,
    .cart-panel textarea,
    .cart-panel select {
      width: 100%;
      padding: 12px 14px;
      border-radius: 12px;
      border: 1px solid rgba(255,255,255,0.18);
      background: rgba(255,255,255,0.05);
      color: #f9fbff;
      font-size: 0.95rem;
      outline: none;
      box-sizing: border-box;
      margin-bottom: 12px;
    }
    .cart-summary {
      background: rgba(255,255,255,0.06);
      border-radius: 16px;
      padding: 16px;
    }
    .cart-summary p {
      margin: 8px 0;
      font-size: 0.95rem;
    }
    .cart-summary strong {
      color: #fefefe;
    }
    .checkout-btn {
      width: 100%;
      border: none;
      background: #9d4edd;
      color: #fff;
      padding: 14px 16px;
      border-radius: 14px;
      font-size: 1rem;
      cursor: pointer;
      margin-top: 12px;
    }
    .checkout-btn:hover {
      background: #7b2cbf;
    }
    .notice {
      background: rgba(255,255,255,0.08);
      border-left: 4px solid #ffb703;
      padding: 14px 16px;
      border-radius: 12px;
      margin-top: 22px;
      line-height: 1.5;
      color: #eaefff;
    }
    @media (max-width: 980px) {
      .main-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <!-- Planets Background -->
  <div class="planets-bg">
    <div class="stars"></div>
    <div class="planet planet-1"></div>
    <div class="planet planet-2"></div>
    <div class="planet planet-3"></div>
    <div class="planet planet-4"></div>
    <div class="planet planet-5"></div>
  </div>
  <div class="app-shell">
    <header>
      <div>
        <h1>Blinkart</h1>
        <p>Blinkit + Amazon Stationery • 15000+ Products • Fast Delivery by Blinkit & Partners</p>
      </div>
      <button class="add-to-cart-btn">Add to Cart 🛒</button>
    </header>
    <div class="banner">
      <span class="badge">15000+ Products</span>
      <span class="badge">Blinkit Delivery</span>
      <span class="badge">Delivery by external partner</span>
      <span class="badge">Owner: Rishav</span>
      <span class="badge">Stationery items inspired by marketplace catalogs</span>
    </div>

    <div class="controls">
      <input id="searchInput" type="text" placeholder="Search pens, notebooks, art supplies..." />
      <button id="clearSearch">Clear</button>
    </div>

    <!-- School Bag Items - Amazon Stationery -->
    <h2 style="text-align:center; color:#ffd700; margin:30px 0 15px;">🎒 School Bag Items (Amazon)</h2>
    <div class="school-items">
      <div class="school-item-card">
        <div class="item-icon">🎒</div>
        <h4>School Backpack</h4>
        <p class="item-price">₹599</p>
        <button>Add to Cart</button>
      </div>
      <div class="school-item-card">
        <div class="item-icon">📚</div>
        <h4>Notebook Set</h4>
        <p class="item-price">₹149</p>
        <button>Add to Cart</button>
      </div>
      <div class="school-item-card">
        <div class="item-icon">✏️</div>
        <h4>Pencil Box</h4>
        <p class="item-price">₹89</p>
        <button>Add to Cart</button>
      </div>
      <div class="school-item-card">
        <div class="item-icon">📏</div>
        <h4>Geometry Box</h4>
        <p class="item-price">₹199</p>
        <button>Add to Cart</button>
      </div>
      <div class="school-item-card">
        <div class="item-icon">🖌️</div>
        <h4>Art Supplies Kit</h4>
        <p class="item-price">₹349</p>
        <button>Add to Cart</button>
      </div>
    </div>

    <!-- Blinkit Stationery Section -->
    <h2 style="text-align:center; color:#00ff88; margin:30px 0 15px;">⚡ Blinkit Express</h2>
    <div class="school-items">
      <div class="school-item-card" style="border-color:rgba(0,255,136,0.3);">
        <div class="item-icon">🖊️</div>
        <h4>Ball Pen Pack</h4>
        <p class="item-price">₹79</p>
        <button style="background:#00ff88;color:#000;">Add to Cart</button>
      </div>
      <div class="school-item-card" style="border-color:rgba(0,255,136,0.3);">
        <div class="item-icon">📓</div>
        <h4>Register Notebook</h4>
        <p class="item-price">₹59</p>
        <button style="background:#00ff88;color:#000;">Add to Cart</button>
      </div>
      <div class="school-item-card" style="border-color:rgba(0,255,136,0.3);">
        <div class="item-icon">🖍️</div>
        <h4>Crayons Set</h4>
        <p class="item-price">₹129</p>
        <button style="background:#00ff88;color:#000;">Add to Cart</button>
      </div>
      <div class="school-item-card" style="border-color:rgba(0,255,136,0.3);">
        <div class="item-icon">📐</div>
        <h4>Scale Set</h4>
        <p class="item-price">₹39</p>
        <button style="background:#00ff88;color:#000;">Add to Cart</button>
      </div>
      <div class="school-item-card" style="border-color:rgba(0,255,136,0.3);">
        <div class="item-icon">🗑️</div>
        <h4>Eraser & Sharpener</h4>
        <p class="item-price">₹29</p>
        <button style="background:#00ff88;color:#000;">Add to Cart</button>
      </div>
    </div>

    <div class="main-grid">
      <section class="product-list">
        <h2>Browse Products</h2>
        <div class="product-grid" id="productGrid"></div>
      </section>

      <aside class="cart-panel">
        <h2>Cart & Checkout</h2>
        <div class="section cart-summary" id="cartSummary">
          <p><strong>Cart is empty</strong></p>
        </div>
        <div class="section">
          <h3>Customer Details</h3>
          <label for="customerName">Name</label>
          <input id="customerName" type="text" placeholder="Your name" />
          <label for="customerPhone">Phone</label>
          <input id="customerPhone" type="tel" placeholder="Mobile number" />
          <label for="customerAddress">Address</label>
          <textarea id="customerAddress" rows="3" placeholder="Delivery address"></textarea>
          <button class="checkout-btn" id="checkoutButton">Add to Cart 🛒</button>
        </div>
        <div class="section">
          <h3>Payment Details</h3>
          <p><strong>Payment: Cash on Delivery only</strong></p>
          <button class="checkout-btn" id="checkoutButton">Add to Cart 🛒</button>
        </div>
        <div class="notice">
          Blinkart is built so someone else can handle delivery and operations while profit goes to owner Rishav. No default products after checkout.
        </div>
      </aside>
    </div>
  </div>

  <script>
    const products = [
      {name: 'Gel Pen Set - Smooth Writing', price: 129},
      {name: 'Ballpoint Pen Pack', price: 98},
      {name: 'Fountain Pen Starter Kit', price: 499},
      {name: 'Mechanical Pencil 0.5mm', price: 159},
      {name: 'Notebook A5 Ruled', price: 89},
      {name: 'Spiral Notebook 200 pages', price: 149},
      {name: 'Sketchbook Art Paper', price: 249},
      {name: 'Highlighter Pen Set', price: 169},
      {name: 'Marker Pen Set', price: 189},
      {name: 'Sticky Notes Pack', price: 99},
      {name: 'Transparent Tape', price: 59},
      {name: 'Glue Stick', price: 69},
      {name: 'Color Pencils 12 shades', price: 139},
      {name: 'Watercolor Paint Set', price: 279},
      {name: 'Paint Brush Kit', price: 119},
      {name: 'Desk Organizer', price: 349},
      {name: 'Ruler & Scale Set', price: 49},
      {name: 'Eraser Pack', price: 39},
      {name: 'Sharpener Dual', price: 45},
      {name: 'Clipboard Board', price: 189},
      {name: 'Printer Paper A4', price: 249},
      {name: 'Sticky Memo Pad', price: 89},
      {name: 'Stationery Gift Box', price: 699},
      {name: 'Study Lamp', price: 999},
      {name: 'Correction Tape', price: 79},
      {name: 'Math Geometry Box', price: 109},
      {name: 'Whiteboard Marker Set', price: 219},
      {name: 'Desk Mat', price: 299},
      {name: 'File Folder Set', price: 139},
      {name: 'Bullet Journal', price: 229},
      {name: 'Archive Box', price: 249},
      {name: 'Art Craft Paper Set', price: 179},
      {name: 'Stencil Kit', price: 129},
      {name: 'Letter Pad', price: 169},
      {name: 'Note Organizer', price: 189},
      {name: 'Sticky Label Sheets', price: 99},
      {name: 'Premium Pen Case', price: 219},
      {name: 'Calculator Basic', price: 299},
      {name: 'Lunch Box', price: 249},
      {name: 'Sports Water Bottle', price: 199},
      {name: 'Gift Wrapping Paper', price: 129},
      {name: 'Scissors Sharp', price: 79},
      {name: 'Punching Machine', price: 259},
      {name: 'Desk Wall Calendar', price: 169},
      {name: 'Paper Clips Set', price: 39},
      {name: 'Binder Clips Pack', price: 59},
      {name: 'Sticky Flag Notes', price: 69},
      {name: 'Pen Stand', price: 249},
      {name: 'Travel Diary', price: 319},
      {name: 'Stamp Pad', price: 149},
      {name: 'Ink Refill', price: 129},
      {name: 'Label Maker Tape', price: 179},
      {name: 'Organizer Tray', price: 199},
      {name: 'Magnetic Board', price: 349},
      {name: 'Postcard Set', price: 89},
      {name: 'Desk Clock', price: 279},
      {name: 'Cork Board', price: 329},
      {name: 'Study Table Mat', price: 229},
      {name: 'Planner Book', price: 249},
      {name: 'Notebook Hardcover', price: 199},
      {name: 'School Bag', price: 799},
      {name: 'Watercolor Brush Set', price: 159}
    ];

    let cart = [];
    const productGrid = document.getElementById('productGrid');
    const cartSummary = document.getElementById('cartSummary');
    const searchInput = document.getElementById('searchInput');
    const clearSearch = document.getElementById('clearSearch');
    const checkoutButton = document.getElementById('checkoutButton');

    function renderProducts(filter = '') {
      productGrid.innerHTML = '';
      const normalizedFilter = filter.trim().toLowerCase();
      const visibleProducts = products.filter(product => product.name.toLowerCase().includes(normalizedFilter));
      const count = visibleProducts.length;
      if (count === 0) {
        productGrid.innerHTML = '<p style="color:#fff; grid-column:1/-1;">No items found. Try another search.</p>';
        return;
      }
      visibleProducts.forEach((product, index) => {
        const card = document.createElement('div');
        card.className = 'product-card';
        card.innerHTML = `
          <h3>${product.name}</h3>
          <p>Stationery product with delivery through partner service.</p>
          <div class="price">₹ ${product.price}</div>
          <button data-index="${index}">Add to Cart</button>
        `;
        const btn = card.querySelector('button');
        btn.addEventListener('click', () => addToCart(product));
        productGrid.appendChild(card);
      });
    }

    function updateCart() {
      if (cart.length === 0) {
        cartSummary.innerHTML = '<p><strong>Cart is empty</strong></p>';
        return;
      }
      let total = 0;
      cartSummary.innerHTML = '';
      cart.forEach(item => {
        total += item.price * item.quantity;
        const line = document.createElement('p');
        line.textContent = `${item.name} x ${item.quantity} - ₹ ${item.price * item.quantity}`;
        cartSummary.appendChild(line);
      });
      const totalLine = document.createElement('p');
      totalLine.innerHTML = `<strong>Total: ₹ ${total}</strong>`;
      cartSummary.appendChild(totalLine);
      const infoLine = document.createElement('p');
      infoLine.textContent = 'Delivery and operations handled by someone else, profit credited to owner Rishav.';
      cartSummary.appendChild(infoLine);
    }

    function addToCart(product) {
      const existing = cart.find(item => item.name === product.name);
      if (existing) {
        existing.quantity += 1;
      } else {
        cart.push({ ...product, quantity: 1 });
      }
      updateCart();
    }

    function clearSearchField() {
      searchInput.value = '';
      renderProducts();
    }

    function checkout() {
      const name = document.getElementById('customerName').value.trim();
      const phone = document.getElementById('customerPhone').value.trim();
      const address = document.getElementById('customerAddress').value.trim();
      if (cart.length === 0) {
        alert('Please add at least one product to the cart.');
        return;
      }
      if (!name || !phone || !address) {
        alert('Please fill in customer details before checkout.');
        return;
      }
      const total = cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
      alert(`Order confirmed!\nOwner: Rishav\nCustomer: ${name}\nTotal: ₹ ${total}\nPayment: Cash on Delivery\nDelivery handled by partner.
      `);
      cart = [];
      updateCart();
      document.getElementById('customerName').value = '';
      document.getElementById('customerPhone').value = '';
      document.getElementById('customerAddress').value = '';
    }

    searchInput.addEventListener('input', () => renderProducts(searchInput.value));
    clearSearch.addEventListener('click', clearSearchField);
    checkoutButton.addEventListener('click', checkout);

    renderProducts();
  </script>
</body>
</html>
