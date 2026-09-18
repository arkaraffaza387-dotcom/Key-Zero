<html lang="id" data-theme="dark">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes"/>
<title>Login — By Fanzxy Modz</title>
<style>
/* ============================================================
   TEMA
============================================================ */
:root[data-theme="dark"] {
  --bg-1:#0b1120; --bg-2:#1e293b;
  --card-bg: rgba(30,41,59,.72);
  --card-border: rgba(96,165,250,.15);
  --text:#f1f5f9; --text-muted:#94a3b8; --text-dim:#64748b;
  --input-bg: rgba(15,23,42,.7);
  --input-border:#334155;
  --input-text:#fff;
  --primary:#3b82f6; --primary-hover:#2563eb;
  --primary-glow: rgba(59,130,246,.5);
  --accent:#8b5cf6;
  --success:#22c55e; --error:#ef4444; --warning:#fbbf24;
  --shadow: 0 20px 60px rgba(0,0,0,.55);
  --shadow-glow: 0 0 40px rgba(59,130,246,.15);
  --overlay: rgba(2,6,23,.82);
  --modal-bg: rgba(30,41,59,.95);
  --modal-border: rgba(96,165,250,.2);
  --divider: rgba(51,65,85,.6);
  --particle: rgba(147,197,253,.5);
}
:root[data-theme="light"] {
  --bg-1:#eff6ff; --bg-2:#dbeafe;
  --card-bg: rgba(255,255,255,.78);
  --card-border: rgba(59,130,246,.18);
  --text:#0f172a; --text-muted:#475569; --text-dim:#64748b;
  --input-bg: rgba(248,250,252,.9);
  --input-border:#cbd5e1;
  --input-text:#0f172a;
  --primary:#2563eb; --primary-hover:#1d4ed8;
  --primary-glow: rgba(37,99,235,.35);
  --accent:#7c3aed;
  --success:#16a34a; --error:#dc2626; --warning:#d97706;
  --shadow: 0 20px 60px rgba(15,23,42,.15);
  --shadow-glow: 0 0 40px rgba(37,99,235,.15);
  --overlay: rgba(15,23,42,.5);
  --modal-bg: rgba(255,255,255,.97);
  --modal-border: rgba(59,130,246,.25);
  --divider: rgba(203,213,225,.7);
  --particle: rgba(37,99,235,.4);
}

/* ============================================================
   BASE
============================================================ */
* { margin:0; padding:0; box-sizing:border-box;
    font-family: system-ui,-apple-system,"Segoe UI",sans-serif;
    -webkit-tap-highlight-color: transparent; }
html, body { min-height:100%; overflow-x:hidden; }
body {
  min-height: 100vh;
  display:flex; align-items:center; justify-content:center;
  background: radial-gradient(circle at 30% 20%, var(--bg-2), var(--bg-1) 70%);
  color: var(--text);
  padding: 1rem;
  transition: background .8s cubic-bezier(.4,0,.2,1), color .5s ease;
  position: relative;
  perspective: 1200px;
}

