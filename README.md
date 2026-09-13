<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Verifikasi Follow • AzferModz</title>
    <style>
        /* ==================== LOADING SCREEN STYLES ==================== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Poppins', Roboto, system-ui, sans-serif;
        }

        body {
            background: radial-gradient(ellipse at center, #1a0000 0%, #0a0000 50%, #000000 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 16px;
            margin: 0;
            position: relative;
            overflow-x: hidden;
        }

        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 20% 20%, rgba(139, 0, 0, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(184, 134, 11, 0.2) 0%, transparent 50%),
                radial-gradient(circle at 50% 50%, rgba(255, 215, 0, 0.05) 0%, transparent 70%);
            pointer-events: none;
            z-index: 0;
        }

        /* ==================== LOADING SCREEN ==================== */
        #loadingScreen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            background: radial-gradient(ellipse at center, #1a0000 0%, #0a0000 50%, #000000 100%);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }

        #loadingScreen.hidden {
            opacity: 0;
            transform: scale(1.2);
            pointer-events: none;
        }

        .loading-container {
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 40px;
            z-index: 1;
        }

        .loading-particles {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .loading-particle {
            position: absolute;
            background: #ffd700;
            border-radius: 50%;
            animation: floatParticle 8s ease-in-out infinite;
            box-shadow: 0 0 10px #ffd700, 0 0 20px #cc0000;
        }

        .loading-particle:nth-child(1) { width: 3px; height: 3px; top: 20%; left: 15%; animation-delay: 0s; animation-duration: 6s; background: #ff4444; }
        .loading-particle:nth-child(2) { width: 2px; height: 2px; top: 60%; left: 80%; animation-delay: 1s; animation-duration: 7s; background: #ffd700; }
        .loading-particle:nth-child(3) { width: 4px; height: 4px; top: 40%; left: 30%; animation-delay: 2s; animation-duration: 5s; background: #ff6b6b; }
        .loading-particle:nth-child(4) { width: 2px; height: 2px; top: 70%; left: 50%; animation-delay: 0.5s; animation-duration: 8s; background: #ffed4a; }
        .loading-particle:nth-child(5) { width: 3px; height: 3px; top: 10%; left: 70%; animation-delay: 1.5s; animation-duration: 6.5s; background: #cc0000; }
        .loading-particle:nth-child(6) { width: 5px; height: 5px; top: 80%; left: 20%; animation-delay: 2.5s; animation-duration: 7.5s; background: #ffd700; box-shadow: 0 0 20px #ffd700, 0 0 40px #cc0000; }

        .loading-nebula {
            position: absolute;
            width: 600px;
            height: 600px;
            border-radius: 50%;
            pointer-events: none;
            z-index: 0;
            filter: blur(80px);
            opacity: 0.3;
        }

        .loading-nebula-1 { top: -200px; left: -200px; background: radial-gradient(circle, #8b0000, transparent); animation: nebulaPulse 4s ease-in-out infinite; }
        .loading-nebula-2 { bottom: -200px; right: -200px; background: radial-gradient(circle, #b8860b, transparent); animation: nebulaPulse 5s ease-in-out infinite; animation-delay: 1s; }
        .loading-nebula-3 { top: 50%; left: 50%; transform: translate(-50%, -50%); width: 800px; height: 800px; background: radial-gradient(circle, #ffd700, transparent); opacity: 0.1; animation: nebulaPulse 6s ease-in-out infinite; animation-delay: 2s; }

        .orbital-system { position: relative; width: 180px; height: 180px; animation: systemRotate 20s linear infinite; }
        .orbit { position: absolute; border-radius: 50%; border: 2px solid rgba(255, 215, 0, 0.2); animation: orbitRotate 6s linear infinite; }
        .orbit-1 { width: 180px; height: 180px; top: 0; left: 0; border-color: rgba(139, 0, 0, 0.4); animation-duration: 8s; }
        .orbit-2 { width: 140px; height: 140px; top: 20px; left: 20px; border-color: rgba(255, 215, 0, 0.3); animation-duration: 6s; animation-direction: reverse; }
        .orbit-3 { width: 100px; height: 100px; top: 40px; left: 40px; border-color: rgba(255, 68, 68, 0.4); animation-duration: 4s; }

        .orbital-dot { position: absolute; width: 12px; height: 12px; border-radius: 50%; box-shadow: 0 0 20px currentColor, 0 0 40px currentColor; animation: dotOrbit 8s linear infinite; }
        .dot-1 { top: -6px; left: 50%; color: #cc0000; background: #cc0000; }
        .dot-2 { bottom: -6px; right: 20%; color: #ffd700; background: #ffd700; animation-duration: 6s; animation-direction: reverse; }
        .dot-3 { top: 30%; left: -6px; color: #ff4444; background: #ff4444; animation-duration: 4s; }

        .core {
            position: absolute;
            width: 50px;
            height: 50px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: radial-gradient(circle, #ffd700, #cc0000);
            border-radius: 50%;
            box-shadow: 0 0 30px #ffd700, 0 0 60px #cc0000, 0 0 90px #8b0000;
            animation: corePulse 2s ease-in-out infinite;
        }

        .core::after {
            content: '';
            position: absolute;
            width: 70px;
            height: 70px;
            top: -10px;
            left: -10px;
            border-radius: 50%;
            border: 2px solid rgba(255, 215, 0, 0.5);
            animation: coreRing 3s ease-in-out infinite;
        }

        .energy-wave { position: absolute; width: 100%; height: 100%; border-radius: 50%; border: 2px solid rgba(255, 215, 0, 0.3); animation: waveExpand 3s ease-out infinite; }
        .wave-2 { animation-delay: 1s; }
        .wave-3 { animation-delay: 2s; }

        .loading-text {
            color: #ffd700;
            font-size: 1.8rem;
            font-weight: 800;
            letter-spacing: 6px;
            text-transform: uppercase;
            animation: textGlow 2s ease-in-out infinite;
            text-align: center;
            text-shadow: 0 0 20px rgba(255, 215, 0, 0.8), 0 0 40px rgba(204, 0, 0, 0.5);
        }

        .loading-text span { display: inline-block; animation: bounceText 2s ease-in-out infinite; }
        .loading-text span:nth-child(1) { animation-delay: 0s; }
        .loading-text span:nth-child(2) { animation-delay: 0.1s; }
        .loading-text span:nth-child(3) { animation-delay: 0.2s; }
        .loading-text span:nth-child(4) { animation-delay: 0.3s; }
        .loading-text span:nth-child(5) { animation-delay: 0.4s; }
        .loading-text span:nth-child(6) { animation-delay: 0.5s; }
        .loading-text span:nth-child(7) { animation-delay: 0.6s; }
        .loading-text span:nth-child(8) { animation-delay: 0.7s; }
        .loading-text span:nth-child(9) { animation-delay: 0.8s; }
        .loading-text span:nth-child(10) { animation-delay: 0.9s; }

        .loading-progress-container {
            width: 300px;
            height: 6px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
            box-shadow: inset 0 0 20px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(184, 134, 11, 0.5);
        }

        .loading-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #8b0000, #cc0000, #ffd700, #ffed4a);
            border-radius: 10px;
            position: relative;
            box-shadow: 0 0 20px #cc0000, 0 0 40px #ffd700;
            transition: width 0.3s ease;
            animation: shimmerBar 2s linear infinite;
            background-size: 300% auto;
        }

        .loading-progress-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.6), transparent);
            animation: shimmer 1.5s ease-in-out infinite;
        }

        .loading-status {
            color: #cc9999;
            font-size: 0.85rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            animation: statusBlink 1.5s ease-in-out infinite;
            text-align: center;
        }

        .loading-percentage {
            font-size: 3rem;
            font-weight: 900;
            background: linear-gradient(to bottom, #ffed4a 0%, #ffd700 40%, #b8860b 100%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 40px rgba(255, 215, 0, 0.6);
            animation: percentageGlow 2s ease-in-out infinite;
            letter-spacing: 2px;
        }

        @keyframes orbitRotate { to { transform: rotate(360deg); } }
        @keyframes systemRotate { to { transform: rotate(360deg); } }
        @keyframes dotOrbit { to { transform: rotate(360deg); } }

        @keyframes corePulse {
            0%, 100% { transform: translate(-50%, -50%) scale(1); box-shadow: 0 0 30px #ffd700, 0 0 60px #cc0000, 0 0 90px #8b0000; }
            50% { transform: translate(-50%, -50%) scale(1.2); box-shadow: 0 0 50px #ffd700, 0 0 80px #cc0000, 0 0 120px #8b0000, 0 0 150px #ff4444; }
        }

        @keyframes coreRing {
            0%, 100% { transform: scale(1); opacity: 0.5; }
            50% { transform: scale(1.5); opacity: 0; }
        }

        @keyframes waveExpand {
            0% { transform: scale(1); opacity: 0.5; }
            100% { transform: scale(2); opacity: 0; }
        }

        @keyframes floatParticle {
            0%, 100% { transform: translateY(0) translateX(0); opacity: 0.3; }
            25% { transform: translateY(-20px) translateX(10px); opacity: 0.8; }
            50% { transform: translateY(-10px) translateX(-15px); opacity: 0.5; }
            75% { transform: translateY(-30px) translateX(20px); opacity: 0.7; }
        }

        @keyframes nebulaPulse {
            0%, 100% { opacity: 0.2; transform: scale(1); }
            50% { opacity: 0.4; transform: scale(1.1); }
        }

        @keyframes textGlow {
            0%, 100% { text-shadow: 0 0 10px rgba(255, 215, 0, 0.5); }
            50% { text-shadow: 0 0 20px rgba(255, 215, 0, 0.8), 0 0 40px rgba(204, 0, 0, 0.5); }
        }

        @keyframes bounceText {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-12px); }
        }

        @keyframes shimmerBar {
            0% { background-position: 0% center; }
            100% { background-position: 300% center; }
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(200%); }
        }

        @keyframes statusBlink {
            0%, 100% { opacity: 0.7; }
            50% { opacity: 1; }
        }

        @keyframes percentageGlow {
            0%, 100% { filter: brightness(1); }
            50% { filter: brightness(1.3); }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.5); }
            to { opacity: 1; transform: scale(1); }
        }

        /* ==================== LOGIN PAGE STYLES ==================== */
        .login-card {
            background: linear-gradient(165deg, #1a0a0a 0%, #0d0505 30%, #1a0a0a 70%, #0a0000 100%);
            border: 2px solid #b8860b;
            border-radius: 40px;
            box-shadow: 0 30px 60px -12px rgba(139, 0, 0, 0.8), 0 0 0 1px rgba(255, 215, 0, 0.3) inset, 0 0 30px rgba(184, 134, 11, 0.3);
            width: 100%;
            max-width: 480px;
            padding: 40px 30px;
            position: relative;
            z-index: 1;
            animation: fadeIn 0.8s ease;
        }

        .login-card::before {
            content: "";
            position: absolute;
            top: -2px;
            left: 20%;
            right: 20%;
            height: 3px;
            background: linear-gradient(90deg, transparent, #ffed4a, #ffd700, #ffed4a, transparent);
            border-radius: 50%;
            filter: blur(1px);
            animation: border-shine 3s ease-in-out infinite;
        }

        @keyframes border-shine {
            0%, 100% { opacity: 0.5; transform: scaleX(0.8); }
            50% { opacity: 1; transform: scaleX(1); }
        }

        .login-title {
            text-align: center;
            font-size: 2.2rem;
            font-weight: 900;
            background: linear-gradient(135deg, #ffd700 0%, #ffed4a 30%, #b8860b 60%, #ffd700 100%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .login-subtitle {
            text-align: center;
            color: #cc9999;
            font-size: 0.9rem;
            margin-bottom: 30px;
            letter-spacing: 1px;
        }

        .key-input-group { margin-bottom: 20px; }

        .key-input-label {
            color: #ffd700;
            font-size: 0.85rem;
            font-weight: 700;
            letter-spacing: 1px;
            margin-bottom: 10px;
            text-transform: uppercase;
        }

        .key-input-wrapper {
            position: relative;
            display: flex;
            align-items: center;
        }

        .key-input {
            width: 100%;
            padding: 16px 50px 16px 20px;
            background: #0d0202;
            border: 2px solid rgba(184, 134, 11, 0.5);
            border-radius: 16px;
            color: #ffed4a;
            font-family: 'Courier New', monospace;
            font-size: 1.1rem;
            font-weight: 700;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            outline: none;
        }

        .key-input:focus {
            border-color: #ffd700;
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.3), 0 0 40px rgba(139, 0, 0, 0.3);
        }

        .key-input::placeholder { color: #886666; font-weight: 400; }

        .key-input.error {
            border-color: #ff4444;
            box-shadow: 0 0 20px rgba(255, 68, 68, 0.5);
            animation: shake 0.5s ease;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }

        .key-input.valid {
            border-color: #00ff88;
            box-shadow: 0 0 20px rgba(0, 255, 136, 0.5);
        }

        .key-toggle {
            position: absolute;
            right: 12px;
            background: none;
            border: none;
            color: #cc9999;
            cursor: pointer;
            font-size: 1.2rem;
            padding: 8px;
            transition: all 0.3s;
        }

        .key-toggle:hover { color: #ffd700; }

        .login-button {
            background: linear-gradient(135deg, #8b0000 0%, #cc0000 50%, #8b0000 100%);
            border: 2px solid #ffd700;
            color: #ffed4a;
            font-weight: 800;
            font-size: 1.2rem;
            padding: 16px 36px;
            border-radius: 60px;
            cursor: pointer;
            letter-spacing: 1px;
            box-shadow: 0 12px 30px -5px rgba(139, 0, 0, 0.8), 0 0 20px rgba(255, 215, 0, 0.2);
            transition: all 0.3s ease;
            width: 100%;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            position: relative;
            overflow: hidden;
            margin-top: 10px;
        }

        .login-button::after {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent 40%, rgba(255, 215, 0, 0.3) 50%, transparent 60%);
            animation: button-shine 3s infinite;
        }

        @keyframes button-shine {
            0% { transform: translateX(-100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }

        .login-button:hover:not(:disabled) {
            transform: scale(1.02);
            background: linear-gradient(135deg, #cc0000 0%, #ff1a1a 50%, #cc0000 100%);
            box-shadow: 0 18px 40px -6px rgba(204, 0, 0, 0.9), 0 0 40px rgba(255, 215, 0, 0.4);
        }

        .login-button:active:not(:disabled) { transform: scale(0.98); }
        .login-button:disabled { opacity: 0.6; cursor: not-allowed; }

        .forgot-key {
            display: block;
            text-align: center;
            margin-top: 20px;
            color: #cc9999;
            font-size: 0.85rem;
            cursor: pointer;
            text-decoration: underline dotted;
            transition: all 0.3s;
            background: none;
            border: none;
            width: 100%;
            padding: 8px;
        }

        .forgot-key:hover { color: #ffd700; opacity: 1; }

        .error-message {
            color: #ff4444;
            font-size: 0.85rem;
            text-align: center;
            margin-top: 12px;
            display: none;
            letter-spacing: 0.5px;
            padding: 10px;
            border-radius: 10px;
            background: rgba(255, 68, 68, 0.1);
            border: 1px solid rgba(255, 68, 68, 0.3);
        }

        .error-message.show {
            display: block;
            animation: fadeIn 0.3s ease;
        }

        /* ==================== VERIFICATION CARD STYLES ==================== */
        :root {
            --merah-gelap: #1a0000;
            --merah-tua: #3d0000;
            --merah-darah: #8b0000;
            --merah-api: #cc0000;
            --merah-terang: #ff1a1a;
            --emas-muda: #ffd700;
            --emas-tua: #b8860b;
            --emas-gelap: #8b6914;
            --emas-sinar: #ffed4a;
            --hitam-pekat: #0a0a0a;
            --text-emas: #ffcc00;
            --text-merah: #ff4444;
        }

        .verification-card {
            background: linear-gradient(165deg, #1a0a0a 0%, #0d0505 30%, #1a0a0a 70%, #0a0000 100%);
            border: 2px solid var(--emas-tua);
            border-radius: 40px;
            box-shadow: 0 30px 60px -12px rgba(139, 0, 0, 0.8), 0 0 0 1px rgba(255, 215, 0, 0.3) inset, 0 0 30px rgba(184, 134, 11, 0.3);
            width: 100%;
            max-width: 580px;
            padding: 32px 26px 36px;
            position: relative;
            z-index: 1;
            backdrop-filter: blur(8px);
            transition: all 0.4s ease;
            animation: fadeIn 0.8s ease;
        }

        .verification-card::before {
            content: "";
            position: absolute;
            top: -2px;
            left: 20%;
            right: 20%;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--emas-sinar), var(--emas-muda), var(--emas-sinar), transparent);
            border-radius: 50%;
            filter: blur(1px);
            animation: border-shine 3s ease-in-out infinite;
        }

        h1 {
            font-size: 2rem;
            font-weight: 800;
            letter-spacing: -0.5px;
            background: linear-gradient(135deg, #ffd700 0%, #ffed4a 30%, #b8860b 60%, #ffd700 100%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-align: center;
            margin-bottom: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            text-shadow: 0 0 30px rgba(255, 215, 0, 0.3);
        }

        .subhead {
            text-align: center;
            color: #cc9999;
            font-weight: 600;
            margin-bottom: 28px;
            font-size: 0.95rem;
            letter-spacing: 0.5px;
            border-bottom: 1px solid rgba(184, 134, 11, 0.4);
            padding-bottom: 18px;
            text-transform: uppercase;
        }

        .progress-container {
            background: #1a0a0a;
            border-radius: 50px;
            height: 16px;
            margin-bottom: 30px;
            overflow: hidden;
            border: 1px solid var(--emas-gelap);
            box-shadow: inset 0 2px 6px rgba(0, 0, 0, 0.8), 0 0 10px rgba(139, 0, 0, 0.3);
        }

        .progress-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #8b0000, #cc0000, #ffd700, #ffed4a, #cc0000);
            background-size: 300% auto;
            animation: shimmer-gold-red 2s linear infinite;
            border-radius: 50px;
            transition: width 0.5s cubic-bezier(0.25, 0.8, 0.3, 1);
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.5);
        }

        @keyframes shimmer-gold-red {
            0% { background-position: 0% center; }
            100% { background-position: 300% center; }
        }

        .step-indicator {
            display: flex;
            justify-content: center;
            margin-bottom: 30px;
            font-size: 0.85rem;
            color: #cc9999;
            padding: 0 6px;
        }

        .step-indicator span {
            background: #1a0a0a;
            padding: 5px 16px;
            border-radius: 30px;
            font-weight: 700;
            border: 1px solid var(--emas-gelap);
            color: var(--emas-muda);
        }

        .step-indicator .active-step {
            background: linear-gradient(135deg, #8b0000, #3d0000);
            color: var(--emas-sinar);
            box-shadow: 0 0 20px rgba(255, 0, 0, 0.6), 0 0 30px rgba(255, 215, 0, 0.3);
            border-color: var(--emas-muda);
        }

        .community-box {
            background: linear-gradient(145deg, #1a0505 0%, #0d0202 100%);
            border-radius: 30px;
            padding: 30px 22px;
            margin-bottom: 24px;
            border: 1px solid rgba(139, 0, 0, 0.6);
            text-align: center;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .community-box::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--emas-muda), transparent);
        }

        .channel-icon {
            font-size: 3.6rem;
            margin-bottom: 10px;
            filter: drop-shadow(0 0 20px rgba(255, 215, 0, 0.6)) drop-shadow(0 0 10px rgba(255, 0, 0, 0.4));
            animation: icon-float 3s ease-in-out infinite;
        }

        @keyframes icon-float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }

        .community-name {
            font-weight: 800;
            font-size: 1.5rem;
            color: var(--emas-muda);
            letter-spacing: -0.3px;
            margin-bottom: 6px;
            text-shadow: 0 0 20px rgba(255, 215, 0, 0.4);
        }

        .community-url {
            color: #cc9999;
            font-size: 0.8rem;
            word-break: break-all;
            background: #1a0a0a;
            display: inline-block;
            padding: 6px 14px;
            border-radius: 30px;
            margin: 10px 0 18px;
            border: 1px solid rgba(184, 134, 11, 0.5);
            font-family: 'Courier New', monospace;
        }

        .follow-button {
            background: linear-gradient(135deg, #8b0000 0%, #cc0000 50%, #8b0000 100%);
            border: 2px solid var(--emas-muda);
            color: var(--emas-sinar);
            font-weight: 800;
            font-size: 1.25rem;
            padding: 14px 36px;
            border-radius: 60px;
            cursor: pointer;
            letter-spacing: 1px;
            box-shadow: 0 12px 30px -5px rgba(139, 0, 0, 0.8), 0 0 20px rgba(255, 215, 0, 0.2);
            transition: all 0.3s ease;
            width: 100%;
            max-width: 300px;
            text-transform: uppercase;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            position: relative;
            overflow: hidden;
        }

        .follow-button::after {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent 40%, rgba(255, 215, 0, 0.3) 50%, transparent 60%);
            animation: button-shine 3s infinite;
        }

        .follow-button:hover:not(:disabled) {
            transform: scale(1.05);
            background: linear-gradient(135deg, #cc0000 0%, #ff1a1a 50%, #cc0000 100%);
            box-shadow: 0 18px 40px -6px rgba(204, 0, 0, 0.9), 0 0 40px rgba(255, 215, 0, 0.4);
            border-color: var(--emas-sinar);
        }

        .follow-button:active:not(:disabled) { transform: scale(0.95); }
        .follow-button:disabled { background: #2a1a1a; color: #886666; box-shadow: none; cursor: not-allowed; transform: none; border-color: #5a3a3a; }

        .waiting-panel {
            background: linear-gradient(145deg, #1a0505 0%, #0d0202 100%);
            border-radius: 30px;
            padding: 32px 22px;
            text-align: center;
            border: 1px solid rgba(139, 0, 0, 0.6);
            margin-top: 20px;
            position: relative;
        }

        .countdown-number {
            font-size: 5rem;
            font-weight: 900;
            background: linear-gradient(to bottom, #ffed4a 0%, #ffd700 40%, #b8860b 100%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            line-height: 1;
            margin: 15px 0;
            text-shadow: 0 0 40px rgba(255, 215, 0, 0.6);
            animation: countdown-pulse 1s ease-in-out infinite;
        }

        @keyframes countdown-pulse {
            0%, 100% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.1); opacity: 0.8; }
        }

        .key-box {
            background: linear-gradient(145deg, #1a0505 0%, #0d0202 100%);
            border-radius: 30px;
            padding: 28px 20px;
            margin-top: 18px;
            border: 2px solid var(--emas-muda);
            box-shadow: 0 0 40px rgba(255, 215, 0, 0.3), 0 0 60px rgba(139, 0, 0, 0.5), 0 0 0 1px rgba(255, 215, 0, 0.4) inset;
            position: relative;
            overflow: hidden;
            animation: key-appear 0.6s ease-out;
        }

        @keyframes key-appear {
            0% { transform: scale(0.8); opacity: 0; }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); opacity: 1; }
        }

        .key-box::before {
            content: "🔒 TERPROTEKSI";
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            background: #1a0a0a;
            color: var(--emas-sinar);
            font-size: 0.65rem;
            font-weight: bold;
            letter-spacing: 2px;
            padding: 3px 16px;
            border-radius: 0 0 14px 14px;
            border: 1px solid var(--emas-muda);
            border-top: none;
            z-index: 2;
            text-transform: uppercase;
        }

        .key-box::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(135deg, transparent 30%, rgba(255, 215, 0, 0.05) 50%, transparent 70%);
            pointer-events: none;
        }

        .key-label {
            color: var(--emas-muda);
            letter-spacing: 2px;
            font-size: 0.85rem;
            font-weight: 700;
            margin-bottom: 10px;
            text-transform: uppercase;
            margin-top: 14px;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }

        .key-value {
            font-family: 'Courier New', monospace;
            font-size: 2.2rem;
            font-weight: 800;
            color: var(--emas-sinar);
            word-break: break-word;
            background: #0d0202;
            padding: 16px 12px;
            border-radius: 20px;
            letter-spacing: 1px;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.8), 0 0 30px rgba(255, 0, 0, 0.5), 0 0 45px rgba(255, 215, 0, 0.3);
            user-select: all;
            -webkit-user-select: all;
            position: relative;
            border: 1px solid var(--emas-gelap);
        }

        .key-value::after {
            content: "🔐";
            position: absolute;
            right: 12px;
            top: 50%;
            transform: translateY(-50%);
            font-size: 1.3rem;
            opacity: 0.8;
            animation: lock-shine 2s ease-in-out infinite;
        }

        @keyframes lock-shine {
            0%, 100% { filter: brightness(1); }
            50% { filter: brightness(1.5); }
        }

        .key-expiry {
            color: #ff6b6b;
            font-size: 0.85rem;
            margin-top: 12px;
            padding: 8px 16px;
            background: rgba(139, 0, 0, 0.3);
            border-radius: 20px;
            border: 1px solid rgba(255, 68, 68, 0.5);
            display: inline-block;
            letter-spacing: 1px;
        }

        .key-expiry.active {
            color: #4caf50;
            border-color: rgba(76, 175, 80, 0.5);
            background: rgba(76, 175, 80, 0.1);
        }

        .copy-button {
            background: linear-gradient(135deg, #1a0a0a 0%, #2a1a1a 100%);
            border: 1px solid var(--emas-muda);
            color: var(--emas-sinar);
            font-weight: 700;
            font-size: 1.1rem;
            padding: 14px 28px;
            border-radius: 40px;
            cursor: pointer;
            margin-top: 22px;
            width: 100%;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            letter-spacing: 0.8px;
            text-transform: uppercase;
        }

        .copy-button:hover {
            background: linear-gradient(135deg, #2a1a1a 0%, #3d1a1a 100%);
            border-color: var(--emas-sinar);
            box-shadow: 0 0 25px rgba(255, 215, 0, 0.5), 0 0 40px rgba(139, 0, 0, 0.5);
            transform: translateY(-2px);
        }

        .copy-button:active { transform: scale(0.95); }

        .reset-link {
            color: #cc9999;
            text-align: center;
            margin-top: 20px;
            font-size: 0.85rem;
            cursor: pointer;
            text-decoration: underline dotted;
            opacity: 0.7;
            transition: all 0.3s;
        }

        .reset-link:hover { opacity: 1; color: var(--emas-muda); }

        .security-badge {
            text-align: center;
            margin-top: 14px;
            font-size: 0.7rem;
            color: #886666;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }

        .session-info {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            margin-bottom: 20px;
            padding: 10px;
            background: rgba(76, 175, 80, 0.1);
            border-radius: 12px;
            border: 1px solid rgba(76, 175, 80, 0.3);
        }

        .session-info .session-dot {
            width: 10px;
            height: 10px;
            background: #4caf50;
            border-radius: 50%;
            animation: sessionPulse 2s ease-in-out infinite;
        }

        @keyframes sessionPulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(1.3); }
        }

        .session-info .session-text {
            color: #4caf50;
            font-size: 0.8rem;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .session-info .session-time {
            color: #cc9999;
            font-size: 0.75rem;
        }

        .hidden { display: none !important; }

        @media (max-width: 400px) {
            .verification-card { padding: 20px 14px; }
            .login-card { padding: 30px 20px; }
            .key-value { font-size: 1.5rem; }
            .follow-button { font-size: 1rem; }
            .countdown-number { font-size: 3.5rem; }
            .loading-text { font-size: 1.2rem; letter-spacing: 3px; }
            .loading-percentage { font-size: 2rem; }
            .loading-progress-container { width: 200px; }
            .orbital-system { width: 140px; height: 140px; }
            .orbit-1 { width: 140px; height: 140px; }
            .orbit-2 { width: 110px; height: 110px; top: 15px; left: 15px; }
            .orbit-3 { width: 80px; height: 80px; top: 30px; left: 30px; }
        }
    </style>
</head>
<body>
    <!-- LOADING SCREEN -->
    <div id="loadingScreen">
        <div class="loading-particles">
            <div class="loading-particle"></div>
            <div class="loading-particle"></div>
            <div class="loading-particle"></div>
            <div class="loading-particle"></div>
            <div class="loading-particle"></div>
            <div class="loading-particle"></div>
        </div>
        
        <div class="loading-nebula loading-nebula-1"></div>
        <div class="loading-nebula loading-nebula-2"></div>
        <div class="loading-nebula loading-nebula-3"></div>

        <div class="loading-container">
            <div class="orbital-system">
                <div class="orbit orbit-1"><div class="orbital-dot dot-1"></div></div>
                <div class="orbit orbit-2"><div class="orbital-dot dot-2"></div></div>
                <div class="orbit orbit-3"><div class="orbital-dot dot-3"></div></div>
                <div class="energy-wave"></div>
                <div class="energy-wave wave-2"></div>
                <div class="energy-wave wave-3"></div>
                <div class="core"></div>
            </div>

            <div class="loading-percentage" id="loadingPercentage">0%</div>

            <div class="loading-text" id="loadingText">
                <span>V</span><span>E</span><span>R</span><span>I</span><span>F</span><span>I</span><span>K</span><span>A</span><span>S</span><span>I</span>
            </div>

            <div class="loading-progress-container">
                <div class="loading-progress-bar" id="loadingProgressBar"></div>
            </div>

            <div class="loading-status" id="loadingStatus">Memuat Sistem...</div>
        </div>
    </div>

    <!-- LOGIN PAGE -->
    <div class="login-card hidden" id="loginPage">
        <div class="login-title">🔐 LOGIN KEY</div>
        <div class="login-subtitle">Masukkan key untuk melanjutkan</div>
        
        <div class="key-input-group">
            <div class="key-input-label">Key Akses</div>
            <div class="key-input-wrapper">
                <input 
                    type="text" 
                    class="key-input" 
                    id="keyInput" 
                    placeholder="Masukkan key Anda"
                    autocomplete="off"
                    spellcheck="false"
                />
                <button class="key-toggle" id="keyToggle" onclick="clearKeyInput()" style="display:none;">✖</button>
            </div>
        </div>
        
        <button class="login-button" id="loginButton" onclick="verifyKey()">
            🔓 MASUK
        </button>
        
        <div class="error-message" id="errorMessage">
            ❌ Key tidak valid! Silakan coba lagi.
        </div>
        
        <button class="forgot-key" onclick="goToForgotKey()">
            🔑 Buat Key Baru Disini
        </button>
    </div>

    <!-- VERIFICATION CARD -->
    <div class="verification-card hidden" id="verificationApp">
        <h1>🔐 VERIFIKASI FOLLOW</h1>
        <div class="subhead">Ikuti 6 channel komunitas</div>

        <div class="session-info" id="sessionInfo">
            <div class="session-dot"></div>
            <div class="session-text">Sesi Aktif</div>
            <div class="session-time" id="sessionTime"></div>
        </div>

        <div class="progress-container">
            <div class="progress-fill" id="progressFill" style="width: 0%;"></div>
        </div>
        <div class="step-indicator" id="stepIndicator">
            <span>0/6 FOLLOW</span>
        </div>

        <div id="dynamicContent"></div>

        <div class="reset-link" id="resetLink" onclick="resetVerification()">↻ Mulai ulang verifikasi</div>
        <div class="security-badge">🛡️ KEY TERENKRIPSI & TIDAK BOCOR</div>
    </div>

    <script>
        // ================================================================
        // KONFIGURASI DATABASE
        // ================================================================
        const DB_API_KEY = "sk_34701ad7da358959a51880e914c5515d6947c583dc37cb90";
        const DB_HOST = "https://free-database-fazxy.netlify.app";
        const DB_BASE = DB_HOST + "/api/v1";
        const KEYS_COLLECTION = "keys";

        // ================================================================
        // SESSION MANAGEMENT
        // ================================================================
        const SESSION_KEY = 'azfermodz_verified_session';
        const SESSION_DURATION = 24 * 60 * 60 * 1000;

        function saveSession(keyUsed) {
            const sessionData = {
                verified: true,
                keyUsed: keyUsed,
                timestamp: Date.now(),
                expiresAt: Date.now() + SESSION_DURATION
            };
            localStorage.setItem(SESSION_KEY, JSON.stringify(sessionData));
        }

        function getSession() {
            const raw = localStorage.getItem(SESSION_KEY);
            if (!raw) return null;
            try { return JSON.parse(raw); } catch { return null; }
        }

        function isSessionValid() {
            const session = getSession();
            if (!session) return false;
            if (Date.now() > session.expiresAt) { clearSession(); return false; }
            return session.verified === true;
        }

        function clearSession() { localStorage.removeItem(SESSION_KEY); }

        function getSessionRemainingTime() {
            const session = getSession();
            if (!session) return 0;
            const remaining = session.expiresAt - Date.now();
            return remaining > 0 ? remaining : 0;
        }

        function formatRemainingTime(ms) {
            const totalSec = Math.floor(ms / 1000);
            const hours = Math.floor(totalSec / 3600);
            const minutes = Math.floor((totalSec % 3600) / 60);
            const seconds = totalSec % 60;
            return `${hours}j ${minutes}m ${seconds}d`;
        }

        function updateSessionDisplay() {
            const el = document.getElementById('sessionTime');
            if (!el) return;
            const rem = getSessionRemainingTime();
            if (rem > 0) el.textContent = `• ${formatRemainingTime(rem)}`;
        }
        setInterval(updateSessionDisplay, 1000);

        // Auto logout saat session expired
        setInterval(() => {
            if (!isSessionValid()) {
                const lp = document.getElementById('loginPage');
                const va = document.getElementById('verificationApp');
                if (va && !va.classList.contains('hidden')) {
                    va.classList.add('hidden');
                    lp.classList.remove('hidden');
                    lp.style.animation = 'fadeIn 0.8s ease';
                    if (window.resetVerification) window.resetVerification();
                }
            }
        }, 1000);

        // ================================================================
        // LOADING SCREEN
        // ================================================================
        (function() {
            const cfg = { totalDuration: 5000, updateInterval: 100 };
            let pct = 0;
            const start = Date.now();
            const pctEl = document.getElementById('loadingPercentage');
            const barEl = document.getElementById('loadingProgressBar');
            const statusEl = document.getElementById('loadingStatus');
            const screenEl = document.getElementById('loadingScreen');
            const loginEl = document.getElementById('loginPage');
            const verEl = document.getElementById('verificationApp');

            const msgs = [
                'Memuat Sistem...',
                'Menginisialisasi Modul...',
                'Menghubungkan ke Server...',
                'Memverifikasi Keamanan...',
                'Menyiapkan Antarmuka...',
                'Hampir Selesai...'
            ];

            function updateStatus() {
                const idx = Math.floor(pct / 20);
                if (idx < msgs.length) statusEl.textContent = msgs[idx];
            }

            function tick() {
                const elapsed = Date.now() - start;
                const progress = elapsed / cfg.totalDuration;
                if (pct < 100) {
                    const target = Math.min(progress * 100, 99);
                    if (pct < target) pct = Math.min(pct + Math.random() * 2 + 0.5, target);
                    pctEl.textContent = Math.floor(pct) + '%';
                    barEl.style.width = pct + '%';
                    updateStatus();
                    setTimeout(tick, cfg.updateInterval);
                } else {
                    finish();
                }
            }

            function finish() {
                pct = 100;
                pctEl.textContent = '100%';
                barEl.style.width = '100%';
                statusEl.textContent = 'Sistem Siap!';
                setTimeout(() => {
                    screenEl.classList.add('hidden');
                    if (isSessionValid()) {
                        verEl.classList.remove('hidden');
                        verEl.style.animation = 'fadeIn 0.8s ease';
                        updateSessionDisplay();
                    } else {
                        loginEl.classList.remove('hidden');
                        loginEl.style.animation = 'fadeIn 0.8s ease';
                    }
                }, 800);
            }

            tick();
            setTimeout(() => { if (pct < 100) { pct = 100; finish(); } }, cfg.totalDuration + 3000);
        })();

        // ================================================================
        // KEY VALIDATION — VERIFIKASI KE DATABASE
        // ================================================================
        async function verifyKey() {
            const input = document.getElementById('keyInput');
            const errEl = document.getElementById('errorMessage');
            const btn = document.getElementById('loginButton');
            const enteredKey = input.value.trim();

            errEl.classList.remove('show');
            input.classList.remove('error', 'valid');

            if (!enteredKey) {
                showError('❌ Masukkan key terlebih dahulu!');
                input.classList.add('error');
                return;
            }

            btn.disabled = true;
            btn.innerHTML = '⏳ MEMVERIFIKASI...';

            try {
                // Ambil semua key dari database
                const res = await fetch(`${DB_BASE}/${KEYS_COLLECTION}`, {
                    headers: {
                        'x-api-key': DB_API_KEY,
                        'Accept': 'application/json'
                    }
                });

                if (!res.ok) throw new Error(`Database error (${res.status})`);

                const text = await res.text();
                let data;
                try { data = JSON.parse(text); } catch { data = text; }

                // Parse array
                let keys = [];
                if (Array.isArray(data)) keys = data;
                else if (data && Array.isArray(data.data)) keys = data.data;
                else if (data && Array.isArray(data.items)) keys = data.items;

                console.log('[LOGIN] Total keys in DB:', keys.length);
                console.log('[LOGIN] Searching for:', enteredKey);

                // Cari key yang cocok
                const foundKey = keys.find(k => {
                    const dbKey = String(k.key_value || '').trim();
                    return dbKey === enteredKey;
                });

                if (!foundKey) {
                    throw new Error('Key tidak ditemukan di database');
                }

                // Cek is_active
                if (foundKey.is_active === false) {
                    throw new Error('Key sudah dinonaktifkan oleh admin');
                }

                // Cek expired
                if (foundKey.expires_at) {
                    const expTime = new Date(foundKey.expires_at).getTime();
                    const now = Date.now();
                    if (expTime < now) {
                        const diffMins = Math.floor((now - expTime) / 60000);
                        throw new Error(`Key sudah expired ${diffMins} menit lalu`);
                    }
                }

                // ✅ VALID!
                input.classList.add('valid');
                saveSession(enteredKey);

                const loginPage = document.getElementById('loginPage');
                const verApp = document.getElementById('verificationApp');
                loginPage.classList.add('hidden');
                verApp.classList.remove('hidden');
                verApp.style.animation = 'fadeIn 0.8s ease';

                input.value = '';
                updateSessionDisplay();

            } catch (err) {
                console.error('[LOGIN ERROR]', err);
                showError('❌ ' + err.message);
                input.classList.add('error');
                setTimeout(() => input.classList.remove('error'), 800);
            } finally {
                btn.disabled = false;
                btn.innerHTML = '🔓 MASUK';
            }
        }

        function showError(msg) {
            const el = document.getElementById('errorMessage');
            el.textContent = msg;
            el.classList.add('show');
        }

        function clearKeyInput() {
            const input = document.getElementById('keyInput');
            input.value = '';
            input.classList.remove('error', 'valid');
            document.getElementById('keyToggle').style.display = 'none';
            input.focus();
        }

        // Tampilkan tombol clear saat ada input
        document.addEventListener('DOMContentLoaded', () => {
            const input = document.getElementById('keyInput');
            const toggle = document.getElementById('keyToggle');
            
            input.addEventListener('input', () => {
                toggle.style.display = input.value.length > 0 ? 'block' : 'none';
                input.classList.remove('error');
            });

            input.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') verifyKey();
            });
        });

        function goToForgotKey() {
            window.open('create-key.html', '_blank', 'noopener,noreferrer');
        }

        // ================================================================
        // VERIFICATION FLOW
        // ================================================================
        (function() {
            const communities = [
                { name: "KOMUNITAS OFFICIAL 1", url: "https://whatsapp.com/channel/0029Vb8STPh0VycODHqyol10", icon: "📢" },
                { name: "KOMUNITAS OFFICIAL 2", url: "https://whatsapp.com/channel/0029Vb8STPh0VycODHqyol10", icon: "🚀" },
                { name: "KOMUNITAS OFFICIAL 3", url: "https://whatsapp.com/channel/0029Vb8STPh0VycODHqyol10", icon: "💬" },
                { name: "KOMUNITAS OFFICIAL 4", url: "https://whatsapp.com/channel/0029VbDBArY9MF8uLpmviF1S", icon: "✨" },
                { name: "KOMUNITAS OFFICIAL 5", url: "https://whatsapp.com/channel/0029VbDBArY9MF8uLpmviF1S", icon: "🔥" },
                { name: "KOMUNITAS OFFICIAL 6", url: "https://whatsapp.com/channel/0029VbDBArY9MF8uLpmviF1S", icon: "🏆" }
            ];

            let currentStep = 0;
            let phase = 'follow';
            let countdownInterval = null;
            let countdownValue = 15;
            let verificationCompleted = false;

            const dyn = document.getElementById('dynamicContent');
            const fill = document.getElementById('progressFill');
            const step = document.getElementById('stepIndicator');

            function render() {
                if (phase === 'follow') {
                    const p = (currentStep / communities.length) * 100;
                    fill.style.width = p + '%';
                    step.innerHTML = `<span class="active-step">${currentStep}/${communities.length} FOLLOW</span>`;
                } else if (phase === 'countdown') {
                    fill.style.width = '100%';
                    step.innerHTML = `<span class="active-step">✅ 6/6 FOLLOW • TUNGGU VERIFIKASI</span>`;
                } else if (phase === 'key') {
                    fill.style.width = '100%';
                    step.innerHTML = `<span class="active-step">🔓 AKSES DIBERIKAN</span>`;
                    if (!verificationCompleted) {
                        verificationCompleted = true;
                        const session = getSession();
                        saveSession(session ? session.keyUsed : 'unknown');
                        updateSessionDisplay();
                    }
                }

                dyn.innerHTML = '';

                if (phase === 'follow') {
                    if (currentStep >= communities.length) { startCountdownPhase(); return; }
                    const c = communities[currentStep];
                    const box = document.createElement('div');
                    box.className = 'community-box';
                    box.innerHTML = `
                        <div class="channel-icon">${c.icon}</div>
                        <div class="community-name">${c.name}</div>
                        <div class="community-url">${c.url}</div>
                        <button class="follow-button" id="followButton">
                            ✅ FOLLOW SEKARANG
                        </button>
                        <div style="margin-top: 12px; font-size: 0.8rem; color: #cc9999;">Langkah ${currentStep+1} dari ${communities.length}</div>
                    `;
                    dyn.appendChild(box);
                    attachFollowHandler();
                } else if (phase === 'countdown') {
                    const box = document.createElement('div');
                    box.className = 'waiting-panel';
                    box.innerHTML = `
                        <div style="font-size: 1.4rem; font-weight: bold; color: #ffd700;">⏳ VERIFIKASI BERHASIL</div>
                        <div style="margin: 8px 0; color: #cc9999;">Tunggu <strong>${countdownValue}</strong> detik untuk melanjutkan</div>
                        <div class="countdown-number" id="countdownDisplay">${countdownValue}</div>
                        <div style="color: #886666;">Mengamankan akses...</div>
                    `;
                    dyn.appendChild(box);
                    startCountdown();
                } else if (phase === 'key') {
                    const box = document.createElement('div');
                    box.className = 'key-box';
                    box.innerHTML = `
                        <div class="key-label">✅ AKSES DIBERIKAN</div>
                        <div style="color: #ddd; font-size: 1rem; margin-top: 12px; line-height: 1.6;">
                            Verifikasi berhasil! Kamu sekarang memiliki akses penuh.
                        </div>
                        <div class="key-expiry active" style="margin-top: 20px;">
                            🔓 SESSION AKTIF 24 JAM
                        </div>
                        <button class="copy-button" id="redirectButton">
                            🚀 MASUK KE PANEL
                        </button>
                    `;
                    dyn.appendChild(box);
                    attachRedirectHandler();
                }
            }

            function attachFollowHandler() {
                const btn = document.getElementById('followButton');
                if (!btn) return;
                btn.addEventListener('click', (e) => {
                    e.preventDefault();
                    window.open(communities[currentStep].url, '_blank', 'noopener,noreferrer');
                    btn.disabled = true;
                    btn.textContent = '⏳ MEMERIKSA...';
                    setTimeout(() => {
                        if (currentStep < communities.length - 1) {
                            currentStep++;
                            render();
                        } else {
                            currentStep = communities.length;
                            startCountdownPhase();
                        }
                    }, 600);
                });
            }

            function startCountdownPhase() {
                if (countdownInterval) clearInterval(countdownInterval);
                phase = 'countdown';
                countdownValue = 15;
                render();
            }

            function startCountdown() {
                if (countdownInterval) clearInterval(countdownInterval);
                const display = document.getElementById('countdownDisplay');
                if (!display) return;
                countdownInterval = setInterval(() => {
                    countdownValue--;
                    if (display) display.textContent = countdownValue;
                    if (countdownValue <= 0) {
                        clearInterval(countdownInterval);
                        countdownInterval = null;
                        phase = 'key';
                        render();
                    }
                }, 1000);
            }

            function attachRedirectHandler() {
                const btn = document.getElementById('redirectButton');
                if (!btn) return;
                btn.addEventListener('click', () => {
                    // Redirect ke panel cheat atau halaman berikutnya
                    window.location.href = 'panel.html';
                    // Ganti 'panel.html' dengan URL panel cheat kamu
                });
            }

            window.resetVerification = function() {
                if (countdownInterval) clearInterval(countdownInterval);
                currentStep = 0;
                phase = 'follow';
                countdownValue = 15;
                verificationCompleted = false;
                render();
            };

            render();
        })();
    </script>
</body>
</html>
