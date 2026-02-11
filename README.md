# Sneaker-store
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SneakerZone - Las Mejores Zapatillas</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #ff6b35;
            --secondary: #f7931e;
            --dark: #1a1a2e;
            --light: #eee;
            --accent: #00d4ff;
            --purple: #9d4edd;
        }

        body {
            font-family: 'Inter', 'Segoe UI', sans-serif;
            background: #f5f5f5;
            color: var(--dark);
            overflow-x: hidden;
        }

        /* Header */
        header {
            background: white;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.2rem 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 900;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: -1px;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2.5rem;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 600;
            font-size: 0.95rem;
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 3px;
            background: var(--primary);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: var(--primary);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
            font-weight: bold;
        }

        /* Hero Section */
        .hero {
            margin-top: 80px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 90vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 600px;
            height: 600px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            top: -200px;
            right: -200px;
            animation: float 20s ease-in-out infinite;
        }

        .hero::after {
            content: '';
            position: absolute;
            width: 400px;
            height: 400px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            bottom: -100px;
            left: -100px;
            animation: float 15s ease-in-out infinite reverse;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(30px, -30px) rotate(120deg); }
            66% { transform: translate(-20px, 20px) rotate(240deg); }
        }

        .hero-content {
            max-width: 1400px;
            margin: 0 auto;
            padding: 4rem 2rem;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
            position: relative;
            z-index: 1;
        }

        .hero-text h1 {
            font-size: 4.5rem;
            color: white;
            font-weight: 900;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.2);
        }

        .hero-text .highlight {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            display: block;
        }

        .hero-text p {
            font-size: 1.3rem;
            color: rgba(255, 255, 255, 0.9);
            margin-bottom: 2.5rem;
            line-height: 1.6;
        }

        .hero-buttons {
            display: flex;
            gap: 1.5rem;
        }

        .btn {
            padding: 1.2rem 3rem;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background: white;
            color: var(--purple);
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.3);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            border: 3px solid white;
        }

        .btn-secondary:hover {
            background: white;
            color: var(--purple);
        }

        .hero-image {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .sneaker-showcase {
            width: 100%;
            max-width: 500px;
            animation: rotate3d 10s ease-in-out infinite;
            filter: drop-shadow(0 30px 60px rgba(0,0,0,0.4));
        }

        @keyframes rotate3d {
            0%, 100% { transform: perspective(1000px) rotateY(-15deg) rotateX(5deg); }
            50% { transform: perspective(1000px) rotateY(15deg) rotateX(-5deg); }
        }

        /* Featured Section */
        .featured {
            padding: 6rem 2rem;
            background: white;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-header h2 {
            font-size: 3rem;
            font-weight: 900;
            color: var(--dark);
            margin-bottom: 1rem;
        }

        .section-header p {
            font-size: 1.2rem;
            color: #666;
        }

        .products-grid {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
        }

        .product-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 5px 25px rgba(0,0,0,0.08);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 20px 50px rgba(0,0,0,0.15);
        }

        .product-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            background: var(--primary);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 30px;
            font-size: 0.8rem;
            font-weight: 700;
            z-index: 10;
        }

        .product-image {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            height: 300px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .product-image::before {
            content: '👟';
            font-size: 10rem;
            opacity: 0.3;
            position: absolute;
        }

        .product-card:nth-child(1) .product-image { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
        .product-card:nth-child(2) .product-image { background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); }
        .product-card:nth-child(3) .product-image { background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); }
        .product-card:nth-child(4) .product-image { background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%); }

        .product-info {
            padding: 2rem;
        }

        .product-category {
            color: #999;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .product-name {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--dark);
            margin-bottom: 1rem;
        }

        .product-description {
            color: #666;
            font-size: 0.95rem;
            line-height: 1.6;
            margin-bottom: 1.5rem;
        }

        .product-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .product-price {
            font-size: 1.8rem;
            font-weight: 900;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .add-to-cart {
            background: var(--dark);
            color: white;
            border: none;
            padding: 0.8rem 1.8rem;
            border-radius: 50px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .add-to-cart:hover {
            background: var(--primary);
            transform: scale(1.05);
        }

        /* Categories Section */
        .categories {
            padding: 6rem 2rem;
            background: #f9f9f9;
        }

        .categories-grid {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .category-card {
            background: white;
            border-radius: 20px;
            padding: 3rem 2rem;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
            border: 3px solid transparent;
        }

        .category-card:hover {
            border-color: var(--primary);
            transform: translateY(-10px);
        }

        .category-icon {
            font-size: 4rem;
            margin-bottom: 1.5rem;
        }

        .category-card h3 {
            font-size: 1.4rem;
            font-weight: 800;
            margin-bottom: 0.5rem;
        }

        .category-card p {
            color: #666;
            font-size: 0.95rem;
        }

        /* Newsletter */
        .newsletter {
            padding: 6rem 2rem;
            background: linear-gradient(135deg, var(--dark) 0%, #2d2d44 100%);
            text-align: center;
        }

        .newsletter-content {
            max-width: 700px;
            margin: 0 auto;
        }

        .newsletter h2 {
            font-size: 2.5rem;
            color: white;
            margin-bottom: 1rem;
            font-weight: 900;
        }

        .newsletter p {
            color: rgba(255,255,255,0.8);
            font-size: 1.1rem;
            margin-bottom: 2.5rem;
        }

        .newsletter-form {
            display: flex;
            gap: 1rem;
            max-width: 500px;
            margin: 0 auto;
        }

        .newsletter-form input {
            flex: 1;
            padding: 1.2rem 1.5rem;
            border: none;
            border-radius: 50px;
            font-size: 1rem;
            outline: none;
        }

        .newsletter-form button {
            padding: 1.2rem 2.5rem;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .newsletter-form button:hover {
            background: var(--secondary);
            transform: scale(1.05);
        }

        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            padding: 4rem 2rem 2rem;
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
            margin-bottom: 3rem;
        }

        .footer-section h3 {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            font-weight: 800;
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section ul li {
            margin-bottom: 0.8rem;
        }

        .footer-section a {
            color: rgba(255,255,255,0.7);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-section a:hover {
            color: var(--primary);
        }

        .social-icons {
            display: flex;
            gap: 1.5rem;
            margin-top: 1.5rem;
        }

        .social-icons a {
            font-size: 1.8rem;
            transition: transform 0.3s ease;
        }

        .social-icons a:hover {
            transform: scale(1.2);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            border-top: 1px solid rgba(255,255,255,0.1);
            color: rgba(255,255,255,0.5);
        }

        /* Responsive */
        @media (max-width: 968px) {
            .hero-content {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .hero-text h1 {
                font-size: 3rem;
            }

            .hero-buttons {
                justify-content: center;
            }

            .sneaker-showcase {
                max-width: 350px;
            }

            .nav-links {
                display: none;
            }

            .newsletter-form {
                flex-direction: column;
            }
        }

        @media (max-width: 600px) {
            .hero-text h1 {
                font-size: 2.2rem;
            }

            .section-header h2 {
                font-size: 2rem;
            }

            .products-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Animaciones de entrada */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .product-card {
            animation: fadeInUp 0.6s ease-out forwards;
        }

        .product-card:nth-child(1) { animation-delay: 0.1s; }
        .product-card:nth-child(2) { animation-delay: 0.2s; }
        .product-card:nth-child(3) { animation-delay: 0.3s; }
        .product-card:nth-child(4) { animation-delay: 0.4s; }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">SneakerZone</div>
            <ul class="nav-links">
                <li><a href="#home">Inicio</a></li>
                <li><a href="#productos">Productos</a></li>
                <li><a href="#categorias">Categorías</a></li>
                <li><a href="#contacto">Contacto</a></li>
                <li class="cart-icon">
                    🛒
                    <span class="cart-count">3</span>
                </li>
            </ul>
        </nav>
    </header>

    <section class="hero" id="home">
        <div class="hero-content">
            <div class="hero-text">
                <h1>
                    Los Mejores
                    <span class="highlight">Sneakers</span>
                    Para Tu Estilo
                </h1>
                <p>Descubre las últimas tendencias en zapatillas deportivas y urbanas. Calidad premium, diseños exclusivos y comodidad incomparable.</p>
                <div class="hero-buttons">
                    <a href="#productos" class="btn btn-primary">Ver Colección</a>
                    <a href="#categorias" class="btn btn-secondary">Explorar</a>
                </div>
            </div>
            <div class="hero-image">
                <div class="sneaker-showcase">
                    <svg viewBox="0 0 500 300" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <ellipse cx="250" cy="260" rx="150" ry="20" fill="rgba(0,0,0,0.2)"/>
                        <path d="M100 150 Q150 100 250 120 Q350 140 400 130 L380 180 Q300 190 250 180 Q150 170 120 190 Z" fill="white" stroke="#333" stroke-width="3"/>
                        <path d="M120 190 Q150 200 200 195 Q250 190 300 200 L320 160 Q280 155 250 150 Q200 145 160 160 Z" fill="#f5f5f5" stroke="#333" stroke-width="2"/>
                        <circle cx="180" cy="175" r="25" fill="var(--primary)" stroke="#333" stroke-width="2"/>
                        <path d="M250 120 L245 140 L255 140 Z" fill="var(--secondary)"/>
                        <line x1="100" y1="150" x2="140" y2="160" stroke="var(--accent)" stroke-width="3" stroke-linecap="round"/>
                        <line x1="110" y1="155" x2="150" y2="165" stroke="var(--accent)" stroke-width="3" stroke-linecap="round"/>
                    </svg>
                </div>
            </div>
        </div>
    </section>

    <section class="featured" id="productos">
        <div class="section-header">
            <h2>Productos Destacados</h2>
            <p>Las zapatillas más populares de la temporada</p>
        </div>
        <div class="products-grid">
            <div class="product-card">
                <span class="product-badge">NUEVO</span>
                <div class="product-image"></div>
                <div class="product-info">
                    <div class="product-category">Running</div>
                    <h3 class="product-name">Air Max Ultra</h3>
                    <p class="product-description">Máxima comodidad y estilo para tus entrenamientos diarios.</p>
                    <div class="product-footer">
                        <span class="product-price">$129.99</span>
                        <button class="add-to-cart">Agregar</button>
                    </div>
                </div>
            </div>

            <div class="product-card">
                <span class="product-badge">HOT</span>
                <div class="product-image"></div>
                <div class="product-info">
                    <div class="product-category">Urban</div>
                    <h3 class="product-name">Street Pro X</h3>
                    <p class="product-description">Diseño urbano con tecnología de punta para el día a día.</p>
                    <div class="product-footer">
                        <span class="product-price">$159.99</span>
                        <button class="add-to-cart">Agregar</button>
                    </div>
                </div>
            </div>

            <div class="product-card">
                <span class="product-badge">SALE -20%</span>
                <div class="product-image"></div>
                <div class="product-info">
                    <div class="product-category">Basketball</div>
                    <h3 class="product-name">Hoop Master</h3>
                    <p class="product-description">Perfecto agarre y soporte para dominar la cancha.</p>
                    <div class="product-footer">
                        <span class="product-price">$99.99</span>
                        <button class="add-to-cart">Agregar</button>
                    </div>
                </div>
            </div>

            <div class="product-card">
                <span class="product-badge">EDICIÓN LIMITADA</span>
                <div class="product-image"></div>
                <div class="product-info">
                    <div class="product-category">Lifestyle</div>
                    <h3 class="product-name">Classic Retro</h3>
                    <p class="product-description">Estilo vintage con confort moderno para cualquier ocasión.</p>
                    <div class="product-footer">
                        <span class="product-price">$179.99</span>
                        <button class="add-to-cart">Agregar</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="categories" id="categorias">
        <div class="section-header">
            <h2>Explora por Categoría</h2>
            <p>Encuentra el calzado perfecto para cada actividad</p>
        </div>
        <div class="categories-grid">
            <div class="category-card">
                <div class="category-icon">🏃</div>
                <h3>Running</h3>
                <p>Zapatillas para corredores</p>
            </div>
            <div class="category-card">
                <div class="category-icon">🏀</div>
                <h3>Basketball</h3>
                <p>Alto rendimiento en cancha</p>
            </div>
            <div class="category-card">
                <div class="category-icon">🌆</div>
                <h3>Urban</h3>
                <p>Estilo urbano casual</p>
            </div>
            <div class="category-card">
                <div class="category-icon">⚽</div>
                <h3>Fútbol</h3>
                <p>Domina el campo</p>
            </div>
            <div class="category-card">
                <div class="category-icon">🎨</div>
                <h3>Lifestyle</h3>
                <p>Comodidad diaria</p>
            </div>
        </div>
    </section>

    <section class="newsletter">
        <div class="newsletter-content">
            <h2>Únete a la Comunidad</h2>
            <p>Recibe ofertas exclusivas, lanzamientos anticipados y las últimas tendencias en sneakers</p>
            <form class="newsletter-form">
                <input type="email" placeholder="Tu correo electrónico" required>
                <button type="submit">Suscribirse</button>
            </form>
        </div>
    </section>

    <footer id="contacto">
        <div class="footer-content">
            <div class="footer-section">
                <h3>SneakerZone</h3>
                <p>Tu destino número uno para las mejores zapatillas del mercado.</p>
                <div class="social-icons">
                    <a href="#">📘</a>
                    <a href="#">📷</a>
                    <a href="#">🐦</a>
                    <a href="#">📺</a>
                </div>
            </div>
            <div class="footer-section">
                <h3>Comprar</h3>
                <ul>
                    <li><a href="#">Nuevos Lanzamientos</a></li>
                    <li><a href="#">Ofertas</a></li>
                    <li><a href="#">Más Vendidos</a></li>
                    <li><a href="#">Colecciones</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Ayuda</h3>
                <ul>
                    <li><a href="#">Guía de Tallas</a></li>
                    <li><a href="#">Envíos</a></li>
                    <li><a href="#">Devoluciones</a></li>
                    <li><a href="#">FAQ</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Contacto</h3>
                <ul>
                    <li><a href="#">contacto@sneakerzone.com</a></li>
                    <li><a href="#">+1 (555) 123-4567</a></li>
                    <li><a href="#">Chat en Vivo</a></li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2025 SneakerZone. Todos los derechos reservados.</p>
        </div>
    </footer>

    <script>
        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });

        // Add to cart functionality
        const cartButtons = document.querySelectorAll('.add-to-cart');
        const cartCount = document.querySelector('.cart-count');
        let count = 3;

        cartButtons.forEach(button => {
            button.addEventListener('click', function() {
                count++;
                cartCount.textContent = count;
                this.textContent = '✓ Agregado';
                this.style.background = '#43e97b';
                
                setTimeout(() => {
                    this.textContent = 'Agregar';
                    this.style.background = '';
                }, 2000);
            });
        });

        // Newsletter form
        document.querySelector('.newsletter-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const button = this.querySelector('button');
            const input = this.querySelector('input');
            
            button.textContent = '✓ ¡Suscrito!';
            button.style.background = '#43e97b';
            input.value = '';
            
            setTimeout(() => {
                button.textContent = 'Suscribirse';
                button.style.background = '';
            }, 3000);
        });

        // Header scroll effect
        let lastScroll = 0;
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            const currentScroll = window.pageYOffset;
            
            if (currentScroll > 100) {
                header.style.padding = '0.8rem 0';
                header.style.boxShadow = '0 5px 30px rgba(0,0,0,0.15)';
            } else {
                header.style.padding = '1.2rem 0';
                header.style.boxShadow = '0 2px 20px rgba(0,0,0,0.1)';
            }
            
            lastScroll = currentScroll;
        });
    </script>
</body>
</html>
