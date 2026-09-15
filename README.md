<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Brain &amp; Mind Academy • DHANANJAYA - Calculus I: Continuity</title>

  <!-- MathJax Configuration & Loader -->
  <script>
    window.MathJax = {
      tex: {
        inlineMath: [['\\(', '\\)'], ['$', '$']],
        displayMath: [['\\[', '\\]'], ['$$', '$$']],
        processEscapes: true
      },
      svg: { fontCache: 'global' }
    };
  </script>
  <script type="text/javascript" id="MathJax-script" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>

  <style>
    :root {
      --navy-dark: #0c4a6e;
      --brand-blue: #0284c7;
      --accent-cyan: #0ea5e9;
      --bg-tint: #f0f9ff;
      --card-surf: #ffffff;
      --border-accent: #7dd3fc;
      --border-soft: #bae6fd;
      --green-ok: #059669;
      --green-surf: #d1fae5;
      --red-fail: #dc2626;
      --red-surf: #fee2e2;
      --brand-gold: #f59e0b;
      --gold-dark: #d97706;
      --gold-surf: #fef3c7;
      --text-main: #0f172a;
      --text-muted: #475569;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
    }

    body {
      background-color: var(--bg-tint);
      color: var(--text-main);
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    header {
      background: var(--navy-dark);
      color: #fff;
      padding: 12px 24px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 12px rgba(12, 74, 110, 0.15);
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .brand-wrap {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .logo-badge {
      width: 44px;
      height: 44px;
      background: #ffffff;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    }

    .brand-title h1 {
      font-size: 1.15rem;
      font-weight: 700;
      letter-spacing: 0.5px;
    }

    .brand-title p {
      font-size: 0.78rem;
      color: var(--accent-cyan);
      font-weight: 500;
    }

    .header-controls {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .chip {
      background: rgba(255, 255, 255, 0.15);
      border: 1px solid var(--border-accent);
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 0.88rem;
      color: #ffffff;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .chip strong {
      color: #ffffff;
      font-weight: 800;
      letter-spacing: 0.3px;
    }

    .btn-icon {
      background: transparent;
      border: 1px solid var(--border-accent);
      color: #fff;
      border-radius: 50%;
      width: 36px;
      height: 36px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
    }

    nav {
      background: #ffffff;
      border-bottom: 1px solid var(--border-soft);
      display: flex;
      justify-content: center;
      gap: 8px;
      padding: 8px 16px;
    }

    nav button {
      background: none;
      border: none;
      outline: none;
      padding: 10px 20px;
      font-size: 0.95rem;
      font-weight: 600;
      color: var(--text-muted);
      cursor: pointer;
      border-radius: 8px;
      transition: all 0.2s;
    }

    nav button.active {
      background: var(--bg-tint);
      color: var(--brand-blue);
      border-bottom: 3px solid var(--brand-blue);
    }

    main {
      flex: 1;
      padding: 24px;
      max-width: 1400px;
      margin: 0 auto;
      width: 100%;
    }

    .view {
      display: none;
    }

    .view.active {
      display: block;
    }

    #loginGateView {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(12, 74, 110, 0.92);
      backdrop-filter: blur(6px);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .login-box {
      background: #fff;
      padding: 36px;
      border-radius: 16px;
      width: 100%;
      max-width: 460px;
      text-align: center;
      box-shadow: 0 14px 35px rgba(0,0,0,0.3);
    }

    .login-box h2 {
      font-size: 1.45rem;
      color: var(--navy-dark);
      margin-bottom: 6px;
    }

    .login-box p {
      font-size: 0.88rem;
      color: var(--text-muted);
      margin-bottom: 20px;
      line-height: 1.5;
    }

    .resume-alert {
      display: none;
      background: #eff6ff;
      border: 1px solid var(--border-accent);
      border-radius: 8px;
      padding: 10px 14px;
      margin-bottom: 16px;
      font-size: 0.86rem;
      color: var(--navy-dark);
      text-align: left;
    }

    .login-box input {
      width: 100%;
      padding: 12px 16px;
      border: 1px solid var(--border-soft);
      border-radius: 8px;
      font-size: 1rem;
      margin-bottom: 16px;
      outline: none;
    }

    .btn-primary {
      background: var(--brand-blue);
      color: #fff;
      border: none;
      padding: 12px 24px;
      font-size: 1rem;
      font-weight: 600;
      border-radius: 8px;
      cursor: pointer;
      width: 100%;
      transition: background 0.2s;
    }

    .btn-primary:hover {
      background: var(--navy-dark);
    }

    .btn-secondary {
      background: transparent;
      border: 1px solid var(--border-accent);
      color: var(--navy-dark);
      padding: 9px 18px;
      font-size: 0.88rem;
      font-weight: 600;
      border-radius: 6px;
      cursor: pointer;
      width: 100%;
      margin-top: 10px;
    }

    .btn-secondary:hover {
      background: var(--bg-tint);
    }

    .theory-card {
      background: #fff;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      padding: 24px;
      margin-bottom: 24px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.02);
    }

    .theory-card h3 {
      color: var(--navy-dark);
      margin-bottom: 14px;
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 1.25rem;
    }

    .theory-intro-text {
      color: var(--text-main);
      line-height: 1.65;
      margin-bottom: 18px;
      font-size: 0.95rem;
    }

    .compendium-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
      margin: 16px 0;
    }

    .comp-card {
      background: #ffffff;
      border: 1px solid var(--border-soft);
      border-radius: 10px;
      padding: 18px;
      display: flex;
      flex-direction: column;
      box-shadow: 0 2px 6px rgba(12, 74, 110, 0.04);
    }

    .comp-card h4 {
      color: var(--navy-dark);
      border-bottom: 2px solid var(--border-soft);
      padding-bottom: 8px;
      margin-bottom: 12px;
      font-size: 1.05rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .recap-body {
      font-size: 0.92rem;
      line-height: 1.65;
      color: var(--text-main);
    }

    .formula-box {
      background: #f8fafc;
      border-left: 4px solid var(--brand-blue);
      border-radius: 0 6px 6px 0;
      padding: 10px 14px;
      margin-top: 10px;
    }

    .sheet-grid {
      display: grid;
      grid-template-columns: 1fr 340px;
      gap: 24px;
    }

    @media (max-width: 990px) {
      .sheet-grid {
        grid-template-columns: 1fr;
      }
    }

    .question-card {
      background: #fff;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      padding: 26px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.03);
    }

    .concept-tag {
      display: inline-block;
      padding: 4px 10px;
      border-radius: 14px;
      font-size: 0.75rem;
      font-weight: 700;
      letter-spacing: 0.4px;
      text-transform: uppercase;
      margin-bottom: 8px;
      background: #e0f2fe;
      color: #0369a1;
      border: 1px solid #7dd3fc;
    }

    .mcq-container {
      display: grid;
      grid-template-columns: 1fr;
      gap: 10px;
      margin: 18px 0;
    }

    .mcq-option-btn {
      background: #f8fafc;
      border: 2px solid var(--border-soft);
      border-radius: 8px;
      padding: 12px 16px;
      text-align: left;
      font-size: 0.96rem;
      color: var(--text-main);
      cursor: pointer;
      transition: all 0.15s ease;
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .mcq-option-btn:hover:not(:disabled) {
      background: var(--bg-tint);
      border-color: var(--brand-blue);
    }

    .mcq-option-btn.selected-correct {
      background: var(--green-surf) !important;
      border-color: var(--green-ok) !important;
      color: var(--green-ok) !important;
      font-weight: 700;
    }

    .mcq-option-btn.selected-wrong {
      background: var(--red-surf) !important;
      border-color: var(--red-fail) !important;
      color: var(--red-fail) !important;
    }

    .opt-letter {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: #ffffff;
      border: 1px solid var(--border-accent);
      font-weight: 700;
      color: var(--navy-dark);
      flex-shrink: 0;
    }

    .attempts-badge {
      font-size: 0.8rem;
      font-weight: 700;
      padding: 4px 10px;
      border-radius: 12px;
      background: #f1f5f9;
      color: #64748b;
      margin-left: 6px;
    }

    .btn-reveal {
      background: var(--brand-gold);
      color: #fff;
      border: none;
      padding: 6px 14px;
      border-radius: 6px;
      font-weight: 600;
      font-size: 0.85rem;
      cursor: pointer;
      margin-left: 8px;
    }

    .btn-reveal:hover {
      background: var(--gold-dark);
    }

    .feedback-box {
      margin-top: 16px;
      padding: 16px;
      border-radius: 8px;
      font-size: 0.95rem;
      line-height: 1.65;
      display: block;
      animation: fadeIn 0.25s ease-in;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(4px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .feedback-box.correct {
      background: #ecfdf5;
      border-left: 5px solid var(--green-ok);
      color: #065f46;
    }

    .feedback-box.incorrect {
      background: #fef2f2;
      border-left: 5px solid var(--red-fail);
      color: #991b1b;
    }

    .svg-container {
      display: flex;
      justify-content: center;
      margin: 16px 0;
      padding: 14px;
      background: var(--bg-tint);
      border-radius: 8px;
      border: 1px solid var(--border-soft);
      overflow-x: auto;
    }

    .nav-toolbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 26px;
      padding-top: 18px;
      border-top: 1px solid var(--border-soft);
    }

    .nav-btn-group {
      display: flex;
      gap: 10px;
    }

    .btn-nav-action {
      background: #f8fafc;
      border: 1px solid var(--border-accent);
      color: var(--navy-dark);
      padding: 8px 18px;
      border-radius: 6px;
      font-weight: 600;
      font-size: 0.9rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: all 0.15s;
    }

    .btn-nav-action:hover:not(:disabled) {
      background: var(--bg-tint);
      border-color: var(--brand-blue);
    }

    .btn-nav-action:disabled {
      opacity: 0.45;
      cursor: not-allowed;
    }

    .btn-skip {
      border-color: var(--brand-gold);
      color: var(--gold-dark);
      background: var(--gold-surf);
    }

    .btn-skip:hover {
      background: #fde68a;
    }

    .palette-box {
      background: #fff;
      border: 1px solid var(--border-soft);
      border-radius: 12px;
      padding: 16px;
      margin-bottom: 20px;
    }

    .palette-legend {
      display: flex;
      justify-content: space-between;
      font-size: 0.75rem;
      margin: 8px 0 12px 0;
      padding: 6px 8px;
      background: var(--bg-tint);
      border-radius: 6px;
    }

    .legend-item {
      display: flex;
      align-items: center;
      gap: 4px;
      font-weight: 600;
    }

    .legend-dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
    }

    .palette-grid {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 6px;
      margin-bottom: 12px;
    }

    .palette-btn {
      aspect-ratio: 1;
      border: 1px solid var(--border-soft);
      background: var(--bg-tint);
      border-radius: 6px;
      font-weight: 600;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.15s;
      font-size: 0.85rem;
      color: var(--navy-dark);
    }

    .palette-btn.active {
      border: 2px solid var(--navy-dark) !important;
      background: var(--border-accent);
      color: #fff;
      font-weight: 800;
    }

    .palette-btn.completed {
      background: var(--green-ok) !important;
      color: #fff !important;
      border-color: var(--green-ok) !important;
    }

    .palette-btn.skipped {
      background: var(--brand-gold) !important;
      color: #fff !important;
      border-color: var(--gold-dark) !important;
    }

    .hero-score-card {
      background: #fff;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      padding: 28px;
      text-align: center;
      margin-bottom: 24px;
      box-shadow: 0 4px 14px rgba(0,0,0,0.03);
    }

    .student-badge {
      display: inline-block;
      background: var(--bg-tint);
      border: 1px solid var(--border-accent);
      padding: 6px 18px;
      border-radius: 20px;
      font-size: 1rem;
      margin-bottom: 14px;
      color: var(--navy-dark);
    }

    .student-badge strong {
      color: var(--brand-blue);
    }

    .score-badge {
      font-size: 3rem;
      font-weight: 800;
      color: var(--brand-blue);
      margin: 8px 0;
    }

    .progress-bar-wrap {
      width: 100%;
      height: 12px;
      background: #e2e8f0;
      border-radius: 6px;
      overflow: hidden;
      margin: 16px 0;
    }

    .progress-bar-fill {
      height: 100%;
      background: var(--green-ok);
      width: 0%;
      transition: width 0.3s ease;
    }

    .toast {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: var(--navy-dark);
      color: #fff;
      padding: 12px 20px;
      border-radius: 8px;
      box-shadow: 0 4px 16px rgba(0,0,0,0.2);
      display: none;
      z-index: 1000;
    }

    @media print {
      header, nav, .palette-box, .btn-primary, #loginGateView, .nav-toolbar {
        display: none !important;
      }
      body { background: #fff; }
      main { width: 100%; max-width: 100%; padding: 0; }
      .sheet-grid { display: block; }
      .view { display: block !important; }
    }
  </style>
</head>
<body>

  <!-- Brand Header -->
  <header>
    <div class="brand-wrap">
      <div class="logo-badge">
        <svg width="34" height="34" viewBox="0 0 100 100" fill="none">
          <path d="M 20 30 Q 50 10 80 30" stroke="#f59e0b" stroke-width="8" stroke-linecap="round"/>
          <path d="M 26 40 Q 50 22 74 40" stroke="#f59e0b" stroke-width="8" stroke-linecap="round"/>
          <path d="M 32 50 Q 50 36 68 50" stroke="#f59e0b" stroke-width="7" stroke-linecap="round"/>
          <path d="M 18 80 Q 50 68 50 82 Q 50 68 82 80 L 82 52 Q 50 42 50 56 Q 50 42 18 52 Z" fill="#ffffff" stroke="#334155" stroke-width="7" stroke-linejoin="round"/>
        </svg>
      </div>
      <div class="brand-title">
        <h1>Brain &amp; Mind Academy</h1>
        <p>B&amp;M – The Experts • Calculus I: Continuity (Complete Class &amp; Practice Set)</p>
      </div>
    </div>
    <div class="header-controls">
      <div class="chip" id="timerChip">⏱️ 00:00</div>
      <div class="chip" id="userPill"><strong>Student: Guest</strong></div>
      <button class="btn-icon" id="audioToggleBtn" title="Toggle Audio">🔊</button>
    </div>
  </header>

  <!-- Navigation Bar -->
  <nav>
    <button class="tab-btn active" id="tabPracticeBtn" onclick="switchView('practiceView')">✍️ Interactive Workstation</button>
    <button class="tab-btn" id="tabTheoryBtn" onclick="switchView('theoryView')">📖 Concept &amp; Theorems Guide</button>
    <button class="tab-btn" id="tabResultsBtn" onclick="switchView('resultsView')">📋 Mark Scheme &amp; Full Derivations</button>
  </nav>

  <!-- Student Authentication Modal with Resume Progress Capability -->
  <div id="loginGateView">
    <div class="login-box">
      <h2>Calculus Continuity Portal</h2>
      <p>Class Notes &amp; Practice Problems • Paul's Online Math Notes Complete Set</p>
      
      <div id="resumeAlertBox" class="resume-alert">
        <strong>Saved Session Found!</strong><br>
        <span id="savedSessionDetails"></span>
      </div>

      <input type="text" id="studentNameInput" placeholder="Enter Student Name" />
      <button class="btn-primary" id="startSessionBtn" onclick="initDirectLogin(false)">Start New Session</button>
      <button class="btn-secondary" id="resumeSessionBtn" style="display:none;" onclick="initDirectLogin(true)">Resume Saved Session</button>
    </div>
  </div>

  <main>
    <!-- View 1: Interactive Workstation -->
    <div id="practiceView" class="view active">
      <div class="sheet-grid">
        <div class="question-card" id="activeQuestionCard"></div>

        <aside>
          <div class="palette-box">
            <div style="display: flex; justify-content: space-between; align-items: center;">
              <h4>Abhyas Palette</h4>
              <span style="font-size:0.8rem; color:var(--text-muted);" id="paletteCount">0 / 18 Completed</span>
            </div>

            <div class="palette-legend">
              <div class="legend-item"><span class="legend-dot" style="background:var(--green-ok);"></span> Solved</div>
              <div class="legend-item"><span class="legend-dot" style="background:#f59e0b;"></span> Skipped</div>
              <div class="legend-item"><span class="legend-dot" style="background:#7dd3fc;"></span> Active</div>
              <div class="legend-item"><span class="legend-dot" style="background:#f0f9ff; border:1px solid #bae6fd;"></span> Unseen</div>
            </div>
            
            <div class="palette-grid" id="paletteGrid"></div>
            
            <button class="btn-primary" style="margin-top: 10px; background: var(--navy-dark);" onclick="switchView('resultsView')">
              📊 View Performance Scorecard
            </button>
            <button class="btn-secondary" style="margin-top: 8px; border-color: #cbd5e1;" onclick="resetStudentProgress()">
              🔄 Clear &amp; Restart All Progress
            </button>
          </div>

          <div class="palette-box" style="background: #f8fafc;">
            <h4 style="font-size: 0.92rem; margin-bottom: 8px; color: var(--navy-dark);">Persistence &amp; Rules</h4>
            <p style="font-size: 0.82rem; line-height: 1.6; color: var(--text-muted);">
              • Your progress is <strong>automatically saved in local storage</strong>. If you close your browser or refresh, you can resume seamlessly.<br/>
              • <strong>2 attempts</strong> per problem are allowed before the <strong>Reveal Solution</strong> option unlocks.<br/>
              • All 18 problems from the tutorial and problem sets are mapped into interactive MCQs.
            </p>
          </div>
        </aside>
      </div>
    </div>

    <!-- View 2: Concept & Theorems Guide -->
    <div id="theoryView" class="view">
      <div class="theory-card">
        <h3>📐 Calculus I: Continuity &amp; The Intermediate Value Theorem</h3>
        <p class="theory-intro-text">
          A function \(f(x)\) is continuous at a number \(x = c\) if three conditions are satisfied simultaneously:
        </p>

        <div class="compendium-grid">
          <div class="comp-card">
            <h4>1. Three-Part Definition of Continuity</h4>
            <div class="recap-body">
              <div class="formula-box">
                \[1. \, f(c) \text{ is defined}\]
                \[2. \, \lim_{x \to c} f(x) \text{ exists} \quad (\lim_{x \to c^-} f(x) = \lim_{x \to c^+} f(x))\]
                \[3. \, \lim_{x \to c} f(x) = f(c)\]
              </div>
              <p style="margin-top:6px;">If any condition fails, the function is discontinuous at \(x = c\).</p>
            </div>
          </div>

          <div class="comp-card">
            <h4>2. Types of Discontinuities</h4>
            <div class="recap-body">
              <p>• <strong>Removable Discontinuity (Hole):</strong> \(\lim_{x \to c} f(x)\) exists, but \(f(c)\) is undefined or \(\lim_{x \to c} f(x) \ne f(c)\).</p>
              <p style="margin-top:4px;">• <strong>Jump Discontinuity:</strong> Both one-sided limits exist but are unequal: \(\lim_{x \to c^-} f(x) \ne \lim_{x \to c^+} f(x)\).</p>
              <p style="margin-top:4px;">• <strong>Infinite Discontinuity:</strong> One or both one-sided limits are \(\pm\infty\) (vertical asymptote).</p>
            </div>
          </div>

          <div class="comp-card">
            <h4>3. Continuity of Standard Functions</h4>
            <div class="recap-body">
              <p>Polynomials, rational functions, root functions, exponentials, and trigonometric functions are continuous on their natural domains:</p>
              <div class="formula-box">
                <p>• Polynomials: continuous on \((-\infty, \infty)\).</p>
                <p>• Rational \(\frac{P(x)}{Q(x)}\): continuous where \(Q(x) \ne 0\).</p>
                <p>• Root \(\sqrt[n]{g(x)}\): continuous where \(g(x) \ge 0\) for even \(n\).</p>
              </div>
            </div>
          </div>

          <div class="comp-card">
            <h4>4. Intermediate Value Theorem (IVT)</h4>
            <div class="recap-body">
              <p>Suppose \(f(x)\) is continuous on \([a, b]\) and \(M\) is any number between \(f(a)\) and \(f(b)\):</p>
              <div class="formula-box">
                \[\exists \, c \in (a, b) \quad \text{such that} \quad f(c) = M\]
                <p style="margin-top:4px; font-size:0.85rem;"><strong>Root Theorem:</strong> If \(f(a)\) and \(f(b)\) have opposite signs (\(f(a) \cdot f(b) < 0\)), there is at least one zero \(f(c) = 0\) in \((a, b)\).</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- View 3: Complete Solutions & Final Results -->
    <div id="resultsView" class="view">
      <div class="hero-score-card">
        <h2>Continuity Comprehensive Diagnostic Scorecard</h2>
        <div class="student-badge" id="reportStudentBadge"><strong>Student: Guest</strong></div>
        <div class="score-badge" id="scoreValue">0 / 18</div>
        <div class="progress-bar-wrap">
          <div class="progress-bar-fill" id="progressBarFill"></div>
        </div>
        <p id="scoreSubtitle" style="font-size:1.02rem; font-weight:600; color:var(--navy-dark); margin-top:8px;">
          Review all problem solutions, worked derivations, and continuity curves below.
        </p>
        <button class="btn-primary" style="margin-top: 14px; max-width: 240px;" onclick="window.print()">🖨️ Print Final Scorecard</button>
      </div>

      <div id="completeSolutionsContainer"></div>
    </div>
  </main>

  <div class="toast" id="toastMessage"></div>

  <script>
    /* ==========================================================================
       COMPLETE 18-QUESTION DATASET (MAPPING EVERY CLASS EXAMPLE & PRACTICE PROBLEM)
       Source: Paul's Online Math Notes - Calculus I: Continuity
       ========================================================================== */
    const CHAPTER_QUESTIONS = [
      // ---------- PART I: CLASS LECTURE NOTES EXAMPLES (Q1 - Q9) ----------
      {
        id: 1,
        section: "Class Notes: Example 1",
        title: "Discontinuity in a Rational Function with a Common Factor",
        prompt: "Given the function \\[f(x) = \\frac{x^2 - 2x - 8}{x - 4}\\]<br>" +
                "Why is \\(f(x)\\) discontinuous at \\(x = 4\\), what is \\(\\lim_{x \\to 4} f(x)\\), and what type of discontinuity exists?",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="130" x2="360" y2="130" stroke="#64748b" stroke-width="1.5"/>
          <line x1="120" y1="15" x2="120" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <text x="350" y="145" font-size="11" fill="#475569">x</text><text x="126" y="25" font-size="11" fill="#475569">y</text>
          <!-- Line y = x + 2 with a hole at (4, 6) -->
          <line x1="40" y1="150" x2="216" y2="52" stroke="#0284c7" stroke-width="2.5"/>
          <line x1="224" y1="48" x2="340" y2="-10" stroke="#0284c7" stroke-width="2.5"/>
          <circle cx="220" cy="50" r="4.5" fill="#ffffff" stroke="#0284c7" stroke-width="2.2"/>
          <line x1="220" y1="50" x2="220" y2="130" stroke="#94a3b8" stroke-dasharray="3"/>
          <line x1="120" y1="50" x2="220" y2="50" stroke="#94a3b8" stroke-dasharray="3"/>
          <text x="215" y="145" font-size="10">4</text><text x="105" y="54" font-size="10">6</text>
          <text x="230" y="46" font-size="10" font-weight="bold" fill="#0284c7">Hole: (4, 6)</text>
        </svg>`,
        options: [
          { label: "A", text: "f(4) is undefined; lim(x->4) f(x) = 6; Removable discontinuity (hole)" },
          { label: "B", text: "f(4) = 6; lim(x->4) f(x) does not exist; Jump discontinuity" },
          { label: "C", text: "f(4) is undefined; lim(x->4) f(x) = ∞; Infinite vertical asymptote" },
          { label: "D", text: "f(4) = 0; lim(x->4) f(x) = 0; Continuous everywhere" }
        ],
        correctIndex: 0,
        explanation: "Factor the numerator: \\(x^2 - 2x - 8 = (x - 4)(x + 2)\\).<br>" +
                     "For \\(x \\ne 4\\), \\(f(x) = x + 2\\). At \\(x = 4\\), the denominator is 0, so \\(f(4)\\) does not exist (violates Condition 1 of continuity).<br>" +
                     "However, \\(\\lim_{x \\to 4} f(x) = \\lim_{x \\to 4} (x + 2) = 6\\) exists. Because the limit exists while \\(f(4)\\) is undefined, \\(x = 4\\) is a <strong>removable discontinuity</strong> (hole)."
      },
      {
        id: 2,
        section: "Class Notes: Example 2",
        title: "Piecewise Function with Non-Matching Single-Point Value",
        prompt: "Consider the piecewise function \\[g(x) = \\begin{cases} \\frac{x^2 - 2x - 8}{x - 4} & x \\ne 4 \\\\ 3 & x = 4 \\end{cases}\\]<br>" +
                "Is \\(g(x)\\) continuous at \\(x = 4\\)?",
        options: [
          { label: "A", text: "No, because lim(x->4) g(x) = 6 ≠ 3 = g(4)" },
          { label: "B", text: "Yes, because g(4) is defined and equals 3" },
          { label: "C", text: "No, because lim(x->4) g(x) does not exist" },
          { label: "D", text: "Yes, because the limits from left and right differ" }
        ],
        correctIndex: 0,
        explanation: "1. \\(g(4) = 3\\) is defined.<br>" +
                     "2. \\(\\lim_{x \\to 4} g(x) = \\lim_{x \\to 4} (x + 2) = 6\\) exists.<br>" +
                     "3. Condition 3 requires \\(\\lim_{x \\to 4} g(x) = g(4)\\). Here \\(6 \\ne 3\\).<br>" +
                     "Since Condition 3 fails, \\(g(x)\\) is discontinuous at \\(x = 4\\) (removable discontinuity)."
      },
      {
        id: 3,
        section: "Class Notes: Example 3",
        title: "Removing Discontinuity by Setting Point Value",
        prompt: "Consider \\[h(x) = \\begin{cases} \\frac{x^2 - 2x - 8}{x - 4} & x \\ne 4 \\\\ 6 & x = 4 \\end{cases}\\]<br>" +
                "Is \\(h(x)\\) continuous at \\(x = 4\\)?",
        options: [
          { label: "A", text: "Yes, because h(4) = 6, lim(x->4) h(x) = 6, and lim(x->4) h(x) = h(4)" },
          { label: "B", text: "No, because piecewise functions can never be continuous at junctions" },
          { label: "C", text: "No, because the derivative is undefined at x = 4" },
          { label: "D", text: "Yes, but only from the right-hand side" }
        ],
        correctIndex: 0,
        explanation: "1. \\(h(4) = 6\\) is defined.<br>" +
                     "2. \\(\\lim_{x \\to 4} h(x) = \\lim_{x \\to 4} (x + 2) = 6\\) exists.<br>" +
                     "3. \\(\\lim_{x \\to 4} h(x) = 6 = h(4)\\).<br>" +
                     "All three conditions of continuity are met. The discontinuity has been successfully removed, so \\(h(x)\\) is continuous at \\(x = 4\\)."
      },
      {
        id: 4,
        section: "Class Notes: Example 4",
        title: "Jump Discontinuity at Piecewise Junction",
        prompt: "Let \\(f(x) = \\begin{cases} 2x - 1 & x < 2 \\\\ x^2 + 1 & x \\ge 2 \\end{cases}\\).<br>" +
                "Evaluate the continuity of \\(f(x)\\) at \\(x = 2\\).",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="140" x2="360" y2="140" stroke="#64748b" stroke-width="1.5"/>
          <line x1="80" y1="15" x2="80" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <text x="350" y="155" font-size="11" fill="#475569">x</text><text x="86" y="25" font-size="11" fill="#475569">y</text>
          
          <!-- Left branch: y = 2x - 1 for x < 2 (scaled: x=2 -> 180) -->
          <line x1="30" y1="150" x2="176" y2="81" stroke="#0284c7" stroke-width="2.5"/>
          <circle cx="180" cy="80" r="4.5" fill="#ffffff" stroke="#0284c7" stroke-width="2.2"/>
          <text x="120" y="75" font-size="10" fill="#0284c7">Left: (2, 3)</text>
          
          <!-- Right branch: y = x^2 + 1 for x >= 2 (value at x=2 is 5) -->
          <circle cx="180" cy="40" r="4.5" fill="#0c4a6e"/>
          <path d="M 180,40 Q 230,25 320,5" fill="none" stroke="#0c4a6e" stroke-width="2.5"/>
          <text x="190" y="42" font-size="10" font-weight="bold" fill="#0c4a6e">Right: (2, 5)</text>
          
          <!-- Jump gap visual -->
          <line x1="180" y1="45" x2="180" y2="75" stroke="#dc2626" stroke-width="1.5" stroke-dasharray="3"/>
          <text x="185" y="65" font-size="9" fill="#dc2626">Jump = 2</text>
        </svg>`,
        options: [
          { label: "A", text: "Discontinuous with a jump: lim(x->2-) f(x) = 3 ≠ 5 = lim(x->2+) f(x)" },
          { label: "B", text: "Continuous: both branches are polynomials" },
          { label: "C", text: "Discontinuous with a vertical asymptote at x = 2" },
          { label: "D", text: "Removable discontinuity: lim(x->2) f(x) = 4 but f(2) = 5" }
        ],
        correctIndex: 0,
        explanation: "Compute the one-sided limits as \\(x \\to 2\\):<br>" +
                     "• \\(\\lim_{x \\to 2^-} f(x) = \\lim_{x \\to 2^-} (2x - 1) = 2(2) - 1 = 3\\).<br>" +
                     "• \\(\\lim_{x \\to 2^+} f(x) = \\lim_{x \\to 2^+} (x^2 + 1) = 2^2 + 1 = 5\\).<br>" +
                     "Because the left-hand and right-hand limits exist but are unequal (\\(3 \\ne 5\\)), \\(\\lim_{x \\to 2} f(x)\\) does not exist. Hence, \\(f(x)\\) has a <strong>jump discontinuity</strong> at \\(x = 2\\)."
      },
      {
        id: 5,
        section: "Class Notes: Example 5",
        title: "Continuous Piecewise Function Across Junction",
        prompt: "Let \\(f(x) = \\begin{cases} x^2 & x < 1 \\\\ \\sqrt{x} & x \\ge 1 \\end{cases}\\).<br>" +
                "Where is \\(f(x)\\) continuous?",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="140" x2="360" y2="140" stroke="#64748b" stroke-width="1.5"/>
          <line x1="120" y1="15" x2="120" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <text x="350" y="155" font-size="11" fill="#475569">x</text><text x="126" y="25" font-size="11" fill="#475569">y</text>
          
          <!-- x = 1 is at 190 (scale: 70px = 1 unit) -->
          <!-- Parabola x^2 for x < 1 -->
          <path d="M 40,30 Q 120,140 190,70" fill="none" stroke="#0284c7" stroke-width="2.5"/>
          <!-- Root sqrt(x) for x >= 1 -->
          <path d="M 190,70 Q 260,50 350,35" fill="none" stroke="#0284c7" stroke-width="2.5"/>
          <!-- Seamless junction at (1, 1) -->
          <circle cx="190" cy="70" r="4.5" fill="#059669"/>
          <text x="198" y="74" font-size="10" font-weight="bold" fill="#059669">(1, 1) Continuous Junction</text>
        </svg>`,
        options: [
          { label: "A", text: "Continuous everywhere on (-∞, ∞)" },
          { label: "B", text: "Continuous on [0, ∞) only" },
          { label: "C", text: "Discontinuous at x = 1 because derivatives differ" },
          { label: "D", text: "Continuous on (-∞, 1) ∪ (1, ∞) with a jump at x = 1" }
        ],
        correctIndex: 0,
        explanation: "1. For \\(x < 1\\), \\(f(x) = x^2\\) is a polynomial and continuous on \\((-\\infty, 1)\\).<br>" +
                     "2. For \\(x > 1\\), \\(f(x) = \\sqrt{x}\\) is a root function and continuous on \\((1, \\infty)\\).<br>" +
                     "3. At the boundary \\(x = 1\\):<br>" +
                     "• \\(f(1) = \\sqrt{1} = 1\\)<br>" +
                     "• \\(\\lim_{x \\to 1^-} x^2 = 1^2 = 1\\)<br>" +
                     "• \\(\\lim_{x \\to 1^+} \\sqrt{x} = 1\\)<br>" +
                     "Thus \\(\\lim_{x \\to 1} f(x) = f(1) = 1\\), so \\(f(x)\\) is continuous at \\(x = 1\\). Therefore, \\(f(x)\\) is continuous everywhere on \\((-\\infty, \\infty)\\)."
      },
      {
        id: 6,
        section: "Class Notes: Example 6",
        title: "Continuity Domain of a Rational Function",
        prompt: "Determine where the rational function \\[R(x) = \\frac{x^3 - 2x + 1}{x^2 - 9}\\] is continuous.",
        options: [
          { label: "A", text: "(-∞, -3) ∪ (-3, 3) ∪ (3, ∞)" },
          { label: "B", text: "(-∞, 9) ∪ (9, ∞)" },
          { label: "C", text: "[-3, 3]" },
          { label: "D", text: "(-∞, ∞)" }
        ],
        correctIndex: 0,
        explanation: "A rational function is continuous everywhere on its domain (i.e. wherever the denominator is non-zero):<br>\\[x^2 - 9 = 0 \\implies (x - 3)(x + 3) = 0 \\implies x = 3 \\text{ and } x = -3\\]<br>" +
                     "Neither \\(x = 3\\) nor \\(x = -3\\) are roots of the numerator (\\(3^3 - 6 + 1 = 22 \\ne 0\\) and \\((-3)^3 + 6 + 1 = -20 \\ne 0\\)).<br>" +
                     "Thus, \\(R(x)\\) is continuous on \\((-\\infty, -3) \\cup (-3, 3) \\cup (3, \\infty)\\)."
      },
      {
        id: 7,
        section: "Class Notes: Example 7",
        title: "Continuity of a Radical Rational Function",
        prompt: "Determine the interval(s) on which \\[f(x) = \\frac{\\sqrt{2x + 3}}{x - 1}\\] is continuous.",
        svg: `<svg width="100%" height="160" viewBox="0 0 460 140" style="max-width:440px;">
          <rect width="460" height="140" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="80" x2="440" y2="80" stroke="#64748b" stroke-width="2"/>
          <!-- Scale markers -->
          <circle cx="100" cy="80" r="5" fill="#0284c7"/>
          <text x="85" y="105" font-size="10" font-weight="bold" fill="#0284c7">−3/2 [included]</text>
          
          <line x1="100" y1="80" x2="246" y2="80" stroke="#0284c7" stroke-width="4"/>
          <circle cx="250" cy="80" r="5" fill="#ffffff" stroke="#dc2626" stroke-width="2.5"/>
          <text x="240" y="105" font-size="10" font-weight="bold" fill="#dc2626">1 (excluded)</text>
          
          <line x1="254" y1="80" x2="430" y2="80" stroke="#0284c7" stroke-width="4"/>
          <polygon points="435,80 425,75 425,85" fill="#0284c7"/>
          <text x="140" y="55" font-size="10" fill="#0284c7">[-3/2, 1) ∪ (1, ∞)</text>
        </svg>`,
        options: [
          { label: "A", text: "[-3/2, 1) ∪ (1, ∞)" },
          { label: "B", text: "(-3/2, 1) ∪ (1, ∞)" },
          { label: "C", text: "[1, ∞)" },
          { label: "D", text: "(-∞, 1) ∪ (1, ∞)" }
        ],
        correctIndex: 0,
        explanation: "1. For the square root in the numerator to be defined in real numbers: \\(2x + 3 \\ge 0 \\implies x \\ge -\\frac{3}{2}\\).<br>" +
                     "2. For the denominator to be non-zero: \\(x - 1 \\ne 0 \\implies x \\ne 1\\).<br>" +
                     "3. Combining these domain requirements, the function is continuous on \\([-3/2, 1) \\cup (1, \\infty)\\)."
      },
      {
        id: 8,
        section: "Class Notes: Example 8",
        title: "Continuity of Trigonometric Functions",
        prompt: "Where is the function \\[f(x) = \\tan(x)\\] continuous?",
        options: [
          { label: "A", text: "Continuous on all real numbers except x = π/2 + kπ for any integer k" },
          { label: "B", text: "Continuous everywhere on (-∞, ∞)" },
          { label: "C", text: "Continuous only on (-π/2, π/2)" },
          { label: "D", text: "Continuous on all real numbers except x = kπ for any integer k" }
        ],
        correctIndex: 0,
        explanation: "Express tangent as a quotient: \\(\\tan(x) = \\frac{\\sin(x)}{\\cos(x)}\\).<br>" +
                     "Because \\(\\sin(x)\\) and \\(\\cos(x)\\) are continuous everywhere, \\(\\tan(x)\\) is continuous wherever \\(\\cos(x) \\ne 0\\).<br>" +
                     "The cosine function is zero at all odd multiples of \\(\\frac{\\pi}{2}\\):<br>\\[x = \\frac{\\pi}{2} + k\\pi, \\quad k \\in \\mathbb{Z}\\]<br>" +
                     "Hence, \\(\\tan(x)\\) is continuous on all real numbers except \\(x = \\frac{\\pi}{2} + k\\pi\\)."
      },
      {
        id: 9,
        section: "Class Notes: IVT Example",
        title: "Intermediate Value Theorem Polynomial Root",
        prompt: "Use the Intermediate Value Theorem to show that \\[x^5 - 2x^3 - 2 = 0\\] has a root on the interval \\([1, 2]\\). Which statement provides the proof?",
        options: [
          { label: "A", text: "Let f(x) = x^5 - 2x^3 - 2. Since f is continuous on [1, 2], f(1) = -3 < 0, and f(2) = 14 > 0, IVT guarantees a root in (1, 2)." },
          { label: "B", text: "f(1) = 1 and f(2) = 2, so by IVT there is a root." },
          { label: "C", text: "f'(x) > 0 on [1, 2], which guarantees a root by Rolle's Theorem." },
          { label: "D", text: "IVT does not apply because odd degree polynomials are not continuous on [1, 2]." }
        ],
        correctIndex: 0,
        explanation: "Let \\(f(x) = x^5 - 2x^3 - 2\\).<br>" +
                     "1. \\(f(x)\\) is a polynomial, so it is continuous on \\([1, 2]\\).<br>" +
                     "2. \\(f(1) = 1^5 - 2(1)^3 - 2 = 1 - 2 - 2 = -3 < 0\\).<br>" +
                     "3. \\(f(2) = 2^5 - 2(2)^3 - 2 = 32 - 16 - 2 = 14 > 0\\).<br>" +
                     "Because \\(f(1) < 0 < f(2)\\), 0 is an intermediate value between \\(f(1)\\) and \\(f(2)\\). By IVT, there must exist at least one \\(c \\in (1, 2)\\) such that \\(f(c) = 0\\)."
      },

      // ---------- PART II: PRACTICE PROBLEMS (Q10 - Q18) ----------
      {
        id: 10,
        section: "Practice Problem 1",
        title: "Discontinuity of f(x) = (x² - 9) / (x + 3)",
        prompt: "For the function \\[f(x) = \\frac{x^2 - 9}{x + 3}\\] determine all points of discontinuity.",
        options: [
          { label: "A", text: "x = -3 only (removable discontinuity)" },
          { label: "B", text: "x = 3 and x = -3" },
          { label: "C", text: "x = 3 only" },
          { label: "D", text: "Continuous everywhere on (-∞, ∞)" }
        ],
        correctIndex: 0,
        explanation: "Factor the numerator: \\(x^2 - 9 = (x - 3)(x + 3)\\).<br>" +
                     "The denominator is zero at \\(x = -3\\), meaning \\(f(-3)\\) is undefined.<br>" +
                     "However, \\(\\lim_{x \\to -3} \\frac{(x - 3)(x + 3)}{x + 3} = \\lim_{x \\to -3} (x - 3) = -6\\) exists.<br>" +
                     "Therefore, the only discontinuity is at \\(x = -3\\), and it is removable."
      },
      {
        id: 11,
        section: "Practice Problem 2",
        title: "Discontinuities of Quadratic Denominator Rational",
        prompt: "For the function \\[f(x) = \\frac{2x - 1}{x^2 - 4x - 12}\\] determine all points of discontinuity.",
        options: [
          { label: "A", text: "x = -2 and x = 6 (both are infinite discontinuities)" },
          { label: "B", text: "x = 2 and x = -6" },
          { label: "C", text: "x = 1/2 only" },
          { label: "D", text: "x = 6 only" }
        ],
        correctIndex: 0,
        explanation: "Factor the denominator:<br>\\[x^2 - 4x - 12 = (x - 6)(x + 2) = 0 \\implies x = 6, \\quad x = -2\\]<br>" +
                     "Neither \\(x = 6\\) nor \\(x = -2\\) makes the numerator \\(2x - 1\\) zero (\\(2(6)-1=11\\), \\(2(-2)-1=-5\\)).<br>" +
                     "Hence, \\(f(x)\\) has vertical asymptotes (infinite discontinuities) at \\(x = -2\\) and \\(x = 6\\)."
      },
      {
        id: 12,
        section: "Practice Problem 3",
        title: "Discontinuities of Cubic Denominator Rational",
        prompt: "For the function \\[f(x) = \\frac{x + 7}{x^3 - 4x}\\] determine all points of discontinuity.",
        options: [
          { label: "A", text: "x = 0, x = 2, and x = -2" },
          { label: "B", text: "x = 2 and x = -2 only" },
          { label: "C", text: "x = 0 and x = 4" },
          { label: "D", text: "x = -7, x = 0, x = 2, x = -2" }
        ],
        correctIndex: 0,
        explanation: "Factor the denominator completely:<br>\\[x^3 - 4x = x(x^2 - 4) = x(x - 2)(x + 2)\\]<br>" +
                     "The denominator is zero at \\(x = 0\\), \\(x = 2\\), and \\(x = -2\\).<br>" +
                     "The numerator \\(x + 7\\) is non-zero at all three of these points.<br>" +
                     "Thus, \\(f(x)\\) has three infinite discontinuities at \\(x = 0, 2, -2\\)."
      },
      {
        id: 13,
        section: "Practice Problem 4",
        title: "Rational Function with Irreducible Denominator",
        prompt: "For the function \\[f(x) = \\frac{x - 1}{x^2 + 1}\\] determine all points of discontinuity.",
        options: [
          { label: "A", text: "None; f(x) is continuous for all real numbers" },
          { label: "B", text: "x = 1" },
          { label: "C", text: "x = 1 and x = -1" },
          { label: "D", text: "x = 0" }
        ],
        correctIndex: 0,
        explanation: "Set the denominator equal to zero: \\(x^2 + 1 = 0 \\implies x^2 = -1\\), which has no real solutions.<br>" +
                     "Since the denominator is never zero for any real number \\(x\\), the rational function is continuous everywhere on \\((-\\infty, \\infty)\\)."
      },
      {
        id: 14,
        section: "Practice Problem 5",
        title: "Piecewise Junction Jump Test",
        prompt: "Given the piecewise function \\[f(x) = \\begin{cases} 3x - 2 & x \\le 1 \\\\ x^2 + 1 & x > 1 \\end{cases}\\]<br>" +
                "Determine where \\(f(x)\\) is continuous.",
        options: [
          { label: "A", text: "Continuous on (-∞, 1) ∪ (1, ∞); discontinuous at x = 1 (jump)" },
          { label: "B", text: "Continuous everywhere on (-∞, ∞)" },
          { label: "C", text: "Continuous on [1, ∞) only" },
          { label: "D", text: "Discontinuous at x = 1 (removable hole)" }
        ],
        correctIndex: 0,
        explanation: "1. Both \\(3x - 2\\) and \\(x^2 + 1\\) are polynomials, so they are continuous on their open intervals.<br>" +
                     "2. Check the boundary at \\(x = 1\\):<br>" +
                     "• \\(f(1) = 3(1) - 2 = 1\\)<br>" +
                     "• \\(\\lim_{x \\to 1^-} f(x) = 3(1) - 2 = 1\\)<br>" +
                     "• \\(\\lim_{x \\to 1^+} f(x) = 1^2 + 1 = 2\\)<br>" +
                     "Because \\(\\lim_{x \\to 1^-} f(x) \\ne \\lim_{x \\to 1^+} f(x)\\), the limit does not exist at \\(x = 1\\).<br>" +
                     "Thus, \\(f(x)\\) has a jump discontinuity at \\(x = 1\\) and is continuous on \\((-\\infty, 1) \\cup (1, \\infty)\\)."
      },
      {
        id: 15,
        section: "Practice Problem 6",
        title: "Multi-Piece Function with Mixed Boundaries",
        prompt: "Given the three-piece function \\[f(x) = \\begin{cases} 4x + 1 & x < -2 \\\\ x^2 - 3 & -2 \\le x \\le 3 \\\\ 2x & x > 3 \\end{cases}\\]<br>" +
                "Determine where \\(f(x)\\) is continuous.",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="110" x2="360" y2="110" stroke="#64748b" stroke-width="1.5"/>
          <line x1="160" y1="15" x2="160" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <text x="350" y="125" font-size="11" fill="#475569">x</text><text x="166" y="25" font-size="11" fill="#475569">y</text>
          
          <!-- Boundary x = -2 (at x=100) Jump -->
          <line x1="95" y1="15" x2="95" y2="165" stroke="#94a3b8" stroke-dasharray="3"/>
          <circle cx="95" cy="155" r="4" fill="#ffffff" stroke="#0284c7" stroke-width="2"/>
          <circle cx="95" cy="100" r="4" fill="#0284c7"/>
          <text x="45" y="130" font-size="9" fill="#dc2626">x = −2 (Jump)</text>
          
          <!-- Boundary x = 3 (at x=260) Continuous -->
          <line x1="260" y1="15" x2="260" y2="165" stroke="#94a3b8" stroke-dasharray="3"/>
          <circle cx="260" cy="50" r="4.5" fill="#059669"/>
          <text x="268" y="55" font-size="9" font-weight="bold" fill="#059669">x = 3 (Continuous)</text>
        </svg>`,
        options: [
          { label: "A", text: "Continuous on (-∞, -2) ∪ (-2, ∞); discontinuous at x = -2 only" },
          { label: "B", text: "Discontinuous at both x = -2 and x = 3" },
          { label: "C", text: "Continuous everywhere on (-∞, ∞)" },
          { label: "D", text: "Continuous on (-2, 3) only" }
        ],
        correctIndex: 0,
        explanation: "Check the two transition boundaries \\(x = -2\\) and \\(x = 3\\):<br>" +
                     "1. At \\(x = -2\\):<br>" +
                     "• \\(\\lim_{x \\to -2^-} (4x + 1) = 4(-2) + 1 = -7\\)<br>" +
                     "• \\(f(-2) = \\lim_{x \\to -2^+} (x^2 - 3) = (-2)^2 - 3 = 1\\)<br>" +
                     "Since \\(-7 \\ne 1\\), there is a jump discontinuity at \\(x = -2\\).<br>" +
                     "2. At \\(x = 3\\):<br>" +
                     "• \\(f(3) = \\lim_{x \\to 3^-} (x^2 - 3) = 3^2 - 3 = 6\\)<br>" +
                     "• \\(\\lim_{x \\to 3^+} (2x) = 2(3) = 6\\)<br>" +
                     "Since left limit = right limit = \\(f(3) = 6\\), \\(f(x)\\) is continuous at \\(x = 3\\).<br>" +
                     "Hence, \\(f(x)\\) is continuous everywhere except \\(x = -2\\): \\((-\\infty, -2) \\cup (-2, \\infty)\\)."
      },
      {
        id: 16,
        section: "Practice Problem 7",
        title: "Determining Constant c to Force Continuity",
        prompt: "Find the value of \\(c\\) that makes \\[f(x) = \\begin{cases} cx^2 + 2x & x < 2 \\\\ 2x^3 - c & x \\ge 2 \\end{cases}\\] continuous everywhere.",
        options: [
          { label: "A", text: "c = 12/5 (or 2.4)" },
          { label: "B", text: "c = 3" },
          { label: "C", text: "c = 2" },
          { label: "D", text: "c = 14/5" }
        ],
        correctIndex: 0,
        explanation: "For \\(f(x)\\) to be continuous at \\(x = 2\\), the left-hand limit and right-hand limit must match:<br>" +
                     "• \\(\\lim_{x \\to 2^-} f(x) = c(2)^2 + 2(2) = 4c + 4\\)<br>" +
                     "• \\(f(2) = \\lim_{x \\to 2^+} f(x) = 2(2)^3 - c = 16 - c\\)<br>" +
                     "Set them equal:<br>\\[4c + 4 = 16 - c \\implies 5c = 12 \\implies c = \\frac{12}{5} = 2.4\\]"
      },
      {
        id: 17,
        section: "Practice Problem 8",
        title: "Solving for Parameter c with Negative Boundary",
        prompt: "Find the value of \\(c\\) that makes \\[f(x) = \\begin{cases} 2x^2 + c & x \\le -1 \\\\ 3cx - 4 & x > -1 \\end{cases}\\] continuous everywhere.",
        options: [
          { label: "A", text: "c = -3/2 (or -1.5)" },
          { label: "B", text: "c = 3/2" },
          { label: "C", text: "c = -1" },
          { label: "D", text: "c = -2" }
        ],
        correctIndex: 0,
        explanation: "Equate one-sided limits at \\(x = -1\\):<br>" +
                     "• \\(f(-1) = \\lim_{x \\to -1^-} (2x^2 + c) = 2(-1)^2 + c = 2 + c\\)<br>" +
                     "• \\(\\lim_{x \\to -1^+} (3cx - 4) = 3c(-1) - 4 = -3c - 4\\)<br>" +
                     "Equating the limits:<br>\\[2 + c = -3c - 4 \\implies 4c = -6 \\implies c = -\\frac{6}{4} = -\\frac{3}{2} = -1.5\\]"
      },
      {
        id: 18,
        section: "Practice Problems 9 & 10",
        title: "Intermediate Value Theorem Application",
        prompt: "Consider the two equations:<br>" +
                "I. \\(x^3 - 3x^2 + 5x - 1 = 0\\) on \\([0, 1]\\)<br>" +
                "II. \\(\\cos(x) = x\\) on \\([0, \\pi/2]\\)<br><br>" +
                "Does the Intermediate Value Theorem guarantee at least one root on the given interval for each equation?",
        svg: `<svg width="100%" height="190" viewBox="0 0 380 160" style="max-width:360px;">
          <rect width="380" height="160" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="4"/>
          <line x1="20" y1="80" x2="360" y2="80" stroke="#64748b" stroke-width="1.5"/>
          <line x1="80" y1="15" x2="80" y2="145" stroke="#64748b" stroke-width="1.5"/>
          <text x="350" y="95" font-size="11">x</text><text x="86" y="25" font-size="11">y</text>
          
          <!-- Curve crossing axis -->
          <circle cx="80" cy="115" r="4" fill="#0284c7"/>
          <text x="90" y="125" font-size="10" fill="#0284c7">f(0) = −1 < 0</text>
          <circle cx="280" cy="35" r="4" fill="#0284c7"/>
          <text x="235" y="30" font-size="10" fill="#0284c7">f(1) = 2 > 0</text>
          
          <path d="M 80,115 Q 160,105 210,80 T 280,35" fill="none" stroke="#0c4a6e" stroke-width="2.5"/>
          <circle cx="210" cy="80" r="4.5" fill="#059669"/>
          <text x="215" y="75" font-size="10" font-weight="bold" fill="#059669">c (root)</text>
        </svg>`,
        options: [
          { label: "A", text: "Yes for both I and II" },
          { label: "B", text: "Yes for I only" },
          { label: "C", text: "Yes for II only" },
          { label: "D", text: "No for both" }
        ],
        correctIndex: 0,
        explanation: "• For I: Let \\(P(x) = x^3 - 3x^2 + 5x - 1\\). \\(P(x)\\) is continuous on \\([0, 1]\\).<br>" +
                     "\\(P(0) = -1 < 0\\) and \\(P(1) = 1 - 3 + 5 - 1 = 2 > 0\\). Since it changes sign, IVT guarantees a root in \\((0, 1)\\).<br>" +
                     "• For II: Let \\(g(x) = \\cos(x) - x\\). \\(g(x)\\) is continuous on \\([0, \\pi/2]\\).<br>" +
                     "\\(g(0) = \\cos(0) - 0 = 1 > 0\\) and \\(g(\\pi/2) = \\cos(\\pi/2) - \\pi/2 = -\\pi/2 < 0\\). Since it changes sign, IVT guarantees a root in \\((0, \\pi/2)\\).<br>" +
                     "Thus, IVT guarantees a root for both equations."
      }
    ];

    /* ==========================================================================
       PERSISTENCE & STATE MANAGEMENT ENGINE (RESUME ON RESTART)
       ========================================================================== */
    const STORAGE_KEY = "bm_calci_continuity_state_v1";

    let currentStudentName = "Guest";
    let currentQuestionIndex = 0;
    
    // Per-question tracking
    let questionStates = CHAPTER_QUESTIONS.map(() => ({
      attempts: 0,
      selectedIndex: null,
      isResolved: false,
      isCorrect: false,
      status: "unseen" // 'unseen', 'active', 'completed', 'skipped'
    }));

    let audioMuted = false;
    let totalSeconds = 0;
    let timerInterval = null;

    // Save complete session state to localStorage
    function saveSessionProgress() {
      try {
        const payload = {
          studentName: currentStudentName,
          currentQuestionIndex: currentQuestionIndex,
          totalSeconds: totalSeconds,
          questionStates: questionStates,
          timestamp: new Date().toISOString()
        };
        localStorage.setItem(STORAGE_KEY, JSON.stringify(payload));
      } catch (e) {
        console.warn("localStorage save failed", e);
      }
    }

    // Check and load saved state from localStorage
    function checkSavedSession() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (!raw) return;
        const data = JSON.parse(raw);
        if (data && data.studentName) {
          const alertBox = document.getElementById('resumeAlertBox');
          const detailsSpan = document.getElementById('savedSessionDetails');
          const resumeBtn = document.getElementById('resumeSessionBtn');
          const startBtn = document.getElementById('startSessionBtn');
          const input = document.getElementById('studentNameInput');

          input.value = data.studentName;
          const completed = data.questionStates.filter(q => q.isResolved).length;
          detailsSpan.innerText = `Candidate: ${data.studentName} • ${completed}/18 questions completed • Time: ${Math.floor(data.totalSeconds / 60)}m ${data.totalSeconds % 60}s`;
          alertBox.style.display = 'block';
          resumeBtn.style.display = 'inline-block';
          startBtn.innerText = 'Start Fresh Session';
        }
      } catch (e) {
        console.warn("Failed to check saved session", e);
      }
    }

    // Audio synthesizer
    const AudioEngine = {
      ctx: null,
      init() {
        if (!this.ctx) {
          this.ctx = new (window.AudioContext || window.webkitAudioContext)();
        }
      },
      playTone(freq, type, duration, delay = 0) {
        if (audioMuted || !this.ctx) return;
        setTimeout(() => {
          try {
            const osc = this.ctx.createOscillator();
            const gain = this.ctx.createGain();
            osc.type = type;
            osc.frequency.setValueAtTime(freq, this.ctx.currentTime);
            gain.gain.setValueAtTime(0.12, this.ctx.currentTime);
            gain.gain.exponentialRampToValueAtTime(0.0001, this.ctx.currentTime + duration);
            osc.connect(gain);
            gain.connect(this.ctx.destination);
            osc.start();
            osc.stop(this.ctx.currentTime + duration);
          } catch (e) {
            console.warn(e);
          }
        }, delay * 1000);
      },
      correct() {
        this.init();
        this.playTone(659.25, 'sine', 0.15, 0);
        this.playTone(880.00, 'sine', 0.25, 0.12);
      },
      incorrect() {
        this.init();
        this.playTone(196.00, 'triangle', 0.2, 0);
        this.playTone(146.83, 'triangle', 0.3, 0.12);
      },
      milestone() {
        this.init();
        [523.25, 659.25, 783.99, 1046.50].forEach((freq, idx) => {
          this.playTone(freq, 'sine', 0.22, idx * 0.09);
        });
      }
    };

    function startTimer() {
      if (timerInterval) clearInterval(timerInterval);
      timerInterval = setInterval(() => {
        totalSeconds++;
        const mins = String(Math.floor(totalSeconds / 60)).padStart(2, '0');
        const secs = String(totalSeconds % 60).padStart(2, '0');
        document.getElementById('timerChip').innerText = `⏱️ ${mins}:${secs}`;
        saveSessionProgress();
      }, 1000);
    }

    function showToast(msg) {
      const t = document.getElementById('toastMessage');
      t.innerText = msg;
      t.style.display = 'block';
      setTimeout(() => { t.style.display = 'none'; }, 2800);
    }

    function initDirectLogin(isResume = false) {
      const nameInput = document.getElementById('studentNameInput').value.trim() || 'Student';
      
      if (isResume) {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (raw) {
          const data = JSON.parse(raw);
          currentStudentName = data.studentName || nameInput;
          currentQuestionIndex = data.currentQuestionIndex || 0;
          totalSeconds = data.totalSeconds || 0;
          if (Array.isArray(data.questionStates)) {
            questionStates = data.questionStates;
          }
          showToast(`Welcome back, ${currentStudentName}! Resuming session.`);
        }
      } else {
        currentStudentName = nameInput;
        totalSeconds = 0;
        currentQuestionIndex = 0;
        questionStates = CHAPTER_QUESTIONS.map(() => ({
          attempts: 0,
          selectedIndex: null,
          isResolved: false,
          isCorrect: false,
          status: "unseen"
        }));
        saveSessionProgress();
      }

      document.getElementById('userPill').innerHTML = `<strong>Student: ${currentStudentName}</strong>`;
      document.getElementById('reportStudentBadge').innerHTML = `<strong>Student: ${currentStudentName}</strong>`;
      document.getElementById('loginGateView').style.display = 'none';
      
      AudioEngine.init();
      startTimer();
      renderPalette();
      loadQuestion(currentQuestionIndex);
      renderSolutions();
    }

    function resetStudentProgress() {
      if (confirm("Are you sure you want to clear your saved progress and start over?")) {
        localStorage.removeItem(STORAGE_KEY);
        location.reload();
      }
    }

    function switchView(viewId) {
      document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
      document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));
      document.getElementById(viewId).classList.add('active');

      if (viewId === 'practiceView') document.getElementById('tabPracticeBtn').classList.add('active');
      if (viewId === 'theoryView') document.getElementById('tabTheoryBtn').classList.add('active');
      if (viewId === 'resultsView') {
        document.getElementById('tabResultsBtn').classList.add('active');
        renderSolutions();
      }

      if (window.MathJax && window.MathJax.typesetPromise) {
        MathJax.typesetPromise();
      }
    }

    function renderPalette() {
      const grid = document.getElementById('paletteGrid');
      grid.innerHTML = '';

      let solvedCount = 0;
      CHAPTER_QUESTIONS.forEach((q, idx) => {
        const state = questionStates[idx];
        if (state.isResolved) solvedCount++;

        const btn = document.createElement('button');
        let stateClass = '';
        if (idx === currentQuestionIndex) {
          stateClass = 'active';
        } else if (state.isResolved) {
          stateClass = 'completed';
        } else if (state.status === 'skipped') {
          stateClass = 'skipped';
        }

        btn.className = `palette-btn ${stateClass}`;
        btn.innerText = idx + 1;
        btn.title = `${q.section}: ${q.title}`;
        btn.onclick = () => loadQuestion(idx);
        grid.appendChild(btn);
      });

      document.getElementById('paletteCount').innerText = `${solvedCount} / ${CHAPTER_QUESTIONS.length} Completed`;
    }

    function loadQuestion(idx) {
      currentQuestionIndex = idx;
      saveSessionProgress();
      renderPalette();
      const q = CHAPTER_QUESTIONS[idx];
      const state = questionStates[idx];
      const card = document.getElementById('activeQuestionCard');

      let optionsHtml = '';
      q.options.forEach((opt, optIdx) => {
        let optClass = '';
        if (state.isResolved) {
          if (optIdx === q.correctIndex) {
            optClass = 'selected-correct';
          } else if (state.selectedIndex === optIdx) {
            optClass = 'selected-wrong';
          }
        }

        optionsHtml += `
          <button class="mcq-option-btn ${optClass}" 
            onclick="handleOptionSelect(${idx}, ${optIdx})"
            ${state.isResolved ? 'disabled' : ''}>
            <span class="opt-letter">${opt.label}</span>
            <span>\\(${opt.text}\\)</span>
          </button>
        `;
      });

      let feedbackHtml = '';
      if (state.isResolved) {
        feedbackHtml = `
          <div class="feedback-box ${state.isCorrect ? 'correct' : 'incorrect'}">
            <strong>${state.isCorrect ? '✓ Correct!' : '✗ Solution Revealed'}</strong> (Correct Answer: Option ${q.options[q.correctIndex].label})<br/>
            <div style="margin-top: 8px;">${q.explanation}</div>
          </div>
        `;
      }

      const prevDisabled = idx === 0 ? 'disabled' : '';
      const nextDisabled = idx === CHAPTER_QUESTIONS.length - 1 ? 'disabled' : '';

      card.innerHTML = `
        <span class="concept-tag">${q.section}</span>
        <h2 style="color:var(--navy-dark); margin: 6px 0 10px 0;">Problem ${idx + 1}: ${q.title}</h2>
        <div style="margin-top: 8px; line-height: 1.65; font-size:1.02rem;">${q.prompt}</div>
        ${q.svg ? `<div class="svg-container">${q.svg}</div>` : ''}
        <div class="mcq-container">${optionsHtml}</div>
        
        <div style="display:flex; align-items:center; margin-top:12px;">
          <span class="attempts-badge">Attempts: ${state.attempts}/2</span>
          ${!state.isResolved && state.attempts >= 2 ? `
            <button class="btn-reveal" onclick="revealSolution(${idx})">Reveal Solution</button>
          ` : ''}
        </div>

        ${feedbackHtml}

        <div class="nav-toolbar">
          <button class="btn-nav-action" onclick="navigateQuestion(-1)" ${prevDisabled}>
            ⏮ Previous
          </button>
          <div class="nav-btn-group">
            <button class="btn-nav-action btn-skip" onclick="skipQuestion()">
              ⏭ Skip Question
            </button>
            <button class="btn-nav-action" onclick="navigateQuestion(1)" ${nextDisabled}>
              Next ❯
            </button>
          </div>
        </div>
      `;

      if (window.MathJax && window.MathJax.typesetPromise) {
        MathJax.typesetPromise();
      }
    }

    function handleOptionSelect(qIdx, optIdx) {
      const q = CHAPTER_QUESTIONS[qIdx];
      const state = questionStates[qIdx];
      if (state.isResolved) return;

      state.selectedIndex = optIdx;
      state.attempts++;

      if (optIdx === q.correctIndex) {
        state.isResolved = true;
        state.isCorrect = true;
        state.status = 'completed';
        AudioEngine.correct();
        showToast("Correct! Progress saved.");
      } else {
        AudioEngine.incorrect();
        if (state.attempts >= 2) {
          showToast("2 attempts reached. You can try once more or click 'Reveal Solution'.");
        } else {
          showToast("Incorrect option. You have 1 attempt remaining!");
        }
      }

      saveSessionProgress();
      renderPalette();
      loadQuestion(qIdx);
      renderSolutions();
    }

    function revealSolution(qIdx) {
      const state = questionStates[qIdx];
      state.isResolved = true;
      state.status = 'completed';
      AudioEngine.incorrect();
      showToast("Solution revealed.");
      saveSessionProgress();
      renderPalette();
      loadQuestion(qIdx);
      renderSolutions();
    }

    function navigateQuestion(delta) {
      const target = currentQuestionIndex + delta;
      if (target >= 0 && target < CHAPTER_QUESTIONS.length) {
        loadQuestion(target);
      }
    }

    function skipQuestion() {
      const state = questionStates[currentQuestionIndex];
      if (!state.isResolved) {
        state.status = 'skipped';
      }
      showToast(`Problem ${currentQuestionIndex + 1} marked as skipped.`);
      saveSessionProgress();
      renderPalette();
      navigateQuestion(1);
    }

    function renderSolutions() {
      const container = document.getElementById('completeSolutionsContainer');
      let score = 0;

      CHAPTER_QUESTIONS.forEach((q, idx) => {
        if (questionStates[idx].isCorrect) score++;
      });

      const totalQuestions = CHAPTER_QUESTIONS.length;
      const percentage = Math.round((score / totalQuestions) * 100);

      document.getElementById('scoreValue').innerText = `${score} / ${totalQuestions}`;
      document.getElementById('progressBarFill').style.width = `${percentage}%`;
      document.getElementById('reportStudentBadge').innerHTML = `<strong>Student: ${currentStudentName}</strong> (${percentage}% Score)`;

      let html = '';
      CHAPTER_QUESTIONS.forEach((q, idx) => {
        const state = questionStates[idx];
        let statusBadge = `<span style="color:var(--text-muted); font-weight:bold;">Unattempted</span>`;

        if (state.isResolved) {
          statusBadge = state.isCorrect
            ? `<span style="color:var(--green-ok); font-weight:bold;">✓ Correct (1/1)</span>`
            : `<span style="color:var(--red-fail); font-weight:bold;">✗ Solution Revealed (0/1)</span>`;
        }

        const studentChoiceLabel = (state.selectedIndex !== null && q.options[state.selectedIndex])
          ? `[${q.options[state.selectedIndex].label}] \\(${q.options[state.selectedIndex].text}\\)`
          : 'None';

        html += `
          <div class="theory-card">
            <div style="display:flex; justify-content:space-between; align-items:center;">
              <span class="concept-tag">${q.section}</span>
              ${statusBadge}
            </div>
            <h3 style="margin-top:6px;">Problem ${idx + 1}: ${q.title}</h3>
            <div style="margin: 8px 0; font-size:0.95rem;">${q.prompt}</div>
            ${q.svg ? `<div class="svg-container" style="max-width:320px; margin:12px 0;">${q.svg}</div>` : ''}
            
            <div style="background:#f8fafc; border-left:4px solid var(--brand-blue); padding:14px; margin-top:12px; border-radius:0 6px 6px 0;">
              <strong>Correct Answer:</strong> [${q.options[q.correctIndex].label}] \\(${q.options[q.correctIndex].text}\\)<br/>
              <strong>Your Selection:</strong> ${studentChoiceLabel}<br/>
              <div style="margin-top:8px;"><strong>Full Worked Derivation:</strong><br/>${q.explanation}</div>
            </div>
          </div>
        `;
      });

      container.innerHTML = html;
      if (window.MathJax && window.MathJax.typesetPromise) {
        MathJax.typesetPromise();
      }
    }

    document.getElementById('audioToggleBtn').onclick = () => {
      audioMuted = !audioMuted;
      document.getElementById('audioToggleBtn').innerText = audioMuted ? '🔇' : '🔊';
    };

    // Check for existing progress on startup
    window.addEventListener('DOMContentLoaded', checkSavedSession);
  </script>
</body>
</html>