.aurora {
  position: fixed; inset:-30%; z-index:0;
  background:
    radial-gradient(circle at 20% 30%, #3b82f6 0%, transparent 45%),
    radial-gradient(circle at 80% 60%, #8b5cf6 0%, transparent 45%),
    radial-gradient(circle at 50% 90%, #06b6d4 0%, transparent 45%);
  filter: blur(90px); opacity:.35;
  animation: auroraFloat 24s ease-in-out infinite;
  pointer-events:none;
}
@keyframes auroraFloat {
  0%,100% { transform: translate(0,0) scale(1) rotate(0deg); }
  33%     { transform: translate(6%,-4%) scale(1.08) rotate(8deg); }
  66%     { transform: translate(-5%,5%) scale(.95) rotate(-6deg); }
}

#particles { position: fixed; inset:0; z-index:1; pointer-events:none; opacity:.7; }
[data-theme="light"] #particles { opacity:.5; }

/* THEME TOGGLE */
.theme-toggle {
  position: fixed; top: 1rem; right: 1rem;
  width: 52px; height: 52px;
  border-radius: 50%;
  border: 1px solid var(--card-border);
  background: var(--card-bg);
  backdrop-filter: blur(14px); -webkit-backdrop-filter: blur(14px);
  cursor: pointer;
  display:flex; align-items:center; justify-content:center;
  font-size: 1.4rem;
  box-shadow: var(--shadow);
  z-index: 200;
  transition: transform .55s cubic-bezier(.34,1.56,.64,1), box-shadow .35s ease;
  overflow:hidden;
}
.theme-toggle:hover { transform: scale(1.12) rotate(180deg); box-shadow: var(--shadow), 0 0 30px var(--primary-glow); }
.theme-toggle:active { transform: scale(.9) rotate(180deg); }
.theme-toggle .icon { position:absolute; transition: transform .6s cubic-bezier(.34,1.56,.64,1), opacity .4s ease; }
.theme-toggle .icon-sun  { transform: rotate(0deg) scale(1); opacity:1; }
.theme-toggle .icon-moon { transform: rotate(-120deg) scale(0); opacity:0; }
[data-theme="light"] .theme-toggle .icon-sun  { transform: rotate(120deg) scale(0); opacity:0; }
[data-theme="light"] .theme-toggle .icon-moon { transform: rotate(0deg) scale(1); opacity:1; }

/* CARD */
.card-wrap {
  position: relative; z-index: 2;
  width:100%; max-width:420px;
  transform-style: preserve-3d;
  transition: transform .35s cubic-bezier(.2,.8,.2,1);
}
.card {
  position: relative;
  background: var(--card-bg);
  backdrop-filter: blur(24px) saturate(1.4);
  -webkit-backdrop-filter: blur(24px) saturate(1.4);
  padding: 2.5rem 2rem;
  border-radius: 24px; width: 100%;
  box-shadow: var(--shadow), var(--shadow-glow);
  border: 1px solid var(--card-border);
  overflow: hidden;
  animation: cardIn .9s cubic-bezier(.34,1.56,.64,1) both;
}
.card::before {
  content:""; position:absolute; inset:-1px;
  border-radius: 24px; padding: 1px;
  background: linear-gradient(120deg, transparent, var(--primary), var(--accent), transparent);
  background-size: 300% 300%;
  -webkit-mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
  -webkit-mask-composite: xor; mask-composite: exclude;
  opacity: .7;
  animation: borderFlow 6s linear infinite;
  pointer-events:none;
}
@keyframes borderFlow { 0% { background-position: 0% 50%; } 100% { background-position: 300% 50%; } }
.card::after {
  content:""; position:absolute; top:-50%; left:-60%;
  width: 60%; height: 200%;
  background: linear-gradient(105deg, transparent 40%, rgba(255,255,255,.08) 50%, transparent 60%);
  transform: rotate(12deg);
  animation: shine 6s ease-in-out infinite;
  pointer-events:none;
}
@keyframes shine {
  0%, 70% { transform: translateX(-100%) rotate(12deg); }
  100%    { transform: translateX(350%) rotate(12deg); }
}
@keyframes cardIn {
  0%   { opacity:0; transform: translateY(40px) scale(.92) rotateX(-10deg); }
  60%  { opacity:1; }
  100% { opacity:1; transform: translateY(0) scale(1) rotateX(0); }
}
.card h1 {
  margin-bottom: 1.75rem; font-size: 1.85rem; text-align:center;
  background: linear-gradient(120deg, var(--primary), var(--accent), var(--primary));
  background-size: 200% auto;
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 800; letter-spacing: -0.5px;
  animation: gradientShift 4s linear infinite, fadeSlide .8s cubic-bezier(.34,1.56,.64,1) .15s both;
}
@keyframes gradientShift { to { background-position: 200% center; } }
@keyframes fadeSlide {
  from { opacity:0; transform: translateY(14px); }
  to   { opacity:1; transform: translateY(0); }
}

/* FLOATING LABEL */
.field { position: relative; margin-bottom: 1.35rem; animation: fadeSlide .6s cubic-bezier(.34,1.56,.64,1) both; }
.field:nth-of-type(1) { animation-delay: .2s; }
.field:nth-of-type(2) { animation-delay: .3s; }
.field input {
  width:100%; padding: 1.15rem 1rem .55rem;
  border-radius: 14px;
  border: 1.5px solid var(--input-border);
  background: var(--input-bg);
  color: var(--input-text);
  font-size: 1rem;
  transition: border-color .35s ease, box-shadow .35s ease, background .35s ease, transform .35s cubic-bezier(.34,1.56,.64,1);
  outline: none;
}
.field input:focus {
  border-color: var(--primary);
  box-shadow: 0 0 0 4px var(--primary-glow);
  transform: translateY(-2px);
}
.field label {
  position:absolute; left: 1rem; top: 50%;
  transform: translateY(-50%);
  color: var(--text-dim); font-size: 1rem;
  pointer-events:none;
  transition: all .35s cubic-bezier(.34,1.56,.64,1);
  padding: 0 .35rem;
}
.field input:focus + label,
.field input:not(:placeholder-shown) + label {
  top: 0; font-size: .72rem; color: var(--primary);
  background: var(--card-bg); border-radius: 6px;
  font-weight: 700; letter-spacing: .5px;
  transform: translateY(-50%) translateX(4px);
}

/* BUTTON LOGIN */
.btn-login {
  position: relative; width:100%; padding: 1rem;
  border: none; border-radius: 14px; cursor: pointer;
  background: linear-gradient(120deg, var(--primary), var(--accent), var(--primary));
  background-size: 220% auto;
  color:#fff; font-weight: 800; font-size: 1rem; letter-spacing: .5px;
  overflow:hidden;
  display:flex; align-items:center; justify-content:center; gap:.6rem;
  box-shadow: 0 8px 24px var(--primary-glow), 0 0 0 0 var(--primary-glow);
  transition: transform .4s cubic-bezier(.34,1.56,.64,1), box-shadow .4s ease, filter .3s ease;
  animation: fadeSlide .6s cubic-bezier(.34,1.56,.64,1) .4s both, gradientShift 4s linear infinite;
}
.btn-login:hover:not(:disabled) {
  transform: translateY(-3px) scale(1.02);
  box-shadow: 0 14px 36px var(--primary-glow), 0 0 24px var(--primary-glow);
  filter: brightness(1.1);
}
.btn-login:active:not(:disabled) { transform: translateY(0) scale(.97); }
.btn-login:disabled { cursor:not-allowed; opacity:.9; }
.btn-login::after {
  content:""; position:absolute; top:0; left:-100%;
  width: 60%; height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,.35), transparent);
  transform: skewX(-20deg);
  animation: btnShine 3s ease-in-out infinite;
}
@keyframes btnShine { 0%, 60% { left: -100%; } 100% { left: 150%; } }
.spinner {
  width: 18px; height: 18px;
  border: 2.5px solid rgba(255,255,255,.35);
  border-top-color: #fff;
  border-radius: 50%;
  animation: spin .7s linear infinite;
  display: none;
}
@keyframes spin { to { transform: rotate(360deg); } }
.btn-login.loading .spinner { display:inline-block; }
.btn-login.loading .btn-text { opacity:.85; }

/* TOAST MESSAGE */
.msg {
  margin-top: 0; padding: 0 1rem; max-height: 0;
  border-radius: 12px; font-size: .875rem; text-align:center; line-height:1.5;
  opacity:0; transform: translateY(-10px) scale(.95);
  overflow:hidden;
  transition: all .55s cubic-bezier(.34,1.56,.64,1);
  border: 1px solid transparent;
}
.msg.show {
  opacity:1; transform: translateY(0) scale(1);
  max-height: 200px; padding: .95rem 1rem; margin-top: 1rem;
}
.msg.error {
  background: rgba(239,68,68,.14);
  border-color: rgba(239,68,68,.5);
  color: #fca5a5;
  box-shadow: 0 0 24px rgba(239,68,68,.15);
}
[data-theme="light"] .msg.error { color:#b91c1c; }
.msg.success {
  background: rgba(34,197,94,.14);
  border-color: rgba(34,197,94,.5);
  color:#86efac;
  box-shadow: 0 0 24px rgba(34,197,94,.15);
}
[data-theme="light"] .msg.success { color:#15803d; }
.msg.info {
  background: rgba(59,130,246,.14);
  border-color: rgba(59,130,246,.5);
  color:#93c5fd;
}
[data-theme="light"] .msg.info { color:#1d4ed8; }

/* DIVIDER + TOMBOL REGISTER */
.divider-text {
  display: flex; align-items: center; gap: 0.75rem;
  margin: 1.5rem 0 1rem;
  color: var(--text-dim);
  font-size: 0.72rem;
  letter-spacing: 1px;
  text-transform: uppercase;
  animation: fadeSlide 0.6s ease 0.55s both;
}
.divider-text::before,
.divider-text::after {
  content: "";
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--divider), transparent);
}
.btn-register {
  position: relative;
  display: flex; align-items: center; justify-content: center; gap: 0.5rem;
  width: 100%; padding: 0.95rem;
  border-radius: 14px;
  border: 1.5px solid var(--primary);
  background: transparent;
  color: var(--primary);
  font-weight: 800; font-size: 0.95rem; letter-spacing: 0.4px;
  text-decoration: none;
  cursor: pointer;
  overflow: hidden;
  transition: all 0.45s cubic-bezier(.34, 1.56, .64, 1);
  animation: fadeSlide 0.6s cubic-bezier(.34, 1.56, .64, 1) 0.6s both;
  box-shadow: 0 0 0 0 var(--primary-glow);
}
.btn-register::before {
  content: "";
  position: absolute; top: 0; left: -100%;
  width: 60%; height: 100%;
  background: linear-gradient(90deg, transparent, var(--primary-glow), transparent);
  transform: skewX(-20deg);
  transition: left 0.6s ease;
}
.btn-register:hover::before { left: 150%; }
.btn-register:hover {
  background: linear-gradient(120deg, var(--primary), var(--accent), var(--primary));
  background-size: 220% auto;
  color: #fff;
  border-color: transparent;
  transform: translateY(-3px) scale(1.02);
  box-shadow: 0 12px 30px var(--primary-glow), 0 0 24px var(--primary-glow);
  animation: gradientShift 3s linear infinite;
}
.btn-register:active { transform: translateY(0) scale(0.97); }

.info {
  margin-top: 1.4rem; font-size: .75rem;
  color: var(--text-dim); text-align:center; letter-spacing:.3px;
}
.info b {
  background: linear-gradient(120deg, var(--primary), var(--accent));
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 800;
}

/* MODAL */
.modal-overlay {
  position: fixed; inset:0;
  background: var(--overlay);
  display:flex; align-items:center; justify-content:center;
  padding: 1rem; z-index: 999;
  opacity:0; pointer-events:none;
  backdrop-filter: blur(0px); -webkit-backdrop-filter: blur(0px);
  transition: opacity .45s ease, backdrop-filter .45s ease;
}
.modal-overlay.show {
  opacity:1; pointer-events:auto;
  backdrop-filter: blur(8px); -webkit-backdrop-filter: blur(8px);
}
.modal {
  background: var(--modal-bg);
  border: 1px solid var(--modal-border);
  border-radius: 24px;
  width:100%; max-width:420px;
  padding: 2rem 1.75rem;
  box-shadow: var(--shadow), 0 0 60px rgba(59,130,246,.2);
  transform: scale(.7) translateY(40px) rotateX(20deg);
  opacity:0;
  transition: transform .6s cubic-bezier(.34,1.56,.64,1), opacity .35s ease;
  position: relative; overflow:hidden;
}
.modal-overlay.show .modal { transform: scale(1) translateY(0) rotateX(0); opacity:1; }
.modal::before {
  content:""; position:absolute; top:-50%; left:-50%;
  width: 200%; height: 100%;
  background: radial-gradient(circle, rgba(59,130,246,.15), transparent 60%);
  animation: modalGlow 4s ease-in-out infinite;
  pointer-events:none;
}
@keyframes modalGlow {
  0%,100% { opacity:.6; transform: scale(1); }
  50%     { opacity:1; transform: scale(1.15); }
}
.modal h2 {
  text-align:center; font-size: 1.05rem; margin-bottom: 1.5rem;
  color: var(--warning); letter-spacing:.6px; line-height:1.4;
  font-weight: 800;
  animation: pulseWarn 2s ease-in-out infinite;
  position: relative;
}
@keyframes pulseWarn {
  0%,100% { text-shadow: 0 0 0 rgba(251,191,36,0); }
  50%     { text-shadow: 0 0 18px rgba(251,191,36,.6); }
}
.modal-row {
  display:flex; justify-content:space-between; align-items:center;
  padding: .85rem 0;
  border-bottom: 1px solid var(--divider);
  font-size:.9rem; gap:1rem;
  opacity:0; transform: translateX(-30px);
  transition: all .6s cubic-bezier(.34,1.56,.64,1);
}
.modal-overlay.show .modal-row { opacity:1; transform: translateX(0); }
.modal-overlay.show .modal-row:nth-child(2) { transition-delay:.15s; }
.modal-overlay.show .modal-row:nth-child(3) { transition-delay:.25s; }
.modal-overlay.show .modal-row:nth-child(4) { transition-delay:.35s; }
.modal-row:last-of-type { border-bottom:none; }
.modal-row .lbl { color: var(--text-muted); flex-shrink:0; font-weight:600; letter-spacing:.3px; }
.modal-row .val { color: var(--text); font-weight:800; text-align:right; word-break: break-all; }
.modal-btns {
  display:grid; grid-template-columns: 1fr 1fr;
  gap:.75rem; margin-top:1.75rem;
  opacity:0; transform: translateY(20px);
  transition: all .6s cubic-bezier(.34,1.56,.64,1) .45s;
}
.modal-overlay.show .modal-btns { opacity:1; transform: translateY(0); }
.modal-btns button {
  padding: .95rem; border-radius: 14px; border:none;
  font-weight: 800; font-size:.95rem; cursor:pointer;
  letter-spacing:.8px;
  position: relative; overflow:hidden;
  transition: transform .4s cubic-bezier(.34,1.56,.64,1), box-shadow .35s ease, background .3s ease;
}
.modal-btns button:hover  { transform: translateY(-3px) scale(1.03); }
.modal-btns button:active { transform: translateY(0) scale(.96); }
.btn-no {
  background: var(--input-bg); color: var(--text);
  border: 1px solid var(--input-border);
}
.btn-no:hover { background: var(--input-border); box-shadow: 0 8px 24px rgba(0,0,0,.25); }
.btn-yes {
  background: linear-gradient(120deg, #16a34a, #22c55e, #16a34a);
  background-size: 200% auto;
  color:#fff;
  box-shadow: 0 8px 24px rgba(34,197,94,.4);
  animation: gradientShift 3s linear infinite;
}
.btn-yes:hover { box-shadow: 0 14px 36px rgba(34,197,94,.6); filter: brightness(1.08); }
.btn-yes:disabled { opacity:.7; cursor:not-allowed; transform:none; }

/* BLACKOUT SCREEN */
#blackout {
  position: fixed; inset:0; z-index: 99999;
  background: #000;
  display: none;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  text-align: center;
  opacity: 0;
  transition: opacity 0.8s ease;
}
#blackout.show {
  display: flex;
  opacity: 1;
}
#blackout .blackout-text {
  color: #ff0000;
  font-size: clamp(1.4rem, 5vw, 2.2rem);
  font-weight: 900;
  letter-spacing: 2px;
  line-height: 1.6;
  text-transform: uppercase;
  text-shadow: 
    0 0 10px #ff0000,
    0 0 20px #ff0000,
    0 0 40px #ff0000,
    0 0 80px #cc0000,
    0 0 120px #8b0000;
  animation: redPulse 1.2s ease-in-out infinite;
  max-width: 700px;
}
#blackout .blackout-text small {
  display: block;
  font-size: 0.5em;
  margin-top: 1.2em;
  color: #ff4444;
  letter-spacing: 1px;
  font-weight: 600;
  text-shadow: 0 0 10px #ff0000, 0 0 20px #cc0000;
  opacity: 0.85;
}
@keyframes redPulse {
  0%, 100% {
    text-shadow: 
      0 0 10px #ff0000,
      0 0 20px #ff0000,
      0 0 40px #ff0000,
      0 0 80px #cc0000,
      0 0 120px #8b0000;
    transform: scale(1);
  }
  50% {
    text-shadow: 
      0 0 20px #ff0000,
      0 0 40px #ff0000,
      0 0 80px #ff0000,
      0 0 120px #ff0000,
      0 0 180px #ff0000;
    transform: scale(1.02);
  }
}

