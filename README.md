#Get-your-certificate-
Get your participation certificate by name or registration 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Certificate of Participation</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #C9A84C;
    --gold-light: #E8C97A;
    --gold-dark: #9A7530;
    --cream: #FDF8EE;
    --deep: #1A1208;
    --ink: #2C2010;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #0e0b06;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-family: 'Montserrat', sans-serif;
    overflow-x: hidden;
  }

  /* Subtle grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
  }

  /* ─── FORM SECTION ─── */
  .form-section {
    position: relative;
    z-index: 10;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0;
    padding: 20px;
    width: 100%;
    max-width: 520px;
    animation: fadeUp 0.8s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .form-badge {
    font-family: 'Montserrat', sans-serif;
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 4px;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 12px;
    opacity: 0.8;
  }

  .form-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(28px, 6vw, 44px);
    color: var(--cream);
    text-align: center;
    line-height: 1.2;
    margin-bottom: 6px;
  }

  .form-title span {
    color: var(--gold);
    font-style: italic;
  }

  .form-subtitle {
    font-family: 'Cormorant Garamond', serif;
    font-size: 16px;
    color: rgba(253,248,238,0.5);
    text-align: center;
    margin-bottom: 40px;
    font-style: italic;
  }

  .input-group {
    position: relative;
    width: 100%;
    margin-bottom: 16px;
  }

  .input-group label {
    display: block;
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 3px;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .input-group input {
    width: 100%;
    padding: 16px 20px;
    background: rgba(201,168,76,0.05);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 2px;
    color: var(--cream);
    font-family: 'Cormorant Garamond', serif;
    font-size: 20px;
    font-weight: 300;
    letter-spacing: 1px;
    outline: none;
    transition: all 0.3s ease;
  }

  .input-group input::placeholder {
    color: rgba(253,248,238,0.2);
    font-style: italic;
  }

  .input-group input:focus {
    border-color: var(--gold);
    background: rgba(201,168,76,0.08);
    box-shadow: 0 0 0 1px rgba(201,168,76,0.3), 0 4px 24px rgba(201,168,76,0.08);
  }

  .divider-line {
    width: 100%;
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 8px 0 24px;
  }
  .divider-line::before, .divider-line::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(201,168,76,0.3), transparent);
  }
  .divider-dot {
    width: 4px; height: 4px;
    background: var(--gold);
    border-radius: 50%;
    opacity: 0.6;
  }

  .generate-btn {
    width: 100%;
    padding: 18px;
    background: linear-gradient(135deg, var(--gold-dark), var(--gold), var(--gold-light), var(--gold));
    background-size: 300% 300%;
    border: none;
    border-radius: 2px;
    color: var(--deep);
    font-family: 'Montserrat', sans-serif;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 4px;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.4s ease;
    animation: shimmer 4s ease infinite;
    position: relative;
    overflow: hidden;
  }

  @keyframes shimmer {
    0%, 100% { background-position: 0% 50%; }
    50%       { background-position: 100% 50%; }
  }

  .generate-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 32px rgba(201,168,76,0.4);
    letter-spacing: 5px;
  }

  .generate-btn:active { transform: translateY(0); }

  /* ─── CERTIFICATE OVERLAY ─── */
  #cert-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(10,8,3,0.9);
    z-index: 100;
    align-items: center;
    justify-content: center;
    padding: 20px;
    overflow-y: auto;
    animation: fadeIn 0.4s ease both;
  }

  @keyframes fadeIn {
    from { opacity: 0; } to { opacity: 1; }
  }

  #cert-overlay.active { display: flex; }

  .cert-wrapper {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    animation: scaleIn 0.5s cubic-bezier(0.34, 1.56, 0.64, 1) both;
  }

  @keyframes scaleIn {
    from { opacity: 0; transform: scale(0.85); }
    to   { opacity: 1; transform: scale(1); }
  }

  /* ─── THE CERTIFICATE ─── */
  #certificate {
    width: 800px;
    max-width: 100%;
    aspect-ratio: 1.414 / 1;
    background: var(--cream);
    position: relative;
    overflow: hidden;
    box-shadow: 0 40px 120px rgba(0,0,0,0.8), 0 0 0 1px rgba(201,168,76,0.3);
  }

  /* Parchment texture via gradient layers */
  #certificate::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse at 20% 20%, rgba(201,168,76,0.06) 0%, transparent 60%),
      radial-gradient(ellipse at 80% 80%, rgba(201,168,76,0.06) 0%, transparent 60%),
      radial-gradient(ellipse at 50% 50%, rgba(255,248,220,0.3) 0%, transparent 80%);
    pointer-events: none;
    z-index: 1;
  }

  /* Outer decorative border */
  .cert-border-outer {
    position: absolute;
    inset: 16px;
    border: 2px solid var(--gold);
    z-index: 2;
  }

  /* Inner decorative border */
  .cert-border-inner {
    position: absolute;
    inset: 22px;
    border: 1px solid rgba(201,168,76,0.4);
    z-index: 2;
  }

  /* Corner ornaments */
  .corner {
    position: absolute;
    width: 50px;
    height: 50px;
    z-index: 3;
  }
  .corner svg { width: 100%; height: 100%; }
  .corner-tl { top: 10px; left: 10px; }
  .corner-tr { top: 10px; right: 10px; transform: scaleX(-1); }
  .corner-bl { bottom: 10px; left: 10px; transform: scaleY(-1); }
  .corner-br { bottom: 10px; right: 10px; transform: scale(-1,-1); }

  .cert-content {
    position: relative;
    z-index: 4;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100%;
    padding: 50px 70px 40px;
    text-align: center;
  }

  /* Watermark */
  .cert-watermark {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 3;
    opacity: 0.04;
    pointer-events: none;
  }
  .cert-watermark svg {
    width: 60%;
    height: 60%;
  }

  .cert-top-ornament {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 6px;
  }
  .cert-top-ornament .line {
    width: 80px;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold));
  }
  .cert-top-ornament .line.r {
    background: linear-gradient(90deg, var(--gold), transparent);
  }
  .cert-top-ornament span {
    font-family: 'Cormorant Garamond', serif;
    font-size: 11px;
    letter-spacing: 5px;
    color: var(--gold-dark);
    text-transform: uppercase;
  }

  .cert-org {
    font-family: 'Montserrat', sans-serif;
    font-size: 9px;
    font-weight: 500;
    letter-spacing: 4px;
    color: var(--gold-dark);
    text-transform: uppercase;
    opacity: 0.8;
    margin-bottom: 12px;
  }

  .cert-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(26px, 5vw, 42px);
    color: var(--ink);
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    line-height: 1.1;
    margin-bottom: 4px;
  }

  .cert-of {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(16px, 3vw, 22px);
    color: var(--gold-dark);
    font-style: italic;
    letter-spacing: 4px;
    margin-bottom: 18px;
  }

  .cert-divider {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 14px;
    width: 70%;
  }
  .cert-divider::before, .cert-divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold-dark));
  }
  .cert-divider::after {
    background: linear-gradient(90deg, var(--gold-dark), transparent);
  }
  .cert-divider-diamond {
    width: 6px; height: 6px;
    background: var(--gold);
    transform: rotate(45deg);
  }

  .cert-presented {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(12px, 2.2vw, 16px);
    color: #6b5b35;
    letter-spacing: 2px;
    font-style: italic;
    margin-bottom: 10px;
  }

  .cert-name {
    font-family: 'Playfair Display', serif;
    font-size: clamp(28px, 6vw, 52px);
    color: var(--ink);
    font-weight: 400;
    font-style: italic;
    letter-spacing: 2px;
    line-height: 1.2;
    margin-bottom: 10px;
    position: relative;
  }

  .cert-name::after {
    content: '';
    display: block;
    width: 80%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    margin: 6px auto 0;
  }

  .cert-reg {
    font-family: 'Montserrat', sans-serif;
    font-size: 9px;
    font-weight: 400;
    letter-spacing: 3px;
    color: var(--gold-dark);
    text-transform: uppercase;
    margin-bottom: 14px;
    opacity: 0.7;
  }

  .cert-body {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(12px, 2vw, 15px);
    color: #5a4a28;
    line-height: 1.7;
    max-width: 80%;
    margin-bottom: 18px;
  }

  .cert-footer {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    width: 100%;
    padding: 0 20px;
    margin-top: auto;
  }

  .cert-sig-block {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
  }

  .cert-sig-line {
    width: 120px;
    height: 1px;
    background: var(--gold-dark);
    opacity: 0.6;
  }

  .cert-sig-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 8px;
    letter-spacing: 2px;
    color: #8b7340;
    text-transform: uppercase;
  }

  .cert-date-val {
    font-family: 'Cormorant Garamond', serif;
    font-size: 13px;
    color: #7a6535;
    font-style: italic;
  }

  .cert-seal {
    width: 80px;
    height: 80px;
    position: relative;
  }
  .cert-seal svg { width: 100%; height: 100%; }

  /* ─── BUTTONS BELOW CERT ─── */
  .cert-actions {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    justify-content: center;
  }

  .btn-action {
    padding: 13px 28px;
    border: 1px solid rgba(201,168,76,0.4);
    background: transparent;
    color: var(--cream);
    font-family: 'Montserrat', sans-serif;
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.3s ease;
    border-radius: 1px;
  }

  .btn-action:hover {
    background: rgba(201,168,76,0.1);
    border-color: var(--gold);
    color: var(--gold-light);
  }

  .btn-download {
    background: linear-gradient(135deg, var(--gold-dark), var(--gold));
    border-color: transparent;
    color: var(--deep);
  }

  .btn-download:hover {
    background: linear-gradient(135deg, var(--gold), var(--gold-light));
    color: var(--deep);
  }

  /* small screen */
  @media (max-width: 540px) {
    #certificate { width: 100%; aspect-ratio: 1.2 / 1; }
    .cert-content { padding: 30px 30px 24px; }
    .cert-footer { padding: 0 4px; gap: 6px; }
    .cert-seal { width: 56px; height: 56px; }
  }
