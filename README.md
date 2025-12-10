<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Rural Employment Helper - AI</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg-gradient: radial-gradient(circle at top left, #dbeafe 0, #eff6ff 35%, #f9fafb 100%);
      --primary: #2563eb;
      --primary-soft: #dbeafe;
      --primary-dark: #1d4ed8;
      --border-soft: #e5e7eb;
      --text-main: #0f172a;
      --text-muted: #6b7280;
      --card-bg: #ffffff;
      --danger-soft: #fef3c7;
      --danger-border: #fed7aa;
      --radius-lg: 18px;
      --radius-md: 12px;
      --radius-pill: 999px;
      --shadow-soft: 0 20px 45px rgba(15, 23, 42, 0.10);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: "Inter", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      min-height: 100vh;
      background: var(--bg-gradient);
      padding: 20px 12px 32px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* ---------------- GENERIC CARD SHELL ---------------- */
    .card-shell {
      width: 100%;
      max-width: 520px;
      background: linear-gradient(145deg, rgba(255,255,255,0.96), rgba(255,255,255,0.90));
      border-radius: 26px;
      box-shadow: var(--shadow-soft);
      border: 1px solid rgba(148, 163, 184, 0.25);
      padding: 22px 22px 18px;
      overflow: hidden;
    }

    /* ---------------- LOGIN SHELL ---------------- */
    #login-shell { }

    .login-badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 4px 10px;
      border-radius: var(--radius-pill);
      background: rgba(219, 234, 254, 0.8);
      color: #1d4ed8;
      font-size: 0.75rem;
      font-weight: 600;
      margin-bottom: 8px;
    }
    .login-dot {
      width: 7px; height: 7px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 0 4px rgba(34, 197, 94, 0.28);
    }

    #login-title {
      font-size: 1.5rem;
      color: var(--text-main);
      margin-bottom: 4px;
    }
    #login-subtitle {
      font-size: 0.9rem;
      color: var(--text-muted);
      margin-bottom: 14px;
    }

    .login-tabs {
      display: inline-flex;
      border-radius: 999px;
      background: #f1f5f9;
      padding: 3px;
      margin-bottom: 16px;
    }
    .login-tab {
      border-radius: 999px;
      padding: 7px 14px;
      font-size: 0.8rem;
      font-weight: 600;
      border: none;
      background: transparent;
      color: #64748b;
      cursor: pointer;
    }
    .login-tab.active {
      background: #ffffff;
      color: #111827;
      box-shadow: 0 4px 10px rgba(148,163,184,0.4);
    }

    .login-form {
      margin-top: 6px;
    }
    .login-field {
      margin-bottom: 10px;
    }
    .login-label {
      font-size: 0.78rem;
      font-weight: 600;
      margin-bottom: 4px;
      color: #0f172a;
    }
    .login-label span.req {
      color: #ef4444;
      margin-left: 2px;
    }
    .login-input-shell {
      border-radius: 999px;
      border: 1px solid var(--border-soft);
      background: #f9fafb;
      padding: 7px 11px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .login-input-shell input {
      border: none;
      background: transparent;
      outline: none;
      font-size: 0.88rem;
      width: 100%;
    }
    .login-icon {
      font-size: 1rem;
      opacity: 0.75;
    }

    .otp-row {
      display: flex;
      gap: 8px;
      align-items: center;
      margin-top: 6px;
    }
    .otp-row input {
      flex: 1;
      border-radius: 999px;
      border: 1px solid var(--border-soft);
      background: #f9fafb;
      padding: 7px 10px;
      font-size: 0.86rem;
      outline: none;
    }
    .otp-row input:focus {
      outline: 2px solid rgba(37, 99, 235, 0.3);
      outline-offset: 1px;
    }
    .otp-send-btn, .otp-verify-btn {
      border-radius: 999px;
      border: none;
      padding: 7px 11px;
      font-size: 0.8rem;
      cursor: pointer;
      font-weight: 600;
      white-space: nowrap;
    }
    .otp-send-btn {
      background: #e0f2fe;
      color: #0369a1;
    }
    .otp-send-btn:hover {
      background: #bae6fd;
    }
    .otp-verify-btn {
      background: #22c55e;
      color: white;
    }
    .otp-verify-btn:hover {
      background: #16a34a;
    }

    .otp-info {
      font-size: 0.75rem;
      color: #92400e;
      background: #fffbeb;
      border-radius: 10px;
      border: 1px dashed #facc15;
      padding: 6px 8px;
      margin-top: 6px;
    }

    .login-footer {
      margin-top: 10px;
      font-size: 0.75rem;
      color: var(--text-muted);
    }

    /* ---------------- VERIFICATION SHELL ---------------- */
    #verification-shell { display:none; }

    #verify-title {
      font-size: 1.4rem;
      color: var(--text-main);
      margin-bottom: 4px;
    }
    #verify-subtitle {
      font-size: 0.9rem;
      color: var(--text-muted);
      margin-bottom: 10px;
    }

    .verify-tagline {
      font-size: 0.8rem;
      color: var(--text-muted);
      margin-bottom: 12px;
    }

    .verify-label {
      font-size: 0.78rem;
      font-weight: 600;
      margin-bottom: 4px;
      color: #0f172a;
    }
    .verify-label span.req { color:#ef4444; margin-left:2px; }

    .verify-field { margin-bottom: 10px; }

    .verify-input-shell {
      border-radius: 999px;
      border: 1px solid var(--border-soft);
      background: #f9fafb;
      padding: 7px 11px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .verify-input-shell input,
    .verify-input-shell select {
      border:none;
      background:transparent;
      outline:none;
      font-size:0.88rem;
      width:100%;
    }

    .verify-file {
      width:100%;
      font-size:0.8rem;
      padding:6px 0;
    }

    .verify-info {
      font-size:0.73rem;
      color:#6b7280;
      margin-bottom:8px;
    }

    .verify-btn-row {
      text-align:right;
      margin-top:6px;
    }

    .verify-btn {
      border:none;
      border-radius:999px;
      padding:9px 16px;
      background: radial-gradient(circle at top left, #4ade80, #16a34a);
      color:white;
      font-size:0.9rem;
      font-weight:600;
      cursor:pointer;
      box-shadow:0 8px 16px rgba(22,163,74,0.4);
    }

    .verify-status {
      font-size:0.75rem;
      margin-top:6px;
      color:#15803d;
    }

    /* ---------------- MAIN APP SHELL ---------------- */
    .app-shell {
      width: 100%;
      max-width: 1040px;
      background: linear-gradient(145deg, rgba(255,255,255,0.96), rgba(255,255,255,0.90));
      border-radius: 28px;
      box-shadow: var(--shadow-soft);
      border: 1px solid rgba(148, 163, 184, 0.25);
      overflow: hidden;
      display: grid;
      grid-template-columns: minmax(0, 3fr) minmax(0, 4fr);
      margin: 0 auto;
    }

    .app-left {
      padding: 22px 24px 22px;
      border-right: 1px solid rgba(226, 232, 240, 0.8);
      background: radial-gradient(circle at top, rgba(219, 234, 254, 0.6), transparent 55%);
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 4px 10px;
      border-radius: var(--radius-pill);
      background: rgba(219, 234, 254, 0.7);
      color: #1d4ed8;
      font-size: 0.75rem;
      font-weight: 600;
      margin-bottom: 8px;
    }

    .badge-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 0 4px rgba(34, 197, 94, 0.25);
    }

    h1 {
      font-size: 1.6rem;
      line-height: 1.2;
      color: var(--text-main);
      margin-bottom: 4px;
    }

    .subtitle {
      font-size: 0.9rem;
      color: var(--text-muted);
      margin-bottom: 14px;
    }

    .lang-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      margin-bottom: 12px;
    }

    .lang-label {
      font-size: 0.8rem;
      color: var(--text-muted);
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .lang-label span.icon {
      font-size: 1rem;
    }

    .lang-select-wrap {
      background: #f8fafc;
      border-radius: 999px;
      padding: 4px 10px;
      border: 1px solid #e5e7eb;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    select#languageSelector {
      border: none;
      background: transparent;
      font-size: 0.82rem;
      outline: none;
      color: #111827;
      padding-right: 6px;
      cursor: pointer;
    }

    .small-hint {
      font-size: 0.75rem;
      color: var(--text-muted);
      margin-bottom: 16px;
    }
    .small-hint span {
      color: var(--primary);
      font-weight: 600;
    }

    form#userForm {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px 14px;
      margin-top: 6px;
    }

    .full {
      grid-column: 1 / 3;
    }

    .field-label {
      font-size: 0.78rem;
      font-weight: 600;
      color: #0f172a;
      margin-bottom: 4px;
      display: inline-block;
    }

    .field-label span.req {
      color: #ef4444;
      margin-left: 2px;
    }

    .input-shell {
      border-radius: 999px;
      border: 1px solid var(--border-soft);
      background: #f9fafb;
      padding: 7px 10px;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .input-icon {
      font-size: 1rem;
      opacity: 0.75;
    }

    input, select, textarea {
      width: 100%;
      border: none;
      outline: none;
      background: transparent;
      font-size: 0.88rem;
      color: #111827;
    }

    textarea {
      border-radius: 14px;
      padding: 10px 11px;
      min-height: 60px;
      resize: vertical;
      background: #f9fafb;
      border: 1px solid var(--border-soft);
    }

    textarea:focus, select:focus, input:focus {
      outline: 2px solid rgba(37, 99, 235, 0.3);
      outline-offset: 1px;
    }

    .mic-row {
      display: flex;
      justify-content: flex-end;
      gap: 6px;
      margin-top: 4px;
      margin-bottom: 2px;
    }

    .mic-btn {
      border-radius: 999px;
      border: 1px solid #dbeafe;
      background: #eff6ff;
      font-size: 0.75rem;
      padding: 4px 9px;
      display: inline-flex;
      align-items: center;
      gap: 4px;
      cursor: pointer;
      color: #1d4ed8;
    }

    .mic-btn span.icon {
      font-size: 0.9rem;
    }

    .btn-row {
      text-align: right;
      margin-top: 4px;
    }

    button.main-btn {
      border: none;
      border-radius: 999px;
      padding: 10px 18px;
      background: radial-gradient(circle at top left, #60a5fa, #2563eb);
      color: white;
      font-size: 0.9rem;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      cursor: pointer;
      box-shadow: 0 10px 20px rgba(37, 99, 235, 0.35);
      transition: transform 0.08s ease, box-shadow 0.08s ease, filter 0.08s ease;
    }
    .main-btn:hover {
      transform: translateY(-1px);
      filter: brightness(1.05);
      box-shadow: 0 14px 26px rgba(37, 99, 235, 0.40);
    }
    .main-btn:active {
      transform: translateY(0);
      box-shadow: 0 8px 16px rgba(37, 99, 235, 0.32);
    }
    .main-btn span.sparkle {
      font-size: 1.05rem;
    }

    .footnote {
      margin-top: 10px;
      font-size: 0.75rem;
      color: var(--text-muted);
    }
    .footnote span {
      font-weight: 600;
      color: #0f172a;
    }

    /* Right side – results */
    .app-right {
      padding: 22px 22px 18px;
      background: linear-gradient(160deg, #0b1120, #020617);
      color: #e5e7eb;
      position: relative;
      overflow: hidden;
    }

    .glow-circle {
      position: absolute;
      width: 260px;
      height: 260px;
      background: radial-gradient(circle, rgba(96, 165, 250, 0.32), transparent 60%);
      border-radius: 999px;
      top: -80px;
      right: -90px;
      pointer-events: none;
      filter: blur(1px);
    }

    .results-header {
      position: relative;
      z-index: 1;
      margin-bottom: 14px;
    }

    .results-chip {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 4px 10px;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.85);
      border: 1px solid rgba(148, 163, 184, 0.6);
      font-size: 0.75rem;
      color: #e5e7eb;
      margin-bottom: 6px;
    }

    .results-chip-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #22c55e;
    }

    #results_title {
      font-size: 1.05rem;
      font-weight: 600;
      margin-bottom: 2px;
    }

    #results_hint {
      font-size: 0.82rem;
      color: #9ca3af;
      margin-bottom: 10px;
    }

    .scroll-area {
      position: relative;
      z-index: 1;
      max-height: 380px;
      overflow-y: auto;
      padding-right: 4px;
    }
    .scroll-area::-webkit-scrollbar {
      width: 6px;
    }
    .scroll-area::-webkit-scrollbar-track {
      background: rgba(15,23,42,0.4);
      border-radius: 999px;
    }
    .scroll-area::-webkit-scrollbar-thumb {
      background: rgba(148, 163, 184, 0.8);
      border-radius: 999px;
    }

    .card {
      border-radius: var(--radius-md);
      border: 1px solid rgba(148, 163, 184, 0.55);
      background: linear-gradient(145deg, rgba(15, 23, 42, 0.95), rgba(17, 24, 39, 0.96));
      padding: 10px 11px 10px;
      margin-bottom: 10px;
    }

    .job-title {
      font-size: 0.94rem;
      font-weight: 600;
      color: #e5e7eb;
      margin-bottom: 4px;
    }

    .chip-row {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-bottom: 5px;
    }

    .tag {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      border-radius: 999px;
      padding: 2px 8px;
      font-size: 0.72rem;
      background: rgba(30, 64, 175, 0.7);
      color: #e5e7eb;
    }

    .tag.secondary {
      background: rgba(15, 118, 110, 0.75);
    }

    .tag-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: rgba(248, 250, 252, 0.9);
      opacity: 0.82;
    }

    .card-text {
      font-size: 0.82rem;
      color: #e5e7eb;
      opacity: 0.9;
      margin-bottom: 6px;
    }

    .score-bar {
      width: 100%;
      height: 6px;
      border-radius: 999px;
      background: rgba(30, 64, 175, 0.35);
      overflow: hidden;
      margin-top: 3px;
    }

    .score-fill {
      height: 100%;
      border-radius: 999px;
      background: linear-gradient(90deg, #4ade80, #22c55e, #a3e635);
      width: 0%;
      transition: width 0.5s ease-out;
    }

    .score-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 3px;
      font-size: 0.76rem;
      color: #9ca3af;
    }

    .score-row span.value {
      color: #e5e7eb;
      font-weight: 600;
    }

    .because-row {
      font-size: 0.76rem;
      color: #9ca3af;
      margin-top: 6px;
    }

    .because-row strong {
      color: #e5e7eb;
      font-weight: 600;
    }

    .no-results {
      background: rgba(251, 191, 36, 0.12);
      border-radius: var(--radius-md);
      border: 1px solid rgba(251, 191, 36, 0.55);
      padding: 9px 10px;
      font-size: 0.82rem;
      color: #fbbf24;
      margin-top: 4px;
    }

    .no-results ul {
      margin-top: 6px;
      padding-left: 18px;
      font-size: 0.78rem;
      color: #e5e7eb;
    }

    .watermark {
      position: absolute;
      bottom: 8px;
      right: 12px;
      font-size: 0.72rem;
      color: #6b7280;
      opacity: 0.6;
    }

    .user-pill {
      position: absolute;
      top: 10px;
      right: 14px;
      font-size: 0.74rem;
      color: #e5e7eb;
      background: rgba(15,23,42,0.8);
      border-radius: 999px;
      padding: 3px 9px;
      border: 1px solid rgba(148,163,184,0.7);
      z-index: 2;
    }

    /* Employer dashboard specific */
    .employer-subtitle {
      font-size: 0.9rem;
      color: var(--text-muted);
      margin-bottom: 12px;
    }
    .employer-tagline {
      font-size: 0.8rem;
      color: var(--text-muted);
      margin-bottom: 8px;
    }

    .job-list-empty {
      font-size: 0.82rem;
      color: #9ca3af;
    }

    @media (max-width: 880px) {
      .app-shell {
        grid-template-columns: minmax(0, 1fr);
      }
      .app-left {
        border-right: none;
        border-bottom: 1px solid rgba(226, 232, 240, 0.9);
        padding: 18px 16px 16px;
      }
      .app-right {
        padding: 18px 16px 14px;
      }
      body {
        padding: 14px 10px 22px;
      }
    }

    @media (max-width: 520px) {
      .app-shell {
        border-radius: 22px;
      }
      h1 {
        font-size: 1.35rem;
      }
      #login-title, #verify-title {
        font-size: 1.35rem;
      }
    }
  </style>