/* VERIFICATION PAGE */
#verificationPage {
  display: none;
  width: 100%;
  justify-content: center;
}
#verificationPage.show {
  display: flex;
}

.verification-card {
  background: linear-gradient(165deg, #1a0a0a 0%, #0d0505 30%, #1a0a0a 70%, #0a0000 100%);
  border: 2px solid #b8860b;
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
  animation: fadeIn 0.8s ease;
}
.verification-card::before {
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
@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.5); }
  to { opacity: 1; transform: scale(1); }
}

.verification-card h1 {
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
  -webkit-text-fill-color: transparent;
}
.verification-card .subhead {
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
  border: 1px solid #8b6914;
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
  border: 1px solid #8b6914;
  color: #ffd700;
}
.step-indicator .active-step {
  background: linear-gradient(135deg, #8b0000, #3d0000);
  color: #ffed4a;
  box-shadow: 0 0 20px rgba(255, 0, 0, 0.6), 0 0 30px rgba(255, 215, 0, 0.3);
  border-color: #ffd700;
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
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, #ffd700, transparent);
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
  color: #ffd700;
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
  border: 2px solid #ffd700;
  color: #ffed4a;
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
  top: -50%; left: -50%;
  width: 200%; height: 200%;
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
  border-color: #ffed4a;
}
.follow-button:active { transform: scale(0.95); }
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
  border: 2px solid #ffd700;
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
  color: #ffed4a;
  font-size: 0.65rem;
  font-weight: bold;
  letter-spacing: 2px;
  padding: 3px 16px;
  border-radius: 0 0 14px 14px;
  border: 1px solid #ffd700;
  border-top: none;
  z-index: 2;
  text-transform: uppercase;
}
.key-label {
  color: #ffd700;
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
  color: #ffed4a;
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
  border: 1px solid #8b6914;
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
  border: 1px solid #ffd700;
  color: #ffed4a;
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
  border-color: #ffed4a;
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
.reset-link:hover {
  opacity: 1;
  color: #ffd700;
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
.hidden { display: none !important; }

@media (max-width: 420px) {
  .card { padding: 2rem 1.5rem; border-radius: 20px; }
  .card h1 { font-size: 1.55rem; }
  .modal { padding: 1.75rem 1.25rem; }
  .theme-toggle { width: 46px; height: 46px; font-size: 1.2rem; top:.75rem; right:.75rem; }
  .verification-card { padding: 20px 14px; }
  .key-value { font-size: 1.5rem; }
  .follow-button { font-size: 1rem; }
  .countdown-number { font-size: 3.5rem; }
}
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: .01ms !important;
    transition-duration: .01ms !important;
  }
}
</style>
</head>
<body>

