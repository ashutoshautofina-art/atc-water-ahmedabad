<!-- ATC WATER - WordPress Integration Code -->
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<style>
    .wp-atc-wrapper {
        background-color: #00121e;
        color: #ffffff;
        font-family: 'Plus Jakarta Sans', sans-serif;
        border-radius: 20px;
        overflow: hidden;
        margin: 20px 0;
    }

    .wp-atc-wrapper * {
        box-sizing: border-box;
    }

    /* 3D Canvas Container */
    #hero-container-wp {
        position: relative;
        width: 100%;
        height: 500px;
        background: radial-gradient(circle at center, #002b45 0%, #000c18 100%);
        display: flex;
        align-items: center;
        justify-content: center;
        overflow: hidden;
    }

    #webgl-canvas-wp {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 1;
    }

    .hero-overlay-wp {
        position: relative;
        z-index: 2;
        text-align: center;
        max-width: 750px;
        padding: 24px;
        background: rgba(0, 15, 30, 0.65);
        backdrop-filter: blur(10px);
        border-radius: 24px;
        border: 1px solid rgba(0, 210, 255, 0.25);
        margin: 0 15px;
    }

    .hero-overlay-wp h1 {
        font-size: 2.5rem;
        font-weight: 800;
        color: #00D2FF;
        margin-bottom: 10px;
        line-height: 1.2;
    }

    .hero-overlay-wp p {
        font-size: 1.1rem;
        color: #cbd5e1;
        margin-bottom: 20px;
    }

    .btn-group-wp {
        display: flex;
        gap: 12px;
        justify-content: center;
        flex-wrap: wrap;
    }

    .btn-main-wp {
        background: linear-gradient(90deg, #0052CC, #00D2FF);
        color: #ffffff !important;
        padding: 12px 28px;
        font-size: 0.95rem;
        font-weight: 700;
        border-radius: 50px;
        text-decoration: none !important;
        display: inline-block;
        box-shadow: 0 0 15px rgba(0, 210, 255, 0.4);
        transition: 0.3s;
    }

    .btn-green-wp {
        background: #10B981;
        box-shadow: 0 0 15px rgba(16, 185, 129, 0.4);
    }

    /* Booking Card */
    .booking-card-wp {
        background: #ffffff;
        color: #0f172a;
        border-radius: 24px;
        padding: 30px;
        margin: -40px 20px 40px 20px;
        position: relative;
        z-index: 10;
        box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
    }

    .booking-grid-wp {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 16px;
        margin-top: 20px;
    }

    .form-group-wp {
        display: flex;
        flex-direction: column;
    }

    .form-group-wp label {
        font-weight: 700;
        margin-bottom: 6px;
        font-size: 0.85rem;
        color: #334155;
    }

    .form-group-wp input, .form-group-wp select {
        padding: 12px;
        border: 2px solid #e2e8f0;
        border-radius: 10px;
        font-size: 0.9rem;
        background: #f8fafc;
        color: #0f172a;
    }

    .btn-submit-wp {
        background: #10B981;
        color: white;
        font-weight: 800;
        padding: 14px;
        border: none;
        border-radius: 10px;
        cursor: pointer;
        font-size: 1rem;
        grid-column: 1 / -1;
        transition: 0.3s;
    }

    .btn-submit-wp:hover {
        background: #059669;
    }

    .section-padding-wp {
        padding: 40px 20px;
    }

    .tutorial-grid-wp {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
        gap: 20px;
    }

    .tutorial-step-wp {
        background: rgba(255, 255, 255, 0.05);
        border: 1px solid rgba(255, 255, 255, 0.1);
        border-radius: 16px;
        padding: 20px;
        text-align: center;
    }

    .step-number-wp {
        width: 40px;
        height: 40px;
        background: #00D2FF;
        color: #000;
        font-weight: 800;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 0 auto 12px auto;
    }
</style>

<div class="wp-atc-wrapper">
    <!-- 3D HERO canvas -->
    <div id="hero-container-wp">
        <canvas id="webgl-canvas-wp"></canvas>
        <div class="hero-overlay-wp">
            <h1>ATC WATER</h1>
            <p>हिमालय की शुद्धता - 100% Lab Tested Mineral Water in Ahmedabad</p>
            <div class="btn-group-wp">
                <a href="#booking-wp" class="btn-main-wp">💧 Order Now</a>
                <a href="https://wa.me/918200484728?text=Hi%20ATC%20WATER,%20I%20want%20to%20order%20drinking%20water." target="_blank" class="btn-main-wp btn-green-wp">💬 WhatsApp (+91 82004 84728)</a>
            </div>
        </div>
    </div>

    <!-- Quick Booking Form -->
    <div id="booking-wp" class="booking-card-wp">
        <h2 style="text-align: center; color: #0052CC; font-size: 1.6rem; margin-bottom: 5px;">⚡ Instant Water Order</h2>
        <p style="text-align: center; color: #64748b; margin-bottom: 15px; font-size: 0.9rem;">फॉर्म भरें और व्हाट्सएप पर तुरंत ऑर्डर प्राप्त करें</p>
        
        <form onsubmit="sendWpWhatsAppOrder(event)">
            <div class="booking-grid-wp">
                <div class="form-group-wp">
                    <label>ऑर्डर प्रकार</label>
                    <select id="wpOrderType">
                        <option value="B2C Home Delivery">Home Delivery (B2C)</option>
                        <option value="B2B Commercial Bulk">Commercial / Office (B2B Bulk)</option>
                    </select>
                </div>
                <div class="form-group-wp">
                    <label>प्रोडक्ट चुनें</label>
                    <select id="wpProductSelect">
                        <option value="20L Camper Jar (Rs 40)">20 LTR Camper / Jar - ₹40</option>
                        <option value="500ml Box (Rs 240/216)">500ml Box (24 Pcs) - ₹240 (B2C) / ₹216 (B2B)</option>
                        <option value="1000ml Box (Rs 480/430)">1000ml Box (24 Pcs) - ₹480 (B2C) / ₹430 (B2B)</option>
                    </select>
                </div>
                <div class="form-group-wp">
                    <label>मात्रा (Quantity)</label>
                    <input type="number" id="wpQty" value="1" min="1" required>
                </div>
                <div class="form-group-wp">
                    <label>आपका नाम</label>
                    <input type="text" id="wpName" placeholder="नाम लिखें" required>
                </div>
                <div class="form-group-wp">
                    <label>फ़ोन नंबर</label>
                    <input type="tel" id="wpPhone" placeholder="मोबाइल नंबर" required>
                </div>
                <div class="form-group-wp">
                    <label>अहमदाबाद डिलीवरी एड्रेस</label>
                    <input type="text" id="wpAddress" placeholder="एरिया व मकान नंबर" required>
                </div>
                <button type="submit" class="btn-submit-wp">📱 Order via WhatsApp (+91 82004 84728)</button>
            </div>
        </form>
    </div>

    <!-- Steps -->
    <div class="section-padding-wp">
        <h2 style="text-align: center; color: #00D2FF; margin-bottom: 20px;">Why Choose ATC WATER?</h2>
        <div class="tutorial-grid-wp">
            <div class="tutorial-step-wp">
                <div class="step-number-wp">1</div>
                <h3>7-Stage RO</h3>
                <p style="color: #94a3b8; font-size: 0.85rem;">प्रतिदिन TDS व pH लैब टेस्टिंग से शुद्ध पानी।</p>
            </div>
            <div class="tutorial-step-wp">
                <div class="step-number-wp">2</div>
                <h3>Automated Bottling</h3>
                <p style="color: #94a3b8; font-size: 0.85rem;">100% सीलबंद और बैक्टीरिया-मुक्त पैकेजिंग।</p>
            </div>
            <div class="tutorial-step-wp">
                <div class="step-number-wp">3</div>
                <h3>Fast Delivery</h3>
                <p style="color: #94a3b8; font-size: 0.85rem;">अहमदाबाद में ऑन-टाइम डोरस्टेप डिलीवरी।</p>
            </div>
        </div>
    </div>
</div>

<script>
    (function() {
        // Three.js 3D Droplet for WordPress
        const canvas = document.getElementById('webgl-canvas-wp');
        if (!canvas) return;
        
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, canvas.clientWidth / canvas.clientHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });

        renderer.setSize(canvas.clientWidth, canvas.clientHeight);

        const dropGeometry = new THREE.SphereGeometry(1.2, 32, 32);
        dropGeometry.scale(1, 1.4, 1);
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

        camera.position.z = 4;

        function animate() {
            requestAnimationFrame(animate);
            waterDrop.rotation.y += 0.01;
            waterDrop.position.y = Math.sin(Date.now() * 0.002) * 0.2;
            renderer.render(scene, camera);
        }
        animate();
    })();

    function sendWpWhatsAppOrder(e) {
        e.preventDefault();
        const type = document.getElementById('wpOrderType').value;
        const prod = document.getElementById('wpProductSelect').value;
        const qty = document.getElementById('wpQty').value;
        const name = document.getElementById('wpName').value;
        const phone = document.getElementById('wpPhone').value;
        const addr = document.getElementById('wpAddress').value;

        const message = `*New Order - ATC WATER*%0A%0A` +
                        `*Type:* ${type}%0A` +
                        `*Product:* ${prod}%0A` +
                        `*Qty:* ${qty}%0A` +
                        `*Name:* ${name}%0A` +
                        `*Phone:* ${phone}%0A` +
                        `*Address:* ${addr}, Ahmedabad`;

        window.open(`https://wa.me/918200484728?text=${message}`, '_blank');
    }
</script>
