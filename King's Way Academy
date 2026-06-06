<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>King's Way Academy – Portal</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --navy: #0a1f44; --blue: #1a56db; --gold: #f59e0b;
      --brown: #7c4a2d; --dark-brown: #3b1f0e;
      --pale: #f0f6ff; --white: #fff;
      --text: #1e293b; --muted: #64748b;
      --bg: #f8fafc; --card: #fff;
      --border: #e2e8f0; --shadow: rgba(10,31,68,0.10);
      --success: #10b981; --danger: #ef4444; --warning: #f59e0b;
    }
    [data-theme="dark"] {
      --bg: #0a1628; --card: #132040; --border: #1e3a6e;
      --text: #e2e8f0; --muted: #94a3b8; --pale: #0f1f3d;
      --shadow: rgba(0,0,0,0.4); --white: #0a1628;
    }

    html { scroll-behavior: smooth; }
    body { font-family: 'DM Sans', sans-serif; background: var(--bg); color: var(--text); min-height: 100vh; transition: background 0.3s, color 0.3s; }

    /* ── PAGES ── */
    .page { display: none; min-height: 100vh; }
    .page.active { display: flex; }

    /* ══════════════════════════════
       LOGIN PAGE
    ══════════════════════════════ */
    #loginPage {
      background:
        linear-gradient(135deg, rgba(10,31,68,0.95) 0%, rgba(26,86,219,0.80) 100%),
        url('https://images.unsplash.com/photo-1580582932707-520aed937b7b?w=1600&q=80') center/cover no-repeat;
      align-items: center; justify-content: center;
      flex-direction: column; padding: 24px; position: relative; overflow: hidden;
    }
    #loginPage canvas { position:absolute; inset:0; pointer-events:none; z-index:0; }

    .login-box {
      position: relative; z-index: 1;
      background: rgba(255,255,255,0.07);
      backdrop-filter: blur(20px);
      border: 1px solid rgba(255,255,255,0.15);
      border-radius: 20px; padding: 48px 44px;
      width: 100%; max-width: 440px;
      box-shadow: 0 32px 80px rgba(0,0,0,0.4);
      animation: popIn 0.6s cubic-bezier(.34,1.56,.64,1) both;
    }
    .login-logo { text-align: center; margin-bottom: 28px; }
    .login-logo img { width: 90px; height: 90px; object-fit: contain; filter: drop-shadow(0 4px 16px rgba(0,0,0,0.5)); }
    .login-title { font-family:'Playfair Display',serif; font-size:1.6rem; font-weight:900; color:#fff; text-align:center; margin-bottom:4px; }
    .login-sub { font-size:13px; color:rgba(255,255,255,0.6); text-align:center; margin-bottom:32px; letter-spacing:0.5px; }

    .role-tabs { display:flex; gap:8px; margin-bottom:28px; background:rgba(255,255,255,0.08); border-radius:10px; padding:4px; }
    .role-tab {
      flex:1; padding:10px; border:none; border-radius:8px;
      font-family:'DM Sans',sans-serif; font-size:13px; font-weight:600;
      cursor:pointer; color:rgba(255,255,255,0.6); background:transparent;
      transition:all 0.2s; letter-spacing:0.3px;
    }
    .role-tab.active { background:var(--gold); color:#0a1f44; }

    .form-group { margin-bottom:16px; }
    .form-group label { font-size:12px; font-weight:600; color:rgba(255,255,255,0.75); letter-spacing:0.5px; text-transform:uppercase; display:block; margin-bottom:8px; }
    .form-group input {
      width:100%; padding:13px 16px;
      background:rgba(255,255,255,0.10); border:1.5px solid rgba(255,255,255,0.15);
      border-radius:8px; font-family:'DM Sans',sans-serif; font-size:14px;
      color:#fff; outline:none; transition:border-color 0.2s, background 0.2s;
    }
    .form-group input::placeholder { color:rgba(255,255,255,0.35); }
    .form-group input:focus { border-color:var(--gold); background:rgba(255,255,255,0.15); }
    .login-error {
      background:rgba(239,68,68,0.2); border:1px solid rgba(239,68,68,0.4);
      color:#fca5a5; font-size:13px; padding:10px 14px; border-radius:8px;
      margin-bottom:16px; display:none;
    }
    .login-error.show { display:block; }
    .btn-login {
      width:100%; padding:14px; background:var(--gold); color:#0a1f44;
      border:none; border-radius:8px; font-family:'DM Sans',sans-serif;
      font-size:15px; font-weight:700; cursor:pointer; letter-spacing:0.5px;
      transition:all 0.2s; margin-top:4px;
    }
    .btn-login:hover { background:#d97706; transform:translateY(-1px); box-shadow:0 8px 24px rgba(245,158,11,0.35); }
    .login-hint { font-size:12px; color:rgba(255,255,255,0.4); text-align:center; margin-top:20px; line-height:1.6; }
    .login-hint b { color:rgba(255,255,255,0.7); }

    /* ══════════════════════════════
       APP SHELL (after login)
    ══════════════════════════════ */
    #appPage { flex-direction:row; }

    /* SIDEBAR */
    .sidebar {
      width: 260px; flex-shrink:0;
      background: var(--navy); min-height:100vh;
      display:flex; flex-direction:column;
      transition: width 0.3s, transform 0.3s;
      position: relative; z-index: 50;
    }
    [data-theme="dark"] .sidebar { background:#060f22; }

    .sidebar-header {
      padding:24px 20px; border-bottom:1px solid rgba(255,255,255,0.08);
      display:flex; align-items:center; gap:12px;
    }
    .sidebar-logo { width:40px; height:40px; object-fit:contain; flex-shrink:0; }
    .sidebar-school { line-height:1.2; }
    .sidebar-name { font-family:'Playfair Display',serif; font-size:13px; font-weight:700; color:#fff; }
    .sidebar-motto { font-size:10px; color:var(--gold); letter-spacing:1px; }

    .sidebar-user {
      margin:16px; background:rgba(255,255,255,0.06);
      border-radius:10px; padding:14px;
      display:flex; align-items:center; gap:12px;
    }
    .user-avatar {
      width:40px; height:40px; border-radius:50%;
      display:flex; align-items:center; justify-content:center;
      font-size:16px; font-weight:700; flex-shrink:0;
      color:#fff;
    }
    .user-name { font-size:13px; font-weight:600; color:#fff; }
    .user-role { font-size:11px; color:rgba(255,255,255,0.5); text-transform:uppercase; letter-spacing:0.8px; margin-top:2px; }
    .user-badge {
      margin-left:auto; font-size:10px; font-weight:600; padding:3px 8px;
      border-radius:20px; letter-spacing:0.5px;
    }

    .sidebar-nav { flex:1; padding:8px 12px; overflow-y:auto; }
    .nav-section-label { font-size:10px; color:rgba(255,255,255,0.35); letter-spacing:2px; text-transform:uppercase; padding:16px 8px 8px; }
    .nav-item {
      display:flex; align-items:center; gap:12px;
      padding:11px 12px; border-radius:8px; margin-bottom:2px;
      cursor:pointer; color:rgba(255,255,255,0.65); font-size:14px; font-weight:500;
      transition:all 0.2s; text-decoration:none;
    }
    .nav-item:hover { background:rgba(255,255,255,0.08); color:#fff; }
    .nav-item.active { background:var(--gold); color:#0a1f44; font-weight:600; }
    .nav-item .nav-icon { font-size:18px; width:24px; text-align:center; flex-shrink:0; }
    .nav-badge {
      margin-left:auto; background:var(--danger); color:#fff;
      font-size:10px; font-weight:700; padding:2px 7px; border-radius:20px;
    }

    .sidebar-footer {
      padding:16px; border-top:1px solid rgba(255,255,255,0.08);
    }
    .btn-logout {
      width:100%; padding:11px; background:rgba(239,68,68,0.15);
      border:1px solid rgba(239,68,68,0.3); color:#fca5a5;
      border-radius:8px; font-family:'DM Sans',sans-serif;
      font-size:13px; font-weight:600; cursor:pointer; transition:all 0.2s;
    }
    .btn-logout:hover { background:rgba(239,68,68,0.25); }

    /* MAIN CONTENT */
    .main {
      flex:1; display:flex; flex-direction:column;
      min-height:100vh; overflow:hidden;
    }

    /* TOP BAR */
    .topbar {
      height:64px; background:var(--card);
      border-bottom:1px solid var(--border);
      display:flex; align-items:center; padding:0 28px;
      gap:16px; flex-shrink:0;
      box-shadow:0 1px 4px var(--shadow);
    }
    .topbar-title { font-family:'Playfair Display',serif; font-size:1.2rem; font-weight:700; color:var(--navy); flex:1; }
    [data-theme="dark"] .topbar-title { color:#e2e8f0; }
    .topbar-date { font-size:13px; color:var(--muted); }

    .theme-btn {
      width:36px; height:36px; border-radius:50%;
      background:var(--pale); border:1px solid var(--border);
      cursor:pointer; font-size:16px; display:flex; align-items:center; justify-content:center;
      transition:background 0.2s;
    }
    .theme-btn:hover { background:var(--border); }

    /* CONTENT AREA */
    .content { flex:1; padding:28px; overflow-y:auto; }

    /* ── DASHBOARD PANELS ── */
    .panel { display:none; }
    .panel.active { display:block; animation: fadeIn 0.4s ease both; }

    /* STAT CARDS */
    .stats-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr)); gap:18px; margin-bottom:28px; }
    .stat-card {
      background:var(--card); border-radius:12px; padding:22px 20px;
      border:1px solid var(--border); position:relative; overflow:hidden;
      transition:transform 0.2s, box-shadow 0.2s;
    }
    .stat-card:hover { transform:translateY(-3px); box-shadow:0 12px 32px var(--shadow); }
    .stat-card-icon { font-size:28px; margin-bottom:12px; }
    .stat-card-num { font-family:'Playfair Display',serif; font-size:2rem; font-weight:900; color:var(--navy); line-height:1; }
    [data-theme="dark"] .stat-card-num { color:#e2e8f0; }
    .stat-card-label { font-size:13px; color:var(--muted); margin-top:4px; }
    .stat-card-bar {
      position:absolute; bottom:0; left:0; right:0; height:4px;
    }

    /* GRID 2-COL */
    .grid-2 { display:grid; grid-template-columns:1fr 1fr; gap:20px; }
    @media(max-width:900px){ .grid-2 { grid-template-columns:1fr; } }

    /* CARD */
    .card {
      background:var(--card); border-radius:12px;
      border:1px solid var(--border); overflow:hidden;
      margin-bottom:20px;
    }
    .card-header {
      padding:18px 20px; border-bottom:1px solid var(--border);
      display:flex; align-items:center; justify-content:space-between;
    }
    .card-title { font-weight:700; color:var(--navy); font-size:15px; }
    [data-theme="dark"] .card-title { color:#e2e8f0; }
    .card-body { padding:20px; }

    /* TABLE */
    .data-table { width:100%; border-collapse:collapse; font-size:13px; }
    .data-table th { text-align:left; padding:10px 14px; font-size:11px; text-transform:uppercase; letter-spacing:0.8px; color:var(--muted); border-bottom:1px solid var(--border); }
    .data-table td { padding:12px 14px; border-bottom:1px solid var(--border); color:var(--text); }
    .data-table tr:last-child td { border-bottom:none; }
    .data-table tr:hover td { background:var(--pale); }

    /* BADGE */
    .badge { display:inline-block; padding:3px 10px; border-radius:20px; font-size:11px; font-weight:600; }
    .badge-green { background:#d1fae5; color:#065f46; }
    .badge-blue  { background:#dbeafe; color:#1e40af; }
    .badge-gold  { background:#fef3c7; color:#92400e; }
    .badge-red   { background:#fee2e2; color:#991b1b; }
    [data-theme="dark"] .badge-green { background:#064e3b; color:#6ee7b7; }
    [data-theme="dark"] .badge-blue  { background:#1e3a5f; color:#93c5fd; }
    [data-theme="dark"] .badge-gold  { background:#451a03; color:#fcd34d; }
    [data-theme="dark"] .badge-red   { background:#450a0a; color:#fca5a5; }

    /* TIMETABLE */
    .timetable { display:grid; grid-template-columns:80px repeat(5,1fr); gap:6px; font-size:12px; }
    .tt-head { background:var(--navy); color:#fff; padding:8px; border-radius:6px; text-align:center; font-weight:600; font-size:11px; }
    [data-theme="dark"] .tt-head { background:#1e3a6e; }
    .tt-time { background:var(--pale); padding:8px; border-radius:6px; text-align:center; color:var(--muted); font-weight:600; display:flex; align-items:center; justify-content:center; }
    .tt-cell {
      padding:10px 8px; border-radius:6px; text-align:center;
      font-weight:500; line-height:1.3; display:flex; align-items:center; justify-content:center; min-height:52px;
    }
    .tt-math    { background:#dbeafe; color:#1e40af; }
    .tt-english { background:#d1fae5; color:#065f46; }
    .tt-science { background:#fce7f3; color:#9d174d; }
    .tt-social  { background:#fef3c7; color:#92400e; }
    .tt-comp    { background:#ede9fe; color:#5b21b6; }
    .tt-arts    { background:#ffedd5; color:#9a3412; }
    .tt-pe      { background:#ecfccb; color:#365314; }
    .tt-break   { background:var(--pale); color:var(--muted); font-style:italic; }
    [data-theme="dark"] .tt-math    { background:#1e3a5f; color:#93c5fd; }
    [data-theme="dark"] .tt-english { background:#064e3b; color:#6ee7b7; }
    [data-theme="dark"] .tt-science { background:#4a044e; color:#f0abfc; }
    [data-theme="dark"] .tt-social  { background:#451a03; color:#fcd34d; }
    [data-theme="dark"] .tt-comp    { background:#2e1065; color:#c4b5fd; }
    [data-theme="dark"] .tt-arts    { background:#431407; color:#fdba74; }
    [data-theme="dark"] .tt-pe      { background:#1a2e05; color:#a3e635; }
    [data-theme="dark"] .tt-break   { background:var(--pale); color:var(--muted); }

    /* GRADES CHART */
    .grade-bars { display:flex; flex-direction:column; gap:14px; }
    .grade-row { display:flex; align-items:center; gap:12px; }
    .grade-subject { width:110px; font-size:13px; color:var(--text); flex-shrink:0; }
    .grade-bar-wrap { flex:1; background:var(--pale); border-radius:20px; height:10px; overflow:hidden; }
    .grade-bar { height:100%; border-radius:20px; transition:width 1s ease; }
    .grade-score { width:36px; font-size:13px; font-weight:700; color:var(--navy); text-align:right; flex-shrink:0; }
    [data-theme="dark"] .grade-score { color:#e2e8f0; }

    /* NOTICES */
    .notice-list { display:flex; flex-direction:column; gap:12px; }
    .notice-item {
      padding:14px 16px; border-radius:10px;
      border-left:4px solid; background:var(--pale);
    }
    .notice-item.info  { border-color:var(--blue); }
    .notice-item.warn  { border-color:var(--gold); }
    .notice-item.alert { border-color:var(--danger); }
    .notice-title { font-weight:600; font-size:14px; color:var(--navy); margin-bottom:4px; }
    [data-theme="dark"] .notice-title { color:#e2e8f0; }
    .notice-date { font-size:11px; color:var(--muted); }

    /* PROFILE FORM */
    .profile-grid { display:grid; grid-template-columns:1fr 1fr; gap:16px; }
    .p-group { display:flex; flex-direction:column; gap:6px; }
    .p-group label { font-size:12px; font-weight:600; color:var(--muted); text-transform:uppercase; letter-spacing:0.5px; }
    .p-group input, .p-group select {
      padding:11px 14px; border:1.5px solid var(--border);
      border-radius:8px; font-family:'DM Sans',sans-serif;
      font-size:14px; color:var(--text); background:var(--card);
      outline:none; transition:border-color 0.2s;
    }
    .p-group input:focus, .p-group select:focus { border-color:var(--blue); }
    .btn-save {
      padding:12px 28px; background:var(--navy); color:#fff;
      border:none; border-radius:8px; font-family:'DM Sans',sans-serif;
      font-size:14px; font-weight:600; cursor:pointer; margin-top:8px;
      transition:all 0.2s;
    }
    .btn-save:hover { background:var(--blue); transform:translateY(-1px); }

    /* MOBILE SIDEBAR TOGGLE */
    .sidebar-toggle {
      display:none; background:none; border:none;
      font-size:22px; cursor:pointer; color:var(--text); margin-right:8px;
    }
    .sidebar-overlay {
      display:none; position:fixed; inset:0;
      background:rgba(0,0,0,0.5); z-index:40;
    }
    .sidebar-overlay.show { display:block; }

    @media(max-width:768px){
      .sidebar { position:fixed; top:0; left:0; bottom:0; transform:translateX(-100%); }
      .sidebar.open { transform:translateX(0); }
      .sidebar-toggle { display:block; }
      .content { padding:16px; }
      .timetable { grid-template-columns:60px repeat(5,1fr); font-size:10px; }
      .profile-grid { grid-template-columns:1fr; }
    }

    /* ANIMATIONS */
    @keyframes popIn { from{opacity:0;transform:scale(0.9);} to{opacity:1;transform:scale(1);} }
    @keyframes fadeIn { from{opacity:0;transform:translateY(12px);} to{opacity:1;transform:translateY(0);} }
  </style>
</head>
<body>

<!-- ══════════════ LOGIN PAGE ══════════════ -->
<div class="page active" id="loginPage">
  <canvas id="pCanvas"></canvas>
  <div class="login-box">
    <div class="login-logo">
      <img src="data:image/jpeg;base64,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