</style>
</head>
<body>

<!-- FORM -->
<section class="form-section" id="form-section">
  <p class="form-badge">✦ Official Recognition ✦</p>
  <h1 class="form-title">Generate Your <span>Certificate</span></h1>
  <p class="form-subtitle">Enter your details to receive your certificate of participation</p>

  <div class="input-group">
    <label for="name-input">Full Name</label>
    <input type="text" id="name-input" placeholder="e.g. Alexandra Thornton" autocomplete="off" />
  </div>

  <div class="input-group">
    <label for="reg-input">Registration Number <span style="opacity:.5;font-size:9px">(optional)</span></label>
    <input type="text" id="reg-input" placeholder="e.g. REG-2024-0042" autocomplete="off" />
  </div>

  <div class="input-group">
    <label for="event-input">Event / Programme Name</label>
    <input type="text" id="event-input" placeholder="e.g. International Science Conference" autocomplete="off" />
  </div>

  <div class="divider-line"><div class="divider-dot"></div></div>

  <button class="generate-btn" onclick="generateCertificate()">
    ✦ &nbsp; Generate Certificate &nbsp; ✦
  </button>
</section>

<!-- CERTIFICATE OVERLAY -->
<div id="cert-overlay">
  <div class="cert-wrapper">

    <!-- THE CERTIFICATE -->
    <div id="certificate">

      <!-- Watermark -->
      <div class="cert-watermark">
        <svg viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="100" cy="100" r="90" stroke="#9A7530" stroke-width="2"/>
          <circle cx="100" cy="100" r="75" stroke="#9A7530" stroke-width="1"/>
          <text x="100" y="94" font-family="serif" font-size="18" text-anchor="middle" fill="#9A7530" font-style="italic">Certificate</text>
          <text x="100" y="116" font-family="serif" font-size="12" text-anchor="middle" fill="#9A7530" letter-spacing="4">of Participation</text>
          <line x1="30" y1="100" x2="70" y2="100" stroke="#9A7530" stroke-width="1"/>
          <line x1="130" y1="100" x2="170" y2="100" stroke="#9A7530" stroke-width="1"/>
        </svg>
      </div>

      <!-- Borders -->
      <div class="cert-border-outer"></div>
      <div class="cert-border-inner"></div>

      <!-- Corner ornaments -->
      <div class="corner corner-tl">
        <svg viewBox="0 0 50 50" fill="none"><path d="M5 45 L5 5 L45 5" stroke="#C9A84C" stroke-width="1.5"/><path d="M5 5 L18 18" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="5" r="3" fill="#C9A84C"/><circle cx="45" cy="5" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="45" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/></svg>
      </div>
      <div class="corner corner-tr">
        <svg viewBox="0 0 50 50" fill="none"><path d="M5 45 L5 5 L45 5" stroke="#C9A84C" stroke-width="1.5"/><path d="M5 5 L18 18" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="5" r="3" fill="#C9A84C"/><circle cx="45" cy="5" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="45" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/></svg>
      </div>
      <div class="corner corner-bl">
        <svg viewBox="0 0 50 50" fill="none"><path d="M5 45 L5 5 L45 5" stroke="#C9A84C" stroke-width="1.5"/><path d="M5 5 L18 18" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="5" r="3" fill="#C9A84C"/><circle cx="45" cy="5" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="45" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/></svg>
      </div>
      <div class="corner corner-br">
        <svg viewBox="0 0 50 50" fill="none"><path d="M5 45 L5 5 L45 5" stroke="#C9A84C" stroke-width="1.5"/><path d="M5 5 L18 18" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="5" r="3" fill="#C9A84C"/><circle cx="45" cy="5" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/><circle cx="5" cy="45" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/></svg>
      </div>

      <!-- Main content -->
      <div class="cert-content">
        <div class="cert-top-ornament">
          <span class="line"></span>
          <span>✦</span>
          <span class="line r"></span>
        </div>

        <p class="cert-org" id="cert-org-name">Organisation Name</p>

        <h2 class="cert-title">Certificate</h2>
        <p class="cert-of">of Participation</p>

        <div class="cert-divider"><div class="cert-divider-diamond"></div></div>

        <p class="cert-presented">This certificate is proudly presented to</p>

        <div class="cert-name" id="cert-display-name">Participant Name</div>
        <div class="cert-reg" id="cert-display-reg"></div>

        <p class="cert-body" id="cert-body-text">
          in recognition of their valuable participation and contribution to the event.
        </p>

        <div class="cert-footer">
          <div class="cert-sig-block">
            <div class="cert-sig-line"></div>
            <div class="cert-sig-label">Authorised Signatory</div>
          </div>

          <div class="cert-seal">
            <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
              <circle cx="50" cy="50" r="46" fill="none" stroke="#C9A84C" stroke-width="1.5"/>
              <circle cx="50" cy="50" r="38" fill="none" stroke="#C9A84C" stroke-width="0.8"/>
              <!-- star -->
              <polygon points="50,14 53,38 64,26 55,46 80,42 60,54 78,68 56,60 62,86 50,68 38,86 44,60 22,68 40,54 20,42 45,46 36,26 47,38" fill="#C9A84C" opacity="0.7"/>
              <circle cx="50" cy="50" r="12" fill="none" stroke="#C9A84C" stroke-width="1"/>
              <text x="50" y="54" font-family="serif" font-size="7" text-anchor="middle" fill="#9A7530" font-style="italic">Certified</text>
            </svg>
          </div>

          <div class="cert-sig-block">
            <div class="cert-date-val" id="cert-date-display"></div>
            <div class="cert-sig-label">Date of Issue</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Action buttons -->
    <div class="cert-actions">
      <button class="btn-action btn-download" onclick="downloadCertificate()">⬇ &nbsp; Download PNG</button>
      <button class="btn-action" onclick="printCertificate()">⎙ &nbsp; Print</button>
      <button class="btn-action" onclick="closeCertificate()">✕ &nbsp; Close</button>
    </div>

  </div>