</head>
<body>

<!-- LOGIN SCREEN -->
<div id="login-shell" class="card-shell">
  <div class="login-badge">
    <span class="login-dot"></span>
    Secure Login · ग्रामीण / Rural Users
  </div>
  <h2 id="login-title">Welcome to Rural Employment Helper</h2>
  <p id="login-subtitle">
    Choose whether you are looking for work (Employee) or you have work to offer (Employer).
  </p>

  <div class="login-tabs">
    <button class="login-tab active" id="tab-employee" onclick="switchRole('employee')">Employee / Job Seeker</button>
    <button class="login-tab" id="tab-employer" onclick="switchRole('employer')">Employer / Business</button>
  </div>

  <!-- Employee Form -->
  <form class="login-form" id="form-employee" onsubmit="event.preventDefault();">
    <div class="login-field">
      <div class="login-label">Name <span class="req">*</span></div>
      <div class="login-input-shell">
        <span class="login-icon">👤</span>
        <input id="emp-name" placeholder="Your full name" required />
      </div>
    </div>

    <div class="login-field">
      <div class="login-label">Place (Village / Town) <span class="req">*</span></div>
      <div class="login-input-shell">
        <span class="login-icon">📍</span>
        <input id="emp-place" placeholder="Village / Town, District" required />
      </div>
    </div>

    <div class="login-field">
      <div class="login-label">Mobile Number <span class="req">*</span></div>
      <div class="login-input-shell">
        <span class="login-icon">📱</span>
        <input id="emp-mobile" placeholder="10-digit mobile" maxlength="10" />
      </div>

      <div class="otp-row">
        <input id="emp-otp" placeholder="Enter OTP" />
        <button type="button" class="otp-send-btn" onclick="sendOTP('employee')">Send OTP</button>
        <button type="button" class="otp-verify-btn" onclick="verifyOTP('employee')">Verify</button>
      </div>

      <div id="emp-otp-info" class="otp-info" style="display:none;"></div>
    </div>
  </form>

  <!-- Employer Form -->
  <form class="login-form" id="form-employer" style="display:none;" onsubmit="event.preventDefault();">
    <div class="login-field">
      <div class="login-label">Name <span class="req">*</span></div>
      <div class="login-input-shell">
        <span class="login-icon">👤</span>
        <input id="er-name" placeholder="Your full name" />
      </div>
    </div>

    <div class="login-field">
      <div class="login-label">Place (Village / Town) <span class="req">*</span></div>
      <div class="login-input-shell">
        <span class="login-icon">📍</span>
        <input id="er-place" placeholder="Village / Town, District" />
      </div>
    </div>

    <div class="login-field">
      <div class="login-label">Business Name <span class="req">*</span></div>
      <div class="login-input-shell">
        <span class="login-icon">🏪</span>
        <input id="er-business" placeholder="Shop / Farm / Company name" />
      </div>
    </div>

    <div class="login-field">
      <div class="login-label">Mobile Number <span class="req">*</span></div>
      <div class="login-input-shell">
        <span class="login-icon">📱</span>
        <input id="er-mobile" placeholder="10-digit mobile" maxlength="10" />
      </div>

      <div class="otp-row">
        <input id="er-otp" placeholder="Enter OTP" />
        <button type="button" class="otp-send-btn" onclick="sendOTP('employer')">Send OTP</button>
        <button type="button" class="otp-verify-btn" onclick="verifyOTP('employer')">Verify</button>
      </div>

      <div id="er-otp-info" class="otp-info" style="display:none;"></div>
    </div>
  </form>

  <div class="login-footer">
    Note: OTP here is for <strong>demo purpose</strong>. In real deployment, connect this to your SMS provider API.
  </div>