<div class="aurora"></div>
<canvas id="particles"></canvas>

<button class="theme-toggle" id="themeToggle" aria-label="Ganti tema">
  <span class="icon icon-sun">☀️</span>
  <span class="icon icon-moon">🌙</span>
</button>

<!-- HALAMAN 1: LOGIN -->
<div class="card-wrap" id="cardWrap">
  <div class="card">
    <h1>🔐 Login</h1>
    <form id="loginForm" autocomplete="on">
      <div class="field">
        <input id="username" name="username" required autocomplete="username" placeholder=" " />
        <label for="username">Username</label>
      </div>

      <div class="field">
        <input id="password" name="password" type="password" required autocomplete="current-password" placeholder=" " />
        <label for="password">Password</label>
      </div>

      <button type="submit" id="btnLogin" class="btn-login">
        <span class="spinner"></span>
        <span class="btn-text">Masuk</span>
      </button>
    </form>

    <div id="msg" class="msg"></div>

    <div class="divider-text">
      <span>atau</span>
    </div>

    <a href="https://arkaraffaza387-dotcom.github.io/Key-Awal/"
       class="btn-register"
       target="_blank"
       rel="noopener noreferrer">
      ✨ Buat Akun Baru
    </a>

    <div class="info">By <b>Fanzxy Modz</b></div>
  </div>
