<!doctype html>
<html lang="pl">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<title>M-Shop • Jednoplikowy Sklep</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#0b0c0f; --card:#111216; --ring:#22252c; --fg:#eef2ff; --muted:#9aa3b2;
  --accent:#ff7a1a; --accent2:#f472b6; --ok:#22c55e;
}
*{box-sizing:border-box}
html,body{margin:0;background:var(--bg);color:var(--fg);font-family:Inter,system-ui,Segoe UI,Roboto,Helvetica,Arial,sans-serif;scroll-behavior:smooth}
a{color:#fff;text-decoration:none}
.container{max-width:1140px;margin:0 auto;padding:0 20px}

/* Header */
.header{position:sticky;top:0;z-index:80;background:rgba(0,0,0,.75);backdrop-filter:blur(8px);border-bottom:1px solid var(--ring)}
.nav{display:flex;align-items:center;justify-content:space-between;padding:12px 0}
.brand{display:flex;align-items:center;gap:10px}
.badge{width:40px;height:40px;border-radius:12px;display:grid;place-items:center;background:linear-gradient(135deg,var(--accent2),var(--accent));color:#000;font-weight:800}
.brand h1{font-size:20px;margin:0}
.actions{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
.navbtn,.btn{padding:9px 14px;border-radius:12px;font-weight:800;border:1px solid var(--ring);cursor:pointer;background:transparent;color:var(--fg)}
.btn{background:#fff;color:#000}

/* Hero */
.hero{padding:40px 0 22px}
.heroBox{background:
  radial-gradient(1200px 600px at 8% -10%,rgba(244,114,182,.22),transparent),
  radial-gradient(1200px 600px at 100% 0,rgba(255,122,26,.18),transparent);
  border:1px solid var(--ring);border-radius:18px;padding:28px;
  display:grid;grid-template-columns:1.2fr 1fr;gap:18px;align-items:center}
.hero h2{font-size:36px;line-height:1.05;margin:0}
.hero p{color:var(--muted);max-width:640px;margin:10px 0 0}
.heroImg{width:100%;height:260px;border-radius:14px;background:#fff;display:grid;place-items:center}
@media(max-width:860px){.heroBox{grid-template-columns:1fr}.heroImg{height:200px}}

/* Kats */
.kats{display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;margin:18px 0}
.kat{background:var(--card);border:1px solid var(--ring);border-radius:14px;padding:14px}
.kat .desc{color:var(--muted)}
@media(max-width:860px){.kats{grid-template-columns:1fr}}

/* Products */
.grid{display:grid;grid-template-columns:1fr 1fr;gap:18px;margin:18px 0}
@media(max-width:860px){.grid{grid-template-columns:1fr}}
.card{background:var(--card);border:1px solid var(--ring);border-radius:18px;overflow:hidden;position:relative}
.thumb{width:100%;height:360px;background:#fff;display:grid;place-items:center;cursor:pointer}
.tag{position:absolute;top:12px;left:12px;background:var(--ok);color:#001;padding:6px 10px;border-radius:999px;font-size:12px;font-weight:800}
.box{padding:14px}
.name{font-weight:800;font-size:18px}
.desc{color:var(--muted);margin-top:2px}
.price{font-weight:800;margin-top:8px}
.ctaRow{display:flex;align-items:center;gap:10px;margin-top:10px;flex-wrap:wrap}

/* Why & FAQ */
.why{display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;margin:22px 0}
.why .w{background:#0f1115;border:1px solid var(--ring);border-radius:14px;padding:14px}
@media(max-width:860px){.why{grid-template-columns:1fr}}
.faq .q{background:#0f1115;border:1px solid var(--ring);border-radius:14px;padding:12px;margin:10px 0;cursor:pointer}
.faq .a{display:none;color:var(--muted);padding:10px 12px 0 12px}

/* Footer */
.sub{margin:20px 0;background:#0f1115;border:1px solid var(--ring);border-radius:14px;padding:16px;display:flex;gap:12px;align-items:center;justify-content:space-between;flex-wrap:wrap}
.sub p{margin:0;font-weight:700}
.sep{height:1px;background:var(--ring);margin:18px 0}
footer{color:#cbd5e1;text-align:center;margin:14px 0}
.footer-nav{display:flex;gap:12px;justify-content:center;margin-top:6px;flex-wrap:wrap}

/* Modal cart */
.modalBG{position:fixed;inset:0;background:rgba(0,0,0,.7);display:none;align-items:center;justify-content:center;z-index:90}
.modal{width:min(680px,92vw);background:#000;border:1px solid var(--ring);border-radius:16px;padding:16px;color:#fff}
.row{display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--ring)}
.row .mini{width:60px;height:60px;border-radius:8px;background:#fff;display:grid;place-items:center}
.qty{display:flex;align-items:center;gap:6px}
.qty button{width:30px;height:30px;border-radius:8px;border:1px solid var(--ring);background:transparent;color:#fff;cursor:pointer}
.close{background:transparent;color:#fff;border:none;font-size:20px;cursor:pointer}
</style>
</head>
<body>

<header class="header">
  <div class="container nav">
    <div class="brand"><div class="badge">M</div><h1>M-Shop</h1></div>
    <div class="actions">
      <button class="navbtn" onclick="document.getElementById('kategorie').scrollIntoView({behavior:'smooth'})">Kategorie</button>
      <button class="navbtn" onclick="document.getElementById('produkty').scrollIntoView({behavior:'smooth'})">Sklep</button>
      <button class="navbtn" onclick="document.getElementById('faq').scrollIntoView({behavior:'smooth'})">FAQ</button>
      <button class="navbtn" onclick="document.getElementById('kontakt').scrollIntoView({behavior:'smooth'})">Kontakt</button>
      <button class="btn" id="openCart">Koszyk: <span id="count">0</span></button>
    </div>
  </div>
</header>

<main class="container">

  <!-- HERO -->
  <section class="hero" id="home">
    <div class="heroBox">
      <div>
        <h2>Nowa kolekcja <span style="background:linear-gradient(135deg,var(--accent2),var(--accent));-webkit-background-clip:text;background-clip:text;color:transparent">M-Classic</span></h2>
        <p>Kubki i koszulki z dużym „M” — proste zamawianie przez e-mail, szybka dostawa 4–6 dni. Przejdź do sklepu i zamów w 30 sekund.</p>
        <div style="display:flex;gap:10px;margin-top:16px;flex-wrap:wrap">
          <button class="btn" onclick="document.getElementById('produkty').scrollIntoView({behavior:'smooth'})">Przeglądaj produkty</button>
          <button class="navbtn" onclick="document.getElementById('kategorie').scrollIntoView({behavior:'smooth'})">Zobacz kategorie</button>
        </div>
      </div>
      <!-- BIAŁA KOSZULKA (SVG) -->
      <div class="heroImg">
        <svg width="260" height="160" viewBox="0 0 260 160" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Biała koszulka z M">
          <rect x="0" y="0" width="260" height="160" fill="#ffffff"/>
          <path d="M60 40 h140 v80 h-140 z" fill="#f5f5f5" stroke="#e5e7eb"/>
          <text x="130" y="100" text-anchor="middle" font-size="76" font-family="Arial, Helvetica, sans-serif" fill="#ff7a1a" font-weight="900">M</text>
        </svg>
      </div>
    </div>
  </section>

  <!-- KATEGORIE -->
  <section id="kategorie">
    <h3>Kategorie</h3>
    <div class="kats">
      <div class="kat"><strong>Odzież</strong><div class="desc">Koszulki M Classic</div></div>
      <div class="kat"><strong>Kubki</strong><div class="desc">Ceramika 330 ml</div></div>
      <div class="kat"><strong>Akcesoria</strong><div class="desc">Wkrótce</div></div>
    </div>
  </section>

  <!-- PRODUKTY -->
  <section id="produkty">
    <h3>Sklep</h3>
    <div class="grid">
      <!-- KOSZULKA -->
      <article class="card" data-id="shirt" data-price="62">
        <div class="thumb" data-clickadd="shirt">
          <!-- BIAŁA KOSZULKA (SVG) -->
          <svg width="100%" height="100%" viewBox="0 0 260 160" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Koszulka M Classic – Biała">
            <rect x="0" y="0" width="260" height="160" fill="#ffffff"/>
            <path d="M60 40 h140 v80 h-140 z" fill="#f5f5f5" stroke="#e5e7eb"/>
            <text x="130" y="100" text-anchor="middle" font-size="76" font-family="Arial, Helvetica, sans-serif" fill="#ff7a1a" font-weight="900">M</text>
          </svg>
        </div>
        <div class="box">
          <div class="name">Koszulka M Classic – Biała</div>
          <div class="desc">Bawełna 100%, duże M z przodu.</div>
          <div class="price">62,00 zł</div>
          <div class="ctaRow">
            <button class="btn add" data-add="shirt">Dodaj do koszyka</button>
          </div>
        </div>
      </article>

      <!-- KUBEK -->
      <article class="card" data-id="mug" data-price="34">
        <span class="tag">Nowość!</span>
        <div class="thumb" data-clickadd="mug">
          <!-- BIAŁY KUBEK (SVG) -->
          <svg width="100%" height="100%" viewBox="0 0 260 160" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Kubek M Classic – biały">
            <rect x="0" y="0" width="260" height="160" fill="#ffffff"/>
            <rect x="70" y="30" width="120" height="100" rx="8" fill="#f5f5f5" stroke="#e5e7eb"/>
            <circle cx="190" cy="80" r="26" fill="none" stroke="#e5e7eb" stroke-width="10"/>
            <text x="130" y="100" text-anchor="middle" font-size="64" font-family="Arial, Helvetica, sans-serif" fill="#ff7a1a" font-weight="900">M</text>
          </svg>
        </div>
        <div class="box">
          <div class="name">Kubek M Classic – biały</div>
          <div class="desc">Ceramika 330 ml z logo M.</div>
          <div class="price">34,00 zł</div>
          <div class="ctaRow">
            <button class="btn add" data-add="mug">Dodaj do koszyka</button>
          </div>
        </div>
      </article>
    </div>
  </section>

  <!-- WHY -->
  <section>
    <h3>Dlaczego M-Shop?</h3>
    <div class="why">
      <div class="w"><strong>Jakość</strong><div class="desc">Bawełna premium i trwała ceramika.</div></div>
      <div class="w"><strong>Szybka dostawa</strong><div class="desc">4–6 dni roboczych od płatności.</div></div>
      <div class="w"><strong>Proste zamówienia</strong><div class="desc">Koszyk + e-mail — zero zbędnych kroków.</div></div>
    </div>
  </section>

  <!-- FAQ -->
  <section id="faq" class="faq">
    <h3>FAQ</h3>
    <div class="q">Jak złożyć zamówienie?</div>
    <div class="a">Dodaj produkty do koszyka i kliknij „Zamów e-mailem”. W mailu uzupełnij adres dostawy.</div>
    <div class="q">Jakie są formy płatności?</div>
    <div class="a">Przelew po potwierdzeniu zamówienia; integracja PayPal dostępna na życzenie.</div>
    <div class="q">Kiedy otrzymam paczkę?</div>
    <div class="a">Realizacja trwa 4–6 dni roboczych od momentu zaksięgowania płatności.</div>
  </section>

  <!-- NEWSLETTER/CONTACT CTA -->
  <div class="sub" id="kontakt">
    <p>📩 Chcesz być informowany o nowościach?</p>
    <a class="btn" href="mailto:ministorebisnes@gmail.com?subject=Chcę%20być%20informowany%20o%20nowościach%20w%20M-Shop&body=Dzień%20dobry,%0AChcę%20otrzymywać%20informacje%20o%20nowościach.%0AProszę%20dodać%20mnie%20do%20listy%20mailowej.%0ADziękuję.">Tak</a>
  </div>

  <div class="sep"></div>

  <!-- REGULAMIN + DOSTAWA + O NAS -->
  <section id="regulamin">
    <h2>Regulamin sklepu internetowego M-Shop</h2>
    <p>Obowiązuje od dnia 2025-01-01. Regulamin określa zasady zakupów w sklepie M-Shop (woj. Pomorskie) oraz prawa i obowiązki Klienta.</p>
    <h3>Zakupy</h3>
    <ul>
      <li>Dodaj do koszyka → „Zamów e-mailem”.</li>
      <li>Dane dostawy: imię, adres, telefon.</li>
      <li>Płatność: przelew (PayPal na życzenie).</li>
      <li>Dostawa: 4–6 dni roboczych od płatności.</li>
    </ul>
    <h3>Zwroty i reklamacje</h3>
    <ul>
      <li>Zwrot do 14 dni (konsument).</li>
      <li>Reklamacje: odpowiedź do 14 dni.</li>
    </ul>
    <h3>RODO</h3>
    <p>Administrator: M-Shop. Dane przetwarzane wyłącznie w celu obsługi zamówień.</p>
  </section>

  <section id="dostawa">
    <h2>Dostawa</h2>
    <p>Wysyłka w terminie <strong>4–6 dni roboczych</strong> od zaksięgowania płatności. Formy dostawy: kurier / paczkomat (wg dostępności).</p>
  </section>

  <section id="onas">
    <h2>O nas</h2>
    <p>M-Shop to mały sklep z merch’em „M-Classic”. Stawiamy na jakość, prostotę i szybką obsługę.</p>
  </section>

</main>

<footer>
  © 2025 M-Shop – wszystkie prawa zastrzeżone
  <div class="footer-nav" style="margin-top:8px">
    <a href="#regulamin">Regulamin</a> ·
    <a href="#dostawa">Dostawa 4–6 dni</a> ·
    <a href="#kontakt">Kontakt</a> ·
    <a href="#onas">O nas</a> ·
    <a href="#produkty">Sklep</a>
  </div>
</footer>

<!-- MODAL KOSZYKA -->
<div class="modalBG" id="cartBG" aria-hidden="true">
  <div class="modal" role="dialog" aria-label="Koszyk">
    <div style="display:flex;align-items:center;justify-content:space-between">
      <strong>Twoje zamówienie</strong>
      <button class="close" id="closeCart" aria-label="Zamknij">✕</button>
    </div>
    <div id="cartRows" style="max-height:48vh;overflow:auto;margin-top:6px"></div>
    <div style="display:flex;align-items:center;justify-content:space-between;margin-top:8px;font-weight:800">
      <span>Suma</span><span id="total">0,00 zł</span>
    </div>
    <a id="mailto" class="btn" style="margin-top:10px" href="#">Zamów e-mailem</a>
    <p style="color:#9aa3b2;margin-top:6px">Wiadomość e-mail automatycznie zawiera podsumowanie koszyka.</p>
  </div>
</div>

<script>
// FAQ toggles
document.querySelectorAll('.faq .q').forEach(q=>{
  q.addEventListener('click', ()=>{
    const a = q.nextElementSibling;
    a.style.display = a.style.display==='block' ? 'none' : 'block';
  });
});

// Cart
const PLN = n => new Intl.NumberFormat('pl-PL',{style:'currency',currency:'PLN'}).format(n);
const cart = {};
function add(id, price, name, imgSvg){
  cart[id] = cart[id] || {name,price,img:imgSvg,qty:0};
  cart[id].qty++;
  update();
}
function dec(id){
  if(!cart[id]) return;
  cart[id].qty = Math.max(0, cart[id].qty-1);
  if(cart[id].qty===0) delete cart[id];
  update();
}
function sum(){ return Object.values(cart).reduce((s,it)=> s + it.price*it.qty, 0); }
function count(){ return Object.values(cart).reduce((s,it)=> s + it.qty, 0); }

document.querySelectorAll('.add').forEach(btn=>{
  btn.addEventListener('click', ()=>{
    const card = btn.closest('.card');
    const id = btn.dataset.add;
    const price = parseFloat(card.dataset.price);
    const name = card.querySelector('.name').textContent;
    const svg = card.querySelector('.thumb').innerHTML;
    add(id, price, name, svg);
  });
});
document.querySelectorAll('[data-clickadd]').forEach(area=>{
  area.addEventListener('click', ()=>{
    const id = area.dataset.clickadd;
    const card = area.closest('.card');
    const price = parseFloat(card.dataset.price);
    const name = card.querySelector('.name').textContent;
    const svg = area.innerHTML;
    add(id, price, name, svg);
  });
});

function update(){
  document.getElementById('count').textContent = count();
  const rows = document.getElementById('cartRows');
  const items = Object.entries(cart);
  rows.innerHTML = items.length ? items.map(([id,it])=>`
    <div class="row">
      <div class="mini">${it.img}</div>
      <div style="flex:1">
        <div style="font-weight:600">${it.name}</div>
        <div style="color:#9aa3b2;font-size:12px">${PLN(it.price)} / szt.</div>
        <div class="qty" style="margin-top:6px">
          <button data-dec="${id}">-</button>
          <span style="min-width:2ch;text-align:center">${it.qty}</span>
          <button data-add="${id}">+</button>
        </div>
      </div>
      <div style="font-weight:700">${PLN(it.price*it.qty)}</div>
    </div>
  `).join('') : '<p style="color:#9aa3b2">Koszyk jest pusty.</p>';
  rows.querySelectorAll('[data-dec]').forEach(b=> b.onclick=()=>dec(b.dataset.dec));
  rows.querySelectorAll('[data-add]').forEach(b=> b.onclick=()=>{
    const it = cart[b.dataset.add];
    add(b.dataset.add, it.price, it.name, it.img);
  });
  document.getElementById('total').textContent = PLN(sum());
  const itemsTxt = items.map(([id,it])=> `- ${it.name} x${it.qty} — ${PLN(it.price*it.qty)}`).join('%0A');
  const body = `Dzień dobry,%0AChcę zamówić:%0A${itemsTxt}%0ASuma: ${PLN(sum())}%0A%0ADane do dostawy:%0AImię i nazwisko:%0AAdres:%0ATelefon:%0ADziękuję.`;
  document.getElementById('mailto').href = `mailto:ministorebisnes@gmail.com?subject=Zamówienie M-Shop (One-Page)&body=${body}`;
}

// Modal
const bg = document.getElementById('cartBG');
document.getElementById('openCart').onclick = ()=>{ bg.style.display='flex'; update(); };
document.getElementById('closeCart').onclick = ()=>{ bg.style.display='none'; };
bg.onclick = (e)=>{ if(e.target===bg) bg.style.display='none'; };
</script>
</body>
</html>