</div>

<!-- DOCUMENT VERIFICATION SCREEN -->
<div id="verification-shell" class="card-shell">
  <div class="login-badge">
    <span class="login-dot"></span>
    Step 2 · Document Verification
  </div>
  <h2 id="verify-title">Verify your identity</h2>
  <p id="verify-subtitle">
    For safety, we verify each user with one government ID before letting them use the platform.
  </p>
  <p class="verify-tagline" id="verify-user-line"></p>

  <form id="doc-form">
    <div class="verify-field">
      <div class="verify-label">Select Document Type <span class="req">*</span></div>
      <div class="verify-input-shell">
        <span class="login-icon">🪪</span>
        <select id="doc-type" required>
          <option value="">Choose Document</option>
          <option value="aadhaar">Aadhaar Card</option>
          <option value="pan">PAN Card</option>
          <option value="dl">Driving Licence</option>
          <option value="passport">Passport</option>
        </select>
      </div>
    </div>

    <div class="verify-field">
      <div class="verify-label">Document Number <span class="req">*</span></div>
      <div class="verify-input-shell">
        <span class="login-icon">#</span>
        <input id="doc-number" placeholder="Enter document number" required />
      </div>
    </div>

    <div class="verify-field">
      <div class="verify-label">Upload Document Photo (optional)</div>
      <input id="doc-file" type="file" class="verify-file" accept="image/*,application/pdf" />
      <div class="verify-info">
        For demo, we are <strong>not</strong> sending this anywhere. In real app, backend would handle secure verification.
      </div>
    </div>

    <div class="verify-field">
      <label style="font-size:0.78rem; display:flex; align-items:center; gap:6px;">
        <input type="checkbox" id="doc-consent" />
        I confirm that these details are correct and I agree to use them for verification.
      </label>
    </div>

    <div class="verify-btn-row">
      <button type="submit" class="verify-btn">Verify & Continue</button>
    </div>

    <div id="verify-status" class="verify-status"></div>
  </form>
