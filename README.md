<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ATC WATER - Himalayan Pure Mineral Water | Ahmedabad</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">
    <!-- Tested Three.js CDN -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        :root {
            --primary-dark: #00121e;
            --ocean-blue: #0052CC;
            --cyan-glow: #00D2FF;
            --leaf-green: #10B981;
            --card-white: #ffffff;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Plus Jakarta Sans', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--primary-dark);
            color: #ffffff;
            overflow-x: hidden;
        }

        /* 3D WebGL Hero Container */
        #hero-container {
            position: relative;
            width: 100vw;
            height: 80vh;
            background: radial-gradient(circle at center, #002b45 0%, #000c18 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        #webgl-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .hero-overlay {
            position: relative;
            z-index: 2;
            text-align: center;
            max-width: 800px;
            padding: 24px;
            background: rgba(0, 15, 30, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            border: 1px solid rgba(0, 210, 255, 0.25);
            margin: 0 15px;
        }

        .hero-overlay h1 {
            font-size: 2.8rem;
            font-weight: 800;
            background: linear-gradient(90deg, #ffffff, var(--cyan-glow));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 12px;
        }

        .hero-overlay p {
            font-size: 1.15rem;
            color: #cbd5e1;
            margin-bottom: 24px;
            line-height: 1.5;
        }

        .btn-group {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn-main {
            background: linear-gradient(90deg, var(--ocean-blue), var(--cyan-glow));
            color: #ffffff;
            padding: 14px 32px;
            font-size: 1rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(0, 210, 255, 0.4);
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .btn-main:hover {
            transform: translateY(-2px);
            box-shadow: 0 0 30px rgba(0, 210, 255, 0.7);
        }

        .btn-green {
            background: var(--leaf-green);
            box-shadow: 0 0 20px rgba(16, 185, 129, 0.4);
        }

        .btn-green:hover {
            box-shadow: 0 0 30px rgba(16, 185, 129, 0.7);
        }

        /* Layout & Sections */
        .section-padding {
            padding: 70px 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.2rem;
            font-weight: 800;
            margin-bottom: 12px;
            color: var(--cyan-glow);
        }

        .section-subtitle {
            text-align: center;
            color: #94a3b8;
            margin-bottom: 40px;
            font-size: 1rem;
        }

        /* Quick Booking Form */
        .booking-card {
            background: var(--card-white);
            color: #0f172a;
            border-radius: 24px;
            padding: 36px;
            box-shadow: 0 20px 50px rgba(0, 210, 255, 0.15);
            margin-top: -50px;
            position: relative;
            z-index: 10;
        }

        .booking-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            font-weight: 700;
            margin-bottom: 8px;
            font-size: 0.9rem;
            color: #334155;
        }

        .form-group input, .form-group select {
            padding: 14px;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            font-size: 0.95rem;
            outline: none;
            transition: 0.3s;
            background: #f8fafc;
            color: #0f172a;
        }

        .form-group input:focus, .form-group select:focus {
            border-color: var(--ocean-blue);
            background: #ffffff;
        }

        .btn-submit {
            background: var(--leaf-green);
            color: white;
            font-weight: 800;
            padding: 16px;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            font-size: 1.1rem;
            grid-column: 1 / -1;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(16, 185, 129, 0.3);
        }

        .btn-submit:hover {
            background: #059669;
        }

        /* Quality Steps */
        .tutorial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }

        .tutorial-step {
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 20px;
            padding: 28px;
            text-align: center;
        }

        .step-number {
            width: 48px;
            height: 48px;
            background: var(--cyan-glow);
            color: #000;
            font-weight: 800;
            font-size: 1.3rem;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 18px auto;
        }

        /* Offers */
        .ads-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 24px;
        }

        .ad-banner {
            background: linear-gradient(135deg, #002b45, #00121e);
            border: 2px dashed var(--cyan-glow);
            border-radius: 20px;
            padding: 28px;
        }

        .ad-badge {
            background: #ef4444;
            color: white;
            padding: 4px 12px;
            font-size: 0.75rem;
            font-weight: 800;
            border-radius: 12px;
            display: inline-block;
            margin-bottom: 12px;
        }

        /* Footer */
        footer {
            background: #000810;
            border-top: 1px solid rgba(255, 255, 255, 0.08);
            padding: 60px 20px 24px 20px;
        }

        .footer-grid {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 36px;
            margin-bottom: 40px;
        }

        .footer-col h3 {
            color: var(--cyan-glow);
            margin-bottom: 16px;
            font-size: 1.2rem;
        }

        .footer-col p {
            color: #94a3b8;
            line-height: 1.6;
            font-size: 0.95rem;
            margin-bottom: 8px;
        }

        .footer-col a {
            color: var(--cyan-glow);
            text-decoration: none;
            font-weight: 700;
        }

        .copyright {
            text-align: center;
            color: #64748b;
            font-size: 0.85rem;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            padding-top: 20px;
        }
    </style>
</head>
<body>

    <!-- 3D WebGL Canvas Hero Section -->
    <div id="hero-container">
        <canvas id="webgl-canvas"></canvas>
        <div class="hero-overlay">
            <h1>ATC WATER</h1>
            <p>हिमालय की शुद्धता - 100% Lab Tested RO & Mineral Water in Ahmedabad</p>
            <div class="btn-group">
                <a href="#booking" class="btn-main">💧 1-Click Order Now</a>
                <a href="https://wa.me/918200484728?text=Hi%20ATC%20WATER,%20I%20want%20to%20order%20drinking%20water." target="_blank" class="btn-main btn-green">💬 WhatsApp (+91 82004 84728)</a>
            </div>
        </div>
    </div>

    <!-- 1. Quick Booking Form -->
    <section id="booking" class="section-padding">
        <div class="booking-card">
            <h2 style="text-align: center; color: var(--ocean-blue); font-size: 1.8rem;">⚡ Instant Water Booking</h2>
            <p style="text-align: center; color: #64748b; margin-bottom: 20px;">फॉर्म भरें और व्हाट्सएप पर तुरंत ऑर्डर कन्फर्म करें</p>
            
            <form onsubmit="sendWhatsAppOrder(event)">
                <div class="booking-grid">
                    <div class="form-group">
                        <label>ऑर्डर का प्रकार (Order Type)</label>
                        <select id="orderType">
                            <option value="B2C Home Delivery">Home Delivery (B2C)</option>
                            <option value="B2B Commercial Bulk">Commercial / Office (B2B Bulk)</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>प्रोडक्ट चुनें (Select Product)</label>
                        <select id="productSelect">
                            <option value="20L Camper Jar (Rs 40)">20 LTR Camper / Jar - ₹40</option>
                            <option value="500ml Box 24 Pcs (Rs 240/216)">500ml Box (24 Pcs) - ₹240 (B2C) / ₹216 (B2B)</option>
                            <option value="1000ml Box 24 Pcs (Rs 480/430)">1000ml Box (24 Pcs) - ₹480 (B2C) / ₹430 (B2B)</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>मात्रा (Quantity)</label>
                        <input type="number" id="qty" value="1" min="1" required>
                    </div>
                    <div class="form-group">
                        <label>आपका नाम (Full Name)</label>
                        <input type="text" id="custName" placeholder="उदा. राहुल पटेल" required>
                    </div>
                    <div class="form-group">
                        <label>फ़ोन नंबर (Phone Number)</label>
                        <input type="tel" id="custPhone" placeholder="10 अंक का मोबाइल नंबर" required>
                    </div>
                    <div class="form-group">
                        <label>अहमदाबाद का पता (Delivery Address)</label>
                        <input type="text" id="custAddress" placeholder="एरिया व मकान/ऑफिस नंबर" required>
                    </div>
                    <button type="submit" class="btn-submit">📱 Send Order to WhatsApp (+91 82004 84728)</button>
                </div>
            </form>
        </div>
    </section>

    <!-- 2. Tutorial & Quality Steps -->
    <section class="section-padding">
        <h2 class="section-title">Quality & Order Tutorial</h2>
        <p class="section-subtitle">ATC WATER की शुद्धता प्रक्रिया और डिलीवरी के 3 आसान चरण</p>
        
        <div class="tutorial-grid">
            <div class="tutorial-step">
                <div class="step-number">1</div>
                <h3>7-Stage RO Filtration</h3>
                <p style="color: #cbd5e1; font-size: 0.95rem;">प्रतिदिन TDS व pH लैब टेस्टिंग द्वारा सुरक्षित और मीठे पानी का उत्पादन।</p>
            </div>
            <div class="tutorial-step">
                <div class="step-number">2</div>
                <h3>Automated Bottling</h3>
                <p style="color: #cbd5e1; font-size: 0.95rem;">बिना किसी मानवीय स्पर्श के 100% बैक्टीरिया-मुक्त सीलबंद पैकेजिंग।</p>
            </div>
            <div class="tutorial-step">
                <div class="step-number">3</div>
                <h3>Doorstep Delivery</h3>
                <p style="color: #cbd5e1; font-size: 0.95rem;">अहमदाबाद में आपके घर या ऑफिस पर तय समय पर त्वरित डिलीवरी।</p>
            </div>
        </div>
    </section>

    <!-- 3. Offers -->
    <section class="section-padding">
        <h2 class="section-title">Special Offers & B2B Rates</h2>
        <p class="section-subtitle">होटलों, ऑफिसों और कॉर्पोरेट इवेंट्स के लिए विशेष डिस्काउंट्स</p>

        <div class="ads-grid">
            <div class="ad-banner">
                <span class="ad-badge">B2B SPECIAL</span>
                <h3>Hotels & Restaurant Bulk Supply</h3>
                <p style="margin: 12px 0; color: #cbd5e1; font-size: 0.95rem;">500ml एवं 1000ml बॉटल बॉक्स पर बल्क ऑर्डर्स पर विशेष रियायती दरें।</p>
                <a href="#booking" style="color: var(--cyan-glow); font-weight: 700; text-decoration: none;">ऑर्डर करें →</a>
            </div>
            <div class="ad-banner">
                <span class="ad-badge">HOME PASS</span>
                <h3>Monthly Household Water Pass</h3>
                <p style="margin: 12px 0; color: #cbd5e1; font-size: 0.95rem;">20L पानी के कैन की दैनिक डिलीवरी के लिए मंथली कार्ड बनवाएँ।</p>
                <a href="#booking" style="color: var(--cyan-glow); font-weight: 700; text-decoration: none;">कार्ड बनवाएँ →</a>
            </div>
        </div>
    </section>

    <!-- 4. Footer -->
    <footer>
        <div class="footer-grid">
            <div class="footer-col">
                <h3>ATC WATER</h3>
                <p>अहमदाबाद का भरोसेमंद RO एवं मिनरल वॉटर ब्रांड। 100% हाइजीनिक और लैब-टेस्टेड पानी।</p>
                <p style="margin-top: 12px; color: var(--cyan-glow); font-weight: 700;">FSSAI License | IS 14543 ISI Certified</p>
            </div>
            <div class="footer-col">
                <h3>Rates & Pricing</h3>
                <p>• 20L Camper: ₹40</p>
                <p>• 500ml Box (24 Pcs): ₹240 (B2C) / ₹216 (B2B)</p>
                <p>• 1000ml Box (24 Pcs): ₹480 (B2C) / ₹430 (B2B)</p>
            </div>
            <div class="footer-col">
                <h3>Contact & Location</h3>
                <p>📍 Plant: Ahmedabad, Gujarat, India</p>
                <p>📞 Phone: <a href="tel:8200484728">+91 82004 84728</a></p>
                <p>💬 WhatsApp: <a href="https://wa.me/918200484728" target="_blank">+91 82004 84728</a></p>
            </div>
        </div>
        <div class="copyright">
            © 2026 ATC WATER. All Rights Reserved. Mobile / WhatsApp: +91 82004 84728
        </div>
    </footer>

    <!-- Three.js 3D Droplet Script & WhatsApp Dispatcher -->
    <script>
        const canvas = document.getElementById('webgl-canvas');
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / (window.innerHeight * 0.8), 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });

        renderer.setSize(window.innerWidth, window.innerHeight * 0.8);

        const dropGeometry = new THREE.SphereGeometry(1.2, 32, 32);
        dropGeometry.scale(1, 1.5, 1);
        const dropMaterial = new THREE.MeshPhongMaterial({
            color: 0x00d2ff,
            emissive: 0x002b45,
            specular: 0xffffff,
            shininess: 100,
            transparent: true,
            opacity: 0.9
        });
        const waterDrop = new THREE.Mesh(dropGeometry, dropMaterial);
        scene.add(waterDrop);

        const pointLight = new THREE.PointLight(0xffffff, 1.5);
        pointLight.position.set(5, 5, 5);
        scene.add(pointLight);

        const ambientLight = new THREE.AmbientLight(0x001122);
        scene.add(ambientLight);

        camera.position.z = 4.5;

        function animate() {
            requestAnimationFrame(animate);
            waterDrop.rotation.y += 0.01;
            waterDrop.position.y = Math.sin(Date.now() * 0.002) * 0.25;
            renderer.render(scene, camera);
        }
        animate();

        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / (window.innerHeight * 0.8);
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight * 0.8);
        });

        function sendWhatsAppOrder(e) {
            e.preventDefault();
            const type = document.getElementById('orderType').value;
            const prod = document.getElementById('productSelect').value;
            const qty = document.getElementById('qty').value;
            const name = document.getElementById('custName').value;
            const phone = document.getElementById('custPhone').value;
            const addr = document.getElementById('custAddress').value;

            const message = `*New Order - ATC WATER*%0A%0A` +
                            `*Order Type:* ${type}%0A` +
                            `*Product:* ${prod}%0A` +
                            `*Quantity:* ${qty}%0A` +
                            `*Customer Name:* ${name}%0A` +
                            `*Customer Phone:* ${phone}%0A` +
                            `*Delivery Address:* ${addr}, Ahmedabad`;

            window.open(`https://wa.me/918200484728?text=${message}`, '_blank');
        }
    </script>
</body>
</html>