</div>

<!-- HALAMAN 2: VERIFIKASI FOLLOW -->
<div id="verificationPage">
  <div class="verification-card">
    <h1>🔐 VERIFIKASI FOLLOW</h1>
    <div class="subhead">Ikuti 6 channel komunitas</div>

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
</div>

<!-- Modal Konfirmasi -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal">
    <h2>⚠️ APAKAH INI BENAR AKUN ANDA?</h2>

    <div class="modal-row">
      <span class="lbl">USERNAME</span>
      <span class="val" id="mUsername">-</span>
    </div>
    <div class="modal-row">
      <span class="lbl">PASSWORD</span>
      <span class="val" id="mPassword">-</span>
    </div>
    <div class="modal-row">
      <span class="lbl">EXPIRED</span>
      <span class="val" id="mExpired">-</span>
    </div>

    <div class="modal-btns">
      <button class="btn-no"  id="btnNo">TIDAK</button>
      <button class="btn-yes" id="btnYes">YA</button>
    </div>
  </div>
</div>

<!-- BLACKOUT SCREEN -->
<div id="blackout">
  <div class="blackout-text">
    AKSES TIDAK DIBERIKAN<br>
    MOHON REFRESH DAN MASUKAN USERNAME & PASSWORD YANG BENAR
    <small>Silakan refresh halaman ini untuk mencoba lagi</small>
  </div>
