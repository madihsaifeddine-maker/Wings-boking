<!doctype html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WINGS BOOKING - VIP</title>
  <style>
    :root{
      --bg:#0a0a0a;
      --card:#141414;
      --fg:#f6f0e5;
      --gold:#d4af37;
      --muted:#b7a489;
    }
    *{box-sizing:border-box}
    html,body{margin:0; padding:0; font-family: Inter, system-ui, Arial; background:var(--bg); color:var(--fg)}
    a{color:inherit; text-decoration:none}
    header{display:flex; justify-content:space-between; align-items:center; padding:18px 20px; border-bottom:1px solid #2a2a2a; position:sticky; top:0; background:#0a0a0a; z-index:999}
    .brand{font-weight:800; letter-spacing:.5px; font-size:1.1rem}
    .lang{display:flex; gap:8px}
    .btn{background:var(--gold); color:#000; border-radius:10px; padding:10px 14px; font-weight:700; cursor:pointer}
    .hero{min-height:62vh; display:flex; align-items:center; justify-content:center; text-align:center; padding:40px 20px; background:url('https://images.unsplash.com/photo-1511250975035-66662bb4b5f4?q=80&w=1600&auto=format&fit=crop') center/cover no-repeat; position:relative}
    .overlay{position:absolute; inset:0; background:linear-gradient(to bottom, rgba(0,0,0,.5), rgba(0,0,0,.7));}
    .hero-content{position:relative; z-index:1; max-width:800px}
    .hero h1{font-size:2.6rem; margin:0 0 12px; text-shadow:0 2px 14px rgba(0,0,0,.6)}
    .hero p{margin:0 0 20px; color:#ddd}
    section{padding:40px 20px}
    .section-grid{display:grid; grid-template-columns:repeat(3,1fr); gap:20px; max-width:1100px; margin:0 auto}
    .card{background:var(--card); border-radius:14px; padding:20px; min-height:140px; display:flex; flex-direction:column; justify-content:space-between; border:1px solid #2a2a2a}
    .section h2{margin:0 0 10px; font-size:1.5rem}
    form{display:grid; gap:12px; max-width:640px; margin:0 auto}
    input, select, textarea{width:100%; padding:12px; border-radius:8px; border:1px solid #333; background:#111; color:#fff}
    textarea{min-height:100px; resize:vertical}
    .gallery{display:grid; grid-template-columns:repeat(auto-fill, minmax(180px, 1fr)); gap:12px; max-width:1100px; margin:0 auto}
    .gallery img{width:100%; height:140px; object-fit:cover; border-radius:8px}
    .map{width:100%; height:320px; border:0; border-radius:12px; }
    footer{text-align:center; color:var(--muted); padding:20px}
    @media (max-width: 980px){
      .section-grid{grid-template-columns:1fr 1fr}
    }
    @media (max-width: 600px){
      .section-grid{grid-template-columns:1fr}
      .hero{min-height:55vh}
    }
  </style>
</head>
<body>

  <header>
    <div class="brand">WINGS BOOKING</div>
    <div class="lang" aria-label="Language switcher">
      <button class="btn" onclick="setLang('fr')">Fr</button>
      <button class="btn" onclick="setLang('en')">En</button>
      <button class="btn" onclick="setLang('th')">Thai</button>
      <button class="btn" onclick="setLang('ar')">العربية</button>
    </div>
  </header>

  <section class="hero" id="home" aria-label="VIP hero">
    <div class="overlay"></div>
    <div class="hero-content">
      <h1>تجربة حجز VIP فاخرة</h1>
      <p>اختيار باقة VIP / Gold / Standard مع عرض صور ومعرض وتواصل سهل عبر WhatsApp.</p>
      <a href="#booking" class="btn" aria-label="احجز الآن">احجز الآن</a>
    </div>
  </section>

  <section aria-labelledby="features" class="section" id="features">
    <h2>الخدمات والخصائص</h2>
    <div class="section-grid">
      <div class="card">
        <div> اختيار اللغة: Français | English | ไทย | العربية</div>
        <div> خرائط Google مدمجة</div>
      </div>
      <div class="card">
        <div> WhatsApp: 0777467727</div>
        <div> VIP / Gold / Standard</div>
      </div>
      <div class="card">
        <div> معرض صور احترافي</div>
        <div> تأثيرات حديثة</div>
      </div>
    </div>
  </section>

  <section aria-labelledby="booking-title" class="section" id="booking">
    <h2 id="booking-title">فورم الحجز</h2>
    <form onsubmit="return handleSubmit(event)">
      <input type="text" name="name" placeholder="الاسم الكامل" required />
      <input type="tel" name="phone" placeholder="الهاتف" required />
      <input type="date" name="date" required />
      <select name="package" required>
        <option value="" disabled selected>اختيار الباقة</option>
        <option>VIP</option>
        <option>Gold</option>
        <option>Standard</option>
      </select>
      <textarea name="notes" placeholder="ملاحظات (اختياري)"></textarea>
      <button class="btn" type="submit" aria-label="إرسال الحجز">إرسال الحجز</button>
    </form>
  </section>

  <section class="section" aria-labelledby="gallery-title" id="gallery">
    <h2 id="gallery-title">معرض الصور</h2>
    <div class="gallery" aria-label="معرض الصور">
      <img src="https://images.unsplash.com/photo-1504639725590-38135b4d8b28?q=80&w=600&auto=format&fit=crop" alt="صورة 1">
      <img src="https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?q=80&w=600&auto=format&fit=crop" alt="صورة 2">
      <img src="https://images.unsplash.com/photo-1491553895911-0055eca6402d?q=80&w=600&auto=format&fit=crop" alt="صورة 3">
      <img src="https://images.unsplash.com/photo-1520975922284-58b9b6e0d7b1?q=80&w=600&auto=format&fit=crop" alt="صورة 4">
    </div>
  </section>

  <section class="section" aria-labelledby="location-title" id="location">
    <h2 id="location-title">المكان والخرائط</h2>
    <iframe class="map" loading="lazy" 
