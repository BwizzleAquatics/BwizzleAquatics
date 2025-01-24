<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pokémon Cards & Fish Emporium</title>
    <link rel="stylesheet" href="styles.css">
    <script src="script.js" defer></script>
</head>
<body>
    <header>
        <div class="container">
            <h1>Pokémon Cards & Fish Emporium</h1>
            <nav>
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#pokemon">Pokémon Cards</a></li>
                    <li><a href="#fish">Fish</a></li>
                    <li><a href="#about">About Us</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <section id="home">
        <div class="hero">
            <h2>Your One-Stop Shop for Pokémon Cards and Fish</h2>
            <p>Discover rare Pokémon cards and exotic fish to enhance your collection or aquarium.</p>
            <a href="#pokemon" class="btn">Shop Pokémon Cards</a>
            <a href="#fish" class="btn">Shop Fish</a>
        </div>
    </section>

    <section id="pokemon" class="product-section">
        <h2>Pokémon Cards</h2>
        <div class="product-grid">
            <div class="product">
                <img src="images/pokemon-card1.jpg" alt="Rare Pokémon Card">
                <h3>Rare Charizard Card</h3>
                <p>$150</p>
                <button onclick="addToCart('Rare Charizard Card', 150)">Add to Cart</button>
            </div>
            <div class="product">
                <img src="images/pokemon-card2.jpg" alt="Booster Pack">
                <h3>Booster Pack (10 Cards)</h3>
                <p>$5</p>
                <button onclick="addToCart('Booster Pack (10 Cards)', 5)">Add to Cart</button>
            </div>
        </div>
    </section>

    <section id="fish" class="product-section">
        <h2>Fish</h2>
        <div class="product-grid">
            <div class="product">
                <img src="images/clownfish.jpg" alt="Clownfish">
                <h3>Clownfish</h3>
                <p>$20</p>
                <button onclick="addToCart('Clownfish', 20)">Add to Cart</button>
            </div>
            <div class="product">
                <img src="images/betta-fish.jpg" alt="Betta Fish">
                <h3>Betta Fish</h3>
                <p>$15</p>
                <button onclick="addToCart('Betta Fish', 15)">Add to Cart</button>
            </div>
        </div>
    </section>

    <section id="about">
        <h2>About Us</h2>
        <p>Welcome to Pokémon Cards & Fish Emporium, where collectors and aquarium enthusiasts unite! Whether you're hunting for rare Pokémon cards or looking to add vibrant life to your tank, we've got you covered.</p>
    </section>

    <section id="contact">
        <h2>Contact Us</h2>
        <form action="#" method="post">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>

            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>

            <label for="message">Message:</label>
            <textarea id="message" name="message" rows="5" required></textarea>

            <button type="submit">Send</button>
        </form>
    </section>

    <section id="cart">
        <h2>Your Cart</h2>
        <div id="cart-items">
            <p>Your cart is empty.</p>
        </div>
        <div id="cart-total">
            <h3>Total: $<span id="total-price">0</span></h3>
        </div>
        <button id="checkout">Checkout</button>
    </section>

    <footer>
        <p>&copy; 2025 Pokémon Cards & Fish Emporium. All rights reserved.</p>
    </footer>

    <script>
        const cart = [];

        function addToCart(item, price) {
            cart.push({ item, price });
            updateCartDisplay();
        }

        function updateCartDisplay() {
            const cartItems = document.getElementById('cart-items');
            const totalPriceElement = document.getElementById('total-price');
            let total = 0;

            if (cart.length === 0) {
                cartItems.innerHTML = '<p>Your cart is empty.</p>';
            } else {
                cartItems.innerHTML = '';
                cart.forEach((cartItem, index) => {
                    const div = document.createElement('div');
                    div.className = 'cart-item';
                    div.innerHTML = `<p>${cartItem.item} - $${cartItem.price} <button onclick="removeFromCart(${index})">Remove</button></p>`;
                    cartItems.appendChild(div);
                    total += cartItem.price;
                });
            }

            totalPriceElement.textContent = total;
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCartDisplay();
        }
    </script>
</body>
</html>