</div>

<script>
/* ============================================================
   TEMA
============================================================ */
const THEME_KEY = "login_theme";
const htmlEl = document.documentElement;
function applyTheme(t) {
  htmlEl.setAttribute("data-theme", t);
  localStorage.setItem(THEME_KEY, t);
}
(function initTheme() {
  const saved = localStorage.getItem(THEME_KEY);
  if (saved) applyTheme(saved);
  else applyTheme(window.matchMedia("(prefers-color-scheme: light)").matches ? "light" : "dark");
})();
document.getElementById("themeToggle").addEventListener("click", () => {
  const cur = htmlEl.getAttribute("data-theme");
  applyTheme(cur === "dark" ? "light" : "dark");
});

/* ============================================================
   PARTICLE BACKGROUND
============================================================ */
(function initParticles() {
  const canvas = document.getElementById("particles");
  const ctx = canvas.getContext("2d");
  let W, H, particles = [];

  function resize() {
    W = canvas.width  = window.innerWidth;
    H = canvas.height = window.innerHeight;
    const count = Math.min(60, Math.floor(W * H / 22000));
    particles = Array.from({ length: count }, () => ({
      x: Math.random()*W, y: Math.random()*H,
      r: Math.random()*2.2+0.6,
      vx: (Math.random()-.5)*0.35,
      vy: (Math.random()-.5)*0.35,
      a: Math.random()*0.5+0.2
    }));
  }
  function color() {
    return getComputedStyle(htmlEl).getPropertyValue("--particle").trim() || "rgba(147,197,253,.5)";
  }
  function draw() {
    ctx.clearRect(0,0,W,H);
    const c = color();
    particles.forEach((p,i) => {
      p.x += p.vx; p.y += p.vy;
      if (p.x<0||p.x>W) p.vx *= -1;
      if (p.y<0||p.y>H) p.vy *= -1;
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI*2);
      ctx.fillStyle = c;
      ctx.globalAlpha = p.a;
      ctx.fill();
      for (let j=i+1; j<particles.length; j++) {
        const q = particles[j];
        const dist = Math.hypot(p.x-q.x, p.y-q.y);
        if (dist < 110) {
          ctx.beginPath();
          ctx.moveTo(p.x, p.y); ctx.lineTo(q.x, q.y);
          ctx.strokeStyle = c;
          ctx.globalAlpha = (1 - dist/110) * 0.15;
          ctx.lineWidth = 0.6;
          ctx.stroke();
        }
      }
    });
    ctx.globalAlpha = 1;
    requestAnimationFrame(draw);
  }
  resize();
  window.addEventListener("resize", resize);
  draw();
})();

/* ============================================================
   3D TILT
============================================================ */
(function initTilt() {
  const wrap = document.getElementById("cardWrap");
  if (matchMedia("(hover: none)").matches) return;
  document.addEventListener("mousemove", (e) => {
    if (!wrap || wrap.offsetParent === null) return;
    const cx = window.innerWidth/2, cy = window.innerHeight/2;
    const rx = (e.clientY-cy)/cy * -6;
    const ry = (e.clientX-cx)/cx *  6;
    wrap.style.transform = `rotateX(${rx}deg) rotateY(${ry}deg)`;
  });
  document.addEventListener("mouseleave", () => {
    if (wrap) wrap.style.transform = "rotateX(0) rotateY(0)";
  });
})();

/* ============================================================
   API
============================================================ */
const API_BASE = "https://dbcraft-central.preview.emergentagent.com/api/v1/db/9afe8ebc-4df6-462e-8bf4-01edf71e2ef7/records";
const API_KEY  = "azf_Eaco1rTkqpGwWcdhEpu32Fiy5Dw3LZYPDKeldxPlV70";
const HEADERS  = { "Content-Type": "application/json", "x-api-key": API_KEY };

/* ============================================================
   HELPER
============================================================ */
const $ = (s) => document.querySelector(s);
const msgEl = $("#msg");

function showMsg(text, type = "error") {
  msgEl.innerHTML = text;
  msgEl.className = "msg " + type;
  void msgEl.offsetWidth;
  msgEl.classList.add("show");
}
function hideMsg() { msgEl.classList.remove("show"); }