</div>

<!-- html2canvas CDN -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

<script>
  function getOrdinal(d) {
    if (d > 3 && d < 21) return d + 'th';
    switch (d % 10) {
      case 1: return d + 'st';
      case 2: return d + 'nd';
      case 3: return d + 'rd';
      default: return d + 'th';
    }
  }

  function formatDate(date) {
    const months = ['January','February','March','April','May','June',
                    'July','August','September','October','November','December'];
    return getOrdinal(date.getDate()) + ' ' + months[date.getMonth()] + ' ' + date.getFullYear();
  }

  function generateCertificate() {
    const name = document.getElementById('name-input').value.trim();
    const reg  = document.getElementById('reg-input').value.trim();
    const event = document.getElementById('event-input').value.trim();

    if (!name) {
      document.getElementById('name-input').focus();
      document.getElementById('name-input').style.borderColor = '#e05a5a';
      setTimeout(() => document.getElementById('name-input').style.borderColor = '', 2000);
      return;
    }

    // Populate certificate
    document.getElementById('cert-display-name').textContent = name;

    if (reg) {
      document.getElementById('cert-display-reg').textContent = 'Registration No. ' + reg;
    } else {
      document.getElementById('cert-display-reg').textContent = '';
    }

    const eventLabel = event || 'The Programme';
    document.getElementById('cert-body-text').textContent =
      `in recognition of their valuable participation and outstanding contribution to "${eventLabel}". This achievement is a testament to their commitment and dedication.`;

   
