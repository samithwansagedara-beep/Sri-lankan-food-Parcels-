<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lanka Food Parcels — Authentic Sri Lankan Flavours Worldwide</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;0,900;1,400&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --spice:  #C0742A;
    --dark:   #3D0C02;
    --cream:  #FDF6EE;
    --gold:   #F5D9A8;
    --brown:  #7A4010;
    --teal:   #2A7C6F;
    --purple: #7B2D8B;
  }

  html { scroll-behavior: smooth; }
  body { background: var(--cream); font-family: 'DM Sans', sans-serif; color: #222; }

  /* ─── HERO ─── */
  .hero {
    background: linear-gradient(140deg, #3D0C02 0%, #7A2A0A 45%, #C0742A 100%);
    padding: 56px 20px 48px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23ffffff' fill-opacity='0.04'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/svg%3E");
    pointer-events: none;
  }
  .hero-flag { font-size: 48px; display: block; margin-bottom: 12px; animation: float 3s ease-in-out infinite; }
  @keyframes float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-6px)} }
  .hero h1 { font-family: 'Playfair Display', serif; font-size: clamp(28px,6vw,52px); font-weight: 900; color: #FFF8EE; letter-spacing: -1px; line-height: 1.1; position: relative; }
  .hero h1 span { color: var(--gold); font-style: italic; }
  .hero-tagline { font-size: 13px; color: var(--gold); letter-spacing: 3px; text-transform: uppercase; margin-top: 12px; font-weight: 300; position: relative; }
  .hero-badges { display: flex; justify-content: center; gap: 10px; flex-wrap: wrap; margin-top: 20px; position: relative; }
  .hero-badge { background: rgba(255,255,255,0.12); border: 1px solid rgba(255,255,255,0.25); color: #FFE8C0; font-size: 11px; padding: 5px 16px; border-radius: 20px; letter-spacing: 1px; }
  .hero-scroll { display: block; margin: 28px auto 0; width: 36px; height: 36px; border: 2px solid rgba(255,255,255,0.3); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: rgba(255,255,255,0.6); font-size: 16px; cursor: pointer; animation: bounce 2s infinite; }
  @keyframes bounce { 0%,100%{transform:translateY(0)} 50%{transform:translateY(4px)} }

  /* ─── NAV ─── */
  nav { background: var(--dark); display: flex; justify-content: center; border-bottom: 2px solid var(--spice); position: sticky; top: 0; z-index: 100; }
  .nav-btn { font-family: 'DM Sans', sans-serif; font-size: 12px; font-weight: 600; padding: 15px 28px; cursor: pointer; background: transparent; border: none; color: #D4956A; letter-spacing: 1.5px; text-transform: uppercase; transition: all .2s; border-bottom: 3px solid transparent; margin-bottom: -2px; }
  .nav-btn.active, .nav-btn:hover { color: #FFE8C0; background: rgba(192,116,42,.25); border-bottom-color: var(--spice); }

  /* ─── MAIN LAYOUT ─── */
  .page { display: none; animation: fadeIn .35s ease; }
  .page.active { display: block; }
  @keyframes fadeIn { from{opacity:0;transform:translateY(8px)} to{opacity:1;transform:translateY(0)} }

  /* ─── PACKAGE SELECTOR ─── */
  .pkg-bar { display: flex; gap: 10px; padding: 24px 20px 0; justify-content: center; flex-wrap: wrap; }
  .pkg-btn {
    font-family: 'DM Sans', sans-serif; font-size: 13px; font-weight: 700;
    padding: 11px 28px; border-radius: 100px; cursor: pointer;
    transition: all .25s; letter-spacing: .5px; border: 2.5px solid;
  }
  .pkg-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 18px rgba(0,0,0,.12); }
  .pkg-btn.active { color: white !important; box-shadow: 0 6px 20px rgba(0,0,0,.2); transform: translateY(-2px); }

  /* ─── PACKAGE BANNER ─── */
  .pkg-banner { margin: 16px 20px 0; border-radius: 16px; padding: 18px 20px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; border: 2px solid; transition: all .3s; }
  .pkg-banner-left h2 { font-family: 'Playfair Display', serif; font-size: 22px; font-weight: 700; }
  .pkg-banner-left p { font-size: 13px; color: #888; margin-top: 3px; }
  .pkg-price { font-family: 'Playfair Display', serif; font-size: 28px; font-weight: 900; }

  /* ─── VARIANTS ─── */
  .variants-label { font-size: 10px; text-transform: uppercase; letter-spacing: 2px; color: #aaa; padding: 18px 20px 8px; }
  .variants-grid { display: grid; grid-template-columns: repeat(5,1fr); gap: 8px; padding: 0 20px; }
  @media(max-width:540px){ .variants-grid { grid-template-columns: repeat(5,1fr); gap: 5px; } }
  .var-btn { padding: 12px 6px 10px; border-radius: 12px; cursor: pointer; transition: all .2s; text-align: center; border: 2px solid; font-size: 10px; font-weight: 700; letter-spacing: .5px; line-height: 1.4; }
  .var-btn .vi { font-size: 22px; display: block; margin-bottom: 4px; }
  .var-btn:hover { transform: translateY(-2px); }
  .var-btn.active { color: white !important; box-shadow: 0 4px 14px rgba(0,0,0,.18); }

  /* ─── PRODUCT CARD ─── */
  .prod-card { background: white; border-radius: 16px; overflow: hidden; margin: 16px 20px; box-shadow: 0 2px 20px rgba(0,0,0,.08); }
  .prod-card-head { padding: 16px 20px; display: flex; align-items: center; gap: 12px; border-bottom: 1.5px solid #f0e6d8; }
  .prod-card-head .emoij { font-size: 28px; }
  .prod-card-head h3 { font-family: 'Playfair Display', serif; font-size: 18px; font-weight: 700; }
  .prod-card-head p { font-size: 12px; color: #999; margin-top: 2px; }
  .prod-row { display: flex; justify-content: space-between; align-items: center; padding: 11px 20px; border-bottom: 1px solid #faf0e8; transition: background .15s; }
  .prod-row:hover { background: #fdf8f3; }
  .prod-row:last-child { border-bottom: none; }
  .prod-name { font-size: 13.5px; color: #333; }
  .prod-meta { display: flex; gap: 8px; align-items: center; }
  .prod-weight { font-size: 11.5px; color: #bbb; }
  .prod-unit { font-size: 11px; font-weight: 700; padding: 3px 10px; border-radius: 20px; }

  /* ─── PRICE CHIPS ─── */
  .price-chips { display: flex; gap: 10px; padding: 14px 20px; flex-wrap: wrap; }
  .chip { flex:1; min-width:130px; background:white; border-radius:12px; padding:12px 16px; border:1.5px solid #E8D5BE; }
  .chip label { font-size: 10px; text-transform: uppercase; letter-spacing:1.5px; color:#aaa; display:block; margin-bottom:4px; }
  .chip span { font-family:'Playfair Display',serif; font-size: 20px; font-weight:700; }

  /* ─── NOTE ─── */
  .note { background:#FFF4E6; border-left:3px solid var(--spice); padding:13px 18px; margin:0 20px 24px; border-radius:0 10px 10px 0; font-size:12.5px; color:var(--brown); line-height:1.7; }

  /* ─── SHIPPING TABLE ─── */
  .ship-head { padding: 28px 20px 4px; }
  .ship-head h2 { font-family: 'Playfair Display', serif; font-size: 24px; font-weight: 700; color: var(--dark); }
  .ship-head p { font-size: 13px; color: #888; margin-top: 6px; }
  .zones { display:flex; gap:8px; flex-wrap:wrap; padding:12px 20px; }
  .z { font-size:10.5px; padding:4px 12px; border-radius:20px; font-weight:700; letter-spacing:.5px; }
  .z-a { background:#FFE8E8; color:#B02020; }
  .z-b { background:#E8F5F0; color:#1A6A5A; }
  .z-c { background:#EAF0FF; color:#2040B0; }
  .table-wrap { margin:0 20px; border-radius:14px; overflow:hidden; box-shadow:0 2px 20px rgba(0,0,0,.08); overflow-x:auto; }
  table { width:100%; border-collapse:collapse; font-size:13px; min-width:520px; }
  thead th { background:var(--dark); color:var(--gold); padding:12px 14px; text-align:left; font-weight:500; letter-spacing:.5px; font-size:12px; }
  tbody td { padding:11px 14px; border-bottom:1px solid #F0E6D8; }
  tbody tr:last-child td { border-bottom:none; }
  tbody tr:nth-child(even) td { background:#FDF6EE; }
  .td-country { font-weight:600; }
  .td-basic { color:var(--spice); font-weight:700; }
  .td-std { color:var(--teal); font-weight:700; }
  .td-lux { color:var(--purple); font-weight:700; }
  .td-time { color:#888; font-size:12px; }

  /* ─── KG CARDS ─── */
  .kg-title { font-family:'Playfair Display',serif; font-size:18px; font-weight:700; padding:20px 20px 10px; color:var(--dark); }
  .kg-grid { display:grid; grid-template-columns:1fr 1fr; gap:10px; padding:0 20px 28px; }
  @media(max-width:400px){ .kg-grid { grid-template-columns:1fr; } }
  .kg-card { background:white; border-radius:12px; padding:14px 16px; box-shadow:0 1px 8px rgba(0,0,0,.07); }
  .kg-card .kz { display:inline-block; font-size:10px; font-weight:700; padding:3px 10px; border-radius:20px; margin-bottom:8px; }
  .kg-card .kr { font-family:'Playfair Display',serif; font-size:22px; font-weight:800; color:var(--dark); }

  /* ─── CONTACT / ORDER ─── */
  .cta-section { background:linear-gradient(135deg,#3D0C02,#7A2A0A); padding:40px 20px; text-align:center; margin-top:8px; }
  .cta-section h2 { font-family:'Playfair Display',serif; color:#FFF8EE; font-size:clamp(20px,4vw,32px); margin-bottom:10px; }
  .cta-section p { color:var(--gold); font-size:13px; margin-bottom:22px; line-height:1.7; max-width:460px; margin-left:auto; margin-right:auto; }
  .cta-btns { display:flex; gap:10px; justify-content:center; flex-wrap:wrap; }
  .cta-btn { padding:13px 28px; border-radius:100px; font-family:'DM Sans',sans-serif; font-weight:700; font-size:13px; letter-spacing:.5px; cursor:pointer; transition:all .2s; border:2px solid; }
  .cta-btn:hover { transform:translateY(-2px); box-shadow:0 6px 20px rgba(0,0,0,.25); }
  .cta-btn.primary { background:var(--gold); color:var(--dark); border-color:var(--gold); }
  .cta-btn.secondary { background:transparent; color:#FFE8C0; border-color:rgba(255,255,255,.35); }

  /* ─── FOOTER ─── */
  footer { background:var(--dark); padding:20px; text-align:center; }
  footer p { font-size:11.5px; color:#8A5030; letter-spacing:1px; line-height:1.9; }
  footer strong { color:var(--gold); }
</style>
</head>
<body>

<!-- HERO -->
<header class="hero">
  <span class="hero-flag">🇱🇰</span>
  <h1>Lanka <span>Food</span> Parcels</h1>
  <p class="hero-tagline">Authentic Sri Lankan Flavours Worldwide</p>
  <div class="hero-badges">
    <span class="hero-badge">✈️ Air Courier Delivery</span>
    <span class="hero-badge">🌿 Island-Fresh Packed</span>
    <span class="hero-badge">📦 11 Countries Served</span>
  </div>
  <div class="hero-scroll" onclick="document.querySelector('nav').scrollIntoView({behavior:'smooth'})">↓</div>
</header>

<!-- STICKY NAV -->
<nav>
  <button class="nav-btn active" onclick="showPage('packages',this)">📦 Packages</button>
  <button class="nav-btn" onclick="showPage('shipping',this)">✈️ Shipping Rates</button>
  <button class="nav-btn" onclick="showPage('order',this)">🛒 Order Now</button>
</nav>

<!-- ═══════════════ PACKAGES PAGE ═══════════════ -->
<div id="page-packages" class="page active">

  <!-- Package type buttons -->
  <div class="pkg-bar">
    <button class="pkg-btn active" id="pkgbtn-basic"
      style="color:#C0742A;border-color:#C0742A;background:white"
      onclick="selectPkg('basic')">🌿 Basic</button>
    <button class="pkg-btn" id="pkgbtn-standard"
      style="color:#2A7C6F;border-color:#2A7C6F;background:white"
      onclick="selectPkg('standard')">🍃 Standard</button>
    <button class="pkg-btn" id="pkgbtn-luxury"
      style="color:#7B2D8B;border-color:#7B2D8B;background:white"
      onclick="selectPkg('luxury')">👑 Luxury</button>
  </div>

  <!-- Banner -->
  <div class="pkg-banner" id="pkg-banner"></div>

  <!-- Variants -->
  <div class="variants-label">Choose Variant</div>
  <div class="variants-grid" id="variants-grid"></div>

  <!-- Product card -->
  <div class="prod-card" id="prod-card"></div>

  <!-- Price chips -->
  <div class="price-chips" id="price-chips"></div>

  <div class="note">
    💡 <strong>Note:</strong> All products are vacuum-sealed &amp; export-grade packed for air courier.
    Prices in USD. Actual shipping cost is added at checkout based on your destination &amp; package weight.
    Final total = Package price + Shipping charge.
  </div>
</div>

<!-- ═══════════════ SHIPPING PAGE ═══════════════ -->
<div id="page-shipping" class="page">
  <div class="ship-head">
    <h2>✈️ Air Courier Charges by Country</h2>
    <p>Estimated airfreight charges (USD) per package tier, from Sri Lanka to your destination.</p>
  </div>
  <div class="zones">
    <span class="z z-a">Zone A — Americas</span>
    <span class="z z-b">Zone B — Europe / Oceania</span>
    <span class="z z-c">Zone C — Middle East</span>
  </div>
  <div class="table-wrap">
    <table>
      <thead>
        <tr>
          <th>Country</th>
          <th>Zone</th>
          <th>🌿 Basic</th>
          <th>🍃 Standard</th>
          <th>👑 Luxury</th>
          <th>Transit Time</th>
        </tr>
      </thead>
      <tbody>
        <tr><td class="td-country">🇺🇸 USA</td><td><span class="z z-a">Zone A</span></td><td class="td-basic">$28–$35</td><td class="td-std">$55–$68</td><td class="td-lux">$95–$115</td><td class="td-time">⏱ 7–10 days</td></tr>
        <tr><td class="td-country">🇨🇦 Canada</td><td><span class="z z-a">Zone A</span></td><td class="td-basic">$30–$38</td><td class="td-std">$58–$72</td><td class="td-lux">$100–$120</td><td class="td-time">⏱ 8–12 days</td></tr>
        <tr><td class="td-country">🇦🇺 Australia</td><td><span class="z z-b">Zone B</span></td><td class="td-basic">$22–$30</td><td class="td-std">$45–$58</td><td class="td-lux">$82–$100</td><td class="td-time">⏱ 6–9 days</td></tr>
        <tr><td class="td-country">🇦🇪 Dubai (UAE)</td><td><span class="z z-c">Zone C</span></td><td class="td-basic">$12–$18</td><td class="td-std">$28–$38</td><td class="td-lux">$52–$65</td><td class="td-time">⏱ 3–5 days</td></tr>
        <tr><td class="td-country">🇬🇧 England (UK)</td><td><span class="z z-b">Zone B</span></td><td class="td-basic">$20–$28</td><td class="td-std">$42–$55</td><td class="td-lux">$78–$95</td><td class="td-time">⏱ 6–8 days</td></tr>
        <tr><td class="td-country">🇮🇪 Ireland</td><td><span class="z z-b">Zone B</span></td><td class="td-basic">$22–$30</td><td class="td-std">$45–$58</td><td class="td-lux">$82–$100</td><td class="td-time">⏱ 7–9 days</td></tr>
        <tr><td class="td-country">🇫🇷 France</td><td><span class="z z-b">Zone B</span></td><td class="td-basic">$21–$29</td><td class="td-std">$44–$56</td><td class="td-lux">$80–$98</td><td class="td-time">⏱ 6–9 days</td></tr>
        <tr><td class="td-country">🇩🇪 Germany</td><td><span class="z z-b">Zone B</span></td><td class="td-basic">$21–$29</td><td class="td-std">$44–$56</td><td class="td-lux">$80–$98</td><td class="td-time">⏱ 6–9 days</td></tr>
        <tr><td class="td-country">🇰🇼 Kuwait</td><td><span class="z z-c">Zone C</span></td><td class="td-basic">$13–$19</td><td class="td-std">$29–$40</td><td class="td-lux">$54–$68</td><td class="td-time">⏱ 3–5 days</td></tr>
        <tr><td class="td-country">🇶🇦 Qatar</td><td><span class="z z-c">Zone C</span></td><td class="td-basic">$12–$18</td><td class="td-std">$28–$38</td><td class="td-lux">$52–$65</td><td class="td-time">⏱ 3–5 days</td></tr>
        <tr><td class="td-country">🇳🇿 New Zealand</td><td><span class="z z-b">Zone B</span></td><td class="td-basic">$24–$32</td><td class="td-std">$50–$62</td><td class="td-lux">$88–$108</td><td class="td-time">⏱ 7–10 days</td></tr>
      </tbody>
    </table>
  </div>

  <div class="kg-title">📊 Approximate Per-KG Airfreight Rates</div>
  <div class="kg-grid">
    <div class="kg-card"><span class="kz z-c">Middle East</span><div class="kr">$4–6 / kg</div><div style="font-size:12px;color:#888;margin-top:4px">UAE · Kuwait · Qatar</div></div>
    <div class="kg-card"><span class="kz z-b">Europe &amp; Oceania</span><div class="kr">$7–10 / kg</div><div style="font-size:12px;color:#888;margin-top:4px">UK · EU · AU · NZ</div></div>
    <div class="kg-card"><span class="kz z-a">Americas</span><div class="kr">$10–14 / kg</div><div style="font-size:12px;color:#888;margin-top:4px">USA · Canada</div></div>
    <div class="kg-card" style="background:#FFF4E6;border:1.5px solid #E8C88A;">
      <span style="font-size:10px;font-weight:700;color:var(--brown)">⚡ Fastest</span>
      <div class="kr" style="font-size:18px;margin-top:6px">3 days</div>
      <div style="font-size:12px;color:#888;margin-top:4px">Dubai · Qatar · Kuwait</div>
    </div>
  </div>

  <div class="note">
    ⚠️ <strong>Shipping rates are estimates.</strong> Final charges depend on actual package weight, courier partner
    (DHL / FedEx / EMS), and any applicable customs/import duties in the destination country.
    Duties &amp; taxes are the buyer's responsibility. All shipments include full tracking.
  </div>
</div>

<!-- ═══════════════ ORDER PAGE ═══════════════ -->
<div id="page-order" class="page">
  <div class="ship-head">
    <h2>🛒 How to Order</h2>
    <p>Ordering is quick and simple — reach us via WhatsApp or email and we'll confirm your package, destination, and total cost.</p>
  </div>

  <div style="margin:0 20px 10px">
    <div style="background:white;border-radius:16px;overflow:hidden;box-shadow:0 2px 16px rgba(0,0,0,.08)">
      <div style="background:var(--dark);padding:14px 20px;color:var(--gold);font-size:12px;font-weight:600;letter-spacing:1.5px;text-transform:uppercase">
        📋 Order Steps
      </div>
      <div style="padding:0">
        <div class="prod-row"><span style="font-size:20px">1️⃣</span><span style="margin-left:12px;font-size:13.5px">Choose your <strong>package tier</strong> — Basic, Standard, or Luxury</span></div>
        <div class="prod-row"><span style="font-size:20px">2️⃣</span><span style="margin-left:12px;font-size:13.5px">Pick your favourite <strong>variant</strong> (Spice, Tea, Rice, Snack, or Sweets)</span></div>
        <div class="prod-row"><span style="font-size:20px">3️⃣</span><span style="margin-left:12px;font-size:13.5px">Tell us your <strong>destination country</strong> so we can quote exact shipping</span></div>
        <div class="prod-row"><span style="font-size:20px">4️⃣</span><span style="margin-left:12px;font-size:13.5px">Confirm order &amp; make <strong>payment</strong> (bank transfer / PayPal / card)</span></div>
        <div class="prod-row"><span style="font-size:20px">5️⃣</span><span style="margin-left:12px;font-size:13.5px">Receive your <strong>tracking number</strong> within 24–48 hours of dispatch</span></div>
      </div>
    </div>
  </div>

  <div style="margin:12px 20px">
    <div style="background:white;border-radius:16px;overflow:hidden;box-shadow:0 2px 16px rgba(0,0,0,.08)">
      <div style="background:var(--dark);padding:14px 20px;color:var(--gold);font-size:12px;font-weight:600;letter-spacing:1.5px;text-transform:uppercase">
        📞 Contact Us
      </div>
      <div style="padding:20px 20px;display:flex;flex-direction:column;gap:14px">
        <a href="https://wa.me/94XXXXXXXXX" target="_blank" style="display:flex;align-items:center;gap:14px;padding:14px 18px;background:#E8F8EE;border-radius:12px;border:1.5px solid #A8D8BC;text-decoration:none;color:#1A5A30;font-weight:600;font-size:14px">
          <span style="font-size:28px">💬</span>
          <div>
            <div>WhatsApp Us</div>
            <div style="font-size:11.5px;color:#888;font-weight:400;margin-top:2px">+94 XX XXX XXXX · Fastest response</div>
          </div>
        </a>
        <a href="mailto:orders@lankafoodparcels.com" style="display:flex;align-items:center;gap:14px;padding:14px 18px;background:#FFF4E6;border-radius:12px;border:1.5px solid #E8C88A;text-decoration:none;color:var(--brown);font-weight:600;font-size:14px">
          <span style="font-size:28px">📧</span>
          <div>
            <div>Email Us</div>
            <div style="font-size:11.5px;color:#888;font-weight:400;margin-top:2px">orders@lankafoodparcels.com</div>
          </div>
        </a>
        <a href="https://www.facebook.com/lankafoodparcels" target="_blank" style="display:flex;align-items:center;gap:14px;padding:14px 18px;background:#EEF2FF;border-radius:12px;border:1.5px solid #B0BEFF;text-decoration:none;color:#2040B0;font-weight:600;font-size:14px">
          <span style="font-size:28px">📘</span>
          <div>
            <div>Facebook Page</div>
            <div style="font-size:11.5px;color:#888;font-weight:400;margin-top:2px">@lankafoodparcels</div>
          </div>
        </a>
      </div>
    </div>
  </div>

  <div class="note" style="margin-bottom:24px">
    📦 <strong>Custom Requests:</strong> Want to mix products from different variants? Need a corporate hamper or festival gift box? Contact us — we accommodate custom orders!
  </div>
</div>

<!-- CTA SECTION (always visible) -->
<div class="cta-section">
  <h2>🌴 Taste Sri Lanka, Anywhere in the World</h2>
  <p>From our island to your doorstep — hand-packed with love, sealed for freshness, shipped with care.</p>
  <div class="cta-btns">
    <button class="cta-btn primary" onclick="showPage('packages',document.querySelectorAll('.nav-btn')[0])">Browse Packages →</button>
    <button class="cta-btn secondary" onclick="showPage('order',document.querySelectorAll('.nav-btn')[2])">Order Now</button>
  </div>
</div>

<footer>
  <p>🇱🇰 <strong>Lanka Food Parcels</strong><br>
  Delivering the taste of home worldwide · All prices in USD<br>
  © 2025 Lanka Food Parcels · Subject to change without notice</p>
</footer>

<script>
/* ── DATA ── */
const PKG = {
  basic: {
    color:'#C0742A', light:'#FFF4E6', border:'#E8A86A',
    icon:'🌿', label:'Basic', tagline:'Taste of Home', price:'$35 – $45', weight:'≈ 2–3 kg',
    variants:[
      { id:'B1', emoji:'🌶️', name:'Spice Essentials Box', desc:'Aromatic spice blends every Sri Lankan kitchen needs',
        products:[
          {n:'Roasted Curry Powder',q:'200g',u:'1 pack'},{n:'Unroasted Curry Powder',q:'200g',u:'1 pack'},
          {n:'Raw Turmeric Powder',q:'100g',u:'1 pack'},{n:'Chilli Powder',q:'150g',u:'1 pack'},
          {n:'Black Pepper Powder',q:'100g',u:'1 pack'},{n:'Coriander Powder',q:'100g',u:'1 pack'}]},
      { id:'B2', emoji:'🍵', name:'Ceylon Tea & Biscuits Box', desc:'Premium Ceylon tea with beloved local biscuits',
        products:[
          {n:'Ceylon Black Tea (BOPF)',q:'200g',u:'1 pack'},{n:'Ceylon Green Tea',q:'100g',u:'1 pack'},
          {n:'Cream Cracker Biscuits',q:'200g',u:'1 pack'},{n:'Marie Biscuits',q:'200g',u:'1 pack'},
          {n:'Chocolate Puff',q:'150g',u:'1 pack'},{n:'Milk Toffees',q:'100g',u:'1 pack'}]},
      { id:'B3', emoji:'🌾', name:'Rice & Grain Box', desc:'Authentic Sri Lankan rice & staple grains',
        products:[
          {n:'Samba Rice (Red)',q:'1 kg',u:'1 bag'},{n:'Keeri Samba Rice',q:'500g',u:'1 bag'},
          {n:'Red Raw Rice Flour',q:'500g',u:'1 bag'},{n:'Kurakkan Flour',q:'500g',u:'1 bag'},
          {n:'Black-Eye Beans',q:'250g',u:'1 pack'},{n:'Dried Dhal (Red Lentils)',q:'250g',u:'1 pack'}]},
      { id:'B4', emoji:'🥜', name:'Snack Attack Box', desc:'Crispy, savory street-style Sri Lankan snacks',
        products:[
          {n:'Murukku (Rice Crackers)',q:'200g',u:'1 pack'},{n:'Chilli Mixture',q:'200g',u:'1 pack'},
          {n:'Acharu (Pickled Mango)',q:'150g',u:'1 jar'},{n:'Bombay Mix',q:'150g',u:'1 pack'},
          {n:'Salted Cashews',q:'100g',u:'1 pack'},{n:'Peanut Brittle (Kadala Toffee)',q:'100g',u:'1 pack'}]},
      { id:'B5', emoji:'🍬', name:'Sweets & Treats Box', desc:'Traditional Sri Lankan confections & festive sweets',
        products:[
          {n:'Kavum (Oil Cake)',q:'150g',u:'1 pack'},{n:'Kokis',q:'150g',u:'1 pack'},
          {n:'Aasmi',q:'100g',u:'1 pack'},{n:'Milk Balls (Kiri Aluva)',q:'150g',u:'1 pack'},
          {n:'Coconut Toffee',q:'100g',u:'1 pack'},{n:'Jaggery (Palm Sugar)',q:'200g',u:'1 pack'}]}
    ]
  },
  standard: {
    color:'#2A7C6F', light:'#E8F7F4', border:'#6ABCB0',
    icon:'🍃', label:'Standard', tagline:'Full Flavour Experience', price:'$75 – $95', weight:'≈ 5–7 kg',
    variants:[
      { id:'S1', emoji:'🌶️', name:'Spice Master Box', desc:'Expanded spice collection with special blends',
        products:[
          {n:'Roasted Curry Powder',q:'400g',u:'2 packs'},{n:'Unroasted Curry Powder',q:'400g',u:'2 packs'},
          {n:'Raw Turmeric Powder',q:'200g',u:'2 packs'},{n:'Chilli Powder',q:'300g',u:'2 packs'},
          {n:'Black Pepper (whole)',q:'200g',u:'1 pack'},{n:'Fenugreek Seeds',q:'100g',u:'1 pack'},
          {n:'Cinnamon Sticks (Ceylon)',q:'100g',u:'1 pack'},{n:'Cardamom Pods',q:'50g',u:'1 pack'}]},
      { id:'S2', emoji:'🍵', name:'Tea Garden & Biscuit Box', desc:'Curated teas with expanded biscuit & candy selection',
        products:[
          {n:'Ceylon Black Tea (BOPF)',q:'400g',u:'2 packs'},{n:'Ceylon Green Tea',q:'200g',u:'2 packs'},
          {n:'Ceylon White Tea',q:'100g',u:'1 pack'},{n:'Cream Cracker Biscuits',q:'400g',u:'2 packs'},
          {n:'Marie Biscuits',q:'400g',u:'2 packs'},{n:'Chocolate Puff',q:'300g',u:'2 packs'},
          {n:'Milk Toffees',q:'200g',u:'2 packs'},{n:'Coconut Biscuits',q:'150g',u:'1 pack'}]},
      { id:'S3', emoji:'🌾', name:'Rice & Pantry Box', desc:'Full pantry staples for authentic Sri Lankan cooking',
        products:[
          {n:'Samba Rice (Red)',q:'2 kg',u:'2 bags'},{n:'Keeri Samba Rice',q:'1 kg',u:'2 bags'},
          {n:'Red Raw Rice Flour',q:'1 kg',u:'2 bags'},{n:'Kurakkan Flour',q:'500g',u:'1 bag'},
          {n:'Black-Eye Beans',q:'500g',u:'2 packs'},{n:'Dried Dhal',q:'500g',u:'2 packs'},
          {n:'Dried Maldive Fish',q:'200g',u:'1 pack'},{n:'Coconut Milk Powder',q:'250g',u:'1 pack'}]},
      { id:'S4', emoji:'🥜', name:'Snack Fiesta Box', desc:'Bigger snack haul with extra varieties',
        products:[
          {n:'Murukku (Rice Crackers)',q:'400g',u:'2 packs'},{n:'Chilli Mixture',q:'400g',u:'2 packs'},
          {n:'Acharu (Pickled Mango)',q:'300g',u:'2 jars'},{n:'Bombay Mix',q:'300g',u:'2 packs'},
          {n:'Salted Cashews',q:'200g',u:'2 packs'},{n:'Peanut Brittle',q:'200g',u:'2 packs'},
          {n:'Pol Toffee (Coconut Candy)',q:'150g',u:'1 pack'},{n:'Dry Fish Crackers',q:'100g',u:'1 pack'}]},
      { id:'S5', emoji:'🍬', name:'Festival Sweets Box', desc:'Generous traditional sweets for celebrations',
        products:[
          {n:'Kavum (Oil Cake)',q:'300g',u:'2 packs'},{n:'Kokis',q:'300g',u:'2 packs'},
          {n:'Aasmi',q:'200g',u:'2 packs'},{n:'Milk Balls (Kiri Aluva)',q:'300g',u:'2 packs'},
          {n:'Coconut Toffee',q:'200g',u:'2 packs'},{n:'Jaggery (Palm Sugar)',q:'400g',u:'2 packs'},
          {n:'Watalappam Mix',q:'200g',u:'1 pack'},{n:'Dodol',q:'200g',u:'1 pack'}]}
    ]
  },
  luxury: {
    color:'#7B2D8B', light:'#F8EEFA', border:'#C07AD0',
    icon:'👑', label:'Luxury', tagline:'Premium Sri Lankan Heritage', price:'$140 – $180', weight:'≈ 10–13 kg',
    variants:[
      { id:'L1', emoji:'🌶️', name:'Royal Spice Collection', desc:'Full artisan spice range including rare blends',
        products:[
          {n:'Roasted Curry Powder',q:'800g',u:'4 packs'},{n:'Unroasted Curry Powder',q:'800g',u:'4 packs'},
          {n:'Turmeric Powder',q:'400g',u:'4 packs'},{n:'Chilli Powder',q:'600g',u:'4 packs'},
          {n:'Ceylon Cinnamon Sticks',q:'300g',u:'3 packs'},{n:'Black Pepper (whole)',q:'400g',u:'2 packs'},
          {n:'Cardamom Pods',q:'150g',u:'3 packs'},{n:'Cloves (whole)',q:'100g',u:'2 packs'},
          {n:'Fenugreek Seeds',q:'200g',u:'2 packs'},{n:'Goraka (Gamboge)',q:'100g',u:'1 pack'}]},
      { id:'L2', emoji:'🍵', name:'Heritage Tea & Confection Box', desc:'Luxury tea estate selections with premium sweets',
        products:[
          {n:'Ceylon Silver Tips White Tea',q:'100g',u:'1 gift box'},{n:'Ceylon Black Tea (BOPF)',q:'800g',u:'4 packs'},
          {n:'Ceylon Green Tea',q:'400g',u:'4 packs'},{n:'Herbal Cinnamon Tea',q:'100g',u:'1 pack'},
          {n:'Cream Cracker Biscuits',q:'800g',u:'4 packs'},{n:'Marie Biscuits',q:'600g',u:'3 packs'},
          {n:'Chocolate Puff',q:'600g',u:'4 packs'},{n:'Coconut Biscuits',q:'400g',u:'2 packs'},
          {n:'Milk Toffees (Assorted)',q:'400g',u:'4 packs'},{n:'Mixed Chocolates',q:'200g',u:'1 box'}]},
      { id:'L3', emoji:'🌾', name:'Full Pantry Heritage Box', desc:'Complete Sri Lankan pantry for the whole family',
        products:[
          {n:'Samba Rice (Red)',q:'4 kg',u:'4 bags'},{n:'Keeri Samba Rice',q:'2 kg',u:'4 bags'},
          {n:'Red Raw Rice Flour',q:'2 kg',u:'4 bags'},{n:'Kurakkan Flour',q:'1 kg',u:'2 bags'},
          {n:'Black-Eye Beans',q:'1 kg',u:'4 packs'},{n:'Dried Dhal',q:'1 kg',u:'4 packs'},
          {n:'Dried Maldive Fish',q:'400g',u:'2 packs'},{n:'Coconut Milk Powder',q:'500g',u:'2 packs'},
          {n:'Tamarind Block',q:'200g',u:'2 packs'},{n:'Lunu Miris Paste',q:'200g',u:'2 jars'}]},
      { id:'L4', emoji:'🥜', name:'Ultimate Snack Hamper', desc:'Grand collection of all beloved Sri Lankan snacks',
        products:[
          {n:'Murukku (Rice Crackers)',q:'800g',u:'4 packs'},{n:'Chilli Mixture',q:'800g',u:'4 packs'},
          {n:'Acharu (Pickled Mango)',q:'600g',u:'4 jars'},{n:'Bombay Mix',q:'600g',u:'4 packs'},
          {n:'Salted Cashews',q:'400g',u:'4 packs'},{n:'Peanut Brittle',q:'400g',u:'4 packs'},
          {n:'Pol Toffee (Coconut Candy)',q:'400g',u:'2 packs'},{n:'Dry Fish Crackers',q:'200g',u:'2 packs'},
          {n:'Banana Chips',q:'300g',u:'2 packs'},{n:'Roasted Gram',q:'200g',u:'2 packs'}]},
      { id:'L5', emoji:'🍬', name:'Grand Festival Sweets Hamper', desc:'Complete traditional sweets for all occasions',
        products:[
          {n:'Kavum (Oil Cake)',q:'600g',u:'4 packs'},{n:'Kokis',q:'600g',u:'4 packs'},
          {n:'Aasmi',q:'400g',u:'4 packs'},{n:'Milk Balls (Kiri Aluva)',q:'600g',u:'4 packs'},
          {n:'Coconut Toffee',q:'400g',u:'4 packs'},{n:'Jaggery (Palm Sugar)',q:'800g',u:'4 packs'},
          {n:'Watalappam Mix',q:'400g',u:'2 packs'},{n:'Dodol',q:'400g',u:'2 packs'},
          {n:'Kevum Ladoo',q:'300g',u:'2 packs'},{n:'Halape (Traditional Sweet)',q:'300g',u:'2 packs'}]}
    ]
  }
};

let curPkg = 'basic';
let curVar = 0;

function showPage(id, btn) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  if(btn) btn.classList.add('active');
  window.scrollTo({top:0, behavior:'smooth'});
}

function selectPkg(key) {
  curPkg = key; curVar = 0;
  document.querySelectorAll('.pkg-btn').forEach(b => {
    const k = b.id.replace('pkgbtn-','');
    const p = PKG[k];
    b.style.background = k===key ? p.color : 'white';
    b.style.color = k===key ? 'white' : p.color;
    b.classList.toggle('active', k===key);
  });
  render();
}

function selectVar(i) {
  curVar = i; renderVariants(); renderProduct();
}

function render() {
  renderBanner(); renderVariants(); renderProduct(); renderChips();
}

function renderBanner() {
  const p = PKG[curPkg];
  const el = document.getElementById('pkg-banner');
  el.style.background = p.light;
  el.style.borderColor = p.border;
  el.innerHTML = `
    <div>
      <div style="font-family:'Playfair Display',serif;font-size:22px;font-weight:700;color:${p.color}">${p.icon} ${p.label} Package</div>
      <div style="font-size:13px;color:#888;margin-top:3px">${p.tagline} &bull; ${p.weight}</div>
    </div>
    <div style="font-family:'Playfair Display',serif;font-size:28px;font-weight:900;color:${p.color}">${p.price}</div>
  `;
}

function renderVariants() {
  const p = PKG[curPkg];
  const grid = document.getElementById('variants-grid');
  grid.innerHTML = p.variants.map((v,i) => `
    <button class="var-btn ${i===curVar?'active':''}"
      style="border-color:${p.border};background:${i===curVar?p.color:p.light};color:${i===curVar?'white':p.color}"
      onclick="selectVar(${i})">
      <span class="vi">${v.emoji}</span>${v.id}
    </button>
  `).join('');
}

function renderProduct() {
  const p = PKG[curPkg];
  const v = p.variants[curVar];
  const card = document.getElementById('prod-card');
  card.innerHTML = `
    <div class="prod-card-head" style="background:${p.light};border-color:${p.border}">
      <span class="emoij">${v.emoji}</span>
      <div>
        <h3 style="color:${p.color}">${v.name}</h3>
        <p>${v.desc}</p>
      </div>
    </div>
    <div style="padding:6px 0 0">
      <div style="font-size:10.5px;text-transform:uppercase;letter-spacing:1.5px;color:${p.color};font-weight:700;padding:8px 20px 4px">
        📋 ${v.products.length} Products Included
      </div>
      ${v.products.map(pr => `
        <div class="prod-row">
          <span class="prod-name">${pr.n}</span>
          <div class="prod-meta">
            <span class="prod-weight">${pr.q}</span>
            <span class="prod-unit" style="background:${p.light};color:${p.color}">${pr.u}</span>
          </div>
        </div>
      `).join('')}
    </div>
  `;
}

function renderChips() {
  const p = PKG[curPkg];
  document.getElementById('price-chips').innerHTML = `
    <div class="chip">
      <label>Package Price</label>
      <span style="color:${p.color}">${p.price}</span>
    </div>
    <div class="chip">
      <label>Est. Weight</label>
      <span style="color:#555;font-size:17px">${p.weight}</span>
    </div>
    <div class="chip" style="cursor:pointer" onclick="showPage('shipping',document.querySelectorAll('.nav-btn')[1])">
      <label>Shipping →</label>
      <span style="color:${p.color};font-size:17px">See Rates</span>
    </div>
  `;
}

// init
render();
</script>
</body>
</html>
