<!DOCTYPE html>
<html lang="ur">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Shadi — Shafi Ur Rehman & Ruqyya Khatoon</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Nastaliq+Urdu:wght@400;700&family=Cinzel+Decorative:wght@400;700&family=Cormorant+Garamond:ital,wght@0,400;0,600&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{background:#0d0200;min-height:100vh;font-family:'Cormorant Garamond',serif;overflow-x:hidden;}
@keyframes fadeUp{from{opacity:0;transform:translateY(28px)}to{opacity:1;transform:none}}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-9px)}}
@keyframes shimmer{0%,100%{opacity:.7}50%{opacity:1}}
@keyframes pulse{0%,100%{transform:scale(1)}50%{transform:scale(1.05)}}
@keyframes spin{to{transform:rotate(360deg)}}

/* PAGES */
.pg{display:none;min-height:100vh;flex-direction:column;align-items:center;justify-content:flex-start;padding:24px 14px 50px;animation:fadeUp .7s ease;}
.pg.on{display:flex;}

/* MUSIC */
#mbtn{position:fixed;top:14px;right:14px;z-index:9999;background:linear-gradient(135deg,#b8860b,#8B0000);color:#ffd700;border:2px solid #ffd700;border-radius:50%;width:46px;height:46px;font-size:18px;cursor:pointer;display:flex;align-items:center;justify-content:center;box-shadow:0 0 18px rgba(255,215,0,.3);transition:transform .2s;}
#mbtn:hover{transform:scale(1.1);}

