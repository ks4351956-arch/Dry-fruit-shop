<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Healthy Bites Mobile</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root { --main-color: #6f4e37; --accent: #25D366; }
        body { font-family: 'Segoe UI', sans-serif; margin: 0; background: #fdf6e3; padding-bottom: 80px; }
        
        /* Mobile Header */
        header { background: var(--main-color); color: white; padding: 15px; text-align: center; position: sticky; top: 0; z-index: 100; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
        
        /* Product Container */
        .container { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; padding: 12px; }
        
        .card { background: white; border-radius: 15px; padding: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); text-align: center; }
        .card img { width: 100%; height: 110px; object-fit: cover; border-radius: 10px; }
        .card h3 { font-size: 0.9rem; margin: 8px 0; }
        .price { color: var(--main-color); font-weight: bold; margin-bottom: 10px; }
        
        .buy-btn { background: var(--main-color); color: white; border: none; width: 100%; padding: 8px; border-radius: 8px; font-weight: bold; font-size: 0.8rem; cursor: pointer; }
        
        /* Floating Bottom Cart Bar (Mobile Special) */
        .bottom-nav { position: fixed; bottom: 0; width: 100%; background: white; display: flex; justify-content: space-between; align-items: center; padding: 15px 20px; box-sizing: border-box; box-shadow: 0 -2px 10px rgba(0,0,0,0.1); border-radius: 20px 20px 0 0; }
        
        .cart-info { font-size: 1.1rem; font-weight: bold; color: #333; }
        .order-btn { background: var(--accent); color: white; border: none; padding: 10px 20px; border-radius: 10px; font-weight: bold; display: flex; align-items: center; gap: 8px; text-decoration: none; }

        /* Remove Animation */
        .badge { background: red; color: white; border-radius: 50%; padding: 2px 7px; font-size: 0.7rem; position: absolute; top: -5px; right: -5px; }
    </style>
</head>
<body>

<header>
    <h2 style="margin:0;">🌰 Healthy Bites</h2>
</header>

<div class="container">
    <div class="card">
        <img src="https://images.unsplash.com/photo-1623428187969-5da2dcea5ebf?w=300" alt="Badam">
        <h3>Almonds (Badam)</h3>
        <div class="price">$10.00</div>
        <button class="buy-btn" onclick="addToCart('Almonds', 10)">Add to Cart</button>
    </div>

    <div class="card">
        <img src="https://images.unsplash.com/photo-1596910547037-846b1980329f?w=300" alt="Walnuts">
        <h3>Walnuts (Akhrot)</h3>
        <div class="price">$12.00</div>
        <button class="buy-btn" onclick="addToCart('Walnuts', 12)">Add to Cart</button>
    </div>

    <div class="card">
        <img src="https://images.unsplash.com/photo-1574926054530-540288c8e678?w=300" alt="Cashews">
        <h3>Cashews (Kaju)</h3>
        <div class="price">$15.00</div>
        <button class="buy-btn" onclick="addToCart('Cashews', 15)">Add to Cart</button>
    </div>

    <div class="card">
        <img src="https://images.unsplash.com/photo-158565230ce23-86877924719d?w=300" alt="Pista">
        <h3>Pistachios</h3>
        <div class="price">$18.00</div>
        <button class="buy-btn" onclick="addToCart('Pistachios', 18)">Add to Cart</button>
    </div>
</div>

<div class="bottom-nav">
    <div class="cart-info">
        <i class="fa-solid fa-cart-shopping"></i> Total: $<span id="total-val">0</span>
    </div>
    <button class="order-btn" onclick="orderNow()">
        <i class="fa-brands fa-whatsapp"></i> Order Now
    </button>
</div>

<script>
    let cart = [];
    let total = 0;

    function addToCart(name, price) {
        cart.push({name, price});
        total += price;
        document.getElementById('total-val').innerText = total;
        // Chhota vibration feel karane ke liye (agar mobile support kare)
        if (navigator.vibrate) navigator.vibrate(50);
    }

    function orderNow() {
        if(cart.length === 0) {
            alert("Pehle cart mein kuch add karein!");
            return;
        }
        let phone = "911234567890"; // <-- Apna Number Dalein
        let text = "Naya Order Details:%0A------------------%0A";
        cart.forEach((item, i) => {
            text += `${i+1}. ${item.name} ($${item.price})%0A`;
        });
        text += `%0A*Pura Total: $${total}*`;
        
        window.open(`https://wa.me/${phone}?text=${text}`, '_blank');
    }
</script>

</body>
</html>