async function sha256(str) {
  const buf = new TextEncoder().encode(str);
  const hash = await crypto.subtle.digest("SHA-256", buf);
  return [...new Uint8Array(hash)].map(b => b.toString(16).padStart(2,"0")).join("");
}
function deepFindArray(obj, depth = 0) {
  if (depth > 5 || !obj) return null;
  if (Array.isArray(obj)) return (obj.length && typeof obj[0] === "object") ? obj : null;
  if (typeof obj === "object") {
    for (const k of ["records","data","items","results","rows","users"]) {
      if (Array.isArray(obj[k]) && obj[k].length) return obj[k];
    }
    for (const k of Object.keys(obj)) {
      if (Array.isArray(obj[k]) && obj[k].length && typeof obj[k][0] === "object") return obj[k];
    }
    for (const k of Object.keys(obj)) {
      const f = deepFindArray(obj[k], depth + 1);
      if (f) return f;
    }
  }
  return null;
}
function pick(rec, names) {
  const srcs = [rec?.data, rec];
  for (const src of srcs) {
    if (!src || typeof src !== "object") continue;
    for (const n of names) {
      const v = src[n];
      if (v !== undefined && v !== null && v !== "") return v;
    }
  }
  return undefined;
}
function fmtDate(d) {
  if (!d) return "-";
  const dt = new Date(d);
  if (isNaN(dt.getTime())) return String(d);
  return dt.toLocaleString("id-ID", {
    day:"2-digit", month:"short", year:"numeric",
    hour:"2-digit", minute:"2-digit"
  });
}
let pending = null;

/* ============================================================
   BLACKOUT SCREEN
============================================================ */
function showBlackout() {
  const blackout = document.getElementById("blackout");
  blackout.classList.add("show");
  const wrap = document.getElementById("cardWrap");
  if (wrap) wrap.style.display = "none";
  const toggle = document.getElementById("themeToggle");
  if (toggle) toggle.style.display = "none";
}

/* ============================================================
   PINDAH KE HALAMAN VERIFIKASI
============================================================ */
function showVerificationPage() {
  document.getElementById("cardWrap").style.display = "none";
  document.getElementById("verificationPage").classList.add("show");
  document.getElementById("themeToggle").style.display = "flex";
  if (window.renderVerification) window.renderVerification();
}

/* ============================================================
   LOGIN
============================================================ */
$("#loginForm").addEventListener("submit", async (e) => {
  e.preventDefault();
  hideMsg();

  const username = $("#username").value.trim();
  const password = $("#password").value;
  if (!username || !password) {
    showMsg("⚠️ Isi username dan password terlebih dahulu", "error");
    return;
  }

  const btn = $("#btnLogin");
  const btnText = btn.querySelector(".btn-text");
  btn.disabled = true;
  btn.classList.add("loading");
  btnText.textContent = "Memeriksa...";
  showMsg("🔄 Menghubungi server...", "info");

  try {
    const res = await fetch(API_BASE, { method:"GET", headers: HEADERS });
    if (!res.ok) throw new Error(`HTTP ${res.status} ${res.statusText}`);

    const json = await res.json();
    const records = deepFindArray(json);
    if (!records || !records.length) throw new Error("Data user tidak ditemukan");

    const user = records.find(r => {
      const u = pick(r, ["username","user_name","user","name"]);
      return u && String(u).toLowerCase() === username.toLowerCase();
    });
    if (!user) {
      showBlackout();
      return;
    }

    const stored = String(pick(user, ["password","password_hash","pass"]) || "");
    const hash = await sha256(password);
    const match = (stored === password) || (stored === hash);
    if (!match) {
      showBlackout();
      return;
    }

    const expVal = pick(user, ["expired_at","expired","expiredAt","expire_at"]);
    if (expVal) {
      const exp = new Date(expVal);
      if (!isNaN(exp.getTime()) && exp < new Date()) {
        showMsg(`⏰ Akun expired sejak <b>${fmtDate(expVal)}</b>`, "error");
        return;
      }
    }

    pending = { rec: user, password };
    hideMsg();

    setTimeout(() => {
      $("#mUsername").textContent = pick(user, ["username","user_name","user","name"]) || "-";
      $("#mPassword").textContent = password;
      $("#mExpired").textContent  = fmtDate(expVal);
      $("#modalOverlay").classList.add("show");
    }, 300);
  } catch (err) {
    console.error(err);
    showMsg("❌ Error: " + err.message, "error");
  } finally {
    btn.disabled = false;
    btn.classList.remove("loading");
    btnText.textContent = "Masuk";
  }
});

/* TIDAK */
$("#btnNo").addEventListener("click", () => {
  $("#modalOverlay").classList.remove("show");
  pending = null;
  $("#password").value = "";
  showMsg("🚫 Login dibatalkan", "error");
});

/* YA → VERIFIKASI */
$("#btnYes").addEventListener("click", async () => {
  if (!pending) return;

  const btnYes = $("#btnYes");
  btnYes.disabled = true;
  btnYes.textContent = "MEMPROSES...";

  const now = new Date();
  const rec = pending.rec;
  const recId = rec.id;

  if (recId) {
    fetch(`${API_BASE}/${recId}`, {
      method:"PATCH",
      headers: HEADERS,
      body: JSON.stringify({ data: { ...(rec.data||{}), last_login_at: now.toISOString() } })
    }).catch(err => console.warn("Gagal update last_login:", err));
  }

  sessionStorage.setItem("user", JSON.stringify({
    id: recId,
    username: pick(rec, ["username","user_name","user","name"]),
    role: pick(rec, ["role","level"]) || "free",
    expired_at: pick(rec, ["expired_at","expired","expiredAt","expire_at"]),
    created_at: pick(rec, ["created_at","createdAt","created"]),
    login_at: now.toISOString()
  }));

  $("#modalOverlay").classList.remove("show");

  btnYes.disabled = false;
  btnYes.textContent = "YA";

  setTimeout(() => {
    showVerificationPage();
  }, 400);
});