/* ====== WELCOME ====== */
#pg-welcome{background:radial-gradient(ellipse at center,#2a0800 0%,#080100 100%);justify-content:center;text-align:center;padding:30px 20px;}
.welcome-rose{font-size:64px;animation:float 3s ease-in-out infinite;display:block;margin-bottom:12px;}
.w-bism{font-family:'Noto Nastaliq Urdu',serif;font-size:1.1rem;color:#c8a96e;direction:rtl;line-height:2;margin-bottom:10px;}
.w-guest{font-family:'Noto Nastaliq Urdu',serif;font-size:2.4rem;color:#ffd700;direction:rtl;line-height:1.6;text-shadow:0 0 24px rgba(255,215,0,.5);animation:shimmer 2.5s ease-in-out infinite;margin:8px 0 6px;}
.w-invite{font-family:'Noto Nastaliq Urdu',serif;font-size:1.05rem;color:#e8c878;direction:rtl;line-height:1.9;margin-bottom:6px;}
.w-invite-en{font-size:.88rem;color:#c8a96e;font-style:italic;margin-bottom:20px;}
.w-info{font-size:.82rem;color:#a07050;line-height:1.8;margin-bottom:26px;}
.w-info b{color:#c8a96e;}
.enter-btn{background:linear-gradient(135deg,#8B0000,#b8860b,#8B0000);color:#fff8e1;border:2px solid #ffd700;padding:13px 48px;font-family:'Cinzel Decorative',cursive;font-size:.82rem;letter-spacing:2px;border-radius:50px;cursor:pointer;box-shadow:0 4px 20px rgba(184,134,11,.4);transition:all .3s;}
.enter-btn:hover{transform:translateY(-2px);box-shadow:0 8px 30px rgba(255,215,0,.45);}

/* ====== CARD ====== */
#pg-card{background:#080100;}
.card-box{width:100%;max-width:660px;background:linear-gradient(160deg,#1a0600 0%,#2e0d00 45%,#1a0600 100%);border:3px solid #b8860b;border-radius:16px;overflow:hidden;position:relative;box-shadow:0 0 60px rgba(184,134,11,.22),inset 0 0 80px rgba(0,0,0,.4);}
.card-box::before{content:'';position:absolute;inset:8px;border:1px solid rgba(184,134,11,.28);border-radius:10px;pointer-events:none;z-index:1;}
.co{position:absolute;width:76px;height:76px;opacity:.55;z-index:2;}
.co.tl{top:0;left:0}.co.tr{top:0;right:0;transform:scaleX(-1)}.co.bl{bottom:0;left:0;transform:scaleY(-1)}.co.br{bottom:0;right:0;transform:scale(-1,-1)}

.c-head{text-align:center;padding:28px 18px 16px;border-bottom:1px solid rgba(184,134,11,.28);position:relative;z-index:5;}
.c-bism{font-family:'Noto Nastaliq Urdu',serif;font-size:1.5rem;color:#ffd700;direction:rtl;line-height:2;text-shadow:0 0 14px rgba(255,215,0,.3);}
.c-title{font-family:'Cinzel Decorative',cursive;font-size:1.9rem;color:#ffd700;letter-spacing:4px;margin:6px 0 3px;}
.c-sub{font-family:'Cinzel Decorative',cursive;font-size:.72rem;color:#c8a96e;letter-spacing:3px;}

.divrow{display:flex;align-items:center;gap:10px;padding:10px 22px;opacity:.75;}
.dl{flex:1;height:1px;background:linear-gradient(90deg,transparent,#b8860b,transparent);}
.dd{width:7px;height:7px;background:#ffd700;transform:rotate(45deg);flex-shrink:0;}

.c-names{text-align:center;padding:12px 16px;position:relative;z-index:5;}
.ur-nm{font-family:'Noto Nastaliq Urdu',serif;font-size:1.9rem;color:#ffd700;direction:rtl;line-height:2;text-shadow:0 0 10px rgba(255,215,0,.2);}
.weds-lbl{font-family:'Cinzel Decorative',cursive;font-size:.68rem;color:#b8860b;letter-spacing:4px;margin:3px 0;}
.en-nm{font-family:'Cinzel Decorative',cursive;font-size:1rem;color:#e8c878;letter-spacing:2px;}
.amp{color:#ffd700;font-size:1.5rem;margin:0 10px;}

.dg{display:grid;grid-template-columns:1fr 1fr;gap:4px;padding:0 16px 16px;position:relative;z-index:5;}
.dc{background:rgba(184,134,11,.08);border:1px solid rgba(184,134,11,.22);border-radius:8px;padding:11px 12px;text-align:center;margin:3px;}
.dl2{font-family:'Cinzel Decorative',cursive;font-size:.63rem;color:#c8a96e;letter-spacing:2px;margin-bottom:5px;}
.dv{font-size:.95rem;color:#ffd700;font-weight:600;}
.dv-ur{font-family:'Noto Nastaliq Urdu',serif;font-size:.82rem;color:#e8c878;direction:rtl;margin-top:2px;}

/* COUNTDOWN */
.cd-sec{text-align:center;padding:16px;background:rgba(0,0,0,.3);border-top:1px solid rgba(184,134,11,.25);border-bottom:1px solid rgba(184,134,11,.25);position:relative;z-index:5;}
.cd-lbl{font-family:'Cinzel Decorative',cursive;font-size:.68rem;color:#c8a96e;letter-spacing:3px;margin-bottom:10px;}
.cd-row{display:flex;justify-content:center;gap:10px;flex-wrap:wrap;}
.cd-b{background:rgba(139,0,0,.4);border:1px solid #b8860b;border-radius:8px;padding:8px 14px;min-width:54px;animation:pulse 2s ease-in-out infinite;}
.cd-b:nth-child(2){animation-delay:.25s}.cd-b:nth-child(3){animation-delay:.5s}.cd-b:nth-child(4){animation-delay:.75s}
.cd-n{font-size:1.65rem;color:#ffd700;font-weight:700;line-height:1;}
.cd-u{font-size:.58rem;color:#c8a96e;letter-spacing:1px;text-transform:uppercase;margin-top:2px;}

.c-invite{padding:16px 20px;text-align:center;position:relative;z-index:5;}
.inv-hi{font-size:.95rem;color:#e8c878;line-height:2;}
.inv-hi span{color:#ffd700;font-weight:600;}
.inv-ur{font-family:'Noto Nastaliq Urdu',serif;font-size:1rem;color:#c8a96e;direction:rtl;line-height:2.2;margin-top:10px;}

.c-venue{text-align:center;padding:12px 18px 4px;position:relative;z-index:5;}
.v-lbl{font-family:'Cinzel Decorative',cursive;font-size:.65rem;color:#c8a96e;letter-spacing:2px;margin-bottom:5px;}
.v-name{font-size:1.05rem;color:#ffd700;font-weight:600;}
.v-dist{font-size:.84rem;color:#c8a96e;margin-top:2px;}
.v-ur{font-family:'Noto Nastaliq Urdu',serif;font-size:.9rem;color:#e8c878;direction:rtl;margin-top:3px;}
.map-a{display:inline-flex;align-items:center;gap:8px;margin:10px auto;background:rgba(139,0,0,.3);color:#ffd700;border:1px solid #b8860b;padding:9px 26px;border-radius:50px;font-family:'Cinzel Decorative',cursive;font-size:.7rem;letter-spacing:1px;text-decoration:none;transition:all .22s;}
.map-a:hover{background:rgba(184,134,11,.22);border-color:#ffd700;}

.rsvp-btn{display:block;margin:18px auto 24px;background:linear-gradient(135deg,#8B0000,#b8860b,#8B0000);color:#fff8e1;border:2px solid #ffd700;padding:12px 44px;font-family:'Cinzel Decorative',cursive;font-size:.8rem;letter-spacing:2px;border-radius:50px;cursor:pointer;box-shadow:0 4px 18px rgba(184,134,11,.3);transition:all .3s;position:relative;z-index:5;}
.rsvp-btn:hover{transform:translateY(-2px);}

/* ====== FORM ====== */
#pg-form{background:#080100;}
.form-box{width:100%;max-width:600px;background:linear-gradient(160deg,#1a0600,#2e0d00);border:2px solid #b8860b;border-radius:16px;padding:28px 24px;box-shadow:0 0 40px rgba(184,134,11,.18);}
.ft{font-family:'Cinzel Decorative',cursive;font-size:1.2rem;color:#ffd700;text-align:center;letter-spacing:2px;margin-bottom:4px;}
.fs2{text-align:center;color:#c8a96e;font-size:.86rem;margin-bottom:22px;}
.fg{margin-bottom:16px;}
.fl{display:block;font-family:'Cinzel Decorative',cursive;font-size:.72rem;color:#c8a96e;letter-spacing:1px;margin-bottom:5px;}
.fi,.fsel,.ftx{width:100%;background:rgba(255,255,255,.05);border:1px solid rgba(184,134,11,.4);border-radius:8px;color:#ffd700;padding:10px 13px;font-size:.93rem;font-family:'Cormorant Garamond',serif;outline:none;transition:border-color .2s;}
.fi:focus,.fsel:focus,.ftx:focus{border-color:#ffd700;background:rgba(255,215,0,.04);}
.fsel option{background:#1a0600;color:#ffd700;}
.ftx{resize:vertical;min-height:72px;}
.rrow{display:flex;gap:12px;flex-wrap:wrap;}
.rl{display:flex;align-items:center;gap:7px;color:#e8c878;cursor:pointer;font-size:.92rem;padding:8px 18px;border:1px solid rgba(184,134,11,.4);border-radius:50px;transition:all .2s;}
.rl:hover{border-color:#ffd700;background:rgba(255,215,0,.07);}
.rl input{accent-color:#b8860b;}
.hidden{display:none!important;}
.sbtn{width:100%;background:linear-gradient(135deg,#8B0000,#b8860b,#8B0000);color:#fff8e1;border:2px solid #ffd700;padding:13px;font-family:'Cinzel Decorative',cursive;font-size:.82rem;letter-spacing:2px;border-radius:50px;cursor:pointer;margin-top:8px;transition:all .3s;}
.sbtn:hover{transform:translateY(-2px);}
.sbtn:disabled{opacity:.6;cursor:not-allowed;transform:none;}
.succ{text-align:center;padding:28px 10px;display:none;}

/* ====== QR PAGE ====== */
#pg-qr{background:#080100;}
.qr-top{text-align:center;margin-bottom:22px;width:100%;max-width:680px;}
.qr-title{font-family:'Cinzel Decorative',cursive;font-size:1.2rem;color:#ffd700;letter-spacing:3px;margin-bottom:5px;}
.qr-sub{color:#c8a96e;font-size:.85rem;margin-bottom:14px;}
.print-btn2{background:linear-gradient(135deg,#8B0000,#b8860b,#8B0000);color:#fff8e1;border:2px solid #ffd700;padding:10px 34px;font-family:'Cinzel Decorative',cursive;font-size:.76rem;letter-spacing:2px;border-radius:50px;cursor:pointer;box-shadow:0 4px 16px rgba(184,134,11,.35);transition:all .25s;}
.print-btn2:hover{transform:translateY(-1px);}
.qr-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(285px,1fr));gap:18px;width:100%;max-width:680px;}

/* QR card */
.qrc{background:linear-gradient(160deg,#1a0600 0%,#2e0d00 48%,#1a0600 100%);border:2px solid #b8860b;border-radius:13px;padding:16px 14px;text-align:center;position:relative;overflow:hidden;box-shadow:0 0 22px rgba(184,134,11,.15);}
.qrc::before{content:'';position:absolute;inset:6px;border:1px solid rgba(184,134,11,.18);border-radius:8px;pointer-events:none;}
.qco{position:absolute;width:18px;height:18px;opacity:.4;}
.qco.tl{top:7px;left:7px}.qco.tr{top:7px;right:7px;transform:scaleX(-1)}.qco.bl{bottom:7px;left:7px;transform:scaleY(-1)}.qco.br{bottom:7px;right:7px;transform:scale(-1,-1)}
.qc-bism{font-family:'Noto Nastaliq Urdu',serif;font-size:.95rem;color:#ffd700;direction:rtl;line-height:1.9;margin-bottom:3px;}
.qc-tag{font-family:'Cinzel Decorative',cursive;font-size:.6rem;color:#b8860b;letter-spacing:3px;margin-bottom:3px;}
.qc-couple{font-family:'Noto Nastaliq Urdu',serif;font-size:.85rem;color:#c8a96e;direction:rtl;line-height:1.7;margin-bottom:7px;}
.qc-div{height:1px;background:linear-gradient(90deg,transparent,#b8860b 30%,#ffd700 50%,#b8860b 70%,transparent);margin:6px 8px;}
.for-lbl{font-family:'Cinzel Decorative',cursive;font-size:.55rem;color:#906040;letter-spacing:2px;margin:6px 0 2px;}
.qc-gname{font-family:'Noto Nastaliq Urdu',serif;font-size:1.45rem;color:#ffd700;direction:rtl;line-height:1.7;text-shadow:0 0 10px rgba(255,215,0,.25);}
.qc-gen{font-size:.7rem;color:#705040;letter-spacing:1px;margin-bottom:5px;}
.qr-wrap{background:#fff;border:2px solid #b8860b;border-radius:9px;padding:6px;display:inline-block;margin:7px 0 5px;box-shadow:0 0 10px rgba(184,134,11,.2);}
.qr-wrap img{display:block;width:150px;height:150px;}
.scan-lbl2{font-size:.62rem;color:#c8a96e;letter-spacing:1px;margin-bottom:6px;}
.qc-date{font-family:'Cinzel Decorative',cursive;font-size:.68rem;color:#ffd700;letter-spacing:1px;}
.qc-venue{font-size:.7rem;color:#c8a96e;margin:2px 0;}
.qc-vur{font-family:'Noto Nastaliq Urdu',serif;font-size:.7rem;color:#705040;direction:rtl;}
.qc-time{font-size:.63rem;color:#503020;margin-top:3px;}

/* back btn */
.back-btn{background:transparent;color:#c8a96e;border:1px solid rgba(184,134,11,.35);border-radius:50px;padding:8px 22px;cursor:pointer;margin:14px auto 0;font-family:'Cinzel Decorative',cursive;font-size:.68rem;letter-spacing:1px;display:block;transition:all .2s;}
.back-btn:hover{border-color:#ffd700;color:#ffd700;}

/* PRINT */
@media print{
  body{background:#fff!important;padding:0;}
  #mbtn,#pg-welcome,#pg-card,#pg-form,.back-btn,.qr-top{display:none!important;}
  #pg-qr{display:block!important;padding:0;background:#fff!important;}
  .qr-grid{display:block;}
  .qrc{page-break-inside:avoid;max-width:300px;margin:8px auto;background:#fff!important;border:2px solid #8B0000!important;box-shadow:none!important;-webkit-print-color-adjust:exact;print-color-adjust:exact;}
  .qc-bism,.qc-tag,.qc-couple,.for-lbl,.qc-gname,.scan-lbl2,.qc-date,.qc-venue,.qc-vur,.qc-time{color:#000!important;}
}
</style>
</head>
<body>
<button id="mbtn">🎵</button>

<!-- PAGE 1: WELCOME -->
<div class="pg on" id="pg-welcome">
  <span class="welcome-rose">🌹</span>
  <div class="w-bism">بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيْمِ</div>
  <div class="w-guest" id="guest-disp">محترم مہمان</div>
  <div class="w-invite">آپ کو تقریبِ شادی میں دل سے مدعو کیا جاتا ہے</div>
  <div class="w-invite-en">You are warmly invited to the Walima Celebration</div>
  <div class="w-info">
    🌹 <b>Shafi Ur Rehman & Ruqyya Khatoon</b><br>
    <b>Shadi — 30 May 2026</b><br>
    نکاح بعد نمازِ ظہر • Nikah After Zuhr<br>
    Kurda, Distt Basti, U.P
  </div>
  <button class="enter-btn" onclick="go('card')">✦ Card Dekhein ✦</button>
</div>

<!-- PAGE 2: CARD -->
<div class="pg" id="pg-card">
<div class="card-box">
  <svg class="co tl" viewBox="0 0 76 76"><path d="M5,5L5,33Q5,11,29,11L33,11 M5,5L33,5 M10,10L10,26Q10,16,24,16L27,16" stroke="#b8860b" stroke-width="1.5" fill="none"/><circle cx="8" cy="8" r="3" fill="#b8860b" opacity=".8"/></svg>
  <svg class="co tr" viewBox="0 0 76 76"><path d="M5,5L5,33Q5,11,29,11L33,11 M5,5L33,5 M10,10L10,26Q10,16,24,16L27,16" stroke="#b8860b" stroke-width="1.5" fill="none"/><circle cx="8" cy="8" r="3" fill="#b8860b" opacity=".8"/></svg>
  <svg class="co bl" viewBox="0 0 76 76"><path d="M5,5L5,33Q5,11,29,11L33,11 M5,5L33,5 M10,10L10,26Q10,16,24,16L27,16" stroke="#b8860b" stroke-width="1.5" fill="none"/><circle cx="8" cy="8" r="3" fill="#b8860b" opacity=".8"/></svg>
  <svg class="co br" viewBox="0 0 76 76"><path d="M5,5L5,33Q5,11,29,11L33,11 M5,5L33,5 M10,10L10,26Q10,16,24,16L27,16" stroke="#b8860b" stroke-width="1.5" fill="none"/><circle cx="8" cy="8" r="3" fill="#b8860b" opacity=".8"/></svg>

  <div class="c-head">
    <div class="c-bism">بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيْمِ</div>
    <div class="c-title">SHADI</div>
    <div class="c-sub">✦ شادی ✦ विवाह ✦</div>
  </div>
  <div class="divrow"><div class="dl"></div><div class="dd"></div><div class="dl"></div></div>
  <div class="c-names">
    <div class="ur-nm">شفیع الرحمٰن</div>
    <div class="weds-lbl">WEDS</div>
    <div class="ur-nm">رقیہ خاتون</div>
    <div style="margin-top:7px;">
      <span class="en-nm">Shafi Ur Rehman</span>
      <span class="amp">♥</span>
      <span class="en-nm">Ruqyya Khatoon</span>
    </div>
  </div>
  <div class="divrow"><div class="dl"></div><div class="dd"></div><div class="dl"></div></div>
  <div class="dg">
    <div class="dc"><div class="dl2">Date / تاریخ</div><div class="dv">30 May 2026</div><div class="dv-ur">30 مئی 2026</div></div>
    <div class="dc"><div class="dl2">Event / تقریب</div><div class="dv">Shadi</div><div class="dv-ur">تقریبِ شادی</div></div>
    <div class="dc" style="grid-column:1/-1;text-align:left;">
      <div class="dl2" style="text-align:center;margin-bottom:8px;">Program / پروگرام</div>
      <div style="font-size:.82rem;color:#ffd700;line-height:2.2;text-align:center;">
        🕐 <b>Nikah</b> — Baad Namaz Zuhr &nbsp;|&nbsp; نکاح بعد نمازِ ظہر<br>
        🍽️ <b>Khana</b> — Baad Nikah &nbsp;|&nbsp; کھانا بعد نکاح<br>
        🌸 <b>Rukhsati</b> — Sham 5 Baje &nbsp;|&nbsp; رخصتی شام 5 بجے
      </div>
    </div>
    <div class="dc"><div class="dl2">Venue / مقام</div><div class="dv" style="font-size:.84rem;">Kurda</div><div class="dv-ur">کردہ</div></div>
  </div>
  <div class="cd-sec">
    <div class="cd-lbl">✦ SHADI MEIN BAAKI ✦</div>
    <div class="cd-row">
      <div class="cd-b"><div class="cd-n" id="cd-d">00</div><div class="cd-u">Days</div></div>
      <div class="cd-b"><div class="cd-n" id="cd-h">00</div><div class="cd-u">Hours</div></div>
      <div class="cd-b"><div class="cd-n" id="cd-m">00</div><div class="cd-u">Mins</div></div>
      <div class="cd-b"><div class="cd-n" id="cd-s">00</div><div class="cd-u">Secs</div></div>
    </div>
  </div>
  <div class="c-invite">
    <div class="inv-hi"><span>Shafi Ur Rehman</span> aur <span>Ruqyya Khatoon</span> ki<br><span>Shadi</span> mein aapko aur aapke poore gharane ko<br><span>dil se khushamdeed kaha jaata hai 🌹</span></div>
    <div class="inv-ur">شفیع الرحمٰن اور رقیہ خاتون کی<br>تقریبِ شادی میں آپ کا دلی خیرمقدم ہے</div>
  </div>
  <div class="divrow"><div class="dl"></div><div class="dd"></div><div class="dl"></div></div>
  <div class="c-venue">
    <div class="v-lbl">Complete Address</div>
    <div class="v-name">Kurda</div>
    <div class="v-dist">Distt Basti, Uttar Pradesh</div>
    <div class="v-ur">کردہ، ضلع بستی، اتر پردیش</div>
    <a class="map-a" href="https://www.google.com/maps/place/Kurda,+Uttar+Pradesh+272163/@26.8633296,82.6046088,15z" target="_blank">📍 Google Maps — نقشہ دیکھیں</a>
  </div>
  <button class="rsvp-btn" onclick="go('form')">✉ RSVP — Jawab Dein ✉</button>
</div>
<button class="back-btn" onclick="go('welcome')">← Wapas</button>
</div>

<!-- PAGE 3: FORM -->
<div class="pg" id="pg-form">
<div class="form-box">
  <div class="ft">RSVP</div>
  <div class="fs2">Apni haziri confirm farmaein ✦ براہ کرم جواب دیں</div>

  <div id="form-body">
    <div class="fg">
      <label class="fl">Aapka Naam / آپ کا نام *</label>
      <input type="text" class="fi" id="f-name" placeholder="Apna poora naam likhein...">
    </div>
    <div class="fg">
      <label class="fl">Mobile Number / موبائل نمبر *</label>
      <input type="tel" class="fi" id="f-mob" placeholder="+91 XXXXX XXXXX">
    </div>
    <div class="fg">
      <label class="fl">Kya Aap Ayenge? / کیا آپ آئیں گے؟ *</label>
      <div class="rrow">
        <label class="rl"><input type="radio" name="att" value="yes" onchange="togF()"> ✅ Haan, Zaroor</label>
        <label class="rl"><input type="radio" name="att" value="no" onchange="togF()"> ❌ Maafi Chahta Hoon</label>
      </div>
    </div>
    <div class="fg hidden" id="fg-count">
      <label class="fl">Kitne Log Ayenge? / کتنے لوگ؟</label>
      <select class="fsel" id="f-count">
        <option value="1">1 Shakhs</option>
        <option value="2">2 Ashkhas</option>
        <option value="3">3 Ashkhas</option>
        <option value="4">4 Ashkhas</option>
        <option value="5">5 Ashkhas</option>
        <option value="5+">5 se zyada</option>
      </select>
    </div>
    <div class="fg hidden" id="fg-reason">
      <label class="fl">Wajah batayein / وجہ بتائیں</label>
      <textarea class="ftx" id="f-reason" placeholder="Aane mein koi majboori ho to zaroor likhein..."></textarea>
    </div>
    <button class="sbtn" id="sub-btn" onclick="submitForm()">✦ Jawab Bhejein — Submit ✦</button>
    <div id="form-err" style="color:#ff6060;font-size:.82rem;text-align:center;margin-top:8px;display:none;"></div>
  </div>

  <div class="succ" id="succ-div">
    <div style="font-size:3rem;margin-bottom:10px;">🌹</div>
    <div style="font-family:'Cinzel Decorative',cursive;font-size:1rem;color:#ffd700;margin-bottom:8px;">Shukriya! JazakAllah Khair</div>
    <div style="color:#c8a96e;">Aapka jawab hamare paas pahunch gaya.<br>Allah aapko barakat de. Aameen.</div>
    <div style="margin-top:12px;font-family:'Noto Nastaliq Urdu',serif;direction:rtl;color:#e8c878;font-size:1.05rem;">جزاک اللہ خیراً ۔ آمین</div>
  </div>
</div>
<button class="back-btn" onclick="go('card')">← Card Dekhein</button>
</div>

<!-- PAGE 4: QR CARDS -->
<div class="pg" id="pg-qr">
<div class="qr-top">
  <div class="qr-title">✦ QR INVITATION CARDS ✦</div>
  <div class="qr-sub">Print karein ya PDF save karein — har mehman ka alag card</div>
  <button class="print-btn2" onclick="window.print()">🖨️ Print / PDF Save</button>
</div>
<div class="qr-grid" id="qr-grid"></div>
<button class="back-btn" onclick="go('card')" style="margin-top:22px;">← Card Dekhein</button>
</div>

<script>
// ===== NAVIGATION =====
function go(pg){
  document.querySelectorAll('.pg').forEach(p=>p.classList.remove('on'));
  document.getElementById('pg-'+pg).classList.add('on');
  window.scrollTo(0,0);
}

// ===== GUEST NAME FROM URL =====
const gn = new URLSearchParams(window.location.search).get('guest');
if(gn) document.getElementById('guest-disp').textContent = decodeURIComponent(gn);

// ===== COUNTDOWN =====
function tick(){
  const now=new Date();
  const target=new Date('2026-05-30T13:00:00+05:30');
  const diff=target-now;
  if(diff<=0){
    ['cd-d','cd-h','cd-m','cd-s'].forEach(id=>document.getElementById(id).textContent='00');
    return;
  }
  const s=Math.floor(diff/1000);
  document.getElementById('cd-d').textContent=String(Math.floor(s/86400)).padStart(2,'0');
  document.getElementById('cd-h').textContent=String(Math.floor((s%86400)/3600)).padStart(2,'0');
  document.getElementById('cd-m').textContent=String(Math.floor((s%3600)/60)).padStart(2,'0');
  document.getElementById('cd-s').textContent=String(s%60).padStart(2,'0');
}
tick(); setInterval(tick,1000);

// ===== FORM =====
function togF(){
  const v=document.querySelector('input[name="att"]:checked')?.value;
  document.getElementById('fg-count').classList.toggle('hidden',v!=='yes');
  document.getElementById('fg-reason').classList.toggle('hidden',v!=='no');
}

const SCRIPT_URL='https://script.google.com/macros/s/AKfycbwEcWiUC9Dww2SLJhS0NWk9viuhvTK5XhJaorjysMv8IbRhsKkE8znv_9lC7q3bKaL1Rg/exec';

function showErr(msg){
  const e=document.getElementById('form-err');
  e.textContent=msg; e.style.display='block';
  setTimeout(()=>e.style.display='none',3000);
}

function submitForm(){
  const name=document.getElementById('f-name').value.trim();
  const mob=document.getElementById('f-mob').value.trim();
  const att=document.querySelector('input[name="att"]:checked')?.value;
  if(!name){showErr('❌ Naam zaroor likhein!');return;}
  if(!mob){showErr('❌ Mobile number zaroor likhein!');return;}
  if(!att){showErr('❌ Haan ya Na zaroor chunein!');return;}

  const count=att==='yes'?document.getElementById('f-count').value:'';
  const reason=att==='no'?document.getElementById('f-reason').value:'';

  const btn=document.getElementById('sub-btn');
  btn.textContent='⏳ Bhej rahe hain...';
  btn.disabled=true;

  // Build URL with params — works with Google Apps Script GET handler
  const p=new URLSearchParams({name,mob,attend:att,count,reason,
    timestamp:new Date().toLocaleString('en-IN',{timeZone:'Asia/Kolkata'})});

  // Use image trick — 100% works with no-cors Google Apps Script
  const img=new Image();
  img.onload=img.onerror=function(){
    document.getElementById('form-body').style.display='none';
    document.getElementById('succ-div').style.display='block';
  };
  img.src=SCRIPT_URL+'?'+p.toString();
}

// ===== MUSIC =====
let actx=null,playing=false,loopT=null;
const mb=document.getElementById('mbtn');
const notes=[261.63,293.66,329.63,349.23,392,440,493.88,523.25];
const mel=[2,3,4,3,2,1,0,1,2,3,4,5,4,3,2,1,2,3,4,3,2,1,0];
const dur=[.5,.5,.5,.5,.5,.5,.9,.5,.5,.5,.5,.5,.5,.55,.5,.5,.5,.5,.5,.5,.5,.5,.9];
function playM(){
  if(!actx)actx=new(window.AudioContext||window.webkitAudioContext)();
  let t=actx.currentTime+.1,total=0;
  mel.forEach((ni,i)=>{
    const o=actx.createOscillator(),g=actx.createGain();
    o.connect(g);g.connect(actx.destination);
    o.frequency.value=notes[ni];o.type='triangle';
    g.gain.setValueAtTime(0,t);
    g.gain.linearRampToValueAtTime(.09,t+.07);
    g.gain.linearRampToValueAtTime(.06,t+dur[i]-.07);
    g.gain.linearRampToValueAtTime(0,t+dur[i]);
    o.start(t);o.stop(t+dur[i]);
    t+=dur[i];total+=dur[i];
  });
  if(playing) loopT=setTimeout(playM,total*1000+300);
}
mb.addEventListener('click',()=>{
  if(!playing){playing=true;mb.textContent='🔇';playM();}
  else{playing=false;mb.textContent='🎵';clearTimeout(loopT);if(actx){actx.close();actx=null;}}
});

// ===== QR CARDS =====
const GUESTS=[];

// Build QR cards using Google Charts API (free, no signup needed)
function buildQR(){
  const grid=document.getElementById('qr-grid');
  grid.innerHTML='<div style="text-align:center;padding:30px;color:#c8a96e;font-family:Cinzel Decorative,cursive;font-size:.9rem;letter-spacing:2px;">✦ Shadi Card QR ✦<br><br><div style=\'font-size:.8rem;color:#665040;margin-top:8px;\'>Card ka link copy karke share karein</div></div>';
  return;
  const base=window.location.href.split('?')[0];
  GUESTS.forEach(function(g){
    const link=base+'?guest='+encodeURIComponent(g.ur);
    // Google Charts QR - dark maroon dots on cream bg
    const qrUrl='https://chart.googleapis.com/chart?cht=qr&chs=150x150&chl='+
      encodeURIComponent(link)+'&chco=1a0000,ffffff&chf=bg,s,fffdf5&chld=M|1';

    const card=document.createElement('div');
    card.className='qrc';

    ['tl','tr','bl','br'].forEach(p=>{
      card.innerHTML+=`<svg class="qco ${p}" viewBox="0 0 18 18"><polygon points="9,0.5 11,6.5 17.5,6.5 12.5,10.5 14.5,17 9,13 3.5,17 5.5,10.5 0.5,6.5 7,6.5" fill="#b8860b"/></svg>`;
    });

    card.innerHTML+=`
      <div class="qc-bism">بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيْمِ</div>
      <div class="qc-tag">✦ WALIMA ✦ ولیمہ ✦</div>
      <div class="qc-couple">شفیع الرحمٰن ♥ رقیہ خاتون</div>
      <div class="qc-div"></div>
      <div class="for-lbl">SPECIAL INVITATION FOR</div>
      <div class="qc-gname">${g.ur}</div>
      <div class="qc-gen">${g.en}</div>
      <div class="qr-wrap"><img src="${qrUrl}" alt="QR" width="150" height="150" loading="lazy"></div>
      <div class="scan-lbl2">📱 Scan Karein — اسکین کریں</div>
      <div class="qc-div"></div>
      <div class="qc-date">30 MAY 2026 — SHADI</div>
      <div class="qc-venue">📍 Danokuiyan, Sant Kabir Nagar, U.P</div>
      <div class="qc-vur">دانوکوئیاں، ضلع سنت کبیر نگر</div>
      <div class="qc-time">نکاح بعد نمازِ ظہر • Nikah After Zuhr Prayer</div>`;

    grid.appendChild(card);
  });
}
buildQR();

// Show QR button at bottom of card page
const qrBtn=document.createElement('button');
qrBtn.className='back-btn';
qrBtn.style.cssText='margin-top:6px;border-color:rgba(184,134,11,.6);color:#b8860b;';
qrBtn.style.display='none'; qrBtn.textContent='📋 QR Cards Dekhein';
qrBtn.onclick=()=>go('qr');
document.getElementById('pg-card').appendChild(qrBtn);
</script>
</body>
</html>
