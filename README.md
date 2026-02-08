<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For You ❤️</title>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;700;800&family=Pacifico&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Nunito', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 50%, #ffecd2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            position: relative;
        }

        /* Animated gradient background */
        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, 
                rgba(255, 154, 158, 0.3), 
                rgba(254, 207, 239, 0.3), 
                rgba(255, 140, 107, 0.3));
            animation: gradientShift 10s ease infinite;
            z-index: 0;
        }

        @keyframes gradientShift {
            0%, 100% { opacity: 0.5; transform: scale(1); }
            50% { opacity: 0.8; transform: scale(1.1); }
        }

        /* Floating background elements - FIXED */
        .bg-heart {
            position: absolute;
            font-size: 2rem;
            animation: float 6s linear infinite;
            z-index: 1;
            pointer-events: none;
            user-select: none;
            filter: drop-shadow(0 2px 4px rgba(255, 255, 255, 0.5));
        }

        @keyframes float {
            0% { 
                transform: translateY(100vh) rotate(0deg) scale(0.5); 
                opacity: 0; 
            }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { 
                transform: translateY(-100px) rotate(360deg) scale(1.2); 
                opacity: 0; 
            }
        }

        /* Sparkle effect */
        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            animation: sparkle 2s ease-in-out infinite;
            z-index: 1;
        }

        @keyframes sparkle {
            0%, 100% { opacity: 0; transform: scale(0); }
            50% { opacity: 1; transform: scale(1); }
        }

        /* The Main Card Container */
        .card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            width: 90%;
            max-width: 450px;
            padding: 50px 35px;
            border-radius: 35px;
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.2);
            text-align: center;
            position: relative;
            z-index: 10;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 4px solid rgba(255, 255, 255, 0.8);
            margin: 20px auto;
            min-height: auto;
        }

        .card::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, #ff9a9e, #fecfef, #ffdde1, #ee9ca7);
            border-radius: 37px;
            z-index: -1;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .card:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 30px 70px rgba(0, 0, 0, 0.25);
        }

        .card:hover::before {
            opacity: 0.5;
        }

        /* Hidden Sections */
        .section {
            display: none;
            flex-direction: column;
            align-items: center;
            animation: fadeIn 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .section.active {
            display: flex;
        }

        @keyframes fadeIn {
            from { 
                opacity: 0; 
                transform: scale(0.8) translateY(20px); 
            }
            to { 
                opacity: 1; 
                transform: scale(1) translateY(0); 
            }
        }

        /* Cute GIF styling */
        .gif-container {
            width: 170px;
            height: 170px;
            margin-bottom: 25px;
            border-radius: 50%;
            overflow: hidden;
            border: 6px solid #ffe0e6;
            background: white;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 10px 30px rgba(255, 77, 109, 0.3);
            animation: pulse 2s ease-in-out infinite;
            position: relative;
            z-index: 101;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        .gif-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* Emoji circle styling */
        .emoji-circle {
            background: linear-gradient(135deg, #fff5f7 0%, #ffe8ec 100%);
        }

        .big-emoji {
            font-family: 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji', sans-serif;
            font-size: 5rem;
            animation: emojiFloat 3s ease-in-out infinite;
            display: inline-block;
        }

        @keyframes emojiFloat {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            25% { transform: translateY(-10px) rotate(-5deg); }
            75% { transform: translateY(-5px) rotate(5deg); }
        }

        /* Different animations for each emoji */
        #step1 .big-emoji {
            animation: emojiPulse 1.5s ease-in-out infinite;
        }

        @keyframes emojiPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        #step2 .big-emoji {
            animation: emojiSpin 4s linear infinite;
        }

        @keyframes emojiSpin {
            0% { transform: rotate(0deg) scale(1); }
            25% { transform: rotate(-10deg) scale(1.1); }
            75% { transform: rotate(10deg) scale(1.1); }
            100% { transform: rotate(0deg) scale(1); }
        }

        #step3 .big-emoji {
            animation: emojiBounce 2s ease-in-out infinite;
        }

        @keyframes emojiBounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        #step4 .big-emoji {
            animation: emojiShake 0.5s ease-in-out infinite;
        }

        @keyframes emojiShake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px) rotate(-5deg); }
            75% { transform: translateX(5px) rotate(5deg); }
        }

        #step5 .big-emoji {
            animation: emojiCelebrate 0.6s ease-in-out infinite;
        }

        @keyframes emojiCelebrate {
            0%, 100% { transform: scale(1) rotate(0deg); }
            25% { transform: scale(1.2) rotate(-15deg); }
            75% { transform: scale(1.2) rotate(15deg); }
        }

        h1 {
            color: #ff4d6d;
            font-size: 2.3rem;
            font-weight: 800;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(255, 77, 109, 0.2);
            font-family: 'Pacifico', cursive;
        }

        p {
            color: #595959;
            font-size: 1.15rem;
            line-height: 1.7;
            margin-bottom: 25px;
            font-weight: 600;
        }

        /* Poem Text Specifics */
        .poem-line {
            font-style: italic;
            color: #ff758c;
            font-weight: 700;
            font-size: 1.25rem;
            margin-bottom: 15px;
            line-height: 1.8;
        }

        /* Button Styling */
        .btn-group {
            display: flex;
            gap: 15px;
            width: 100%;
            justify-content: center;
            position: relative;
            min-height: 50px;
        }

        @media (max-width: 480px) {
            .btn-group {
                min-height: 120px;
            }
        }

        .btn {
            padding: 14px 35px;
            border: none;
            border-radius: 50px;
            font-size: 1.15rem;
            font-weight: 800;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            font-family: 'Nunito', sans-serif;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .btn:hover::before {
            width: 300px;
            height: 300px;
        }

        .btn-next {
            background: linear-gradient(135deg, #ff4d6d 0%, #ff758c 100%);
            color: white;
            width: 100%;
            box-shadow: 0 6px 20px rgba(255, 77, 109, 0.4);
        }

        .btn-next:hover {
            box-shadow: 0 8px 25px rgba(255, 77, 109, 0.5);
        }

        .btn-yes {
            background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
            color: white;
            box-shadow: 0 6px 20px rgba(46, 204, 113, 0.4);
            flex: 1;
        }

        .btn-yes:hover {
            box-shadow: 0 8px 25px rgba(46, 204, 113, 0.5);
        }

        .btn-no {
            background: linear-gradient(135deg, #ff4757 0%, #e84118 100%);
            color: white;
            box-shadow: 0 6px 20px rgba(255, 71, 87, 0.4);
            transition: all 0.2s ease;
            flex: 1;
        }

        .btn-no:hover {
            box-shadow: 0 8px 25px rgba(255, 71, 87, 0.5);
        }

        .btn:hover {
            transform: scale(1.08);
        }
        
        .btn:active {
            transform: scale(0.97);
        }

        /* Progress Bar */
        .progress-dots {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-top: 30px;
        }

        .dot {
            width: 10px;
            height: 10px;
            background: #ddd;
            border-radius: 50%;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .dot.active {
            background: linear-gradient(135deg, #ff4d6d, #ff758c);
            transform: scale(1.4);
            box-shadow: 0 3px 10px rgba(255, 77, 109, 0.5);
        }

        /* Emoji fix - ensure proper rendering */
        .emoji {
            font-family: 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji', sans-serif;
            font-style: normal;
        }

        /* Celebration animation */
        @keyframes celebrate {
            0% { transform: scale(1) rotate(0deg); }
            25% { transform: scale(1.1) rotate(-5deg); }
            50% { transform: scale(1.2) rotate(5deg); }
            75% { transform: scale(1.1) rotate(-5deg); }
            100% { transform: scale(1) rotate(0deg); }
        }

        .celebrating {
            animation: celebrate 0.5s ease-in-out;
        }

        /* Responsive design */
        @media (max-width: 768px) {
            body {
                padding: 20px;
            }
            
            .card {
                padding: 35px 25px;
                max-width: 95%;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            .gif-container {
                width: 140px;
                height: 140px;
            }
            
            .big-emoji {
                font-size: 4rem;
            }
            
            .btn {
                padding: 12px 25px;
                font-size: 1rem;
            }
            
            p {
                font-size: 1rem;
            }
            
            .poem-line {
                font-size: 1.1rem;
            }
        }

        @media (max-width: 480px) {
            .card {
                padding: 30px 20px;
                border-radius: 25px;
            }
            
            h1 {
                font-size: 1.6rem;
                margin-bottom: 12px;
            }
            
            .gif-container {
                width: 120px;
                height: 120px;
                border: 4px solid #ffe0e6;
                margin-bottom: 20px;
            }
            
            .big-emoji {
                font-size: 3.5rem;
            }
            
            .btn {
                padding: 10px 20px;
                font-size: 0.95rem;
            }
            
            .btn-group {
                flex-direction: column;
                gap: 10px;
            }
            
            .btn-yes, .btn-no {
                width: 100%;
            }
            
            p {
                font-size: 0.95rem;
                margin-bottom: 20px;
            }
            
            .poem-line {
                font-size: 1rem;
                margin-bottom: 12px;
            }
            
            .progress-dots {
                margin-top: 20px;
                gap: 8px;
            }
            
            .dot {
                width: 8px;
                height: 8px;
            }
        }

        @media (max-width: 360px) {
            .card {
                padding: 25px 15px;
            }
            
            h1 {
                font-size: 1.4rem;
            }
            
            .gif-container {
                width: 100px;
                height: 100px;
            }
            
            .big-emoji {
                font-size: 3rem;
            }
            
            .btn {
                padding: 10px 18px;
                font-size: 0.9rem;
            }
            
            p {
                font-size: 0.9rem;
            }
            
            .poem-line {
                font-size: 0.95rem;
            }
        }

        /* Landscape mobile optimization */
        @media (max-height: 600px) and (orientation: landscape) {
            .card {
                padding: 20px;
                max-height: 90vh;
                overflow-y: auto;
            }
            
            .gif-container {
                width: 100px;
                height: 100px;
                margin-bottom: 15px;
            }
            
            .big-emoji {
                font-size: 3rem;
            }
            
            h1 {
                font-size: 1.5rem;
                margin-bottom: 10px;
            }
            
            p {
                font-size: 0.9rem;
                margin-bottom: 15px;
            }
            
            .btn {
                padding: 8px 20px;
            }
            
            .progress-dots {
                margin-top: 15px;
            }
        }

    </style>
</head>
<body>

    <div id="bg-hearts"></div>
    <div id="sparkles"></div>

    <div class="card">
        <div class="section active" id="step1">
            <div class="gif-container emoji-circle">
                <span class="big-emoji">🫶</span>
            </div>
            <h1>Hey Cutie! <span class="emoji">✨</span></h1>
            <p>I wrote something special for you...</p>
            <button class="btn btn-next" onclick="nextStep(2)">Show Me! <span class="emoji">💕</span></button>
        </div>

        <div class="section" id="step2">
            <div class="gif-container emoji-circle">
                <span class="big-emoji">😊</span>
            </div>
            <h1>Smile</h1>
            <p class="poem-line">"There is a place where your smile stays,<br>soft as morning light."</p>
            <p style="font-size: 1rem;">Your smile is literally my favorite thing.</p>
            <button class="btn btn-next" onclick="nextStep(3)">Next <span class="emoji">🌸</span></button>
        </div>

        <div class="section" id="step3">
            <div class="gif-container emoji-circle">
                <span class="big-emoji">🥰</span>
            </div>
            <h1>Memories</h1>
            <p class="poem-line">"If time were a river,<br>I would keep every second where you laughed."</p>
            <p style="font-size: 1rem;">Every moment with you is a core memory.</p>
            <button class="btn btn-next" onclick="nextStep(4)">Next <span class="emoji">✨</span></button>
        </div>

        <div class="section" id="step4">
            <div class="gif-container emoji-circle">
                <span class="big-emoji">🥺</span>
            </div>
            <h1>One Question...</h1>
            <p>Will you be my Valentine?</p>
            <div class="btn-group">
                <button class="btn btn-yes" onclick="nextStep(5)">YES! <span class="emoji">💖</span></button>
                <button class="btn btn-no" id="noBtn" onmouseover="moveNoButton()" ontouchstart="moveNoButton()">No <span class="emoji">💔</span></button>
            </div>
        </div>

        <div class="section" id="step5">
            <div class="gif-container emoji-circle">
                <span class="big-emoji">🤗</span>
            </div>
            <h1 style="position: relative; z-index: 101;">YAAAY! <span class="emoji">🎉</span></h1>
            <p style="position: relative; z-index: 101;">I knew you'd say yes! <br> I love you so much! <span class="emoji">❤️</span></p>
            <p class="poem-line" style="font-size: 1.1rem; position: relative; z-index: 101;">"Some smiles deserve to last forever."</p>
        </div>

        <div class="progress-dots">
            <div class="dot active" id="dot1"></div>
            <div class="dot" id="dot2"></div>
            <div class="dot" id="dot3"></div>
            <div class="dot" id="dot4"></div>
            <div class="dot" id="dot5"></div>
        </div>
    </div>

    <script>
        // Create sparkles
        function createSparkles() {
            const container = document.getElementById('sparkles');
            for(let i = 0; i < 20; i++) {
                const sparkle = document.createElement('div');
                sparkle.className = 'sparkle';
                sparkle.style.left = Math.random() * 100 + 'vw';
                sparkle.style.top = Math.random() * 100 + 'vh';
                sparkle.style.animationDelay = Math.random() * 2 + 's';
                container.appendChild(sparkle);
            }
        }
        createSparkles();

        // Background Hearts - FIXED VERSION
        function createHearts() {
            const container = document.getElementById('bg-hearts');
            // Using Unicode representation for better compatibility
            const hearts = [
                '\u2764\uFE0F',  // ❤️
                '\u{1F496}',     // 💖
                '\u{1F338}',     // 🌸
                '\u2728',        // ✨
                '\u{1F353}'      // 🍓
            ];
            
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'bg-heart';
                heart.style.fontFamily = "'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji', sans-serif";
                
                // Create text node with emoji
                const emoji = hearts[Math.floor(Math.random() * hearts.length)];
                heart.textContent = emoji;
                
                // Random color tint
                const colors = ['rgba(255, 77, 109, 0.4)', 'rgba(255, 117, 140, 0.4)', 'rgba(255, 192, 203, 0.4)'];
                heart.style.color = colors[Math.floor(Math.random() * colors.length)];
                
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDuration = (Math.random() * 3 + 4) + 's'; // 4-7s
                heart.style.fontSize = (Math.random() * 1.5 + 1.5) + 'rem'; // 1.5-3rem
                
                container.appendChild(heart);
                
                setTimeout(() => heart.remove(), 7000);
            }, 400);
        }
        createHearts();

        // Navigation Logic with animation
        function nextStep(step) {
            // Add celebration animation to card
            const card = document.querySelector('.card');
            card.classList.add('celebrating');
            setTimeout(() => card.classList.remove('celebrating'), 500);

            // Hide all sections
            document.querySelectorAll('.section').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.dot').forEach(el => el.classList.remove('active'));

            // Show current section
            document.getElementById('step' + step).classList.add('active');
            document.getElementById('dot' + step).classList.add('active');

            // Celebration confetti
            if(step === 5) {
                setTimeout(() => confettiEffect(), 300);
            }
        }

        // Moving 'No' Button Logic - IMPROVED
        let noButtonClickCount = 0;
        function moveNoButton() {
            const btn = document.getElementById('noBtn');
            const btnGroup = btn.parentElement;
            
            noButtonClickCount++;
            
            // Make button smaller each time
            const newScale = Math.max(0.5, 1 - (noButtonClickCount * 0.1));
            btn.style.transform = `scale(${newScale})`;
            
            // On mobile, make it simpler - just move within safer bounds
            const isMobile = window.innerWidth <= 768;
            
            if (isMobile) {
                // Simpler movement for mobile
                const positions = [
                    { left: '10px', top: '0px' },
                    { left: 'auto', right: '10px', top: '0px' },
                    { left: '50%', top: '60px', transform: `translateX(-50%) scale(${newScale})` },
                    { left: '10px', top: '60px' },
                    { left: 'auto', right: '10px', top: '60px' }
                ];
                
                const pos = positions[noButtonClickCount % positions.length];
                btn.style.position = 'absolute';
                Object.assign(btn.style, pos);
            } else {
                // Desktop version - more dynamic movement
                const maxX = btnGroup.offsetWidth - btn.offsetWidth - 10;
                const maxY = 100;
                
                const randomX = Math.random() * maxX;
                const randomY = (Math.random() - 0.5) * maxY;
                
                btn.style.position = 'absolute';
                btn.style.left = randomX + 'px';
                btn.style.top = randomY + 'px';
            }
            
            btn.style.transition = 'all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275)';
            
            // After several attempts, change button text
            if(noButtonClickCount === 3) {
                btn.innerHTML = 'Please? <span class="emoji">🥺</span>';
            }
            if(noButtonClickCount === 5) {
                btn.innerHTML = 'Pretty please? <span class="emoji">🥹</span>';
            }
            if(noButtonClickCount === 7) {
                btn.innerHTML = 'You know you want to! <span class="emoji">😊</span>';
            }
        }

        // Enhanced confetti effect
        function confettiEffect() {
            const emojis = ['\u{1F389}', '\u{1F38A}', '\u2764\uFE0F', '\u{1F496}', '\u2728', '\u{1F338}'];
            
            for(let i = 0; i < 80; i++) {
                setTimeout(() => {
                    const conf = document.createElement('div');
                    conf.className = 'bg-heart';
                    conf.style.position = 'fixed';
                    conf.style.left = '50%';
                    conf.style.top = '50%';
                    conf.style.fontFamily = "'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji', sans-serif";
                    conf.textContent = emojis[Math.floor(Math.random() * emojis.length)];
                    conf.style.fontSize = (Math.random() * 2 + 1.5) + 'rem';
                    conf.style.zIndex = '5';
                    document.body.appendChild(conf);

                    const angle = (Math.random() * Math.PI * 2);
                    const velocity = Math.random() * 400 + 300;
                    const x = Math.cos(angle) * velocity;
                    const y = Math.sin(angle) * velocity - 200; // Bias upward

                    setTimeout(() => {
                        conf.style.transition = 'all 1.5s cubic-bezier(0.25, 0.46, 0.45, 0.94)';
                        conf.style.transform = `translate(${x}px, ${y}px) rotate(${Math.random() * 720 - 360}deg)`;
                        conf.style.opacity = '0';
                    }, 20);
                    
                    setTimeout(() => conf.remove(), 1500);
                }, i * 20);
            }
        }

        // Add some nice touch interactions
        document.querySelectorAll('.btn').forEach(btn => {
            btn.addEventListener('touchstart', function() {
                this.style.transform = 'scale(0.95)';
            });
            btn.addEventListener('touchend', function() {
                this.style.transform = '';
            });
        });
    </script>
</body>
</html>
