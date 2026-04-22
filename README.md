[index(5).html](https://github.com/user-attachments/files/26984275/index.5.html)[Uploading index(<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tarifs & Forfaits – Vélo</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --orange: #F5A623;
      --navy: #1A2B5F;
      --green: #2E6B3E;
      --rust: #C0440A;
      --slate: #4A6080;
      --cream: #FDF8F2;
      --dark: #111820;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--cream);
      font-family: 'DM Sans', sans-serif;
      color: var(--dark);
      min-height: 100vh;
    }

    header {
      background: var(--navy);
      color: white;
      padding: 2.5rem 2rem 2rem;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    header::before {
      content: '';
      position: absolute;
      top: -60px; left: -60px;
      width: 200px; height: 200px;
      border-radius: 50%;
      background: rgba(245,166,35,0.15);
    }
    header::after {
      content: '';
      position: absolute;
      bottom: -80px; right: -40px;
      width: 250px; height: 250px;
      border-radius: 50%;
      background: rgba(255,255,255,0.05);
    }
    .header-icon { font-size: 2.5rem; margin-bottom: 0.5rem; }
    header h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(2.8rem, 8vw, 5rem);
      letter-spacing: 3px;
      line-height: 1;
      color: white;
    }
    header h1 span { color: var(--orange); }
    header p {
      margin-top: 0.5rem;
      font-size: 0.95rem;
      color: rgba(255,255,255,0.6);
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    .subtitle {
      text-align: center;
      padding: 1.2rem 1rem 0.2rem;
      font-size: 0.95rem;
      color: #666;
    }
    .subtitle strong { color: var(--navy); }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1.2rem;
      padding: 1.2rem 1.5rem 2rem;
      max-width: 900px;
      margin: 0 auto;
    }

    .card {
      background: white;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 4px 20px rgba(0,0,0,0.07);
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
      color: inherit;
      display: block;
    }
    .card:hover { transform: translateY(-5px); box-shadow: 0 12px 32px rgba(0,0,0,0.15); }
    .card:active { transform: scale(0.98); }

    .card-header {
      padding: 0.9rem 1.2rem;
      color: white;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.3rem;
      letter-spacing: 1.5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .card-header .tap-hint {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.65rem;
      font-weight: 500;
      opacity: 0.85;
      background: rgba(255,255,255,0.2);
      padding: 0.2rem 0.5rem;
      border-radius: 20px;
    }

    .c-orange .card-header { background: var(--orange); }
    .c-navy   .card-header { background: var(--navy); }
    .c-green  .card-header { background: var(--green); }
    .c-rust   .card-header { background: var(--rust); }
    .c-slate  .card-header { background: var(--slate); }
    .c-gray   .card-header { background: #5A6472; }

    .card-body { padding: 1.2rem 1.4rem 1.4rem; }

    .price {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 3rem;
      line-height: 1;
      margin-bottom: 1rem;
      letter-spacing: 1px;
    }
    .c-orange .price { color: var(--orange); }
    .c-navy   .price { color: var(--navy); }
    .c-green  .price { color: var(--green); }
    .c-rust   .price { color: var(--rust); }
    .c-slate  .price { color: var(--slate); }
    .c-gray   .price { color: #5A6472; }

    ul { list-style: none; display: flex; flex-direction: column; gap: 0.5rem; }
    ul li {
      font-size: 0.9rem;
      color: #444;
      display: flex;
      align-items: flex-start;
      gap: 0.5rem;
      line-height: 1.4;
    }
    ul li::before {
      content: '●';
      font-size: 0.5rem;
      margin-top: 0.35rem;
      flex-shrink: 0;
    }
    .c-orange ul li::before { color: var(--orange); }
    .c-navy   ul li::before { color: var(--navy); }
    .c-green  ul li::before { color: var(--green); }
    .c-rust   ul li::before { color: var(--rust); }
    .c-slate  ul li::before { color: var(--slate); }
    .c-gray   ul li::before { color: #5A6472; }

    .option-note { margin-top: 0.8rem; font-size: 0.82rem; color: #777; font-style: italic; }

    .carte-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.55rem 0.7rem;
      margin: 0.3rem 0;
      border-radius: 10px;
      cursor: pointer;
      transition: background 0.15s;
    }
    .carte-item:hover { background: #f4f4f4; }
    .carte-item .label { font-size: 0.88rem; color: #444; }
    .carte-item .prix { font-weight: 700; color: #5A6472; font-size: 0.88rem; }

    /* POPUP */
    .overlay {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.5);
      z-index: 100;
      justify-content: center;
      align-items: flex-end;
      padding: 1rem;
    }
    .overlay.active { display: flex; }

    .popup {
      background: white;
      border-radius: 20px;
      padding: 1.5rem;
      width: 100%;
      max-width: 400px;
      margin-bottom: 1rem;
      animation: slideUp 0.25s ease;
    }
    @keyframes slideUp {
      from { transform: translateY(40px); opacity: 0; }
      to   { transform: translateY(0);   opacity: 1; }
    }

    .popup h3 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.4rem;
      letter-spacing: 1px;
      color: var(--navy);
      margin-bottom: 0.3rem;
    }
    .popup p {
      font-size: 0.85rem;
      color: #888;
      margin-bottom: 1.2rem;
    }

    .popup-btns { display: flex; flex-direction: column; gap: 0.7rem; }

    .btn-wa {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.6rem;
      padding: 0.9rem;
      border-radius: 12px;
      font-size: 1rem;
      font-weight: 700;
      cursor: pointer;
      border: none;
      background: #25D366;
      color: white;
      transition: opacity 0.15s;
    }
    .btn-gmail {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.6rem;
      padding: 0.9rem;
      border-radius: 12px;
      font-size: 1rem;
      font-weight: 700;
      cursor: pointer;
      border: none;
      background: var(--navy);
      color: white;
      transition: opacity 0.15s;
    }
    .btn-wa:hover, .btn-gmail:hover { opacity: 0.85; }

    .btn-cancel {
      background: none;
      border: none;
      color: #aaa;
      font-size: 0.9rem;
      cursor: pointer;
      padding: 0.5rem;
      text-align: center;
    }

    footer {
      background: var(--navy);
      color: white;
      text-align: center;
      padding: 2rem 1rem;
      margin-top: 1rem;
    }
    footer h2 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.8rem;
      letter-spacing: 2px;
      margin-bottom: 1rem;
      color: var(--orange);
    }
    .contact-info { display: flex; flex-wrap: wrap; justify-content: center; gap: 1.5rem; }
    .contact-item {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 1rem;
      font-weight: 500;
      color: white;
      text-decoration: none;
    }
    .contact-item:hover { opacity: 0.8; }
    .contact-item span.icon { font-size: 1.2rem; }

    @media (max-width: 500px) {
      .grid { padding: 1rem; }
      .price { font-size: 2.5rem; }
    }
  </style>
</head>
<body>

<header>
  <div class="header-icon">🚲</div>
  <h1>Tarifs & <span>Forfaits</span></h1>
  <p>Entretien & réparation vélo</p>
</header>

<p class="subtitle">👇 <strong>Appuyez sur une prestation</strong> pour envoyer une demande</p>

<div class="grid">

  <div class="card c-orange" onclick="openPopup('Nettoyage Express', '15€', '')">
    <div class="card-header">1 — Nettoyage Express <span class="tap-hint">📩 Réserver</span></div>
    <div class="card-body">
      <div class="price">15€</div>
      <ul>
        <li>Nettoyage rapide du cadre et des roues</li>
        <li>Gonflage des pneus</li>
        <li>Vérification rapide freins et vitesses</li>
        <li>Idéal avant balade</li>
      </ul>
    </div>
  </div>

  <div class="card c-navy" onclick="openPopup('Remise en route', '30€', '')">
    <div class="card-header">2 — Remise en route <span class="tap-hint">📩 Réserver</span></div>
    <div class="card-body">
      <div class="price">30€</div>
      <ul>
        <li>Nettoyage vélo & graissage chaîne</li>
        <li>Réglage freins & vitesses</li>
        <li>Gonflage des pneus</li>
        <li>Contrôle sécurité rapide</li>
      </ul>
    </div>
  </div>

  <div class="card c-green" onclick="openPopup('Entretien complet', '50€', '')">
    <div class="card-header">3 — Entretien complet <span class="tap-hint">📩 Réserver</span></div>
    <div class="card-body">
      <div class="price">50€</div>
      <ul>
        <li>Nettoyage complet & lubrification</li>
        <li>Réglages freins & vitesses</li>
        <li>Vérification câbles & durites</li>
        <li>Petites réparations incluses</li>
      </ul>
    </div>
  </div>

  <div class="card c-rust" onclick="openPopup('Entretien avancé', '70€', '')">
    <div class="card-header">4 — Entretien avancé <span class="tap-hint">📩 Réserver</span></div>
    <div class="card-body">
      <div class="price">70€</div>
      <ul>
        <li>Nettoyage approfondi & démontage roues</li>
        <li>Graissage axes & roulements</li>
        <li>Petites réparations incluses</li>
        <li>Ajustement fin dérailleurs</li>
        <li>Rapport & conseils vélo</li>
      </ul>
    </div>
  </div>

  <div class="card c-slate" onclick="openPopup('Lavage Pro', '60€', 'Option graissage chaîne +5€ : OUI / NON')">
    <div class="card-header">5 — Lavage Pro <span class="tap-hint">📩 Réserver</span></div>
    <div class="card-body">
      <div class="price">60€</div>
      <ul>
        <li>Lavage au karcher & dégraissage</li>
        <li>Rinçage et séchage à la main</li>
        <li>Parfait pour un coup de propre !</li>
      </ul>
      <p class="option-note">+ Option graissage chaîne : +5€</p>
    </div>
  </div>

  <div class="card c-gray" style="cursor:default;">
    <div class="card-header">6 — Prestations à la carte <span class="tap-hint">📩 Choisir</span></div>
    <div class="card-body">
      <div class="price">À partir de 15€</div>
      <div class="carte-item" onclick="event.stopPropagation(); openPopup('Réglage freins', '15€', '')">
        <span class="label">Réglage freins</span><span class="prix">15€</span>
      </div>
      <div class="carte-item" onclick="event.stopPropagation(); openPopup('Chambre à air', '20€ / pièce', 'Nombre de pièces : ')">
        <span class="label">Chambre à air</span><span class="prix">20€ / pièce</span>
      </div>
      <div class="carte-item" onclick="event.stopPropagation(); openPopup('Chaîne', '30€ / pièce', 'Nombre de pièces : ')">
        <span class="label">Chaîne</span><span class="prix">30€ / pièce</span>
      </div>
      <div class="carte-item" onclick="event.stopPropagation(); openPopup('Pneus complets', '35€ / pièce', 'Nombre de pièces : ')">
        <span class="label">Pneus complets</span><span class="prix">35€ / pièce</span>
      </div>
      <div class="carte-item" onclick="event.stopPropagation(); openPopup('Réglage dérailleur', '20€', '')">
        <span class="label">Réglage dérailleur</span><span class="prix">20€</span>
      </div>
    </div>
  </div>

</div>

<footer>
  <h2>Contactez-nous</h2>
  <div class="contact-info">
    <a class="contact-item" href="tel:0645557613">
      <span class="icon">📞</span>
      <span>06 45 55 76 13</span>
    </a>
    <a class="contact-item" href="mailto:theolebray@gmail.com">
      <span class="icon">✉️</span>
      <span>theolebray@gmail.com</span>
    </a>
  </div>
</footer>

<!-- POPUP -->
<div class="overlay" id="overlay" onclick="closePopup(event)">
  <div class="popup">
    <h3 id="popup-title"></h3>
    <p id="popup-price"></p>
    <div class="popup-btns">
      <button class="btn-wa" onclick="sendWhatsApp()">💬 WhatsApp</button>
      <button class="btn-gmail" onclick="sendGmail()">✉️ Gmail</button>
      <button class="btn-cancel" onclick="closeAll()">Annuler</button>
    </div>
  </div>
</div>

<script>
  const EMAIL = "theolebray@gmail.com";
  const PHONE = "33645557613"; // format international sans +

  let currentPrestation = '';
  let currentPrix = '';
  let currentExtra = '';

  function message(prestation, prix, extra) {
    return `Bonjour,\n\nJe souhaite réserver la prestation suivante :\n\n✅ ${prestation} – ${prix}${extra ? '\n' + extra : ''}\n\nMon prénom et nom : \nMon numéro de téléphone : \n\nMerci !`;
  }

  function openPopup(prestation, prix, extra) {
    currentPrestation = prestation;
    currentPrix = prix;
    currentExtra = extra;
    document.getElementById('popup-title').textContent = prestation;
    document.getElementById('popup-price').textContent = prix;
    document.getElementById('overlay').classList.add('active');
  }

  function closeAll() {
    document.getElementById('overlay').classList.remove('active');
  }

  function closePopup(e) {
    if (e.target === document.getElementById('overlay')) closeAll();
  }

  function sendWhatsApp() {
    const msg = message(currentPrestation, currentPrix, currentExtra);
    window.open(`https://wa.me/${PHONE}?text=${encodeURIComponent(msg)}`, '_blank');
    closeAll();
  }

  function sendGmail() {
    const sujet = `Demande – ${currentPrestation} (${currentPrix})`;
    const body = message(currentPrestation, currentPrix, currentExtra);
    const su = encodeURIComponent(sujet);
    const bo = encodeURIComponent(body);
    const to = encodeURIComponent(EMAIL);

    const isMobile = /Android|iPhone|iPad|iPod/i.test(navigator.userAgent);
    const isIOS = /iPhone|iPad|iPod/i.test(navigator.userAgent);

    if (!isMobile) {
      window.open(`https://mail.google.com/mail/?view=cm&fs=1&to=${to}&su=${su}&body=${bo}`, '_blank');
    } else if (isIOS) {
      const t = Date.now();
      window.location.href = `googlegmail://co?to=${to}&subject=${su}&body=${bo}`;
      setTimeout(() => {
        if (Date.now() - t < 1500) window.location.href = `mailto:${EMAIL}?subject=${su}&body=${bo}`;
      }, 800);
    } else {
      window.location.href = `intent://compose?to=${to}&subject=${su}&body=${bo}#Intent;scheme=googlegmail;package=com.google.android.gm;end`;
      setTimeout(() => {
        window.location.href = `mailto:${EMAIL}?subject=${su}&body=${bo}`;
      }, 1500);
    }
    closeAll();
  }
</script>

</body>
</html>
5).html…]()
