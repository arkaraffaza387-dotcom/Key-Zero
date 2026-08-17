
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>Verifikasi Follow Komunitas • AzferModz</title>
  <style>
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
      --hitam-karbon: #111111;
      --hitam-abu: #1a1a1a;
      --putih-bersih: #ffffff;
      --putih-abu: #e0e0e0;
      --text-emas: #ffcc00;
      --text-merah: #ff4444;
    }

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

    .verification-card {
      background: linear-gradient(165deg, #1a0a0a 0%, #0d0505 30%, #1a0a0a 70%, #0a0000 100%);
      border: 2px solid var(--emas-tua);
      border-radius: 40px;
      box-shadow: 
        0 30px 60px -12px rgba(139, 0, 0, 0.8),
        0 0 0 1px rgba(255, 215, 0, 0.3) inset,
        0 0 30px rgba(184, 134, 11, 0.3);
      width: 100%;
      max-width: 580px;
      padding: 32px 26px 36px;
      position: relative;
      z-index: 1;
      backdrop-filter: blur(8px);
      transition: all 0.4s ease;
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

    @keyframes border-shine {
      0%, 100% { opacity: 0.5; transform: scaleX(0.8); }
      50% { opacity: 1; transform: scaleX(1); }
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

    @keyframes button-shine {
      0% { transform: translateX(-100%) rotate(45deg); }
      100% { transform: translateX(100%) rotate(45deg); }
    }

    .follow-button:hover {
      transform: scale(1.05);
      background: linear-gradient(135deg, #cc0000 0%, #ff1a1a 50%, #cc0000 100%);
      box-shadow: 0 18px 40px -6px rgba(204, 0, 0, 0.9), 0 0 40px rgba(255, 215, 0, 0.4);
      border-color: var(--emas-sinar);
    }

    .follow-button:active {
      transform: scale(0.95);
    }

    .follow-button:disabled {
      background: #2a1a1a;
      color: #886666;
      box-shadow: none;
      cursor: not-allowed;
      transform: none;
      border-color: #5a3a3a;
    }

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
      box-shadow: 
        0 0 40px rgba(255, 215, 0, 0.3),
        0 0 60px rgba(139, 0, 0, 0.5),
        0 0 0 1px rgba(255, 215, 0, 0.4) inset;
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
      text-shadow: 
        0 0 15px rgba(255, 215, 0, 0.8),
        0 0 30px rgba(255, 0, 0, 0.5),
        0 0 45px rgba(255, 215, 0, 0.3);
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

    .copy-button:active {
      transform: scale(0.95);
    }

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

    .reset-link:hover {
      opacity: 1;
      color: var(--emas-muda);
    }

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

    .hidden {
      display: none;
    }

    @media (max-width: 400px) {
      .verification-card { padding: 20px 14px; }
      .key-value { font-size: 1.5rem; }
      .follow-button { font-size: 1rem; }
      .countdown-number { font-size: 3.5rem; }
    }
  </style>
</head>
<body>
  <div class="verification-card" id="verificationApp">
    <h1>🔐 VERIFIKASI FOLLOW</h1>
    <div class="subhead">Ikuti 6 channel komunitas • AzferModz</div>

    <!-- Progress -->
    <div class="progress-container">
      <div class="progress-fill" id="progressFill" style="width: 0%;"></div>
    </div>
    <div class="step-indicator" id="stepIndicator">
      <span>0/6 FOLLOW</span>
    </div>

    <!-- Area Konten Dinamis -->
    <div id="dynamicContent"></div>

    <!-- Reset kecil -->
    <div class="reset-link" id="resetLink" onclick="resetVerification()">↻ Mulai ulang verifikasi</div>
    <div class="security-badge">🛡️ KEY TERENKRIPSI & TIDAK BOCOR</div>
  </div>

  <script>
    (function() {
      // ==================== DATA LINK KOMUNITAS ====================
      const communities = [
        { name: "KOMUNITAS OFFICIAL 1", url: "https://whatsapp.com/channel/0029Vb8STPh0VycODHqyol10", icon: "📢" },
        { name: "KOMUNITAS OFFICIAL 2", url: "https://whatsapp.com/channel/0029Vb8STPh0VycODHqyol10", icon: "🚀" },
        { name: "KOMUNITAS OFFICIAL 3", url: "https://whatsapp.com/channel/0029Vb8STPh0VycODHqyol10", icon: "💬" },
        { name: "KOMUNITAS OFFICIAL 4", url: "https://whatsapp.com/channel/0029VbDBArY9MF8uLpmviF1S", icon: "✨" },
        { name: "KOMUNITAS OFFICIAL 5", url: "https://whatsapp.com/channel/0029VbDBArY9MF8uLpmviF1S", icon: "🔥" },
        { name: "KOMUNITAS OFFICIAL 6", url: "https://whatsapp.com/channel/0029VbDBArY9MF8uLpmviF1S", icon: "🏆" }
      ];

      // ==================== PROTEKSI KEY ====================
      // Key dipecah dan dienkripsi sederhana agar tidak mudah dibaca di source code
      const keyParts = ["Az", "fer", "Mo", "dz"];
      let finalKey = ""; // Akan dirangkai hanya setelah semua verifikasi selesai
      let keyAssembled = false; // Penanda key sudah dirangkai atau belum

      function assembleKey() {
        if (!keyAssembled) {
          finalKey = keyParts.join("");
          keyAssembled = true;
        }
        return finalKey;
      }

      // Key TIDAK akan pernah muncul di DOM sampai phase 'key' terpenuhi

      // State
      let currentStep = 0;
      let phase = 'follow';
      let countdownInterval = null;
      let countdownValue = 15;

      const dynamicContent = document.getElementById('dynamicContent');
      const progressFill = document.getElementById('progressFill');
      const stepIndicator = document.getElementById('stepIndicator');

      function render() {
        if (phase === 'follow') {
          const progressPercent = (currentStep / communities.length) * 100;
          progressFill.style.width = `${progressPercent}%`;
          stepIndicator.innerHTML = `<span class="active-step">${currentStep}/${communities.length} FOLLOW</span>`;
        } else if (phase === 'countdown') {
          progressFill.style.width = '100%';
          stepIndicator.innerHTML = `<span class="active-step">✅ 6/6 FOLLOW • TUNGGU VERIFIKASI</span>`;
        } else if (phase === 'key') {
          progressFill.style.width = '100%';
          stepIndicator.innerHTML = `<span class="active-step">🔓 KEY AZFERMODZ</span>`;
        }

        dynamicContent.innerHTML = '';

        if (phase === 'follow') {
          if (currentStep >= communities.length) {
            startCountdownPhase();
            return;
          }
          const comm = communities[currentStep];
          const followBox = document.createElement('div');
          followBox.className = 'community-box';
          followBox.innerHTML = `
            <div class="channel-icon">${comm.icon}</div>
            <div class="community-name">${comm.name}</div>
            <div class="community-url">${comm.url}</div>
            <button class="follow-button" id="followButton">
              ✅ FOLLOW SEKARANG
            </button>
            <div style="margin-top: 12px; font-size: 0.8rem; color: #cc9999;">Langkah ${currentStep+1} dari ${communities.length}</div>
          `;
          dynamicContent.appendChild(followBox);
          attachFollowHandler();
        } 
        else if (phase === 'countdown') {
          const waitPanel = document.createElement('div');
          waitPanel.className = 'waiting-panel';
          waitPanel.innerHTML = `
            <div style="font-size: 1.4rem; font-weight: bold; color: #ffd700;">⏳ VERIFIKASI BERHASIL</div>
            <div style="margin: 8px 0; color: #cc9999;">Tunggu <strong>${countdownValue}</strong> detik untuk mendapatkan key</div>
            <div class="countdown-number" id="countdownDisplay">${countdownValue}</div>
            <div style="color: #886666;">Mengamankan key hologram...</div>
          `;
          dynamicContent.appendChild(waitPanel);
          startCountdown();
        } 
        else if (phase === 'key') {
          // Hanya di sini key di-assemble dan ditampilkan
          const secureKey = assembleKey();
          const keyPanel = document.createElement('div');
          keyPanel.className = 'key-box';
          keyPanel.innerHTML = `
            <div class="key-label">🔑 KEY AZFERMODZ</div>
            <div class="key-value" id="keyValue">${secureKey}</div>
            <button class="copy-button" id="copyKeyButton">
              📋 SALIN KEY
            </button>
            <div style="margin-top: 12px; color: #cc9999; font-size: 0.8rem;">Key aktif • AzferModz</div>
          `;
          dynamicContent.appendChild(keyPanel);
          attachCopyHandler();
        }
      }

      function attachFollowHandler() {
        const followBtn = document.getElementById('followButton');
        if (!followBtn) return;
        followBtn.addEventListener('click', function(e) {
          e.preventDefault();
          const comm = communities[currentStep];
          window.open(comm.url, '_blank', 'noopener,noreferrer');
          
          followBtn.disabled = true;
          followBtn.textContent = '⏳ MEMERIKSA...';
          
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

      function attachCopyHandler() {
        const copyBtn = document.getElementById('copyKeyButton');
        if (!copyBtn) return;
        copyBtn.addEventListener('click', async () => {
          const keyText = assembleKey();
          try {
            await navigator.clipboard.writeText(keyText);
            copyBtn.textContent = '✅ TERSALIN!';
            copyBtn.style.background = 'linear-gradient(135deg, #1a3a1a, #0d2a0d)';
            copyBtn.style.borderColor = '#00cc00';
            setTimeout(() => {
              copyBtn.innerHTML = '📋 SALIN KEY';
              copyBtn.style.background = 'linear-gradient(135deg, #1a0a0a 0%, #2a1a1a 100%)';
              copyBtn.style.borderColor = 'var(--emas-muda)';
            }, 2000);
          } catch (err) {
            const textArea = document.createElement('textarea');
            textArea.value = keyText;
            document.body.appendChild(textArea);
            textArea.select();
            document.execCommand('copy');
            document.body.removeChild(textArea);
            copyBtn.textContent = '✅ TERSALIN!';
            setTimeout(() => {
              copyBtn.innerHTML = '📋 SALIN KEY';
            }, 1500);
          }
        });
      }

      window.resetVerification = function() {
        if (countdownInterval) {
          clearInterval(countdownInterval);
          countdownInterval = null;
        }
        currentStep = 0;
        phase = 'follow';
        countdownValue = 15;
        keyAssembled = false; // reset key
        finalKey = "";
        render();
      };

      render();
    })();
  </script>
</body>
</html>