</div>

<!-- MAIN APP (HIDDEN UNTIL VERIFICATION DONE) -->
<div id="main-app" style="display:none; width:100%;">
  <!-- EMPLOYEE APP -->
  <div id="employee-app">
    <div class="app-shell">
      <!-- LEFT: INPUT / FORM -->
      <section class="app-left">
        <div class="badge">
          <span class="badge-dot"></span>
          Simple AI job recommender for rural areas
        </div>

        <h1 id="title">Rural Employment Helper (AI)</h1>
        <p class="subtitle" id="subtitle">
          Enter basic details and our AI will highlight earning opportunities that fit your skills.
        </p>

        <div class="lang-row">
          <div class="lang-label">
            <span class="icon">🌐</span>
            <span>Language / भाषा / भाषा</span>
          </div>
          <div class="lang-select-wrap">
            <select id="languageSelector" onchange="setLanguage()">
              <option value="en">English</option>
              <option value="hi">हिंदी (Hindi)</option>
              <option value="mr">मराठी (Marathi)</option>
            </select>
          </div>
        </div>

        <p class="small-hint">
          Tip: write your <span>skills</span> like “typing, farming, tailoring, mobile repair” for better AI matching.
        </p>

        <form id="userForm">
          <div class="full">
            <label class="field-label" id="lbl_location">
              Location <span class="req">*</span>
            </label>
            <div class="input-shell">
              <span class="input-icon">📍</span>
              <input id="location" placeholder="Village / Town, District" required />
            </div>
          </div>

          <div>
            <label class="field-label" id="lbl_education">
              Education <span class="req">*</span>
            </label>
            <div class="input-shell">
              <span class="input-icon">🎓</span>
              <select id="education" required>
                <option value="">Select</option>
                <option value="10th">10th Pass</option>
                <option value="12th">12th Pass</option>
                <option value="iti">ITI / Diploma</option>
                <option value="graduate">Graduate</option>
              </select>
            </div>
          </div>

          <div class="full">
            <label class="field-label" id="lbl_skills">
              Skills (comma separated) <span class="req">*</span>
            </label>
            <textarea id="skills" placeholder="typing, farming, tailoring, driving, mobile repair..." required></textarea>
            <div class="mic-row">
              <button type="button" class="mic-btn" onclick="startVoiceInput('skills')">
                <span class="icon">🎤</span>
                <span>Speak skills</span>
              </button>
            </div>
          </div>

          <div class="full">
            <label class="field-label" id="lbl_interestText">
              Describe what kind of work you want (optional)
            </label>
            <textarea id="interestText" placeholder="e.g. work from home, teaching, start small business, field work"></textarea>
            <div class="mic-row">
              <button type="button" class="mic-btn" onclick="startVoiceInput('interestText')">
                <span class="icon">🎤</span>
                <span>Speak message</span>
              </button>
            </div>
          </div>

          <div class="full btn-row">
            <button type="submit" class="main-btn" id="btn_find">
              <span class="sparkle">✨</span>
              <span>Find AI Suggestions</span>
            </button>
          </div>
        </form>

        <p class="footnote">
          This project uses a simple <span>rule-based AI engine</span> in JavaScript — perfect for offline rural usage.
        </p>
      </section>

      <!-- RIGHT: AI RESULTS -->
      <section class="app-right">
        <div class="glow-circle"></div>
        <div class="user-pill" id="user-pill-employee"></div>

        <div class="results-header">
          <div class="results-chip">
            <span class="results-chip-dot"></span>
            Real-time AI matching
          </div>
          <p id="results_title">AI Suggestions will appear here</p>
          <p id="results_hint">
            Fill the form on the left and click the AI button. Top matches will be shown with a score and reason.
          </p>
        </div>

        <div class="scroll-area" id="results-content">
          <div class="no-results">
            No suggestions yet.
            <ul>
              <li>Write 2–5 clear skills you have.</li>
              <li>Mention what kind of work you prefer (online / offline / business).</li>
              <li>Then press “Find AI Suggestions”.</li>
            </ul>
          </div>
        </div>

        <div class="watermark">
          Rural Employment Helper · AI Prototype
        </div>
      </section>
    </div>
  </div>

  <!-- EMPLOYER APP -->
  <div id="employer-app" style="display:none;">
    <div class="app-shell">
      <!-- LEFT: business + post form -->
      <section class="app-left">
        <div class="badge">
          <span class="badge-dot"></span>
          Employer Dashboard · Hire locally
        </div>
        <h1 id="empDashTitle">Publish Hiring Posts</h1>
        <p class="employer-subtitle">
          Share details about your business and the workers you need. This helps nearby people find your jobs.
        </p>
        <p class="employer-tagline" id="empBusinessInfo"></p>

        <form id="employer-job-form">
          <div class="full">
            <label class="field-label">
              Job Title <span class="req">*</span>
            </label>
            <div class="input-shell">
              <span class="input-icon">💼</span>
              <input id="job-title" placeholder="e.g. Helper for dairy farm, Shop assistant" required />
            </div>
          </div>

          <div>
            <label class="field-label">
              Job Location <span class="req">*</span>
            </label>
            <div class="input-shell">
              <span class="input-icon">📍</span>
              <input id="job-location" placeholder="Village / Area" required />
            </div>
          </div>

          <div>
            <label class="field-label">
              Job Type <span class="req">*</span>
            </label>
            <div class="input-shell">
              <span class="input-icon">🕒</span>
             <select id="job-type" required>
                <option value="">Select Type</option>
                <option value="Full-time">Full-time</option>
                <option value="Part-time">Part-time</option>
                <option value="Daily Wage">Daily Wage / Contract</option>
              </select>
            </div>
          </div>

          <div class="full">
            <label class="field-label">
              Salary / Pay (approx) <span class="req">*</span>
            </label>
            <div class="input-shell">
              <span class="input-icon">💰</span>
              <input id="job-salary" placeholder="e.g. ₹8000/month, ₹400/day" required />
            </div>
          </div>

          <div class="full">
            <label class="field-label">
              Job Details / Requirements <span class="req">*</span>
            </label>
            <textarea id="job-details" placeholder="Work timing, skills needed, any special notes..." required></textarea>
            <div class="mic-row">
              <button type="button" class="mic-btn" onclick="startVoiceInput('job-details')">
                <span class="icon">🎤</span>
                <span>Speak details</span>
              </button>
            </div>
          </div>

          <div class="full btn-row">
            <button type="submit" class="main-btn">
              <span class="sparkle">📢</span>
              <span>Publish Hiring Post</span>
            </button>
          </div>
        </form>

        <p class="footnote">
          All posts stay in this browser only (demo). Real app would save to database and show to job seekers.
        </p>
      </section>

      <!-- RIGHT: list of posts -->
      <section class="app-right">
        <div class="glow-circle"></div>
        <div class="user-pill" id="user-pill-employer"></div>

        <div class="results-header">
          <div class="results-chip">
            <span class="results-chip-dot"></span>
            Your published hiring posts
          </div>
          <p id="empResultsTitle">Live openings from your business</p>
          <p id="empResultsHint">
            New posts will appear here. You can show this page to students / youth during awareness sessions.
          </p>
        </div>

        <div class="scroll-area" id="job-list">
          <p class="job-list-empty">
            No hiring posts yet. Create your first post using the form on the left.
          </p>
        </div>

        <div class="watermark">
          Rural Employment Helper · Employer View
        </div>
      </section>
    </div>
  </div>
