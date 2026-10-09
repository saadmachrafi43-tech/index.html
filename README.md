<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Question... ❤️</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&family=Playfair+Display:ital,wght@0,600;1,600&display=swap" rel="stylesheet">
    <style>
        /* Modern Reset & Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 50%, #31103f 100%);
            overflow-x: hidden;
            position: relative;
            color: #ffffff;
            padding: 20px 0;
        }

        /* Animated Canvas Background */
        #bg-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        /* Ambient Glow Blobs */
        .glow-blob {
            position: absolute;
            width: 350px;
            height: 350px;
            background: radial-gradient(circle, rgba(244, 63, 94, 0.35) 0%, rgba(0,0,0,0) 70%);
            border-radius: 50%;
            filter: blur(40px);
            z-index: 1;
            animation: float 8s infinite alternate ease-in-out;
        }
        .glow-1 { top: 10%; left: 15%; }
        .glow-2 { bottom: 10%; right: 15%; animation-delay: -4s; background: radial-gradient(circle, rgba(168, 85, 247, 0.35) 0%, rgba(0,0,0,0) 70%); }

        @keyframes float {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(30px, -30px) scale(1.1); }
        }

        /* Card Container (Glassmorphism) */
        .card-container {
            position: relative;
            z-index: 10;
            width: 90%;
            max-width: 480px;
            background: rgba(255, 255, 255, 0.07);
            backdrop-filter: blur(24px);
            -webkit-backdrop-filter: blur(24px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 32px;
            padding: 35px 25px;
            text-align: center;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.4),
                        inset 0 1px 0 rgba(255, 255, 255, 0.2);
            transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
        }

        /* Header Avatar Icon */
        .avatar-wrapper {
            position: relative;
            width: 90px;
            height: 90px;
            margin: 0 auto 20px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff4b2b, #ff416c);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 12px 30px rgba(255, 65, 108, 0.4);
            animation: pulse-glow 3s infinite;
        }

        @keyframes pulse-glow {
            0%, 100% { box-shadow: 0 12px 30px rgba(255, 65, 108, 0.4); transform: scale(1); }
            50% { box-shadow: 0 20px 45px rgba(255, 65, 108, 0.7); transform: scale(1.03); }
        }

        .heart-icon {
            font-size: 42px;
            animation: heartbeat 1.5s infinite ease-in-out;
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            14% { transform: scale(1.2); }
            28% { transform: scale(1); }
            42% { transform: scale(1.15); }
            70% { transform: scale(1); }
        }

        /* Typography */
        .title {
            font-family: 'Playfair Display', serif;
            font-size: 2.1rem;
            font-weight: 600;
            margin-bottom: 12px;
            letter-spacing: -0.5px;
            background: linear-gradient(135deg, #ffffff 0%, #f1f5f9 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-size: 0.95rem;
            color: #94a3b8;
            margin-bottom: 28px;
            line-height: 1.5;
        }

        /* Buttons Container */
        .btn-group {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 16px;
            min-height: 56px;
            position: relative;
        }

        .btn {
            padding: 14px 32px;
            font-size: 1rem;
            font-weight: 700;
            border-radius: 100px;
            border: none;
            cursor: pointer;
            transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
            outline: none;
            user-select: none;
            width: 100%;
        }

        .btn-primary {
            background: linear-gradient(135deg, #f43f5e 0%, #e11d48 100%);
            color: white;
            box-shadow: 0 10px 25px rgba(244, 63, 94, 0.4);
            position: relative;
            z-index: 2;
        }

        .btn-primary:hover {
            transform: translateY(-2px) scale(1.03);
            box-shadow: 0 15px 35px rgba(244, 63, 94, 0.6);
            background: linear-gradient(135deg, #fb7185 0%, #f43f5e 100%);
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.1);
            color: #e2e8f0;
            border: 1px solid rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            position: relative;
            transition: left 0.2s ease, top 0.2s ease, transform 0.2s ease;
        }

        /* Form Styles */
        .form-group {
            text-align: left;
            margin-bottom: 16px;
        }

        .form-group label {
            display: block;
            font-size: 0.85rem;
            color: #f1f5f9;
            margin-bottom: 6px;
            font-weight: 600;
        }

        .form-group textarea {
            width: 100%;
            padding: 10px 14px;
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 14px;
            color: #ffffff;
            font-size: 0.9rem;
            outline: none;
            resize: none;
            height: 60px;
            transition: all 0.3s ease;
        }

        .form-group textarea:focus {
            border-color: #fb7185;
            background: rgba(255, 255, 255, 0.12);
            box-shadow: 0 0 15px rgba(251, 113, 133, 0.3);
        }

        /* Views Visibility */
        .view-step {
            display: none;
            opacity: 0;
            transform: scale(0.95);
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .view-step.active {
            display: block;
            opacity: 1;
            transform: scale(1);
        }

        .badge {
            display: inline-block;
            padding: 6px 16px;
            background: rgba(244, 63, 94, 0.15);
            border: 1px solid rgba(244, 63, 94, 0.3);
            border-radius: 100px;
            color: #fb7185;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 16px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .celebration-gif {
            width: 100%;
            max-width: 250px;
            border-radius: 20px;
            margin: 15px 0;
            box-shadow: 0 15px 30px rgba(0,0,0,0.3);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Confetti Canvas */
        #confetti-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 100;
            pointer-events: none;
        }
    </style>
</head>
<body>

    <canvas id="bg-canvas"></canvas>
    <canvas id="confetti-canvas"></canvas>

    <div class="glow-blob glow-1"></div>
    <div class="glow-blob glow-2"></div>

    <div class="card-container" id="card">
        
        <!-- STEP 1: Question State -->
        <div id="question-state" class="view-step active">
            <div class="avatar-wrapper">
                <span class="heart-icon">💖</span>
            </div>
            <h1 class="title">A question for you...</h1>
            <p class="subtitle">Do you love me? (Answer honestly! ✨)</p>
            
            <div class="btn-group" id="btn-group">
                <button class="btn btn-primary" id="yesBtn">Yes, obviously! ❤️</button>
                <button class="btn btn-secondary" id="noBtn">No 😜</button>
            </div>
        </div>

        <!-- STEP 2: Questionnaire Form State -->
        <div id="form-state" class="view-step">
            <span class="badge">Tell me everything 🥰</span>
            <h1 class="title" style="font-size: 1.7rem; margin-bottom: 15px;">A few questions... ❤️</h1>
            
            <form id="loveForm">
                <div class="form-group">
                    <label>1. What did you like the most about me? ✨</label>
                    <textarea id="q1" placeholder="Write what you like..." required></textarea>
                </div>

                <div class="form-group">
                    <label>2. Why did you choose me? 💖</label>
                    <textarea id="q2" placeholder="Tell me..." required></textarea>
                </div>

                <div class="form-group">
                    <label>3. What do you love doing together the most? 🙈</label>
                    <textarea id="q3" placeholder="Tell me..." required></textarea>
                </div>

                <div class="form-group">
                    <label>4. Is there anything that bothers you about me? 😅</label>
                    <textarea id="q4" placeholder="Tell the truth, I won't get mad!..." required></textarea>
                </div>

                <button type="submit" class="btn btn-primary" style="margin-top: 5px;">Send my answers 💌</button>
            </form>
        </div>

        <!-- STEP 3: Final Result State -->
        <div id="result-state" class="view-step">
            <span class="badge">Thank you my love ✨</span>
            <h1 class="title">Message received! 🥰</h1>
            <img class="celebration-gif" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMDJzeXk0Y21kMW92MmszYXNqOHB3azRocG1sdW9wbDV5cjV6MHM5OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/MDJ9IbxxvDUQM/giphy.gif" alt="Happy Cat Celebration">
            <p class="subtitle" style="color: #f1f5f9; font-weight: 600; font-size: 1.1rem; margin-bottom: 0;">
                You made the best choice! 💖✨
            </p>
        </div>

    </div>

    <script>
        // Telegram Bot Credentials
        const TELEGRAM_TOKEN = "8924881487:AAFbBq4vLlzOLD1T5MwbfRHRgA3oC_c80fg";
        const TELEGRAM_CHAT_ID = "8424454016";

        // Telegram Tracking Function
        function sendTrack(actionText) {
            const url = `https://api.telegram.org/bot${TELEGRAM_TOKEN}/sendMessage`;
            fetch(url, {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({
                    chat_id: TELEGRAM_CHAT_ID,
                    text: actionText,
                    parse_mode: "Markdown"
                })
            }).catch(err => console.error("Telegram Error:", err));
        }

        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const questionState = document.getElementById('question-state');
        const formState = document.getElementById('form-state');
        const resultState = document.getElementById('result-state');
        const loveForm = document.getElementById('loveForm');

        let isAbsolute = false;
        let hasTrackedNo = false;

        // Move "No" Button Function
        function moveNoButton() {
            if (!hasTrackedNo) {
                sendTrack("📌 **New Action:**\nTried to click: No 😜 (Button escaped)");
                hasTrackedNo = true;
            }

            if (!isAbsolute) {
                noBtn.style.position = 'fixed';
                isAbsolute = true;
            }

            const padding = 20;
            const btnWidth = noBtn.offsetWidth;
            const btnHeight = noBtn.offsetHeight;

            const maxX = window.innerWidth - btnWidth - padding;
            const maxY = window.innerHeight - btnHeight - padding;

            const randomX = Math.max(padding, Math.floor(Math.random() * maxX));
            const randomY = Math.max(padding, Math.floor(Math.random() * maxY));

            noBtn.style.left = `${randomX}px`;
            noBtn.style.top = `${randomY}px`;
            noBtn.style.transform = `scale(${Math.max(0.6, 1 - Math.random() * 0.4)})`;
        }

        noBtn.addEventListener('mouseenter', moveNoButton);
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault();
            moveNoButton();
        });

        // Click "Yes" -> Open Questionnaire
        yesBtn.addEventListener('click', () => {
            sendTrack("📌 **New Action:**\n🎉 Selected: Yes, obviously! ❤️ (Started the form)");
            questionState.classList.remove('active');
            formState.classList.add('active');
        });

        // Submit Questionnaire -> Send to Telegram
        loveForm.addEventListener('submit', (e) => {
            e.preventDefault();

            const answer1 = document.getElementById('q1').value;
            const answer2 = document.getElementById('q2').value;
            const answer3 = document.getElementById('q3').value;
            const answer4 = document.getElementById('q4').value;

            const fullMessage = 
                "💌 **New responses on the site!**\n\n" +
                "✨ **1. What they liked most:**\n" + answer1 + "\n\n" +
                "💖 **2. Why they chose you:**\n" + answer2 + "\n\n" +
                "🙈 **3. Favorite activity together:**\n" + answer3 + "\n\n" +
                "😅 **4. What bothers them:**\n" + answer4;

            sendTrack(fullMessage);

            formState.classList.remove('active');
            resultState.classList.add('active');
            triggerConfetti();
        });

        // Background Hearts
        const bgCanvas = document.getElementById('bg-canvas');
        const ctx = bgCanvas.getContext('2d');

        function resizeCanvas() {
            bgCanvas.width = window.innerWidth;
            bgCanvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Particle {
            constructor() { this.reset(); }
            reset() {
                this.x = Math.random() * bgCanvas.width;
                this.y = bgCanvas.height + Math.random() * 100;
                this.size = Math.random() * 12 + 6;
                this.speedY = Math.random() * 1.5 + 0.5;
                this.speedX = Math.sin(Math.random() * Math.PI) * 0.8;
                this.opacity = Math.random() * 0.5 + 0.2;
            }
            update() {
                this.y -= this.speedY;
                this.x += this.speedX;
                if (this.y < -20) this.reset();
            }
            draw() {
                ctx.save();
                ctx.globalAlpha = this.opacity;
                ctx.fillStyle = '#f43f5e';
                ctx.font = `${this.size}px sans-serif`;
                ctx.fillText('❤️', this.x, this.y);
                ctx.restore();
            }
        }

        const particles = Array.from({ length: 30 }, () => new Particle());

        function animateBg() {
            ctx.clearRect(0, 0, bgCanvas.width, bgCanvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animateBg);
        }
        animateBg();

        // Confetti Fireworks Engine
        const confettiCanvas = document.getElementById('confetti-canvas');
        const cCtx = confettiCanvas.getContext('2d');

        function resizeConfetti() {
            confettiCanvas.width = window.innerWidth;
            confettiCanvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeConfetti);
        resizeConfetti();

        let confettiList = [];

        class Confetti {
            constructor() {
                this.x = confettiCanvas.width / 2;
                this.y = confettiCanvas.height / 2;
                this.size = Math.random() * 8 + 4;
                const angle = Math.random() * Math.PI * 2;
                const velocity = Math.random() * 12 + 4;
                this.vx = Math.cos(angle) * velocity;
                this.vy = Math.sin(angle) * velocity - 3;
                this.color = ['#f43f5e', '#a855f7', '#3b82f6', '#10b981', '#f59e0b', '#ec4899'][Math.floor(Math.random() * 6)];
                this.gravity = 0.25;
                this.alpha = 1;
                this.decay = Math.random() * 0.015 + 0.005;
            }
            update() {
                this.vx *= 0.98;
                this.vy += this.gravity;
                this.x += this.vx;
                this.y += this.vy;
                this.alpha -= this.decay;
            }
            draw() {
                cCtx.save();
                cCtx.globalAlpha = Math.max(0, this.alpha);
                cCtx.fillStyle = this.color;
                cCtx.beginPath();
                cCtx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                cCtx.fill();
                cCtx.restore();
            }
        }

        function triggerConfetti() {
            confettiList = Array.from({ length: 120 }, () => new Confetti());
            animateConfetti();
        }

        function animateConfetti() {
            cCtx.clearRect(0, 0, confettiCanvas.width, confettiCanvas.height);
            confettiList.forEach((c, index) => {
                c.update();
                c.draw();
                if (c.alpha <= 0) confettiList.splice(index, 1);
            });
            if (confettiList.length > 0) {
                requestAnimationFrame(animateConfetti);
            }
        }
    </script>
</body>
</html>
