<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>عيادة المصارف - الدكتور حذيفة الحمداني</title>
  
  <style>
    :root {
      --bg-radial: radial-gradient(circle at 50% 20%, #0d2838 0%, #071624 55%, #030811 100%);
      --sidebar-bg: #08121d;
      --sidebar-hover: #122336;
      --primary: #00b48a;
      --primary-glow: rgba(0, 180, 138, 0.45);
      --accent-blue: #38bdf8;
      --accent-gold: #f59e0b;
      --accent-red: #ef4444;
      --accent-purple: #a855f7;
      --panel-bg: rgba(14, 27, 43, 0.9);
      --card-bg: rgba(19, 35, 56, 0.85);
      --card-border: #1e3a5a;
      --text-main: #f8fafc;
      --text-dim: #94a3b8;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; font-family: system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif; -webkit-tap-highlight-color: transparent; }
    body { background: var(--bg-radial); background-attachment: fixed; color: var(--text-main); min-height: 100vh; display: flex; overflow-x: hidden; }

    /* ================= 1. واجهة الدخول والقفل ================= */
    #loginGateOverlay {
      position: fixed;
      inset: 0;
      background: radial-gradient(circle at center, #0f2d42 0%, #06111e 70%, #02060c 100%);
      z-index: 10000;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 16px;
      transition: opacity 0.3s ease, visibility 0.3s ease;
    }
    .login-card {
      background: rgba(15, 29, 46, 0.98);
      border: 1px solid var(--card-border);
      backdrop-filter: blur(16px);
      border-radius: 24px;
      padding: 30px 22px;
      width: 100%;
      max-width: 420px;
      text-align: center;
      box-shadow: 0 20px 50px rgba(0,0,0,0.85), 0 0 30px rgba(0, 180, 138, 0.25);
    }
    .hudhaifa-logo-frame {
      width: 90px;
      height: 90px;
      border-radius: 50%;
      margin: 0 auto 12px;
      border: 3px solid var(--accent-blue);
      box-shadow: 0 0 22px rgba(56, 189, 248, 0.55);
      background: white;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }

    /* الشريط الجانبي */
    aside {
      width: 72px;
      background: var(--sidebar-bg);
      border-left: 1px solid var(--card-border);
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 12px 0;
      gap: 8px;
      flex-shrink: 0;
      z-index: 40;
      box-shadow: 4px 0 20px rgba(0,0,0,0.6);
    }
    @media (min-width: 768px) { aside { width: 90px; gap: 12px; } }

    .brand-logo-circle {
      width: 46px;
      height: 46px;
      border-radius: 50%;
      border: 2px solid var(--accent-blue);
      background: white;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 10px rgba(56, 189, 248, 0.4);
      margin-bottom: 4px;
      overflow: hidden;
    }
    .brand-text { font-size: 0.65rem; font-weight: 900; color: var(--accent-blue); display: block; text-align: center; }

    .nav-btn {
      width: 62px;
      height: 56px;
      background: transparent;
      border: 1px solid transparent;
      border-radius: 12px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 3px;
      color: var(--text-dim);
      cursor: pointer;
      transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    }
    @media (min-width: 768px) { .nav-btn { width: 72px; height: 62px; border-radius: 14px; } }
    .nav-btn svg { width: 20px; height: 20px; fill: currentColor; }
    .nav-btn span { font-size: 0.65rem; font-weight: 800; }
    .nav-btn:hover { background: var(--sidebar-hover); color: var(--accent-blue); transform: translateY(-2px); }
    .nav-btn.active {
      background: linear-gradient(135deg, rgba(0, 180, 138, 0.25), rgba(56, 189, 248, 0.2));
      color: white;
      border-color: var(--primary);
      box-shadow: 0 0 16px rgba(0, 180, 138, 0.35);
    }
    .nav-btn.active svg { fill: var(--primary); }

    /* الحاوية الرئيسية */
    .app-main { flex: 1; display: flex; flex-direction: column; height: 100vh; overflow-y: auto; min-width: 0; }

    /* الشريط العلوي */
    .top-header {
      background: rgba(8, 18, 29, 0.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--card-border);
      padding: 10px 14px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 8px;
      position: sticky;
      top: 0;
      z-index: 30;
    }
    .clinic-title h1 { font-size: 1.05rem; font-weight: 900; color: white; display: flex; align-items: center; gap: 6px; }
    .clinic-badge { font-size: 0.68rem; background: rgba(0, 180, 138, 0.15); color: var(--primary); border: 1px solid var(--primary); padding: 2px 8px; border-radius: 20px; font-weight: bold; }

    .header-ctrls { display: flex; gap: 6px; align-items: center; }
    .btn-action {
      background: #122336;
      color: white;
      border: 1px solid var(--card-border);
      padding: 8px 12px;
      border-radius: 10px;
      font-size: 0.76rem;
      font-weight: bold;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 5px;
      transition: all 0.2s;
    }
    .btn-action:hover { background: #1c3552; border-color: var(--accent-blue); }
    .btn-emerald { background: var(--primary); border: none; color: #04141d; font-weight: 900; }
    .btn-emerald:hover { background: #02cfa0; box-shadow: 0 0 16px var(--primary-glow); }

    /* الصفحات والمحتوى */
    .content-viewport { padding: 12px; flex: 1; }
    .page-tab { display: none; }
    .page-tab.active { display: block; animation: fadeIn 0.3s ease; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(4px); } to { opacity: 1; transform: translateY(0); } }

    .input-box {
      background: #06101c;
      border: 1px solid var(--card-border);
      color: white;
      padding: 9px 12px;
      border-radius: 10px;
      font-size: 0.85rem;
      outline: none;
      transition: border 0.2s;
    }
    .input-box:focus { border-color: var(--primary); box-shadow: 0 0 10px rgba(0, 180, 138, 0.25); }

    /* بطاقات المراجعين المتجاوبة */
    .patients-grid { display: grid; grid-template-columns: 1fr; gap: 12px; margin-top: 14px; }
    @media (min-width: 768px) { .patients-grid { grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); } }

    .patient-card {
      background: var(--card-bg);
      backdrop-filter: blur(8px);
      border: 1px solid var(--card-border);
      border-radius: 16px;
      padding: 14px;
      display: flex;
      flex-direction: column;
      gap: 9px;
      border-right: 5px solid var(--primary);
      transition: all 0.25s;
    }
    .patient-card:hover { transform: translateY(-2px); box-shadow: 0 8px 25px rgba(0,0,0,0.45); border-color: var(--accent-blue); }
    
    .pt-top { display: flex; justify-content: space-between; align-items: flex-start; }
    .pt-avatar { width: 40px; height: 40px; border-radius: 10px; background: linear-gradient(135deg, #1e3a5a, #0d2838); display: flex; align-items: center; justify-content: center; font-size: 1.2rem; border: 1px solid var(--accent-blue); }
    .pt-info h3 { font-size: 1rem; font-weight: 900; color: white; }
    .pt-info p { font-size: 0.72rem; color: var(--text-dim); margin-top: 2px; }
    .pt-dates-badge { font-size: 0.68rem; background: #071422; padding: 3px 6px; border-radius: 6px; border: 1px solid var(--card-border); color: var(--accent-blue); }

    .pt-finance-bar {
      background: #081422;
      border: 1px solid #1c3652;
      border-radius: 8px;
      padding: 6px 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.74rem;
    }
    .pt-debt-alert { font-weight: 900; color: #ef4444; background: rgba(239, 68, 68, 0.15); padding: 2px 6px; border-radius: 6px; }

    .pt-actions { display: grid; grid-template-columns: repeat(4, 1fr); gap: 5px; margin-top: auto; padding-top: 8px; border-top: 1px solid var(--card-border); }
    .btn-pt-action {
      background: #112032;
      border: 1px solid var(--card-border);
      color: white;
      padding: 6px 2px;
      border-radius: 8px;
      font-size: 0.68rem;
      font-weight: bold;
      cursor: pointer;
      text-align: center;
      transition: all 0.2s;
    }
    .btn-pt-action:hover { background: var(--primary); color: #05101a; border-color: var(--primary); }

    /* ================= الفكين 3D ================= */
    .jaw-3d-wrapper {
      background: radial-gradient(circle at center, #0e243a 0%, #06111e 100%);
      border: 2px solid var(--card-border);
      border-radius: 20px;
      padding: 20px 6px;
      position: relative;
      overflow-x: auto;
      box-shadow: inset 0 0 50px rgba(0,0,0,0.85);
    }
    .jaw-arch-title { text-align: center; font-size: 0.8rem; font-weight: 900; color: var(--accent-blue); margin-bottom: 6px; }
    .dental-arch-3d { display: flex; justify-content: center; align-items: center; gap: 2px; position: relative; margin: 12px 0; padding: 0 4px; }
    @media (min-width: 650px) { .dental-arch-3d { gap: 5px; } }

    .tooth-3d {
      width: 22px;
      height: 72px;
      display: flex;
      flex-direction: column;
      align-items: center;
      cursor: pointer;
      position: relative;
      user-select: none;
      transition: all 0.25s cubic-bezier(0.34, 1.56, 0.64, 1);
    }
    @media (min-width: 768px) { .tooth-3d { width: 34px; height: 94px; } }
    .tooth-3d:hover { transform: translateY(-6px) scale(1.15); z-index: 25; }
    .tooth-3d.active-selected { transform: translateY(-8px) scale(1.2); z-index: 30; filter: drop-shadow(0 0 12px #38bdf8); }
    .tooth-number { font-size: 0.6rem; font-weight: 900; color: #64748b; margin-top: 2px; }

    .root-3d, .crown-3d { transition: fill 0.3s ease; }
    .tooth-3d.is-endo .root-3d { fill: url(#redGlowGrad) !important; }
    .tooth-3d.is-filling .crown-3d { fill: url(#blueGlowGrad) !important; }
    .tooth-3d.is-crown .crown-3d { fill: url(#goldGlowGrad) !important; }
    .tooth-3d.is-extract { opacity: 0.3; filter: grayscale(1); }
    .tooth-3d.is-extract::after { content: "✕"; position: absolute; top: 40%; left: 50%; transform: translate(-50%, -50%); color: #ef4444; font-size: 1.6rem; font-weight: 900; }

    .bubble-tag-3d {
      position: absolute;
      background: linear-gradient(135deg, #f59e0b, #d97706);
      color: #030811;
      font-size: 0.62rem;
      font-weight: 900;
      padding: 2px 6px;
      border-radius: 6px;
      white-space: nowrap;
      pointer-events: none;
      z-index: 35;
      box-shadow: 0 4px 10px rgba(0,0,0,0.6);
    }
    .bubble-tag-3d.up { top: -24px; }
    .bubble-tag-3d.down { bottom: -24px; }

    .color-swatch-bar {
      display: flex;
      justify-content: center;
      gap: 12px;
      background: rgba(14, 27, 43, 0.95);
      padding: 6px 16px;
      border-radius: 30px;
      width: fit-content;
      margin: 14px auto 0;
      border: 1px solid var(--card-border);
    }
    .color-dot { width: 20px; height: 20px; border-radius: 50%; cursor: pointer; border: 2px solid transparent; }
    .color-dot:hover { transform: scale(1.2); border-color: white; }

    /* النوافذ العائمة */
    .modal-overlay {
      position: fixed;
      inset: 0;
      background: rgba(3, 8, 17, 0.85);
      backdrop-filter: blur(6px);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      padding: 12px;
    }
    .modal-card {
      background: #0f1c2d;
      border: 1px solid var(--card-border);
      border-radius: 18px;
      width: 100%;
      max-width: 540px;
      max-height: 90vh;
      overflow-y: auto;
      box-shadow: 0 25px 50px rgba(0,0,0,0.7);
    }
    .modal-head {
      background: #07121f;
      padding: 12px 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: 900;
      border-bottom: 1px solid var(--card-border);
    }
    .modal-body { padding: 16px; display: flex; flex-direction: column; gap: 12px; }

    .allergy-alert-banner {
      background: linear-gradient(135deg, #ef4444, #991b1b);
      color: white;
      padding: 10px 14px;
      border-radius: 10px;
      display: none;
      align-items: center;
      gap: 8px;
      font-weight: 900;
      font-size: 0.82rem;
    }

    .finance-privacy-blur { filter: blur(8px); user-select: none; pointer-events: none; }

    /* الطباعة الشاملة A4 */
    #printableMasterSheet { display: none; background: white !important; color: #0f172a !important; padding: 24px; }
    @media print {
      body * { visibility: hidden; }
      #printableMasterSheet, #printableMasterSheet * { visibility: visible; }
      #printableMasterSheet {
        display: block !important;
        position: fixed;
        left: 0;
        top: 0;
        width: 100%;
        background: white !important;
        color: #0f172a !important;
        margin: 0;
        padding: 20px;
      }
    }
  </style>
</head>
<body>

  <!-- تدرجات SVG 3D للأسنان -->
  <svg style="position: absolute; width: 0; height: 0;" aria-hidden="true">
    <defs>
      <linearGradient id="toothNormalGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#ffffff"/>
        <stop offset="60%" stop-color="#f1f5f9"/>
        <stop offset="100%" stop-color="#cbd5e1"/>
      </linearGradient>
      <linearGradient id="rootNormalGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#e2e8f0"/>
        <stop offset="70%" stop-color="#cbd5e1"/>
        <stop offset="100%" stop-color="#94a3b8"/>
      </linearGradient>
      <linearGradient id="redGlowGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#f87171"/>
        <stop offset="100%" stop-color="#dc2626"/>
      </linearGradient>
      <linearGradient id="blueGlowGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#38bdf8"/>
        <stop offset="100%" stop-color="#0284c7"/>
      </linearGradient>
      <linearGradient id="goldGlowGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#fbbf24"/>
        <stop offset="100%" stop-color="#d97706"/>
      </linearGradient>
    </defs>
  </svg>

  <!-- ================= واجهة الدخول مع قفل الرمز السري ================= -->
  <div id="loginGateOverlay">
    <div class="login-card">
      <div class="hudhaifa-logo-frame">
        <!-- رسم الشعار الدائري الأصلي للدكتور حذيفة الحمداني -->
        <svg viewBox="0 0 200 200" style="width:100%; height:100%;">
          <circle cx="100" cy="100" r="98" fill="#ffffff" stroke="#38bdf8" stroke-width="4"/>
          <!-- شكل السن الأزرق في الخلفية -->
          <path d="M40 70 C30 30 75 15 100 35 C125 15 170 30 160 70 C155 100 145 130 135 150 C125 130 115 125 100 125 C85 125 75 130 65 150 C55 130 45 100 40 70 Z" fill="#29a8eb" opacity="0.95"/>
          <!-- مجسم الوجه والابتسامة الكحلي -->
          <circle cx="100" cy="110" r="50" fill="#0f3458"/>
          <path d="M75 112 C75 92 86 80 100 80 C114 80 125 92 125 112 C125 132 114 148 100 148 C86 148 75 132 75 112 Z" fill="#ffffff"/>
          <path d="M82 105 C85 96 92 90 100 90 C108 90 115 96 118 105 C112 100 106 98 100 98 C94 98 88 100 82 105 Z" fill="#0f3458"/>
          <!-- الابتسامة واللحية الأنيقة -->
          <path d="M88 126 Q100 138 112 126 Q100 132 88 126 Z" fill="#0f3458"/>
          <path d="M70 110 C70 140 85 165 100 168 C115 165 130 140 130 110 C130 135 118 160 100 160 C82 160 70 135 70 110 Z" fill="#0f3458"/>
          <!-- العيون والشعر -->
          <ellipse cx="91" cy="108" rx="4" ry="5" fill="#0f3458"/>
          <ellipse cx="109" cy="108" rx="4" ry="5" fill="#0f3458"/>
          <path d="M72 90 Q100 68 128 90 Q100 78 72 90 Z" fill="#0f3458"/>
        </svg>
      </div>
      <h2 style="font-size:1.3rem; color:white; font-weight:900;">عيادة المصارف</h2>
      <p style="font-size:0.82rem; color:var(--accent-blue); font-weight:bold; margin-bottom:16px;">الدكتور حذيفة الحمداني - طب وجراحة الأسنان</p>

      <div style="display:flex; flex-direction:column; gap:10px;">
        <form onsubmit="handleDoctorPinSubmit(event)" style="background:#071422; border:1px solid #1c3d5c; border-radius:12px; padding:12px;">
          <label style="font-size:0.75rem; color:#94a3b8; display:block; margin-bottom:6px;">🔒 رمز دخول الدكتور حذيفة الحمداني:</label>
          <div style="display:flex; gap:6px;">
            <input type="password" id="docPinInput" inputmode="numeric" placeholder="أدخل الرمز السري" class="input-box" style="flex:1; text-align:center; font-size:1.1rem; letter-spacing:4px;">
            <button type="submit" class="btn-action btn-emerald">دخول</button>
          </div>
          <div id="pinErrorMsg" style="color:#ef4444; font-size:0.75rem; margin-top:6px; display:none; font-weight:bold;">⚠️ الرمز السري غير صحيح، يرجى المحاولة مجدداً</div>
        </form>

        <button type="button" class="btn-action" style="justify-content:center; padding:10px; font-size:0.82rem;" onclick="unlockClinic('staff')">
          📋 دخول السكرتارية والاستقبال (مباشر)
        </button>
      </div>
    </div>
  </div>

  <!-- القائمة الجانبية -->
  <aside>
    <div class="brand-logo-circle">
      <svg viewBox="0 0 200 200" style="width:100%; height:100%;">
        <circle cx="100" cy="100" r="98" fill="#ffffff"/>
        <path d="M40 70 C30 30 75 15 100 35 C125 15 170 30 160 70 C155 100 145 130 135 150 C125 130 115 125 100 125 C85 125 75 130 65 150 C55 130 45 100 40 70 Z" fill="#29a8eb"/>
        <circle cx="100" cy="110" r="50" fill="#0f3458"/>
        <path d="M75 112 C75 92 86 80 100 80 C114 80 125 92 125 112 C125 132 114 148 100 148 C86 148 75 132 75 112 Z" fill="#ffffff"/>
        <ellipse cx="91" cy="108" rx="4" ry="5" fill="#0f3458"/>
        <ellipse cx="109" cy="108" rx="4" ry="5" fill="#0f3458"/>
        <path d="M88 126 Q100 138 112 126 Q100 132 88 126 Z" fill="#0f3458"/>
      </svg>
    </div>
    <span class="brand-text">د. حذيفة</span>

    <button class="nav-btn active" onclick="switchView('tabPatients', this)">
      <svg viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-5 14H7v-2h7v2zm3-4H7v-2h10v2zm0-4H7V7h10v2z"/></svg>
      <span>المراجعين</span>
    </button>

    <button class="nav-btn" onclick="switchView('tabJaws', this)">
      <svg viewBox="0 0 24 24"><path d="M18.6 6.62c-1.44-3.82-4.9-4.62-6.6-4.62s-5.16.8-6.6 4.62c-1.57 4.18-.76 8.59.31 12.08.38 1.25 1.13 2.3 2.19 3.03.74.52 1.63.78 2.54.74.88-.04 1.56-.7 1.56-1.58v-4.89h0c0-.55.45-1 1-1s1 .45 1 1v4.89c0 .88.68 1.54 1.56 1.58.91.04 1.8-.22 2.54-.74 1.06-.73 1.81-1.78 2.19-3.03 1.07-3.49 1.88-7.9.31-12.08z"/></svg>
      <span>الفكين 3D</span>
    </button>

    <button class="nav-btn" onclick="switchView('tabAppointments', this)">
      <svg viewBox="0 0 24 24"><path d="M19 4h-1V2h-2v2H8V2H6v2H5c-1.11 0-1.99.9-1.99 2L3 20c0 1.1.89 2 2 2h14c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 16H5V10h14v10zm0-12H5V6h14v2z"/></svg>
      <span>المواعيد</span>
    </button>

    <button class="nav-btn" onclick="switchView('tabFinance', this)">
      <svg viewBox="0 0 24 24"><path d="M21 18v1c0 1.1-.9 2-2 2H5c-1.11 0-2-.9-2-2V5c0-1.1.89-2 2-2h14c1.1 0 2 .9 2 2v1h-9c-1.11 0-2 .9-2 2v8c0 1.1.89 2 2 2h9zm-9-2h10V8H12v8zm4-2.5c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5z"/></svg>
      <span>المالية 🔒</span>
    </button>

    <button class="nav-btn" onclick="switchView('tabWhatsapp', this)">
      <svg viewBox="0 0 24 24"><path d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5c-1.66 0-3 1.34-3 3s1.34 3 3 3zm-8 0c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5C6.34 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/></svg>
      <span>واتساب 💬</span>
    </button>

    <button class="nav-btn" onclick="switchView('tabStaff', this)">
      <svg viewBox="0 0 24 24"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>
      <span>الكادر 👨‍⚕️</span>
    </button>
  </aside>

  <!-- جسم التطبيق الرئيسي -->
  <div class="app-main">
    
    <!-- الشريط العلوي -->
    <header class="top-header">
      <div class="clinic-title">
        <h1>
          <span>عيادة المصارف - د. حذيفة الحمداني</span>
          <span class="clinic-badge" id="currentRoleBadge">المدير: د. حذيفة الحمداني</span>
        </h1>
      </div>

      <div class="header-ctrls">
        <button class="btn-action" onclick="speakDailySchedule()">🔊 نطق المواعيد</button>
        <button class="btn-action btn-emerald" onclick="openModal('newPatientModal')">➕ مراجع جديد</button>
      </div>
    </header>

    <div class="content-viewport">

      <!-- ================= 1. سجل المراجعين ================= -->
      <section id="tabPatients" class="page-tab active">
        <div style="display:flex; justify-content:space-between; flex-wrap:wrap; gap:10px;">
          <input type="text" id="patientSearchBox" oninput="filterPatientsList()" placeholder="🔍 ابحث باسم المريض أو رقم الهاتف..." class="input-box" style="flex:1; max-width:320px;">
          <button class="btn-action" onclick="exportPatientsCsv()">📊 تصدير Excel</button>
        </div>
        <div class="patients-grid" id="patientsContainer"></div>
      </section>

      <!-- ================= 2. المخطط السريري للفكين 3D ================= -->
      <section id="tabJaws" class="page-tab">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:12px; flex-wrap:wrap; gap:8px;">
          <div>
            <h3 style="font-size:1.05rem; font-weight:900; color:var(--accent-blue);">المخطط التشريحي للفكين (3D Dental Arches)</h3>
            <p style="font-size:0.75rem; color:var(--text-dim);">المراجع المحدد: <strong id="chartPatientTitle" style="color:white;">--</strong></p>
          </div>
          <button class="btn-action btn-emerald" onclick="printMasterReportForCurrent()">🖨 طباعة التقرير الشامل (A4)</button>
        </div>

        <div class="jaw-3d-wrapper" id="dentalChartBox">
          <div style="display:flex; justify-content:space-between; color:var(--accent-blue); font-weight:900; font-size:0.75rem; padding:0 10px;">
            <span>اليمين (Right)</span>
            <span>اليسار (Left)</span>
          </div>

          <div class="jaw-arch-title">الفك العلوي (Upper Arch)</div>
          <div class="dental-arch-3d" id="upperArch"></div>

          <div class="dental-arch-3d" id="lowerArch" style="margin-top:20px;"></div>
          <div class="jaw-arch-title" style="margin-top:6px;">الفك السفلي (Lower Arch)</div>

          <div class="color-swatch-bar">
            <div class="color-dot" style="background:#ffffff;" title="سليم" onclick="setChartColor('normal')"></div>
            <div class="color-dot" style="background:#38bdf8;" title="حشوة بيضاء" onclick="setChartColor('filling')"></div>
            <div class="color-dot" style="background:#ef4444;" title="عصب / جذر" onclick="setChartColor('endo')"></div>
            <div class="color-dot" style="background:#f59e0b;" title="تغليف / تاج" onclick="setChartColor('crown')"></div>
            <div class="color-dot" style="background:#64748b;" title="قلع سن" onclick="setChartColor('extract')"></div>
          </div>
        </div>
      </section>

      <!-- ================= 3. جدول المواعيد ================= -->
      <section id="tabAppointments" class="page-tab">
        <div style="display:flex; justify-content:space-between; gap:10px; margin-bottom:12px; flex-wrap:wrap;">
          <input type="date" id="appointmentDateFilter" onchange="renderAppointments()" class="input-box">
          <button class="btn-action btn-emerald" onclick="openNewAppModal()">➕ حجز موعد مراجع</button>
        </div>
        <div id="appointmentsList" style="display:flex; flex-direction:column; gap:8px;"></div>
      </section>

      <!-- ================= 4. الإدارة المالية ================= -->
      <section id="tabFinance" class="page-tab">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:12px;">
          <h3 style="font-size:1.05rem; color:var(--accent-blue); font-weight:900;">الإدارة المالية للعيادة</h3>
          <button class="btn-action" id="togglePrivacyBtn" onclick="toggleFinancialPrivacy()">👁️ إظهار/إخفاء الأرقام</button>
        </div>

        <div id="financeCardsContainer" style="display:grid; grid-template-columns:repeat(auto-fit, minmax(160px, 1fr)); gap:10px; margin-bottom:14px;">
          <div style="background:var(--card-bg); padding:12px; border-radius:12px; border-right:4px solid var(--primary);">
            <div style="font-size:0.72rem; color:var(--text-dim);">مقبوضات كاش (💵):</div>
            <h3 id="statCash" style="color:var(--primary); font-size:1.3rem;">0 د.ع</h3>
          </div>
          <div style="background:var(--card-bg); padding:12px; border-radius:12px; border-right:4px solid var(--accent-blue);">
            <div style="font-size:0.72rem; color:var(--text-dim);">مقبوضات بطاقة (💳):</div>
            <h3 id="statCard" style="color:var(--accent-blue); font-size:1.3rem;">0 د.ع</h3>
          </div>
          <div style="background:var(--card-bg); padding:12px; border-radius:12px; border-right:4px solid var(--accent-red);">
            <div style="font-size:0.72rem; color:var(--text-dim);">الديون المتبقية:</div>
            <h3 id="statDebt" style="color:var(--accent-red); font-size:1.3rem;">0 د.ع</h3>
          </div>
        </div>
        <div id="financeList" style="display:flex; flex-direction:column; gap:8px;"></div>
      </section>

      <!-- ================= 5. التواصل عبر واتساب ================= -->
      <section id="tabWhatsapp" class="page-tab">
        <h3 style="font-size:1rem; color:var(--accent-blue); margin-bottom:12px;">تذكير المراجعين عبر WhatsApp</h3>
        <div id="whatsappList" style="display:flex; flex-direction:column; gap:8px;"></div>
      </section>

      <!-- ================= 6. قسم كادر الأطباء (حتى 10 أطباء) ================= -->
      <section id="tabStaff" class="page-tab">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:12px;">
          <div>
            <h3 style="font-size:1.05rem; color:var(--accent-blue); font-weight:900;">كادر أطباء عيادة المصارف (حتى 10 أطباء)</h3>
            <p style="font-size:0.75rem; color:var(--text-dim);">بإشراف الدكتور حذيفة الحمداني</p>
          </div>
          <button class="btn-action btn-emerald" onclick="openModal('newDoctorModal')">➕ إضافة طبيب</button>
        </div>
        <div id="staffListWrapper" style="display:grid; grid-template-columns:repeat(auto-fill, minmax(260px, 1fr)); gap:10px;"></div>
      </section>

    </div>
  </div>

  <!-- ================= نافذة إضافة طبيب للكادر ================= -->
  <div class="modal-overlay" id="newDoctorModal">
    <div class="modal-card" style="max-width:420px;">
      <div class="modal-head">
        <span>إضافة طبيب جديد للكادر</span>
        <button style="background:none; border:none; color:white; font-size:1.5rem; cursor:pointer;" onclick="closeModal('newDoctorModal')">&times;</button>
      </div>
      <form onsubmit="handleSaveNewDoctor(event)" class="modal-body">
        <div>
          <label style="font-size:0.8rem; font-weight:bold;">اسم الطبيب:</label>
          <input type="text" id="inpDocName" required placeholder="مثال: د. أحمد يوسف" class="input-box" style="width:100%; margin-top:4px;">
        </div>
        <div>
          <label style="font-size:0.8rem; font-weight:bold;">الاختصاص:</label>
          <input type="text" id="inpDocSpecialty" required placeholder="مثال: أخصائي جراحة الفم والزراعة" class="input-box" style="width:100%; margin-top:4px;">
        </div>
        <button type="submit" class="btn-action btn-emerald" style="justify-content:center;">حفظ الطبيب</button>
      </form>
    </div>
  </div>

  <!-- ================= نافذة إجراء السن والجلسات ================= -->
  <div class="modal-overlay" id="toothActionModal">
    <div class="modal-card">
      <div class="modal-head">
        <span>إجراء للسن رقم: <strong id="lblToothNum" style="color:var(--accent-blue);"></strong></span>
        <button style="background:none; border:none; color:white; font-size:1.5rem; cursor:pointer;" onclick="closeModal('toothActionModal')">&times;</button>
      </div>
      <div class="modal-body">
        <div style="display:grid; grid-template-columns:1fr 1fr; gap:8px;">
          <div>
            <label style="font-size:0.8rem; font-weight:bold;">نوع الإجراء:</label>
            <select id="toothOpSelect" class="input-box" style="width:100%; margin-top:4px;" onchange="toggleMeasurementFields()">
              <option value="حشوة جذر">حشوة جذر / سحب عصب (Endo)</option>
              <option value="حشوة بيضاء">حشوة بيضاء (Composite)</option>
              <option value="زراعة سن">زراعة سن (Implant)</option>
              <option value="تغليف السن">تغليف السن (Crown)</option>
              <option value="قلع سن">قلع سن (Extraction)</option>
              <option value="تقويم أسنان">تقويم أسنان (Orthodontics)</option>
            </select>
          </div>

          <div>
            <label style="font-size:0.8rem; font-weight:bold; color:var(--accent-gold);">رقم الجلسة:</label>
            <select id="toothSessionSelect" class="input-box" style="width:100%; margin-top:4px;">
              <option value="الجلسة الأولى">الجلسة الأولى</option>
              <option value="الجلسة الثانية">الجلسة الثانية</option>
              <option value="الجلسة الثالثة">الجلسة الثالثة</option>
              <option value="جلسة إنهاء العلاج">جلسة إنهاء العلاج</option>
              <option value="جلسة متابعة ومعاينة">جلسة متابعة ومعاينة</option>
            </select>
          </div>
        </div>

        <div id="endoMeasureBox" style="background:#071422; padding:10px; border-radius:10px; border:1px solid #1c3d5c;">
          <h4 style="font-size:0.75rem; color:#38bdf8; margin-bottom:6px;">📏 عمق الأقنية (Working Length - ملم):</h4>
          <div style="display:grid; grid-template-columns:1fr 1fr; gap:6px;">
            <input type="text" id="inpCanal1" placeholder="MB (21.5mm)" class="input-box">
            <input type="text" id="inpCanal2" placeholder="ML (21.0mm)" class="input-box">
            <input type="text" id="inpCanal3" placeholder="DB (20.5mm)" class="input-box">
            <input type="text" id="inpCanal4" placeholder="Palatal/Distal" class="input-box">
          </div>
        </div>

        <div id="implantMeasureBox" style="background:#071422; padding:10px; border-radius:10px; border:1px solid #1c3d5c; display:none;">
          <h4 style="font-size:0.75rem; color:#f59e0b; margin-bottom:6px;">🔩 أبعاد الغرسة:</h4>
          <div style="display:grid; grid-template-columns:1fr 1fr; gap:6px;">
            <input type="text" id="inpImpLength" placeholder="الطول (11.5mm)" class="input-box">
            <input type="text" id="inpImpDia" placeholder="القطر (4.2mm)" class="input-box">
            <input type="text" id="inpImpTorque" placeholder="العزم (Torque)" class="input-box" style="grid-column:span 2;">
          </div>
        </div>

        <div id="orthoMeasureBox" style="background:#071422; padding:10px; border-radius:10px; border:1px solid #1c3d5c; display:none;">
          <h4 style="font-size:0.75rem; color:#a855f7; margin-bottom:6px;">📐 قياسات التقويم:</h4>
          <div style="display:grid; grid-template-columns:1fr 1fr; gap:6px;">
            <input type="text" id="inpOrthoOverjet" placeholder="Overjet (ملم)" class="input-box">
            <input type="text" id="inpOrthoWire" placeholder="السلك (0.016 NiTi)" class="input-box">
          </div>
        </div>

        <div>
          <label style="font-size:0.8rem; font-weight:bold;">نص بالون الملاحظة (Bubble Note):</label>
          <input type="text" id="toothBubbleInput" placeholder="مثال: تنظيف وتوسيع..." class="input-box" style="width:100%; margin-top:4px;">
        </div>

        <button class="btn-action btn-emerald" style="width:100%; justify-content:center;" onclick="applyToothChanges()">تثبيت الإجراء</button>
      </div>
    </div>
  </div>

  <!-- ================= نافذة مراجع جديد ================= -->
  <div class="modal-overlay" id="newPatientModal">
    <div class="modal-card">
      <div class="modal-head">
        <span>إضافة مراجع جديد</span>
        <button style="background:none; border:none; color:white; font-size:1.5rem; cursor:pointer;" onclick="closeModal('newPatientModal')">&times;</button>
      </div>
      <form onsubmit="handleSavePatient(event)" class="modal-body">
        <input type="text" id="newPtName" required placeholder="اسم المراجع الكامل" class="input-box">
        
        <div style="display:flex; gap:8px;">
          <input type="number" id="newPtAge" required placeholder="العمر" class="input-box" style="flex:1;">
          <input type="tel" id="newPtPhone" required placeholder="رقم الهاتف" class="input-box" style="flex:1;">
        </div>

        <input type="text" id="newPtAddress" placeholder="السكن / المنطقة" class="input-box">

        <div>
          <label style="font-size:0.8rem; font-weight:bold; color:var(--primary);">الطبيب المعالج:</label>
          <select id="newPtDoctor" class="input-box" style="width:100%; margin-top:4px;"></select>
        </div>

        <div style="background:#071422; padding:10px; border-radius:10px; border:1px solid #1c3652;">
          <h4 style="font-size:0.8rem; color:var(--accent-gold); margin-bottom:6px;">💰 الحساب المالي (داخلي فقط):</h4>
          <div style="display:grid; grid-template-columns:1fr 1fr; gap:6px;">
            <div>
              <label style="font-size:0.72rem; color:#94a3b8;">سعر الإجراء (د.ع):</label>
              <input type="number" id="newPtCost" value="100000" oninput="recalcNewPatientDebt()" class="input-box" style="width:100%; margin-top:2px;">
            </div>
            <div>
              <label style="font-size:0.72rem; color:#94a3b8;">المدفوع (د.ع):</label>
              <input type="number" id="newPtPaid" value="50000" oninput="recalcNewPatientDebt()" class="input-box" style="width:100%; margin-top:2px;">
            </div>
          </div>
          <div style="margin-top:6px; font-size:0.78rem; font-weight:bold; color:#38bdf8;">
            المتبقي بذمته: <span id="lblNewPtDebt" style="color:#ef4444; font-size:0.9rem;">50,000</span> د.ع
          </div>
        </div>

        <input type="text" id="newPtHealth" placeholder="الحساسية الدوائية (بنسلين، سلفا، بروفين... أو سليم)" class="input-box" style="border-color:#ef4444;">
        
        <div>
          <label style="font-size:0.8rem; font-weight:bold; color:var(--accent-blue);">ملاحظات الطبيب:</label>
          <textarea id="newPtDocNotes" placeholder="ملاحظات سريرية وتشخيص..." class="input-box" style="width:100%; height:60px; margin-top:4px;"></textarea>
        </div>

        <button type="submit" class="btn-action btn-emerald" style="justify-content:center;">حفظ المراجع</button>
      </form>
    </div>
  </div>

  <!-- ================= نافذة تعديل بيانات المراجع ================= -->
  <div class="modal-overlay" id="editPatientModal">
    <div class="modal-card">
      <div class="modal-head">
        <span>تعديل مراجع: <strong id="lblEditPtTitle" style="color:var(--accent-blue);"></strong></span>
        <button style="background:none; border:none; color:white; font-size:1.5rem; cursor:pointer;" onclick="closeModal('editPatientModal')">&times;</button>
      </div>
      <form onsubmit="handleUpdatePatient(event)" class="modal-body">
        <input type="hidden" id="editPtId">
        <input type="text" id="editPtName" required placeholder="اسم المراجع الكامل" class="input-box">
        
        <div style="display:flex; gap:8px;">
          <input type="number" id="editPtAge" required placeholder="العمر" class="input-box" style="flex:1;">
          <input type="tel" id="editPtPhone" required placeholder="رقم الهاتف" class="input-box" style="flex:1;">
        </div>

        <input type="text" id="editPtAddress" placeholder="السكن / المنطقة" class="input-box">

        <div>
          <label style="font-size:0.8rem; font-weight:bold; color:var(--primary);">الطبيب المعالج:</label>
          <select id="editPtDoctor" class="input-box" style="width:100%; margin-top:4px;"></select>
        </div>

        <div style="background:#071422; padding:10px; border-radius:10px; border:1px solid #1c3652;">
          <h4 style="font-size:0.8rem; color:var(--accent-gold); margin-bottom:6px;">💰 تعديل الحساب المالي:</h4>
          <div style="display:grid; grid-template-columns:1fr 1fr; gap:6px;">
            <div>
              <label style="font-size:0.72rem; color:#94a3b8;">السعر الإجمالي:</label>
              <input type="number" id="editPtCost" oninput="recalcEditPatientDebt()" class="input-box" style="width:100%; margin-top:2px;">
            </div>
            <div>
              <label style="font-size:0.72rem; color:#94a3b8;">المدفوع:</label>
              <input type="number" id="editPtPaid" oninput="recalcEditPatientDebt()" class="input-box" style="width:100%; margin-top:2px;">
            </div>
          </div>
          <div style="margin-top:6px; font-size:0.78rem; font-weight:bold; color:#38bdf8;">
            المتبقي: <span id="lblEditPtDebt" style="color:#ef4444; font-size:0.9rem;">0</span> د.ع
          </div>
        </div>

        <input type="text" id="editPtHealth" placeholder="الحساسية للأدوية" class="input-box" style="border-color:#ef4444;">
        
        <div>
          <label style="font-size:0.8rem; font-weight:bold; color:var(--accent-blue);">ملاحظات الطبيب:</label>
          <textarea id="editPtDocNotes" class="input-box" style="width:100%; height:60px; margin-top:4px;"></textarea>
        </div>

        <button type="submit" class="btn-action btn-emerald" style="justify-content:center;">حفظ التعديلات</button>
      </form>
    </div>
  </div>

  <!-- ================= نافذة حجز موعد ================= -->
  <div class="modal-overlay" id="newAppModal">
    <div class="modal-card">
      <div class="modal-head">
        <span>تحديد موعد حجز</span>
        <button style="background:none; border:none; color:white; font-size:1.5rem; cursor:pointer;" onclick="closeModal('newAppModal')">&times;</button>
      </div>
      <form onsubmit="handleSaveApp(event)" class="modal-body">
        <div>
          <label style="font-size:0.8rem; font-weight:bold;">المراجع:</label>
          <select id="selAppPatient" required class="input-box" style="width:100%; margin-top:4px;"></select>
        </div>

        <div>
          <label style="font-size:0.8rem; font-weight:bold; color:var(--primary);">الطبيب المعالج:</label>
          <select id="selAppDoctor" required class="input-box" style="width:100%; margin-top:4px;"></select>
        </div>

        <div style="display:flex; gap:8px;">
          <input type="date" id="inpAppDate" required class="input-box" style="flex:1;">
          <input type="time" id="inpAppTime" required class="input-box" style="flex:1;">
        </div>
        <input type="text" id="inpAppProc" placeholder="نوع الإجراء (جلسة عصب / حشوة / كشف...)" class="input-box">
        <button type="submit" class="btn-action btn-emerald" style="justify-content:center;">تأكيد الموعد</button>
      </form>
    </div>
  </div>

  <!-- ================= نافذة الأدوية، فحص الحساسية، والأشعة ================= -->
  <div class="modal-overlay" id="medsModal">
    <div class="modal-card">
      <div class="modal-head">
        <span>الوصفة الطبية: <strong id="lblMedPatient" style="color:var(--accent-blue);"></strong></span>
        <button style="background:none; border:none; color:white; font-size:1.5rem; cursor:pointer;" onclick="closeModal('medsModal')">&times;</button>
      </div>
      <div class="modal-body">
        <div id="allergyAlertBanner" class="allergy-alert-banner">
          <span>⚠️ تحذير: هذا الدواء يتعارض مع حساسية المريض المسجلة!</span>
        </div>

        <div style="border-bottom:1px solid var(--card-border); padding-bottom:10px;">
          <h4 style="font-size:0.82rem; margin-bottom:4px; color:var(--primary);">➕ كتابة دواء للروشتة (℞):</h4>
          <div style="display:flex; gap:6px;">
            <input type="text" id="inpMedName" oninput="checkDrugAllergyLive()" placeholder="اسم الدواء (مثل: Amoxicillin)" class="input-box" style="flex:1;">
            <input type="text" id="inpMedDose" placeholder="الجرعة" class="input-box" style="flex:1;">
            <button class="btn-action btn-emerald" onclick="addMedication()">إضافة</button>
          </div>
          <div id="patientMedsList" style="margin-top:6px; font-size:0.8rem; display:flex; flex-direction:column; gap:4px;"></div>
        </div>

        <div>
          <h4 style="font-size:0.82rem; margin-bottom:4px; color:var(--accent-gold);">📷 إرفاق صورة الأشعة:</h4>
          <input type="file" id="inpXrayFile" accept="image/*" class="input-box" onchange="handleXrayUpload(event)">
          <div id="patientXrayPreview" style="margin-top:6px;"></div>
        </div>

        <button class="btn-action btn-emerald" style="justify-content:center;" onclick="printMasterReportForCurrent()">🖨️ طباعة التقرير الشامل</button>
      </div>
    </div>
  </div>

  <!-- ================= ورقة الطباعة الشاملة والروشتة A4 ================= -->
  <div id="printableMasterSheet">
    <div style="display:flex; justify-content:space-between; align-items:center; border-bottom:3px solid #00b48a; padding-bottom:12px; margin-bottom:14px;">
      <div style="display:flex; align-items:center; gap:10px;">
        <div style="width:60px; height:60px; border-radius:50%; border:2px solid #00b48a; overflow:hidden;">
          <svg viewBox="0 0 200 200" style="width:100%; height:100%;">
            <circle cx="100" cy="100" r="98" fill="#ffffff"/>
            <path d="M40 70 C30 30 75 15 100 35 C125 15 170 30 160 70 C155 100 145 130 135 150 C125 130 115 125 100 125 C85 125 75 130 65 150 C55 130 45 100 40 70 Z" fill="#29a8eb"/>
            <circle cx="100" cy="110" r="50" fill="#0f3458"/>
            <path d="M75 112 C75 92 86 80 100 80 C114 80 125 92 125 112 C125 132 114 148 100 148 C86 148 75 132 75 112 Z" fill="#ffffff"/>
            <ellipse cx="91" cy="108" rx="4" ry="5" fill="#0f3458"/>
            <ellipse cx="109" cy="108" rx="4" ry="5" fill="#0f3458"/>
            <path d="M88 126 Q100 138 112 126 Q100 132 88 126 Z" fill="#0f3458"/>
          </svg>
        </div>
        <div>
          <h1 style="font-size:1.35rem; font-weight:900; color:#008f6f; margin-bottom:2px;">عيادة المصارف</h1>
          <p style="font-size:0.82rem; color:#475569; font-weight:bold;">الدكتور حذيفة الحمداني - طب وجراحة وتجميل الأسنان</p>
        </div>
      </div>
      <div style="text-align:left; font-size:0.78rem; color:#334155; line-height:1.4;">
        <p><strong>تاريخ التسجيل:</strong> <span id="prtEntryDate">--</span></p>
        <p><strong>موعد الحجز:</strong> <span id="prtAppDate">--</span></p>
        <p><strong>الطبيب المشرف:</strong> <span id="prtDoctorName">د. حذيفة الحمداني</span></p>
      </div>
    </div>

    <div style="background:#f8fafc; border:1px solid #cbd5e1; border-radius:8px; padding:10px 14px; margin-bottom:12px; display:grid; grid-template-columns:repeat(3, 1fr); gap:8px; font-size:0.82rem;">
      <div><strong>اسم المراجع:</strong> <span id="prtName">--</span></div>
      <div><strong>العمر:</strong> <span id="prtAge">--</span></div>
      <div><strong>رقم الهاتف:</strong> <span id="prtPhone">--</span></div>
      <div><strong>السكن:</strong> <span id="prtAddress">--</span></div>
      <div style="grid-column:span 2; color:#b91c1c;"><strong>الحساسية الدوائية:</strong> <span id="prtHealth">سليم</span></div>
    </div>

    <div style="border:1px solid #cbd5e1; border-radius:10px; padding:12px; margin-bottom:12px; text-align:center;">
      <h3 style="font-size:0.9rem; color:#0f766e; margin-bottom:6px;">مخطط الفكين والإجراءات السريرية والجلسات المنجزة</h3>
      <div id="prtJawClone" style="max-height:240px; overflow:hidden;"></div>
    </div>

    <div style="display:grid; grid-template-columns: 1fr 1fr; gap:12px; margin-bottom:14px;">
      <div style="border:1px solid #cbd5e1; border-radius:8px; padding:10px;">
        <h4 style="font-size:0.82rem; color:#0f766e; margin-bottom:4px; border-bottom:1px solid #e2e8f0; padding-bottom:3px;">سجل المعالجات والجلسات:</h4>
        <div id="prtTeethList" style="font-size:0.78rem; display:flex; flex-direction:column; gap:3px;"></div>
        <div style="margin-top:8px; border-top:1px dashed #cbd5e1; padding-top:4px;">
          <h4 style="font-size:0.78rem; color:#0f766e; margin-bottom:2px;">ملاحظات الطبيب:</h4>
          <p id="prtDocNotes" style="font-size:0.76rem; color:#334155; white-space:pre-wrap;">لا توجد ملاحظات.</p>
        </div>
      </div>

      <div style="border:1px solid #cbd5e1; border-radius:8px; padding:10px;">
        <h4 style="font-size:0.9rem; font-family:serif; font-weight:900; color:#0f766e; margin-bottom:4px; border-bottom:1px solid #e2e8f0; padding-bottom:3px;">الوصفة الطبية (℞):</h4>
        <div id="prtMedsList" style="font-size:0.78rem; display:flex; flex-direction:column; gap:3px; min-height:50px;"></div>
        <div id="prtXrayBox" style="margin-top:8px; border-top:1px dashed #cbd5e1; padding-top:4px; display:none;">
          <strong style="font-size:0.72rem; color:#475569; display:block; margin-bottom:2px;">صورة الأشعة:</strong>
          <img id="prtXrayImg" src="" style="max-height:80px; border-radius:4px; border:1px solid #cbd5e1;">
        </div>
      </div>
    </div>

    <div style="display:flex; justify-content:space-between; align-items:center; border-top:1px solid #cbd5e1; padding-top:10px; font-size:0.8rem; margin-top:16px;">
      <div><strong>توقيع الدكتور حذيفة الحمداني:</strong> ________________________</div>
      <div><strong>ختم عيادة المصارف:</strong> ________________________</div>
    </div>
  </div>

  <!-- ================= المنطق البرمجي ================= -->
  <script>
    const SafeStorage = {
      get: function(key, fallback) {
        try {
          const val = localStorage.getItem(key);
          return val ? JSON.parse(val) : fallback;
        } catch(e) { return fallback; }
      },
      set: function(key, val) {
        try { localStorage.setItem(key, JSON.stringify(val)); } catch(e) {}
      }
    };

    function renderToothSvg3D(toothNum, isUpper) {
      const isMolar = [18,17,16,26,27,28,48,47,46,36,37,38].includes(Number(toothNum));
      if (isUpper) {
        if (isMolar) {
          return `
            <svg viewBox="0 0 50 100" style="width:100%; height:100%;">
              <path class="root-3d" d="M12,45 C8,25 6,10 10,2 C13,10 18,25 20,45 Z" fill="url(#rootNormalGrad)" stroke="#475569" stroke-width="1.2"/>
              <path class="root-3d" d="M22,45 C24,20 25,5 26,1 C28,5 29,20 30,45 Z" fill="url(#rootNormalGrad)" stroke="#475569" stroke-width="1.2"/>
              <path class="root-3d" d="M32,45 C35,25 40,10 42,2 C45,10 44,25 38,45 Z" fill="url(#rootNormalGrad)" stroke="#475569" stroke-width="1.2"/>
              <path class="crown-3d" d="M6,45 C4,65 5,85 15,92 C25,95 30,95 38,92 C46,85 47,65 44,45 Z" fill="url(#toothNormalGrad)" stroke="#334155" stroke-width="1.5"/>
            </svg>`;
        } else {
          return `
            <svg viewBox="0 0 35 100" style="width:100%; height:100%;">
              <path class="root-3d" d="M10,40 C14,18 16,5 17.5,1 C19,5 21,18 25,40 Z" fill="url(#rootNormalGrad)" stroke="#475569" stroke-width="1.2"/>
              <path class="crown-3d" d="M5,40 C4,60 7,85 17.5,90 C28,85 31,60 30,40 Z" fill="url(#toothNormalGrad)" stroke="#334155" stroke-width="1.5"/>
            </svg>`;
        }
      } else {
        if (isMolar) {
          return `
            <svg viewBox="0 0 50 100" style="width:100%; height:100%;">
              <path class="crown-3d" d="M6,55 C4,35 5,15 15,8 C25,5 30,5 38,8 C46,15 47,35 44,55 Z" fill="url(#toothNormalGrad)" stroke="#334155" stroke-width="1.5"/>
              <path class="root-3d" d="M12,55 C9,75 8,90 12,98 C15,90 19,75 22,55 Z" fill="url(#rootNormalGrad)" stroke="#475569" stroke-width="1.2"/>
              <path class="root-3d" d="M28,55 C32,75 35,90 38,98 C42,90 41,75 38,55 Z" fill="url(#rootNormalGrad)" stroke="#475569" stroke-width="1.2"/>
            </svg>`;
        } else {
          return `
            <svg viewBox="0 0 35 100" style="width:100%; height:100%;">
              <path class="crown-3d" d="M5,60 C4,40 7,15 17.5,10 C28,15 31,40 30,60 Z" fill="url(#toothNormalGrad)" stroke="#334155" stroke-width="1.5"/>
              <path class="root-3d" d="M10,60 C14,82 16,95 17.5,99 C19,95 21,82 25,60 Z" fill="url(#rootNormalGrad)" stroke="#475569" stroke-width="1.2"/>
            </svg>`;
        }
      }
    }

    const AppData = {
      doctors: SafeStorage.get('masarif_clinic_docs', [
        { id: "D_1", name: "د. حذيفة الحمداني", specialty: "طب وجراحة وتجميل الأسنان (المدير)" },
        { id: "D_2", name: "د. أحمد يوسف", specialty: "أخصائي حشوات الجذور والأعصاب" },
        { id: "D_3", name: "د. مصطفى العلي", specialty: "أخصائي جراحة الفم وزراعة الأسنان" },
        { id: "D_4", name: "د. زينب النعيمي", specialty: "أخصائية تقويم وتعديل الأسنان" }
      ]),
      patients: SafeStorage.get('masarif_clinic_pts', [
        {
          id: "P_1",
          name: "قاسم حافظ",
          phone: "07707992444",
          age: 29,
          address: "الموصل - حي المصارف",
          healthAlert: "حساسية بنسلين",
          docNotes: "المراجع يراجع لدى د. حذيفة الحمداني، يعاني من حساسية البنسلين، تم البدء بجلسة سحب عصب للسن 16.",
          entryDate: "2026-09-20",
          appointmentDate: "2026-10-02 (05:00 م)",
          doctorName: "د. حذيفة الحمداني",
          totalCost: 100000,
          paidAmount: 50000,
          debt: 50000,
          payments: [{ id: 1, amount: 50000, type: "cash", date: "2026-09-10" }],
          teeth: {
            16: { status: "endo", note: "حشوة جذر", session: "الجلسة الأولى", measurements: "MB: 21.5mm | ML: 21.0mm | DB: 20.5mm" },
            18: { status: "extract", note: "قلع سن العقل", session: "جلسة إنهاء العلاج", measurements: "" },
            21: { status: "filling", note: "حشوة بيضاء", session: "الجلسة الأولى", measurements: "" }
          },
          meds: [
            { name: "Erythromycin 500mg", dose: "كبسولة كل 8 ساعات بعد الأكل (بديل آمن للبنسلين)" },
            { name: "Paracetamol 500mg", dose: "قرص عند اللزوم لتسكين الألم" }
          ],
          xray: ""
        }
      ]),
      appointments: [
        { id: "A_1", patientName: "قاسم حافظ", time: "17:00", date: "2026-10-02", doctor: "د. حذيفة الحمداني", proc: "إكمال جلسة العصب للسن 16" }
      ],
      currentPatientId: "P_1",
      activeTooth: null,
      isFinancePrivate: false
    };

    function persist() {
      SafeStorage.set('masarif_clinic_pts', AppData.patients);
      SafeStorage.set('masarif_clinic_docs', AppData.doctors);
    }

    window.addEventListener('DOMContentLoaded', () => {
      document.getElementById('appointmentDateFilter').value = new Date().toISOString().split('T')[0];
      build3DArches();
      syncDoctorDropdowns();
      renderPatientsCards(AppData.patients);
      renderAppointments();
      renderFinance();
      renderWhatsappList();
      renderStaffList();
      bindPatientToJaw("P_1");
    });

    function normalizeDigits(str) {
      return str.replace(/[٠-٩]/g, d => d.charCodeAt(0) - 1632).trim();
    }

    function handleDoctorPinSubmit(e) {
      if (e) e.preventDefault();
      const rawPin = document.getElementById('docPinInput').value;
      const cleanPin = normalizeDigits(rawPin);
      const err = document.getElementById('pinErrorMsg');

      if (cleanPin === "1992") {
        err.style.display = 'none';
        unlockClinic('doctor');
      } else {
        err.style.display = 'block';
      }
    }

    function unlockClinic(role) {
      document.getElementById('currentRoleBadge').innerText = role === 'doctor' ? 'المدير: د. حذيفة الحمداني' : 'الاستقبال والسكرتارية';
      const gate = document.getElementById('loginGateOverlay');
      gate.style.pointerEvents = 'none';
      gate.style.opacity = '0';
      setTimeout(() => { gate.style.display = 'none'; }, 300);
    }

    function switchView(tabId, el) {
      document.querySelectorAll('.page-tab').forEach(p => p.classList.remove('active'));
      document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
      document.getElementById(tabId).classList.add('active');
      if (el) el.classList.add('active');
    }

    function renderStaffList() {
      const wrap = document.getElementById('staffListWrapper');
      wrap.innerHTML = '';
      AppData.doctors.forEach((doc, idx) => {
        const card = document.createElement('div');
        card.style.cssText = "background:var(--card-bg); border:1px solid var(--card-border); padding:12px; border-radius:12px; display:flex; justify-content:space-between; align-items:center;";
        card.innerHTML = `
          <div>
            <h4 style="color:white; font-size:0.9rem;">👨‍⚕️ ${doc.name}</h4>
            <p style="color:var(--accent-blue); font-size:0.72rem;">${doc.specialty}</p>
          </div>
          ${idx > 0 ? `<button style="background:none; border:none; color:#ef4444; font-size:1.1rem; cursor:pointer;" onclick="deleteDoctor('${doc.id}')">🗑️</button>` : '<span style="font-size:0.68rem; color:var(--primary); font-weight:bold;">المدير</span>'}
        `;
        wrap.appendChild(card);
      });
    }

    function syncDoctorDropdowns() {
      const selects = [document.getElementById('newPtDoctor'), document.getElementById('editPtDoctor'), document.getElementById('selAppDoctor')];
      selects.forEach(sel => {
        if (!sel) return;
        sel.innerHTML = '';
        AppData.doctors.forEach(d => {
          sel.innerHTML += `<option value="${d.name}">${d.name} (${d.specialty})</option>`;
        });
      });
    }

    function handleSaveNewDoctor(e) {
      e.preventDefault();
      if (AppData.doctors.length >= 10) {
        alert("تم الوصول للحد الأقصى (10 أطباء).");
        return;
      }
      const name = document.getElementById('inpDocName').value.trim();
      const spec = document.getElementById('inpDocSpecialty').value.trim();
      AppData.doctors.push({ id: "D_" + Date.now(), name: name, specialty: spec });
      persist();
      syncDoctorDropdowns();
      renderStaffList();
      closeModal('newDoctorModal');
      e.target.reset();
    }

    function deleteDoctor(id) {
      if (confirm("هل ترغب بحذف هذا الطبيب من الكادر؟")) {
        AppData.doctors = AppData.doctors.filter(d => d.id !== id);
        persist();
        syncDoctorDropdowns();
        renderStaffList();
      }
    }

    function build3DArches() {
      const up = document.getElementById('upperArch');
      const low = document.getElementById('lowerArch');
      up.innerHTML = '';
      low.innerHTML = '';

      const upperTeeth = [18,17,16,15,14,13,12,11, 21,22,23,24,25,26,27,28];
      const lowerTeeth = [48,47,46,45,44,43,42,41, 31,32,33,34,35,36,37,38];

      upperTeeth.forEach(n => up.appendChild(createToothNode(n, true)));
      lowerTeeth.forEach(n => low.appendChild(createToothNode(n, false)));
    }

    function createToothNode(num, isUpper) {
      const div = document.createElement('div');
      div.className = 'tooth-3d';
      div.id = `t3d_${num}`;
      div.innerHTML = `<div class="tooth-number">${num}</div>${renderToothSvg3D(num, isUpper)}`;
      div.onclick = () => onToothClick(num);
      return div;
    }

    function bindPatientToJaw(pId) {
      AppData.currentPatientId = pId;
      const p = AppData.patients.find(x => x.id === pId);
      if (!p) return;

      document.getElementById('chartPatientTitle').innerText = `${p.name} (${p.phone})`;

      document.querySelectorAll('.tooth-3d').forEach(node => {
        node.className = 'tooth-3d';
        const tag = node.querySelector('.bubble-tag-3d');
        if (tag) tag.remove();
      });

      if (p.teeth) {
        Object.keys(p.teeth).forEach(n => {
          const t = p.teeth[n];
          const node = document.getElementById(`t3d_${n}`);
          if (node) {
            if (t.status === 'endo') node.classList.add('is-endo');
            if (t.status === 'filling') node.classList.add('is-filling');
            if (t.status === 'crown') node.classList.add('is-crown');
            if (t.status === 'extract') node.classList.add('is-extract');

            if (t.note) {
              const isUp = [18,17,16,15,14,13,12,11,21,22,23,24,25,26,27,28].includes(Number(n));
              const bubble = document.createElement('div');
              bubble.className = `bubble-tag-3d ${isUp ? 'up' : 'down'}`;
              const sessionInfo = t.session ? ` [${t.session}]` : '';
              bubble.innerText = `${t.note}${sessionInfo}`;
              node.appendChild(bubble);
            }
          }
        });
      }
    }

    function onToothClick(num) {
      document.querySelectorAll('.tooth-3d').forEach(el => el.classList.remove('active-selected'));
      const activeEl = document.getElementById(`t3d_${num}`);
      if (activeEl) activeEl.classList.add('active-selected');

      AppData.activeTooth = num;
      document.getElementById('lblToothNum').innerText = num;
      const p = AppData.patients.find(x => x.id === AppData.currentPatientId);
      const toothData = (p.teeth && p.teeth[num]) ? p.teeth[num] : {};

      document.getElementById('toothBubbleInput').value = toothData.note || '';
      if (toothData.session) document.getElementById('toothSessionSelect').value = toothData.session;

      openModal('toothActionModal');
      toggleMeasurementFields();
    }

    function toggleMeasurementFields() {
      const op = document.getElementById('toothOpSelect').value;
      document.getElementById('endoMeasureBox').style.display = op.includes('جذر') ? 'block' : 'none';
      document.getElementById('implantMeasureBox').style.display = op.includes('زراعة') ? 'block' : 'none';
      document.getElementById('orthoMeasureBox').style.display = op.includes('تقويم') ? 'block' : 'none';
    }

    function applyToothChanges() {
      const p = AppData.patients.find(x => x.id === AppData.currentPatientId);
      const num = AppData.activeTooth;
      const op = document.getElementById('toothOpSelect').value;
      const session = document.getElementById('toothSessionSelect').value;
      const bubble = document.getElementById('toothBubbleInput').value;

      let measures = "";
      if (op.includes('جذر')) {
        measures = `أطوال الأقنية: MB=${document.getElementById('inpCanal1').value || '-'}, ML=${document.getElementById('inpCanal2').value || '-'}, DB=${document.getElementById('inpCanal3').value || '-'}`;
      } else if (op.includes('زراعة')) {
        measures = `أبعاد الغرسة: طول=${document.getElementById('inpImpLength').value || '-'}, قطر=${document.getElementById('inpImpDia').value || '-'}, عزم=${document.getElementById('inpImpTorque').value || '-'}`;
      } else if (op.includes('تقويم')) {
        measures = `قياسات التقويم: Overjet=${document.getElementById('inpOrthoOverjet').value || '-'}, سلك=${document.getElementById('inpOrthoWire').value || '-'}`;
      }

      if (!p.teeth) p.teeth = {};
      let stat = 'normal';
      if (op.includes('عصب') || op.includes('جذر')) stat = 'endo';
      else if (op.includes('بيضاء') || op.includes('حشوة')) stat = 'filling';
      else if (op.includes('تغليف') || op.includes('تاج')) stat = 'crown';
      else if (op.includes('قلع')) stat = 'extract';

      p.teeth[num] = { status: stat, note: bubble || op, session: session, measurements: measures };
      persist();
      bindPatientToJaw(p.id);
      closeModal('toothActionModal');
    }

    function setChartColor(type) {
      if (!AppData.activeTooth) return;
      const p = AppData.patients.find(x => x.id === AppData.currentPatientId);
      if (!p.teeth) p.teeth = {};
      p.teeth[AppData.activeTooth] = { status: type, note: '', session: 'الجلسة الأولى', measurements: '' };
      persist();
      bindPatientToJaw(p.id);
    }

    function renderPatientsCards(list) {
      const wrap = document.getElementById('patientsContainer');
      wrap.innerHTML = '';
      list.forEach(p => {
        const card = document.createElement('div');
        card.className = 'patient-card';
        const cost = p.totalCost || 0;
        const paid = p.paidAmount || 0;
        const debt = (p.debt !== undefined) ? p.debt : Math.max(0, cost - paid);

        card.innerHTML = `
          <div class="pt-top">
            <div style="display:flex; gap:8px; align-items:center;">
              <div class="pt-avatar">👤</div>
              <div class="pt-info">
                <h3>${p.name}</h3>
                <p>📞 ${p.phone} | ${p.age} سنة | ${p.address || ''}</p>
              </div>
            </div>
            <div class="pt-dates-badge">${p.entryDate || 'تلقائي'}</div>
          </div>

          <div class="pt-finance-bar">
            <span>التكلفة: <strong>${cost.toLocaleString()}</strong></span>
            <span>المدفوع: <strong>${paid.toLocaleString()}</strong></span>
            <span class="${debt > 0 ? 'pt-debt-alert' : ''}">المتبقي: ${debt.toLocaleString()} د.ع</span>
          </div>

          ${p.healthAlert ? `<div style="color:#ef4444; font-size:0.72rem; font-weight:bold;">⚠️ تنبيه الحساسية: ${p.healthAlert}</div>` : ''}
          <div style="font-size:0.72rem; color:#94a3b8;">📅 موعد الحجز: <strong style="color:#38bdf8;">${p.appointmentDate || 'لم يحدد'}</strong> | الطبيب: <span style="color:#00b48a;">${p.doctorName || 'د. حذيفة الحمداني'}</span></div>
          
          <div class="pt-actions">
            <button class="btn-pt-action" onclick="openEditPatientModal('${p.id}')">✏️ تعديل</button>
            <button class="btn-pt-action" onclick="openJawForPatient('${p.id}')">🦷 الفكين</button>
            <button class="btn-pt-action" onclick="openMedsModal('${p.id}')">💊 الأدوية</button>
            <button class="btn-pt-action" style="background:#00b48a; color:#030811; font-weight:900;" onclick="printMasterReport('${p.id}')">🖨️ طباعة</button>
          </div>
        `;
        wrap.appendChild(card);
      });
    }

    function openJawForPatient(pId) {
      bindPatientToJaw(pId);
      switchView('tabJaws', document.querySelectorAll('.nav-btn')[1]);
    }

    function filterPatientsList() {
      const q = document.getElementById('patientSearchBox').value.toLowerCase().trim();
      const filtered = AppData.patients.filter(p => p.name.toLowerCase().includes(q) || p.phone.includes(q));
      renderPatientsCards(filtered);
    }

    function recalcNewPatientDebt() {
      const cost = Number(document.getElementById('newPtCost').value) || 0;
      const paid = Number(document.getElementById('newPtPaid').value) || 0;
      const debt = Math.max(0, cost - paid);
      document.getElementById('lblNewPtDebt').innerText = debt.toLocaleString();
    }

    function handleSavePatient(e) {
      e.preventDefault();
      const now = new Date();
      const cost = Number(document.getElementById('newPtCost').value) || 0;
      const paid = Number(document.getElementById('newPtPaid').value) || 0;
      const debt = Math.max(0, cost - paid);

      const p = {
        id: "P_" + Date.now(),
        name: document.getElementById('newPtName').value,
        phone: document.getElementById('newPtPhone').value,
        age: document.getElementById('newPtAge').value,
        address: document.getElementById('newPtAddress').value,
        doctorName: document.getElementById('newPtDoctor').value,
        totalCost: cost,
        paidAmount: paid,
        debt: debt,
        healthAlert: document.getElementById('newPtHealth').value,
        docNotes: document.getElementById('newPtDocNotes').value,
        entryDate: now.toLocaleDateString('ar-EG'),
        appointmentDate: "قيد التحديد",
        payments: paid > 0 ? [{ id: Date.now(), amount: paid, type: "cash", date: now.toISOString().split('T')[0] }] : [],
        teeth: {},
        meds: [],
        xray: ""
      };

      AppData.patients.unshift(p);
      persist();
      renderPatientsCards(AppData.patients);
      renderFinance();
      closeModal('newPatientModal');
      e.target.reset();
    }

    function openEditPatientModal(pId) {
      const p = AppData.patients.find(x => x.id === pId);
      if (!p) return;

      document.getElementById('editPtId').value = p.id;
      document.getElementById('lblEditPtTitle').innerText = p.name;
      document.getElementById('editPtName').value = p.name;
      document.getElementById('editPtAge').value = p.age;
      document.getElementById('editPtPhone').value = p.phone;
      document.getElementById('editPtAddress').value = p.address || '';
      document.getElementById('editPtDoctor').value = p.doctorName || 'د. حذيفة الحمداني';
      document.getElementById('editPtCost').value = p.totalCost || 0;
      document.getElementById('editPtPaid').value = p.paidAmount || 0;
      document.getElementById('editPtHealth').value = p.healthAlert || '';
      document.getElementById('editPtDocNotes').value = p.docNotes || '';

      recalcEditPatientDebt();
      openModal('editPatientModal');
    }

    function recalcEditPatientDebt() {
      const cost = Number(document.getElementById('editPtCost').value) || 0;
      const paid = Number(document.getElementById('editPtPaid').value) || 0;
      const debt = Math.max(0, cost - paid);
      document.getElementById('lblEditPtDebt').innerText = debt.toLocaleString();
    }

    function handleUpdatePatient(e) {
      e.preventDefault();
      const pId = document.getElementById('editPtId').value;
      const p = AppData.patients.find(x => x.id === pId);
      if (!p) return;

      const cost = Number(document.getElementById('editPtCost').value) || 0;
      const paid = Number(document.getElementById('editPtPaid').value) || 0;

      p.name = document.getElementById('editPtName').value;
      p.age = document.getElementById('editPtAge').value;
      p.phone = document.getElementById('editPtPhone').value;
      p.address = document.getElementById('editPtAddress').value;
      p.doctorName = document.getElementById('editPtDoctor').value;
      p.totalCost = cost;
      p.paidAmount = paid;
      p.debt = Math.max(0, cost - paid);
      p.healthAlert = document.getElementById('editPtHealth').value;
      p.docNotes = document.getElementById('editPtDocNotes').value;

      persist();
      renderPatientsCards(AppData.patients);
      renderFinance();
      closeModal('editPatientModal');
    }

    function checkDrugAllergyLive() {
      const p = AppData.patients.find(x => x.id === AppData.currentPatientId);
      const drugInput = document.getElementById('inpMedName').value.trim().toLowerCase();
      const alertBanner = document.getElementById('allergyAlertBanner');

      if (!p || !p.healthAlert) {
        alertBanner.style.display = 'none';
        return;
      }

      const alertText = p.healthAlert.toLowerCase();
      const penicillinDerivatives = ['بنسلين', 'بنسيلين', 'penicillin', 'amoxicillin', 'اموكسيسيلين', 'أموكسيسيلين', 'augmentin', 'اوجمنتين', 'أوجمنتين', 'ampicillin', 'امبيسيلين', 'كلافوكس', 'klavox'];
      const nsaidDerivatives = ['بروفين', 'brufen', 'ibuprofen', 'ايبوبروفين', 'اسبرين', 'أسبرين', 'aspirin', 'فولتارين', 'voltaren', 'diclofenac'];
      const sulfaDerivatives = ['سلفا', 'sulfa', 'bactrim', 'باكتريم', 'septrin'];

      let isDangerous = false;
      if (alertText.includes('بنسلين') || alertText.includes('penicillin')) {
        if (penicillinDerivatives.some(d => drugInput.includes(d))) isDangerous = true;
      }
      if (alertText.includes('بروفين') || alertText.includes('اسبرين') || alertText.includes('aspirin')) {
        if (nsaidDerivatives.some(d => drugInput.includes(d))) isDangerous = true;
      }
      if (alertText.includes('سلفا') || alertText.includes('sulfa')) {
        if (sulfaDerivatives.some(d => drugInput.includes(d))) isDangerous = true;
      }

      alertBanner.style.display = isDangerous ? 'flex' : 'none';
    }

    function openMedsModal(pId) {
      AppData.currentPatientId = pId;
      const p = AppData.patients.find(x => x.id === pId);
      document.getElementById('lblMedPatient').innerText = p.name;
      document.getElementById('allergyAlertBanner').style.display = 'none';
      renderPatientMeds(p);
      openModal('medsModal');
    }

    function addMedication() {
      const p = AppData.patients.find(x => x.id === AppData.currentPatientId);
      const name = document.getElementById('inpMedName').value.trim();
      const dose = document.getElementById('inpMedDose').value.trim();
      if (!name) return;

      if (!p.meds) p.meds = [];
      p.meds.push({ name, dose });
      persist();
      renderPatientMeds(p);
      document.getElementById('inpMedName').value = '';
      document.getElementById('inpMedDose').value = '';
      document.getElementById('allergyAlertBanner').style.display = 'none';
    }

    function renderPatientMeds(p) {
      const wrap = document.getElementById('patientMedsList');
      wrap.innerHTML = '';
      if (!p.meds || p.meds.length === 0) {
        wrap.innerHTML = '<span style="color:#64748b;">لا توجد أدوية مسجلة.</span>';
        return;
      }
      p.meds.forEach((m, i) => {
        wrap.innerHTML += `<div style="display:flex; justify-content:space-between; background:#07121f; padding:5px 8px; border-radius:6px;"><span>${i+1}. <strong>${m.name}</strong></span><span style="color:#38bdf8;">${m.dose}</span></div>`;
      });
    }

    function handleXrayUpload(e) {
      const file = e.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(evt) {
        const p = AppData.patients.find(x => x.id === AppData.currentPatientId);
        p.xray = evt.target.result;
        persist();
        document.getElementById('patientXrayPreview').innerHTML = `<img src="${p.xray}" style="max-height:80px; border-radius:6px;">`;
      };
      reader.readAsDataURL(file);
    }

    function printMasterReportForCurrent() {
      printMasterReport(AppData.currentPatientId);
    }

    function printMasterReport(pId) {
      const p = AppData.patients.find(x => x.id === pId);
      if (!p) return;

      document.getElementById('prtEntryDate').innerText = p.entryDate || new Date().toLocaleDateString('ar-EG');
      document.getElementById('prtAppDate').innerText = p.appointmentDate || 'لا يوجد حجز محدد';
      document.getElementById('prtDoctorName').innerText = p.doctorName || 'د. حذيفة الحمداني';
      document.getElementById('prtName').innerText = p.name;
      document.getElementById('prtAge').innerText = p.age + " سنة";
      document.getElementById('prtPhone').innerText = p.phone;
      document.getElementById('prtAddress').innerText = p.address || 'الموصل - حي المصارف';
      document.getElementById('prtHealth').innerText = p.healthAlert || 'سليم، لا توجد أمراض أو حساسية';
      document.getElementById('prtDocNotes').innerText = p.docNotes || 'لا توجد ملاحظات إضافية.';

      bindPatientToJaw(p.id);
      const jawClone = document.getElementById('dentalChartBox').cloneNode(true);
      const prtTarget = document.getElementById('prtJawClone');
      prtTarget.innerHTML = '';
      prtTarget.appendChild(jawClone);

      const teethListWrap = document.getElementById('prtTeethList');
      teethListWrap.innerHTML = '';
      if (p.teeth && Object.keys(p.teeth).length > 0) {
        Object.keys(p.teeth).forEach(n => {
          const t = p.teeth[n];
          let extra = t.measurements ? ` [${t.measurements}]` : '';
          let sess = t.session ? ` - (${t.session})` : '';
          teethListWrap.innerHTML += `<div>• السن <strong>${n}</strong>: ${t.note || t.status}${sess}${extra}</div>`;
        });
      } else {
        teethListWrap.innerHTML = '<div>• لم تسجل أي معالجات بعد.</div>';
      }

      const medsListWrap = document.getElementById('prtMedsList');
      medsListWrap.innerHTML = '';
      if (p.meds && p.meds.length > 0) {
        p.meds.forEach((m, idx) => {
          medsListWrap.innerHTML += `<div><strong>${idx+1}. ${m.name}</strong> - ${m.dose}</div>`;
        });
      } else {
        medsListWrap.innerHTML = '<div>• لا توجد أدوية مقررة.</div>';
      }

      const xrayBox = document.getElementById('prtXrayBox');
      const xrayImg = document.getElementById('prtXrayImg');
      if (p.xray) {
        xrayBox.style.display = 'block';
        xrayImg.src = p.xray;
      } else {
        xrayBox.style.display = 'none';
      }

      window.print();
    }

    function renderAppointments() {
      const d = document.getElementById('appointmentDateFilter').value;
      const wrap = document.getElementById('appointmentsList');
      wrap.innerHTML = '';
      const matched = AppData.appointments.filter(a => a.date === d);

      if (matched.length === 0) {
        wrap.innerHTML = `<div style="text-align:center; padding:20px; color:var(--text-dim);">لا توجد مواعيد مسجلة في تاريخ: ${d}</div>`;
        return;
      }

      matched.sort((a,b) => a.time.localeCompare(b.time)).forEach(a => {
        const row = document.createElement('div');
        row.style.cssText = "display:flex; justify-content:space-between; align-items:center; background:var(--card-bg); padding:10px 14px; border-radius:10px; border:1px solid var(--card-border);";
        row.innerHTML = `
          <div style="display:flex; align-items:center; gap:10px;">
            <span style="background:var(--primary); color:#04141d; padding:3px 8px; border-radius:6px; font-weight:900; font-size:0.75rem;">${a.time}</span>
            <div>
              <strong style="color:white; font-size:0.85rem;">${a.patientName}</strong>
              <div style="font-size:0.72rem; color:var(--text-dim);">${a.proc || 'معاينة'} | الطبيب: <span style="color:#00b48a;">${a.doctor || 'د. حذيفة'}</span></div>
            </div>
          </div>
          <button style="border:none; background:none; color:#ef4444; font-size:1.1rem; cursor:pointer;" onclick="deleteAppointment('${a.id}')">🗑️</button>
        `;
        wrap.appendChild(row);
      });
    }

    function openNewAppModal() {
      const sel = document.getElementById('selAppPatient');
      sel.innerHTML = '<option value="">اختر المراجع من القائمة...</option>';
      AppData.patients.forEach(p => {
        sel.innerHTML += `<option value="${p.id}">${p.name} (${p.phone})</option>`;
      });
      document.getElementById('inpAppDate').value = new Date().toISOString().split('T')[0];
      openModal('newAppModal');
    }

    function handleSaveApp(e) {
      e.preventDefault();
      const pId = document.getElementById('selAppPatient').value;
      const p = AppData.patients.find(x => x.id === pId);
      const appDate = document.getElementById('inpAppDate').value;
      const appTime = document.getElementById('inpAppTime').value;
      const doctor = document.getElementById('selAppDoctor').value;

      AppData.appointments.push({
        id: "A_" + Date.now(),
        patientName: p ? p.name : 'مجهول',
        date: appDate,
        time: appTime,
        doctor: doctor,
        proc: document.getElementById('inpAppProc').value
      });

      if (p) {
        p.appointmentDate = `${appDate} (${appTime})`;
        p.doctorName = doctor;
      }
      persist();
      renderPatientsCards(AppData.patients);
      renderAppointments();
      closeModal('newAppModal');
      e.target.reset();
    }

    function deleteAppointment(id) {
      if (confirm('هل ترغب بحذف هذا الموعد؟')) {
        AppData.appointments = AppData.appointments.filter(a => a.id !== id);
        renderAppointments();
      }
    }

    function speakDailySchedule() {
      if (!('speechSynthesis' in window)) {
        alert("المتصفح لا يدعم القراءة الصوتية.");
        return;
      }
      window.speechSynthesis.cancel();
      const today = new Date().toISOString().split('T')[0];
      const matched = AppData.appointments.filter(a => a.date === today);
      const hour = new Date().getHours();
      const greeting = (hour < 12) ? "صباح الخير دكتور حذيفة" : "مساء الخير دكتور حذيفة";

      let speech = "";
      if (matched.length === 0) {
        speech = `${greeting}. أهلاً بك في عيادة المصارف. جدول مواعيد اليوم فارغ، لا توجد حجوزات حتى الآن. نتمنى لك يوماً سعيداً.`;
      } else {
        speech = `${greeting}. لديك اليوم في عيادة المصارف ${matched.length} مواعيد مجدولة. `;
        matched.forEach((apt, idx) => {
          speech += `الموعد ${idx + 1} في الساعة ${apt.time} للمراجع ${apt.patientName}، مع الطبيب ${apt.doctor || 'المشرف'}. `;
        });
      }

      const utterance = new SpeechSynthesisUtterance(speech);
      utterance.lang = 'ar-SA';
      utterance.rate = 0.92;
      window.speechSynthesis.speak(utterance);
    }

    function toggleFinancialPrivacy() {
      AppData.isFinancePrivate = !AppData.isFinancePrivate;
      const cont = document.getElementById('financeCardsContainer');
      const list = document.getElementById('financeList');
      if (AppData.isFinancePrivate) {
        cont.classList.add('finance-privacy-blur');
        list.classList.add('finance-privacy-blur');
        document.getElementById('togglePrivacyBtn').innerText = '🔒 كشف الأرقام المالية';
      } else {
        cont.classList.remove('finance-privacy-blur');
        list.classList.remove('finance-privacy-blur');
        document.getElementById('togglePrivacyBtn').innerText = '👁️ إخفاء الأرقام المالية';
      }
    }

    function renderFinance() {
      let cash = 0, card = 0, debt = 0;
      const wrap = document.getElementById('financeList');
      wrap.innerHTML = '';

      AppData.patients.forEach(p => {
        debt += (p.debt || 0);
        if (p.payments) {
          p.payments.forEach(pay => {
            if (pay.type === 'cash') cash += pay.amount;
            if (pay.type === 'card') card += pay.amount;

            wrap.innerHTML += `
              <div style="display:flex; justify-content:space-between; align-items:center; background:var(--card-bg); padding:10px 14px; border-radius:10px; border:1px solid var(--card-border);">
                <div>
                  <strong style="color:white; font-size:0.85rem;">${p.name}</strong>
                  <div style="font-size:0.72rem; color:var(--text-dim);">${pay.date} | ${pay.type === 'cash' ? '💵 كاش' : '💳 بطاقة'}</div>
                </div>
                <div style="font-weight:900; color:var(--accent-blue);">${pay.amount.toLocaleString()} د.ع</div>
              </div>
            `;
          });
        }
      });

      document.getElementById('statCash').innerText = cash.toLocaleString() + " د.ع";
      document.getElementById('statCard').innerText = card.toLocaleString() + " د.ع";
      document.getElementById('statDebt').innerText = debt.toLocaleString() + " د.ع";
    }

    function renderWhatsappList() {
      const wrap = document.getElementById('whatsappList');
      wrap.innerHTML = '';
      AppData.patients.forEach(p => {
        const row = document.createElement('div');
        row.style.cssText = "display:flex; justify-content:space-between; align-items:center; background:var(--card-bg); padding:10px 14px; border-radius:10px; border:1px solid var(--card-border); margin-bottom:8px;";
        row.innerHTML = `
          <div>
            <strong style="color:white; font-size:0.85rem;">${p.name}</strong>
            <div style="font-size:0.72rem; color:var(--text-dim);">هاتف: ${p.phone} | الموعد: ${p.appointmentDate || 'لم يحدد'}</div>
          </div>
          <div style="display:flex; gap:6px;">
            <button class="btn-action" style="background:#25D366; color:white; border:none;" onclick="sendWhatsapp('${p.phone}', '${p.name}', 'reminder')">📲 تذكير</button>
            <button class="btn-action" style="background:#0284c7; color:white; border:none;" onclick="sendWhatsapp('${p.phone}', '${p.name}', 'postop')">📋 تعليمات</button>
          </div>
        `;
        wrap.appendChild(row);
      });
    }

    function sendWhatsapp(phone, name, type) {
      const clean = phone.replace(/^0/, '964');
      let msg = type === 'reminder' 
        ? `مرحباً أستاذ ${name}، نود تذكيركم بموعدكم القادم في عيادة المصارف (الدكتور حذيفة الحمداني). نتمنى لكم السلامة.`
        : `مرحباً أستاذ ${name}، نتمنى لكم الشفاء العاجل. نرفق لكم تعليمات ما بعد علاج الأسنان من عيادة المصارف (د. حذيفة الحمداني): تجنب المشروبات الساخنة، واستمر على الأدوية بانتظام.`;
      window.open(`https://wa.me/${clean}?text=${encodeURIComponent(msg)}`, '_blank');
    }

    function exportPatientsCsv() {
      let csv = "\uFEFFالاسم,الهاتف,العمر,السكن,الحالة الصحية,التكلفة,المدفوع,المتبقي,تاريخ التسجيل,موعد الحجز,الطبيب\n";
      AppData.patients.forEach(p => {
        csv += `"${p.name}","${p.phone}","${p.age}","${p.address || ''}","${p.healthAlert || 'سليم'}","${p.totalCost || 0}","${p.paidAmount || 0}","${p.debt || 0}","${p.entryDate || ''}","${p.appointmentDate || ''}"\n`;
      });
      const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = "سجل_مراجعين_عيادة_المصارف_د_حذيفة.csv";
      a.click();
    }

    function openModal(id) { document.getElementById(id).style.display = 'flex'; }
    function closeModal(id) { document.getElementById(id).style.display = 'none'; }
  </script>
</body>
</html>
