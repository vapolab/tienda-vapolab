
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VapoLab</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
            color: #333;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 10px 20px;
            text-align: center;
        }
        .logo {
            font-family: 'Poppins', sans-serif;
            font-size: 2.5em;
            font-weight: 700;
        }
        .hero {
            text-align: center;
            padding: 50px 20px;
            background: linear-gradient(135deg, #b2dcd7, #f5f5f5);
        }
        .hero h1 {
            font-family: 'Poppins', sans-serif;
            color: #2a2a2a;
            font-size: 3em;
            margin-bottom: 10px;
        }
        .hero p {
            font-size: 1.2em;
            color: #555;
        }
        .products {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 20px;
        }
        .product-card {
            background-color: #fff;
            border: 1px solid #ddd;
            border-radius: 8px;
            margin: 15px;
            padding: 15px;
            width: 300px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.2);
        }
        .product-card img {
            max-width: 100%;
            border-radius: 8px;
        }
        .product-card h3 {
            font-family: 'Poppins', sans-serif;
            margin: 15px 0 10px;
            color: #2a2a2a;
            font-size: 1.3em;
        }
        .product-card p {
            color: #666;
            font-size: 0.9em;
        }
        .stock {
            font-size: 1em;
            font-weight: bold;
            margin-top: 10px;
        }
        .in-stock {
            color: green;
        }
        .out-of-stock {
            color: red;
        }
        .flavor-options {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-top: 10px;
        }
        .flavor-button {
            background-color: #6200ea;
            color: white;
            border: none;
            padding: 10px 15px;
            font-size: 0.9rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
        }
        .flavor-button:hover {
            background-color: #4500b5;
            transform: scale(1.05);
        }
        .cart {
            background: white;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin: 30px auto;
            max-width: 800px;
        }
        .cart h2 {
            font-size: 1.5em;
            margin-bottom: 15px;
        }
        .cart-item {
            padding: 10px;
            border-bottom: 1px solid #ddd;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .cart-item:last-child {
            border-bottom: none;
        }
        .cart button {
            background-color: #6200ea;
            color: white;
            border: none;
            padding: 10px 15px;
            font-size: 1rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .cart button:hover {
            background-color: #4500b5;
        }
        footer {
            text-align: center;
            padding: 10px;
            background-color: #444;
            color: #ccc;
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">VapoLab</div>
    </header>

    <section class="hero">
        <h1>Bienvenido a VapoLab</h1>
        <p>Descubre los mejores vapes con envío gratis. Calidad garantizada.</p>
    </section>

    <section class="products" id="product-list">
        <!-- Los productos serán generados dinámicamente aquí -->
    </section>

    <div class="cart">
        <h2>Tu Carrito</h2>
        <div id="cart-items"></div>
        <button onclick="sendToWhatsApp()">Enviar Pedido por WhatsApp</button>
    </div>

    <footer>
        <p>© 2024 VapoLab. Todos los derechos reservados.</p>
    </footer>

    <script>
        const products = [
            {
                "name": "WeFume",
                "stock": false,
                "description": "Elegante, moderno y con una experiencia única.",
                "image": "https://vapos.uy/wp-content/uploads/2024/08/wefume-strawberry-kiwi-600x600.webp",
                "flavors": []
            },
            {
                "name": "ElfBar King Ice 40K",
                "stock": true,
                "description": "Diseño fresco y gran rendimiento para largas sesiones.",
                "image": "https://rosariovapeshop.com/wp-content/uploads/2024/11/1000490622-3.jpg",
                "flavors": ["Miami Mint"]
            },
            {
                "name": "LostMary Mixer",
                "stock": true,
                "description": "Colores vibrantes y una experiencia de vapeo incomparable.",
                "image": "https://indyargentina.com/cdn/shop/files/lost-mary-mixer-30000-orange-strawberry-684453_800x.jpg?v=1731086779",
                "flavors": ["Watermelon Blowpop", "Blueberry Watermelon"]
            },
            {
                "name": "ElfBar 10K Touch",
                "stock": true,
                "description": "Compacto, elegante y fácil de usar.",
                "image": "https://jackvapestore.com/1988-large_default/elfbar-touch-10000-puffs-citrus-grape.jpg",
                "flavors": ["Miami Mint"]
            },
            {
                "name": "ElfBar 10K Gold",
                "stock": true,
                "description": "Diseño premium y sabores intensos.",
                "image": "https://podvapeshop.com/wp-content/uploads/2024/10/Elf-Bar-Bc-10000-Black-Gold-Pod-Descartavel.jpg",
                "flavors": ["Blue Razz Ice", "Peach Mango Watermelon"]
            },
            {
                "name": "ElfBar TE 30K",
                "stock": true,
                "description": "Ideal para quienes buscan variedad y potencia.",
                "image": "https://atacadousa.com.py/img/p/1/9/9/2/1992-home_default.jpg",
                "flavors": ["Sour Raspberry", "Sour Lush Gummy", "Strawmelon Peach", "Blue Sour Raspberry", "Bubbaloo Grape"]
            },
            {
                "name": "Ignite V150",
                "stock": false,
                "description": "Innovador y versátil, ideal para los amantes del vapeo.",
                "image": "https://vapesvault.com.ar/wp-content/uploads/2022/04/ignite-v150-600x600.jpg",
                "flavors": []
            }
        ];

        const cart = [];

        function renderProducts() {
            const productList = document.getElementById('product-list');
            productList.innerHTML = '';

            products.forEach(product => {
                const productCard = document.createElement('div');
                productCard.classList.add('product-card');

                productCard.innerHTML = `
                    <img src="${product.image}" alt="${product.name}">
                    <h3>${product.name}</h3>
                    <p>${product.description}</p>
                    <p class="stock ${product.stock ? 'in-stock' : 'out-of-stock'}">
                        ${product.stock ? 'En stock' : 'Sin stock'}
                    </p>
                `;

                if (product.stock) {
                    const flavorOptions = document.createElement('div');
                    flavorOptions.classList.add('flavor-options');

                    product.flavors.forEach(flavor => {
                        const flavorButton = document.createElement('button');
                        flavorButton.classList.add('flavor-button');
                        flavorButton.textContent = flavor;
                        flavorButton.onclick = () => addToCart(product.name, flavor);
                        flavorOptions.appendChild(flavorButton);
                    });

                    productCard.appendChild(flavorOptions);
                }

                productList.appendChild(productCard);
            });
        }

        function addToCart(productName, flavor) {
            cart.push({ product: productName, flavor: flavor });
            updateCartDisplay();
        }

        function updateCartDisplay() {
            const cartItems = document.getElementById('cart-items');
            cartItems.innerHTML = '';
            cart.forEach((item, index) => {
                cartItems.innerHTML += `<div class="cart-item">${item.product} - ${item.flavor} <button onclick="removeFromCart(${index})">Eliminar</button></div>`;
            });
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCartDisplay();
        }

        function sendToWhatsApp() {
            if (cart.length === 0) {
                alert('Tu carrito está vacío.');
                return;
            }
            let message = 'Hola, quiero realizar el siguiente pedido:%0A';
            cart.forEach(item => {
                message += `- ${item.product} (${item.flavor})%0A`;
            });
            const whatsappURL = `https://wa.me/543571510327?text=${message}`; // Reemplaza XXXXXXXXXX con el número de WhatsApp
            window.open(whatsappURL, '_blank');
        }

        document.addEventListener('DOMContentLoaded', renderProducts);
    </script>
</body>
</html>