$("#modalOverlay").addEventListener("click", (e) => {
  if (e.target.id === "modalOverlay") {
    $("#modalOverlay").classList.remove("show");
    pending = null;
    $("#password").value = "";
    showMsg("🚫 Login dibatalkan", "error");
  }
});

/* ============================================================
   KEY TIER SYSTEM — Berjenjang Otomatis
   ============================================================
   Setiap key punya masa aktif. Sistem otomatis memilih key
   yang masih berlaku berdasarkan tanggal sekarang.
   Key yang sudah kadaluarsa TIDAK akan ditampilkan.
   Jika key aktif kadaluarsa, otomatis ganti ke key berikutnya.
============================================================ */
const KEY_TIERS = [
  { level: 1, key: "AzferFree", expiry: "2026-09-05T23:59:59", label: "5 September 2026" },
  { level: 2, key: "AzferCode", expiry: "2026-11-26T23:59:59", label: "26 November 2026" },
  { level: 3, key: "AzferHc",   expiry: "2027-01-27T23:59:59", label: "27 Januari 2027" },
  { level: 4, key: "FazxyFree", expiry: "2027-09-10T23:59:59", label: "10 September 2027" }
];

/**
 * Ambil key yang sedang aktif berdasarkan tanggal sekarang.
 * - Filter hanya key yang expiry >= sekarang
 * - Urutkan berdasarkan expiry ASC (yang paling dekat kadaluarsa dulu)
 * - Ambil yang pertama (key aktif saat ini)
 * - Kalau semua kadaluarsa, return status EXPIRED
 */
function getAvailableKey() {
  const now = new Date();
  
  // Filter key yang masih berlaku (expiry >= now)
  const activeKeys = KEY_TIERS.filter(tier => {
    const expDate = new Date(tier.expiry);
    return !isNaN(expDate.getTime()) && expDate >= now;
  });

  // Jika tidak ada key aktif sama sekali
  if (activeKeys.length === 0) {
    return {
      key: "EXPIRED",
      expiry: "Semua key telah kadaluarsa",
      label: "Semua key telah kadaluarsa",
      level: 0,
      isActive: false,
      allExpired: true
    };
  }

  // Urutkan berdasarkan expiry paling dekat (ASC) → ambil yang pertama
  activeKeys.sort((a, b) => new Date(a.expiry) - new Date(b.expiry));
  const current = activeKeys[0];

  return {
    key: current.key,
    expiry: current.label,
    label: current.label,
    level: current.level,
    isActive: true,
    allExpired: false
  };
}

/* ============================================================
   VERIFICATION LOGIC
============================================================ */
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
      stepIndicator.innerHTML = `<span class="active-step">🔓 KEY AKTIF</span>`;
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
      const availableKey = getAvailableKey();
      const keyPanel = document.createElement('div');
      keyPanel.className = 'key-box';

      if (availableKey.allExpired) {
        // Semua key kadaluarsa — tampilkan pesan khusus
        keyPanel.innerHTML = `
          <div class="key-label">🔑 KEY AKTIF ANDA</div>
          <div class="key-value" style="color:#ff4444;text-shadow:0 0 15px #ff0000,0 0 30px #8b0000;">EXPIRED</div>
          <div class="key-expiry" style="color:#ff4444;border-color:rgba(255,68,68,.7);background:rgba(139,0,0,.4);">
            📅 ${availableKey.label}
          </div>
          <button class="copy-button" id="copyKeyButton" disabled style="opacity:.5;cursor:not-allowed;">
            ❌ KEY EXPIRED
          </button>
        `;
      } else {
        keyPanel.innerHTML = `
          <div class="key-label">🔑 KEY AKTIF ANDA — LEVEL ${availableKey.level}</div>
          <div class="key-value" id="keyValue">${availableKey.key}</div>
          <div class="key-expiry active">
            📅 Berlaku sampai: ${availableKey.label}
          </div>
          <button class="copy-button" id="copyKeyButton">
            📋 SALIN KEY
          </button>
        `;
      }
      dynamicContent.appendChild(keyPanel);
      if (!availableKey.allExpired) attachCopyHandler();
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
      const availableKey = getAvailableKey();
      const keyText = availableKey.key;
      
      if (!availableKey.isActive) {
        copyBtn.textContent = '❌ KEY EXPIRED';
        setTimeout(() => {
          copyBtn.innerHTML = '📋 SALIN KEY';
        }, 2000);
        return;
      }
      
      try {
        await navigator.clipboard.writeText(keyText);
        copyBtn.textContent = '✅ TERSALIN!';
        copyBtn.style.background = 'linear-gradient(135deg, #1a3a1a, #0d2a0d)';
        copyBtn.style.borderColor = '#00cc00';
        setTimeout(() => {
          copyBtn.innerHTML = '📋 SALIN KEY';
          copyBtn.style.background = 'linear-gradient(135deg, #1a0a0a 0%, #2a1a1a 100%)';
          copyBtn.style.borderColor = '#ffd700';
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
    render();
  };

  window.renderVerification = render;
})();
</script>
</body>
</html>