</div>

<script>
  /* -------- GLOBAL LOGIN & DEMO/API TOGGLE -------- */
  const USE_DEMO_OTP = true; 
  // 🔁 When you connect a real SMS backend:
  // 1) Change this to false
  // 2) Implement fetch() calls in sendOTP() and verifyOTP() where commented

  let currentRole = 'employee';
  let employeeOTP = null;
  let employerOTP = null;
  let loggedInUser = { role: null, name: "", place: "", business: "" };
  let employerPosts = [];

  function switchRole(role) {
    currentRole = role;
    document.getElementById('tab-employee').classList.toggle('active', role === 'employee');
    document.getElementById('tab-employer').classList.toggle('active', role === 'employer');
    document.getElementById('form-employee').style.display = role === 'employee' ? 'block' : 'none';
    document.getElementById('form-employer').style.display = role === 'employer' ? 'block' : 'none';
  }

  async function sendOTP(role) {
    if (role === 'employee') {
      const mobile = document.getElementById('emp-mobile').value.trim();
      const info = document.getElementById('emp-otp-info');
      if (mobile.length !== 10) {
        info.style.display = 'block';
        info.innerText = "Please enter a valid 10-digit mobile number.";
        return;
      }

      if (USE_DEMO_OTP) {
        const otp = Math.floor(1000 + Math.random() * 9000);
        employeeOTP = otp;
        info.style.display = 'block';
        info.innerText = "Demo OTP for " + mobile + " is: " + otp + " (in real app this is sent via SMS).";
      } else {
        try {
          info.style.display = 'block';
          info.innerText = "Sending OTP via SMS...";
          // Example POST to your backend (Node/Express, etc.)
          /*
          const res = await fetch("https://your-backend-url.com/api/send-otp", {
            method:"POST",
            headers:{ "Content-Type":"application/json" },
            body: JSON.stringify({ mobile, role:"employee" })
          });
          const data = await res.json();
          if(data.success){
            info.innerText = "OTP sent via SMS to " + mobile;
          } else {
            info.innerText = "Failed to send OTP. " + (data.message || "");
          }
          */
          info.innerText = "Backend SMS API placeholder. Implement fetch() when ready.";
        } catch (err) {
          info.innerText = "Error contacting SMS API. Check network/backend.";
        }
      }

    } else {
      const mobile = document.getElementById('er-mobile').value.trim();
      const info = document.getElementById('er-otp-info');
      if (mobile.length !== 10) {
        info.style.display = 'block';
        info.innerText = "Please enter a valid 10-digit mobile number.";
        return;
      }

      if (USE_DEMO_OTP) {
        const otp = Math.floor(1000 + Math.random() * 9000);
        employerOTP = otp;
        info.style.display = 'block';
        info.innerText = "Demo OTP for " + mobile + " is: " + otp + " (in real app this is sent via SMS).";
      } else {
        try {
          info.style.display = 'block';
          info.innerText = "Sending OTP via SMS...";
          /*
          const res = await fetch("https://your-backend-url.com/api/send-otp", {
            method:"POST",
            headers:{ "Content-Type":"application/json" },
            body: JSON.stringify({ mobile, role:"employer" })
          });
          const data = await res.json();
          if(data.success){
            info.innerText = "OTP sent via SMS to " + mobile;
          } else {
            info.innerText = "Failed to send OTP. " + (data.message || "");
          }
          */
          info.innerText = "Backend SMS API placeholder. Implement fetch() when ready.";
        } catch (err) {
          info.innerText = "Error contacting SMS API. Check network/backend.";
        }
      }
    }
  }

  async function verifyOTP(role) {
    if (role === 'employee') {
      const entered = document.getElementById('emp-otp').value.trim();
      const info = document.getElementById('emp-otp-info');
      const name = document.getElementById('emp-name').value.trim();
      const place = document.getElementById('emp-place').value.trim();
      const mobile = document.getElementById('emp-mobile').value.trim();
      if (!name || !place) {
        info.style.display = 'block';
        info.innerText = "Please fill name and place.";
        return;
      }

      if (USE_DEMO_OTP) {
        if (entered === "" + employeeOTP && employeeOTP !== null) {
          info.style.display = 'block';
          info.innerText = "OTP verified successfully! Moving to document verification...";
          loggedInUser = { role: "Employee", name, place };
          setTimeout(() => goToVerificationStep(), 600);
        } else {
          info.style.display = 'block';
          info.innerText = "Incorrect OTP. Please try again or send a new OTP.";
        }
      } else {
        try {
          info.style.display = 'block';
          info.innerText = "Verifying OTP...";
          /*
          const res = await fetch("https://your-backend-url.com/api/verify-otp", {
            method:"POST",
            headers:{ "Content-Type":"application/json" },
            body: JSON.stringify({ mobile, otp: entered, role:"employee" })
          });
          const data = await res.json();
          if(data.success){
            loggedInUser = { role:"Employee", name, place };
            info.innerText = "OTP verified! Moving to document verification...";
            setTimeout(() => goToVerificationStep(), 600);
          } else {
            info.innerText = "OTP invalid. " + (data.message || "");
          }
          */
          info.innerText = "Backend OTP verification placeholder. Implement fetch() when ready.";
        } catch (err) {
          info.innerText = "Error contacting verify API.";
        }
      }

    } else {
      const entered = document.getElementById('er-otp').value.trim();
      const info = document.getElementById('er-otp-info');
      const name = document.getElementById('er-name').value.trim();
      const place = document.getElementById('er-place').value.trim();
      const business = document.getElementById('er-business').value.trim();
      const mobile = document.getElementById('er-mobile').value.trim();
      if (!name || !place || !business) {
        info.style.display = 'block';
        info.innerText = "Please fill name, place and business name.";
        return;
      }

      if (USE_DEMO_OTP) {
        if (entered === "" + employerOTP && employerOTP !== null) {
          info.style.display = 'block';
          info.innerText = "OTP verified successfully! Moving to document verification...";
          loggedInUser = { role: "Employer", name, place, business };
          setTimeout(() => goToVerificationStep(), 600);
        } else {
          info.style.display = 'block';
          info.innerText = "Incorrect OTP. Please try again or send a new OTP.";
        }
      } else {
        try {
          info.style.display = 'block';
          info.innerText = "Verifying OTP...";
          /*
          const res = await fetch("https://your-backend-url.com/api/verify-otp", {
            method:"POST",
            headers:{ "Content-Type":"application/json" },
            body: JSON.stringify({ mobile, otp: entered, role:"employer" })
          });
          const data = await res.json();
          if(data.success){
            loggedInUser = { role:"Employer", name, place, business };
            info.innerText = "OTP verified! Moving to document verification...";
            setTimeout(() => goToVerificationStep(), 600);
          } else {
            info.innerText = "OTP invalid. " + (data.message || "");
          }
          */
          info.innerText = "Backend OTP verification placeholder. Implement fetch() when ready.";
        } catch (err) {
          info.innerText = "Error contacting verify API.";
        }
      }
    }
  }

  /* -------- STEP: DOCUMENT VERIFICATION -------- */
  function goToVerificationStep() {
    document.getElementById("login-shell").style.display = "none";
    document.getElementById("verification-shell").style.display = "block";

    const line = document.getElementById("verify-user-line");
    if (loggedInUser.role === "Employee") {
      line.innerText = `Logged in as Employee: ${loggedInUser.name} (${loggedInUser.place})`;
    } else {
      line.innerText = `Logged in as Employer: ${loggedInUser.name} · ${loggedInUser.business} (${loggedInUser.place})`;
    }
  }

  document.getElementById("doc-form").addEventListener("submit", function(e) {
    e.preventDefault();
    const type = document.getElementById("doc-type").value;
    const num = document.getElementById("doc-number").value.trim();
    const consent = document.getElementById("doc-consent").checked;
    const status = document.getElementById("verify-status");

    if (!type || !num) {
      status.innerText = "Please select document type and enter document number.";
      status.style.color = "#b45309";
      return;
    }
    if (!consent) {
      status.innerText = "Please tick the consent checkbox before continue.";
      status.style.color = "#b45309";
      return;
    }

    // Basic format hint (JUST UI level, not real validation)
    if (type === "aadhaar" && num.replace(/\s+/g,"").length !== 12) {
      status.innerText = "Aadhaar number usually has 12 digits. Please re-check.";
      status.style.color = "#b45309";
      return;
    }

    status.style.color = "#15803d";
    status.innerText = "Document details accepted (demo). Opening your dashboard...";

    // In real app, send to backend for secure verification:
    // fetch("/api/verify-doc", { ... })

    setTimeout(() => {
      document.getElementById("verification-shell").style.display = "none";
      enterMainApp();
    }, 700);
  });

  function enterMainApp() {
    document.getElementById("main-app").style.display = "block";

    if (loggedInUser.role === "Employee") {
      document.getElementById("employee-app").style.display = "block";
      document.getElementById("employer-app").style.display = "none";
      document.getElementById("user-pill-employee").innerText =
        loggedInUser.role + ": " + loggedInUser.name + " (" + loggedInUser.place + ")";
    } else {
      document.getElementById("employee-app").style.display = "none";
      document.getElementById("employer-app").style.display = "block";
      document.getElementById("user-pill-employer").innerText =
        loggedInUser.role + ": " + loggedInUser.name;
      const bizInfo = document.getElementById("empBusinessInfo");
      bizInfo.innerText = `Business: ${loggedInUser.business} · Location: ${loggedInUser.place}`;
    }
  }

  /* -------- LANGUAGE & AI PART (EMPLOYEE SIDE) -------- */
  const lang = {
    en: {
      title: "Rural Employment Helper (AI)",
      subtitle: "Enter basic details and our AI will highlight earning opportunities that fit your skills.",
      location: "Location",
      education: "Education",
      skills: "Skills (comma separated)",
      interestText: "Describe what kind of work you want (optional)",
      btn: "Find AI Suggestions",
      results_title: "AI Based Suggestions",
      results_hint: "Fill the form on the left and click the AI button. Top matches will be shown with a score and reason.",
      no_result: "No strong matches found. Try adding more skills or changing your description.",
      because: "Because you mentioned:",
      score_label: "Match score"
    },
    hi: {
      title: "ग्रामीण रोजगार सहायक (AI)",
      subtitle: "अपनी बुनियादी जानकारी भरें और हमारा AI आपके कौशल के अनुसार रोजगार सुझाएगा।",
      location: "स्थान",
      education: "शिक्षा",
      skills: "कौशल (कॉमा से अलग करें)",
      interestText: "आप किस प्रकार का काम चाहते हैं? (ऐच्छिक)",
      btn: "AI सुझाव देखें",
      results_title: "AI आधारित सुझाव",
      results_hint: "बाईं ओर जानकारी भरें और AI बटन दबाएँ। ऊपर के मेल के साथ सुझाव दिखाए जाएँगे।",
      no_result: "कोई अच्छा मेल नहीं मिला। अपने कौशल या विवरण को थोड़ा बदलकर देखें।",
      because: "क्योंकि आपने ये कौशल लिखे:",
      score_label: "मेल प्रतिशत"
    },
    mr: {
      title: "ग्रामीण रोजगार सहाय्यक (AI)",
      subtitle: "आपली माहिती भरा आणि आमचा AI तुमच्या कौशल्यांनुसार रोजगार संधी दाखवेल.",
      location: "ठिकाण",
      education: "शिक्षण",
      skills: "कौशल्ये (स्वल्पविरामाने वेगळी करा)",
      interestText: "तुम्हाला कोणत्या प्रकारचे काम हवे आहे? (ऐच्छिक)",
      btn: "AI सुचवणी बघा",
      results_title: "AI आधारित सुचवणी",
      results_hint: "डावीकडे माहिती भरा आणि AI बटण दाबा. वरच्या जुळण्यानुसार सुचवणी दिसतील.",
      no_result: "चांगला मेळ सापडला नाही. कौशल्ये किंवा वर्णन थोडे बदलून पहा.",
      because: "कारण तुम्ही ही कौशल्ये लिहिली:",
      score_label: "जुळणारे टक्केवारी"
    }
  };

  function setLanguage() {
    const current = document.getElementById("languageSelector").value;
    const l = lang[current];

    document.getElementById("title").innerText = l.title;
    document.getElementById("subtitle").innerText = l.subtitle;
    document.getElementById("lbl_location").innerHTML = l.location + ' <span class="req">*</span>';
    document.getElementById("lbl_education").innerHTML = l.education + ' <span class="req">*</span>';
    document.getElementById("lbl_skills").innerHTML = l.skills + ' <span class="req">*</span>';
    document.getElementById("lbl_interestText").innerText = l.interestText;
    document.getElementById("btn_find").innerHTML =
      '<span class="sparkle">✨</span><span>' + l.btn + "</span>";
    document.getElementById("results_title").innerText = l.results_title;
    document.getElementById("results_hint").innerText = l.results_hint;
  }

  const opportunities = [
    {
      id: 1,
      title_en: "Online Data Entry (Work from Home)",
      title_hi: "ऑनलाइन डाटा एंट्री (घर से काम)",
      title_mr: "ऑनलाइन डेटा एंट्री (घरून काम)",
      type: "online",
      minEducation: "10th",
      keywords: ["typing","computer","excel","ms","word","online","data","entry","internet"],
      explain_en: "Simple data typing work using computer or mobile.",
      explain_hi: "कंप्यूटर या मोबाइल से सरल टाइपिंग का काम।",
      explain_mr: "कंप्यूटर किंवा मोबाईलवर साधे टायपिंगचे काम."
    },
    {
      id: 2,
      title_en: "Tailoring / Stitching Work",
      title_hi: "सिलाई / टेलरिंग काम",
      title_mr: "शिवणकाम / टेलरिंग",
      type: "offline",
      minEducation: "10th",
      keywords: ["tailoring","stitching","sewing","blouse","uniform","fall","pico"],
      explain_en: "Stitch clothes for school students and local people.",
      explain_hi: "स्थानीय लोगों और छात्रों के कपड़े सिलने का काम।",
      explain_mr: "स्थानिक लोकांसाठी आणि विद्यार्थ्यांसाठी कपडे शिवण्याचे काम."
    },
    {
      id: 3,
      title_en: "Organic Vegetable Farming & Selling",
      title_hi: "जैविक सब्जी खेती और बिक्री",
      title_mr: "सेंद्रिय भाजीपाला शेती व विक्री",
      type: "business",
      minEducation: "10th",
      keywords: ["farming","agriculture","vegetable","veg","organic","market","selling"],
      explain_en: "Grow vegetables and sell directly in local market.",
      explain_hi: "सब्ज़ियां उगाकर सीधे स्थानीय बाज़ार में बेचना।",
      explain_mr: "भाज्या पिकवून थेट स्थानिक बाजारात विक्री."
    },
    {
      id: 4,
      title_en: "Mobile Repairing Service",
      title_hi: "मोबाइल रिपेयरिंग सेवा",
      title_mr: "मोबाईल दुरुस्ती सेवा",
      type: "business",
      minEducation: "10th",
      keywords: ["mobile","repair","electronics","hardware","phone"],
      explain_en: "Repair basic mobile issues for local people.",
      explain_hi: "स्थानीय लोगों के मोबाइल की छोटी-मोटी खराबी ठीक करना।",
      explain_mr: "स्थानिक लोकांचे मोबाईलचे छोटे प्रश्न सोडवण्याचे काम."
    },
    {
      id: 5,
      title_en: "Tuition / Teaching (Local Area or Online)",
      title_hi: "ट्यूशन / शिक्षण कार्य",
      title_mr: "ट्युशन / शिकवणी",
      type: "online/offline",
      minEducation: "12th",
      keywords: ["teaching","tuition","maths","science","english","students","school"],
      explain_en: "Teach school children subjects you are strong in.",
      explain_hi: "स्कूल के बच्चों को वे विषय पढ़ाना जिसमें आप अच्छे हैं।",
      explain_mr: "शाळकरी मुलांना आपल्या मजबूत विषयांचे शिक्षण देणे."
    }
  ];

  const eduRank = { "10th": 1, "12th": 2, "iti": 2.5, "graduate": 3 };

  function normalizeText(str) {
    return str
      .toLowerCase()
      .replace(/[^a-z0-9\s]/g, " ")
      .split(/\s+/)
      .filter(Boolean);
  }

  function computeScore(userTokens, opp, userEduRank) {
    const oppSet = new Set(opp.keywords.map(k => k.toLowerCase()));
    let matchCount = 0;
    const matchedKeywords = [];

    userTokens.forEach(tok => {
      if (oppSet.has(tok) && !matchedKeywords.includes(tok)) {
        matchCount++;
        matchedKeywords.push(tok);
      }
    });

    let baseScore = 0;
    if (opp.keywords.length > 0) {
      baseScore = (matchCount / opp.keywords.length) * 100;
    }

    const oppEduRank = eduRank[opp.minEducation] || 1;
    if (userEduRank < oppEduRank) {
      baseScore *= 0.6;
    }

    baseScore = Math.max(0, Math.min(100, baseScore));
    return { score: Math.round(baseScore), matchedKeywords };
  }

  document.getElementById("userForm").addEventListener("submit", function (e) {
    e.preventDefault();

    const langKey = document.getElementById("languageSelector").value;
    const textPack = lang[langKey];

    const education = document.getElementById("education").value;
    const skills = document.getElementById("skills").value || "";
    const interestText = document.getElementById("interestText").value || "";
    const userEduRank = eduRank[education] || 1;

    const combinedText = skills + " " + interestText;
    const userTokens = normalizeText(combinedText);

    const resultsTitle = document.getElementById("results_title");
    const resultsHint = document.getElementById("results_hint");
    const resultsArea = document.getElementById("results-content");

    resultsTitle.innerText = textPack.results_title;
    resultsHint.innerText = textPack.results_hint;

    if (userTokens.length === 0) {
      resultsArea.innerHTML = `<div class="no-results">${textPack.no_result}</div>`;
      return;
    }

    const scored = opportunities
      .map(opp => ({
        opp,
        ...computeScore(userTokens, opp, userEduRank)
      }))
      .filter(obj => obj.score > 0)
      .sort((a, b) => b.score - a.score);

    if (scored.length === 0) {
      resultsArea.innerHTML = `<div class="no-results">${textPack.no_result}</div>`;
      return;
    }

    resultsArea.innerHTML = "";
    scored.slice(0, 3).forEach(item => {
      const opp = item.opp;
      const score = item.score;
      const matchedKeywords = item.matchedKeywords;

      const title =
        langKey === "hi" ? opp.title_hi :
        langKey === "mr" ? opp.title_mr :
        opp.title_en;

      const explain =
        langKey === "hi" ? opp.explain_hi :
        langKey === "mr" ? opp.explain_mr :
        opp.explain_en;

      const becauseLabel = textPack.because;
      const scoreLabel = textPack.score_label;

      const keywordsText = matchedKeywords.length ? matchedKeywords.join(", ") : "-";

      const card = document.createElement("div");
      card.className = "card";
      card.innerHTML = `
        <div class="job-title">${title}</div>
        <div class="chip-row">
          <span class="tag">
            <span class="tag-dot"></span>
            ${opp.type.toUpperCase()}
          </span>
          <span class="tag secondary">
            <span class="tag-dot"></span>
            Min: ${opp.minEducation}
          </span>
        </div>
        <p class="card-text">${explain}</p>
        <div class="score-bar">
          <div class="score-fill" style="width: ${score}%;"></div>
        </div>
        <div class="score-row">
          <span>${scoreLabel}</span>
          <span class="value">${score}%</span>
        </div>
        <div class="because-row">
          <strong>${becauseLabel}</strong> ${keywordsText}
        </div>
      `;
      resultsArea.appendChild(card);
    });
  });

  // ---------- EMPLOYER JOB POST HANDLING ----------
  function renderEmployerPosts() {
    const list = document.getElementById("job-list");
    if (employerPosts.length === 0) {
      list.innerHTML = `<p class="job-list-empty">
        No hiring posts yet. Create your first post using the form on the left.
      </p>`;
      return;
    }

    list.innerHTML = "";
    employerPosts.forEach((post, idx) => {
      const card = document.createElement("div");
      card.className = "card";
      card.innerHTML = `
        <div class="job-title">${post.title}</div>
        <div class="chip-row">
          <span class="tag">
            <span class="tag-dot"></span>
            ${post.type}
          </span>
          <span class="tag secondary">
            <span class="tag-dot"></span>
            ${post.location}
          </span>
        </div>
        <p class="card-text"><strong>Pay:</strong> ${post.salary}</p>
        <p class="card-text">${post.details}</p>
        <div class="score-row">
          <span>Post #${idx + 1}</span>
          <span class="value">${loggedInUser.business || "Your business"}</span>
        </div>
      `;
      list.appendChild(card);
    });
  }

  document.getElementById("employer-job-form").addEventListener("submit", function(e) {
    e.preventDefault();
    const title = document.getElementById("job-title").value.trim();
    const location = document.getElementById("job-location").value.trim();
    const type = document.getElementById("job-type").value;
    const salary = document.getElementById("job-salary").value.trim();
    const details = document.getElementById("job-details").value.trim();

    if (!title || !location || !type || !salary || !details) {
      alert("Please fill all job details.");
      return;
    }

    employerPosts.push({ title, location, type, salary, details });
    renderEmployerPosts();

    document.getElementById("job-title").value = "";
    document.getElementById("job-location").value = "";
    document.getElementById("job-type").value = "";
    document.getElementById("job-salary").value = "";
    document.getElementById("job-details").value = "";
  });

  // ---------- VOICE INPUT (MIC) ----------
  let recognition = null;
  function getCurrentSpeechLang() {
    const selector = document.getElementById("languageSelector");
    const current = selector ? selector.value : "en";
    if (current === "hi") return "hi-IN";
    if (current === "mr") return "mr-IN";
    return "en-IN";
  }

  function startVoiceInput(targetId) {
    if (!('webkitSpeechRecognition' in window || 'SpeechRecognition' in window)) {
      alert("Voice input not supported in this browser. Try using Chrome on Android.");
      return;
    }
    const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
    recognition = new SpeechRecognition();
    recognition.lang = getCurrentSpeechLang();
    recognition.interimResults = false;
    recognition.maxAlternatives = 1;

    const target = document.getElementById(targetId);
    recognition.onresult = function(event) {
      const transcript = event.results[0][0].transcript;
      if (target.value.length > 0) {
        target.value += ", " + transcript;
      } else {
        target.value = transcript;
      }
    };
    recognition.onerror = function() {
      alert("Sorry, could not capture your voice. Please try again.");
    };
    recognition.start();
  }

  // init language for employee side
  setLanguage();
</script>
</body>
</html>
