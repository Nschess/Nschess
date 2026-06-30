<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="preconnect" href="https://www.youtube-nocookie.com" />
  <link rel="preconnect" href="https://www.youtube.com" />
  <link rel="preconnect" href="https://i.ytimg.com" />
  <link rel="preconnect" href="https://www.google.com" />
  <link rel="preconnect" href="https://cdn.jsdelivr.net" />
  <title>Checkmate Quest - Learn Chess From First Move to Strategy</title>
  <style>
    :root {
      --bg: #201d1a;
      --panel: #2f2b27;
      --panel-2: #3b3630;
      --text: #f7f1e6;
      --muted: #cfc3b2;
      --soft: #f0d9b5;
      --board-light: #f0d9b5;
      --board-dark: #b58863;
      --green: #7fa650;
      --green-dark: #5f7f3a;
      --gold: #e7b65d;
      --blue: #6fa8dc;
      --danger: #d86f62;
      --line: rgba(255, 255, 255, 0.13);
      --shadow: 0 22px 60px rgba(0, 0, 0, 0.32);
      --radius: 8px;
      --max: 1180px;
      --move-speed: 140ms;
    }

    body.theme-light {
      --bg: #f6f1e8;
      --panel: #fffaf0;
      --panel-2: #eadfce;
      --text: #211a12;
      --muted: #675b4d;
      --soft: #3b3026;
      --line: rgba(33, 26, 18, 0.14);
    }

    body.board-wood {
      --board-light: #f0d9b5;
      --board-dark: #b58863;
    }

    body.board-marble {
      --board-light: #ede9df;
      --board-dark: #8fa3a8;
    }

    body.board-neon {
      --board-light: #d8fff4;
      --board-dark: #245cff;
    }

    body.coords-off .coordinates {
      display: none;
    }

    body.piece-letter .puzzle-square {
      font-family: Inter, ui-sans-serif, system-ui, sans-serif;
      font-weight: 1000;
    }

    body.speed-slow {
      --move-speed: 260ms;
    }

    body.speed-fast {
      --move-speed: 70ms;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      line-height: 1.55;
    }

    body.short-feed-locked {
      overflow: hidden;
    }

    body::selection {
      background: var(--gold);
      color: #211a12;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    img,
    iframe {
      max-width: 100%;
    }

    .site-header {
      position: sticky;
      top: 0;
      z-index: 20;
      border-bottom: 1px solid var(--line);
      background: rgba(32, 29, 26, 0.93);
      backdrop-filter: blur(14px);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 24px;
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
      min-height: 68px;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-weight: 900;
      letter-spacing: 0;
      white-space: nowrap;
    }

    .brand-mark {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      border: 2px solid var(--board-light);
      background:
        linear-gradient(45deg, var(--board-dark) 25%, transparent 25% 75%, var(--board-dark) 75%),
        linear-gradient(45deg, var(--board-dark) 25%, transparent 25% 75%, var(--board-dark) 75%);
      background-color: var(--board-light);
      background-position: 0 0, 9px 9px;
      background-size: 18px 18px;
      border-radius: var(--radius);
      color: #211a12;
      font-size: 0.72rem;
      font-weight: 1000;
      line-height: 1;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 8px;
      flex-wrap: wrap;
      justify-content: flex-end;
      min-width: 0;
      padding: 5px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: var(--radius);
      background: rgba(255, 255, 255, 0.04);
      box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.05);
    }

    .nav-group {
      display: inline-flex;
      align-items: center;
      flex: 0 0 auto;
      gap: 4px;
      padding: 3px;
      border-radius: 7px;
      background: rgba(0, 0, 0, 0.12);
    }

    .nav-group-label {
      padding: 0 8px;
      color: var(--gold);
      font-size: 0.68rem;
      font-weight: 1000;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .nav-links a {
      display: inline-flex;
      align-items: center;
      min-height: 36px;
      padding: 0 10px;
      border-radius: 6px;
      color: var(--muted);
      font-size: 0.88rem;
      font-weight: 900;
      white-space: nowrap;
      transition: background var(--move-speed) ease, color var(--move-speed) ease, box-shadow var(--move-speed) ease, transform var(--move-speed) ease;
    }

    .nav-links a.is-quick-tab {
      color: var(--text);
      background: rgba(127, 166, 80, 0.16);
    }

    .nav-links a:hover,
    .nav-links a:focus-visible {
      color: var(--text);
      background: rgba(255, 255, 255, 0.08);
      transform: translateY(-1px);
      outline: none;
    }

    .nav-links a[aria-current="page"],
    .nav-links a.is-active-tab {
      color: #10150d;
      background: var(--green);
      box-shadow: 0 8px 20px rgba(127, 166, 80, 0.24);
    }

    .nav-links::-webkit-scrollbar {
      height: 6px;
    }

    .nav-links::-webkit-scrollbar-track {
      background: rgba(255, 255, 255, 0.06);
      border-radius: 999px;
    }

    .nav-links::-webkit-scrollbar-thumb {
      background: rgba(240, 217, 181, 0.42);
      border-radius: 999px;
    }

    .site-panel,
    #shorts {
      scroll-margin-top: 88px;
    }

    body.site-tab-mode .hero {
      display: none;
    }

    body.site-tab-mode main > .site-panel:not(.is-active-panel) {
      display: none;
    }

    body.site-tab-mode main > .site-panel.is-active-panel {
      min-height: calc(100svh - 68px);
      animation: sitePanelIn 220ms ease both;
    }

    @keyframes sitePanelIn {
      from {
        opacity: 0;
        transform: translateY(10px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .hero {
      position: relative;
      display: grid;
      align-items: center;
      overflow: hidden;
      min-height: clamp(540px, 78svh, 780px);
      border-bottom: 1px solid var(--line);
      isolation: isolate;
    }

    .hero::before {
      content: "";
      position: absolute;
      inset: 0;
      background:
        linear-gradient(90deg, rgba(32, 29, 26, 0.92) 0%, rgba(32, 29, 26, 0.78) 42%, rgba(32, 29, 26, 0.44) 100%),
        radial-gradient(circle at 68% 30%, rgba(231, 182, 93, 0.14), transparent 34%);
      z-index: -1;
      pointer-events: none;
    }

    .hero-board {
      position: absolute;
      right: max(-80px, calc((100vw - var(--max)) / 2 - 90px));
      top: 50%;
      width: min(680px, 64vw);
      aspect-ratio: 1;
      transform: translateY(-48%) rotate(2deg);
      box-shadow: var(--shadow);
      border: 10px solid #181512;
      background: #181512;
      z-index: -2;
    }

    .hero-board-grid,
    .puzzle-board {
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      grid-template-rows: repeat(8, 1fr);
    }

    .hero-square,
    .puzzle-square {
      display: grid;
      place-items: center;
      aspect-ratio: 1;
      font-family: Georgia, "Times New Roman", serif;
      font-size: clamp(1.8rem, 5vw, 4.6rem);
      text-shadow: 0 2px 5px rgba(0, 0, 0, 0.38);
      user-select: none;
      line-height: 1;
    }

    .light {
      background: var(--board-light);
    }

    .dark {
      background: var(--board-dark);
    }

    .white-piece {
      color: #fff8ed;
      -webkit-text-stroke: 0.8px rgba(93, 64, 42, 0.72);
      text-shadow:
        0 1px 0 rgba(110, 75, 48, 0.78),
        0 3px 8px rgba(0, 0, 0, 0.38);
    }

    .black-piece {
      color: #1d1814;
      -webkit-text-stroke: 0.55px rgba(255, 248, 237, 0.42);
      text-shadow:
        0 1px 0 rgba(255, 255, 255, 0.2),
        0 3px 7px rgba(0, 0, 0, 0.32);
    }

    .hero-inner {
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
      padding: 72px 0 58px;
    }

    .hero-layout {
      display: grid;
      grid-template-columns: minmax(0, 1fr) minmax(310px, 420px);
      gap: 34px;
      align-items: center;
    }

    .hero-copy {
      max-width: 640px;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      margin: 0 0 16px;
      color: var(--gold);
      font-size: 0.82rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .eyebrow::before {
      content: "";
      width: 24px;
      height: 2px;
      background: currentColor;
    }

    h1,
    h2,
    h3,
    p {
      margin-top: 0;
    }

    h1 {
      max-width: 11ch;
      margin-bottom: 18px;
      font-size: clamp(3.2rem, 9vw, 7.2rem);
      line-height: 0.91;
      letter-spacing: 0;
    }

    .hero-copy > p {
      max-width: 58ch;
      color: var(--muted);
      font-size: clamp(1rem, 2vw, 1.25rem);
    }

    .hero-actions {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      margin-top: 26px;
    }

    .home-start-flow {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 10px;
      margin-top: 20px;
      max-width: 650px;
    }

    .home-step {
      min-height: 92px;
      padding: 13px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(255, 255, 255, 0.07);
      transition: transform 160ms ease, background 160ms ease, border-color 160ms ease;
    }

    .home-step:hover,
    .home-step:focus-visible {
      transform: translateY(-2px);
      border-color: rgba(231, 182, 93, 0.45);
      background: rgba(255, 255, 255, 0.11);
      outline: none;
    }

    .home-step strong,
    .home-step span {
      display: block;
    }

    .home-step strong {
      color: var(--soft);
      font-size: 0.95rem;
      line-height: 1.2;
    }

    .home-step span {
      margin-top: 6px;
      color: var(--muted);
      font-size: 0.83rem;
      line-height: 1.35;
    }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 44px;
      padding: 0 18px;
      border: 1px solid transparent;
      border-radius: 7px;
      background: var(--green);
      color: #10150d;
      font-weight: 800;
      cursor: pointer;
      transition: transform 160ms ease, background 160ms ease, border-color 160ms ease, color 160ms ease;
    }

    .button:hover,
    .button:focus-visible {
      transform: translateY(-1px);
      background: #95ba60;
      outline: none;
    }

    .button.secondary {
      border-color: var(--line);
      background: rgba(255, 255, 255, 0.08);
      color: var(--text);
    }

    .button.secondary:hover,
    .button.secondary:focus-visible {
      background: rgba(255, 255, 255, 0.13);
    }

    .hero-metrics {
      display: grid;
      grid-template-columns: repeat(3, minmax(110px, 1fr));
      gap: 12px;
      max-width: 560px;
      margin-top: 44px;
    }

    .home-dashboard {
      display: grid;
      gap: 14px;
      margin: 0;
      padding: 18px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(47, 43, 39, 0.78);
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.24);
      backdrop-filter: blur(12px);
    }

    body.theme-light .home-dashboard {
      background: rgba(255, 250, 240, 0.82);
    }

    .home-dashboard h3,
    .home-dashboard p {
      margin: 0;
    }

    .home-stat-grid,
    .quick-practice,
    .recommendation-list {
      display: grid;
      gap: 8px;
    }

    .home-stat-grid,
    .quick-practice {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .recommendation-list {
      grid-template-columns: 1fr;
    }

    .home-stat {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 32px;
      padding: 0 10px;
      border-radius: 7px;
      background: rgba(231, 182, 93, 0.15);
      color: var(--gold);
      font-size: 0.84rem;
      font-weight: 900;
    }

    .recommendation-list a {
      border-color: rgba(127, 166, 80, 0.38);
      background: rgba(127, 166, 80, 0.14);
    }

    .metric {
      min-height: 88px;
      padding: 16px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(47, 43, 39, 0.76);
    }

    .metric strong {
      display: block;
      color: var(--soft);
      font-size: 1.55rem;
      line-height: 1;
    }

    .metric span {
      display: block;
      margin-top: 8px;
      color: var(--muted);
      font-size: 0.9rem;
    }

    section {
      padding: 76px 0;
    }

    .section-dark {
      background: #26221f;
    }

    body.theme-light .site-header {
      background: rgba(246, 241, 232, 0.94);
    }

    body.theme-light .nav-links,
    body.theme-light .nav-group {
      background: rgba(33, 26, 18, 0.04);
    }

    body.theme-light .section-dark,
    body.theme-light .footer {
      background: #ede3d3;
      color: #211a12;
    }

    .section-warm {
      background: #f4eadc;
      color: #211a12;
    }

    .section-warm .section-kicker,
    .section-warm .section-intro,
    .section-warm .muted {
      color: #5d5144;
    }

    .section-warm .lesson-card,
    .section-warm .adventure-card,
    .section-warm .mission-card,
    .section-warm .adventure-play,
    .section-warm .rule-item,
    .section-warm .opening-card,
    .section-warm .notation-card,
    .section-warm .book-card,
    .section-warm .book-detail,
    .section-warm .video-card,
    .section-warm .puzzle-shell {
      border-color: rgba(33, 26, 18, 0.16);
      background: #fff8eb;
      color: #211a12;
      box-shadow: 0 18px 40px rgba(82, 55, 25, 0.12);
    }

    .wrap {
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
    }

    .section-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 28px;
      margin-bottom: 28px;
    }

    .section-kicker {
      margin: 0 0 8px;
      color: var(--gold);
      font-size: 0.8rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    h2 {
      margin-bottom: 0;
      font-size: clamp(2rem, 4.2vw, 3.4rem);
      line-height: 1;
      letter-spacing: 0;
    }

    .section-intro {
      max-width: 54ch;
      margin-bottom: 0;
      color: var(--muted);
    }

    .path-tabs {
      display: inline-grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 4px;
      padding: 4px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(0, 0, 0, 0.18);
    }

    .tab-button {
      min-height: 38px;
      padding: 0 14px;
      border: 0;
      border-radius: 6px;
      background: transparent;
      color: var(--muted);
      font: inherit;
      font-size: 0.92rem;
      font-weight: 800;
      cursor: pointer;
      white-space: nowrap;
    }

    .tab-button[aria-selected="true"] {
      background: var(--green);
      color: #11170e;
    }

    .lesson-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 16px;
    }

    .lesson-card,
    .adventure-card,
    .mission-card,
    .adventure-play,
    .rule-item,
    .opening-card,
    .notation-card,
    .book-card,
    .book-detail,
    .video-card,
    .puzzle-shell {
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--panel);
      box-shadow: 0 16px 35px rgba(0, 0, 0, 0.16);
    }

    .lesson-card {
      display: flex;
      flex-direction: column;
      min-height: 270px;
      padding: 20px;
    }

    .lesson-flow {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(135px, 1fr));
      gap: 10px;
      margin: 0 0 18px;
      padding: 14px;
      border: 1px solid rgba(231, 182, 93, 0.24);
      border-radius: var(--radius);
      background: rgba(231, 182, 93, 0.08);
    }

    .lesson-flow-step {
      display: grid;
      gap: 4px;
      min-height: 72px;
      padding: 11px;
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.07);
      color: var(--muted);
      font-size: 0.85rem;
      font-weight: 800;
    }

    .lesson-flow-step strong {
      color: var(--soft);
      font-size: 0.98rem;
    }

    .lesson-journey {
      display: grid;
      gap: 12px;
      margin: 0 0 18px;
      padding: 16px;
      border: 1px solid rgba(127, 166, 80, 0.28);
      border-radius: var(--radius);
      background: rgba(127, 166, 80, 0.08);
    }

    .lesson-journey h3 {
      margin: 0;
      font-size: 1.16rem;
    }

    .journey-steps {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 8px;
    }

    .journey-step {
      min-height: 42px;
      padding: 0 12px;
      border: 1px solid rgba(239, 229, 211, 0.14);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.06);
      color: var(--soft);
      font: inherit;
      font-weight: 900;
      text-align: left;
      cursor: pointer;
    }

    .journey-step.is-complete {
      border-color: rgba(127, 166, 80, 0.5);
      background: rgba(127, 166, 80, 0.18);
    }

    .journey-step.is-current {
      border-color: rgba(231, 182, 93, 0.55);
      background: rgba(231, 182, 93, 0.14);
    }

    .journey-step.is-locked {
      color: var(--muted);
      cursor: not-allowed;
      opacity: 0.72;
    }

    .lesson-card.is-locked p:not(.lesson-lock-note),
    .lesson-card.is-locked .topic-list,
    .lesson-card.is-locked .lesson-card-footer {
      display: none;
    }

    .lesson-lock-note {
      display: none;
      margin-top: auto;
      color: var(--muted);
      font-weight: 800;
    }

    .lesson-card.is-locked .lesson-lock-note {
      display: block;
    }

    .lesson-card-footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      margin-top: auto;
      padding-top: 16px;
    }

    .lesson-time {
      color: var(--gold);
      font-size: 0.82rem;
      font-weight: 900;
    }

    .gentle-start {
      display: grid;
      grid-template-columns: minmax(0, 0.95fr) minmax(320px, 1.25fr);
      gap: 20px;
      margin: 0 0 26px;
      padding: 22px;
      border: 1px solid rgba(231, 182, 93, 0.24);
      border-radius: var(--radius);
      background:
        linear-gradient(135deg, rgba(127, 166, 80, 0.16), rgba(111, 168, 220, 0.09)),
        var(--panel);
      box-shadow: 0 20px 46px rgba(0, 0, 0, 0.18);
    }

    .gentle-copy h3,
    .gentle-output h4 {
      margin-bottom: 10px;
      font-size: 1.34rem;
      line-height: 1.18;
    }

    .gentle-copy p,
    .gentle-output p {
      color: var(--muted);
    }

    .gentle-badges,
    .gentle-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 16px;
    }

    .gentle-badge {
      display: inline-flex;
      align-items: center;
      min-height: 30px;
      padding: 0 10px;
      border: 1px solid rgba(255, 248, 237, 0.13);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.07);
      color: var(--soft);
      font-size: 0.82rem;
      font-weight: 900;
    }

    .gentle-checklist {
      display: grid;
      gap: 9px;
      margin: 16px 0 18px;
      padding: 0;
      list-style: none;
    }

    .gentle-checklist li {
      display: grid;
      grid-template-columns: 30px 1fr;
      gap: 10px;
      align-items: center;
      color: var(--muted);
      font-weight: 800;
    }

    .gentle-checklist span {
      display: grid;
      place-items: center;
      width: 30px;
      height: 30px;
      border-radius: 7px;
      background: rgba(231, 182, 93, 0.15);
      color: var(--gold);
      font-weight: 900;
    }

    .gentle-coach {
      display: grid;
      gap: 14px;
      padding: 16px;
      border: 1px solid rgba(255, 248, 237, 0.12);
      border-radius: var(--radius);
      background: rgba(0, 0, 0, 0.16);
    }

    .gentle-form {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr)) auto;
      gap: 10px;
      align-items: end;
    }

    .gentle-form label {
      display: grid;
      gap: 7px;
      color: var(--muted);
      font-size: 0.86rem;
      font-weight: 900;
    }

    .gentle-form select {
      min-height: 42px;
      padding: 0 11px;
      border: 1px solid rgba(255, 248, 237, 0.15);
      border-radius: 7px;
      background: #211d1a;
      color: var(--text);
      font: inherit;
      font-weight: 800;
    }

    .gentle-output {
      display: grid;
      gap: 12px;
      min-height: 220px;
      padding: 16px;
      border: 1px solid rgba(127, 166, 80, 0.2);
      border-radius: var(--radius);
      background: rgba(127, 166, 80, 0.08);
    }

    .gentle-task-list {
      display: grid;
      gap: 9px;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .gentle-task {
      display: grid;
      grid-template-columns: auto minmax(0, 1fr) auto auto;
      gap: 10px;
      align-items: center;
      min-height: 58px;
      padding: 10px;
      border: 1px solid rgba(255, 248, 237, 0.12);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.05);
    }

    .gentle-task input {
      width: 19px;
      height: 19px;
      accent-color: var(--green);
    }

    .gentle-task.is-done {
      border-color: rgba(127, 166, 80, 0.34);
      background: rgba(127, 166, 80, 0.12);
    }

    .gentle-task strong,
    .gentle-task small {
      display: block;
    }

    .gentle-task small {
      margin-top: 3px;
      color: var(--muted);
      line-height: 1.42;
    }

    .gentle-time {
      color: var(--gold);
      font-size: 0.82rem;
      font-weight: 900;
      white-space: nowrap;
    }

    .lesson-number {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      margin-bottom: 20px;
      border-radius: 50%;
      background: var(--green);
      color: #10150d;
      font-weight: 900;
    }

    .lesson-card h3,
    .video-card h3,
    .puzzle-info h3 {
      margin-bottom: 10px;
      font-size: 1.18rem;
      line-height: 1.2;
    }

    .lesson-card p,
    .rule-item p,
    .video-card p,
    .puzzle-info p {
      color: var(--muted);
    }

    .section-warm .lesson-card p,
    .section-warm .adventure-card p,
    .section-warm .mission-card p,
    .section-warm .adventure-play p,
    .section-warm .rule-item p,
    .section-warm .opening-card p,
    .section-warm .notation-card p,
    .section-warm .book-card p,
    .section-warm .book-detail p,
    .section-warm .video-card p,
    .section-warm .puzzle-info p {
      color: #5d5144;
    }

    .topic-list {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 18px 0 0;
      padding: 0;
      list-style: none;
    }

    .topic-list li {
      padding: 5px 9px;
      border: 1px solid var(--line);
      border-radius: 999px;
      color: var(--muted);
      font-size: 0.82rem;
    }

    .section-warm .topic-list li {
      border-color: rgba(33, 26, 18, 0.16);
      color: #5d5144;
      background: rgba(181, 136, 99, 0.12);
    }

    .adventure-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 16px;
      margin-bottom: 18px;
    }

    .adventure-card {
      min-height: 210px;
      padding: 20px;
    }

    .character-mark {
      display: grid;
      place-items: center;
      width: 48px;
      height: 48px;
      margin-bottom: 16px;
      border-radius: 50%;
      background: rgba(127, 166, 80, 0.16);
      color: #211a12;
      font-size: 1.6rem;
    }

    .adventure-card h3,
    .mission-card h3 {
      margin-bottom: 8px;
      font-size: 1.15rem;
      line-height: 1.2;
    }

    .mission-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 16px;
    }

    .mission-card {
      padding: 20px;
      min-height: 190px;
    }

    .mission-label {
      display: inline-flex;
      align-items: center;
      min-height: 28px;
      margin-bottom: 12px;
      padding: 0 9px;
      border-radius: 999px;
      background: rgba(231, 182, 93, 0.22);
      color: #704d13;
      font-size: 0.8rem;
      font-weight: 900;
    }

    .adventure-play {
      display: grid;
      grid-template-columns: minmax(300px, 460px) 1fr;
      gap: 24px;
      margin-top: 18px;
      padding: 22px;
      align-items: start;
    }

    .adventure-board-wrap {
      border: 8px solid #211a12;
      border-radius: var(--radius);
      overflow: hidden;
      background: #211a12;
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.22);
    }

    .adventure-board {
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      grid-template-rows: repeat(8, 1fr);
      width: 100%;
      aspect-ratio: 1;
    }

    .adventure-square {
      position: relative;
      display: grid;
      place-items: center;
      aspect-ratio: 1;
      border: 0;
      padding: 0;
      appearance: none;
      font-family: Georgia, "Times New Roman", serif;
      font-size: clamp(1.35rem, 5vw, 3.35rem);
      line-height: 1;
      cursor: pointer;
    }

    .adventure-square.selected {
      outline: 4px solid rgba(231, 182, 93, 0.86);
      outline-offset: -4px;
    }

    .adventure-square.source-piece {
      box-shadow: inset 0 0 0 4px rgba(231, 182, 93, 0.5);
    }

    .adventure-square.legal-target::after {
      content: "";
      position: absolute;
      width: 34%;
      height: 34%;
      border: 3px solid rgba(127, 166, 80, 0.85);
      border-radius: 50%;
      pointer-events: none;
    }

    .adventure-panel {
      min-width: 0;
    }

    .mission-selector {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 8px;
      margin-bottom: 16px;
    }

    .mission-button {
      min-height: 40px;
      padding: 8px 10px;
      border: 1px solid rgba(33, 26, 18, 0.18);
      border-radius: 7px;
      background: #f7efe2;
      color: #211a12;
      font: inherit;
      font-size: 0.86rem;
      font-weight: 900;
      cursor: pointer;
    }

    .mission-button[aria-pressed="true"] {
      border-color: var(--green);
      background: #dfeecf;
    }

    .rules-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 14px;
    }

    .rule-item {
      min-height: 180px;
      padding: 18px;
    }

    .rule-item strong {
      display: block;
      margin-bottom: 9px;
      font-size: 1.05rem;
    }

    .rule-item p {
      margin-bottom: 0;
      font-size: 0.95rem;
    }

    .opening-grid,
    .notation-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 18px;
    }

    .opening-card,
    .notation-card {
      overflow: hidden;
    }

    .opening-body,
    .notation-card {
      padding: 20px;
    }

    .opening-body h3,
    .notation-card h3 {
      margin-bottom: 8px;
      font-size: 1.18rem;
      line-height: 1.2;
    }

    .opening-line {
      display: inline-flex;
      margin-bottom: 12px;
      padding: 6px 9px;
      border-radius: 6px;
      background: rgba(127, 166, 80, 0.14);
      color: var(--green-dark);
      font-size: 0.88rem;
      font-weight: 900;
    }

    .book-lines {
      display: grid;
      gap: 8px;
      margin: 16px 0 0;
      padding: 0;
      list-style: none;
    }

    .book-lines li {
      display: grid;
      gap: 3px;
      padding: 10px;
      border: 1px solid var(--line);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.06);
    }

    .book-lines code {
      color: var(--soft);
      font-family: ui-monospace, SFMono-Regular, Consolas, "Liberation Mono", monospace;
      font-size: 0.84rem;
      font-weight: 900;
      white-space: normal;
    }

    .book-lines span {
      color: var(--muted);
      font-size: 0.82rem;
    }

    .mini-board {
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      grid-template-rows: repeat(8, 1fr);
      width: 100%;
      aspect-ratio: 1;
      border-bottom: 1px solid rgba(33, 26, 18, 0.16);
      background: #211a12;
    }

    .mini-square {
      display: grid;
      place-items: center;
      aspect-ratio: 1;
      font-family: Georgia, "Times New Roman", serif;
      font-size: clamp(1rem, 3vw, 2rem);
      line-height: 1;
      user-select: none;
    }

    .notation-grid {
      grid-template-columns: 1.1fr 0.9fr 1fr;
    }

    .notation-list {
      display: grid;
      gap: 10px;
      margin: 16px 0 0;
      padding: 0;
      list-style: none;
    }

    .notation-list li {
      display: grid;
      grid-template-columns: 82px 1fr;
      gap: 12px;
      align-items: start;
      color: var(--muted);
    }

    .notation-list code {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 30px;
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.08);
      color: var(--soft);
      font-family: ui-monospace, SFMono-Regular, Consolas, "Liberation Mono", monospace;
      font-weight: 900;
    }

    .notation-card.callout {
      background:
        linear-gradient(135deg, rgba(127, 166, 80, 0.22), rgba(231, 182, 93, 0.14)),
        var(--panel);
    }

    .books-shell {
      display: grid;
      gap: 18px;
    }

    .book-stats {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 12px;
    }

    .book-stat {
      min-height: 88px;
      padding: 15px;
      border: 1px solid rgba(33, 26, 18, 0.14);
      border-radius: var(--radius);
      background: #fff8eb;
    }

    .book-stat strong,
    .book-stat span {
      display: block;
    }

    .book-stat strong {
      color: #211a12;
      font-size: 1.38rem;
      line-height: 1;
    }

    .book-stat span {
      margin-top: 8px;
      color: #5d5144;
      font-size: 0.9rem;
      font-weight: 800;
    }

    .books-controls {
      display: grid;
      grid-template-columns: minmax(220px, 1fr) auto auto auto;
      gap: 12px;
      align-items: end;
    }

    .book-search {
      display: grid;
      gap: 7px;
      color: #2c261f;
      font-weight: 900;
    }

    .book-search input {
      width: 100%;
      min-height: 46px;
      padding: 0 14px;
      border: 1px solid rgba(33, 26, 18, 0.18);
      border-radius: 7px;
      background: #fffdf6;
      color: #211a12;
      font: inherit;
      outline: none;
      transition: border-color 160ms ease, box-shadow 160ms ease;
    }

    .book-search input:focus {
      border-color: var(--green);
      box-shadow: 0 0 0 3px rgba(127, 166, 80, 0.18);
    }

    .book-level-filters {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .book-category-filters {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      padding: 10px;
      border: 1px solid rgba(33, 26, 18, 0.12);
      border-radius: var(--radius);
      background: rgba(255, 248, 235, 0.58);
    }

    .book-filter {
      min-height: 42px;
      padding: 0 12px;
      border: 1px solid rgba(33, 26, 18, 0.17);
      border-radius: 7px;
      background: #f7efe2;
      color: #211a12;
      font: inherit;
      font-size: 0.9rem;
      font-weight: 900;
      cursor: pointer;
      transition: background 160ms ease, border-color 160ms ease, transform 160ms ease;
    }

    .book-filter:hover,
    .book-filter:focus-visible {
      transform: translateY(-1px);
      border-color: var(--green);
      outline: none;
    }

    .book-filter[aria-pressed="true"] {
      border-color: transparent;
      background: var(--green);
      color: #10150d;
    }

    .books-shell .button.secondary {
      border-color: rgba(33, 26, 18, 0.18);
      background: rgba(33, 26, 18, 0.06);
      color: #211a12;
    }

    .books-shell .button.secondary:hover,
    .books-shell .button.secondary:focus-visible {
      background: rgba(33, 26, 18, 0.1);
    }

    .book-verify-note {
      padding: 14px 16px;
      border: 1px solid rgba(127, 166, 80, 0.25);
      border-radius: var(--radius);
      background: rgba(127, 166, 80, 0.12);
      color: #2c261f;
    }

    .book-verify-note strong {
      color: #1f2b16;
    }

    .book-grid {
      display: grid;
      gap: 24px;
    }

    .book-level-section {
      display: grid;
      gap: 14px;
    }

    .book-level-head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      padding-bottom: 10px;
      border-bottom: 1px solid rgba(33, 26, 18, 0.14);
    }

    .book-level-head h3 {
      margin: 0;
      font-size: 1.35rem;
      line-height: 1.15;
    }

    .book-level-head p {
      max-width: 58ch;
      margin: 6px 0 0;
      color: #5d5144;
      font-size: 0.94rem;
    }

    .book-level-head span {
      display: inline-flex;
      align-items: center;
      min-height: 32px;
      padding: 0 10px;
      border-radius: 7px;
      background: rgba(127, 166, 80, 0.14);
      color: var(--green-dark);
      font-size: 0.86rem;
      font-weight: 900;
      white-space: nowrap;
    }

    .book-level-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 18px;
    }

    .book-card {
      position: relative;
      display: grid;
      grid-template-rows: auto 1fr auto;
      min-height: 410px;
      padding: 20px;
      overflow: hidden;
      transition: transform 180ms ease, border-color 180ms ease, box-shadow 180ms ease;
    }

    .book-card:hover,
    .book-card:focus-within {
      transform: translateY(-3px);
      border-color: rgba(127, 166, 80, 0.46);
      box-shadow: 0 22px 46px rgba(82, 55, 25, 0.18);
    }

    .book-card.is-selected {
      border-color: rgba(95, 127, 58, 0.72);
      box-shadow: 0 20px 48px rgba(95, 127, 58, 0.16);
    }

    .book-card-main {
      display: grid;
      gap: 14px;
      align-content: start;
    }

    .book-card-top {
      display: grid;
      grid-template-columns: 76px minmax(0, 1fr);
      gap: 14px;
      align-items: start;
    }

    .book-cover {
      display: grid;
      place-items: center;
      width: 76px;
      aspect-ratio: 3 / 4;
      border: 1px solid rgba(33, 26, 18, 0.18);
      border-radius: 7px;
      background:
        linear-gradient(90deg, rgba(33, 26, 18, 0.14) 0 13px, transparent 13px),
        linear-gradient(145deg, #7fa650, #f0d9b5 72%);
      color: #211a12;
      font-family: Georgia, "Times New Roman", serif;
      font-size: 1.35rem;
      font-weight: 900;
      letter-spacing: 0;
    }

    .book-cover.intermediate {
      background:
        linear-gradient(90deg, rgba(33, 26, 18, 0.14) 0 13px, transparent 13px),
        linear-gradient(145deg, #6fa8dc, #f0d9b5 74%);
    }

    .book-cover.advanced {
      background:
        linear-gradient(90deg, rgba(33, 26, 18, 0.14) 0 13px, transparent 13px),
        linear-gradient(145deg, #e7b65d, #b58863 76%);
    }

    .book-card-copy {
      min-width: 0;
    }

    .book-free-tag {
      display: inline-flex;
      align-items: center;
      width: fit-content;
      min-height: 28px;
      margin: 8px 0 10px;
      padding: 0 9px;
      border: 1px solid rgba(95, 127, 58, 0.22);
      border-radius: 7px;
      background: rgba(127, 166, 80, 0.16);
      color: #26391a;
      font-size: 0.78rem;
      font-weight: 900;
    }

    .book-card h3,
    .book-detail h3 {
      margin-bottom: 8px;
      font-size: 1.18rem;
      line-height: 1.2;
    }

    .book-detail h4 {
      margin: 18px 0 8px;
      font-size: 1rem;
    }

    .book-card p {
      margin-bottom: 14px;
      font-size: 0.95rem;
    }

    .book-meta {
      display: grid;
      gap: 8px;
      margin: 14px 0;
      color: #5d5144;
      font-size: 0.9rem;
    }

    .book-meta span {
      display: inline-flex;
      align-items: center;
      min-height: 30px;
      padding: 6px 9px;
      border: 1px solid rgba(33, 26, 18, 0.13);
      border-radius: 7px;
      background: rgba(181, 136, 99, 0.1);
    }

    .book-source {
      margin-top: 0;
      color: #5d5144;
      font-size: 0.82rem;
      word-break: break-word;
    }

    .book-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 16px;
    }

    .book-detail[hidden] {
      display: none;
    }

    .book-detail {
      padding: 24px;
      scroll-margin-top: 86px;
    }

    .book-reader,
    .book-admin {
      border: 1px solid rgba(33, 26, 18, 0.16);
      border-radius: var(--radius);
      background: #fff8eb;
      color: #211a12;
      box-shadow: 0 18px 40px rgba(82, 55, 25, 0.12);
    }

    .book-reader[hidden] {
      display: none;
    }

    .book-reader {
      overflow: hidden;
      scroll-margin-top: 86px;
    }

    .reader-toolbar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 14px;
      border-bottom: 1px solid rgba(33, 26, 18, 0.14);
      background: #f7efe2;
    }

    .reader-title {
      min-width: 0;
    }

    .reader-title h3 {
      margin: 0;
      font-size: 1.18rem;
      line-height: 1.2;
    }

    .reader-title p {
      margin: 4px 0 0;
      color: #5d5144;
      font-size: 0.9rem;
    }

    .reader-controls {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: center;
      justify-content: flex-end;
    }

    .reader-font-control {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      min-height: 42px;
      padding: 0 10px;
      border: 1px solid rgba(33, 26, 18, 0.14);
      border-radius: 7px;
      background: #fffdf6;
      color: #2c261f;
      font-weight: 900;
    }

    .reader-font-control input {
      width: 96px;
    }

    .reader-layout {
      display: grid;
      grid-template-columns: minmax(190px, 260px) minmax(0, 1fr);
      min-height: 440px;
    }

    .reader-toc {
      padding: 16px;
      border-right: 1px solid rgba(33, 26, 18, 0.14);
      background: #fbf1e3;
    }

    .reader-toc h4,
    .reader-page h4 {
      margin: 0 0 10px;
      font-size: 1rem;
    }

    .reader-toc-list {
      display: grid;
      gap: 8px;
    }

    .reader-toc-button {
      width: 100%;
      min-height: 40px;
      padding: 8px 10px;
      border: 1px solid rgba(33, 26, 18, 0.14);
      border-radius: 7px;
      background: #fff8eb;
      color: #211a12;
      font: inherit;
      font-weight: 900;
      text-align: left;
      cursor: pointer;
    }

    .reader-toc-button[aria-current="true"] {
      border-color: transparent;
      background: var(--green);
      color: #10150d;
    }

    .reader-page {
      padding: clamp(20px, 4vw, 38px);
      background: #fffdf6;
    }

    .reader-page.dark {
      background: #15120f;
      color: #f7f1e6;
    }

    .reader-page.dark p,
    .reader-page.dark li {
      color: #d8ccb9;
    }

    .reader-page p,
    .reader-page li {
      color: #3c332a;
      line-height: 1.75;
    }

    .reader-page ul {
      display: grid;
      gap: 10px;
      margin: 14px 0 0;
      padding-left: 20px;
    }

    .reader-nav {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 24px;
    }

    .reader-nav .button:disabled {
      cursor: default;
      opacity: 0.55;
      transform: none;
    }

    .reader-status {
      min-height: 28px;
      margin-top: 14px;
      color: #5d5144;
      font-weight: 900;
    }

    .book-admin {
      padding: 18px;
    }

    .book-admin summary {
      cursor: pointer;
      font-weight: 900;
    }

    .book-admin p {
      margin: 10px 0 16px;
      color: #5d5144;
    }

    .admin-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 12px;
    }

    .admin-grid label {
      display: grid;
      gap: 6px;
      color: #2c261f;
      font-weight: 900;
    }

    .admin-grid input,
    .admin-grid select,
    .admin-grid textarea {
      width: 100%;
      min-height: 42px;
      padding: 9px 11px;
      border: 1px solid rgba(33, 26, 18, 0.16);
      border-radius: 7px;
      background: #fffdf6;
      color: #211a12;
      font: inherit;
    }

    .admin-grid textarea {
      min-height: 92px;
      resize: vertical;
    }

    .admin-wide {
      grid-column: 1 / -1;
    }

    .admin-list {
      display: grid;
      gap: 8px;
      margin-top: 14px;
    }

    .admin-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      padding: 10px;
      border: 1px solid rgba(33, 26, 18, 0.12);
      border-radius: 7px;
      background: #fffdf6;
    }

    .book-detail-grid {
      display: grid;
      grid-template-columns: minmax(220px, 0.85fr) minmax(0, 1.15fr);
      gap: 22px;
      align-items: start;
    }

    .book-detail-list {
      display: grid;
      grid-template-columns: 118px 1fr;
      gap: 10px 14px;
      margin: 16px 0 0;
    }

    .book-detail-list dt {
      color: #2c261f;
      font-weight: 900;
    }

    .book-detail-list dd {
      margin: 0;
      color: #5d5144;
      word-break: break-word;
    }

    .book-detail a {
      color: var(--green-dark);
      font-weight: 900;
      text-decoration: underline;
      text-underline-offset: 3px;
    }

    .book-empty {
      grid-column: 1 / -1;
      padding: 20px;
      border: 1px dashed rgba(33, 26, 18, 0.22);
      border-radius: var(--radius);
      color: #5d5144;
      background: rgba(255, 248, 235, 0.58);
    }

    .video-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 18px;
    }

    .video-tier {
      margin-top: 26px;
    }

    .video-tier:first-of-type {
      margin-top: 0;
    }

    .video-tier-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 18px;
      margin-bottom: 14px;
    }

    .video-tier-head h3 {
      margin-bottom: 0;
      font-size: 1.35rem;
      line-height: 1.15;
    }

    .video-tier-head p {
      max-width: 58ch;
      margin-bottom: 0;
      color: var(--muted);
      font-size: 0.95rem;
    }

    .video-grid.tier-grid {
      grid-template-columns: repeat(5, minmax(0, 1fr));
    }

    .shorts-tier {
      margin-top: 44px;
      padding-top: 34px;
      border-top: 1px solid rgba(255, 248, 237, 0.12);
      scroll-margin-top: 92px;
    }

    .shorts-title-band {
      display: grid;
      grid-template-columns: 1fr auto;
      gap: 18px;
      align-items: end;
      margin-bottom: 18px;
      padding-bottom: 16px;
      border-bottom: 1px solid rgba(255, 248, 237, 0.08);
    }

    .shorts-title-band .section-kicker {
      margin-bottom: 6px;
    }

    .shorts-title-band h3 {
      margin: 0;
      font-size: clamp(1.85rem, 4vw, 2.65rem);
      line-height: 1.05;
    }

    .shorts-title-band p {
      max-width: 68ch;
      margin: 9px 0 0;
      color: var(--muted);
    }

    .shorts-count {
      display: inline-flex;
      align-items: center;
      min-height: 38px;
      padding: 0 12px;
      border: 1px solid rgba(231, 182, 93, 0.42);
      border-radius: 6px;
      background: rgba(231, 182, 93, 0.13);
      color: var(--gold);
      font-weight: 900;
      white-space: nowrap;
    }

    .shorts-toolbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 14px;
      margin: 0 0 16px;
    }

    .shorts-tabs {
      display: inline-flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .shorts-progress-controls {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      flex-wrap: wrap;
    }

    .shorts-audio-controls {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
      justify-content: flex-end;
    }

    .shorts-tab,
    .shorts-sound-toggle,
    .shorts-resume {
      min-height: 38px;
      padding: 0 12px;
      border: 1px solid rgba(255, 248, 237, 0.14);
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.07);
      color: var(--muted);
      font: inherit;
      font-size: 0.9rem;
      font-weight: 900;
      cursor: pointer;
      transition: background 160ms ease, color 160ms ease, border-color 160ms ease;
    }

    .shorts-tab:hover,
    .shorts-tab:focus-visible,
    .shorts-sound-toggle:hover,
    .shorts-sound-toggle:focus-visible,
    .shorts-resume:hover,
    .shorts-resume:focus-visible {
      color: var(--text);
      border-color: rgba(231, 182, 93, 0.4);
      outline: none;
    }

    .shorts-tab[aria-selected="true"],
    .shorts-sound-toggle[aria-pressed="true"] {
      background: var(--green);
      border-color: transparent;
      color: #10150d;
    }

    .shorts-resume {
      color: var(--text);
      background: rgba(231, 182, 93, 0.13);
      border-color: rgba(231, 182, 93, 0.36);
    }

    .shorts-progress {
      display: inline-flex;
      align-items: center;
      min-height: 38px;
      padding: 0 12px;
      border: 1px solid rgba(255, 248, 237, 0.12);
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.06);
      color: var(--soft);
      font-size: 0.88rem;
      font-weight: 900;
      white-space: nowrap;
    }

    .shorts-volume {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      min-height: 38px;
      padding: 0 10px;
      border: 1px solid rgba(255, 248, 237, 0.14);
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.07);
      color: var(--muted);
      font-size: 0.88rem;
      font-weight: 900;
    }

    .shorts-volume input {
      width: 110px;
      accent-color: var(--green);
      cursor: pointer;
    }

    .shorts-feed {
      position: relative;
      height: calc(100svh - 76px);
      height: calc(100dvh - 76px);
      min-height: 0;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: #111;
      overflow-y: auto;
      overflow-x: hidden;
      scroll-snap-type: y mandatory;
      scroll-behavior: auto;
      scrollbar-width: thin;
      scrollbar-color: rgba(231, 182, 93, 0.58) rgba(255, 255, 255, 0.08);
      overscroll-behavior-y: contain;
      touch-action: pan-y;
      -webkit-overflow-scrolling: touch;
    }

    .shorts-feed::-webkit-scrollbar {
      width: 8px;
    }

    .shorts-feed::-webkit-scrollbar-track {
      background: rgba(255, 255, 255, 0.08);
    }

    .shorts-feed::-webkit-scrollbar-thumb {
      background: rgba(231, 182, 93, 0.58);
      border-radius: 999px;
    }

    .short-slide {
      position: relative;
      display: grid;
      place-items: center;
      min-height: 100%;
      height: 100%;
      padding: 18px;
      scroll-snap-align: start;
      scroll-snap-stop: normal;
      background:
        radial-gradient(circle at 50% 18%, rgba(231, 182, 93, 0.18), transparent 34%),
        linear-gradient(180deg, #17130f, #0d0b09);
      isolation: isolate;
      contain: layout paint style;
      content-visibility: auto;
      contain-intrinsic-size: 100vh;
      contain-intrinsic-size: 100dvh;
    }

    .short-slide.is-filtered-out {
      display: none;
    }

    .short-slide::before {
      content: attr(data-level);
      position: absolute;
      top: 18px;
      left: 18px;
      z-index: 2;
      padding: 6px 10px;
      border: 1px solid rgba(255, 248, 237, 0.16);
      border-radius: 6px;
      background: rgba(17, 15, 13, 0.72);
      color: var(--soft);
      font-size: 0.82rem;
      font-weight: 900;
      backdrop-filter: blur(10px);
    }

    .short-stage {
      position: relative;
      width: auto;
      height: calc(100% - 32px);
      max-height: calc(100% - 32px);
      max-width: calc(100vw - 42px);
      aspect-ratio: 9 / 16;
      border: 1px solid rgba(255, 248, 237, 0.16);
      border-radius: var(--radius);
      background: #050505;
      box-shadow: 0 28px 70px rgba(0, 0, 0, 0.42);
      overflow: hidden;
      transform: translateZ(0);
    }

    .short-frame,
    .short-frame iframe,
    .short-placeholder {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      border: 0;
    }

    .short-frame iframe {
      z-index: 0;
      background: #050505;
    }

    .short-gesture-layer {
      position: absolute;
      inset: 0;
      z-index: 1;
      pointer-events: none;
      touch-action: pan-y;
      background: transparent;
    }

    .short-placeholder {
      display: grid;
      place-items: center;
      background-color: #111;
      background-position: center;
      background-size: cover;
      transform: translateZ(0);
      z-index: 1;
      opacity: 1;
      visibility: visible;
      transition: opacity 180ms ease, visibility 180ms ease;
    }

    .short-placeholder::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(180deg, rgba(0, 0, 0, 0.12), rgba(0, 0, 0, 0.66));
    }

    .short-placeholder::after {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(105deg, transparent 22%, rgba(255, 248, 237, 0.16) 42%, transparent 62%);
      opacity: 0;
      transform: translateX(-120%);
    }

    .short-slide.is-loading .short-placeholder::after {
      opacity: 1;
      animation: shortBufferSweep 1.15s ease-in-out infinite;
    }

    .short-placeholder .play-mark {
      z-index: 2;
    }

    .short-slide.is-loaded .short-placeholder {
      opacity: 0;
      visibility: hidden;
    }

    @keyframes shortBufferSweep {
      to {
        transform: translateX(120%);
      }
    }

    .short-meta {
      position: absolute;
      inset: auto 0 0;
      z-index: 2;
      padding: 82px 16px 16px;
      background: linear-gradient(180deg, transparent, rgba(0, 0, 0, 0.84));
      color: var(--text);
    }

    .short-meta h4 {
      margin: 10px 0 6px;
      font-size: 1.18rem;
      line-height: 1.16;
    }

    .short-meta p {
      margin: 0;
      color: rgba(255, 248, 237, 0.82);
      font-size: 0.92rem;
      line-height: 1.38;
    }

    .short-pill-row {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .short-pill {
      display: inline-flex;
      align-items: center;
      min-height: 26px;
      padding: 0 8px;
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.12);
      color: var(--soft);
      font-size: 0.76rem;
      font-weight: 900;
    }

    .short-pill.creator {
      color: #a9d1f4;
      background: rgba(111, 168, 220, 0.18);
    }

    .short-pill.difficulty {
      color: #10150d;
      background: var(--green);
    }

    .short-pill.category {
      color: var(--gold);
      background: rgba(231, 182, 93, 0.18);
    }

    .short-position {
      position: absolute;
      right: 14px;
      top: 14px;
      z-index: 2;
      color: rgba(255, 248, 237, 0.76);
      font-size: 0.8rem;
      font-weight: 900;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.48);
    }

    .short-actions {
      position: absolute;
      right: 12px;
      top: 44px;
      z-index: 3;
      display: grid;
      gap: 8px;
    }

    .short-action-button {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      border: 1px solid rgba(255, 248, 237, 0.18);
      border-radius: 6px;
      background: rgba(17, 15, 13, 0.74);
      color: var(--text);
      font-size: 1.08rem;
      font-weight: 900;
      cursor: pointer;
      backdrop-filter: blur(10px);
      transition: background var(--speed), border-color var(--speed), transform var(--speed);
    }

    .short-action-button:hover,
    .short-action-button:focus-visible {
      border-color: rgba(231, 182, 93, 0.72);
      background: rgba(231, 182, 93, 0.22);
      outline: none;
      transform: translateY(-1px);
    }

    .short-action-button[aria-pressed="true"] {
      border-color: transparent;
      background: var(--green);
      color: #10150d;
    }

    .short-like[aria-pressed="true"] {
      background: #e9a0a6;
      color: #2a090d;
    }

    .short-bookmark[aria-pressed="true"] {
      background: var(--gold);
      color: #251706;
    }

    .short-share.is-copied {
      border-color: transparent;
      background: #a9d1f4;
      color: #07121c;
    }

    .shorts-feed:fullscreen,
    .shorts-feed:-webkit-full-screen,
    .shorts-feed.is-feed-fullscreen {
      position: fixed;
      inset: 0;
      z-index: 1000;
      width: 100vw;
      height: 100vh;
      height: 100dvh;
      max-height: none;
      border: 0;
      border-radius: 0;
      background: #050505;
      scrollbar-width: none;
      scroll-snap-type: y mandatory;
      overscroll-behavior: none;
      touch-action: pan-y;
    }

    .shorts-feed:fullscreen::-webkit-scrollbar,
    .shorts-feed:-webkit-full-screen::-webkit-scrollbar,
    .shorts-feed.is-feed-fullscreen::-webkit-scrollbar {
      display: none;
    }

    .shorts-feed:fullscreen .short-slide,
    .shorts-feed:-webkit-full-screen .short-slide,
    .shorts-feed.is-feed-fullscreen .short-slide {
      min-height: 100vh;
      min-height: 100dvh;
      height: 100vh;
      height: 100dvh;
      padding: 0;
      background: #050505;
    }

    .shorts-feed:fullscreen .short-stage,
    .shorts-feed:-webkit-full-screen .short-stage,
    .shorts-feed.is-feed-fullscreen .short-stage {
      width: min(100vw, 56.25vh);
      width: min(100vw, 56.25dvh);
      height: min(100vh, 177.78vw);
      height: min(100dvh, 177.78vw);
      max-width: 100vw;
      max-height: 100vh;
      max-height: 100dvh;
      border: 0;
      border-radius: 0;
      box-shadow: none;
    }

    .shorts-feed:fullscreen .short-gesture-layer,
    .shorts-feed:-webkit-full-screen .short-gesture-layer,
    .shorts-feed.is-feed-fullscreen .short-gesture-layer {
      pointer-events: auto;
      cursor: pointer;
    }

    .shorts-feed:fullscreen .short-slide::before,
    .shorts-feed:-webkit-full-screen .short-slide::before,
    .shorts-feed.is-feed-fullscreen .short-slide::before,
    .shorts-feed:fullscreen .short-action-button,
    .shorts-feed:-webkit-full-screen .short-action-button,
    .shorts-feed.is-feed-fullscreen .short-action-button {
      backdrop-filter: none;
    }

    .shorts-feed:fullscreen .short-slide::before,
    .shorts-feed:-webkit-full-screen .short-slide::before,
    .shorts-feed.is-feed-fullscreen .short-slide::before {
      top: 14px;
      left: 14px;
    }

    .shorts-feed.is-mobile-portrait-fullscreen {
      height: 100svh;
      height: 100dvh;
      overscroll-behavior: none;
      touch-action: pan-y;
    }

    .shorts-feed.is-mobile-portrait-fullscreen .short-stage {
      aspect-ratio: 9 / 16;
      width: min(100vw, 56.25svh);
      width: min(100vw, 56.25dvh);
      height: min(100svh, 177.78vw);
      height: min(100dvh, 177.78vw);
    }

    .short-slide.is-active .short-stage {
      border-color: rgba(231, 182, 93, 0.58);
      box-shadow: 0 28px 80px rgba(231, 182, 93, 0.16), 0 24px 64px rgba(0, 0, 0, 0.44);
    }

    .shorts-level + .shorts-level {
      margin-top: 30px;
    }

    .shorts-level-head {
      display: flex;
      justify-content: space-between;
      align-items: end;
      gap: 16px;
      margin-bottom: 14px;
    }

    .shorts-level-head h4 {
      margin: 0;
      font-size: 1.28rem;
      line-height: 1.15;
    }

    .shorts-level-head p {
      max-width: 62ch;
      margin: 6px 0 0;
      color: var(--muted);
      font-size: 0.94rem;
    }

    .shorts-level-badge {
      display: inline-flex;
      align-items: center;
      min-height: 32px;
      padding: 0 10px;
      border-radius: 6px;
      background: rgba(127, 166, 80, 0.17);
      color: #bce38c;
      font-size: 0.86rem;
      font-weight: 900;
      white-space: nowrap;
    }

    .shorts-grid {
      align-items: start;
    }

    .shorts-grid .video-card {
      background:
        linear-gradient(180deg, rgba(231, 182, 93, 0.12), rgba(127, 166, 80, 0.08)),
        var(--card);
    }

    .shorts-grid .video-card {
      scroll-margin-top: 92px;
    }

    .shorts-grid .video-frame {
      aspect-ratio: 9 / 16;
    }

    .shorts-grid .play-mark {
      width: 54px;
      height: 54px;
    }

    .shorts-grid .video-body {
      padding: 14px;
    }

    .shorts-grid .video-body h3 {
      font-size: 1rem;
    }

    .shorts-grid .video-body p {
      font-size: 0.9rem;
    }

    .video-card {
      overflow: hidden;
      transition: transform 180ms ease, border-color 180ms ease, box-shadow 180ms ease;
    }

    .video-card:hover {
      transform: translateY(-3px);
      border-color: rgba(231, 182, 93, 0.45);
      box-shadow: 0 20px 44px rgba(0, 0, 0, 0.24);
    }

    .video-card.video-resume {
      border-color: rgba(231, 182, 93, 0.72);
      box-shadow: 0 22px 48px rgba(231, 182, 93, 0.18);
    }

    .video-frame {
      position: relative;
      aspect-ratio: 16 / 9;
      background: #111;
    }

    .video-frame iframe {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      border: 0;
    }

    .video-thumb {
      position: absolute;
      inset: 0;
      display: grid;
      place-items: center;
      width: 100%;
      height: 100%;
      border: 0;
      background-color: #111;
      background-position: center;
      background-size: cover;
      color: var(--text);
      cursor: pointer;
      overflow: hidden;
    }

    .video-thumb.is-thumb-loading {
      background:
        linear-gradient(105deg, transparent 20%, rgba(255, 248, 237, 0.12) 42%, transparent 64%),
        #111;
      background-size: 220% 100%, auto;
      animation: shortBufferSweep 1.2s ease-in-out infinite;
    }

    .video-thumb::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(180deg, rgba(0, 0, 0, 0.08), rgba(0, 0, 0, 0.58));
    }

    .play-mark {
      position: relative;
      display: grid;
      place-items: center;
      width: 62px;
      height: 62px;
      border: 2px solid rgba(255, 248, 237, 0.86);
      border-radius: 50%;
      background: rgba(32, 29, 26, 0.68);
      box-shadow: 0 12px 28px rgba(0, 0, 0, 0.35);
    }

    .play-mark::before {
      content: "";
      width: 0;
      height: 0;
      margin-left: 5px;
      border-top: 12px solid transparent;
      border-bottom: 12px solid transparent;
      border-left: 18px solid var(--text);
    }

    .video-modal {
      position: fixed;
      inset: 0;
      z-index: 60;
      display: grid;
      place-items: center;
      padding: 24px;
      background: rgba(18, 15, 12, 0.84);
      backdrop-filter: blur(10px);
    }

    .video-modal[hidden] {
      display: none;
    }

    .video-modal-panel {
      width: min(100%, 1040px);
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: #181512;
      box-shadow: var(--shadow);
      overflow: hidden;
    }

    .video-modal.is-short .video-modal-panel {
      width: min(100%, 430px, calc((100vh - 120px) * 9 / 16));
    }

    .video-modal-bar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 14px;
      padding: 12px 14px;
      border-bottom: 1px solid var(--line);
    }

    .video-modal-title {
      margin: 0;
      color: var(--text);
      font-size: 0.98rem;
      font-weight: 900;
    }

    .video-close {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      border: 1px solid var(--line);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.08);
      color: var(--text);
      font-size: 1.2rem;
      line-height: 1;
      cursor: pointer;
    }

    .video-modal-frame {
      position: relative;
      aspect-ratio: 16 / 9;
      background: #000;
    }

    .video-modal.is-short .video-modal-frame {
      aspect-ratio: 9 / 16;
    }

    .video-modal-frame iframe {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      border: 0;
    }

    .video-body {
      padding: 18px;
    }

    .video-body .badge {
      margin-bottom: 11px;
    }

    .badge.duration {
      margin-left: 6px;
      background: rgba(231, 182, 93, 0.18);
      color: var(--gold);
    }

    .badge.creator {
      margin-left: 6px;
      background: rgba(111, 168, 220, 0.16);
      color: #a9d1f4;
    }

    .video-body p {
      margin-bottom: 0;
      font-size: 0.95rem;
    }

    .puzzle-shell {
      display: grid;
      grid-template-columns: minmax(300px, 500px) minmax(320px, 1fr);
      gap: 24px;
      padding: 18px;
      align-items: start;
    }

    .puzzle-board-wrap {
      position: relative;
      align-self: start;
      border: 8px solid #211a12;
      border-radius: var(--radius);
      background: #211a12;
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.26);
      overflow: hidden;
    }

    .puzzle-board {
      width: 100%;
      aspect-ratio: 1;
    }

    .puzzle-square {
      position: relative;
      font-size: clamp(1.4rem, 5vw, 3.55rem);
    }

    .puzzle-square.target::after {
      content: "";
      position: absolute;
      width: 34%;
      height: 34%;
      border: 3px solid rgba(127, 166, 80, 0.8);
      border-radius: 50%;
      pointer-events: none;
    }

    .play-square {
      border: 0;
      padding: 0;
      cursor: pointer;
      transition: background var(--move-speed) ease, box-shadow var(--move-speed) ease, transform var(--move-speed) ease;
    }

    .play-square:hover,
    .play-square:focus-visible {
      z-index: 1;
      outline: none;
      box-shadow: inset 0 0 0 4px rgba(255, 248, 237, 0.36);
    }

    .play-square.selected {
      box-shadow: inset 0 0 0 5px rgba(231, 182, 93, 0.88);
    }

    .play-square.legal::after,
    .play-square.capture::after {
      content: "";
      position: absolute;
      width: 28%;
      height: 28%;
      border-radius: 50%;
      background: rgba(32, 29, 26, 0.34);
      pointer-events: none;
    }

    .play-square.capture::after {
      width: 72%;
      height: 72%;
      border: 4px solid rgba(216, 111, 98, 0.7);
      background: transparent;
    }

    .play-square.last-move {
      background: linear-gradient(rgba(231, 182, 93, 0.42), rgba(231, 182, 93, 0.42)), var(--board-light);
    }

    .play-square.dark.last-move {
      background: linear-gradient(rgba(231, 182, 93, 0.35), rgba(231, 182, 93, 0.35)), var(--board-dark);
    }

    .play-square.in-check {
      background: linear-gradient(rgba(216, 111, 98, 0.72), rgba(216, 111, 98, 0.72)), var(--board-dark);
    }

    .play-square.threat {
      box-shadow: inset 0 0 0 5px rgba(216, 111, 98, 0.78);
    }

    .play-square.dragging {
      opacity: 0.72;
      transform: scale(0.96);
    }

    .play-square.is-ai-thinking {
      cursor: wait;
    }

    .coach-panel {
      gap: 14px;
    }

    .coach-levels {
      grid-template-columns: repeat(3, minmax(0, 1fr));
      margin-bottom: 0;
    }

    .preference-panel {
      display: grid;
      gap: 12px;
      margin-bottom: 18px;
      padding: 16px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--panel);
    }

    .preference-panel h3,
    .preference-note {
      margin: 0;
    }

    .preference-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 10px;
    }

    .preference-grid label {
      display: grid;
      gap: 5px;
      color: var(--muted);
      font-size: 0.84rem;
      font-weight: 900;
    }

    .preference-grid select {
      min-height: 38px;
      border: 1px solid var(--line);
      border-radius: 7px;
      background: var(--panel-2);
      color: var(--text);
      font: inherit;
      font-weight: 800;
    }

    .preference-note {
      color: var(--gold);
      font-weight: 900;
    }

    .captured-row {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 10px;
    }

    .captured-row > div,
    .move-history,
    .guided-review {
      border: 1px solid rgba(255, 248, 237, 0.12);
      border-radius: var(--radius);
      background: rgba(0, 0, 0, 0.14);
      padding: 12px;
    }

    .captured-row strong {
      display: block;
      margin-bottom: 6px;
      font-size: 0.84rem;
    }

    .captured-pieces {
      min-height: 34px;
      font-family: Georgia, "Times New Roman", serif;
      font-size: 1.55rem;
      line-height: 1.15;
    }

    .guided-review {
      display: grid;
      gap: 10px;
    }

    .guided-review[hidden] {
      display: none;
    }

    .review-moment {
      display: grid;
      gap: 5px;
      padding-top: 10px;
      border-top: 1px solid rgba(255, 248, 237, 0.1);
    }

    .review-moment span {
      color: var(--muted);
      font-size: 0.9rem;
      line-height: 1.45;
    }

    .principle-strip {
      display: grid;
      grid-template-columns: repeat(5, minmax(0, 1fr));
      gap: 10px;
      margin-bottom: 18px;
    }

    .principle-strip span {
      padding: 12px;
      border: 1px solid var(--line);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.045);
      color: var(--soft);
      font-weight: 900;
    }

    .move-history {
      display: grid;
      gap: 6px;
      max-height: 160px;
      overflow: auto;
      color: var(--muted);
      font-size: 0.92rem;
    }

    .move-pair {
      display: grid;
      grid-template-columns: 42px 1fr 1fr;
      gap: 8px;
      align-items: center;
    }

    .move-pair strong {
      color: var(--gold);
    }

    .coordinates {
      position: absolute;
      inset: 0;
      pointer-events: none;
      font-size: 0.72rem;
      font-weight: 800;
      color: rgba(33, 26, 18, 0.72);
    }

    .coordinates span {
      position: absolute;
    }

    .puzzle-info {
      display: grid;
      gap: 12px;
      min-width: 0;
    }

    .puzzle-brief {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 8px;
    }

    .puzzle-brief span,
    .puzzle-complete {
      padding: 10px;
      border: 1px solid rgba(33, 26, 18, 0.12);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.52);
      color: #3a3127;
      font-weight: 800;
    }

    .puzzle-tags {
      margin: 0;
    }

    .puzzle-tags span {
      background: rgba(33, 26, 18, 0.06);
      color: #3a3127;
    }

    .puzzle-complete {
      display: grid;
      gap: 8px;
      margin-bottom: 14px;
      border-left: 4px solid var(--green);
    }

    .puzzle-complete[hidden] {
      display: none;
    }

    .puzzle-complete p {
      margin: 0;
    }

    .puzzle-board-wrap.is-correct {
      animation: puzzlePulse 420ms ease;
    }

    .puzzle-board-wrap.is-wrong {
      animation: puzzleShake 280ms ease;
    }

    @keyframes puzzlePulse {
      50% {
        box-shadow: 0 0 0 5px rgba(127, 166, 80, 0.42), 0 15px 30px rgba(0, 0, 0, 0.26);
      }
    }

    @keyframes puzzleShake {
      20% { transform: translateX(-5px); }
      40% { transform: translateX(5px); }
      60% { transform: translateX(-3px); }
      80% { transform: translateX(3px); }
    }

    .puzzle-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .daily-puzzle-badge {
      background: rgba(231, 182, 93, 0.22);
      color: #704d13;
    }

    .puzzle-plan-selector {
      grid-template-columns: repeat(5, minmax(0, 1fr));
      margin: 0;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      min-height: 28px;
      padding: 0 9px;
      border-radius: 999px;
      background: rgba(127, 166, 80, 0.16);
      color: var(--green-dark);
      font-size: 0.82rem;
      font-weight: 900;
    }

    .puzzle-stats {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 10px;
    }

    .stat-pill {
      min-height: 66px;
      padding: 10px 12px;
      border: 1px solid rgba(33, 26, 18, 0.14);
      border-radius: var(--radius);
      background: #f7efe2;
    }

    .stat-pill strong,
    .stat-pill span {
      display: block;
    }

    .stat-pill strong {
      color: #211a12;
      font-size: 1.08rem;
      line-height: 1.1;
    }

    .stat-pill span {
      margin-top: 5px;
      color: #5d5144;
      font-size: 0.82rem;
      font-weight: 800;
    }

    .progress-track {
      height: 9px;
      overflow: hidden;
      border-radius: 999px;
      background: rgba(33, 26, 18, 0.12);
    }

    .progress-fill {
      display: block;
      width: 0;
      height: 100%;
      border-radius: inherit;
      background: var(--green);
      transition: width 180ms ease;
    }

    .beginner-progress {
      display: grid;
      gap: 12px;
      padding: 14px;
      border: 1px solid rgba(127, 166, 80, 0.24);
      border-radius: var(--radius);
      background: rgba(127, 166, 80, 0.1);
    }

    .puzzle-progress-drawer {
      border: 1px solid rgba(33, 26, 18, 0.12);
      border-radius: var(--radius);
      background: rgba(255, 255, 255, 0.45);
    }

    .puzzle-progress-drawer summary {
      display: flex;
      justify-content: space-between;
      gap: 10px;
      padding: 12px 14px;
      color: #2c261f;
      font-weight: 900;
      cursor: pointer;
      list-style: none;
    }

    .puzzle-progress-drawer summary::-webkit-details-marker {
      display: none;
    }

    .puzzle-progress-drawer summary::after {
      content: "+";
      color: var(--green-dark);
      font-size: 1.15rem;
    }

    .puzzle-progress-drawer[open] summary::after {
      content: "-";
    }

    .puzzle-progress-drawer .beginner-progress {
      border-width: 1px 0 0;
      border-radius: 0 0 var(--radius) var(--radius);
      background: rgba(127, 166, 80, 0.08);
    }

    .progress-mini-stats,
    .achievement-row,
    .mini-game-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: center;
    }

    .xp-pill,
    .achievement-badge {
      display: inline-flex;
      align-items: center;
      min-height: 30px;
      padding: 0 10px;
      border-radius: 7px;
      font-size: 0.82rem;
      font-weight: 900;
    }

    .xp-pill {
      background: rgba(231, 182, 93, 0.16);
      color: var(--gold);
    }

    .level-pill {
      background: rgba(127, 166, 80, 0.18);
      color: #dfeecf;
    }

    .achievement-badge {
      border: 1px solid rgba(33, 26, 18, 0.14);
      background: rgba(255, 248, 235, 0.72);
      color: #5d5144;
    }

    .achievement-badge.unlocked {
      background: var(--green);
      color: #10150d;
    }

    .game-reward-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 10px;
    }

    .game-unlock {
      display: inline-flex;
      align-items: center;
      min-height: 30px;
      padding: 0 10px;
      border-radius: 7px;
      background: rgba(111, 168, 220, 0.16);
      color: var(--soft);
      font-size: 0.82rem;
      font-weight: 900;
    }

    body.no-pressure .pressure-rating {
      display: none;
    }

    .habit-reward,
    .simple-coach {
      margin: 0;
      color: #2c261f;
      font-weight: 800;
    }

    .habit-reward {
      padding: 10px 12px;
      border: 1px solid rgba(231, 182, 93, 0.34);
      border-radius: var(--radius);
      background: rgba(231, 182, 93, 0.16);
    }

    .weekly-chart {
      display: grid;
      grid-template-columns: repeat(7, minmax(0, 1fr));
      gap: 6px;
      align-items: end;
      min-height: 78px;
    }

    .week-bar {
      display: grid;
      align-content: end;
      gap: 4px;
      min-height: 78px;
      color: #5d5144;
      font-size: 0.72rem;
      font-weight: 900;
      text-align: center;
    }

    .week-bar span {
      display: block;
      min-height: 8px;
      border-radius: 999px 999px 4px 4px;
      background: var(--green);
    }

    .confetti-burst {
      position: fixed;
      inset: 0;
      z-index: 2000;
      pointer-events: none;
      overflow: hidden;
    }

    .confetti-piece {
      position: absolute;
      top: -12px;
      width: 8px;
      height: 14px;
      border-radius: 3px;
      animation: confettiFall 900ms ease-out forwards;
    }

    @keyframes confettiFall {
      to {
        transform: translateY(105vh) rotate(540deg);
        opacity: 0;
      }
    }

    .celebration-toast {
      position: fixed;
      left: 50%;
      top: 82px;
      z-index: 2100;
      display: grid;
      gap: 4px;
      min-width: min(300px, calc(100vw - 28px));
      padding: 16px 18px;
      border: 1px solid rgba(231, 182, 93, 0.5);
      border-radius: var(--radius);
      background: rgba(27, 22, 17, 0.94);
      color: var(--soft);
      text-align: center;
      box-shadow: 0 18px 42px rgba(0, 0, 0, 0.28);
      transform: translate(-50%, -12px);
      animation: celebrationPop 1600ms ease forwards;
    }

    .celebration-toast strong {
      color: var(--gold);
      font-size: 1.16rem;
    }

    .celebration-toast span {
      font-weight: 900;
    }

    @keyframes celebrationPop {
      10%, 78% {
        opacity: 1;
        transform: translate(-50%, 0);
      }
      to {
        opacity: 0;
        transform: translate(-50%, -16px);
      }
    }

    .puzzle-hint {
      min-height: 48px;
      margin: 0;
      padding: 11px 13px;
      border: 1px solid rgba(127, 166, 80, 0.28);
      border-radius: var(--radius);
      background: rgba(127, 166, 80, 0.12);
      color: #2c261f;
    }

    .answers {
      display: none;
      gap: 10px;
      margin: 18px 0;
    }

    .answer-button {
      width: 100%;
      min-height: 48px;
      padding: 12px 14px;
      border: 1px solid rgba(33, 26, 18, 0.18);
      border-radius: 7px;
      background: #f7efe2;
      color: #211a12;
      font: inherit;
      font-weight: 800;
      text-align: left;
      cursor: pointer;
      transition: border-color 160ms ease, background 160ms ease, transform 160ms ease;
    }

    .answer-button:hover,
    .answer-button:focus-visible {
      transform: translateX(2px);
      border-color: var(--green);
      outline: none;
    }

    .answer-button:disabled {
      cursor: default;
      transform: none;
      opacity: 0.86;
    }

    .answer-button.correct {
      border-color: var(--green);
      background: #dfeecf;
    }

    .answer-button.wrong {
      border-color: var(--danger);
      background: #f8ded9;
    }

    .feedback {
      min-height: 64px;
      margin: 0 0 18px;
      padding: 12px 14px;
      border-left: 4px solid var(--green);
      background: rgba(127, 166, 80, 0.12);
      color: #2c261f;
    }

    .puzzle-info .thinking-checklist {
      margin: 12px 0;
    }

    .puzzle-info .thinking-checklist li {
      color: #3a3127;
      font-size: 0.9rem;
    }

    .vision-drill {
      display: grid;
      gap: 8px;
      margin: 12px 0;
      padding: 12px;
      border: 1px solid rgba(33, 26, 18, 0.12);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.48);
    }

    .vision-drill p,
    .vision-drill small {
      margin: 0;
      color: #3a3127;
      line-height: 1.45;
    }

    .puzzle-actions {
      display: grid;
      gap: 8px;
      margin-top: 2px;
    }

    .puzzle-action-row {
      display: grid;
      grid-template-columns: repeat(5, minmax(0, 1fr));
      gap: 8px;
    }

    .puzzle-action-row.primary {
      grid-template-columns: 1.2fr 1.2fr 1fr;
    }

    .puzzle-action-row.utility {
      grid-template-columns: repeat(3, minmax(0, 1fr));
    }

    .puzzle-action-row .button {
      min-height: 42px;
      padding-inline: 10px;
    }

    .study-plan {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 18px;
      align-items: start;
    }

    .plan-panel {
      padding: 24px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--panel);
    }

    .plan-panel h3 {
      margin-bottom: 12px;
      font-size: 1.25rem;
    }

    .plan-panel p {
      margin: 0 0 16px;
      color: var(--muted);
    }

    .plan-panel.wide {
      grid-column: 1 / -1;
      padding: 0;
      border: 0;
      background: transparent;
    }

    .plan-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 16px;
    }

    .plan-meta .badge {
      background: rgba(127, 166, 80, 0.16);
      color: #dfeecf;
    }

    .plan-list {
      display: grid;
      gap: 12px;
      margin: 0;
      padding: 0;
      list-style: none;
      color: var(--muted);
    }

    .plan-list li {
      display: grid;
      grid-template-columns: 42px 1fr;
      gap: 12px;
      align-items: start;
    }

    .plan-list a {
      color: inherit;
      text-decoration: none;
    }

    .plan-list a:hover,
    .plan-list a:focus-visible {
      color: var(--soft);
      text-decoration: underline;
    }

    .plan-list span {
      display: grid;
      place-items: center;
      width: 36px;
      height: 36px;
      border-radius: 50%;
      background: rgba(231, 182, 93, 0.16);
      color: var(--gold);
      font-weight: 900;
    }

    .plan-focus {
      margin-top: 18px;
      padding: 13px 14px;
      border: 1px solid rgba(231, 182, 93, 0.24);
      border-radius: 7px;
      background: rgba(231, 182, 93, 0.1);
      color: #f3e3c1;
      font-weight: 800;
    }

    .daily-trainer {
      display: grid;
      gap: 18px;
    }

    .trainer-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 18px;
    }

    .trainer-head p {
      max-width: 68ch;
    }

    .trainer-form {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 12px;
      padding: 16px;
      border: 1px solid rgba(239, 229, 211, 0.12);
      border-radius: var(--radius);
      background: rgba(255, 255, 255, 0.035);
    }

    .trainer-form > label,
    .trainer-field {
      display: grid;
      gap: 8px;
      margin: 0;
      color: var(--muted);
      font-size: 0.88rem;
      font-weight: 800;
    }

    .trainer-form select,
    .trainer-form input[type="range"] {
      width: 100%;
    }

    .trainer-form select {
      min-height: 44px;
      padding: 0 12px;
      border: 1px solid rgba(239, 229, 211, 0.16);
      border-radius: 7px;
      background: #211d1a;
      color: var(--text);
      font: inherit;
      font-weight: 800;
    }

    .trainer-form input[type="range"] {
      accent-color: var(--green);
    }

    .trainer-wide {
      grid-column: 1 / -1;
    }

    .trainer-field {
      padding: 0;
      border: 0;
    }

    .trainer-field legend {
      padding: 0;
      color: var(--muted);
    }

    .trainer-check-grid {
      display: grid;
      grid-template-columns: repeat(6, minmax(0, 1fr));
      gap: 8px;
    }

    .trainer-check {
      display: flex;
      align-items: center;
      gap: 8px;
      min-height: 38px;
      padding: 0 10px;
      border: 1px solid rgba(239, 229, 211, 0.13);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.045);
      color: var(--text);
      cursor: pointer;
    }

    .trainer-check input {
      accent-color: var(--green);
    }

    .trainer-output {
      display: grid;
      gap: 14px;
    }

    .trainer-summary {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 10px;
    }

    .trainer-stat {
      min-height: 88px;
      padding: 14px;
      border: 1px solid rgba(239, 229, 211, 0.12);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.045);
    }

    .trainer-stat strong {
      display: block;
      color: var(--gold);
      font-size: 1.12rem;
      line-height: 1.2;
    }

    .trainer-stat span {
      display: block;
      margin-top: 6px;
      color: var(--muted);
      font-size: 0.82rem;
      font-weight: 800;
    }

    .trainer-progress {
      height: 10px;
      overflow: hidden;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.1);
    }

    .trainer-progress span {
      display: block;
      width: 0;
      height: 100%;
      border-radius: inherit;
      background: var(--green);
      transition: width 180ms ease;
    }

    .training-task-list {
      display: grid;
      gap: 10px;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .training-task {
      display: grid;
      grid-template-columns: auto minmax(0, 1fr) auto;
      gap: 12px;
      align-items: center;
      min-height: 76px;
      padding: 13px;
      border: 1px solid rgba(239, 229, 211, 0.12);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.035);
    }

    .training-task.is-complete {
      border-color: rgba(127, 166, 80, 0.34);
      background: rgba(127, 166, 80, 0.1);
    }

    .training-task input {
      width: 20px;
      height: 20px;
      accent-color: var(--green);
    }

    .training-task strong,
    .training-task small {
      display: block;
    }

    .training-task small {
      margin-top: 4px;
      color: var(--muted);
      line-height: 1.45;
    }

    .training-time {
      display: inline-flex;
      align-items: center;
      min-height: 30px;
      padding: 0 9px;
      border-radius: 7px;
      background: rgba(231, 182, 93, 0.14);
      color: var(--gold);
      font-size: 0.82rem;
      font-weight: 900;
      white-space: nowrap;
    }

    .trainer-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
    }

    .trainer-patterns {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .trainer-patterns span {
      padding: 7px 10px;
      border: 1px solid rgba(239, 229, 211, 0.13);
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.045);
      color: var(--muted);
      font-size: 0.82rem;
      font-weight: 800;
    }

    .trainer-patterns .is-active {
      border-color: rgba(127, 166, 80, 0.42);
      background: rgba(127, 166, 80, 0.16);
      color: var(--text);
    }

    .trainer-note {
      margin: 0;
      color: var(--muted);
      font-size: 0.92rem;
    }

    .weekly-roadmap {
      display: grid;
      grid-template-columns: repeat(7, minmax(0, 1fr));
      gap: 10px;
      margin-top: 16px;
    }

    .day-card {
      display: block;
      min-height: 136px;
      padding: 14px;
      border: 1px solid rgba(239, 229, 211, 0.12);
      border-radius: 7px;
      background: rgba(255, 255, 255, 0.035);
      color: inherit;
      text-decoration: none;
      transition: transform 160ms ease, border-color 160ms ease, background 160ms ease;
    }

    .day-card:hover,
    .day-card:focus-visible {
      transform: translateY(-2px);
      border-color: rgba(231, 182, 93, 0.45);
      background: rgba(231, 182, 93, 0.08);
    }

    .day-card strong {
      display: block;
      margin-bottom: 8px;
      color: var(--gold);
      font-size: 0.86rem;
      text-transform: uppercase;
      letter-spacing: 0;
    }

    .day-card span {
      display: block;
      margin-bottom: 7px;
      color: var(--cream);
      font-weight: 900;
    }

    .day-card p {
      margin: 0;
      font-size: 0.92rem;
      line-height: 1.5;
    }

    .footer {
      padding: 34px 0;
      border-top: 1px solid var(--line);
      color: var(--muted);
      background: #181512;
    }

    .footer .wrap {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      flex-wrap: wrap;
    }

    .hidden {
      display: none;
    }

    @media (max-width: 980px) {
      .hero-board {
        right: -230px;
        width: min(720px, 94vw);
        opacity: 0.72;
      }

      .lesson-grid,
      .adventure-grid,
      .mission-grid,
      .rules-grid,
      .opening-grid,
      .book-level-grid,
      .notation-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .video-grid,
      .video-grid.tier-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .adventure-play,
      .puzzle-shell,
      .book-detail-grid,
      .study-plan,
      .gentle-start {
        grid-template-columns: 1fr;
      }

      .weekly-roadmap {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .lesson-flow {
        grid-template-columns: repeat(3, minmax(0, 1fr));
      }

      .gentle-form {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .trainer-form,
      .trainer-summary,
      .preference-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .trainer-check-grid {
        grid-template-columns: repeat(3, minmax(0, 1fr));
      }

      .puzzle-board-wrap {
        max-width: 540px;
        margin: 0 auto;
        width: 100%;
      }
    }

    @media (max-width: 760px) {
      .nav {
        align-items: flex-start;
        flex-direction: column;
        padding: 13px 0;
      }

      .nav-links {
        width: 100%;
        justify-content: flex-start;
        overflow-x: auto;
        flex-wrap: nowrap;
        padding-bottom: 5px;
        scroll-snap-type: x proximity;
      }

      .nav-group {
        flex: 0 0 auto;
        scroll-snap-align: start;
      }

      .nav-group-label {
        padding-left: 6px;
      }

      .hero {
        min-height: auto;
      }

      .hero-inner {
        padding: 56px 0 44px;
      }

      .hero-layout {
        grid-template-columns: 1fr;
        gap: 24px;
      }

      .home-dashboard {
        max-width: 680px;
      }

      .hero-board {
        right: -270px;
        top: 48%;
        width: 760px;
      }

      h1 {
        max-width: 8ch;
      }

      .hero-metrics,
      .section-head {
        grid-template-columns: 1fr;
      }

      .hero-metrics {
        display: grid;
      }

      .section-head {
        display: grid;
        align-items: start;
      }

      .video-tier-head {
        display: grid;
        align-items: start;
      }

      .shorts-title-band {
        grid-template-columns: 1fr;
        align-items: start;
      }

      .shorts-toolbar {
        display: grid;
        align-items: start;
      }

      .shorts-level-head {
        display: grid;
        align-items: start;
      }

      .book-stats {
        grid-template-columns: 1fr;
      }

      .books-controls {
        grid-template-columns: 1fr;
        align-items: stretch;
      }

      .book-level-filters {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .book-category-filters {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .reader-toolbar,
      .reader-controls {
        display: grid;
        justify-content: stretch;
      }

      .reader-layout,
      .admin-grid {
        grid-template-columns: 1fr;
      }

      .reader-toc {
        border-right: 0;
        border-bottom: 1px solid rgba(33, 26, 18, 0.14);
      }

      .shorts-feed {
        height: calc(100svh - 64px);
        height: calc(100dvh - 64px);
      }

      .short-slide {
        padding: 12px;
      }

      .short-slide::before {
        top: 12px;
        left: 12px;
        max-width: calc(100% - 118px);
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }

      .path-tabs {
        width: 100%;
      }

      section {
        padding: 56px 0;
      }
    }

    @media (max-width: 580px) {
      .lesson-grid,
      .adventure-grid,
      .mission-grid,
      .rules-grid,
      .opening-grid,
      .book-level-grid,
      .notation-grid,
      .video-grid,
      .video-grid.tier-grid,
      .mission-selector,
      .lesson-flow,
      .puzzle-shell,
      .study-plan,
      .puzzle-stats,
      .captured-row {
        grid-template-columns: 1fr;
      }

      .hero-metrics {
        grid-template-columns: 1fr;
      }

      .hero-actions {
        align-items: stretch;
      }

      .home-start-flow,
      .home-stat-grid,
      .quick-practice {
        grid-template-columns: 1fr;
      }

      .home-dashboard {
        padding: 14px;
      }

      .weekly-roadmap {
        grid-template-columns: 1fr;
      }

      .trainer-head,
      .trainer-form,
      .trainer-summary,
      .trainer-check-grid,
      .preference-grid,
      .training-task,
      .lesson-card-footer,
      .gentle-form,
      .gentle-task {
        grid-template-columns: 1fr;
      }

      .trainer-head {
        display: grid;
        align-items: start;
      }

      .lesson-card-footer {
        display: grid;
        align-items: start;
      }

      .gentle-start {
        padding: 16px;
      }

      .gentle-task .button {
        width: 100%;
      }

      .training-time {
        width: fit-content;
      }

      .button {
        width: 100%;
        min-height: 52px;
        font-size: 1rem;
      }

      .puzzle-actions,
      .puzzle-action-row,
      .puzzle-action-row.primary,
      .puzzle-action-row.utility,
      .coach-levels,
      .progress-mini-stats,
      .achievement-row,
      .puzzle-brief {
        display: grid;
        grid-template-columns: 1fr;
      }

      .puzzle-actions .button,
      .mission-button,
      .xp-pill,
      .achievement-badge {
        min-height: 46px;
        justify-content: center;
      }

      .puzzle-board-wrap {
        border-width: 5px;
      }

      .puzzle-square {
        font-size: clamp(1.85rem, 10vw, 3.2rem);
      }

      .beginner-progress,
      .puzzle-shell,
      .lesson-card {
        padding: 14px;
      }

      .book-actions {
        display: grid;
      }

      .reader-nav,
      .admin-row {
        display: grid;
      }

      .book-level-head,
      .book-card-top {
        grid-template-columns: 1fr;
      }

      .book-level-head {
        display: grid;
        align-items: start;
      }

      .shorts-tabs,
      .shorts-progress-controls,
      .shorts-audio-controls,
      .shorts-volume,
      .shorts-sound-toggle,
      .shorts-resume,
      .shorts-progress {
        width: 100%;
      }

      .shorts-audio-controls {
        justify-content: stretch;
      }

      .shorts-tabs {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .shorts-progress-controls {
        display: grid;
        grid-template-columns: minmax(0, 1fr) auto;
      }

      .shorts-sound-toggle {
        flex: 1 1 120px;
      }

      .shorts-volume {
        flex: 2 1 180px;
        justify-content: space-between;
      }

      .shorts-volume input {
        flex: 1;
        width: auto;
      }

      .shorts-tab {
        flex: 1 1 0;
        min-width: 0;
        padding: 0 8px;
      }

      .shorts-feed {
        height: calc(100svh - 58px);
        height: calc(100dvh - 58px);
        border-left: 0;
        border-right: 0;
      }

      .short-stage {
        height: calc(100% - 18px);
        max-height: calc(100% - 18px);
        max-width: calc(100vw - 20px);
      }

      .short-meta {
        padding: 76px 13px 13px;
      }

      .short-meta h4 {
        font-size: 1.05rem;
      }

      .short-meta p {
        font-size: 0.84rem;
      }

      .short-pill {
        min-height: 24px;
        padding: 0 7px;
        font-size: 0.7rem;
      }

      .short-position {
        top: 10px;
        right: 10px;
        font-size: 0.74rem;
      }

      .short-actions {
        top: 38px;
        right: 10px;
      }

      .short-action-button {
        width: 34px;
        height: 34px;
        font-size: 0.98rem;
      }

      .puzzle-shell {
        padding: 14px;
      }

      .puzzle-board-wrap {
        border-width: 5px;
      }

      .tab-button {
        padding: 0 8px;
        font-size: 0.86rem;
      }
    }

    @media (max-width: 520px) {
      .brand-mark {
        width: 34px;
        height: 34px;
      }

      .nav-links a {
        min-height: 40px;
        padding: 0 10px;
      }

      .nav-group-label {
        font-size: 0.62rem;
      }
    }

    @media print {
      * {
        box-shadow: none !important;
        text-shadow: none !important;
      }

      body {
        background: #fff !important;
        color: #111 !important;
        font-size: 11pt;
      }

      .site-header,
      .hero,
      #paths,
      #adventures,
      #rules,
      #openings,
      #videos,
      #notation,
      #puzzles,
      #plan,
      .footer,
      .books-controls,
      .book-category-filters,
      .book-admin,
      .reader-toolbar,
      .reader-toc,
      .reader-nav,
      .book-actions,
      .video-modal {
        display: none !important;
      }

      main,
      #books,
      #books .wrap {
        display: block !important;
        width: 100% !important;
        max-width: none !important;
        margin: 0 !important;
        padding: 0 !important;
        background: #fff !important;
        color: #111 !important;
      }

      #books .section-head {
        display: block;
        margin-bottom: 16px;
      }

      .book-grid {
        display: block;
      }

      .book-level-grid,
      .book-level-section {
        display: block;
      }

      .book-card,
      .book-detail,
      .book-reader,
      .reader-page,
      .book-stat,
      .book-verify-note {
        break-inside: avoid;
        page-break-inside: avoid;
        margin: 0 0 14px;
        border: 1px solid #777 !important;
        background: #fff !important;
        color: #111 !important;
      }

      .reader-layout {
        display: block !important;
      }

      .book-detail[hidden] {
        display: none !important;
      }

      .badge,
      .topic-list li,
      .book-meta span {
        border: 1px solid #777 !important;
        background: #fff !important;
        color: #111 !important;
      }

      a[href]::after {
        content: " (" attr(href) ")";
        font-size: 9pt;
        font-weight: 400;
        word-break: break-all;
      }
    }
  </style>
</head>
<body>
  <header class="site-header">
    <nav class="nav" aria-label="Main navigation">
      <a class="brand" href="#top" aria-label="Checkmate Quest home">
        <span class="brand-mark" aria-hidden="true">CQ</span>
        <span>Checkmate Quest</span>
      </a>
      <div class="nav-links" aria-label="Course section tabs">
        <div class="nav-group" aria-label="Learn">
          <span class="nav-group-label">Learn</span>
          <a href="#paths" data-site-tab="paths" data-site-panel="paths">Lessons</a>
          <a href="#adventures" data-site-tab="adventures" data-site-panel="adventures">Adventures</a>
          <a href="#rules" data-site-tab="rules" data-site-panel="rules">Rules</a>
          <a href="#openings" data-site-tab="openings" data-site-panel="openings">Openings</a>
        </div>
        <div class="nav-group" aria-label="Practice">
          <span class="nav-group-label">Play</span>
          <a class="is-quick-tab" href="#play" data-site-tab="play" data-site-panel="play">Play AI</a>
          <a class="is-quick-tab" href="#puzzles" data-site-tab="puzzles" data-site-panel="puzzles">Puzzles</a>
          <a href="#shorts" data-site-tab="shorts" data-site-panel="videos" data-site-focus="shorts">Shorts</a>
        </div>
        <div class="nav-group" aria-label="Study">
          <span class="nav-group-label">Study</span>
          <a href="#videos" data-site-tab="videos" data-site-panel="videos">Videos</a>
          <a href="#books" data-site-tab="books" data-site-panel="books">Books</a>
          <a href="#notation" data-site-tab="notation" data-site-panel="notation">Notation</a>
          <a class="is-quick-tab" href="#plan" data-site-tab="plan" data-site-panel="plan">Plan</a>
        </div>
      </div>
    </nav>
  </header>

  <main id="top">
    <section class="hero" aria-labelledby="hero-title">
      <div class="hero-board" aria-hidden="true">
        <div class="hero-board-grid" id="heroBoard"></div>
      </div>
      <div class="hero-inner">
        <div class="hero-layout">
          <div class="hero-copy">
            <p class="eyebrow">Beginner chess that feels like a game</p>
            <h1 id="hero-title">Checkmate Quest</h1>
            <p>Start with tiny missions, 60-second tricks, friendly puzzles, and a coach that rewards progress instead of pressure.</p>
            <div class="hero-actions">
              <a class="button" href="#paths" id="newToChessButton">I'm new to chess</a>
              <a class="button secondary" href="#puzzles">Try a Puzzle</a>
            </div>
            <div class="home-start-flow" aria-label="Start here">
              <a class="home-step" href="#paths"><strong>1. Learn</strong><span>One tiny mission.</span></a>
              <a class="home-step" href="#puzzles"><strong>2. Try</strong><span>One mini puzzle.</span></a>
              <a class="home-step" href="#play"><strong>3. Play</strong><span>Ask the coach why.</span></a>
            </div>
          </div>
          <div class="home-dashboard" aria-label="Personal chess dashboard">
            <h3 id="homeWelcome">Welcome back!</h3>
            <div class="home-stat-grid">
              <span class="home-stat" id="homeStreak">0-day streak</span>
              <span class="home-stat" id="homeLevel">Level: Beginner</span>
              <span class="home-stat" id="homeXp">0 XP</span>
              <span class="home-stat" id="homeProgress">0 lessons done</span>
            </div>
            <div class="quick-practice" aria-label="Quick practice">
              <a class="button secondary" href="#puzzles">2-minute practice</a>
              <a class="button secondary" href="#puzzles">5 puzzles</a>
              <a class="button secondary" href="#videos">One endgame</a>
              <a class="button secondary" href="#puzzles">Checkmate challenge</a>
            </div>
            <p id="homeInsight">One puzzle today is better than none.</p>
            <div class="game-reward-row" id="homeUnlocks" aria-label="Unlocked rewards"></div>
            <div class="recommendation-list" id="homeRecommendations" aria-label="Recommended practice"></div>
          </div>
        </div>
      </div>
    </section>

    <section id="paths" class="section-dark" aria-labelledby="paths-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Learning paths</p>
            <h2 id="paths-title">Complete beginner missions</h2>
          </div>
          <p class="section-intro">No ratings, no heavy analysis. Finish one tiny mission, celebrate it, and remember: you're getting better every day.</p>
        </div>

        <aside class="gentle-start" id="gentleStart" aria-labelledby="gentleStartTitle">
          <div class="gentle-copy">
            <div class="gentle-badges" aria-label="Beginner friendly promises">
              <span class="gentle-badge">No pressure</span>
              <span class="gentle-badge">Tiny wins</span>
              <span class="gentle-badge">Fun first</span>
            </div>
            <h3 id="gentleStartTitle">Gentle Start Coach</h3>
            <p>Take a 2-minute skill assessment, then get a personalized path for today. A good day can be just one clear idea.</p>
            <ul class="gentle-checklist">
              <li><span>1</span><strong>Learn one idea, not ten.</strong></li>
              <li><span>2</span><strong>Play or solve once to feel it.</strong></li>
              <li><span>3</span><strong>Celebrate the mistake you understood.</strong></li>
            </ul>
            <div class="gentle-actions">
              <a class="button secondary" href="#adventures">Try Adventures</a>
              <a class="button secondary" href="#puzzles">Solve One Puzzle</a>
            </div>
          </div>

          <div class="gentle-coach">
            <form class="gentle-form" id="gentleStartForm">
              <label for="gentleMood">
                Today I feel
                <select id="gentleMood" name="gentleMood">
                  <option value="new">Brand new</option>
                  <option value="blunders">I keep losing pieces</option>
                  <option value="fun">I want a fun challenge</option>
                  <option value="opening">Openings confuse me</option>
                </select>
              </label>
              <label for="gentleMinutes">
                Time
                <select id="gentleMinutes" name="gentleMinutes">
                  <option value="5" selected>5 minutes</option>
                  <option value="8">8 minutes</option>
                  <option value="12">12 minutes</option>
                </select>
              </label>
              <label for="gentleEnergy">
                Energy
                <select id="gentleEnergy" name="gentleEnergy">
                  <option value="calm">Calm</option>
                  <option value="normal" selected>Normal</option>
                  <option value="spark">Excited</option>
                </select>
              </label>
              <button class="button" type="submit">Build My Path</button>
            </form>
            <div class="gentle-output" id="gentleQuestOutput" aria-live="polite"></div>
          </div>
        </aside>

        <div class="lesson-flow" aria-label="Short lesson flow">
          <div class="lesson-flow-step"><strong>Learn</strong><span>One idea only.</span></div>
          <div class="lesson-flow-step"><strong>Try</strong><span>Use it once.</span></div>
          <div class="lesson-flow-step"><strong>One Puzzle</strong><span>Test the pattern.</span></div>
          <div class="lesson-flow-step"><strong>Celebrate</strong><span>Mark the win.</span></div>
          <div class="lesson-flow-step"><strong>Next Lesson</strong><span>Keep momentum.</span></div>
        </div>

        <div class="lesson-journey" id="chessJourney" aria-live="polite"></div>

        <div class="path-tabs" role="tablist" aria-label="Lesson levels">
          <button class="tab-button" type="button" role="tab" aria-selected="true" aria-controls="beginner" id="tab-beginner" data-level="beginner">Beginner</button>
          <button class="tab-button" type="button" role="tab" aria-selected="false" aria-controls="intermediate" id="tab-intermediate" data-level="intermediate">Intermediate</button>
          <button class="tab-button" type="button" role="tab" aria-selected="false" aria-controls="advanced" id="tab-advanced" data-level="advanced">Advanced</button>
        </div>

        <div class="lesson-grid" id="beginner" role="tabpanel" aria-labelledby="tab-beginner">
          <article class="lesson-card">
            <span class="lesson-number">1</span>
            <h3>Mission 1: Control the Center</h3>
            <p>Put a pawn or piece near the middle so your army has more room to move.</p>
            <ul class="topic-list">
              <li>e4/d4</li>
              <li>Center squares</li>
              <li>Space</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">2</span>
            <h3>Mission 2: Develop Pieces</h3>
            <p>Bring knights and bishops out before chasing attacks with the queen.</p>
            <ul class="topic-list">
              <li>Knights</li>
              <li>Bishops</li>
              <li>Simple plans</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">3</span>
            <h3>Mission 3: Castle</h3>
            <p>Move the king to safety and connect your rooks before the board opens up.</p>
            <ul class="topic-list">
              <li>King safety</li>
              <li>Rooks</li>
              <li>Timing</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">4</span>
            <h3>Mission 4: Protect Pieces</h3>
            <p>Before moving, ask what is attacked and what your opponent wants next.</p>
            <ul class="topic-list">
              <li>Threats</li>
              <li>Loose pieces</li>
              <li>Safe moves</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">5</span>
            <h3>Mission 5: Win Your First Game</h3>
            <p>Use center, development, castling, and piece safety together in one friendly game.</p>
            <ul class="topic-list">
              <li>Play AI</li>
              <li>One tip</li>
              <li>Celebrate</li>
            </ul>
          </article>
        </div>

        <div class="lesson-grid hidden" id="intermediate" role="tabpanel" aria-labelledby="tab-intermediate">
          <article class="lesson-card">
            <span class="lesson-number">1</span>
            <h3>Tactical Patterns</h3>
            <p>Train forks, pins, skewers, discoveries, and back-rank ideas until the patterns start appearing before you calculate.</p>
            <ul class="topic-list">
              <li>Forks</li>
              <li>Pins</li>
              <li>Skewers</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">2</span>
            <h3>Calculation</h3>
            <p>List forcing moves first: checks, captures, and threats. Then compare candidate lines before touching a piece.</p>
            <ul class="topic-list">
              <li>Candidate moves</li>
              <li>Forcing lines</li>
              <li>Blunder checks</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">3</span>
            <h3>Pawn Structure</h3>
            <p>Use pawn chains, open files, isolated pawns, and outposts to decide where your pieces belong after the opening.</p>
            <ul class="topic-list">
              <li>Outposts</li>
              <li>Open files</li>
              <li>Weak squares</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">4</span>
            <h3>Practical Endgames</h3>
            <p>Convert extra material by activating the king, cutting off counterplay, and knowing the basic rook and pawn endings.</p>
            <ul class="topic-list">
              <li>King activity</li>
              <li>Rook endings</li>
              <li>Passed pawns</li>
            </ul>
          </article>
        </div>

        <div class="lesson-grid hidden" id="advanced" role="tabpanel" aria-labelledby="tab-advanced">
          <article class="lesson-card">
            <span class="lesson-number">1</span>
            <h3>Positional Imbalances</h3>
            <p>Compare bishops vs. knights, space, pawn weaknesses, king exposure, and initiative before choosing a plan.</p>
            <ul class="topic-list">
              <li>Space</li>
              <li>Initiative</li>
              <li>Piece quality</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">2</span>
            <h3>Opening Repertoires</h3>
            <p>Build compact opening files around structures and middlegame plans, not just memorized move orders.</p>
            <ul class="topic-list">
              <li>Repertoires</li>
              <li>Transpositions</li>
              <li>Model games</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">3</span>
            <h3>Endgame Technique</h3>
            <p>Refine opposition, triangulation, rook activity, queen checks, and conversion methods for small advantages.</p>
            <ul class="topic-list">
              <li>Opposition</li>
              <li>Triangulation</li>
              <li>Conversion</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">4</span>
            <h3>Game Review</h3>
            <p>Annotate without an engine first, mark turning points, then use analysis to test your reasoning against the position.</p>
            <ul class="topic-list">
              <li>Annotations</li>
              <li>Critical moments</li>
              <li>Engine review</li>
            </ul>
          </article>
        </div>
      </div>
    </section>

    <section id="adventures" class="section-warm" aria-labelledby="adventures-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Adventure mode</p>
            <h2 id="adventures-title">Turn lessons into adventures</h2>
          </div>
          <p class="section-intro">Every piece becomes a character in Chess Kingdom, and every rule becomes a mission the player can picture before they move.</p>
        </div>

        <div class="adventure-grid">
          <article class="adventure-card">
            <span class="character-mark" aria-hidden="true">&#128081;</span>
            <h3>King = nervous boss</h3>
            <p>The boss is important but fragile. Every mission is secretly about keeping him safe while the team does the work.</p>
            <ul class="topic-list">
              <li>One square</li>
              <li>Never into danger</li>
              <li>Needs guards</li>
            </ul>
          </article>
          <article class="adventure-card">
            <span class="character-mark" aria-hidden="true">&#128120;</span>
            <h3>Queen = superhero</h3>
            <p>The superhero flies across ranks, files, and diagonals. She is powerful, but even heroes need backup.</p>
            <ul class="topic-list">
              <li>Any distance</li>
              <li>Straight or diagonal</li>
              <li>Big attacker</li>
            </ul>
          </article>
          <article class="adventure-card">
            <span class="character-mark" aria-hidden="true">&#127984;</span>
            <h3>Rook = castle guardian</h3>
            <p>The guardian patrols the castle walls in straight lines, guarding files and ranks like long hallways.</p>
            <ul class="topic-list">
              <li>Files</li>
              <li>Ranks</li>
              <li>Open lanes</li>
            </ul>
          </article>
          <article class="adventure-card">
            <span class="character-mark" aria-hidden="true">&#128052;</span>
            <h3>Knight = trickster jumper</h3>
            <p>The trickster leaps over crowds and lands in an L shape, surprising enemies that thought they were safe.</p>
            <ul class="topic-list">
              <li>Jumps pieces</li>
              <li>L shape</li>
              <li>Forks</li>
            </ul>
          </article>
          <article class="adventure-card">
            <span class="character-mark" aria-hidden="true">&#9962;</span>
            <h3>Bishop = diagonal sniper</h3>
            <p>The sniper watches long diagonal roads. Once a diagonal opens, the bishop can strike from far away.</p>
            <ul class="topic-list">
              <li>Diagonals</li>
              <li>Long range</li>
              <li>Color bound</li>
            </ul>
          </article>
          <article class="adventure-card">
            <span class="character-mark" aria-hidden="true">&#9823;&#65039;</span>
            <h3>Pawn = rookie soldier</h3>
            <p>The rookie soldier marches forward, captures diagonally, and dreams of promotion at the far side of the board.</p>
            <ul class="topic-list">
              <li>Moves forward</li>
              <li>Captures diagonal</li>
              <li>Promotes</li>
            </ul>
          </article>
        </div>

        <div class="mission-grid">
          <article class="mission-card">
            <span class="mission-label">Lesson 1 replacement</span>
            <h3>&#128052; The Knight's Secret Jump Mission</h3>
            <p>The trickster jumper must rescue a trapped pawn by leaping over two guards and landing in the perfect L-shaped hideout.</p>
          </article>
          <article class="mission-card">
            <span class="mission-label">Movement story</span>
            <h3>&#128120; The Queen's Superhero Rescue</h3>
            <p>The queen races down a file, cuts across a diagonal, and saves the nervous boss by attacking the enemy's strongest piece.</p>
          </article>
          <article class="mission-card">
            <span class="mission-label">Board control</span>
            <h3>&#127984; The Rook's Castle Wall Patrol</h3>
            <p>The rook opens a file like a castle gate, then patrols the whole hallway so no enemy can sneak through.</p>
          </article>
          <article class="mission-card">
            <span class="mission-label">Diagonal vision</span>
            <h3>&#9962; The Bishop's Hidden Sniper Trail</h3>
            <p>The bishop waits on a quiet diagonal until one pawn moves, revealing a long-range attack across the kingdom.</p>
          </article>
          <article class="mission-card">
            <span class="mission-label">Pawn power</span>
            <h3>&#9823;&#65039; The Rookie Soldier's Promotion Quest</h3>
            <p>The pawn survives one square at a time, dodges captures, and reaches the final rank to become a new hero.</p>
          </article>
          <article class="mission-card">
            <span class="mission-label">King safety</span>
            <h3>&#128081; Protect the Nervous Boss</h3>
            <p>The whole team builds a shield, castles the king away from danger, and checks every move for hidden threats.</p>
          </article>
        </div>

        <div class="adventure-play" aria-labelledby="adventurePlayTitle">
          <div class="adventure-board-wrap" aria-label="Playable adventure board">
            <div class="adventure-board" id="adventureBoard"></div>
          </div>
          <div class="adventure-panel">
            <div class="mission-selector" id="adventureMissionList" aria-label="Adventure mission list"></div>
            <div class="puzzle-meta">
              <span class="badge" id="adventureRole">Knight mission</span>
              <span class="badge" id="adventureMove">White to move</span>
            </div>
            <h3 id="adventurePlayTitle">Adventure mission</h3>
            <p id="adventureTask">Choose a mission to begin.</p>
            <p class="puzzle-hint" id="adventureTip">Select the glowing character, then click the target square.</p>
            <p class="feedback" id="adventureFeedback">Start with the knight mission.</p>
            <div class="puzzle-actions">
              <button class="button" type="button" id="nextAdventure">Next Mission</button>
              <button class="button secondary" type="button" id="restartAdventure">Restart Mission</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="rules" class="section-warm" aria-labelledby="rules-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Rules</p>
            <h2 id="rules-title">The essentials</h2>
          </div>
          <p class="section-intro">These rules cover the situations that decide most beginner games and prevent the classic illegal-move confusion.</p>
        </div>

        <div class="rules-grid">
          <article class="rule-item">
            <strong>Objective</strong>
            <p>Checkmate the opposing king. A king is checkmated when it is attacked and has no legal way to escape.</p>
          </article>
          <article class="rule-item">
            <strong>Turns</strong>
            <p>White moves first. Players alternate one legal move at a time, and a move cannot leave your own king in check.</p>
          </article>
          <article class="rule-item">
            <strong>Piece movement</strong>
            <p>Rooks move straight, bishops diagonal, queens both ways, knights in an L shape, kings one square, and pawns forward.</p>
          </article>
          <article class="rule-item">
            <strong>Captures</strong>
            <p>Most pieces capture the way they move. Pawns move forward but capture one square diagonally forward.</p>
          </article>
          <article class="rule-item">
            <strong>Castling</strong>
            <p>The king and rook move together if neither has moved, the path is clear, and the king does not pass through check.</p>
          </article>
          <article class="rule-item">
            <strong>Promotion</strong>
            <p>A pawn reaching the last rank becomes a queen, rook, bishop, or knight. Most positions call for a queen.</p>
          </article>
          <article class="rule-item">
            <strong>En passant</strong>
            <p>A pawn that advances two squares can sometimes be captured as if it moved one square, but only immediately.</p>
          </article>
          <article class="rule-item">
            <strong>Draws</strong>
            <p>Games can draw by stalemate, agreement, repetition, the fifty-move rule, or insufficient mating material.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="openings" class="section-dark" aria-labelledby="openings-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Opening compass</p>
            <h2 id="openings-title">Start with a plan</h2>
          </div>
          <p class="section-intro">Openings are easier to remember when each one has a job: control the center, develop pieces, and get the king safe.</p>
        </div>

        <div class="principle-strip" aria-label="Opening principles">
          <span>Control the center</span>
          <span>Develop minor pieces</span>
          <span>Castle early</span>
          <span>Avoid repeat moves</span>
          <span>Connect your rooks</span>
        </div>

        <div class="opening-grid">
          <article class="opening-card">
            <div class="mini-board" data-fen="r1bqkbnr/pppp1ppp/2n5/4p3/2B1P3/5N2/PPPP1PPP/RNBQK2R" aria-label="Italian Game position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 e5 2. Nf3 Nc6 3. Bc4</span>
              <h3>Italian Game</h3>
              <p>Fast development, pressure on f7, and simple castling plans make this a friendly first opening for White.</p>
              <ul class="topic-list">
                <li>Open center</li>
                <li>Quick castle</li>
                <li>f7 pressure</li>
              </ul>
              <ul class="book-lines">
                <li><code>3...Bc5 4. c3 Nf6</code><span>Giuoco Piano: build the center before attacking.</span></li>
                <li><code>3...Nf6 4. Ng5</code><span>Two Knights: tactical pressure on f7.</span></li>
                <li><code>4. b4</code><span>Evans Gambit: trade a pawn for fast activity.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkbnr/ppp1pppp/8/3p4/2PP4/8/PP2PPPP/RNBQKBNR" aria-label="Queen's Gambit position"></div>
            <div class="opening-body">
              <span class="opening-line">1. d4 d5 2. c4</span>
              <h3>Queen's Gambit</h3>
              <p>White offers a wing pawn to pull Black away from the center and build a strong pawn duo.</p>
              <ul class="topic-list">
                <li>Central space</li>
                <li>Pawn tension</li>
                <li>Piece harmony</li>
              </ul>
              <ul class="book-lines">
                <li><code>2...e6 3. Nc3 Nf6</code><span>Queen's Gambit Declined: solid center and natural development.</span></li>
                <li><code>2...dxc4 3. e4</code><span>Queen's Gambit Accepted: win back c4 with central control.</span></li>
                <li><code>2...c6</code><span>Slav Defense: support d5 before developing the bishop.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkbnr/pp1ppppp/8/2p5/4P3/8/PPPP1PPP/RNBQKBNR" aria-label="Sicilian Defense position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 c5</span>
              <h3>Sicilian Defense</h3>
              <p>Black fights from the side, creates an unbalanced pawn structure, and plays for active counterplay.</p>
              <ul class="topic-list">
                <li>Counterattack</li>
                <li>Open c-file</li>
                <li>Sharp play</li>
              </ul>
              <ul class="book-lines">
                <li><code>2. Nf3 d6 3. d4 cxd4</code><span>Open Sicilian: immediate central fight.</span></li>
                <li><code>2. Nf3 Nc6 3. Bb5</code><span>Rossolimo: develop with pressure on c6.</span></li>
                <li><code>2. c3</code><span>Alapin: build a broad pawn center.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="r1bqkbnr/pppp1ppp/2n5/1B2p3/4P3/5N2/PPPP1PPP/RNBQK2R" aria-label="Ruy Lopez position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 e5 2. Nf3 Nc6 3. Bb5</span>
              <h3>Ruy Lopez</h3>
              <p>White develops with pressure on the knight that defends e5, aiming for long-term central control.</p>
              <ul class="topic-list">
                <li>Center pressure</li>
                <li>Slow squeeze</li>
                <li>Model games</li>
              </ul>
              <ul class="book-lines">
                <li><code>3...a6 4. Ba4 Nf6</code><span>Morphy Defense: ask the bishop to choose.</span></li>
                <li><code>3...Nf6</code><span>Berlin Defense: challenge e4 immediately.</span></li>
                <li><code>3...a6 4. Bxc6</code><span>Exchange: trade structure for a simpler plan.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkbnr/ppp2ppp/4p3/3p4/3PP3/8/PPP2PPP/RNBQKBNR" aria-label="French Defense position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 e6 2. d4 d5</span>
              <h3>French Defense</h3>
              <p>Black builds a strong pawn chain and challenges White's center, often attacking from the queenside.</p>
              <ul class="topic-list">
                <li>Pawn chain</li>
                <li>Counterattack</li>
                <li>Locked center</li>
              </ul>
              <ul class="book-lines">
                <li><code>3. e5 c5</code><span>Advance: lock space, then attack the base.</span></li>
                <li><code>3. Nc3 Bb4</code><span>Winawer: pin the knight and fight e4.</span></li>
                <li><code>3. Nd2 Nf6</code><span>Tarrasch: flexible development with less pin pressure.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkbnr/pp2pppp/2p5/3p4/3PP3/8/PPP2PPP/RNBQKBNR" aria-label="Caro-Kann Defense position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 c6 2. d4 d5</span>
              <h3>Caro-Kann Defense</h3>
              <p>Black supports a central strike with c6, aiming for a sturdy structure and a healthy light-square bishop.</p>
              <ul class="topic-list">
                <li>Solid shell</li>
                <li>Good bishop</li>
                <li>Endgame friendly</li>
              </ul>
              <ul class="book-lines">
                <li><code>3. e5 Bf5</code><span>Advance: develop the bishop before closing in.</span></li>
                <li><code>3. Nc3 dxe4 4. Nxe4</code><span>Classical: clarify the center.</span></li>
                <li><code>3. exd5 cxd5</code><span>Exchange: simple structure and easy development.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkb1r/ppp1pppp/5n2/3p4/3P1B2/5N2/PPP1PPPP/RN1QKB1R" aria-label="London System position"></div>
            <div class="opening-body">
              <span class="opening-line">1. d4 d5 2. Nf3 Nf6 3. Bf4</span>
              <h3>London System</h3>
              <p>White builds a reliable setup with Bf4, e3, c3, and Bd3, focusing on development and safe attacking chances.</p>
              <ul class="topic-list">
                <li>System play</li>
                <li>Easy setup</li>
                <li>Safe king</li>
              </ul>
              <ul class="book-lines">
                <li><code>3...e6 4. e3 Bd6</code><span>Main setup: trade or keep the bishop with h3.</span></li>
                <li><code>2. Bf4</code><span>Early London: set the bishop first.</span></li>
                <li><code>3. e3 c5 4. c3</code><span>Solid center against queenside pressure.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqk2r/ppppppbp/5np1/8/2PP4/2N5/PP2PPPP/R1BQKBNR" aria-label="King's Indian Defense position"></div>
            <div class="opening-body">
              <span class="opening-line">1. d4 Nf6 2. c4 g6 3. Nc3 Bg7</span>
              <h3>King's Indian Defense</h3>
              <p>Black lets White take space, then attacks the center with dynamic piece play and kingside pressure.</p>
              <ul class="topic-list">
                <li>Fianchetto</li>
                <li>Counterpunch</li>
                <li>Kingside attack</li>
              </ul>
              <ul class="book-lines">
                <li><code>4. e4 d6 5. Nf3 O-O</code><span>Classical: big center versus kingside counterplay.</span></li>
                <li><code>4. g3 O-O 5. Bg2</code><span>Fianchetto: quieter pressure on long diagonals.</span></li>
                <li><code>4. e4 d6 5. f3</code><span>Saemisch: support the center and prepare queenside space.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkbnr/ppp1pppp/8/3p4/4P3/8/PPPP1PPP/RNBQKBNR" aria-label="Scandinavian Defense position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 d5</span>
              <h3>Scandinavian Defense</h3>
              <p>Black immediately attacks e4 and accepts early queen activity in exchange for a direct, easy-to-learn plan.</p>
              <ul class="topic-list">
                <li>Direct strike</li>
                <li>Early queen</li>
                <li>Clear plan</li>
              </ul>
              <ul class="book-lines">
                <li><code>2. exd5 Qxd5 3. Nc3 Qa5</code><span>Main line: queen retreats and Black develops.</span></li>
                <li><code>2. exd5 Nf6</code><span>Modern: delay queen recapture and develop first.</span></li>
                <li><code>2. e5</code><span>Advance: keep space but give Black targets.</span></li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqk2r/pppp1ppp/4pn2/8/1bPP4/2N5/PP2PPPP/R1BQKBNR" aria-label="Nimzo-Indian Defense position"></div>
            <div class="opening-body">
              <span class="opening-line">1. d4 Nf6 2. c4 e6 3. Nc3 Bb4</span>
              <h3>Nimzo-Indian Defense</h3>
              <p>Black pins the knight and fights for control of e4, often trading structure for active piece play.</p>
              <ul class="topic-list">
                <li>Pin pressure</li>
                <li>e4 control</li>
                <li>Flexible plans</li>
              </ul>
              <ul class="book-lines">
                <li><code>4. e3 O-O</code><span>Rubinstein: simple development and solid center.</span></li>
                <li><code>4. Qc2</code><span>Classical: protect c3 and keep the bishop pair.</span></li>
                <li><code>4. a3 Bxc3+ 5. bxc3</code><span>Saemisch: accept doubled pawns for the bishop pair.</span></li>
              </ul>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="videos" class="section-dark" aria-labelledby="videos-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Video lessons</p>
            <h2 id="videos-title">Watch the ideas</h2>
          </div>
          <p class="section-intro">A tiered video library with 152 embedded lessons, including 50 regular tutorials and 102 verified Shorts arranged from beginner patterns to advanced tactics.</p>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Beginner videos</h3>
            <p>Start here for rules, piece movement, opening basics, checkmates, and first endgames.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/OCSbzArwB10?rel=0&modestbranding=1&playsinline=1" title="How To Play Chess: The Ultimate Beginner Guide" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 1</span>
                <h3>Complete beginner guide</h3>
                <p>Learn the board, pieces, legal moves, and the first decisions that matter.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/IU6k-4rKf-g?rel=0&modestbranding=1&playsinline=1" title="Learn How to Play Chess for Beginners in Less Than 8 Minutes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 2</span>
                <h3>Piece movement</h3>
                <p>A quick pass through how every chess piece moves and captures.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/8IlJ3v8I4Z8?rel=0&modestbranding=1&playsinline=1" title="Basic Chess Openings Explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 3</span>
                <h3>Opening principles</h3>
                <p>Develop pieces, fight for the center, and castle before chasing attacks.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/I9n8sDRZLZ8?rel=0&modestbranding=1&playsinline=1" title="Checkmate for chess beginners" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 4</span>
                <h3>Basic checkmates</h3>
                <p>Build the pattern vocabulary for finishing games instead of only winning pieces.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/LPK6_QRJRA0?rel=0&modestbranding=1&playsinline=1" title="King Opposition: Draw King and Pawn Endgame" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 5</span>
                <h3>King and pawn basics</h3>
                <p>See why king activity and opposition matter in the simplest endings.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Intermediate videos</h3>
            <p>Move from knowing rules to finding tactics, calculating lines, and building plans.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/MbMslp2WcI0?rel=0&modestbranding=1&playsinline=1" title="The Chess Tactics Guide For Beginners" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 1</span>
                <h3>Forks, pins, skewers</h3>
                <p>Train the tactical patterns that decide most improving-player games.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/9Ga9dP3bvN8?rel=0&modestbranding=1&playsinline=1" title="How To Calculate In Chess" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 2</span>
                <h3>Calculation method</h3>
                <p>Learn how to compare candidate moves and check forcing lines clearly.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/yAnNQY2Ac6w?rel=0&modestbranding=1&playsinline=1" title="Top 5 Pawn Structures You Should Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 3</span>
                <h3>Pawn structures</h3>
                <p>Use pawn shapes to understand where pieces belong after the opening.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/kTON84W-b2Q?rel=0&modestbranding=1&playsinline=1" title="The ONLY Chess Middlegame Guide You Need" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 4</span>
                <h3>Middlegame plans</h3>
                <p>Turn development into real plans: attacks, trades, files, and weak squares.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/zOvaUJdtYTc?rel=0&modestbranding=1&playsinline=1" title="EASY Rook Checkmate!" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 5</span>
                <h3>Rook technique</h3>
                <p>Practice converting a rook advantage with clean king coordination.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Advanced videos</h3>
            <p>Deepen endgame precision, positional evaluation, prophylaxis, and candidate-move discipline.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/wsOQBe5yBqk?rel=0&modestbranding=1&playsinline=1" title="Distant and Rectangular Opposition" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 1</span>
                <h3>Distant opposition</h3>
                <p>Study exact king geometry for pawn endings where one tempo changes everything.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/s8RDioKrLx8?rel=0&modestbranding=1&playsinline=1" title="The Principle of Positional Imbalances" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 2</span>
                <h3>Positional imbalances</h3>
                <p>Evaluate space, minor pieces, pawn weaknesses, initiative, and king safety.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/N6WmHGKLaa8?rel=0&modestbranding=1&playsinline=1" title="PROPHYLAXIS in Chess. GM Johan Hellsten explains." allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 3</span>
                <h3>Prophylaxis</h3>
                <p>Learn to ask what your opponent wants before choosing your own plan.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/aMIRnzCeD64?rel=0&modestbranding=1&playsinline=1" title="Lucena Position Explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 4</span>
                <h3>Lucena technique</h3>
                <p>Master bridge-building, one of the most important winning rook endgames.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/5rEqhhYYOrQ?rel=0&modestbranding=1&playsinline=1" title="How to Choose Candidate Moves" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 5</span>
                <h3>Candidate moves</h3>
                <p>Refine your move-selection process before calculating deep variations.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Accuracy Masterclass: Beginner</h3>
            <p>Five regular tutorials for clean rules, piece safety, opening habits, and simple plans.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/GQvR_fLkNKo?rel=0&modestbranding=1&playsinline=1" title="Chess Lesson 1: The Chess Pieces and the Board" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Beginner 1</span>
                <h3>Board and pieces</h3>
                <p>Start with the exact board setup, piece movement, and legal-move basics.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/AshEhLcPHqU?rel=0&modestbranding=1&playsinline=1" title="Free Chess Course From Beginner To Master Level" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Beginner 2</span>
                <h3>Complete learning path</h3>
                <p>A structured course-style lesson that connects rules, tactics, and improvement habits.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/346S2bg8Gjw?rel=0&modestbranding=1&playsinline=1" title="Learn to Play Chess Openings: The Ultimate Beginner's Guide" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Beginner 3</span>
                <h3>Opening fundamentals</h3>
                <p>Learn opening rules that prevent early mistakes and make development natural.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/UoFqV1lxA7Q?rel=0&modestbranding=1&playsinline=1" title="3 Basic Opening Strategy Principles" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Beginner 4</span>
                <h3>Three opening rules</h3>
                <p>Focus on center control, fast development, and king safety before attacks.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/O_RDwBNWKn8?rel=0&modestbranding=1&playsinline=1" title="Simple Opening Idea Back to Basic Opening Principle" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Beginner 5</span>
                <h3>Simple opening idea</h3>
                <p>A practical Biyaherong-style opening lesson for turning basics into moves.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Accuracy Masterclass: Intermediate</h3>
            <p>Five regular tutorials for sharper tactics, calculation discipline, and practical counterplay.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/uHXmlOI0VrE?rel=0&modestbranding=1&playsinline=1" title="Every Chess Tactic Explained From Beginner To Advanced" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Intermediate 1</span>
                <h3>Tactics map</h3>
                <p>Review the core tactical patterns and learn when each one appears.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/C81vrCD0RcA?rel=0&modestbranding=1&playsinline=1" title="Chess Calculation is Hard Until You Learn These 6 Rules" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Intermediate 2</span>
                <h3>Six calculation rules</h3>
                <p>Use forcing moves and candidate moves to calculate without guessing.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/kh24tXamy3U?rel=0&modestbranding=1&playsinline=1" title="How to Improve Your Chess Calculation" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Intermediate 3</span>
                <h3>Calculation training</h3>
                <p>Build a repeatable thinking process for checks, captures, and threats.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/goW1cFHaxtU?rel=0&modestbranding=1&playsinline=1" title="Chess Tips: Creating Counterplay" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Intermediate 4</span>
                <h3>Counterplay</h3>
                <p>Learn how to create active chances instead of defending passively.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/Ng1Wj87dWHk?rel=0&modestbranding=1&playsinline=1" title="Calculate and Evaluate Like a Grandmaster" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Intermediate 5</span>
                <h3>Calculate and evaluate</h3>
                <p>Compare candidate moves by combining tactical lines with position judgment.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Accuracy Masterclass: Advanced</h3>
            <p>Five regular tutorials for positional precision, closed positions, and exact endgame play.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/h7S9uE3lT0I?rel=0&modestbranding=1&playsinline=1" title="The Only Chess Positional Guide You Need" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Advanced 1</span>
                <h3>Positional guide</h3>
                <p>Improve accuracy by reading pawn structure, piece activity, and weak squares.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/NKBbyDDzzmw?rel=0&modestbranding=1&playsinline=1" title="Mastering Positional Chess" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Advanced 2</span>
                <h3>Master positional play</h3>
                <p>Use grandmaster-level planning ideas without losing the practical thread.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/W_Xkm5v_prI?rel=0&modestbranding=1&playsinline=1" title="Closed Positions Do Not Have to Be Confusing" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Advanced 3</span>
                <h3>Closed positions</h3>
                <p>Find plans when pawn chains slow the game and tactics are hidden.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/mhUoe2JBxco?rel=0&modestbranding=1&playsinline=1" title="Principles of Chess Endgames: King Activity" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Advanced 4</span>
                <h3>King activity</h3>
                <p>Turn endgame accuracy into active king placement and clear conversion plans.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/QUqq7wSLE78?rel=0&modestbranding=1&playsinline=1" title="Introduction to Pawn Endgames" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Accuracy Advanced 5</span>
                <h3>Pawn endgames</h3>
                <p>Study opposition, passed pawns, and tempo details that decide precise endings.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Fast-track tutorials</h3>
            <p>Twenty short, focused lessons for openings, tactics, checkmates, pawn play, middlegames, and endgames.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/6IegDENuxU4?rel=0&modestbranding=1&playsinline=1" title="How To Learn and Study Chess Openings" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Openings</span><span class="badge duration">22:41</span>
                <h3>Study openings smarter</h3>
                <p>Learn how to build opening knowledge around ideas, not random memorization.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/jfcVjIa1EGM?rel=0&modestbranding=1&playsinline=1" title="Every Chess Opening Principle Explained In 18 Minutes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Openings</span><span class="badge duration">17:41</span>
                <h3>Opening principles</h3>
                <p>A fast overview of the rules that keep your first moves clean and purposeful.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/kURU67G98O8?rel=0&modestbranding=1&playsinline=1" title="Chess Basics: Opening Principles" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Openings</span><span class="badge duration">8:08</span>
                <h3>Opening basics</h3>
                <p>Quickly connect center control, development, and king safety into one routine.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/nXyJdetptXg?rel=0&modestbranding=1&playsinline=1" title="35 Vital Chess Principles" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Strategy</span><span class="badge duration">18:51</span>
                <h3>35 vital principles</h3>
                <p>Connect opening, middlegame, and endgame ideas in one practical lesson.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/W1gWHIpQNVU?rel=0&modestbranding=1&playsinline=1" title="All The Chess Tactics You Need To Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Tactics</span><span class="badge duration">15:59</span>
                <h3>Essential tactics</h3>
                <p>Build a tactical checklist that makes threats easier to spot during games.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/hcmMtNqEm4o?rel=0&modestbranding=1&playsinline=1" title="Chess Strategies - Skewers and Pins" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Tactics</span><span class="badge duration">7:37</span>
                <h3>Pins and skewers</h3>
                <p>See how line pieces trap valuable targets behind defenders.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/qMfXy648KIY?rel=0&modestbranding=1&playsinline=1" title="Chess pins, skewers and forks explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Tactics</span><span class="badge duration">11:09</span>
                <h3>Forks, pins, skewers</h3>
                <p>A beginner-friendly breakdown of the three patterns that win material fast.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/iBZLU1FXhcI?rel=0&modestbranding=1&playsinline=1" title="6 Checkmate Patterns You Must Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">21:46</span>
                <h3>Six checkmate patterns</h3>
                <p>Learn mating shapes that come back again and again in real games.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/spj8bTeZpdk?rel=0&modestbranding=1&playsinline=1" title="Learn Every Checkmate Pattern in 8 Minutes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">8:09</span>
                <h3>Checkmate pattern sprint</h3>
                <p>A compact pattern review for recognizing mate threats faster.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/Wjvy_TH1qQs?rel=0&modestbranding=1&playsinline=1" title="5 Basic Checkmate Patterns You Must Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">11:21</span>
                <h3>Five basic mates</h3>
                <p>Turn attacks into finishes with a small set of reliable mating patterns.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/Bo93mIhnDz4?rel=0&modestbranding=1&playsinline=1" title="The Top 23 Checkmate Patterns" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">22:49</span>
                <h3>Top checkmate patterns</h3>
                <p>A broader pattern library for players ready to sharpen attacking vision.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/uszf3ZRxYMo?rel=0&modestbranding=1&playsinline=1" title="Top 10 Chess Endgame Principles Crash Course" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">14:51</span>
                <h3>Endgame crash course</h3>
                <p>Learn the principles that keep simple endings from slipping away.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/mCsc24k-Q8M?rel=0&modestbranding=1&playsinline=1" title="Easy Chess Endgames: King and Pawns" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">21:15</span>
                <h3>King and pawn endings</h3>
                <p>Practice opposition, passed pawns, and king activity in beginner endings.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/JMZJ9P2Hnq0?rel=0&modestbranding=1&playsinline=1" title="Easy Chess Endgames: Rook and Pawn" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">23:00</span>
                <h3>Rook and pawn endings</h3>
                <p>A clear intro to rook activity, pawn races, and practical conversion.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/FaYmAoJxjUY?rel=0&modestbranding=1&playsinline=1" title="15 Rules For The Endgame" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">22:38</span>
                <h3>Endgame rules</h3>
                <p>Memorable endgame rules that help choose plans when pieces disappear.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/nR8ULRlk9HA?rel=0&modestbranding=1&playsinline=1" title="Rook Endgames Crash Course" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">23:32</span>
                <h3>Rook endgame crash course</h3>
                <p>Learn active rooks, checking distance, and pawn support in rook endings.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/XZeTKbB_LWg?rel=0&modestbranding=1&playsinline=1" title="Top 25 Chess Endgame Principles" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">16:56</span>
                <h3>Endgame principles</h3>
                <p>A wider principle list for converting advantages and defending tough endings.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/lYX-VO1ut7U?rel=0&modestbranding=1&playsinline=1" title="5 Most Common Chess Pawn Structure Mistakes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Pawns</span><span class="badge duration">21:06</span>
                <h3>Pawn structure mistakes</h3>
                <p>Spot the pawn decisions that create long-term weaknesses or strong plans.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/VL9F0xs0yHg?rel=0&modestbranding=1&playsinline=1" title="6 Rules That Will Make You A Pawn Genius" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Pawns</span><span class="badge duration">7:37</span>
                <h3>Pawn rules</h3>
                <p>Six quick rules for making pawn moves that support your pieces.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/F98JdnLyUXA?rel=0&modestbranding=1&playsinline=1" title="The 10 Best Chess Plans For The Middlegame" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Middlegame</span><span class="badge duration">13:02</span>
                <h3>Ten middlegame plans</h3>
                <p>Choose useful plans around files, weak squares, piece activity, and attacks.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier shorts-tier" id="shorts" aria-labelledby="shorts-title">
          <div class="shorts-title-band">
            <div>
              <p class="section-kicker">YouTube Shorts</p>
              <h3 id="shorts-title">Shorts Sprint</h3>
              <p>102 bite-size chess tutorials and puzzle sparks, with beginner, intermediate, advanced, and a dedicated Biyaherong Chess Coach track.</p>
            </div>
            <span class="shorts-count">102 Shorts</span>
          </div>
          <div class="shorts-toolbar" aria-label="Shorts controls">
            <div class="shorts-tabs" role="tablist" aria-label="Shorts levels">
              <button class="shorts-tab" type="button" data-shorts-level="Beginner Shorts" role="tab" aria-selected="true">Beginner</button>
              <button class="shorts-tab" type="button" data-shorts-level="Intermediate Shorts" role="tab" aria-selected="false">Intermediate</button>
              <button class="shorts-tab" type="button" data-shorts-level="Advanced Shorts" role="tab" aria-selected="false">Advanced</button>
              <button class="shorts-tab" type="button" data-shorts-creator="Biyaherong" role="tab" aria-selected="false">Biyaherong Coach</button>
            </div>
            <div class="shorts-progress-controls" aria-label="Shorts progress">
              <button class="shorts-resume" id="shortsResumeButton" type="button">Resume</button>
              <span class="shorts-progress" id="shortsProgress">0/102 Done</span>
            </div>
            <div class="shorts-audio-controls">
              <button class="shorts-sound-toggle" id="shortsSoundToggle" type="button" aria-pressed="false" aria-label="Turn Shorts sound on">Sound Off</button>
              <label class="shorts-volume" for="shortsVolumeRange">
                <span>Volume</span>
                <input id="shortsVolumeRange" type="range" min="0" max="100" value="80" />
              </label>
            </div>
          </div>
          <div class="shorts-levels" id="shortsLevels" aria-label="YouTube Shorts chess tutorials"></div>
        </div>
      </div>
    </section>

    <section id="books" class="section-warm" aria-labelledby="books-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Free library</p>
            <h2 id="books-title">Free Chess Books</h2>
          </div>
          <p class="section-intro">A legal-only reading shelf with public-domain classics, quick summaries, skill levels, and source links the learner can trust.</p>
        </div>

        <div class="books-shell">
          <div class="book-stats" aria-label="Free chess book library summary">
            <div class="book-stat">
              <strong>9</strong>
              <span>verified free books</span>
            </div>
            <div class="book-stat">
              <strong>3</strong>
              <span>beginner to advanced shelves</span>
            </div>
            <div class="book-stat">
              <strong>0</strong>
              <span>pirated PDFs linked</span>
            </div>
          </div>

          <div class="books-controls" aria-label="Chess book search and filters">
            <label class="book-search" for="bookSearch">
              <span>Search by title, author, or topic</span>
              <input id="bookSearch" type="search" autocomplete="off" placeholder="Try endgames, Capablanca, strategy..." />
            </label>
            <div class="book-level-filters" role="group" aria-label="Filter chess books by skill level">
              <button class="book-filter" type="button" data-book-level="all" aria-pressed="true">All</button>
              <button class="book-filter" type="button" data-book-level="Beginner" aria-pressed="false">Beginner</button>
              <button class="book-filter" type="button" data-book-level="Intermediate" aria-pressed="false">Intermediate</button>
              <button class="book-filter" type="button" data-book-level="Advanced" aria-pressed="false">Advanced</button>
            </div>
            <button class="button secondary print-button" id="printBooks" type="button">Print</button>
            <button class="button secondary" id="continueReadingBook" type="button">Continue Reading</button>
          </div>

          <div class="book-category-filters" role="group" aria-label="Filter chess books by category">
            <button class="book-filter" type="button" data-book-category="all" aria-pressed="true">All Topics</button>
            <button class="book-filter" type="button" data-book-category="Openings" aria-pressed="false">Openings</button>
            <button class="book-filter" type="button" data-book-category="Middlegame" aria-pressed="false">Middlegame</button>
            <button class="book-filter" type="button" data-book-category="Endgame" aria-pressed="false">Endgame</button>
            <button class="book-filter" type="button" data-book-category="Tactics" aria-pressed="false">Tactics</button>
            <button class="book-filter" type="button" data-book-category="Strategy" aria-pressed="false">Strategy</button>
            <button class="book-filter" type="button" data-book-category="Biographies" aria-pressed="false">Biographies</button>
          </div>

          <div class="book-verify-note">
            <strong>Free and legal check:</strong> every active book below is free to read or download from Project Gutenberg or Wikimedia Commons and is marked public domain in the United States. Verified June 25, 2026. Modern Ideas in Chess and Tarrasch's The Game of Chess stay on the watchlist until a working legal free source is confirmed.
          </div>

          <div class="book-grid" id="bookGrid" aria-live="polite"></div>
          <article class="book-reader" id="bookReader" hidden aria-live="polite"></article>
          <article class="book-detail" id="bookDetail" hidden aria-live="polite"></article>

          <details class="book-admin" id="bookAdminPanel">
            <summary>Local admin demo: add and manage sample books</summary>
            <p>This single-file version stores admin-added books in this browser only. A real upload database needs a backend, authentication, file scanning, and server-side validation.</p>
            <form id="bookAdminForm">
              <div class="admin-grid">
                <label>
                  Title
                  <input id="adminTitle" name="title" required maxlength="90" />
                </label>
                <label>
                  Author
                  <input id="adminAuthor" name="author" required maxlength="90" />
                </label>
                <label>
                  Skill level
                  <select id="adminLevel" name="level">
                    <option>Beginner</option>
                    <option>Intermediate</option>
                    <option>Advanced</option>
                  </select>
                </label>
                <label>
                  Main category
                  <select id="adminCategory" name="category">
                    <option>Openings</option>
                    <option>Middlegame</option>
                    <option>Endgame</option>
                    <option>Tactics</option>
                    <option>Strategy</option>
                    <option>Biographies</option>
                  </select>
                </label>
                <label class="admin-wide">
                  Public-domain or rights-holder source URL
                  <input id="adminSource" name="source" required placeholder="https://www.gutenberg.org/ebooks/..." />
                </label>
                <label class="admin-wide">
                  Short beginner-friendly summary
                  <textarea id="adminSummary" name="summary" required maxlength="360"></textarea>
                </label>
                <label class="admin-wide">
                  Optional local file name
                  <input id="adminFile" name="file" type="file" accept=".txt,.html,.pdf,.epub" />
                </label>
              </div>
              <div class="book-actions">
                <button class="button" type="submit">Add Local Book</button>
                <button class="button secondary" id="clearLocalBooks" type="button">Clear Local Books</button>
              </div>
            </form>
            <div class="admin-list" id="adminBookList" aria-live="polite"></div>
          </details>
        </div>
      </div>
    </section>

    <section id="notation" class="section-dark" aria-labelledby="notation-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Notation</p>
            <h2 id="notation-title">Read your games</h2>
          </div>
          <p class="section-intro">Chess notation turns a game into a study file. Learn the few symbols that appear constantly and review becomes much easier.</p>
        </div>

        <div class="notation-grid">
          <article class="notation-card">
            <h3>Common move symbols</h3>
            <p>Algebraic notation starts with the piece, then the destination square. Pawns usually skip the piece letter.</p>
            <ul class="notation-list">
              <li><code>Nf3</code><span>Knight moves to f3.</span></li>
              <li><code>exd5</code><span>The e-pawn captures on d5.</span></li>
              <li><code>O-O</code><span>Kingside castling.</span></li>
              <li><code>Qxf7#</code><span>Queen captures on f7 with checkmate.</span></li>
            </ul>
          </article>
          <article class="notation-card callout">
            <h3>Board coordinates</h3>
            <p>Files run a through h from White's left to right. Ranks run 1 through 8 from White's side to Black's side.</p>
            <ul class="topic-list">
              <li>a1 is dark</li>
              <li>White starts on ranks 1-2</li>
              <li>Black starts on ranks 7-8</li>
            </ul>
          </article>
          <article class="notation-card">
            <h3>Review prompt</h3>
            <p>After each game, write one sentence for the opening, one for the tactic you missed, and one for the endgame plan you wanted.</p>
            <ul class="notation-list">
              <li><code>?</code><span>A mistake worth reviewing.</span></li>
              <li><code>!</code><span>A strong move with a clear idea.</span></li>
              <li><code>+/-</code><span>White is clearly better.</span></li>
            </ul>
          </article>
        </div>
      </div>
    </section>

    <section id="play" class="section-dark" aria-labelledby="play-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Beginner game</p>
            <h2 id="play-title">Play the coach</h2>
          </div>
          <p class="section-intro">Practice one friendly game at a time. Legal moves, checks, checkmate, castling, en passant, promotion, and draws are handled by chess.js.</p>
        </div>

        <div class="preference-panel" id="learnerPreferences">
          <h3>Board style</h3>
          <div class="preference-grid">
            <label>Mode
              <select id="prefTheme">
                <option value="dark">Dark</option>
                <option value="light">Light</option>
              </select>
            </label>
            <label>Board
              <select id="prefBoard">
                <option value="wood">Wooden</option>
                <option value="marble">Marble</option>
                <option value="neon">Neon</option>
              </select>
            </label>
            <label>Pieces
              <select id="prefPieces">
                <option value="classic">Classic</option>
                <option value="letter">Letters</option>
              </select>
            </label>
            <label>Coordinates
              <select id="prefCoords">
                <option value="on">On</option>
                <option value="off">Off</option>
              </select>
            </label>
            <label>Animation
              <select id="prefSpeed">
                <option value="normal">Normal</option>
                <option value="slow">Slow</option>
                <option value="fast">Fast</option>
              </select>
            </label>
            <label>No pressure
              <select id="prefPressure">
                <option value="on">On</option>
                <option value="off">Off</option>
              </select>
            </label>
          </div>
          <p class="preference-note" id="motivationMessage">Every master was once a beginner.</p>
        </div>

        <div class="puzzle-shell play-shell">
          <div class="puzzle-board-wrap play-board-wrap" aria-label="Playable chess board">
            <div class="puzzle-board play-board" id="coachBoard" role="grid" aria-label="Player versus AI chess board"></div>
          </div>
          <div class="puzzle-info coach-panel">
            <div class="puzzle-meta">
              <span class="badge" id="gameTurnBadge">White to move</span>
              <span class="badge" id="gameStatusBadge">Loading rules</span>
              <span class="badge" id="gameDifficultyBadge">Easy coach</span>
            </div>
            <div class="mission-selector puzzle-plan-selector coach-levels" role="group" aria-label="AI difficulty">
              <button class="mission-button" type="button" data-game-difficulty="easy" aria-pressed="true">Easy</button>
              <button class="mission-button" type="button" data-game-difficulty="medium" aria-pressed="false">Medium</button>
              <button class="mission-button" type="button" data-game-difficulty="hard" aria-pressed="false">Hard</button>
            </div>
            <p class="simple-coach" id="gameCoach">Loading chess.js so every move follows official chess rules.</p>
            <div class="guided-review" id="guidedReview" hidden aria-live="polite">
              <strong>Guided review</strong>
              <div id="guidedReviewList"></div>
            </div>
            <div class="mini-game-row" id="coachPracticeLinks" hidden aria-label="Recommended practice"></div>
            <div class="captured-row" aria-label="Captured pieces">
              <div>
                <strong>White captured</strong>
                <div class="captured-pieces" id="whiteCaptured"></div>
              </div>
              <div>
                <strong>Black captured</strong>
                <div class="captured-pieces" id="blackCaptured"></div>
              </div>
            </div>
            <div class="move-history" id="moveHistory" aria-label="Move history"></div>
            <p class="trainer-note" id="gamePgn">PGN appears here after export.</p>
            <div class="puzzle-actions">
              <button class="button secondary" type="button" id="undoGame">Undo</button>
              <button class="button secondary" type="button" id="restartGame">Restart</button>
              <button class="button secondary" type="button" id="flipGame">Flip Board</button>
              <button class="button secondary" type="button" id="whyGame">Why?</button>
              <button class="button secondary" type="button" id="replayMistake">Replay Mistake</button>
              <button class="button secondary" type="button" id="showThreats">Threats</button>
              <button class="button secondary" type="button" id="offerDraw">Agree Draw</button>
              <button class="button" type="button" id="exportPgn">Copy PGN</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="puzzles" class="section-warm" aria-labelledby="puzzles-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Puzzle board</p>
            <h2 id="puzzles-title">Find the move</h2>
          </div>
          <p class="section-intro">Become a Chess Ninja: pick one 60-second trick, move the pieces, solve the mini puzzle, then jump to the next idea.</p>
        </div>

        <div class="puzzle-shell">
          <div class="puzzle-board-wrap" aria-label="Chess puzzle position">
            <div class="puzzle-board" id="puzzleBoard"></div>
            <div class="coordinates" aria-hidden="true" id="coordinates"></div>
          </div>
          <div class="puzzle-info">
            <div class="puzzle-meta">
              <span class="badge" id="puzzleLevel">Beginner</span>
              <span class="badge" id="puzzleSide">White to move</span>
              <span class="badge daily-puzzle-badge" id="dailyPuzzleBadge">Today</span>
            </div>
            <div class="puzzle-brief" aria-label="Puzzle details">
              <span class="pressure-rating"><strong id="puzzleRating">400</strong> Elo</span>
              <span id="puzzleEstimate">~1 min</span>
              <span id="puzzleClock">00:00</span>
              <span id="puzzleMistakes">0 mistakes</span>
            </div>
            <div class="trainer-patterns puzzle-tags" id="puzzleTags" aria-label="Puzzle themes"></div>
            <div class="mission-selector puzzle-plan-selector" role="group" aria-label="Study plan puzzle track">
              <button class="mission-button" type="button" data-puzzle-plan="all" aria-pressed="true">All</button>
              <button class="mission-button" type="button" data-puzzle-plan="adaptive" aria-pressed="false">Adaptive</button>
              <button class="mission-button" type="button" data-puzzle-plan="Beginner" aria-pressed="false">Beginner</button>
              <button class="mission-button" type="button" data-puzzle-plan="Intermediate" aria-pressed="false">Intermediate</button>
              <button class="mission-button" type="button" data-puzzle-plan="Advanced" aria-pressed="false">Advanced</button>
              <button class="mission-button" type="button" data-puzzle-plan="Forks" aria-pressed="false">Fork Ninja</button>
              <button class="mission-button" type="button" data-puzzle-plan="Pins" aria-pressed="false">Pin Rescue</button>
              <button class="mission-button" type="button" data-puzzle-plan="Back-rank mates" aria-pressed="false">Back Rank</button>
              <button class="mission-button" type="button" data-puzzle-plan="Checkmates" aria-pressed="false">Mate Sprint</button>
            </div>
            <div class="puzzle-stats" aria-label="Puzzle progress">
              <div class="stat-pill">
                <strong id="puzzleCounter">1 / 6</strong>
                <span>Position</span>
              </div>
              <div class="stat-pill">
                <strong id="puzzleSolved">0</strong>
                <span>Solved</span>
              </div>
              <div class="stat-pill">
                <strong id="puzzleStreak">0</strong>
                <span>Streak</span>
              </div>
            </div>
            <div class="progress-track" aria-hidden="true">
              <span class="progress-fill" id="puzzleProgress"></span>
            </div>
            <details class="puzzle-progress-drawer">
              <summary>Progress and rewards</summary>
              <div class="beginner-progress" aria-label="Beginner progress">
                <div class="progress-mini-stats">
                  <span class="xp-pill" id="xpPill">0 XP</span>
                  <span class="xp-pill level-pill" id="learnerLevelPill">Level: Beginner</span>
                  <span class="xp-pill" id="gamesPlayedPill">Games played 0</span>
                  <span class="xp-pill" id="winRatePill">Win rate 0%</span>
                  <span class="xp-pill" id="puzzlesSolvedPill">Puzzles solved 0</span>
                  <span class="xp-pill" id="bestStreakPill">Best streak 0</span>
                  <span class="xp-pill" id="dailyChallengePill">5-minute challenge ready</span>
                  <span class="xp-pill" id="dailyStreakPill">Current streak 0</span>
                  <span class="xp-pill" id="lessonCompletePill">Missions 0</span>
                  <span class="xp-pill" id="favoriteOpeningPill">Favorite opening: Italian Game</span>
                  <span class="xp-pill" id="puzzleAccuracyPill">Puzzle confidence 0%</span>
                  <span class="xp-pill" id="hangingPiecesPill">Hanging pieces/game 0</span>
                  <span class="xp-pill" id="moveQualityPill">Move quality 100%</span>
                  <span class="xp-pill" id="puzzleRatingPill">Puzzle rating 400</span>
                  <span class="xp-pill" id="timeManagementPill">Time: steady</span>
                </div>
                <p class="habit-reward" id="dailyReward">Reward locked: finish today's puzzle.</p>
                <p class="simple-coach" id="simpleCoach">Simple coach: Try one move. Learning counts more than winning.</p>
                <div class="achievement-row" id="achievementBadges" aria-label="Achievement badges"></div>
                <div class="weekly-chart" id="weeklyChart" aria-label="Weekly progress chart"></div>
                <div class="mini-game-row" aria-label="Mini-games">
                  <a class="button secondary" href="#adventures">Piece Mission</a>
                  <a class="button secondary" href="#shorts">Shorts Sprint</a>
                </div>
              </div>
            </details>
            <h3 id="puzzleTitle">Puzzle title</h3>
            <p id="puzzlePrompt">Puzzle prompt</p>
            <ul class="gentle-checklist thinking-checklist" aria-label="Thinking checklist">
              <li><span>1</span>What is my opponent threatening?</li>
              <li><span>2</span>Are any pieces undefended?</li>
              <li><span>3</span>Can I improve my worst piece?</li>
              <li><span>4</span>Do I have checks, captures, or threats?</li>
            </ul>
            <div class="vision-drill" id="visionDrill">
              <strong>Board Vision</strong>
              <p id="visionQuestion">Which piece is hanging?</p>
              <button class="button secondary" type="button" id="visionAnswer">Show Answer</button>
              <small id="visionAnswerText" hidden></small>
            </div>
            <p class="puzzle-hint hidden" id="puzzleHint">Hint text</p>
            <div class="answers" id="answers"></div>
            <p class="feedback" id="feedback">Choose the strongest move.</p>
            <div class="puzzle-complete" id="puzzleComplete" hidden>
              <strong>Puzzle complete</strong>
              <p id="puzzleCompleteSummary">Accuracy, time, and themes appear here.</p>
              <p id="puzzleExplanation">Why the move works appears here.</p>
            </div>
            <div class="puzzle-actions">
              <div class="puzzle-action-row primary">
                <button class="button" type="button" id="startPuzzle">Start Puzzle</button>
                <button class="button" type="button" id="nextPuzzle">Next Puzzle</button>
                <button class="button secondary" type="button" id="dailyPuzzle">Today&apos;s Puzzle</button>
              </div>
              <div class="puzzle-action-row">
                <button class="button secondary" type="button" id="hintPuzzle">Hint</button>
                <button class="button secondary" type="button" id="revealPuzzle">Show Move</button>
                <button class="button secondary" type="button" id="retryPuzzle">Retry</button>
                <button class="button secondary" type="button" id="analyzePuzzle">Analyze</button>
                <button class="button secondary" type="button" id="replayPuzzle">Replay</button>
              </div>
              <div class="puzzle-action-row utility">
                <button class="button secondary" type="button" id="flipPuzzle">Flip</button>
                <button class="button secondary" type="button" id="soundPuzzle" aria-pressed="false">Sound Off</button>
                <button class="button secondary" type="button" id="resetPuzzle">Reset Score</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="plan" class="section-dark" aria-labelledby="plan-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Study rhythm</p>
            <h2 id="plan-title">Fast progress roadmap</h2>
          </div>
          <p class="section-intro">Pick the track that matches your level, train for a short focused block each day, then repeat the weekly rhythm until the goals feel easy.</p>
        </div>

        <div class="study-plan">
          <article class="plan-panel">
            <div class="plan-meta">
              <span class="badge">Beginner</span>
              <span class="badge">25 min/day</span>
              <span class="badge">First 30 days</span>
            </div>
            <h3>Build board confidence</h3>
            <p>Goal: stop losing pieces for free, learn basic mates, and finish games with a simple plan.</p>
            <ul class="plan-list">
              <li><span>1</span><div><a href="#puzzles">Warm up with 5 easy puzzles: mate in one, mate in two, forks, and hanging pieces.</a></div></li>
              <li><span>2</span><div><a href="#paths">Watch 1 beginner lesson or 3 Shorts, then write one rule you will use today.</a></div></li>
              <li><span>3</span><div><a href="#play">Play one 10+5 game. Before every move, ask: is my king safe and is any piece hanging?</a></div></li>
              <li><span>4</span><div><a href="#notation">Review only one moment: the first blunder or the first move where you felt confused.</a></div></li>
            </ul>
            <div class="plan-focus">Level up when you can solve 50 simple puzzles and play 5 games with fewer hanging pieces.</div>
          </article>
          <article class="plan-panel">
            <div class="plan-meta">
              <span class="badge">Intermediate</span>
              <span class="badge">45 min/day</span>
              <span class="badge">Build speed</span>
            </div>
            <h3>Turn ideas into threats</h3>
            <p>Goal: calculate cleaner, understand your openings, and turn winning positions into real wins.</p>
            <ul class="plan-list">
              <li><span>1</span><div><a href="#puzzles">Solve 12-15 themed puzzles. Repeat every miss until you can explain the tactic.</a></div></li>
              <li><span>2</span><div><a href="#openings">Study one opening line plus the idea behind it: center, development, target, or endgame.</a></div></li>
              <li><span>3</span><div><a href="#play">Play one 15+10 game or two 10+5 games. Choose moves using checks, captures, and threats.</a></div></li>
              <li><span>4</span><div><a href="#notation">Review the first mistake after the opening and list three candidate moves you missed.</a></div></li>
            </ul>
            <div class="plan-focus">Level up when you can name the plan in your main openings and finish 75 puzzles in a week.</div>
          </article>
          <article class="plan-panel">
            <div class="plan-meta">
              <span class="badge">Advanced</span>
              <span class="badge">55 min/day</span>
              <span class="badge">Precision</span>
            </div>
            <h3>Train like a serious player</h3>
            <p>Goal: compare candidate moves, respect opponent resources, and convert small advantages.</p>
            <ul class="plan-list">
              <li><span>1</span><div><a href="#puzzles">Solve 8-10 hard puzzles without moving pieces. Spend 3-5 minutes before checking.</a></div></li>
              <li><span>2</span><div><a href="#videos">Study one master-game position or accuracy video. Write the plan, not just the move.</a></div></li>
              <li><span>3</span><div><a href="#play">Play one slow game. Annotate your plans, critical moments, and time-pressure decisions.</a></div></li>
              <li><span>4</span><div><a href="#videos">Drill one endgame from both sides: pawn race, rook activity, opposition, or conversion.</a></div></li>
            </ul>
            <div class="plan-focus">Level up by deeply reviewing 2 games each week and building an opening file with plans.</div>
          </article>
          <article class="plan-panel wide daily-trainer" id="daily-training" aria-labelledby="daily-training-title">
            <div class="trainer-head">
              <div>
                <div class="plan-meta">
                  <span class="badge">Personalized</span>
                  <span class="badge">Saved daily</span>
                  <span class="badge">No account</span>
                </div>
                <h3 id="daily-training-title">Personalized Daily Training</h3>
                <p>Tell the coach what you need today. The site builds a short plan with puzzles, lessons, games, and review so practice feels clear instead of random.</p>
              </div>
              <button class="button secondary" type="button" id="resetTraining">Reset Today</button>
            </div>

            <form class="trainer-form" id="dailyTrainingForm">
              <label for="trainingLevel">
                Level
                <select id="trainingLevel" name="trainingLevel">
                  <option>Beginner</option>
                  <option>Intermediate</option>
                  <option>Advanced</option>
                </select>
              </label>
              <label for="trainingMinutes">
                Time today: <span id="trainingMinutesLabel">25 min</span>
                <input id="trainingMinutes" name="trainingMinutes" type="range" min="15" max="60" step="1" value="25" />
              </label>
              <label for="trainingGoal">
                Main goal
                <select id="trainingGoal" name="trainingGoal">
                  <option value="balanced">Balanced improvement</option>
                  <option value="rating">Win more games</option>
                  <option value="opening">Fix my openings</option>
                  <option value="tactics">Spot tactics faster</option>
                  <option value="endgame">Finish winning games</option>
                </select>
              </label>
              <button class="button" type="submit">Build Today</button>

              <fieldset class="trainer-field trainer-wide">
                <legend>Weak spots to train</legend>
                <div class="trainer-check-grid">
                  <label class="trainer-check"><input type="checkbox" name="trainingWeakness" value="tactics" checked /> Tactics</label>
                  <label class="trainer-check"><input type="checkbox" name="trainingWeakness" value="openings" /> Openings</label>
                  <label class="trainer-check"><input type="checkbox" name="trainingWeakness" value="endgame" /> Endgame</label>
                  <label class="trainer-check"><input type="checkbox" name="trainingWeakness" value="strategy" /> Strategy</label>
                  <label class="trainer-check"><input type="checkbox" name="trainingWeakness" value="calculation" /> Calculation</label>
                  <label class="trainer-check"><input type="checkbox" name="trainingWeakness" value="review" /> Review</label>
                </div>
              </fieldset>
            </form>

            <div class="trainer-output" id="dailyTrainingOutput" aria-live="polite"></div>
          </article>
          <article class="plan-panel wide">
            <div class="plan-meta">
              <span class="badge">Endgame essentials</span>
              <span class="badge">Convert wins</span>
            </div>
            <h3>Endgames that matter first</h3>
            <ul class="plan-list">
              <li><span>1</span><div><a href="#videos">King and Queen vs. King: learn the box method and finish calmly.</a></div></li>
              <li><span>2</span><div><a href="#videos">King and Rook vs. King: cut off the king, then shrink the board.</a></div></li>
              <li><span>3</span><div><a href="#videos">Opposition: use kings to win key squares.</a></div></li>
              <li><span>4</span><div><a href="#videos">King and Pawn vs. King: know when promotion is possible.</a></div></li>
              <li><span>5</span><div><a href="#videos">Basic pawn endings: push only after your king helps.</a></div></li>
            </ul>
          </article>
          <article class="plan-panel wide">
            <div class="plan-meta">
              <span class="badge">Repeat weekly</span>
              <span class="badge">Fast and simple</span>
              <span class="badge">No marathon needed</span>
            </div>
            <h3>7-day arranger</h3>
            <p>Use this weekly rhythm with your level card above. Keep sessions short, write one lesson after each day, and repeat the weak day next week.</p>
            <div class="weekly-roadmap">
              <a class="day-card" href="#paths">
                <strong>Day 1</strong>
                <span>Foundation</span>
                <p>Watch one lesson, then play one game using only today's main rule.</p>
              </a>
              <a class="day-card" href="#puzzles">
                <strong>Day 2</strong>
                <span>Tactics</span>
                <p>Solve by theme. Replay every missed puzzle until the pattern feels automatic.</p>
              </a>
              <a class="day-card" href="#play">
                <strong>Day 3</strong>
                <span>Slow Game</span>
                <p>Play one focused game. Afterward, mark the first unclear move and one better plan.</p>
              </a>
              <a class="day-card" href="#openings">
                <strong>Day 4</strong>
                <span>Opening</span>
                <p>Study one line and one idea. Do not memorize more than you can explain.</p>
              </a>
              <a class="day-card" href="#videos">
                <strong>Day 5</strong>
                <span>Endgame</span>
                <p>Practice a small ending until you know where the king and pawns belong.</p>
              </a>
              <a class="day-card" href="#puzzles">
                <strong>Day 6</strong>
                <span>Challenge</span>
                <p>Take a puzzle test, then play a game where you slow down at critical moments.</p>
              </a>
              <a class="day-card" href="#notation">
                <strong>Day 7</strong>
                <span>Review</span>
                <p>Collect your three biggest mistakes, rewatch one matching lesson, and reset.</p>
              </a>
            </div>
          </article>
          <article class="plan-panel wide">
            <h3>Daily progress rule</h3>
            <ul class="plan-list">
              <li><span>A</span><div>One lesson gives you the idea. One game tests it. One review makes it stick.</div></li>
              <li><span>B</span><div>If you have only 15 minutes, solve puzzles and review one mistake. Consistency beats a long random session.</div></li>
              <li><span>C</span><div>Write one sentence after training: today I learned, tomorrow I will watch for, my biggest mistake was.</div></li>
            </ul>
          </article>
          <article class="plan-panel wide">
            <h3>Beginner to intermediate path</h3>
            <ul class="plan-list">
              <li><span>1</span><div><a href="#paths">Learn piece movement and basic checkmates.</a></div></li>
              <li><span>2</span><div><a href="#puzzles">Build board vision and avoid hanging pieces.</a></div></li>
              <li><span>3</span><div><a href="#puzzles">Practice tactical patterns until they feel familiar.</a></div></li>
              <li><span>4</span><div><a href="#openings">Learn opening principles before memorizing lines.</a></div></li>
              <li><span>5</span><div><a href="#play">Review games and fix recurring mistakes.</a></div></li>
              <li><span>6</span><div><a href="#videos">Study essential endgames and simple planning.</a></div></li>
              <li><span>7</span><div><a href="#play">Play longer games with calm analysis.</a></div></li>
            </ul>
          </article>
        </div>
      </div>
    </section>
  </main>

  <div class="video-modal" id="videoModal" hidden aria-hidden="true" role="dialog" aria-modal="true" aria-labelledby="videoModalTitle">
    <div class="video-modal-panel">
      <div class="video-modal-bar">
        <p class="video-modal-title" id="videoModalTitle">Chess lesson</p>
        <button class="video-close" type="button" id="videoClose" aria-label="Close video">×</button>
      </div>
      <div class="video-modal-frame" id="videoModalFrame"></div>
    </div>
  </div>

  <footer class="footer">
    <div class="wrap">
      <span>Checkmate Quest</span>
      <span>Learn the board, spot the pattern, make the plan.</span>
    </div>
  </footer>

  <script>
    const heroPieces = [
      "♜", "♞", "♝", "♛", "♚", "♝", "♞", "♜",
      "♟", "♟", "♟", "", "♟", "♟", "♟", "♟",
      "", "", "", "", "", "", "", "",
      "", "", "", "♟", "", "", "", "",
      "", "", "", "♙", "", "", "", "",
      "", "", "♘", "", "", "♘", "", "",
      "♙", "♙", "♙", "", "♙", "♙", "♙", "♙",
      "♖", "", "♗", "♕", "♔", "♗", "", "♖"
    ];

    const pieceMap = {
      K: "♔", Q: "♕", R: "♖", B: "♗", N: "♘", P: "♙",
      k: "♚", q: "♛", r: "♜", b: "♝", n: "♞", p: "♟"
    };

    const classicPieceMap = { ...pieceMap };
    const letterPieceMap = { K: "K", Q: "Q", R: "R", B: "B", N: "N", P: "P", k: "k", q: "q", r: "r", b: "b", n: "n", p: "p" };

    function pieceColorClass(piece) {
      if (/^[KQRBNP]$/.test(piece)) return "white-piece";
      if (/^[kqrbnp]$/.test(piece)) return "black-piece";
      if ("♔♕♖♗♘♙".includes(piece)) return "white-piece";
      if ("♚♛♜♝♞♟".includes(piece)) return "black-piece";
      return "";
    }

    const adventureMissions = [
      {
        short: "Knight",
        role: "Knight mission",
        title: "The Knight's Secret Jump Mission",
        task: "Help the trickster jumper leap from d2 to f3. Select the knight, then click f3.",
        tip: "Knights move in an L shape: two squares one way, then one square sideways.",
        fen: "rnbqkbnr/pppppppp/8/8/8/8/PPPNPPPP/R1BQKBNR",
        from: "d2",
        to: "f3",
        targets: ["f3"],
        success: "Mission complete. The knight jumped over the crowd and landed on f3."
      },
      {
        short: "Queen",
        role: "Queen mission",
        title: "The Queen's Superhero Rescue",
        task: "Send the superhero queen from d1 to h5 to capture the attacker.",
        tip: "Queens can move any distance in a straight line or diagonal if the path is clear.",
        fen: "rnbqkbnr/pppppppp/8/7r/8/8/PPPP1PPP/RNBQKBNR",
        from: "d1",
        to: "h5",
        targets: ["h5"],
        success: "Mission complete. The queen raced along the diagonal and removed the attacker."
      },
      {
        short: "Rook",
        role: "Rook mission",
        title: "The Rook's Castle Wall Patrol",
        task: "Move the castle guardian from a1 to a7 and patrol the open file.",
        tip: "Rooks move straight up, down, left, or right when the lane is open.",
        fen: "rnbqkbnr/1ppppppp/8/8/8/8/1PPPPPPP/RNBQKBNR",
        from: "a1",
        to: "a7",
        targets: ["a7"],
        success: "Mission complete. The rook controlled the whole a-file like a castle hallway."
      },
      {
        short: "Bishop",
        role: "Bishop mission",
        title: "The Bishop's Hidden Sniper Trail",
        task: "Slide the diagonal sniper from c1 to h6.",
        tip: "Bishops stay on one color and move along diagonals.",
        fen: "rnbqkbnr/pppppppp/8/8/8/8/PPP1PPPP/RNBQKBNR",
        from: "c1",
        to: "h6",
        targets: ["h6"],
        success: "Mission complete. The bishop found the long diagonal trail to h6."
      },
      {
        short: "Pawn",
        role: "Pawn mission",
        title: "The Rookie Soldier's Promotion Quest",
        task: "March the rookie soldier from e7 to e8 and reach promotion land.",
        tip: "Pawns move forward one square, and promotion happens on the last rank.",
        fen: "k4bnr/ppppPppp/8/8/8/8/PPPP1PPP/RNBQKBNR",
        from: "e7",
        to: "e8",
        targets: ["e8"],
        success: "Mission complete. The pawn reached the final rank and earned a promotion."
      },
      {
        short: "King",
        role: "King mission",
        title: "Protect the Nervous Boss",
        task: "Move the nervous boss from e1 to f1, one safe step away.",
        tip: "Kings move one square and must never walk into danger.",
        fen: "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQK1NR",
        from: "e1",
        to: "f1",
        targets: ["f1"],
        success: "Mission complete. The king took one careful step to safety."
      }
    ];

    const puzzles = [
      {
        level: "Beginner",
        side: "White to move",
        title: "Back-rank mate",
        prompt: "Black's king is trapped by its own pawns. Which move ends the game?",
        fen: "r5k1/pppp1ppp/8/8/8/8/PPPP1PPP/4R1K1",
        targets: ["e8"],
        hint: "Look for a rook move that uses the open file and attacks the king from the back rank.",
        answers: [
          { move: "Re8#", correct: true },
          { move: "Rg1", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Re8# uses the open e-file. The king cannot capture, block, or run because its escape squares are occupied."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Knight fork",
        prompt: "White can attack the black king and queen at the same time.",
        fen: "r6r/pppp1ppp/4k3/7q/8/3N4/PPPP1PPP/R3K2R",
        targets: ["f4"],
        hint: "The knight wants a square where it checks the king and also points at h5.",
        answers: [
          { move: "Nf4+", correct: true },
          { move: "Nc1", correct: false },
          { move: "Kd2", correct: false }
        ],
        feedback: "Nf4+ checks the king on e6 and also attacks the queen on h5. One knight move creates two threats."
      },
      {
        level: "Advanced",
        side: "Black to move",
        title: "Overloaded defender",
        prompt: "White's queen is guarding too much. Find the forcing capture.",
        fen: "r5k1/pppp1ppp/8/2b5/8/6q1/PPPP1QPP/R5K1",
        targets: ["f2"],
        hint: "The bishop on c5 quietly protects the square next to White's king.",
        answers: [
          { move: "Qxf2+", correct: true },
          { move: "Qg4", correct: false },
          { move: "Kh7", correct: false }
        ],
        feedback: "Qxf2+ removes the defender and gives check. The bishop on c5 protects f2, so the capture cannot be answered by Kxf2."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Queen joins the attack",
        prompt: "The bishop already controls the key diagonal. Which queen move finishes the game?",
        fen: "r5kr/5ppp/8/8/2B5/5Q2/PPPP2PP/R5K1",
        targets: ["f7"],
        hint: "The queen can capture a pawn next to the king, and the bishop protects that landing square.",
        answers: [
          { move: "Qxf7#", correct: true },
          { move: "Qxf7+", correct: false },
          { move: "Bc4", correct: false }
        ],
        feedback: "Qxf7# is mate because the queen attacks g8, the bishop protects f7, and Black's own pieces block the escape squares."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Capture the pinned queen",
        prompt: "Black's queen is lined up with the king. Which capture wins material with check?",
        fen: "r3k2r/pppq1ppp/5N2/1B6/8/8/PPPP1PPP/R3K2R",
        targets: ["d7"],
        hint: "Your bishop can take the queen, and your knight protects the bishop afterward.",
        answers: [
          { move: "Bxd7+", correct: true },
          { move: "Nxd7", correct: false },
          { move: "Bf1", correct: false }
        ],
        feedback: "Bxd7+ wins the queen with check. The knight on f6 protects d7, so Black cannot simply recapture."
      },
      {
        level: "Advanced",
        side: "White to move",
        title: "Pawn break with opposition",
        prompt: "Use the king's support to push the pawn and force the black king backward.",
        fen: "r6r/ppp2ppp/8/3k4/8/3K4/PPP1P1PP/R6R",
        targets: ["e4"],
        hint: "The pawn can advance two squares because it is still on its starting square.",
        answers: [
          { move: "e4+", correct: true },
          { move: "Kc3", correct: false },
          { move: "Kd4", correct: false }
        ],
        feedback: "e4+ works because the white king protects e4. The pawn checks the black king and gains space for the endgame."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Scholar's finish",
        prompt: "The queen and bishop are aimed at f7. Which move is checkmate?",
        fen: "rnb1kbnr/pppp1ppp/8/4p3/2B1P3/5Q2/PPPP1PPP/RNB1K1NR",
        targets: ["f7"],
        hint: "The bishop on c4 protects the queen when she lands beside the king.",
        answers: [
          { move: "Qxf7#", correct: true },
          { move: "Qxf7+", correct: false },
          { move: "Bb5", correct: false }
        ],
        feedback: "Qxf7# works because the queen attacks the king and the bishop protects f7."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Rook lift mate",
        prompt: "Black's king has no safe square. Find the clean mate.",
        fen: "6k1/5ppp/8/8/8/8/5PPP/R5K1",
        targets: ["a8"],
        hint: "Use the rook to attack along the back rank.",
        answers: [
          { move: "Ra8#", correct: true },
          { move: "Kf2", correct: false },
          { move: "Ra7", correct: false }
        ],
        feedback: "Ra8# traps the king on g8. The rook controls the rank and the pawns block escape."
      },
      {
        level: "Intermediate",
        side: "Black to move",
        title: "Queen and bishop battery",
        prompt: "White's king is exposed on g1. Which queen move ends it?",
        fen: "6k1/5ppp/8/2b5/8/6q1/5PPP/6K1",
        targets: ["f2"],
        hint: "The bishop guards f2, so the queen can move there with force.",
        answers: [
          { move: "Qxf2#", correct: true },
          { move: "Qg4", correct: false },
          { move: "Bxf2+", correct: false }
        ],
        feedback: "Qxf2# is mate because the bishop on c5 protects the queen and the king has no capture or flight square."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Remove the defender",
        prompt: "The knight is pinned and the king is boxed in. Which capture finishes the attack?",
        fen: "6k1/5ppp/8/8/2B5/5Q2/5PPP/6K1",
        targets: ["f7"],
        hint: "The queen can capture on f7 with bishop support.",
        answers: [
          { move: "Qxf7#", correct: true },
          { move: "Bxf7+", correct: false },
          { move: "Qd5", correct: false }
        ],
        feedback: "Qxf7# combines queen pressure with bishop protection. Black cannot take the queen or escape."
      },
      {
        level: "Advanced",
        side: "White to move",
        title: "Quiet back-rank killer",
        prompt: "The direct check is available, but only one rook move is mate.",
        fen: "6k1/5ppp/8/8/8/8/5PPP/4R1K1",
        targets: ["e8"],
        hint: "Put the rook on the back rank where it cuts every escape.",
        answers: [
          { move: "Re8#", correct: true },
          { move: "Re7", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Re8# controls the eighth rank while Black's own pawns trap the king."
      },
      {
        level: "Advanced",
        side: "Black to move",
        title: "Corner net",
        prompt: "White's king is stuck in the corner. Find the forcing queen move.",
        fen: "6k1/5ppp/8/8/8/8/5qPP/7K",
        targets: ["f1"],
        hint: "The queen can attack from f1 and cover the escape squares.",
        answers: [
          { move: "Qf1#", correct: true },
          { move: "Qxg2+", correct: false },
          { move: "Qe1+", correct: false }
        ],
        feedback: "Qf1# seals the corner. The king cannot capture the queen or move away from check."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Loose queen",
        prompt: "A black queen is undefended. Which move wins it with check?",
        fen: "4k3/8/8/8/8/8/4q3/4R1K1",
        targets: ["e2"],
        hint: "Use the rook on the open file.",
        answers: [
          { move: "Rxe2+", correct: true },
          { move: "Re8+", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Rxe2+ removes the hanging queen and keeps the move forcing with check."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Fork warm-up",
        prompt: "The knight can check the king and attack the queen.",
        fen: "4k3/8/5N2/7q/8/8/8/4K3",
        targets: ["g8"],
        hint: "Look for a knight check that also points at h6 or h4.",
        answers: [
          { move: "Ng8+", correct: true },
          { move: "Nd7", correct: false },
          { move: "Nh7", correct: false }
        ],
        feedback: "Ng8+ checks the king first. After the king moves, White can collect the queen."
      },
      {
        level: "Intermediate",
        side: "Black to move",
        title: "Pinned defender",
        prompt: "White's queen is tied to king safety. Find the forcing capture.",
        fen: "6k1/5ppp/8/2b5/8/5q2/5QPP/6K1",
        targets: ["f2"],
        hint: "The bishop and queen are already working on the same square.",
        answers: [
          { move: "Qxf2+", correct: true },
          { move: "Qg4", correct: false },
          { move: "Bxf2+", correct: false }
        ],
        feedback: "Qxf2+ removes the defender and keeps White's king under direct pressure."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Candidate checks",
        prompt: "Use checks, captures, and threats. Which check wins the queen?",
        fen: "4k3/3q1ppp/5N2/1B6/8/8/5PPP/6K1",
        targets: ["d7"],
        hint: "The bishop can take the queen because the knight protects the landing square.",
        answers: [
          { move: "Bxd7+", correct: true },
          { move: "Nxd7", correct: false },
          { move: "Bf1", correct: false }
        ],
        feedback: "Bxd7+ is the forcing candidate: it wins the queen and checks the king."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Back-rank theme",
        prompt: "The king is boxed in by pawns. Which rook move uses the open file?",
        fen: "6k1/5ppp/8/8/8/8/5PPP/4R1K1",
        targets: ["e8"],
        hint: "Move the rook to the eighth rank.",
        answers: [
          { move: "Re8#", correct: true },
          { move: "Re7", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Re8# turns the open file into a mating net."
      },
      {
        level: "Intermediate",
        side: "Black to move",
        title: "Battery strike",
        prompt: "The bishop guards the target. Which queen capture is strongest?",
        fen: "6k1/5ppp/8/2b5/8/6q1/5PPP/5RK1",
        targets: ["f2"],
        hint: "Capture the defender next to the king.",
        answers: [
          { move: "Qxf2+", correct: true },
          { move: "Qg4", correct: false },
          { move: "Bxf2+", correct: false }
        ],
        feedback: "Qxf2+ uses the bishop's protection and forces White to answer the attack."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Hanging piece check",
        prompt: "A loose piece can be taken with tempo. Find the forcing capture.",
        fen: "4k3/8/8/8/4b3/8/8/4R1K1",
        targets: ["e4"],
        hint: "Use the rook to take the loose bishop.",
        answers: [
          { move: "Rxe4+", correct: true },
          { move: "Re8+", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Rxe4+ wins material while keeping the initiative."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Threat first",
        prompt: "Choose the move that creates a direct mate threat.",
        fen: "6k1/5ppp/8/8/2B5/5Q2/5PPP/6K1",
        targets: ["a8"],
        hint: "The queen can join the bishop on a long diagonal.",
        answers: [
          { move: "Qa8+", correct: true },
          { move: "Qxf7+", correct: false },
          { move: "Bc4", correct: false }
        ],
        feedback: "Qa8+ uses the diagonal battery and forces Black to solve an immediate king problem."
      },
      {
        level: "Intermediate",
        side: "Black to move",
        title: "Count the guards",
        prompt: "White's f-pawn is pinned. Which capture keeps the attack alive?",
        fen: "6k1/5ppp/8/2b5/8/5q2/5PPP/4R1K1",
        targets: ["f2"],
        hint: "The queen can capture because the bishop controls f2.",
        answers: [
          { move: "Qxf2+", correct: true },
          { move: "Bxf2+", correct: false },
          { move: "Qg4", correct: false }
        ],
        feedback: "Qxf2+ works because the target is guarded and the king has to respond."
      },
      {
        level: "Advanced",
        side: "White to move",
        title: "Deep back-rank check",
        prompt: "Compare candidate rook checks. Which one gives Black no useful defense?",
        fen: "6k1/5ppp/8/8/8/8/5PPP/2R3K1",
        targets: ["c8"],
        hint: "Use the farthest back-rank square available to the rook.",
        answers: [
          { move: "Rc8#", correct: true },
          { move: "Rc7", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Rc8# cuts the whole rank and leaves the boxed-in king with no escape."
      },
      {
        level: "Advanced",
        side: "Black to move",
        title: "Deflection finish",
        prompt: "White's rook is the only defender. Which queen move overloads it?",
        fen: "6k1/5ppp/8/2b5/8/5q2/5PPP/4R1K1",
        targets: ["f2"],
        hint: "Force the king to face a protected queen capture.",
        answers: [
          { move: "Qxf2+", correct: true },
          { move: "Bxf2+", correct: false },
          { move: "Qg4", correct: false }
        ],
        feedback: "Qxf2+ deflects the defense because the queen is protected and the check is forcing."
      },
      {
        level: "Advanced",
        side: "White to move",
        title: "Promotion race",
        prompt: "Use the king's support to make the pawn break decisive.",
        fen: "8/4k3/8/3P4/3K4/8/8/8",
        targets: ["d6"],
        hint: "Advance with check and force the king backward.",
        answers: [
          { move: "d6+", correct: true },
          { move: "Kc5", correct: false },
          { move: "Ke4", correct: false }
        ],
        feedback: "d6+ gains a tempo in the pawn race and pushes the defender away."
      },
      {
        level: "Advanced",
        side: "White to move",
        title: "Calculate before capture",
        prompt: "The tempting capture is not enough. Which forcing move starts the finish?",
        fen: "6k1/5ppp/8/8/2B5/5Q2/5PPP/4R1K1",
        targets: ["e8"],
        hint: "Start with the rook check, then the bishop and queen cover escape squares.",
        answers: [
          { move: "Re8+", correct: true },
          { move: "Qxf7+", correct: false },
          { move: "Bxf7+", correct: false }
        ],
        feedback: "Re8+ is the strongest forcing candidate because it limits the king before any capture."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Chess Ninja fork",
        prompt: "Learn this trick in 60 seconds: jump the knight to check the king and attack the queen.",
        fen: "3q3k/8/8/6N1/8/8/8/4K3",
        targets: ["f7"],
        hint: "Knight jumps can hit two targets at once. Look for a check that also attacks d8.",
        answers: [
          { move: "Nf7+", correct: true },
          { move: "Ne6", correct: false },
          { move: "Nh7+", correct: false }
        ],
        feedback: "Nf7+ checks the king on h8 and attacks the queen on d8. One knight jump creates two jobs."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Pin Rescue in 60",
        prompt: "The queen is stuck in front of the king. Take the pinned piece.",
        fen: "4k3/4q3/8/8/8/8/8/4R1K1",
        targets: ["e7"],
        hint: "A pinned piece cannot move without exposing the king.",
        answers: [
          { move: "Rxe7+", correct: true },
          { move: "Re8+", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Rxe7+ wins the queen because it was pinned to the king. Pins make defenders freeze."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Back Rank Blitz",
        prompt: "60-second trick: use the open file first, then count the king's escape squares.",
        fen: "5rk1/6pp/8/8/8/8/6PP/5RK1",
        targets: ["f8"],
        hint: "Rooks love open files. Capture with check before doing anything slow.",
        answers: [
          { move: "Rxf8+", correct: true },
          { move: "Rf7", correct: false },
          { move: "Kh1", correct: false }
        ],
        feedback: "Rxf8+ removes the defender and checks along the back rank. Open files make rook tactics fast."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Queen Superhero mate",
        prompt: "Become a mate hunter: queen plus bishop can finish this in one move.",
        fen: "6kr/5ppp/8/7Q/2B5/8/5PPP/6K1",
        targets: ["f7"],
        hint: "The bishop protects f7, so the queen can land there safely.",
        answers: [
          { move: "Qxf7#", correct: true },
          { move: "Qxh7+", correct: false },
          { move: "Bxf7+", correct: false }
        ],
        feedback: "Qxf7# works because the queen attacks the king and the bishop protects the queen. Teamwork beats theory."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Mate in 2: corner trap",
        prompt: "Play the first quiet-looking check, watch the king step out, then finish with the protected queen.",
        fen: "7k/5K2/4Q3/8/8/8/8/8",
        targets: ["e8", "g8"],
        hint: "Put the queen on e8 first. Your king protects the final landing square.",
        line: ["Qe8", "Kh7", "Qg8"],
        answers: [
          { move: "Qe8+", correct: true },
          { move: "Qg8+", correct: false },
          { move: "Qh3+", correct: false }
        ],
        feedback: "Qe8+ forces Kh7, then Qg8# works because the queen is protected by the king on f7."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Mate in 3: staircase queen",
        prompt: "Use checks like steps. Each queen move pushes the king closer to the final square.",
        fen: "7k/8/4QK2/8/8/8/8/8",
        targets: ["e8", "g6", "g7"],
        hint: "Start with Qe8+. After the king escapes, keep the queen close to your king.",
        line: ["Qe8", "Kh7", "Qg6", "Kh8", "Qg7"],
        answers: [
          { move: "Qe8+", correct: true },
          { move: "Qg8+", correct: false },
          { move: "Qh3+", correct: false }
        ],
        feedback: "The queen walks from e8 to g6 to g7. The king on f6 protects the final mate."
      },
      {
        level: "Advanced",
        side: "White to move",
        title: "Mate in 4: king escort",
        prompt: "Advanced line: bring the king closer first, then use the same queen staircase finish.",
        fen: "7k/8/3QK3/8/8/8/8/8",
        targets: ["f7", "e6", "e8", "g8"],
        hint: "First improve the king. The queen mate only works when the final square is protected.",
        line: ["Kf7", "Kh7", "Qe6", "Kh8", "Qe8", "Kh7", "Qg8"],
        answers: [
          { move: "Kf7", correct: true },
          { move: "Qe7", correct: false },
          { move: "Qd8+", correct: false }
        ],
        feedback: "Kf7 escorts the queen. After Qe6 and Qe8+, Qg8# is protected and the king is trapped."
      }
    ];

    const freeChessBooks = [
      {
        id: "blue-book-of-chess",
        title: "The Blue Book of Chess",
        author: "Howard Staunton",
        year: "Publication year not stated in Project Gutenberg record",
        edition: "Project Gutenberg eBook No. 16377",
        level: "Beginner",
        categories: ["Openings", "Strategy"],
        topics: ["Rules", "Piece movement", "Openings", "Board basics"],
        summary: "A beginner-friendly primer that starts with the board, piece powers, chess terms, rules, and simple opening explanations. Best for a learner who wants the game explained slowly before jumping into tactics.",
        bestUse: "Read the rules and openings sections first, then play a slow game while naming every legal move.",
        importantDetails: [
          "Learn the board, piece movement, and chess terms before memorizing openings.",
          "Use openings as simple development plans, not as long move lists.",
          "Return to this book when a rule or special move feels confusing."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/16377",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      },
      {
        id: "chess-and-checkers-way-to-mastership",
        title: "Chess and Checkers: The Way to Mastership",
        author: "Edward Lasker",
        year: "1918",
        edition: "Project Gutenberg eBook No. 4913",
        level: "Beginner",
        categories: ["Tactics", "Strategy"],
        topics: ["Rules", "Tactics", "Strategy", "Illustrative games"],
        summary: "A clear early-20th-century guide that explains rules, tactical ideas, strategy, and model play in plain language. Use the chess chapters for a practical bridge from rules to real decisions.",
        bestUse: "Skim the rules, then focus on the chess examples that show why forcing moves matter.",
        importantDetails: [
          "Rules are only the start; the real goal is finding threats and replies.",
          "Simple tactics become easier when you ask what each move attacks.",
          "Model games help beginners copy good habits without overthinking."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/4913",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      },
      {
        id: "chess-fundamentals",
        title: "Chess Fundamentals",
        author: "Jose Raul Capablanca",
        year: "1921",
        edition: "Project Gutenberg eBook No. 33870",
        level: "Beginner",
        categories: ["Openings", "Middlegame", "Endgame", "Strategy"],
        topics: ["Endgames", "Simple mates", "Openings", "Middlegame principles"],
        summary: "Capablanca teaches the basics through direct examples: mating patterns, pawn promotion, elementary endings, opening ideas, and the kind of simple plans that make beginner games easier to understand.",
        bestUse: "Study one example at a time, then set up a board and replay the idea until it feels obvious.",
        importantDetails: [
          "Endgames teach piece coordination faster than memorizing opening traps.",
          "Simple mates and pawn endings build confidence for finishing won games.",
          "Capablanca's key lesson is clarity: improve pieces, reduce confusion, and convert."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/33870",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      },
      {
        id: "chess-strategy",
        title: "Chess Strategy",
        author: "Edward Lasker",
        year: "1915 second edition",
        edition: "Project Gutenberg eBook No. 5614; translated by J. Du Mont",
        level: "Intermediate",
        categories: ["Openings", "Middlegame", "Endgame", "Strategy"],
        topics: ["Strategy", "Piece activity", "Openings", "Endgames"],
        summary: "A structured strategy course for players who know the rules and want better plans. It connects piece movement, pawn play, opening judgment, middlegame planning, and endgame thinking.",
        bestUse: "Read the planning sections with your own recent games open, then mark where your pieces had no job.",
        importantDetails: [
          "Strategy means improving your worst piece and choosing useful pawn moves.",
          "Opening moves should connect to a middlegame plan.",
          "Endgame thinking begins earlier than most beginners expect."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/5614",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      },
      {
        id: "checkmates-for-three-pieces",
        title: "Checkmates for Three Pieces",
        author: "William Brett Fishburne",
        year: "Publication year not stated in Project Gutenberg record",
        edition: "Project Gutenberg eBook No. 4542",
        level: "Intermediate",
        categories: ["Tactics", "Endgame"],
        topics: ["Checkmate patterns", "Piece coordination", "Endgame tactics", "Calculation"],
        summary: "A compact pattern book for learning how small groups of pieces finish the king. It is useful when a learner already knows legal moves but misses simple mating nets.",
        bestUse: "Use it as a puzzle warm-up: name the checking piece, the guard, and the escape squares.",
        importantDetails: [
          "Checkmate usually needs one attacking piece and at least one helper.",
          "Always count the king's escape squares before choosing the final move.",
          "Small mating patterns make bigger attacks easier to understand."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/4542",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      },
      {
        id: "chess-history-and-reminiscences",
        title: "Chess History and Reminiscences",
        author: "H. E. Bird",
        year: "Publication year not stated in Project Gutenberg record",
        edition: "Project Gutenberg eBook No. 4902",
        level: "Intermediate",
        categories: ["Biographies", "Strategy"],
        topics: ["Chess history", "Classic players", "Practical lessons", "Game culture"],
        summary: "A historical and biographical chess read that helps learners see how classic players thought about the game. It is best used for context, inspiration, and memorable strategic ideas.",
        bestUse: "Read short sections between tactics sessions and write down one practical lesson from each story.",
        importantDetails: [
          "Chess history gives names and stories to ideas you already see on the board.",
          "Classic games often show simple plans more clearly than modern engine-heavy analysis.",
          "Use the stories as memory hooks, not as a replacement for practice."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/4902",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      },
      {
        id: "my-system",
        title: "My System",
        author: "Aron Nimzowitsch; translated by Philip Hereford",
        year: "1925 original; 1930 Harcourt, Brace & Co. edition",
        edition: "Wikimedia Commons PDF sourced from Internet Archive",
        level: "Advanced",
        categories: ["Middlegame", "Strategy"],
        topics: ["Prophylaxis", "Pawn chains", "Blockade", "Positional play"],
        summary: "A classic positional manual for serious learners. Study it after the basics, because the ideas are powerful but abstract: restraint, blockade, overprotection, pawn chains, and long-term piece placement.",
        bestUse: "Do not read it straight through. Pick one idea, find it in your own game, then move to the next idea.",
        importantDetails: [
          "Prophylaxis means asking what your opponent wants before choosing your move.",
          "Blockades and pawn chains decide where pieces belong.",
          "Overprotection is useful when a key square controls the whole position."
        ],
        printableContent: "Wikimedia Commons provides the public-domain PDF record and original file for reading and printing.",
        sourceName: "Wikimedia Commons / Internet Archive",
        sourceUrl: "https://commons.wikimedia.org/wiki/File:My_System.pdf",
        legal: "Wikimedia Commons identifies the 1930 edition as public domain in the United States because it was published before January 1, 1931."
      },
      {
        id: "chess-generalship-vol-1",
        title: "Chess Generalship, Vol. I. Grand Reconnaissance",
        author: "Franklin K. Young",
        year: "Publication year not stated in Project Gutenberg record",
        edition: "Project Gutenberg eBook No. 55278",
        level: "Advanced",
        categories: ["Middlegame", "Strategy"],
        topics: ["Planning", "Evaluation", "Position reconnaissance", "Strategic discipline"],
        summary: "An advanced strategic manual with a military-style vocabulary. Use it for the big lesson: before attacking, inspect the whole board and understand the position's weak points.",
        bestUse: "Read it slowly as a planning checklist, then apply the checklist to one serious game.",
        importantDetails: [
          "Good plans begin with reconnaissance: threats, weaknesses, files, diagonals, and king safety.",
          "Do not attack just because you can; attack when the position gives you targets.",
          "Evaluation should happen before calculation, then calculation checks whether the plan works."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/55278",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      },
      {
        id: "paul-morphy-exploits-and-triumphs",
        title: "The Exploits and Triumphs, in Europe, of Paul Morphy, the Chess Champion",
        author: "Frederick Milnes Edge",
        year: "Publication year not stated in Project Gutenberg record",
        edition: "Project Gutenberg eBook No. 34180",
        level: "Advanced",
        categories: ["Biographies", "Openings", "Tactics"],
        topics: ["Paul Morphy", "Classic attacking play", "Open games", "Chess biography"],
        summary: "A classic account of Paul Morphy's European tour. For learners, the value is seeing rapid development, open lines, initiative, and direct attacks in memorable historical context.",
        bestUse: "Treat it as attacking inspiration: after each story or game, ask how Morphy developed faster.",
        importantDetails: [
          "Morphy's games reward fast development and open lines.",
          "Attack works best when pieces join together before the queen rushes in.",
          "Biographical context makes classic tactical patterns easier to remember."
        ],
        printableContent: "Project Gutenberg provides public-domain reading formats including online HTML, EPUB, Kindle, and plain text.",
        sourceName: "Project Gutenberg",
        sourceUrl: "https://www.gutenberg.org/ebooks/34180",
        legal: "Project Gutenberg lists this eBook as public domain in the USA and free to download."
      }
    ];

    const shortVideos = [
      {
        id: "Vnblc4jfJHU",
        topic: "Mate",
        duration: "0:25",
        title: "How to win Chess in 3 moves!",
        headline: "Three-move mate trap",
        note: "A quick punishment pattern for slow king defense."
      },
      {
        id: "8Vuwv-aEEXQ",
        topic: "Mate",
        duration: "0:16",
        title: "Checkmate in 6 Moves | Chess Openings and Tricks",
        headline: "Six-move checkmate",
        note: "See how early queen pressure can become a forced finish."
      },
      {
        id: "Kor7ai1q6Vk",
        topic: "Opening",
        duration: "0:30",
        title: "4 MOVE CHECKMATE: Best Chess Trap for Beginners",
        headline: "Wayward queen trap",
        note: "Learn the classic beginner mate and why f7 is vulnerable."
      },
      {
        id: "CbfkPbGrPgw",
        topic: "Tactics",
        duration: "0:17",
        title: "Chess Tactics You MUST Know!",
        headline: "Must-know tactic",
        note: "A fast pattern check for finding forcing moves."
      },
      {
        id: "QQ69f80QxHA",
        topic: "Tip",
        duration: "0:41",
        title: "IMPORTANT Chess Tip",
        headline: "Important chess habit",
        note: "A short reminder that keeps your moves purposeful."
      },
      {
        id: "O_8heoqCuFU",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "0:54",
        title: "8 moves Checkmate! Queen Sacrifice!",
        headline: "Queen-sac mate",
        note: "Watch how sacrifice and tempo combine for checkmate."
      },
      {
        id: "OVsyDJ3hgKM",
        topic: "Skill",
        duration: "0:35",
        title: "Most Important Chess Skill",
        headline: "Core chess skill",
        note: "A sharp clip about the skill every improving player needs."
      },
      {
        id: "90uOYlG68bg",
        topic: "Tactics",
        duration: "0:47",
        title: "Once-in-a-Lifetime Chess Tactics",
        headline: "Rare tactic shot",
        note: "Train your eye to notice a spectacular forcing idea."
      },
      {
        id: "s9sXXRgfozI",
        topic: "Opening",
        duration: "0:27",
        title: "Beating King's Pawn with a Brilliant Move",
        headline: "Answer 1. e4",
        note: "A quick opening idea against the king's pawn."
      },
      {
        id: "_KAc128DlMY",
        topic: "Strategy",
        duration: "0:31",
        title: "The Secret To Chess...",
        headline: "The chess secret",
        note: "A compact idea for turning moves into plans."
      },
      {
        id: "6EDYuq6WcRo",
        topic: "Opening",
        duration: "0:11",
        title: "Dutch defence trap",
        headline: "Dutch trap flash",
        note: "A fast trap to recognize before the opening gets wild."
      },
      {
        id: "y2tOtMiBL2w",
        topic: "Mate",
        duration: "0:35",
        title: "Checkmate in 7 moves",
        headline: "Seven-move finish",
        note: "Follow the forcing checks to a clean early mate."
      },
      {
        id: "uZqud7iFPbs",
        topic: "Mate",
        duration: "0:56",
        title: "WIN AT CHESS In 8 Moves!",
        headline: "Eight-move win",
        note: "A quick attacking line for punishing loose development."
      },
      {
        id: "fHtMC-EqYhs",
        topic: "Tactics",
        duration: "0:50",
        title: "How To Calculate and Find Tactics In Chess",
        headline: "Calculate tactics",
        note: "A short method for checking forcing moves first."
      },
      {
        id: "_RHaVTAYnTs",
        topic: "Tactics",
        duration: "0:13",
        title: "Brilliant King move | Chess tactics",
        headline: "Brilliant king move",
        note: "A tiny tactic that shows the king can be active too."
      },
      {
        id: "p29X57WBTrY",
        topic: "Opening",
        duration: "0:33",
        title: "This Opening will Destroy Your Opponent's Career",
        headline: "Sharp opening trap",
        note: "Spot the trap before your opponent walks into it."
      },
      {
        id: "iTR4OBr13bY",
        topic: "Opening",
        duration: "0:22",
        title: "EASY Chess Opening",
        headline: "Easy opening idea",
        note: "A simple setup for getting pieces out quickly."
      },
      {
        id: "ai8CRRO-Tzs",
        topic: "Opening",
        duration: "0:26",
        title: "The best opening with black",
        headline: "Black opening pick",
        note: "A quick option for fighting back with Black."
      },
      {
        id: "9VFe8wHlB28",
        topic: "Opening",
        duration: "0:44",
        title: "Opening traps and quick checkmate",
        headline: "Opening trap sprint",
        note: "Learn a fast gambit-style idea and the mate threat behind it."
      },
      {
        id: "mbZIjNKlxuY",
        topic: "Opening",
        duration: "0:50",
        title: "EASIEST CHESS OPENING",
        headline: "Easiest opening",
        note: "A beginner-friendly opening setup with clear first moves."
      },
      {
        id: "qJHUh9h-Q84",
        topic: "Opening",
        duration: "1:00",
        title: "The Best Chess Opening For Beginners?",
        headline: "Beginner opening pick",
        note: "A one-minute opening choice for easy development."
      },
      {
        id: "f_UqFFwi_rs",
        topic: "Opening",
        duration: "0:27",
        title: "The Queens Gambit",
        headline: "Queen's Gambit flash",
        note: "A quick look at the famous d4 and c4 opening idea."
      },
      {
        id: "OxRWuF0NPyM",
        topic: "Opening",
        duration: "0:11",
        title: "Bird's Opening: Trap Your Opponent Like a Pro",
        headline: "Bird's Opening trap",
        note: "A fast trap idea from a less common first move."
      },
      {
        id: "AXRLarjbSgM",
        topic: "Opening",
        duration: "0:29",
        title: "Learn This EASY Chess Trap",
        headline: "Easy trap pattern",
        note: "A short opening trap to add to your pattern bank."
      },
      {
        id: "1zw7V1o9K98",
        topic: "Opening",
        duration: "0:59",
        title: "Magnus Carlsen EXPLAINS the BEST CHESS OPENING",
        headline: "Opening explained",
        note: "A quick grandmaster take on choosing a playable opening."
      },
      {
        id: "n05fNUA6PQ4",
        topic: "Opening",
        duration: "0:15",
        title: "King's gambit chess trap",
        headline: "King's Gambit trap",
        note: "See how a risky gambit can become a fast attack."
      },
      {
        id: "n2ZtFqvoy0w",
        topic: "Endgame",
        duration: "1:00",
        title: "How to Win an Endgame",
        headline: "Win the endgame",
        note: "A one-minute reminder for converting a simplified position."
      },
      {
        id: "V09wOvcJJbM",
        topic: "Endgame",
        duration: "0:32",
        title: "What Pawn Promotion Actually Looks Like",
        headline: "Pawn promotion",
        note: "Watch the finish line every passed pawn is chasing."
      },
      {
        id: "I30wGxgXFv4",
        topic: "Endgame",
        duration: "0:29",
        title: "The Art of Stalemate!",
        headline: "Stalemate trick",
        note: "A quick warning about the draw that saves lost positions."
      },
      {
        id: "jr3GYrJDnVg",
        topic: "Endgame",
        duration: "0:37",
        title: "Endgame Secrets",
        headline: "Endgame secret",
        note: "A tiny endgame idea from high-level play."
      },
      {
        id: "dunOMb_XfOg",
        topic: "Endgame",
        duration: "0:28",
        title: "Know This Rook Endgame TRICK To Draw... Or LOSE!",
        headline: "Rook draw trick",
        note: "Remember the defensive detail before the rook ending slips."
      },
      {
        id: "AtgEFLJ7jVc",
        topic: "Mate",
        duration: "0:41",
        title: "Checkmate trap every player falls for",
        headline: "Common mate trap",
        note: "A practical pattern that catches careless king safety."
      },
      {
        id: "E2biHMcMNR0",
        topic: "Puzzle",
        duration: "0:10",
        title: "Can you solve this simple puzzle?",
        headline: "Simple puzzle",
        note: "Pause the board, choose the forcing move, then check the answer."
      },
      {
        id: "y5UzupHULcc",
        topic: "Puzzle",
        duration: "0:45",
        title: "Can You Find The Brilliant Move? Chess Puzzle 84",
        headline: "Find the brilliant move",
        note: "A quick puzzle rep for spotting a hidden tactic."
      },
      {
        id: "ylPIQFOqq88",
        topic: "Endgame",
        duration: "0:58",
        title: "3 pawns vs 3 pawns chess puzzle",
        headline: "Pawn race puzzle",
        note: "Practice pawn timing in a tiny endgame race."
      },
      {
        id: "SaeOMqoC8Mw",
        topic: "Mate",
        duration: "0:14",
        title: "Win in 3 moves",
        headline: "Three-move finish",
        note: "A tiny attacking pattern you can spot from move one."
      },
      {
        id: "BSTiLz4Jfmc",
        topic: "Puzzle",
        duration: "0:45",
        title: "The 3x3 Chess Puzzle That Breaks Your Brain!",
        headline: "3x3 brain teaser",
        note: "A compact board puzzle for calculation without clutter."
      },
      {
        id: "jPxusiHa0xw",
        topic: "Mate",
        duration: "0:18",
        title: "Single Knight Checkmate",
        headline: "Knight mate motif",
        note: "Spot how a knight can close the final escape square."
      },
      {
        id: "fuSH59tZPO0",
        topic: "Puzzle",
        duration: "0:13",
        title: "Can u Explain? Chess puzzle mate in 2",
        headline: "Mate-in-two flash",
        note: "A very fast checkmate puzzle for forcing-move vision."
      },
      {
        id: "N_XDJ0woYHk",
        topic: "Puzzle",
        duration: "0:06",
        title: "Brilliant Chess Mate in 2 Moves",
        headline: "Mate in two",
        note: "Six seconds, one target: find the mating pattern."
      },
      {
        id: "QNKgtULOamY",
        topic: "Puzzle",
        duration: "0:23",
        title: "3000 IQ Chess Puzzle",
        headline: "Tactical puzzle spark",
        note: "Look for the forcing idea before the reveal lands."
      },
      {
        id: "eUiElJvLo6c",
        topic: "Puzzle",
        duration: "0:06",
        title: "White to move. Mate in 2",
        headline: "White to move",
        note: "A lightning mate-in-two rep for pattern recognition."
      },
      {
        id: "yTpNnz3PVSo",
        topic: "Mate",
        duration: "0:14",
        title: "Mate in 4",
        headline: "Mate in four",
        note: "Trace the forcing checks until the king runs out of squares."
      },
      {
        id: "-OU3WJyraKQ",
        topic: "Mate",
        duration: "0:19",
        title: "Checkmate in 4 moves!",
        headline: "Four-move mate",
        note: "A fast opening finish every beginner should recognize."
      },
      {
        id: "PaZVLsojjG0",
        topic: "Mate",
        duration: "0:23",
        title: "How To Win Chess In 2 Moves",
        headline: "Two-move lesson",
        note: "The fastest mate teaches why opening king safety matters."
      },
      {
        id: "0vAozwpZAcI",
        topic: "Mate",
        duration: "0:15",
        title: "Checkmate in 5 Moves: Chess Tricks",
        headline: "Five-move trick",
        note: "A quick trick built from checks and weak squares."
      },
      {
        id: "cF8izlNwIIU",
        topic: "Mate",
        duration: "0:20",
        title: "CHECKMATE IN 7",
        headline: "Checkmate in seven",
        note: "A rapid mate line for training attack tempo."
      },
      {
        id: "f2xXL537e7I",
        topic: "Mate",
        duration: "0:12",
        title: "How to Checkmate in Just 4 Moves",
        headline: "Four-move checkmate",
        note: "See the pattern and the defensive lesson behind it."
      },
      {
        id: "S1s6sqaaCdg",
        topic: "Mate",
        duration: "0:09",
        title: "4 move checkmate",
        headline: "Quick four-move mate",
        note: "A tiny version of the classic beginner checkmate."
      },
      {
        id: "xtV_qZ0kDXY",
        topic: "Mate",
        duration: "0:19",
        title: "How to Win Chess in 3 Moves",
        headline: "Three-move trap",
        note: "Another fast example of punishing exposed diagonals."
      },
      {
        id: "CdZLO5Wbfyk",
        topic: "Puzzle",
        duration: "0:06",
        title: "1 Move Checkmate",
        headline: "Mate in one",
        note: "Instant pattern check: find the only finishing move."
      },
      {
        id: "RO8Glb42K2o",
        topic: "Mate",
        duration: "0:14",
        title: "Checkmate in just 8 moves",
        headline: "Eight-move beginner trap",
        note: "A quick checkmate trap to recognize and avoid."
      },
      {
        id: "9URyJG68wj4",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "0:37",
        title: "6 moves Checkmate! Dirty Trick in the Opening!",
        headline: "Dirty opening mate",
        note: "A fast Biyaherong trap that teaches early king safety."
      },
      {
        id: "adHrqOu-kS4",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "0:44",
        title: "5 Moves Checkmate! Queen Sacrifice!",
        headline: "Five-move queen sac",
        note: "Use forcing checks to turn a queen sacrifice into mate."
      },
      {
        id: "pv05RJ69R9s",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "0:48",
        title: "9 moves Checkmate in the Opening!",
        headline: "Nine-move opening mate",
        note: "A compact attacking line built around quick development."
      },
      {
        id: "GahxuKy7kRc",
        topic: "Opening",
        creator: "Biyaherong",
        duration: "0:56",
        title: "WIN FAST USING THIS OPENING TRAP!",
        headline: "Win-fast trap",
        note: "A Biyaherong opening trap for punishing careless moves."
      },
      {
        id: "4xBgIx_Rr_Y",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "0:50",
        title: "5 moves Checkmate Using Queen Sacrifice!",
        headline: "Queen-sac pattern",
        note: "Another quick queen sacrifice pattern for attacking vision."
      },
      {
        id: "Rj0fu-k6eWA",
        topic: "Opening",
        creator: "Biyaherong",
        duration: "0:58",
        title: "Quickest Win in the Caro Kann Opening!",
        headline: "Caro-Kann quick win",
        note: "See one fast way the Caro-Kann can go wrong."
      },
      {
        id: "kEqoib0vLn8",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "1:02",
        title: "7 moves Checkmate after Queen Sacrifice!",
        headline: "Seven-move queen sac",
        note: "A sharper sacrifice line for calculating forcing moves."
      },
      {
        id: "AbUagQAAPA4",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "1:02",
        title: "Queen Sacrifice in the Opening! Force Checkmate!",
        headline: "Forced queen-sac mate",
        note: "Study how a sacrifice becomes safe when every reply is forced."
      },
      {
        id: "Bi3mCYm8t9k",
        topic: "Opening",
        creator: "Biyaherong",
        duration: "1:03",
        title: "Fastest Checkmate in Carokann Opening!",
        headline: "Caro-Kann mate shot",
        note: "A Caro-Kann trap for players ready to spot tactical details."
      },
      {
        id: "BI24dtla0TU",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "1:06",
        title: "QUICK Checkmate! Queen Sacrifice in the Opening!",
        headline: "Quick queen-sac checkmate",
        note: "Connect opening tempo, sacrifice, and king exposure."
      },
      {
        id: "zuztuAIHvo4",
        topic: "Opening",
        creator: "Biyaherong",
        duration: "1:17",
        title: "Easy Win against Kings Gambit!",
        headline: "King's Gambit answer",
        note: "A longer Short showing how to meet a sharp gambit."
      },
      {
        id: "46f_wcofIPE",
        topic: "Mate",
        creator: "Biyaherong",
        duration: "1:12",
        title: "Unexpected Checkmate in the Opening!",
        headline: "Unexpected opening mate",
        note: "An advanced-looking mating attack from a quick opening slip."
      },
      {
        id: "B3Jl5kTwQqU",
        topic: "Endgame",
        creator: "Biyaherong",
        duration: "1:06",
        title: "Amazing Pawn Endgame Finished!",
        headline: "Pawn endgame finish",
        note: "A short endgame example for promotion timing and pawn races."
      },
      {
        id: "w65DmISackc",
        topic: "Opening",
        creator: "Biyaherong",
        duration: "Short",
        title: "Biyaherong Chess Coach Short",
        headline: "Coach opening lesson",
        note: "A Biyaherong Chess Coach clip added to complete the advanced coach track."
      },
      {
        id: "Um4s2urqVJY",
        topic: "Mate",
        duration: "Short",
        title: "Checkmate in 3 Moves",
        headline: "Three-move checkmate lesson",
        note: "A beginner-friendly mate pattern for winning fast when the king is exposed."
      },
      {
        id: "UrUnUtbFP54",
        topic: "Basics",
        duration: "Short",
        title: "How to Play Chess in a Minute",
        headline: "One-minute chess basics",
        note: "A quick rules refresher for new players learning the board."
      },
      {
        id: "VXJNTGv4F4o",
        topic: "Basics",
        duration: "Short",
        title: "Names of Chess Pieces",
        headline: "Piece names and roles",
        note: "A fast beginner clip for recognizing each piece before learning plans."
      },
      {
        id: "uFNTQAFjai8",
        topic: "Tip",
        duration: "Short",
        title: "Win Every Chess Game With This Simple Trick",
        headline: "Simple beginner trick",
        note: "A short idea that shows how one threat can guide the next move."
      },
      {
        id: "4E9drlZ0Vns",
        topic: "Mate",
        duration: "Short",
        title: "How to Win Chess in 2 Moves",
        headline: "Two-move mate warning",
        note: "Learn the fastest mate and the defensive habit that prevents it."
      },
      {
        id: "Lltl5nQmiN8",
        topic: "Opening",
        duration: "Short",
        title: "Learn the Caro-Kann in 1 Minute",
        headline: "Caro-Kann starter",
        note: "A compact opening intro for meeting 1. e4 with a solid setup."
      },
      {
        id: "qQ1-0EJmQvg",
        topic: "Opening",
        duration: "Short",
        title: "Chess Tricks for Black Against e4",
        headline: "Black response to e4",
        note: "A simple opening trick to watch for when White starts with the king pawn."
      },
      {
        id: "7lr9wWEvbcA",
        topic: "Opening",
        duration: "Short",
        title: "Aggressive Chess Opening",
        headline: "Aggressive opening idea",
        note: "A quick look at how opening activity can create early pressure."
      },
      {
        id: "u3NaExzBL6w",
        topic: "Tip",
        duration: "Short",
        title: "How to Get Better at Chess",
        headline: "Better chess habit",
        note: "A short improvement reminder for choosing more purposeful moves."
      },
      {
        id: "5t9fziJGCcg",
        topic: "Mate",
        duration: "Short",
        title: "Mate in 10 Moves",
        headline: "Ten-move mate path",
        note: "Follow the attacking pattern and see how small threats stack up."
      },
      {
        id: "n51jOpVhI-k",
        topic: "Tactics",
        duration: "Short",
        title: "Two Brilliant Chess Moves",
        headline: "Two-move tactic spark",
        note: "A quick tactical example for spotting brilliant forcing ideas."
      },
      {
        id: "wi-5TDLAN-o",
        topic: "Puzzle",
        duration: "Short",
        title: "Can You Solve This Simple Puzzle?",
        headline: "Simple puzzle test",
        note: "Pause, calculate the forcing move, then compare your answer."
      },
      {
        id: "p0iwRDssQhI",
        topic: "Mate",
        duration: "Short",
        title: "Win in 5 Moves",
        headline: "Five-move queen sacrifice",
        note: "A fast queen-sacrifice attack that teaches forcing checks."
      },
      {
        id: "xyx-AEH18Zs",
        topic: "Opening",
        duration: "Short",
        title: "King Burger Checkmate Trap",
        headline: "Opening mate trap",
        note: "A named trap lesson for punishing loose king safety."
      },
      {
        id: "baLYalPxhmI",
        topic: "Tactics",
        duration: "Short",
        title: "Stop This Chess Trick",
        headline: "Trick defense",
        note: "Learn the warning signs before a common trick lands."
      },
      {
        id: "gAw6F-WaJaY",
        topic: "Opening",
        duration: "Short",
        title: "Tennison Gambit",
        headline: "Tennison Gambit idea",
        note: "A gambit pattern that shows how tempo and tactics connect."
      },
      {
        id: "kLbvupI26-A",
        topic: "Opening",
        duration: "Short",
        title: "Easy Chess Trap",
        headline: "Easy opening trap",
        note: "A practical trap for learning how early mistakes get punished."
      },
      {
        id: "4b2hs1PUcww",
        topic: "Mate",
        duration: "Short",
        title: "Checkmate in 5 Moves Using an Opening Trap",
        headline: "Five-move opening trap",
        note: "A short mating line that turns opening pressure into checkmate."
      },
      {
        id: "9XZqUGBWass",
        topic: "Opening",
        duration: "Short",
        title: "First Trap Magnus Fell For",
        headline: "Famous trap lesson",
        note: "Study a sharp trap idea and why even strong players must respect tactics."
      },
      {
        id: "Mdd1uSRzmZU",
        topic: "Opening",
        duration: "Short",
        title: "High Success Rate Trap",
        headline: "Reliable trap pattern",
        note: "A compact opening trap lesson for spotting a common mistake."
      },
      {
        id: "U2KFhsWMEP4",
        topic: "Opening",
        duration: "Short",
        title: "Beating the Queen's Gambit",
        headline: "Queen's Gambit tactic",
        note: "A quick opening tactic for meeting the Queen's Gambit."
      },
      {
        id: "O7xcKga2hZk",
        topic: "Mate",
        duration: "Short",
        title: "Checkmate in 6: Latvian Gambit",
        headline: "Latvian Gambit mate",
        note: "A six-move attacking line from a sharp gambit setup."
      },
      {
        id: "-SGMZEftNf0",
        topic: "Opening",
        duration: "Short",
        title: "Mate in 6 Moves: Budapest Trap",
        headline: "Budapest trap",
        note: "A tactical opening lesson for using development with tempo."
      },
      {
        id: "cN4Xpz5yHSQ",
        topic: "Opening",
        duration: "Short",
        title: "Fried Liver Counter Attack",
        headline: "Fried Liver counter",
        note: "Learn a counter-trap idea against one of the most famous beginner attacks."
      },
      {
        id: "K28CuIQVB-U",
        topic: "Endgame",
        duration: "Short",
        title: "Checkmate With Two Bishops",
        headline: "Two-bishop mate",
        note: "A compact endgame lesson on coordinating both bishops with the king."
      },
      {
        id: "-UZPXzwt3QI",
        topic: "Endgame",
        duration: "Short",
        title: "Chess Endgame Trick You Must Know",
        headline: "Must-know endgame trick",
        note: "A practical endgame idea for saving or converting a close position."
      },
      {
        id: "BJThK1rAT-0",
        topic: "Endgame",
        duration: "Short",
        title: "Crazy Endgame Sacrifices",
        headline: "Endgame sacrifice idea",
        note: "A reminder that precise endgames can still contain tactical shots."
      },
      {
        id: "cl_Ur0wQ6Og",
        topic: "Puzzle",
        duration: "Short",
        title: "Brilliant Sacrifice",
        headline: "Find the sacrifice",
        note: "Calculate the forcing line before choosing the brilliant move."
      },
      {
        id: "QCXGvgCQXjU",
        topic: "Puzzle",
        duration: "Short",
        title: "How Fast Can You Solve This Puzzle?",
        headline: "Speed puzzle",
        note: "A quick puzzle rep for training pattern recognition under time pressure."
      },
      {
        id: "6ohv0VmtZz4",
        topic: "Tactics",
        duration: "Short",
        title: "Chess Puzzle Tactics",
        headline: "Tactical puzzle",
        note: "Look for checks, captures, and threats before the answer appears."
      },
      {
        id: "oSvOUXIwbxE",
        topic: "Mate",
        duration: "Short",
        title: "Mate in 1",
        headline: "Mate-in-one test",
        note: "An instant checkmate pattern for sharpening board vision."
      },
      {
        id: "zO4LFNqzZyQ",
        topic: "Puzzle",
        duration: "Short",
        title: "The Final Blow",
        headline: "Final blow tactic",
        note: "Find the move that turns pressure into a decisive finish."
      },
      {
        id: "2J_Q6eA-WzY",
        topic: "Opening",
        duration: "Short",
        title: "Trap to Destroy the Queen's Opening",
        headline: "Queen's opening trap",
        note: "An advanced trap idea against an early queen-side setup."
      },
      {
        id: "jwER-v5Q1-M",
        topic: "Puzzle",
        duration: "Short",
        title: "The Hardest Easy Chess Puzzle",
        headline: "Hard easy puzzle",
        note: "A tricky-looking puzzle where the simple forcing move matters."
      },
      {
        id: "UQiZzPIsljE",
        topic: "Mate",
        duration: "Short",
        title: "White Sacrifices Everything for Mate",
        headline: "Sacrifice for mate",
        note: "An attacking lesson in giving material back only when the line is forced."
      },
      {
        id: "OlPnnnuPuDk",
        topic: "Puzzle",
        duration: "Short",
        title: "Do Not Play the Obvious Move",
        headline: "Avoid the obvious move",
        note: "A calculation puzzle that rewards checking the candidate moves first."
      }
    ];

    const shortLevelGroups = [
      {
        title: "Beginner Shorts",
        tag: "Start here",
        description: "Quick mates, easy openings, simple traps, and first puzzle wins.",
        ids: [
          "Vnblc4jfJHU", "8Vuwv-aEEXQ", "Kor7ai1q6Vk", "QQ69f80QxHA",
          "iTR4OBr13bY", "mbZIjNKlxuY", "qJHUh9h-Q84", "f_UqFFwi_rs",
          "OxRWuF0NPyM", "n05fNUA6PQ4", "V09wOvcJJbM", "E2biHMcMNR0",
          "SaeOMqoC8Mw", "-OU3WJyraKQ", "PaZVLsojjG0", "f2xXL537e7I",
          "S1s6sqaaCdg", "xtV_qZ0kDXY", "CdZLO5Wbfyk", "RO8Glb42K2o",
          "O_8heoqCuFU", "9URyJG68wj4", "adHrqOu-kS4", "pv05RJ69R9s",
          "4xBgIx_Rr_Y", "Um4s2urqVJY", "UrUnUtbFP54", "VXJNTGv4F4o",
          "uFNTQAFjai8", "4E9drlZ0Vns", "Lltl5nQmiN8", "qQ1-0EJmQvg",
          "7lr9wWEvbcA", "u3NaExzBL6w", "5t9fziJGCcg", "n51jOpVhI-k",
          "wi-5TDLAN-o"
        ]
      },
      {
        title: "Intermediate Shorts",
        tag: "Build speed",
        description: "Tactics, opening traps, endgame saves, and sharper calculation reps.",
        ids: [
          "CbfkPbGrPgw", "OVsyDJ3hgKM", "s9sXXRgfozI",
          "_KAc128DlMY", "6EDYuq6WcRo", "y2tOtMiBL2w", "uZqud7iFPbs",
          "p29X57WBTrY", "ai8CRRO-Tzs", "9VFe8wHlB28", "AXRLarjbSgM",
          "n2ZtFqvoy0w", "I30wGxgXFv4", "dunOMb_XfOg", "AtgEFLJ7jVc",
          "y5UzupHULcc", "ylPIQFOqq88", "jPxusiHa0xw", "fuSH59tZPO0",
          "N_XDJ0woYHk", "eUiElJvLo6c", "yTpNnz3PVSo", "0vAozwpZAcI",
          "GahxuKy7kRc", "Rj0fu-k6eWA", "kEqoib0vLn8", "AbUagQAAPA4",
          "Bi3mCYm8t9k", "p0iwRDssQhI", "xyx-AEH18Zs", "baLYalPxhmI",
          "gAw6F-WaJaY", "kLbvupI26-A", "4b2hs1PUcww", "9XZqUGBWass",
          "Mdd1uSRzmZU", "U2KFhsWMEP4", "O7xcKga2hZk", "-SGMZEftNf0",
          "cN4Xpz5yHSQ"
        ]
      },
      {
        title: "Advanced Shorts",
        tag: "Sharper ideas",
        description: "Brilliant tactics, sacrifice lines, advanced traps, and endgame conversion.",
        ids: [
          "90uOYlG68bg", "fHtMC-EqYhs", "_RHaVTAYnTs", "1zw7V1o9K98",
          "jr3GYrJDnVg", "BSTiLz4Jfmc", "QNKgtULOamY", "cF8izlNwIIU",
          "BI24dtla0TU", "zuztuAIHvo4", "46f_wcofIPE", "B3Jl5kTwQqU",
          "w65DmISackc", "K28CuIQVB-U", "-UZPXzwt3QI", "BJThK1rAT-0",
          "cl_Ur0wQ6Og", "QCXGvgCQXjU", "6ohv0VmtZz4", "oSvOUXIwbxE",
          "zO4LFNqzZyQ", "2J_Q6eA-WzY", "jwER-v5Q1-M", "UQiZzPIsljE",
          "OlPnnnuPuDk"
        ]
      }
    ];

    const shortLessonStorageKey = "checkmateQuest.shortLessons.v1";

    function readShortLessonState() {
      const fallback = {
        completed: [],
        liked: [],
        bookmarked: [],
        lastVideoId: "",
        lastIndex: 0
      };

      try {
        return {
          ...fallback,
          ...JSON.parse(localStorage.getItem(shortLessonStorageKey) || "{}")
        };
      } catch {
        return fallback;
      }
    }

    function saveShortLessonState(state) {
      const toArray = (value) => value instanceof Set ? [...value] : Array.isArray(value) ? value : [];

      try {
        localStorage.setItem(shortLessonStorageKey, JSON.stringify({
          completed: toArray(state.completed),
          liked: toArray(state.liked),
          bookmarked: toArray(state.bookmarked),
          lastVideoId: state.lastVideoId || "",
          lastIndex: Number.isFinite(state.lastIndex) ? state.lastIndex : 0
        }));
      } catch {
        // Private browsing or file previews can block localStorage; the feed still works without persistence.
      }
    }

    function shortDifficultyFromLevel(level) {
      return (level || "Lesson").replace(/\s+Shorts$/i, "");
    }

    function shortCategoryTags(video) {
      const haystack = `${video.topic || ""} ${video.title || ""} ${video.headline || ""} ${video.note || ""}`.toLowerCase();
      const tags = [video.topic || "Lesson"];

      [
        [/opening|gambit|sicilian|london|queen|trap/, "Opening"],
        [/tactic|fork|pin|skewer|sacrifice|combo/, "Tactic"],
        [/mate|checkmate/, "Checkmate"],
        [/endgame|pawn race|promotion|rook end/, "Endgame"],
        [/defense|defence|king safety/, "Defense"],
        [/calculate|calculation|candidate/, "Calculation"],
        [/puzzle|find|spot/, "Puzzle"]
      ].forEach(([pattern, label]) => {
        if (pattern.test(haystack)) tags.push(label);
      });

      return [...new Set(tags)].slice(0, 3);
    }

    const puzzleStorageKey = "checkmateQuest.puzzles.v1";
    const puzzlePlanLevels = ["Beginner", "Intermediate", "Advanced"];
    const puzzlePatternPlans = ["Forks", "Pins", "Back-rank mates", "Checkmates"];
    const puzzlePlanOptions = ["all", "adaptive", ...puzzlePlanLevels, ...puzzlePatternPlans];
    const savedPuzzleState = readPuzzleState();
    let currentPuzzle = Math.max(0, Math.min(puzzles.length - 1, Number(savedPuzzleState.currentPuzzle) || 0));
    let activePuzzlePlan = puzzlePlanOptions.includes(savedPuzzleState.activePlan) ? savedPuzzleState.activePlan : "all";
    if (puzzlePlanLevels.includes(activePuzzlePlan) && puzzles[currentPuzzle]?.level !== activePuzzlePlan) {
      currentPuzzle = puzzles.findIndex((puzzle) => puzzle.level === activePuzzlePlan);
      if (currentPuzzle < 0) currentPuzzle = 0;
    }
    let activeAnswered = false;
    let puzzleGame = null;
    let selectedPuzzleSquare = "";
    let puzzleLegalMoves = [];
    let puzzleLastMove = null;
    let puzzleHintStep = 0;
    let puzzleStarted = false;
    let puzzleAnalyzeMode = false;
    let puzzleFlipped = false;
    let puzzleSoundOn = false;
    let puzzleMistakeCount = 0;
    let puzzleLineStep = 0;
    let puzzleStartAt = 0;
    let puzzleTimerId = 0;
    let streak = Math.max(0, Number(savedPuzzleState.streak) || 0);
    let puzzleXp = Math.max(0, Number(savedPuzzleState.xp) || 0);
    let bestPuzzleStreak = Math.max(streak, Number(savedPuzzleState.bestStreak) || 0);
    let puzzleAttempts = Math.max(0, Number(savedPuzzleState.attempts) || 0);
    let puzzleCorrect = Math.max(0, Number(savedPuzzleState.correct) || 0);
    let spacedReview = savedPuzzleState.spacedReview && typeof savedPuzzleState.spacedReview === "object" ? savedPuzzleState.spacedReview : null;
    let weeklyPuzzleXp = savedPuzzleState.weekly && typeof savedPuzzleState.weekly === "object" ? savedPuzzleState.weekly : {};
    let favoriteOpening = savedPuzzleState.favoriteOpening || "Italian Game";
    let gameStats = savedPuzzleState.gameStats && typeof savedPuzzleState.gameStats === "object" ? savedPuzzleState.gameStats : {};
    gameStats = {
      played: Math.max(0, Number(gameStats.played) || 0),
      wins: Math.max(0, Number(gameStats.wins) || 0),
      hanging: Math.max(0, Number(gameStats.hanging) || 0),
      moveQualityTotal: Math.max(0, Number(gameStats.moveQualityTotal) || 0),
      moveQualityMoves: Math.max(0, Number(gameStats.moveQualityMoves) || 0),
      cleanGames: Math.max(0, Number(gameStats.cleanGames) || 0),
      principleGames: Math.max(0, Number(gameStats.principleGames) || 0),
      endgameWins: Math.max(0, Number(gameStats.endgameWins) || 0)
    };
    const completedPathLessons = new Set(Array.isArray(savedPuzzleState.completedPathLessons) ? savedPuzzleState.completedPathLessons : []);
    let dailyHabit = savedPuzzleState.habit && typeof savedPuzzleState.habit === "object" ? savedPuzzleState.habit : {};
    dailyHabit = {
      streak: Math.max(0, Number(dailyHabit.streak) || 0),
      lastDate: dailyHabit.lastDate || "",
      rewardDate: dailyHabit.rewardDate || ""
    };
    if (dailyHabit.lastDate && dailyHabit.lastDate !== getTodayKey() && getDayDistance(dailyHabit.lastDate, getTodayKey()) > 1) {
      dailyHabit.streak = 0;
    }
    const solvedPuzzles = new Set((savedPuzzleState.solved || []).map(Number).filter((index) => index >= 0 && index < puzzles.length));
    let currentAdventure = 0;
    let selectedAdventureSquare = "";
    let adventureBoardState = [];
    const bookLevels = ["Beginner", "Intermediate", "Advanced"];
    const bookLevelNotes = {
      Beginner: "Start here for rules, board confidence, simple mates, and first strategy habits.",
      Intermediate: "Use these after the rules feel natural and you want better plans.",
      Advanced: "Deep classics for positional thinking, structure, and serious review."
    };
    const bookCategories = ["Openings", "Middlegame", "Endgame", "Tactics", "Strategy", "Biographies"];
    const bookReaderStorageKey = "checkmateQuest.bookReader.v1";
    const customBooksStorageKey = "checkmateQuest.localBooks.v1";
    const dailyTrainingStorageKey = "checkmateQuest.dailyTraining.v1";
    const gentleStartStorageKey = "checkmateQuest.gentleStart.v1";
    const learnerPrefsStorageKey = "checkmateQuest.preferences.v1";
    let activeBookLevel = "all";
    let activeBookCategory = "all";
    let activeReaderBookId = "";
    let activeReaderChapter = 0;
    let readerTheme = "light";
    let readerFontScale = 1.08;

    function buildHeroBoard() {
      const board = document.getElementById("heroBoard");
      heroPieces.forEach((piece, index) => {
        const square = document.createElement("span");
        const row = Math.floor(index / 8);
        const col = index % 8;
        square.className = `hero-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;
        const colorClass = pieceColorClass(piece);
        if (colorClass) square.classList.add(colorClass);
        square.textContent = piece;
        board.appendChild(square);
      });
    }

    function fenToSquares(fen) {
      const rows = fen.split("/");
      return rows.flatMap((row) => {
        const squares = [];
        [...row].forEach((char) => {
          const empty = Number(char);
          if (Number.isInteger(empty) && empty > 0) {
            for (let i = 0; i < empty; i += 1) squares.push("");
          } else {
            squares.push(pieceMap[char] || "");
          }
        });
        return squares;
      });
    }

    function squareName(index) {
      const files = ["a", "b", "c", "d", "e", "f", "g", "h"];
      const row = Math.floor(index / 8);
      const col = index % 8;
      return `${files[col]}${8 - row}`;
    }

    function squareToIndex(square) {
      const files = ["a", "b", "c", "d", "e", "f", "g", "h"];
      const file = files.indexOf(square[0]);
      const rank = Number(square[1]);
      return (8 - rank) * 8 + file;
    }

    function renderAdventureMissionList() {
      const list = document.getElementById("adventureMissionList");
      list.innerHTML = "";

      adventureMissions.forEach((mission, index) => {
        const button = document.createElement("button");
        button.type = "button";
        button.className = "mission-button";
        button.textContent = mission.short;
        button.setAttribute("aria-pressed", String(index === currentAdventure));
        button.addEventListener("click", () => {
          currentAdventure = index;
          renderAdventureMission();
        });
        list.appendChild(button);
      });
    }

    function renderAdventureBoard() {
      const mission = adventureMissions[currentAdventure];
      const board = document.getElementById("adventureBoard");
      board.innerHTML = "";

      adventureBoardState.forEach((piece, index) => {
        const row = Math.floor(index / 8);
        const col = index % 8;
        const name = squareName(index);
        const square = document.createElement("button");
        square.type = "button";
        square.className = `adventure-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;

        const colorClass = pieceColorClass(piece);
        if (colorClass) square.classList.add(colorClass);
        if (piece && name === mission.from) square.classList.add("source-piece");
        if (name === selectedAdventureSquare) square.classList.add("selected");
        if (mission.targets.includes(name)) square.classList.add("legal-target");

        square.textContent = piece;
        square.setAttribute("aria-label", `${name}${piece ? ` ${piece}` : ""}`);
        square.addEventListener("click", () => handleAdventureClick(name));
        board.appendChild(square);
      });
    }

    function renderAdventureMission() {
      const mission = adventureMissions[currentAdventure];
      selectedAdventureSquare = "";
      adventureBoardState = fenToSquares(mission.fen);

      document.getElementById("adventureRole").textContent = mission.role;
      document.getElementById("adventureMove").textContent = "White to move";
      document.getElementById("adventurePlayTitle").textContent = mission.title;
      document.getElementById("adventureTask").textContent = mission.task;
      document.getElementById("adventureTip").textContent = mission.tip;
      document.getElementById("adventureFeedback").textContent = "Select the highlighted character piece, then choose the glowing target square.";

      renderAdventureMissionList();
      renderAdventureBoard();
    }

    function handleAdventureClick(name) {
      const mission = adventureMissions[currentAdventure];
      const fromIndex = squareToIndex(mission.from);
      const toIndex = squareToIndex(mission.to);
      const clickedPiece = adventureBoardState[squareToIndex(name)];

      if (!selectedAdventureSquare) {
        if (name === mission.from && clickedPiece) {
          selectedAdventureSquare = name;
          document.getElementById("adventureFeedback").textContent = `Good. Now send the piece to ${mission.to}.`;
        } else {
          document.getElementById("adventureFeedback").textContent = `Start with the character on ${mission.from}.`;
        }
        renderAdventureBoard();
        return;
      }

      if (name === selectedAdventureSquare) {
        selectedAdventureSquare = "";
        document.getElementById("adventureFeedback").textContent = "Piece deselected. Choose the character again when ready.";
        renderAdventureBoard();
        return;
      }

      if (name === mission.to) {
        adventureBoardState[toIndex] = adventureBoardState[fromIndex];
        adventureBoardState[fromIndex] = "";
        selectedAdventureSquare = "";
        document.getElementById("adventureFeedback").textContent = mission.success;
        renderAdventureBoard();
        return;
      }

      document.getElementById("adventureFeedback").textContent = `That is not this mission's square. Try ${mission.to}.`;
    }

    function renderMiniBoards() {
      document.querySelectorAll(".mini-board").forEach((board) => {
        const squares = fenToSquares(board.dataset.fen);
        board.innerHTML = "";
        squares.forEach((piece, index) => {
          const row = Math.floor(index / 8);
          const col = index % 8;
          const square = document.createElement("span");
          square.className = `mini-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;
          const colorClass = pieceColorClass(piece);
          if (colorClass) square.classList.add(colorClass);
          square.textContent = piece;
          board.appendChild(square);
        });
      });
    }

    function getPathLessonId(card, index) {
      const title = card.querySelector("h3")?.textContent || `Lesson ${index + 1}`;
      return title.toLowerCase().replace(/[^a-z0-9]+/g, "-").replace(/^-+|-+$/g, "");
    }

    function getActiveLessonPanel() {
      return [...document.querySelectorAll("#paths .lesson-grid")]
        .find((panel) => !panel.classList.contains("hidden")) || document.getElementById("beginner");
    }

    function updateLessonJourney() {
      const journey = document.getElementById("chessJourney");
      const panel = getActiveLessonPanel();
      if (!journey || !panel) return;

      const cards = [...panel.querySelectorAll(".lesson-card")];
      const firstOpen = cards.findIndex((card) => !completedPathLessons.has(card.dataset.lessonId));
      const currentIndex = firstOpen < 0 ? cards.length : firstOpen;
      const steps = document.createElement("div");
      const title = document.createElement("h3");

      journey.innerHTML = "";
      title.textContent = "Chess Journey";
      steps.className = "journey-steps";

      cards.forEach((card, index) => {
        const id = card.dataset.lessonId;
        const complete = completedPathLessons.has(id);
        const locked = !complete && index > currentIndex;
        const current = !complete && index === currentIndex;
        const step = document.createElement("button");
        const done = card.querySelector("[data-lesson-done]");
        const action = card.querySelector("[data-lesson-action]");

        card.classList.toggle("is-locked", locked);
        card.setAttribute("aria-disabled", String(locked));
        if (done) {
          done.disabled = locked;
          done.textContent = complete ? "Celebrated" : "Celebrate done";
        }
        if (action) {
          if (locked) action.removeAttribute("href");
          else action.href = action.dataset.href || "#puzzles";
          action.setAttribute("aria-disabled", String(locked));
        }

        step.type = "button";
        step.className = `journey-step${complete ? " is-complete" : ""}${current ? " is-current" : ""}${locked ? " is-locked" : ""}`;
        step.disabled = locked;
        step.textContent = `${complete ? "\u2611" : locked ? "\uD83D\uDD12" : "\u25A1"} Lesson ${index + 1}`;
        step.addEventListener("click", () => card.scrollIntoView({ behavior: "smooth", block: "center" }));
        steps.appendChild(step);
      });

      journey.append(title, steps);
    }

    function setupLessonFlow() {
      document.querySelectorAll("#paths .lesson-card").forEach((card, index) => {
        const title = card.querySelector("h3")?.textContent || `Lesson ${index + 1}`;
        const isMission = title.startsWith("Mission");
        const id = getPathLessonId(card, index);
        card.dataset.lessonId = id;

        if (!card.querySelector(".lesson-lock-note")) {
          const lockNote = document.createElement("p");
          lockNote.className = "lesson-lock-note";
          lockNote.textContent = "Locked. Celebrate the previous lesson to unlock this step.";
          card.appendChild(lockNote);
        }

        if (card.querySelector(".lesson-card-footer")) return;

        const footer = document.createElement("div");
        const time = document.createElement("span");
        const done = document.createElement("button");
        const action = document.createElement("a");

        footer.className = "lesson-card-footer";
        time.className = "lesson-time";
        time.textContent = isMission ? "2-3 min mission" : "2-3 min lesson";
        done.type = "button";
        done.className = "button secondary";
        done.dataset.lessonDone = id;
        done.textContent = completedPathLessons.has(id) ? "Celebrated" : "Celebrate done";
        done.addEventListener("click", () => {
          if (card.classList.contains("is-locked")) return;
          if (completedPathLessons.has(id)) return;
          completedPathLessons.add(id);
          const xpResult = addPuzzleXp(50);
          savePuzzleState();
          renderBeginnerProgress();
          updateLessonJourney();
          showCelebration("\uD83C\uDF89 Great Job!", "+50 XP", xpResult.levelUp ? "New Badge Unlocked!" : "Lesson complete!");
        });
        action.className = "button secondary";
        action.href = "#puzzles";
        action.dataset.href = "#puzzles";
        action.dataset.lessonAction = id;
        action.textContent = isMission ? "Try mission puzzle" : "Try one puzzle";
        footer.append(time, done, action);
        card.appendChild(footer);
      });
      updateLessonJourney();
    }

    function setupOpeningFavorites() {
      document.querySelectorAll(".opening-card").forEach((card) => {
        if (card.querySelector("[data-favorite-opening]")) return;
        const title = card.querySelector("h3")?.textContent || "Italian Game";
        const button = document.createElement("button");
        button.type = "button";
        button.className = "button secondary";
        button.dataset.favoriteOpening = title;
        button.textContent = favoriteOpening === title ? "Favorite opening" : "Set favorite";
        button.addEventListener("click", () => {
          favoriteOpening = title;
          document.querySelectorAll("[data-favorite-opening]").forEach((item) => {
            item.textContent = item.dataset.favoriteOpening === favoriteOpening ? "Favorite opening" : "Set favorite";
          });
          savePuzzleState();
          renderBeginnerProgress();
        });
        card.querySelector(".opening-body")?.appendChild(button);
      });
    }

    function getPuzzleAccuracy(fallback = 100) {
      return puzzleCorrect + puzzleAttempts ? Math.round((puzzleCorrect / (puzzleCorrect + puzzleAttempts)) * 100) : fallback;
    }

    function getAdaptivePuzzleLevel() {
      const accuracy = getPuzzleAccuracy(0);
      if (accuracy >= 90 && solvedPuzzles.size >= 8) return "Advanced";
      if (accuracy >= 70 && solvedPuzzles.size >= 3) return "Intermediate";
      return "Beginner";
    }

    function getPuzzlePattern(puzzle) {
      const text = `${puzzle.title} ${puzzle.prompt} ${puzzle.hint}`.toLowerCase();
      if (text.includes("fork")) return "Forks";
      if (text.includes("pin")) return "Pins";
      if (text.includes("skewer")) return "Skewers";
      if (text.includes("defender")) return "Removing the defender";
      if (text.includes("back-rank") || text.includes("back rank")) return "Back-rank mates";
      if (text.includes("mate")) return "Checkmates";
      if (text.includes("bishop")) return "Bishop vision";
      return "Tactics";
    }

    function addDaysKey(days) {
      const date = new Date(`${getTodayKey()}T00:00:00`);
      date.setDate(date.getDate() + days);
      return date.toISOString().slice(0, 10);
    }

    function scheduleSpacedReview(wasCorrect) {
      const label = getPuzzlePattern(puzzles[currentPuzzle]);
      if (wasCorrect && spacedReview?.label !== label) return;
      const interval = wasCorrect ? Math.min(Math.max(2, Number(spacedReview?.interval) || 2) * 2, 7) : 1;
      spacedReview = { label, interval, due: addDaysKey(interval) };
    }

    function getActivePuzzleIndexes() {
      let level = activePuzzlePlan;
      if (activePuzzlePlan === "adaptive") level = getAdaptivePuzzleLevel();
      const patternPlan = puzzlePatternPlans.includes(activePuzzlePlan);
      let indexes = puzzles
        .map((puzzle, index) => activePuzzlePlan === "all" || puzzle.level === level || (patternPlan && getPuzzlePattern(puzzle) === activePuzzlePlan) ? index : -1)
        .filter((index) => index >= 0);
      if (activePuzzlePlan === "adaptive" && spacedReview?.due <= getTodayKey()) {
        const reviewIndexes = indexes.filter((index) => getPuzzlePattern(puzzles[index]) === spacedReview.label);
        if (reviewIndexes.length) indexes = reviewIndexes;
      }
      return indexes;
    }

    function getNextPuzzleIndex(direction = 1) {
      const indexes = getActivePuzzleIndexes();
      const currentPosition = Math.max(0, indexes.indexOf(currentPuzzle));
      if (!indexes.length) return 0;

      return indexes[(currentPosition + direction + indexes.length) % indexes.length];
    }

    function renderPuzzlePlanButtons() {
      document.querySelectorAll("[data-puzzle-plan]").forEach((button) => {
        button.setAttribute("aria-pressed", String(button.dataset.puzzlePlan === activePuzzlePlan));
      });
    }

    function setPuzzlePlan(plan) {
      activePuzzlePlan = puzzlePlanOptions.includes(plan) ? plan : "all";
      const indexes = getActivePuzzleIndexes();
      if (!indexes.includes(currentPuzzle)) {
        currentPuzzle = indexes.find((index) => !solvedPuzzles.has(index)) ?? indexes[0] ?? 0;
      }
      renderPuzzle();
    }

    function updatePuzzleStats() {
      const indexes = getActivePuzzleIndexes();
      const solvedInPlan = indexes.filter((index) => solvedPuzzles.has(index)).length;
      const total = indexes.length || puzzles.length;
      const currentPosition = Math.max(0, indexes.indexOf(currentPuzzle));

      document.getElementById("puzzleCounter").textContent = `${currentPosition + 1} / ${total}`;
      document.getElementById("puzzleSolved").textContent = activePuzzlePlan === "all" ? solvedPuzzles.size : solvedInPlan;
      document.getElementById("puzzleStreak").textContent = streak;
      document.getElementById("puzzleProgress").style.width = `${((activePuzzlePlan === "all" ? solvedPuzzles.size : solvedInPlan) / total) * 100}%`;
      renderPuzzlePlanButtons();
      renderBeginnerProgress();
      savePuzzleState();
    }

    function readPuzzleState() {
      const fallback = { activePlan: "all", currentPuzzle: 0, solved: [], streak: 0, xp: 0, bestStreak: 0, attempts: 0, correct: 0, weekly: {}, habit: {}, gameStats: {}, completedPathLessons: [], favoriteOpening: "Italian Game", spacedReview: null };
      const state = readJsonStorage(puzzleStorageKey, fallback);
      return state && typeof state === "object" ? { ...fallback, ...state } : fallback;
    }

    function savePuzzleState() {
      writeJsonStorage(puzzleStorageKey, {
        activePlan: activePuzzlePlan,
        currentPuzzle,
        solved: [...solvedPuzzles],
        streak,
        xp: puzzleXp,
        bestStreak: bestPuzzleStreak,
        attempts: puzzleAttempts,
        correct: puzzleCorrect,
        weekly: weeklyPuzzleXp,
        habit: dailyHabit,
        gameStats,
        completedPathLessons: [...completedPathLessons],
        favoriteOpening,
        spacedReview
      });
    }

    function showCelebration(title = "\uD83C\uDF89 Great Job!", xpText = "+50 XP", badgeText = "") {
      document.querySelector(".celebration-toast")?.remove();
      fireConfettiBurst();
      const toast = document.createElement("div");
      toast.className = "celebration-toast";
      toast.setAttribute("role", "status");
      toast.append(
        createBookText("strong", "", title),
        createBookText("span", "", xpText)
      );
      if (badgeText) toast.append(createBookText("span", "", badgeText));
      document.body.appendChild(toast);
      window.setTimeout(() => toast.remove(), 1700);
    }

    function addPuzzleXp(amount) {
      const today = getTodayKey();
      const beforeLevel = getLearnerLevel(puzzleXp).current[0];
      puzzleXp += amount;
      weeklyPuzzleXp[today] = (Number(weeklyPuzzleXp[today]) || 0) + amount;
      return { levelUp: getLearnerLevel(puzzleXp).current[0] !== beforeLevel };
    }

    function getDayDistance(fromDate, toDate) {
      const from = new Date(`${fromDate}T00:00:00`);
      const to = new Date(`${toDate}T00:00:00`);
      if (Number.isNaN(from.getTime()) || Number.isNaN(to.getTime())) return 999;
      return Math.round((to - from) / 86400000);
    }

    function completeDailyHabit() {
      const today = getTodayKey();
      if (dailyHabit.rewardDate === today) return false;

      const gap = dailyHabit.lastDate ? getDayDistance(dailyHabit.lastDate, today) : 999;
      dailyHabit.streak = gap === 1 ? dailyHabit.streak + 1 : 1;
      dailyHabit.lastDate = today;
      dailyHabit.rewardDate = today;
      addPuzzleXp(10);
      return true;
    }

    function getLearnerLevel(xp) {
      const levels = [
        ["Beginner", 0],
        ["Learner", 40],
        ["Student", 100],
        ["Tactician", 180],
        ["Strategist", 300],
        ["Master Apprentice", 450]
      ];
      const current = levels.reduce((best, level) => xp >= level[1] ? level : best, levels[0]);
      const next = levels.find((level) => level[1] > xp);
      return { current, next };
    }

    function getDailyChallengeName() {
      const puzzle = puzzles[getDailyPuzzleIndex()];
      const text = `${puzzle.title} ${puzzle.prompt}`.toLowerCase();
      if (text.includes("mate")) return "Win in 2 moves";
      if (text.includes("fork")) return "Spot the fork";
      if (text.includes("king") || text.includes("check")) return "Save the king";
      if (text.includes("pawn") || text.includes("endgame")) return "Endgame challenge";
      return "Today's Puzzle";
    }

    function getSolvedPuzzleCountByPattern(pattern) {
      return [...solvedPuzzles].filter((index) => getPuzzlePattern(puzzles[index]) === pattern).length;
    }

    function getMoveQualityScore() {
      return gameStats.moveQualityMoves ? Math.round(gameStats.moveQualityTotal / gameStats.moveQualityMoves) : 100;
    }

    function getHangingPerGame() {
      return gameStats.played ? gameStats.hanging / gameStats.played : 0;
    }

    function getWeeklySkillScores() {
      return [
        ["Tactics", getPuzzleAccuracy(0), "tactics"],
        ["Opening principles", gameStats.principleGames ? 82 : 45, "openings"],
        ["Endgames", gameStats.endgameWins ? 82 : 42, "endgame"],
        ["Board vision", Math.max(35, 90 - Math.round(getHangingPerGame() * 28)), "review"],
        ["Calculation", getMoveQualityScore(), "calculation"]
      ];
    }

    function getWeeklySkillAssessment() {
      return [...getWeeklySkillScores()].sort((a, b) => a[1] - b[1])[0];
    }

    function getGameUnlocks() {
      const level = getLearnerLevel(puzzleXp).current[0];
      return [
        `Avatar: ${puzzleXp >= 40 ? "Knight Rookie" : "Pawn Rookie"}`,
        `Theme: ${puzzleXp >= 100 ? "Neon Board" : "Wood Board"}`,
        `Badge: ${solvedPuzzles.size >= 5 ? "Puzzle Spark" : level}`
      ];
    }

    function getSingleCoachFocus() {
      const [skill, score, weaknessKey] = getWeeklySkillAssessment();
      const forks = getSolvedPuzzleCountByPattern("Forks");
      if (forks < 3) {
        return { skill: "Forks", weaknessKey: "tactics", practice: "spot three fork puzzles", related: "Spot the fork", href: "#puzzles" };
      }
      if (getHangingPerGame() > 0.8 || coachCurrentHanging > 0) {
        return { skill: "Board vision", weaknessKey: "review", practice: "check undefended pieces before every move", related: "Which piece is hanging?", href: "#puzzles" };
      }
      if (!gameStats.principleGames) {
        return { skill: "Opening principles", weaknessKey: "openings", practice: "center, minor pieces, castle, connect rooks", related: "Opening principle drill", href: "#openings" };
      }
      if (!gameStats.endgameWins && gameStats.wins > 0) {
        return { skill: "Endgames", weaknessKey: "endgame", practice: "king and rook or king and pawn basics", related: "Endgame challenge", href: "#videos" };
      }
      return { skill, weaknessKey, practice: `raise ${skill.toLowerCase()} above ${Math.max(60, score + 10)}%`, related: getDailyChallengeName(), href: weaknessKey === "openings" ? "#openings" : weaknessKey === "endgame" ? "#videos" : "#puzzles" };
    }

    function renderHomeDashboard() {
      const welcome = document.getElementById("homeWelcome");
      const recs = document.getElementById("homeRecommendations");
      const unlocks = document.getElementById("homeUnlocks");
      if (!welcome || !recs) return;

      const shortLessonsDone = readShortLessonState().completed.length;
      const lessonCount = completedPathLessons.size + shortLessonsDone;
      const level = getLearnerLevel(puzzleXp).current[0];
      const needsTactics = puzzleAttempts > puzzleCorrect;
      const completedToday = dailyHabit.rewardDate === getTodayKey();
      const nextLesson = Math.max(1, lessonCount + 1);
      const focus = getSingleCoachFocus();
      const recommendations = [
        [`Continue Lesson ${nextLesson}`, "#paths"],
        [completedToday ? "Continue Learning" : "Puzzle of the Day", "#puzzles"],
        [needsTactics ? "Fork Practice" : focus.related, needsTactics ? "#puzzles" : focus.href],
        ["Practice Mistakes", "#play"]
      ];

      welcome.textContent = lessonCount || puzzleXp ? "Welcome back!" : "Welcome! Start with one tiny win.";
      document.getElementById("homeStreak").textContent = `${dailyHabit.streak}-day streak`;
      document.getElementById("homeLevel").textContent = `Level: ${level}`;
      document.getElementById("homeXp").textContent = `${puzzleXp} XP`;
      document.getElementById("homeProgress").textContent = `${lessonCount} lessons done`;
      document.getElementById("homeInsight").textContent = needsTactics
        ? "You struggled with tactics recently. Try one quick pattern."
        : `Single focus today: ${focus.practice}.`;

      if (unlocks) unlocks.replaceChildren(...getGameUnlocks().map((item) => createBookText("span", "game-unlock", item)));
      recs.replaceChildren(...recommendations.map(([label, href]) => {
        const link = document.createElement("a");
        link.className = "button secondary";
        link.href = href;
        link.textContent = label;
        return link;
      }));
    }

    function renderBeginnerProgress() {
      const xpPill = document.getElementById("xpPill");
      const levelPill = document.getElementById("learnerLevelPill");
      const gamesPill = document.getElementById("gamesPlayedPill");
      const winRatePill = document.getElementById("winRatePill");
      const solvedPill = document.getElementById("puzzlesSolvedPill");
      const bestPill = document.getElementById("bestStreakPill");
      const dailyPill = document.getElementById("dailyChallengePill");
      const dailyStreakPill = document.getElementById("dailyStreakPill");
      const lessonPill = document.getElementById("lessonCompletePill");
      const openingPill = document.getElementById("favoriteOpeningPill");
      const accuracyPill = document.getElementById("puzzleAccuracyPill");
      const hangingPill = document.getElementById("hangingPiecesPill");
      const moveQualityPill = document.getElementById("moveQualityPill");
      const puzzleRatingPill = document.getElementById("puzzleRatingPill");
      const timePill = document.getElementById("timeManagementPill");
      const dailyReward = document.getElementById("dailyReward");
      const coach = document.getElementById("simpleCoach");
      const badges = document.getElementById("achievementBadges");
      const chart = document.getElementById("weeklyChart");
      if (!xpPill || !levelPill || !gamesPill || !winRatePill || !solvedPill || !bestPill || !dailyPill || !dailyStreakPill || !lessonPill || !openingPill || !accuracyPill || !dailyReward || !coach || !badges || !chart) return;

      const completedToday = dailyHabit.rewardDate === getTodayKey();
      const shortLessonsDone = readShortLessonState().completed.length;
      const lessonCount = completedPathLessons.size + shortLessonsDone;
      const accuracy = getPuzzleAccuracy(0);
      const winRate = gameStats.played ? Math.round((gameStats.wins / gameStats.played) * 100) : 0;
      const hangingPerGame = gameStats.played ? (gameStats.hanging / gameStats.played).toFixed(1) : "0";
      const moveQuality = getMoveQualityScore();
      const puzzleRating = 400 + (solvedPuzzles.size * 12) + (bestPuzzleStreak * 8) + Math.floor(puzzleXp / 10);
      const level = getLearnerLevel(puzzleXp);
      xpPill.textContent = `${puzzleXp} XP`;
      levelPill.textContent = `Level: ${level.current[0]}`;
      levelPill.title = level.next ? `${level.next[1] - puzzleXp} XP to ${level.next[0]}` : "Top learner title unlocked";
      gamesPill.textContent = `Games played ${gameStats.played}`;
      winRatePill.textContent = `Win rate ${winRate}%`;
      solvedPill.textContent = `Puzzles solved ${solvedPuzzles.size}`;
      bestPill.textContent = `Best streak ${bestPuzzleStreak}`;
      dailyPill.textContent = completedToday ? "Daily challenge done" : `Daily: ${getDailyChallengeName()}`;
      dailyStreakPill.textContent = `Current streak ${dailyHabit.streak}`;
      lessonPill.textContent = `Missions completed ${lessonCount}`;
      openingPill.textContent = `Favorite opening: ${favoriteOpening}`;
      accuracyPill.textContent = `Puzzle confidence ${accuracy}%`;
      if (hangingPill) hangingPill.textContent = `Hanging pieces/game ${hangingPerGame}`;
      if (moveQualityPill) moveQualityPill.textContent = `Move quality ${moveQuality}%`;
      if (puzzleRatingPill) puzzleRatingPill.textContent = `Puzzle rating ${puzzleRating}`;
      if (timePill) timePill.textContent = `Time: ${moveQuality >= 75 ? "steady" : "slow scan"}`;
      dailyReward.textContent = completedToday ? "Reward unlocked: +10 XP. Come back tomorrow for the next spark." : "Reward locked: finish today's puzzle for +10 XP.";
      coach.textContent = puzzleAttempts
        ? `Simple AI coach: You're getting better every day. ${activePuzzlePlan === "adaptive" ? `Adaptive is giving you ${getAdaptivePuzzleLevel()} puzzles. ` : ""}One helpful idea: ${puzzles[currentPuzzle].hint}`
        : "Simple AI coach: You're getting better every day. Try one move.";

      const achievements = [
        ["First Win", gameStats.wins > 0],
        ["Puzzle Solver", solvedPuzzles.size > 0],
        ["7-Day Streak", dailyHabit.streak >= 7],
        ["Fork Spotter", getSolvedPuzzleCountByPattern("Forks") >= 3],
        ["Checkmate Artist", solvedPuzzles.size >= 5],
        ["Fast Thinker", bestPuzzleStreak >= 3],
        ["No Hanging Pieces", gameStats.cleanGames > 0],
        ["Opening Principles", gameStats.principleGames > 0],
        ["Endgame Winner", gameStats.endgameWins > 0]
      ];
      badges.replaceChildren(...achievements.map(([label, unlocked]) => {
        const badge = createBookText("span", `achievement-badge${unlocked ? " unlocked" : ""}`, label);
        badge.setAttribute("aria-label", `${label} ${unlocked ? "unlocked" : "locked"}`);
        return badge;
      }));

      const days = [...Array(7)].map((_, offset) => {
        const date = new Date();
        date.setDate(date.getDate() - (6 - offset));
        const key = `${date.getFullYear()}-${String(date.getMonth() + 1).padStart(2, "0")}-${String(date.getDate()).padStart(2, "0")}`;
        return [key, date.toLocaleDateString(undefined, { weekday: "short" })];
      });
      const max = Math.max(10, ...days.map(([key]) => Number(weeklyPuzzleXp[key]) || 0));
      chart.replaceChildren(...days.map(([key, label]) => {
        const value = Number(weeklyPuzzleXp[key]) || 0;
        const bar = document.createElement("div");
        const fill = document.createElement("span");
        bar.className = "week-bar";
        fill.style.height = `${Math.max(8, (value / max) * 58)}px`;
        bar.append(fill, document.createTextNode(label));
        bar.title = `${label}: ${value} XP`;
        return bar;
      }));
      renderHomeDashboard();
    }

    function fireConfettiBurst() {
      const burst = document.createElement("div");
      burst.className = "confetti-burst";
      const colors = ["#7fa650", "#e7b65d", "#6fa8dc", "#f0d9b5"];
      for (let index = 0; index < 28; index += 1) {
        const piece = document.createElement("span");
        piece.className = "confetti-piece";
        piece.style.left = `${Math.random() * 100}%`;
        piece.style.background = colors[index % colors.length];
        piece.style.animationDelay = `${Math.random() * 140}ms`;
        burst.appendChild(piece);
      }
      document.body.appendChild(burst);
      window.setTimeout(() => burst.remove(), 1200);
    }

    function getDailyPuzzleIndex() {
      const today = new Date();
      const key = Date.UTC(today.getFullYear(), today.getMonth(), today.getDate());
      return Math.floor(key / 86400000) % puzzles.length;
    }

    function renderDailyPuzzleMeta() {
      const badge = document.getElementById("dailyPuzzleBadge");
      if (!badge) return;

      badge.textContent = currentPuzzle === getDailyPuzzleIndex() ? getDailyChallengeName() : "Practice puzzle";
    }

    function getPuzzleSideColor(puzzle) {
      return puzzle.side.toLowerCase().includes("black") ? "b" : "w";
    }

    function getPuzzleFen(puzzle) {
      return `${puzzle.fen} ${getPuzzleSideColor(puzzle)} - - 0 1`;
    }

    function cleanPuzzleSan(move) {
      return String(move || "").replace(/[?!+#]/g, "");
    }

    function getPuzzleLine(puzzle = puzzles[currentPuzzle]) {
      const correct = puzzle.answers.find((answer) => answer.correct);
      return Array.isArray(puzzle.line) && puzzle.line.length ? puzzle.line : [correct?.move].filter(Boolean);
    }

    function findPuzzleSanMove(san) {
      const expected = cleanPuzzleSan(san);
      return puzzleGame?.moves({ verbose: true }).find((move) => cleanPuzzleSan(move.san) === expected) || null;
    }

    function playPuzzleSan(san) {
      const move = findPuzzleSanMove(san);
      if (!move) return null;
      const played = puzzleGame.move(toCoachMoveInput(move));
      puzzleLastMove = played;
      selectedPuzzleSquare = "";
      puzzleLegalMoves = [];
      return played;
    }

    function autoPlayPuzzleReply() {
      const line = getPuzzleLine();
      const puzzleSide = getPuzzleSideColor(puzzles[currentPuzzle]);
      if (puzzleLineStep >= line.length || puzzleGame?.turn() === puzzleSide) return null;
      const reply = playPuzzleSan(line[puzzleLineStep]);
      if (reply) puzzleLineStep += 1;
      return reply;
    }

    function resetPuzzleGame() {
      selectedPuzzleSquare = "";
      puzzleLegalMoves = [];
      puzzleLastMove = null;
      puzzleLineStep = 0;
      if (!CoachChess) {
        puzzleGame = null;
        return;
      }

      try {
        puzzleGame = new CoachChess(getPuzzleFen(puzzles[currentPuzzle]));
      } catch {
        puzzleGame = null;
      }
    }

    function getPuzzleSquares() {
      const flipped = (getPuzzleSideColor(puzzles[currentPuzzle]) === "b") !== puzzleFlipped;
      const files = flipped ? ["h", "g", "f", "e", "d", "c", "b", "a"] : ["a", "b", "c", "d", "e", "f", "g", "h"];
      const ranks = flipped ? ["1", "2", "3", "4", "5", "6", "7", "8"] : ["8", "7", "6", "5", "4", "3", "2", "1"];
      return ranks.flatMap((rank) => files.map((file) => `${file}${rank}`));
    }

    function findPuzzleKing(color) {
      return getPuzzleSquares().find((square) => {
        const piece = puzzleGame?.get(square);
        return piece && piece.type === "k" && piece.color === color;
      }) || "";
    }

    function getSquareCoords(square) {
      return { file: square.charCodeAt(0) - 97, rank: Number(square[1]) - 1 };
    }

    function toSquare(file, rank) {
      return file >= 0 && file < 8 && rank >= 0 && rank < 8 ? `${String.fromCharCode(97 + file)}${rank + 1}` : "";
    }

    function getRaySquares(square, directions) {
      const { file, rank } = getSquareCoords(square);
      const squares = [];
      directions.forEach(([df, dr]) => {
        let nextFile = file + df;
        let nextRank = rank + dr;
        while (toSquare(nextFile, nextRank)) {
          const next = toSquare(nextFile, nextRank);
          squares.push(next);
          if (puzzleGame?.get(next)) break;
          nextFile += df;
          nextRank += dr;
        }
      });
      return squares;
    }

    function getPseudoAttacks(square, piece) {
      const { file, rank } = getSquareCoords(square);
      const colorStep = piece.color === "w" ? 1 : -1;
      const jump = (pairs) => pairs.map(([df, dr]) => toSquare(file + df, rank + dr)).filter(Boolean);
      if (piece.type === "p") return jump([[-1, colorStep], [1, colorStep]]);
      if (piece.type === "n") return jump([[1, 2], [2, 1], [2, -1], [1, -2], [-1, -2], [-2, -1], [-2, 1], [-1, 2]]);
      if (piece.type === "b") return getRaySquares(square, [[1, 1], [1, -1], [-1, 1], [-1, -1]]);
      if (piece.type === "r") return getRaySquares(square, [[1, 0], [-1, 0], [0, 1], [0, -1]]);
      if (piece.type === "q") return getRaySquares(square, [[1, 1], [1, -1], [-1, 1], [-1, -1], [1, 0], [-1, 0], [0, 1], [0, -1]]);
      if (piece.type === "k") return jump([[1, 1], [1, 0], [1, -1], [0, 1], [0, -1], [-1, 1], [-1, 0], [-1, -1]]);
      return [];
    }

    function countAttackers(target, color) {
      if (!puzzleGame) return 0;
      return getPuzzleSquares().filter((square) => {
        const piece = puzzleGame.get(square);
        return piece && piece.color === color && getPseudoAttacks(square, piece).includes(target);
      }).length;
    }

    function getBoardVisionDrill() {
      const side = getPuzzleSideColor(puzzles[currentPuzzle]);
      const enemy = side === "w" ? "b" : "w";
      const pieceNames = { p: "pawn", n: "knight", b: "bishop", r: "rook", q: "queen", k: "king" };
      if (!puzzleGame) return { question: "Which piece is hanging?", answer: "Loading the board. Try again in a moment." };

      if (currentPuzzle % 4 === 1) {
        const bishopSquare = getPuzzleSquares().find((square) => puzzleGame.get(square)?.type === "b") || "";
        const bishop = bishopSquare ? puzzleGame.get(bishopSquare) : null;
        const squares = bishop ? getPseudoAttacks(bishopSquare, bishop).slice(0, 8).join(", ") : "no bishop on this board";
        return { question: "What squares does a bishop control?", answer: bishop ? `The ${bishop.color === "w" ? "white" : "black"} bishop on ${bishopSquare} controls: ${squares}.` : `This position has ${squares}.` };
      }

      if (currentPuzzle % 4 === 2) {
        const king = findPuzzleKing(side);
        const attackers = king ? countAttackers(king, enemy) : 0;
        return { question: "Is your king safe?", answer: king ? `${king} has ${attackers} direct attacker${attackers === 1 ? "" : "s"}. ${attackers ? "Answer the threat first." : "No immediate attacker. Now scan loose pieces."}` : "Find your king first, then count direct attackers." };
      }

      if (currentPuzzle % 4 === 3) {
        const target = puzzles[currentPuzzle].targets[0] || "the target square";
        return { question: `Count attackers and defenders on ${target}.`, answer: `${side === "w" ? "White" : "Black"} attacks ${target} with ${countAttackers(target, side)} piece(s). The defender has ${countAttackers(target, enemy)} piece(s) guarding it.` };
      }

      const hanging = getPuzzleSquares().map((square) => {
        const piece = puzzleGame.get(square);
        if (!piece || piece.type === "k") return null;
        const attackers = countAttackers(square, piece.color === "w" ? "b" : "w");
        const defenders = countAttackers(square, piece.color);
        return attackers > defenders ? { square, piece, attackers, defenders } : null;
      }).find(Boolean);
      return hanging
        ? { question: "Which piece is hanging?", answer: `The ${hanging.piece.color === "w" ? "white" : "black"} ${pieceNames[hanging.piece.type]} on ${hanging.square} has ${hanging.attackers} attacker(s) and ${hanging.defenders} defender(s).` }
        : { question: "Which piece is hanging?", answer: "No clear hanging piece. Good scan. Now look for checks, captures, and threats." };
    }

    function renderBoardVisionDrill() {
      const drill = getBoardVisionDrill();
      const question = document.getElementById("visionQuestion");
      const answer = document.getElementById("visionAnswerText");
      const button = document.getElementById("visionAnswer");
      if (!question || !answer || !button) return;
      question.textContent = drill.question;
      answer.textContent = drill.answer;
      answer.hidden = true;
      button.textContent = "Show Answer";
    }

    function getPuzzleRating(puzzle = puzzles[currentPuzzle]) {
      const base = { Beginner: 650, Intermediate: 1250, Advanced: 1750 }[puzzle.level] || 900;
      return base + (getPuzzlePattern(puzzle).length % 5) * 30;
    }

    function getPuzzleTags(puzzle = puzzles[currentPuzzle]) {
      const text = `${puzzle.title} ${puzzle.prompt} ${puzzle.hint}`.toLowerCase();
      const tags = [getPuzzlePattern(puzzle)];
      [
        [/mate|checkmate/, "Mate"],
        [/back-rank|back rank/, "Back rank"],
        [/fork/, "Fork"],
        [/pin/, "Pin"],
        [/defender|deflect/, "Deflection"],
        [/pawn|endgame|promotion/, "Endgame"],
        [/quiet/, "Quiet move"],
        [/sacrifice/, "Sacrifice"]
      ].forEach(([pattern, label]) => {
        if (pattern.test(text)) tags.push(label);
      });
      return [...new Set(tags)].slice(0, 4);
    }

    function formatPuzzleTime(ms) {
      const seconds = Math.max(0, Math.floor(ms / 1000));
      return `${String(Math.floor(seconds / 60)).padStart(2, "0")}:${String(seconds % 60).padStart(2, "0")}`;
    }

    function updatePuzzleClock() {
      const clock = document.getElementById("puzzleClock");
      if (clock) clock.textContent = formatPuzzleTime(puzzleStartAt ? Date.now() - puzzleStartAt : 0);
    }

    function stopPuzzleTimer() {
      window.clearInterval(puzzleTimerId);
      puzzleTimerId = 0;
      updatePuzzleClock();
    }

    function startPuzzleTimer() {
      puzzleStartAt = Date.now();
      stopPuzzleTimer();
      puzzleTimerId = window.setInterval(updatePuzzleClock, 500);
      updatePuzzleClock();
    }

    function playPuzzleTone(type) {
      if (!puzzleSoundOn || !window.AudioContext) return;
      const context = new AudioContext();
      const oscillator = context.createOscillator();
      const gain = context.createGain();
      oscillator.frequency.value = type === "correct" ? 660 : 180;
      gain.gain.value = 0.025;
      oscillator.connect(gain);
      gain.connect(context.destination);
      oscillator.start();
      window.setTimeout(() => {
        oscillator.stop();
        context.close();
      }, 110);
    }

    function flashPuzzleBoard(className) {
      const wrap = document.querySelector("#puzzleBoard")?.closest(".puzzle-board-wrap");
      if (!wrap) return;
      wrap.classList.remove("is-correct", "is-wrong");
      void wrap.offsetWidth;
      wrap.classList.add(className);
      window.setTimeout(() => wrap.classList.remove(className), 450);
    }

    function renderPuzzleDetails() {
      const puzzle = puzzles[currentPuzzle];
      const tags = getPuzzleTags(puzzle);
      const lineMoves = Math.ceil(getPuzzleLine(puzzle).length / 2);
      document.getElementById("puzzleRating").textContent = String(getPuzzleRating(puzzle));
      document.getElementById("puzzleEstimate").textContent = lineMoves > 1 ? `Mate in ${lineMoves}` : getPuzzleRating(puzzle) >= 1600 ? "~4 min" : getPuzzleRating(puzzle) >= 1200 ? "~2 min" : "~1 min";
      document.getElementById("puzzleMistakes").textContent = `${puzzleMistakeCount} mistake${puzzleMistakeCount === 1 ? "" : "s"}`;
      document.getElementById("puzzleTags").replaceChildren(...tags.map((tag) => createBookText("span", "", tag)));
    }

    function showPuzzleComplete() {
      const panel = document.getElementById("puzzleComplete");
      const summary = document.getElementById("puzzleCompleteSummary");
      const explanation = document.getElementById("puzzleExplanation");
      const tags = getPuzzleTags().join(", ");
      const accuracy = puzzleMistakeCount ? Math.max(20, 100 - puzzleMistakeCount * 25) : 100;
      stopPuzzleTimer();
      panel.hidden = false;
      summary.textContent = `Accuracy ${accuracy}%. Time ${document.getElementById("puzzleClock").textContent}. Rating ${getPuzzleRating()}. Themes: ${tags}. Solution: ${getPuzzleLine().join(" ")}`;
      explanation.textContent = `Why it works: ${puzzles[currentPuzzle].feedback}`;
    }

    function startPuzzle() {
      if (puzzleStarted && !activeAnswered) return;
      puzzleStarted = true;
      puzzleAnalyzeMode = false;
      activeAnswered = false;
      document.getElementById("puzzleComplete").hidden = true;
      document.getElementById("startPuzzle").textContent = "Solving";
      document.getElementById("feedback").textContent = "Find the best move. Use checks, captures, threats.";
      startPuzzleTimer();
      renderPuzzleBoard();
    }

    function finishPuzzleMove(move) {
      const puzzle = puzzles[currentPuzzle];
      const line = getPuzzleLine(puzzle);
      const expected = line[puzzleLineStep];
      const isCorrect = cleanPuzzleSan(move.san) === cleanPuzzleSan(expected);

      selectedPuzzleSquare = "";
      puzzleLegalMoves = [];
      puzzleLastMove = isCorrect ? move : null;

      if (isCorrect) {
        puzzleLineStep += 1;
        const reply = autoPlayPuzzleReply();
        flashPuzzleBoard("is-correct");
        playPuzzleTone("correct");
        if (puzzleLineStep >= line.length) {
          activeAnswered = true;
          const firstSolve = !solvedPuzzles.has(currentPuzzle);
          const habitReward = currentPuzzle === getDailyPuzzleIndex() && completeDailyHabit();
          if (firstSolve) {
            solvedPuzzles.add(currentPuzzle);
            streak += 1;
          }
          bestPuzzleStreak = Math.max(bestPuzzleStreak, streak);
          puzzleCorrect += 1;
          scheduleSpacedReview(true);
          const reward = firstSolve ? 15 : 5;
          const xpResult = addPuzzleXp(reward);
          document.getElementById("feedback").textContent = `Solved! +${reward}${habitReward ? " +10 daily reward" : ""} XP. ${puzzle.feedback}`;
          showPuzzleComplete();
          showCelebration("\uD83C\uDF89 Great Job!", `+${reward} XP`, xpResult.levelUp ? "New Badge Unlocked!" : "Puzzle solved!");
        } else {
          document.getElementById("feedback").textContent = `Good move: ${move.san}. ${reply ? `Coach reply: ${reply.san}. ` : ""}Keep following the line.`;
        }
      } else {
        puzzleGame.undo();
        streak = 0;
        puzzleAttempts += 1;
        puzzleMistakeCount += 1;
        scheduleSpacedReview(false);
        addPuzzleXp(2);
        document.getElementById("feedback").textContent = `Good idea! Here's an even stronger move. ${move.san} was legal. Tip: ${puzzle.hint}`;
        document.getElementById("puzzleMistakes").textContent = `${puzzleMistakeCount} mistake${puzzleMistakeCount === 1 ? "" : "s"}`;
        flashPuzzleBoard("is-wrong");
        playPuzzleTone("wrong");
      }

      updatePuzzleStats();
      renderPuzzleBoard();
    }

    function handlePuzzleSquare(square) {
      if (!puzzleGame || (!puzzleStarted && !puzzleAnalyzeMode) || (activeAnswered && !puzzleAnalyzeMode)) return;
      const piece = puzzleGame.get(square);

      if (selectedPuzzleSquare && square !== selectedPuzzleSquare) {
        const legalMoves = puzzleGame.moves({ square: selectedPuzzleSquare, verbose: true }).filter((move) => move.to === square);
        if (legalMoves.length) {
          const promotion = choosePromotion(legalMoves);
          const move = puzzleGame.move({ from: selectedPuzzleSquare, to: square, ...(promotion ? { promotion } : {}) });
          if (move) {
            if (puzzleAnalyzeMode) {
              puzzleLastMove = move;
              selectedPuzzleSquare = "";
              puzzleLegalMoves = [];
              document.getElementById("feedback").textContent = `Analyze mode: ${move.san} is legal. Explore the position freely.`;
              renderPuzzleBoard();
            } else {
              finishPuzzleMove(move);
            }
          }
          return;
        }
      }

      if (piece && piece.color === puzzleGame.turn()) {
        selectedPuzzleSquare = square;
        puzzleLegalMoves = puzzleGame.moves({ square, verbose: true });
        document.getElementById("feedback").textContent = `${puzzleLegalMoves.length} legal move${puzzleLegalMoves.length === 1 ? "" : "s"} highlighted. Find the forcing move.`;
      } else {
        selectedPuzzleSquare = "";
        puzzleLegalMoves = [];
        document.getElementById("feedback").textContent = "Pick a piece for the side to move first.";
      }
      renderPuzzleBoard();
    }

    function playPuzzleSolution() {
      if (!puzzleGame) return null;
      const line = getPuzzleLine();
      let played = null;
      while (puzzleLineStep < line.length) {
        played = playPuzzleSan(line[puzzleLineStep]);
        if (!played) break;
        puzzleLineStep += 1;
      }
      renderPuzzleBoard();
      return played;
    }

    function getPuzzleHintText(step) {
      const puzzle = puzzles[currentPuzzle];
      const correct = puzzle.answers.find((answer) => answer.correct);
      const text = `${puzzle.title} ${puzzle.prompt} ${puzzle.hint}`.toLowerCase();
      if (step === 1) {
        if (text.includes("fork")) return "Hint 1: Look for a piece attacking two targets.";
        if (text.includes("mate")) return "Hint 1: Look for a forcing check near the king.";
        if (text.includes("pawn") || text.includes("endgame")) return "Hint 1: Look for the move that changes the pawn race.";
        return "Hint 1: Start with checks, captures, and threats.";
      }
      if (step === 2) {
        if (text.includes("knight") || text.includes("fork")) return "Hint 2: Your knight has a fork.";
        return `Hint 2: ${puzzle.hint}`;
      }
      return `Hint 3: Solution line: ${getPuzzleLine().join(" ")}.`;
    }

    function revealPuzzleSolution() {
      if (activeAnswered) return;
      const puzzle = puzzles[currentPuzzle];
      const correct = puzzle.answers.find((answer) => answer.correct);
      const hint = document.getElementById("puzzleHint");
      puzzleHintStep = Math.max(puzzleHintStep, 3);
      hint.textContent = getPuzzleHintText(3);
      hint.classList.remove("hidden");
      document.getElementById("hintPuzzle").textContent = "Show Move";
      const played = playPuzzleSolution();
      activeAnswered = true;
      streak = 0;
      puzzleAttempts += 1;
      puzzleMistakeCount += 1;
      addPuzzleXp(1);
      scheduleSpacedReview(false);
      lockAnswers(null, false);
      document.getElementById("feedback").textContent = `Good idea to learn from the answer. +1 XP. Stronger move: ${played?.san || correct.move}. Tip: ${puzzle.hint}`;
      showPuzzleComplete();
      updatePuzzleStats();
      renderPuzzleBoard();
    }

    function showNextPuzzleHint() {
      if (activeAnswered) return;
      puzzleHintStep += 1;
      const hint = document.getElementById("puzzleHint");
      hint.textContent = getPuzzleHintText(puzzleHintStep);
      hint.classList.remove("hidden");
      document.getElementById("hintPuzzle").textContent = puzzleHintStep >= 2 ? "Show Move" : "Next Hint";
      if (puzzleHintStep >= 3) revealPuzzleSolution();
      else renderPuzzleBoard();
    }

    function renderPuzzleBoard() {
      const puzzle = puzzles[currentPuzzle];
      const board = document.getElementById("puzzleBoard");
      const legalByTarget = new Map(puzzleLegalMoves.map((move) => [move.to, move]));
      const lastSquares = puzzleLastMove ? [puzzleLastMove.from, puzzleLastMove.to] : [];
      const checkedKing = puzzleGame && callCoachRule(puzzleGame, "isCheck", "in_check") ? findPuzzleKing(puzzleGame.turn()) : "";
      const hintVisible = puzzleHintStep >= 3 || activeAnswered;

      board.innerHTML = "";
      if (!puzzleGame) {
        fenToSquares(puzzle.fen).forEach((piece, index) => {
          const row = Math.floor(index / 8);
          const col = index % 8;
          const square = document.createElement("span");
          square.className = `puzzle-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;
          const colorClass = pieceColorClass(piece);
          if (colorClass) square.classList.add(colorClass);
          square.textContent = piece;
          board.appendChild(square);
        });
        return;
      }

      getPuzzleSquares().forEach((name) => {
        const piece = puzzleGame.get(name);
        const legalMove = legalByTarget.get(name);
        const square = document.createElement("button");
        square.type = "button";
        square.className = `puzzle-square play-square ${isLightCoachSquare(name) ? "light" : "dark"}`;
        if (piece) square.classList.add(piece.color === "w" ? "white-piece" : "black-piece");
        if (name === selectedPuzzleSquare) square.classList.add("selected");
        if (legalMove) square.classList.add(legalMove.captured || legalMove.flags.includes("e") ? "capture" : "legal");
        if (lastSquares.includes(name)) square.classList.add("last-move");
        if (name === checkedKing) square.classList.add("in-check");
        if (hintVisible && puzzle.targets.includes(name)) square.classList.add("target");
        square.textContent = piece ? coachPieceSymbols[piece.color][piece.type] : "";
        square.setAttribute("aria-label", `${name}${piece ? ` ${piece.color === "w" ? "white" : "black"} ${piece.type}` : " empty"}`);
        square.draggable = Boolean(piece && piece.color === puzzleGame.turn() && (puzzleStarted || puzzleAnalyzeMode) && (!activeAnswered || puzzleAnalyzeMode));
        square.addEventListener("dragstart", (event) => {
          if (!square.draggable) return event.preventDefault();
          event.dataTransfer.setData("text/plain", name);
          square.classList.add("dragging");
        });
        square.addEventListener("dragend", () => square.classList.remove("dragging"));
        square.addEventListener("dragover", (event) => event.preventDefault());
        square.addEventListener("drop", (event) => {
          event.preventDefault();
          const from = event.dataTransfer.getData("text/plain");
          if (from) {
            selectedPuzzleSquare = from;
            handlePuzzleSquare(name);
          }
        });
        square.addEventListener("click", () => handlePuzzleSquare(name));
        board.appendChild(square);
      });
    }

    function lockAnswers(selectedButton, selectedWasCorrect) {
      const puzzle = puzzles[currentPuzzle];
      const answers = document.getElementById("answers");

      [...answers.children].forEach((child) => {
        child.disabled = true;
        const matching = puzzle.answers.find((item) => item.move === child.textContent);
        if (matching && matching.correct) child.classList.add("correct");
      });

      if (selectedButton && !selectedWasCorrect) {
        selectedButton.classList.add("wrong");
      }
    }

    function handleAnswer(answer, button) {
      if (activeAnswered) return;
      if (!puzzleStarted) startPuzzle();

      const puzzle = puzzles[currentPuzzle];
      activeAnswered = true;
      lockAnswers(button, answer.correct);

      if (answer.correct) {
        const firstSolve = !solvedPuzzles.has(currentPuzzle);
        if (!solvedPuzzles.has(currentPuzzle)) {
          solvedPuzzles.add(currentPuzzle);
          streak += 1;
        }
        bestPuzzleStreak = Math.max(bestPuzzleStreak, streak);
        puzzleCorrect += 1;
        scheduleSpacedReview(true);
        const reward = firstSolve ? 15 : 5;
        const xpResult = addPuzzleXp(reward);
        document.getElementById("feedback").textContent = `Great move! +${reward} XP. You improved because you found the idea: ${puzzle.feedback}`;
        flashPuzzleBoard("is-correct");
        playPuzzleTone("correct");
        showPuzzleComplete();
        showCelebration("\uD83C\uDF89 Great Job!", `+${reward} XP`, xpResult.levelUp ? "New Badge Unlocked!" : "Puzzle solved!");
      } else {
        puzzleAttempts += 1;
        streak = 0;
        puzzleMistakeCount += 1;
        scheduleSpacedReview(false);
        addPuzzleXp(2);
        document.getElementById("feedback").textContent = `Great Try! +2 XP for practicing. You improved because you checked a candidate move. Tip: ${puzzle.hint}`;
        document.getElementById("puzzleMistakes").textContent = `${puzzleMistakeCount} mistake${puzzleMistakeCount === 1 ? "" : "s"}`;
        flashPuzzleBoard("is-wrong");
        playPuzzleTone("wrong");
      }

      updatePuzzleStats();
    }

    function renderPuzzle() {
      const indexes = getActivePuzzleIndexes();
      if (indexes.length && !indexes.includes(currentPuzzle)) {
        currentPuzzle = indexes[0];
      }

      const puzzle = puzzles[currentPuzzle];
      const answers = document.getElementById("answers");
      const feedback = document.getElementById("feedback");
      const hint = document.getElementById("puzzleHint");

      activeAnswered = false;
      puzzleStarted = false;
      puzzleAnalyzeMode = false;
      puzzleMistakeCount = 0;
      puzzleStartAt = 0;
      puzzleHintStep = 0;
      stopPuzzleTimer();
      resetPuzzleGame();
      document.getElementById("puzzleLevel").textContent = activePuzzlePlan === "adaptive"
        ? `Adaptive: ${getAdaptivePuzzleLevel()}`
        : puzzlePatternPlans.includes(activePuzzlePlan) ? activePuzzlePlan : puzzle.level;
      document.getElementById("puzzleSide").textContent = puzzle.side;
      document.getElementById("puzzleTitle").textContent = puzzle.title;
      document.getElementById("puzzlePrompt").textContent = puzzle.prompt;
      document.getElementById("puzzleComplete").hidden = true;
      document.getElementById("startPuzzle").textContent = "Start Puzzle";
      document.getElementById("analyzePuzzle").setAttribute("aria-pressed", "false");
      hint.textContent = puzzle.hint;
      hint.classList.add("hidden");
      feedback.textContent = CoachChess ? "Press Start Puzzle when you are ready." : "Loading chess.js puzzle rules...";
      document.getElementById("hintPuzzle").disabled = false;
      document.getElementById("hintPuzzle").textContent = "Hint";
      document.getElementById("revealPuzzle").disabled = false;
      document.getElementById("revealPuzzle").textContent = getPuzzleLine(puzzle).length > 1 ? "View Solution" : "Show Move";
      renderPuzzleDetails();
      updatePuzzleStats();
      renderDailyPuzzleMeta();
      renderPuzzleBoard();
      renderBoardVisionDrill();

      answers.innerHTML = "";
      puzzle.answers.forEach((answer) => {
        const button = document.createElement("button");
        button.type = "button";
        button.className = "answer-button";
        button.textContent = answer.move;
        button.addEventListener("click", () => handleAnswer(answer, button));
        answers.appendChild(button);
      });
    }

    function retryPuzzle() {
      renderPuzzle();
      document.getElementById("feedback").textContent = "Retry from the original position. Look for the forcing idea.";
      startPuzzle();
    }

    function toggleAnalyzePuzzle() {
      if (!activeAnswered) return;
      puzzleAnalyzeMode = !puzzleAnalyzeMode;
      document.getElementById("analyzePuzzle").setAttribute("aria-pressed", String(puzzleAnalyzeMode));
      document.getElementById("feedback").textContent = puzzleAnalyzeMode
        ? "Analyze mode on: explore legal moves freely."
        : "Analyze mode off. Review the solution or go next.";
      renderPuzzleBoard();
    }

    function flipPuzzleBoard() {
      puzzleFlipped = !puzzleFlipped;
      renderPuzzleBoard();
    }

    function replayPuzzleSolution() {
      retryPuzzle();
      puzzleStarted = true;
      const played = playPuzzleSolution();
      activeAnswered = true;
      document.getElementById("feedback").textContent = `Replay: ${played?.san || "best move"}. ${puzzles[currentPuzzle].feedback}`;
      showPuzzleComplete();
      renderPuzzleBoard();
    }

    function togglePuzzleSound() {
      puzzleSoundOn = !puzzleSoundOn;
      const button = document.getElementById("soundPuzzle");
      button.textContent = puzzleSoundOn ? "Sound On" : "Sound Off";
      button.setAttribute("aria-pressed", String(puzzleSoundOn));
      playPuzzleTone("correct");
    }

    function renderCoordinates() {
      const coordinates = document.getElementById("coordinates");
      const files = ["a", "b", "c", "d", "e", "f", "g", "h"];
      const ranks = ["8", "7", "6", "5", "4", "3", "2", "1"];

      files.forEach((file, index) => {
        const marker = document.createElement("span");
        marker.textContent = file;
        marker.style.left = `${index * 12.5 + 1.5}%`;
        marker.style.bottom = "0.5%";
        coordinates.appendChild(marker);
      });

      ranks.forEach((rank, index) => {
        const marker = document.createElement("span");
        marker.textContent = rank;
        marker.style.top = `${index * 12.5 + 0.5}%`;
        marker.style.left = "1%";
        coordinates.appendChild(marker);
      });
    }

    const chessJsUrl = "https://cdn.jsdelivr.net/npm/chess.js@1.0.0/+esm";
    const coachPieceSymbols = {
      w: { k: "\u2654", q: "\u2655", r: "\u2656", b: "\u2657", n: "\u2658", p: "\u2659" },
      b: { k: "\u265A", q: "\u265B", r: "\u265C", b: "\u265D", n: "\u265E", p: "\u265F" }
    };
    const classicCoachPieceSymbols = JSON.parse(JSON.stringify(coachPieceSymbols));
    const letterCoachPieceSymbols = {
      w: { k: "K", q: "Q", r: "R", b: "B", n: "N", p: "P" },
      b: { k: "k", q: "q", r: "r", b: "b", n: "n", p: "p" }
    };
    const coachPieceValues = { p: 100, n: 320, b: 330, r: 500, q: 900, k: 0 };
    let CoachChess = null;
    let coachGame = null;
    let coachSelected = "";
    let coachLegalMoves = [];
    let coachLastMove = null;
    let coachDifficulty = "easy";
    let coachFlipped = false;
    let coachThinking = false;
    let coachDrawAgreed = false;
    let coachMessage = "You are White. Select a piece to see legal moves.";
    let coachMoveToken = 0;
    let coachThreatMode = false;
    let coachReplayFen = "";
    let coachMistakeNote = "";
    let coachWhyText = "Select or make a move, then ask why.";
    let coachGameRecorded = false;
    let coachReviewMoments = [];
    let coachCurrentHanging = 0;
    let chessRulesPromise = null;

    async function loadChessRules() {
      if (CoachChess) return CoachChess;
      chessRulesPromise ||= import(chessJsUrl).then((module) => module.Chess || module.default?.Chess || module.default);
      CoachChess = await chessRulesPromise;
      return CoachChess;
    }

    function callCoachRule(game, modernName, legacyName) {
      const modern = game && game[modernName];
      const legacy = game && game[legacyName];
      if (typeof modern === "function") return modern.call(game);
      if (typeof legacy === "function") return legacy.call(game);
      return false;
    }

    function isCoachGameOver() {
      return coachDrawAgreed || callCoachRule(coachGame, "isGameOver", "game_over");
    }

    function isCoachCheck() {
      return callCoachRule(coachGame, "isCheck", "in_check");
    }

    function toCoachMoveInput(move) {
      const input = { from: move.from, to: move.to };
      if (move.promotion) input.promotion = move.promotion;
      return input;
    }

    function getCoachSquares() {
      const files = coachFlipped ? ["h", "g", "f", "e", "d", "c", "b", "a"] : ["a", "b", "c", "d", "e", "f", "g", "h"];
      const ranks = coachFlipped ? ["1", "2", "3", "4", "5", "6", "7", "8"] : ["8", "7", "6", "5", "4", "3", "2", "1"];
      return ranks.flatMap((rank) => files.map((file) => `${file}${rank}`));
    }

    function isLightCoachSquare(square) {
      return (square.charCodeAt(0) - 97 + Number(square[1])) % 2 === 0;
    }

    function findCoachKing(color) {
      return getCoachSquares().find((square) => {
        const piece = coachGame.get(square);
        return piece && piece.type === "k" && piece.color === color;
      }) || "";
    }

    function getOneCoachSuggestion() {
      const whiteMoves = coachGame.history({ verbose: true }).filter((move) => move.color === "w");
      const movedQueenEarly = whiteMoves.slice(0, 4).some((move) => move.piece === "q");
      const knightMoves = whiteMoves.filter((move) => move.piece === "n").length;
      if (movedQueenEarly && knightMoves < 2) return "Next time, try developing your knights before moving the queen.";
      if (!whiteMoves.some((move) => move.flags.includes("k") || move.flags.includes("q"))) return "Next time, try castling before starting an attack.";
      return "Next time, ask what the coach threatens before you move.";
    }

    function getCoachThreatSquares() {
      if (!coachGame || !CoachChess) return new Set();
      const fenParts = coachGame.fen().split(" ");
      fenParts[1] = "b";
      try {
        const blackView = new CoachChess(fenParts.join(" "));
        return new Set(blackView.moves({ verbose: true })
          .filter((move) => coachGame.get(move.to)?.color === "w" || move.san.includes("+"))
          .map((move) => move.to));
      } catch {
        return new Set();
      }
    }

    function setCoachDifficulty(level) {
      coachDifficulty = ["easy", "medium", "hard"].includes(level) ? level : "easy";
      document.querySelectorAll("[data-game-difficulty]").forEach((button) => {
        button.setAttribute("aria-pressed", String(button.dataset.gameDifficulty === coachDifficulty));
      });
      document.getElementById("gameDifficultyBadge").textContent = `${coachDifficulty[0].toUpperCase()}${coachDifficulty.slice(1)} coach`;
    }

    function scoreCoachMove(move, careful = false) {
      let score = Math.random() * 18;
      if (move.captured) score += coachPieceValues[move.captured] || 0;
      if (move.promotion) score += coachPieceValues[move.promotion] || 800;
      if (["d4", "e4", "d5", "e5"].includes(move.to)) score += 24;
      if (move.san.includes("+")) score += 70;
      if (move.san.includes("#")) score += 10000;

      try {
        coachGame.move(toCoachMoveInput(move));
        if (callCoachRule(coachGame, "isCheckmate", "in_checkmate")) score += 10000;
        if (callCoachRule(coachGame, "isCheck", "in_check")) score += 80;
        if (careful) {
          const replyDanger = Math.max(0, ...coachGame.moves({ verbose: true }).map((reply) => reply.captured ? coachPieceValues[reply.captured] || 0 : 0));
          score -= replyDanger * 0.45;
        }
        coachGame.undo();
      } catch {
        score -= 9999;
      }
      return score;
    }

    function chooseCoachMove() {
      const moves = coachGame.moves({ verbose: true });
      const scored = moves
        .map((move) => ({ move, score: scoreCoachMove(move, coachDifficulty === "hard") }))
        .sort((a, b) => b.score - a.score);

      if (coachDifficulty === "easy") {
        return Math.random() < 0.35 ? scored[0].move : moves[Math.floor(Math.random() * moves.length)];
      }

      const poolSize = coachDifficulty === "medium" ? 4 : 2;
      const pool = scored.slice(0, Math.min(poolSize, scored.length));
      return pool[Math.floor(Math.random() * pool.length)].move;
    }

    function choosePromotion(legalMoves) {
      if (!legalMoves.some((move) => move.promotion)) return undefined;
      const choice = String(window.prompt("Promote pawn to queen, rook, bishop, or knight? Type q, r, b, or n.", "q") || "q").toLowerCase();
      return ["q", "r", "b", "n"].includes(choice) ? choice : "q";
    }

    function explainLearnerMove(move, bestMove, betterGap) {
      const whiteMoveCount = coachGame.history({ verbose: true }).filter((item) => item.color === "w").length;
      const cheer = whiteMoveCount === 1 ? "Good!" : whiteMoveCount === 2 ? "Great!" : "Nice try!";
      let detail = `You played ${move.san}.`;
      if (move.flags.includes("k") || move.flags.includes("q")) detail = `Nice. ${move.san} castled your king toward safety.`;
      else if (move.captured) detail = `Good capture. ${move.san} won a ${move.captured.toUpperCase()}.`;
      else if (move.san.includes("+")) detail = `${move.san} gave check, so the coach must answer the king threat.`;

      if (bestMove && bestMove.san !== move.san && betterGap > 220) {
        coachWhyText = `${bestMove.san} was safer because forcing moves often give the opponent fewer choices.`;
        return `${cheer} ${detail} Can you find a safer square next time? Check if every piece is defended before moving.`;
      }
      coachWhyText = `${move.san} was playable because it followed the rules and kept the game moving. Now look for the coach's threat.`;
      return `${cheer} ${detail} Next, ask what the coach threatens.`;
    }

    function explainCoachMove(move) {
      if (callCoachRule(coachGame, "isCheckmate", "in_checkmate") || callCoachRule(coachGame, "isDraw", "in_draw")) {
        return buildCoachSummary();
      }
      if (move.captured) {
        coachWhyText = `${move.san} worked because it captured material with tempo.`;
        return `The coach played ${move.san} and captured a piece. Great try: now look for checks, captures, and threats.`;
      }
      if (move.san.includes("+")) {
        coachWhyText = `${move.san} is important because checks must be answered immediately.`;
        return `The coach played ${move.san}. Your king is in check, so answer that first.`;
      }
      coachWhyText = `${move.san} improves the coach's position without risking too much.`;
      return `The coach played ${move.san}. Look for a safe developing move or a forcing move.`;
    }

    function getMistakePracticeTopics(move) {
      if (move.piece === "q") return ["Defending pieces", "Hanging pieces", "Board scanning"];
      if (move.captured) return ["Safe captures", "Counting defenders", "Piece safety"];
      if (move.san.includes("+")) return ["King safety", "Check defense", "Candidate moves"];
      return ["Hanging pieces", "Piece safety", "Board scanning"];
    }

    function rememberCoachMistake(move, bestMove, note) {
      const state = readDailyTrainingState();
      saveDailyTrainingState({
        ...state,
        weaknesses: [...new Set(["review", "tactics", ...(state.weaknesses || [])])],
        lastMistake: {
          date: getTodayKey(),
          note,
          practice: getMistakePracticeTopics(move),
          better: bestMove?.san || ""
        }
      });
      renderDailyTraining();
    }

    function addGuidedReviewMoment(move, bestMove) {
      if (coachReviewMoments.length >= 3) return;
      const names = { p: "pawn", n: "knight", b: "bishop", r: "rook", q: "queen", k: "king" };
      const moveNumber = Math.max(1, Math.ceil(coachGame.history({ verbose: true }).length / 2));
      const piece = names[move.piece] || "piece";
      coachReviewMoments.push({
        move: moveNumber,
        headline: `Your ${piece} was undefended.`,
        why: "Your opponent could win material without giving anything back.",
        remember: bestMove ? `Check whether every piece is protected before moving. A calmer idea was ${bestMove.san}.` : "Check whether every piece is protected before moving."
      });
    }

    function renderGuidedGameReview(show) {
      const panel = document.getElementById("guidedReview");
      const list = document.getElementById("guidedReviewList");
      if (!panel || !list) return;
      panel.hidden = !show;
      if (!show) return;
      const moments = coachReviewMoments.length ? coachReviewMoments : [{
        move: Math.max(1, Math.ceil((coachGame?.history({ verbose: true }).length || 1) / 2)),
        headline: "No big mistake saved.",
        why: "You finished a legal game and practiced thinking.",
        remember: "Keep using the checklist: threat, undefended pieces, worst piece, tactic."
      }];
      list.replaceChildren(...moments.map((moment) => {
        const item = document.createElement("div");
        item.className = "review-moment";
        item.append(
          createBookText("strong", "", `Move ${moment.move}`),
          createBookText("span", "", moment.headline),
          createBookText("span", "", `Why it matters: ${moment.why}`),
          createBookText("span", "", `What to remember: ${moment.remember}`)
        );
        return item;
      }));
    }

    function buildCoachMistakeNote(move, bestMove) {
      const names = { p: "pawn", n: "knight", b: "bishop", r: "rook", q: "queen", k: "king" };
      const moveNumber = Math.max(1, Math.ceil(coachGame.history({ verbose: true }).length / 2));
      const piece = names[move.piece] || "piece";
      const safer = bestMove ? ` A safer idea was ${bestMove.san}.` : "";
      return `Your biggest mistake today: Move ${moveNumber}. Your ${piece} needed one more safety check.${safer} Practice: Hanging Pieces, Piece Safety, Defending Pieces.`;
    }

    function buildCoachSummary() {
      const moves = coachGame.history({ verbose: true });
      const whiteMoves = moves.filter((move) => move.color === "w");
      const captures = whiteMoves.filter((move) => move.captured).length;
      const castles = whiteMoves.some((move) => move.flags.includes("k") || move.flags.includes("q"));
      const focus = getSingleCoachFocus();
      const praise = castles
        ? "Great work getting your king safer."
        : captures
          ? "Great work spotting captures and staying active."
          : "Great work finishing a real legal game.";
      const mistake = coachReviewMoments[0]?.headline || "No major mistake saved.";
      return `You found ${whiteMoves.length} good moves today. What you did well: ${praise} Biggest mistake: ${mistake} Practice next: ${focus.practice}. Related puzzle: ${focus.related}.`;
    }

    function recordCoachGameResult(playerWon) {
      if (coachGameRecorded || !coachGame?.history().length) return;
      coachGameRecorded = true;
      const history = coachGame.history({ verbose: true });
      const whiteMoves = history.filter((move) => move.color === "w");
      const minorMoves = new Set(whiteMoves.filter((move) => ["n", "b"].includes(move.piece)).map((move) => move.from)).size;
      const castled = whiteMoves.some((move) => move.flags.includes("k") || move.flags.includes("q"));
      gameStats.played += 1;
      gameStats.hanging += coachCurrentHanging;
      if (coachCurrentHanging === 0) gameStats.cleanGames += 1;
      if (castled || minorMoves >= 2) gameStats.principleGames += 1;
      if (playerWon && history.length >= 24) gameStats.endgameWins += 1;
      let xpResult = { levelUp: false };
      if (playerWon) {
        gameStats.wins += 1;
        xpResult = addPuzzleXp(50);
        showCelebration("\uD83C\uDF89 Great Job!", "+50 XP", xpResult.levelUp ? "New Badge Unlocked!" : "First Win progress!");
      } else {
        xpResult = addPuzzleXp(coachCurrentHanging === 0 ? 18 : 10);
        showCelebration("Nice practice!", `+${coachCurrentHanging === 0 ? 18 : 10} XP`, coachCurrentHanging === 0 ? "No Hanging Pieces progress!" : "You learned one idea.");
      }
      savePuzzleState();
      renderBeginnerProgress();
    }

    function getScoredLearnerMoves(moves) {
      return moves
        .map((move) => ({ move, score: scoreCoachMove(move, true) }))
        .sort((a, b) => b.score - a.score);
    }

    function renderCoachCaptured() {
      const whiteCaptured = [];
      const blackCaptured = [];
      coachGame.history({ verbose: true }).forEach((move) => {
        if (!move.captured) return;
        const capturedColor = move.color === "w" ? "b" : "w";
        const symbol = coachPieceSymbols[capturedColor][move.captured] || "";
        if (move.color === "w") whiteCaptured.push(symbol);
        else blackCaptured.push(symbol);
      });
      document.getElementById("whiteCaptured").textContent = whiteCaptured.join(" ") || "None";
      document.getElementById("blackCaptured").textContent = blackCaptured.join(" ") || "None";
    }

    function renderCoachHistory() {
      const history = coachGame.history({ verbose: true });
      const list = document.getElementById("moveHistory");
      list.innerHTML = "";
      if (!history.length) {
        list.textContent = "No moves yet.";
        return;
      }

      for (let index = 0; index < history.length; index += 2) {
        const row = document.createElement("div");
        row.className = "move-pair";
        row.append(
          createBookText("strong", "", `${Math.floor(index / 2) + 1}.`),
          createBookText("span", "", history[index]?.san || ""),
          createBookText("span", "", history[index + 1]?.san || "")
        );
        list.appendChild(row);
      }
    }

    function renderCoachPracticeLinks(show) {
      const row = document.getElementById("coachPracticeLinks");
      if (!row) return;
      row.hidden = !show;
      if (!show) return;
      row.replaceChildren();
      const mistake = getCurrentMistakePractice(readDailyTrainingState());
      const focus = getSingleCoachFocus();
      const topics = mistake?.practice?.length ? mistake.practice : ["Hanging pieces", "Piece safety", "Defending pieces"];
      [[`Practice: ${focus.skill}`, focus.href], [`Related puzzle: ${focus.related}`, focus.href], ...topics.map((label) => [label, label.toLowerCase().includes("king") ? "#rules" : "#puzzles"])]
        .filter(([label], index, list) => list.findIndex(([item]) => item === label) === index)
        .forEach(([label, href]) => {
        const link = document.createElement("a");
        link.className = "button secondary";
        link.href = href;
        link.textContent = label;
        row.appendChild(link);
      });
    }

    function updateCoachPanel() {
      if (!coachGame) return;
      const statusBadge = document.getElementById("gameStatusBadge");
      const turnBadge = document.getElementById("gameTurnBadge");
      const coach = document.getElementById("gameCoach");
      const turn = coachGame.turn() === "w" ? "White" : "Black";
      const drawReason = callCoachRule(coachGame, "isStalemate", "in_stalemate") ? "Stalemate"
        : callCoachRule(coachGame, "isThreefoldRepetition", "in_threefold_repetition") ? "Threefold repetition"
          : callCoachRule(coachGame, "isDrawByFiftyMoves", "in_draw_by_fifty_moves") ? "Fifty-move draw"
            : callCoachRule(coachGame, "isInsufficientMaterial", "insufficient_material") ? "Insufficient material"
              : "";
      const isMate = callCoachRule(coachGame, "isCheckmate", "in_checkmate");
      const isDrawn = Boolean(drawReason) || callCoachRule(coachGame, "isDraw", "in_draw");

      if (coachDrawAgreed || isMate || isDrawn) recordCoachGameResult(isMate && coachGame.turn() === "b");

      turnBadge.textContent = coachThinking ? "Coach thinking" : `${turn} to move`;
      if (coachDrawAgreed) {
        statusBadge.textContent = "Draw agreed";
        coach.textContent = `Draw agreed. ${buildCoachSummary()}`;
      } else if (isMate) {
        statusBadge.textContent = "Checkmate";
        coach.textContent = buildCoachSummary();
      } else if (isDrawn) {
        statusBadge.textContent = drawReason || "Draw";
        coach.textContent = `${drawReason || "Draw"}. ${buildCoachSummary()}`;
      } else {
        statusBadge.textContent = isCoachCheck() ? "Check" : "Playing";
        coach.textContent = coachMessage;
      }

      renderCoachCaptured();
      renderCoachHistory();
      renderCoachPracticeLinks(coachDrawAgreed || isMate || isDrawn);
      renderGuidedGameReview(coachDrawAgreed || isMate || isDrawn);
      document.getElementById("undoGame").disabled = coachThinking || !coachGame.history().length;
      document.getElementById("replayMistake").disabled = coachThinking || !coachReplayFen;
      document.getElementById("showThreats").setAttribute("aria-pressed", String(coachThreatMode));
    }

    function renderCoachBoard() {
      const board = document.getElementById("coachBoard");
      if (!board || !coachGame) return;
      const legalByTarget = new Map(coachLegalMoves.map((move) => [move.to, move]));
      const lastSquares = coachLastMove ? [coachLastMove.from, coachLastMove.to] : [];
      const checkedKing = isCoachCheck() ? findCoachKing(coachGame.turn()) : "";
      const threatSquares = coachThreatMode ? getCoachThreatSquares() : new Set();

      board.innerHTML = "";
      getCoachSquares().forEach((squareNameValue) => {
        const piece = coachGame.get(squareNameValue);
        const legalMove = legalByTarget.get(squareNameValue);
        const square = document.createElement("button");
        square.type = "button";
        square.className = `puzzle-square play-square ${isLightCoachSquare(squareNameValue) ? "light" : "dark"}`;
        if (piece) square.classList.add(piece.color === "w" ? "white-piece" : "black-piece");
        if (squareNameValue === coachSelected) square.classList.add("selected");
        if (legalMove) square.classList.add(legalMove.captured || legalMove.flags.includes("e") ? "capture" : "legal");
        if (lastSquares.includes(squareNameValue)) square.classList.add("last-move");
        if (squareNameValue === checkedKing) square.classList.add("in-check");
        if (threatSquares.has(squareNameValue)) square.classList.add("threat");
        if (coachThinking) square.classList.add("is-ai-thinking");
        square.draggable = Boolean(piece && piece.color === "w" && coachGame.turn() === "w" && !coachThinking && !isCoachGameOver());
        square.textContent = piece ? coachPieceSymbols[piece.color][piece.type] : "";
        square.setAttribute("aria-label", `${squareNameValue}${piece ? ` ${piece.color === "w" ? "white" : "black"} ${piece.type}` : " empty"}`);
        square.addEventListener("dragstart", (event) => {
          if (!square.draggable) return event.preventDefault();
          coachSelected = squareNameValue;
          coachLegalMoves = coachGame.moves({ square: squareNameValue, verbose: true });
          event.dataTransfer.setData("text/plain", squareNameValue);
          square.classList.add("dragging");
        });
        square.addEventListener("dragend", () => square.classList.remove("dragging"));
        square.addEventListener("dragover", (event) => event.preventDefault());
        square.addEventListener("drop", (event) => {
          event.preventDefault();
          const from = event.dataTransfer.getData("text/plain");
          if (from) makeCoachMove(from, squareNameValue);
        });
        square.addEventListener("click", () => handleCoachSquare(squareNameValue));
        board.appendChild(square);
      });

      updateCoachPanel();
    }

    function makeCoachMove(from, to) {
      const legalMoves = coachGame.moves({ square: from, verbose: true }).filter((move) => move.to === to);
      if (!legalMoves.length) {
        coachMessage = "Good idea to explore. The rules need one of the highlighted squares here.";
        renderCoachBoard();
        return false;
      }

      const promotion = choosePromotion(legalMoves);
      const scoredMoves = getScoredLearnerMoves(coachGame.moves({ verbose: true }));
      const bestMove = scoredMoves[0]?.move || null;
      const pickedScore = scoredMoves.find(({ move }) => (
        move.from === from && move.to === to && (!move.promotion || move.promotion === (promotion || "q"))
      ))?.score || 0;
      const betterGap = (scoredMoves[0]?.score || 0) - pickedScore;
      const beforeFen = coachGame.fen();
      let move = null;
      try {
        move = coachGame.move({ from, to, ...(promotion ? { promotion } : {}) });
      } catch {
        move = null;
      }

      if (!move) {
        coachMessage = "Good idea to check it. The rules block that move, so choose a highlighted square.";
        renderCoachBoard();
        return false;
      }

      coachSelected = "";
      coachLegalMoves = [];
      coachLastMove = move;
      gameStats.moveQualityTotal += Math.max(0, Math.min(100, 100 - Math.round(betterGap / 8)));
      gameStats.moveQualityMoves += 1;
      if (betterGap > 220) {
        coachCurrentHanging += 1;
        coachReplayFen = beforeFen;
        coachMistakeNote = buildCoachMistakeNote(move, bestMove);
        addGuidedReviewMoment(move, bestMove);
        rememberCoachMistake(move, bestMove, coachMistakeNote);
      }
      coachMessage = explainLearnerMove(move, bestMove, betterGap);
      renderCoachBoard();
      queueCoachReply();
      return true;
    }

    function handleCoachSquare(square) {
      if (!coachGame || coachThinking || coachGame.turn() !== "w" || isCoachGameOver()) return;
      const piece = coachGame.get(square);
      if (coachSelected && square !== coachSelected && makeCoachMove(coachSelected, square)) return;

      if (piece && piece.color === "w") {
        coachSelected = square;
        coachLegalMoves = coachGame.moves({ square, verbose: true });
        coachMessage = `${coachLegalMoves.length} legal move${coachLegalMoves.length === 1 ? "" : "s"} highlighted. Pick one that keeps your pieces safe.`;
      } else {
        coachSelected = "";
        coachLegalMoves = [];
        coachMessage = "Choose one of your white pieces first.";
      }
      renderCoachBoard();
    }

    function queueCoachReply() {
      if (isCoachGameOver() || coachGame.turn() !== "b") return;
      const token = ++coachMoveToken;
      coachThinking = true;
      coachMessage = "Coach is thinking for a moment.";
      renderCoachBoard();

      window.setTimeout(() => {
        if (token !== coachMoveToken || !coachGame || coachGame.turn() !== "b" || isCoachGameOver()) return;
        const reply = chooseCoachMove();
        const move = reply && coachGame.move(toCoachMoveInput(reply));
        if (move) {
          coachLastMove = move;
          coachMessage = explainCoachMove(move);
        }
        coachThinking = false;
        renderCoachBoard();
      }, coachDifficulty === "hard" ? 720 : 520);
    }

    function restartCoachGame() {
      if (!CoachChess) return;
      coachMoveToken += 1;
      coachGame = new CoachChess();
      coachSelected = "";
      coachLegalMoves = [];
      coachLastMove = null;
      coachThinking = false;
      coachDrawAgreed = false;
      coachGameRecorded = false;
      coachMistakeNote = "";
      coachReviewMoments = [];
      coachCurrentHanging = 0;
      coachMessage = "Fresh game. You are White. Select a piece to see legal moves.";
      document.getElementById("gamePgn").textContent = "PGN appears here after export.";
      renderGuidedGameReview(false);
      renderCoachBoard();
    }

    function undoCoachMove() {
      if (!coachGame || coachThinking || !coachGame.history().length) return;
      coachMoveToken += 1;
      coachGame.undo();
      if (coachGame.turn() === "b") coachGame.undo();
      coachSelected = "";
      coachLegalMoves = [];
      coachLastMove = null;
      coachDrawAgreed = false;
      coachReviewMoments = [];
      coachCurrentHanging = 0;
      renderGuidedGameReview(false);
      coachMessage = "Undo complete. Try a calmer move and check what is attacked.";
      renderCoachBoard();
    }

    function askCoachWhy() {
      coachMessage = coachWhyText;
      renderCoachBoard();
    }

    function replayCoachMistake() {
      if (!CoachChess || !coachReplayFen) {
        coachMessage = "No replay moment yet. Make a few moves and the coach will save one useful mistake.";
        renderCoachBoard();
        return;
      }

      coachMoveToken += 1;
      coachGame = new CoachChess(coachReplayFen);
      coachSelected = "";
      coachLegalMoves = [];
      coachLastMove = null;
      coachThinking = false;
      coachDrawAgreed = false;
      coachGameRecorded = false;
      coachMistakeNote = "";
      coachReviewMoments = [];
      coachCurrentHanging = 0;
      coachMessage = "Replay this moment. Try the stronger idea before the coach moves.";
      renderGuidedGameReview(false);
      renderCoachBoard();
    }

    function toggleCoachThreats() {
      coachThreatMode = !coachThreatMode;
      coachMessage = coachThreatMode
        ? "Threats highlighted: red marks show white pieces or king checks Black may target."
        : "Threat highlights off. Keep asking what the coach threatens.";
      renderCoachBoard();
    }

    async function exportCoachPgn() {
      const pgn = coachGame?.pgn() || "No moves yet.";
      document.getElementById("gamePgn").textContent = pgn;
      try {
        if (navigator.clipboard?.writeText) {
          await navigator.clipboard.writeText(pgn);
          coachMessage = "PGN copied. Nice for reviewing your game later.";
        } else {
          coachMessage = "PGN is shown below. You can select it for review.";
        }
      } catch {
        coachMessage = "PGN is shown below. Your browser blocked auto-copy, but you can still select it.";
      }
      renderCoachBoard();
    }

    async function setupPuzzleChess() {
      const board = document.getElementById("puzzleBoard");
      if (!board || setupPuzzleChess.ready) return;
      setupPuzzleChess.ready = true;

      try {
        await loadChessRules();
      } catch {
        document.getElementById("feedback").textContent = "Could not load chess.js for playable puzzles. Check your connection, then refresh.";
        return;
      }

      renderPuzzle();
    }

    async function setupPlayableChess() {
      const board = document.getElementById("coachBoard");
      if (!board || setupPlayableChess.ready) return;
      setupPlayableChess.ready = true;

      try {
        await loadChessRules();
        coachGame = new CoachChess();
        coachGameRecorded = false;
        coachMistakeNote = "";
        coachReviewMoments = [];
        coachCurrentHanging = 0;
      } catch {
        document.getElementById("gameStatusBadge").textContent = "Rules failed";
        document.getElementById("gameCoach").textContent = "Could not load chess.js. Check your connection, then refresh.";
        return;
      }

      setCoachDifficulty(coachDifficulty);
      document.querySelectorAll("[data-game-difficulty]").forEach((button) => {
        button.addEventListener("click", () => {
          setCoachDifficulty(button.dataset.gameDifficulty);
          coachMessage = `Difficulty set to ${coachDifficulty}. Keep it friendly and focus on one idea.`;
          renderCoachBoard();
        });
      });
      document.getElementById("undoGame").addEventListener("click", undoCoachMove);
      document.getElementById("restartGame").addEventListener("click", restartCoachGame);
      document.getElementById("flipGame").addEventListener("click", () => {
        coachFlipped = !coachFlipped;
        renderCoachBoard();
      });
      document.getElementById("whyGame").addEventListener("click", askCoachWhy);
      document.getElementById("replayMistake").addEventListener("click", replayCoachMistake);
      document.getElementById("showThreats").addEventListener("click", toggleCoachThreats);
      document.getElementById("offerDraw").addEventListener("click", () => {
        coachDrawAgreed = true;
        coachMessage = buildCoachSummary();
        renderCoachBoard();
      });
      document.getElementById("exportPgn").addEventListener("click", exportCoachPgn);
      renderCoachBoard();
    }

    function setupSiteTabs() {
      const panelIds = ["paths", "adventures", "rules", "openings", "videos", "books", "notation", "play", "puzzles", "plan"];
      const links = [...document.querySelectorAll("[data-site-tab]")];
      const panels = panelIds
        .map((id) => document.getElementById(id))
        .filter(Boolean);
      const reduceMotion = window.matchMedia("(prefers-reduced-motion: reduce)").matches;

      panels.forEach((panel) => {
        panel.classList.add("site-panel");
        panel.setAttribute("tabindex", "-1");
      });

      function getConfigFromHash(hashValue) {
        const cleanHash = String(hashValue || "").replace(/^#/, "");
        if (!cleanHash || cleanHash === "top") return null;

        if (cleanHash.startsWith("book-")) {
          return { tab: "books", panel: "books", focus: cleanHash };
        }

        if (cleanHash.startsWith("short-")) {
          return { tab: "shorts", panel: "videos", focus: cleanHash };
        }

        const link = links.find((item) => item.dataset.siteTab === cleanHash || item.getAttribute("href") === `#${cleanHash}`);
        if (!link) return null;

        return {
          tab: link.dataset.siteTab,
          panel: link.dataset.sitePanel || link.dataset.siteTab,
          focus: link.dataset.siteFocus || link.dataset.siteTab
        };
      }

      function clearActiveTabs() {
        links.forEach((link) => {
          link.classList.remove("is-active-tab");
          link.removeAttribute("aria-current");
        });
      }

      function showHome(shouldScroll = false) {
        document.body.classList.remove("site-tab-mode");
        clearActiveTabs();
        panels.forEach((panel) => {
          panel.classList.remove("is-active-panel");
          panel.removeAttribute("aria-hidden");
        });

        if (shouldScroll) {
          window.scrollTo({ top: 0, behavior: reduceMotion ? "auto" : "smooth" });
        }
      }

      function activateSiteTab(config, shouldScroll = true) {
        if (!config) {
          showHome(shouldScroll);
          return;
        }

        const panel = document.getElementById(config.panel);
        const activeLink = links.find((link) => link.dataset.siteTab === config.tab);
        if (!panel) {
          showHome(shouldScroll);
          return;
        }

        document.body.classList.add("site-tab-mode");
        panels.forEach((item) => {
          const isActive = item === panel;
          item.classList.toggle("is-active-panel", isActive);
          item.setAttribute("aria-hidden", String(!isActive));
        });

        clearActiveTabs();
        if (activeLink) {
          activeLink.classList.add("is-active-tab");
          activeLink.setAttribute("aria-current", "page");
          activeLink.scrollIntoView({
            behavior: reduceMotion ? "auto" : "smooth",
            block: "nearest",
            inline: "center"
          });
        }

        if (shouldScroll) {
          window.requestAnimationFrame(() => {
            const target = document.getElementById(config.focus) || panel;
            target.scrollIntoView({
              behavior: reduceMotion ? "auto" : "smooth",
              block: "start"
            });
            panel.focus({ preventScroll: true });
          });
        }
      }

      function syncTabsFromHash(shouldScroll = false) {
        const config = getConfigFromHash(window.location.hash);
        if (config) {
          activateSiteTab(config, shouldScroll);
        } else {
          showHome(shouldScroll && window.location.hash === "#top");
        }
      }

      document.querySelectorAll('a[href^="#"]').forEach((link) => {
        const href = link.getAttribute("href");
        const isHomeLink = href === "#top";
        const config = getConfigFromHash(href);
        if (!config && !isHomeLink) return;

        link.addEventListener("click", (event) => {
          if (event.defaultPrevented || event.button !== 0 || event.metaKey || event.ctrlKey || event.shiftKey || event.altKey) return;
          event.preventDefault();

          if (window.history?.pushState) {
            window.history.pushState(null, "", href);
          } else {
            window.location.hash = href;
          }

          if (isHomeLink) {
            showHome(true);
          } else {
            activateSiteTab(config, true);
          }
        });
      });

      window.addEventListener("hashchange", () => syncTabsFromHash(true));
      window.addEventListener("popstate", () => syncTabsFromHash(false));
      syncTabsFromHash(false);
    }

    function wireTabs() {
      const tabs = document.querySelectorAll(".tab-button");
      const panels = ["beginner", "intermediate", "advanced"].map((id) => document.getElementById(id));

      tabs.forEach((tab) => {
        tab.addEventListener("click", () => {
          const level = tab.dataset.level;
          tabs.forEach((item) => item.setAttribute("aria-selected", String(item === tab)));
          panels.forEach((panel) => panel.classList.toggle("hidden", panel.id !== level));
          updateLessonJourney();
        });
      });
    }

    function readJsonStorage(key, fallback) {
      try {
        return JSON.parse(localStorage.getItem(key) || JSON.stringify(fallback));
      } catch {
        return fallback;
      }
    }

    function writeJsonStorage(key, value) {
      try {
        localStorage.setItem(key, JSON.stringify(value));
      } catch {
        // Storage can be unavailable in private browsing; the page still works without persistence.
      }
    }

    function readLearnerPrefs() {
      const fallback = { theme: "dark", board: "wood", pieces: "classic", coords: "on", speed: "normal", pressure: "on" };
      const saved = readJsonStorage(learnerPrefsStorageKey, fallback);
      return { ...fallback, ...(saved && typeof saved === "object" ? saved : {}) };
    }

    function applyPiecePreference(style) {
      const useLetters = style === "letter";
      Object.assign(pieceMap, useLetters ? letterPieceMap : classicPieceMap);
      Object.assign(coachPieceSymbols.w, useLetters ? letterCoachPieceSymbols.w : classicCoachPieceSymbols.w);
      Object.assign(coachPieceSymbols.b, useLetters ? letterCoachPieceSymbols.b : classicCoachPieceSymbols.b);
    }

    function applyLearnerPrefs(prefs) {
      document.body.classList.toggle("theme-light", prefs.theme === "light");
      document.body.classList.toggle("board-wood", prefs.board === "wood");
      document.body.classList.toggle("board-marble", prefs.board === "marble");
      document.body.classList.toggle("board-neon", prefs.board === "neon");
      document.body.classList.toggle("piece-letter", prefs.pieces === "letter");
      document.body.classList.toggle("coords-off", prefs.coords === "off");
      document.body.classList.toggle("speed-slow", prefs.speed === "slow");
      document.body.classList.toggle("speed-fast", prefs.speed === "fast");
      document.body.classList.toggle("no-pressure", prefs.pressure !== "off");
      applyPiecePreference(prefs.pieces);
    }

    function setupLearnerPreferences() {
      const prefs = readLearnerPrefs();
      const fields = {
        theme: document.getElementById("prefTheme"),
        board: document.getElementById("prefBoard"),
        pieces: document.getElementById("prefPieces"),
        coords: document.getElementById("prefCoords"),
        speed: document.getElementById("prefSpeed"),
        pressure: document.getElementById("prefPressure")
      };
      const messages = [
        "Every master was once a beginner.",
        "One puzzle today is better than none.",
        "You're improving - keep going!"
      ];
      const note = document.getElementById("motivationMessage");

      applyLearnerPrefs(prefs);
      Object.entries(fields).forEach(([key, field]) => {
        if (!field) return;
        field.value = prefs[key];
        field.addEventListener("change", () => {
          const next = { ...readLearnerPrefs(), [key]: field.value };
          writeJsonStorage(learnerPrefsStorageKey, next);
          applyLearnerPrefs(next);
          renderMiniBoards();
          renderPuzzle();
          renderCoachBoard();
        });
      });
      if (note) note.textContent = messages[new Date().getDate() % messages.length];
    }

    function slugify(value) {
      return String(value || "book")
        .toLowerCase()
        .replace(/[^a-z0-9]+/g, "-")
        .replace(/^-+|-+$/g, "")
        .slice(0, 72) || "book";
    }

    function getTodayKey() {
      const now = new Date();
      const month = String(now.getMonth() + 1).padStart(2, "0");
      const day = String(now.getDate()).padStart(2, "0");
      return `${now.getFullYear()}-${month}-${day}`;
    }

    function readDailyTrainingState() {
      const fallback = {
        date: getTodayKey(),
        level: "Beginner",
        minutes: 25,
        goal: "balanced",
        weaknesses: ["tactics"],
        completed: [],
        history: [],
        lastMistake: null,
        routineVersion: 2
      };
      const saved = readJsonStorage(dailyTrainingStorageKey, fallback);
      const state = saved && typeof saved === "object" ? saved : {};
      const nextState = {
        ...fallback,
        ...state,
        completed: Array.isArray(state.completed) ? state.completed : [],
        history: Array.isArray(state.history) ? state.history : [],
        lastMistake: state.lastMistake && typeof state.lastMistake === "object" ? state.lastMistake : null,
        weaknesses: Array.isArray(state.weaknesses) && state.weaknesses.length ? state.weaknesses : fallback.weaknesses
      };

      if (nextState.date !== fallback.date) {
        nextState.date = fallback.date;
        nextState.completed = [];
      }
      if (state.routineVersion !== 2 && Number(nextState.minutes) === 20) {
        nextState.minutes = 25;
      }

      return nextState;
    }

    function saveDailyTrainingState(state) {
      writeJsonStorage(dailyTrainingStorageKey, {
        ...readDailyTrainingState(),
        ...state
      });
    }

    function getTrainingFocusBank() {
      return {
        tactics: {
          label: "Tactics",
          detail: "Solve forcing moves first: checks, captures, threats, then quiet winning moves.",
          href: "#puzzles",
          cta: "Open Puzzles"
        },
        openings: {
          label: "Openings",
          detail: "Review one line, then explain the plan in plain words: center, pieces, king safety, target.",
          href: "#openings",
          cta: "Open Openings"
        },
        endgame: {
          label: "Endgame",
          detail: "Drill one simple ending until you know where the king belongs and which pawn move matters.",
          href: "#videos",
          cta: "Watch Endgames"
        },
        strategy: {
          label: "Strategy",
          detail: "Compare your worst piece, pawn weaknesses, open files, king safety, and the opponent's threat.",
          href: "#books",
          cta: "Read Strategy"
        },
        calculation: {
          label: "Calculation",
          detail: "Pick 2 candidate moves, calculate forcing replies, then choose the line with the clearest result.",
          href: "#puzzles",
          cta: "Train Calculation"
        },
        review: {
          label: "Game Review",
          detail: "Find the first move where the position changed and write the better plan in one sentence.",
          href: "#notation",
          cta: "Use Notation"
        }
      };
    }

    function getTrainingPatternLadder() {
      return ["Forks", "Pins", "Skewers", "Double attacks", "Discovered attacks", "Removing the defender", "Back-rank mates", "Smothered mates"];
    }

    function getDailyPattern(level) {
      const tracks = {
        Beginner: ["Forks", "Pins", "Back-rank mates"],
        Intermediate: ["Skewers", "Double attacks", "Removing the defender"],
        Advanced: ["Discovered attacks", "Smothered mates", "Removing the defender"]
      };
      const list = tracks[level] || tracks.Beginner;
      const day = Number(getTodayKey().slice(-2)) || 1;
      return list[day % list.length];
    }

    function splitTrainingMinutes(minutes) {
      if (minutes === 25) return [5, 5, 0, 10, 5];
      const parts = [0.2, 0.25, 0.2, 0.2, 0.15].map((weight) => Math.max(2, Math.floor(minutes * weight)));
      let diff = minutes - parts.reduce((total, value) => total + value, 0);
      let index = 0;
      while (diff > 0) {
        parts[index % parts.length] += 1;
        diff -= 1;
        index += 1;
      }
      while (diff < 0) {
        const largest = parts.indexOf(Math.max(...parts));
        if (parts[largest] <= 2) break;
        parts[largest] -= 1;
        diff += 1;
      }
      return parts;
    }

    function getCurrentMistakePractice(state) {
      return state.lastMistake?.date === getTodayKey() ? state.lastMistake : null;
    }

    function buildDailyTrainingPlan(state) {
      const level = state.level || "Beginner";
      const minutes = Math.max(15, Math.min(60, Number(state.minutes) || 25));
      const goalLabels = {
        balanced: "Balanced improvement",
        rating: "Win more games",
        opening: "Fix my openings",
        tactics: "Spot tactics faster",
        endgame: "Finish winning games"
      };
      const levelTips = {
        Beginner: "Keep it simple: safe king, no hanging pieces, basic mates.",
        Intermediate: "Turn every idea into a threat and review your first serious mistake.",
        Advanced: "Slow down at critical moments and compare candidate moves before calculating deeply."
      };
      const bank = getTrainingFocusBank();
      const accuracy = getPuzzleAccuracy();
      const coachFocus = getSingleCoachFocus();
      const assessmentScores = getWeeklySkillScores();
      const assessment = [...assessmentScores].sort((a, b) => a[1] - b[1])[0];
      const automaticWeaknesses = [
        accuracy < 60 ? "tactics" : "",
        gameStats.played ? "review" : "",
        coachFocus.weaknessKey
      ].filter(Boolean);
      const weaknesses = [...new Set([...(state.weaknesses || ["tactics"]), ...automaticWeaknesses])].filter((item) => bank[item]);
      const primaryKey = weaknesses[0] || "tactics";
      const secondaryKey = weaknesses.find((item) => item !== primaryKey) || (state.goal === "endgame" ? "endgame" : "review");
      const primary = bank[primaryKey];
      const secondary = bank[secondaryKey] || bank.review;
      const pattern = getDailyPattern(level);
      const mistake = getCurrentMistakePractice(state);
      const mistakePractice = Array.isArray(mistake?.practice) ? mistake.practice.join(", ") : "Hanging Pieces, Piece Safety, Defending Pieces";
      const [warmupMinutes, focusMinutes, lessonMinutes, gameMinutes, reviewMinutes] = splitTrainingMinutes(minutes);

      const tasks = [
        {
          key: "warmup",
          title: "Board vision",
          minutes: warmupMinutes,
          detail: level === "Beginner"
            ? "Spend 5 minutes asking: what is hanging, who attacks it, and is my king safe?"
            : "Scan for checks, captures, threats, loose pieces, and king danger before moving.",
          href: "#puzzles",
          cta: "Open Puzzles"
        },
        {
          key: `focus-${primaryKey}`,
          title: `Tactical puzzles: ${pattern}`,
          minutes: focusMinutes,
          detail: `Pattern recognition: start simple, then make ${pattern.toLowerCase()} one step harder. ${primary.detail}`,
          href: "#puzzles",
          cta: "Train Pattern"
        }
      ];

      if (lessonMinutes > 0) tasks.push({
          key: "lesson",
          title: secondaryKey === "endgame" ? "Endgame Drill" : "One lesson, one rule",
          minutes: lessonMinutes,
          detail: secondaryKey === "endgame" ? secondary.detail : state.goal === "opening"
            ? "Watch or read one opening idea and write the plan before memorizing moves."
            : "Watch one short lesson, then write one rule you will use in the next game.",
          href: secondaryKey === "endgame" ? secondary.href : state.goal === "opening" ? "#openings" : "#videos",
          cta: secondaryKey === "endgame" ? secondary.cta : state.goal === "opening" ? "Open Openings" : "Open Videos"
        });

      tasks.push({
        key: "game",
        title: "Play One Game",
        minutes: gameMinutes,
        detail: level === "Advanced"
          ? "Play slowly and mark every candidate-move decision you were unsure about."
          : "Play one game using today's rule. Before each move, ask what your opponent threatens.",
        href: "#play",
        cta: "Play AI"
      });

      tasks.push({
        key: `review-${secondaryKey}`,
        title: "Review 3 Mistakes",
        minutes: reviewMinutes,
        detail: mistake
          ? `${mistake.note} Practice: ${mistakePractice}.`
          : "Find three moments: hanging piece, missed tactic, king safety. Write one better plan.",
        href: "#play",
        cta: "Review Game"
      });

      return {
        title: `${level} Daily Training`,
        focus: primary.label,
        goal: goalLabels[state.goal] || goalLabels.balanced,
        coachTip: levelTips[level] || levelTips.Beginner,
        assessment: `${assessment[0]} ${assessment[1]}%`,
        assessmentSummary: assessmentScores.map(([skill, score]) => `${skill} ${score}%`).join(", "),
        nextFocus: coachFocus,
        activePattern: pattern,
        patterns: getTrainingPatternLadder(),
        tasks
      };
    }

    function syncDailyTrainingForm(state) {
      const level = document.getElementById("trainingLevel");
      const minutes = document.getElementById("trainingMinutes");
      const goal = document.getElementById("trainingGoal");
      const minutesLabel = document.getElementById("trainingMinutesLabel");
      if (!level || !minutes || !goal) return;

      level.value = state.level;
      minutes.value = String(state.minutes);
      goal.value = state.goal;
      if (minutesLabel) minutesLabel.textContent = `${state.minutes} min`;

      document.querySelectorAll('[name="trainingWeakness"]').forEach((input) => {
        input.checked = (state.weaknesses || []).includes(input.value);
      });
    }

    function getSelectedTrainingWeaknesses() {
      const selected = [...document.querySelectorAll('[name="trainingWeakness"]:checked')].map((input) => input.value);
      return selected.length ? selected : ["tactics"];
    }

    function renderDailyTraining() {
      const output = document.getElementById("dailyTrainingOutput");
      if (!output) return;

      const state = readDailyTrainingState();
      const plan = buildDailyTrainingPlan(state);
      const completed = new Set(state.completed || []);
      const doneCount = plan.tasks.filter((task) => completed.has(task.key)).length;
      const planMinutes = plan.tasks.reduce((total, task) => total + task.minutes, 0);
      const progress = Math.round((doneCount / plan.tasks.length) * 100);

      output.innerHTML = "";

      const summary = document.createElement("div");
      const progressBar = document.createElement("div");
      const taskList = document.createElement("ul");
      const actions = document.createElement("div");
      const patternRow = document.createElement("div");
      const note = createBookText("p", "trainer-note", "Progress saves on this device. Finish all tasks to mark today as a completed training day.");
      const actionKeys = new Set();

      summary.className = "trainer-summary";
      progressBar.className = "trainer-progress";
      taskList.className = "training-task-list";
      actions.className = "trainer-actions";
      patternRow.className = "trainer-patterns";
      progressBar.setAttribute("aria-label", `Training progress ${progress}%`);
      progressBar.innerHTML = `<span style="width: ${progress}%"></span>`;

      [
        [plan.title, "Today's track"],
        [planMinutes + " min", "Training time"],
        [doneCount + "/" + plan.tasks.length, "Tasks done"],
        [String((state.history || []).length), "Completed days"]
      ].forEach(([value, label]) => {
        const stat = document.createElement("div");
        stat.className = "trainer-stat";
        stat.append(createBookText("strong", "", value), createBookText("span", "", label));
        summary.appendChild(stat);
      });

      plan.patterns.forEach((pattern) => {
        const badge = document.createElement("span");
        badge.textContent = pattern;
        if (pattern === plan.activePattern) badge.className = "is-active";
        patternRow.appendChild(badge);
      });

      plan.tasks.forEach((task) => {
        const item = document.createElement("li");
        const checkbox = document.createElement("input");
        const copy = document.createElement("div");
        const title = createBookText("strong", "", task.title);
        const detail = createBookText("small", "", task.detail);
        const time = createBookText("span", "training-time", `${task.minutes} min`);
        const link = document.createElement("a");
        const isComplete = completed.has(task.key);

        item.className = `training-task${isComplete ? " is-complete" : ""}`;
        checkbox.type = "checkbox";
        checkbox.checked = isComplete;
        checkbox.setAttribute("aria-label", `Mark ${task.title} complete`);
        checkbox.addEventListener("change", () => {
          const nextState = readDailyTrainingState();
          const nextCompleted = new Set(nextState.completed || []);
          if (checkbox.checked) {
            nextCompleted.add(task.key);
          } else {
            nextCompleted.delete(task.key);
          }

          const nextHistory = new Set(nextState.history || []);
          if (nextCompleted.size >= plan.tasks.length) {
            nextHistory.add(nextState.date);
            fireConfettiBurst();
          }

          saveDailyTrainingState({
            completed: [...nextCompleted],
            history: [...nextHistory]
          });
          renderDailyTraining();
        });

        link.className = "button secondary";
        link.href = task.href;
        link.textContent = task.cta;

        copy.append(title, detail);
        item.append(checkbox, copy, time);
        taskList.appendChild(item);
        if (!actionKeys.has(`${task.href}-${task.cta}`)) {
          actionKeys.add(`${task.href}-${task.cta}`);
          actions.appendChild(link);
        }
      });

      output.append(
        createBookText("p", "plan-focus", `${plan.goal}: ${plan.coachTip} Weekly check: ${plan.assessmentSummary}. Single focus: ${plan.nextFocus.practice}.`),
        summary,
        patternRow,
        progressBar,
        taskList,
        actions,
        note
      );
    }

    function setupDailyTraining() {
      const form = document.getElementById("dailyTrainingForm");
      const minutes = document.getElementById("trainingMinutes");
      const minutesLabel = document.getElementById("trainingMinutesLabel");
      const resetButton = document.getElementById("resetTraining");
      if (!form) return;

      const state = readDailyTrainingState();
      syncDailyTrainingForm(state);
      renderDailyTraining();

      minutes?.addEventListener("input", () => {
        if (minutesLabel) minutesLabel.textContent = `${minutes.value} min`;
      });

      form.addEventListener("submit", (event) => {
        event.preventDefault();
        const nextState = {
          date: getTodayKey(),
          level: document.getElementById("trainingLevel").value,
          minutes: Number(document.getElementById("trainingMinutes").value) || 31,
          goal: document.getElementById("trainingGoal").value,
          weaknesses: getSelectedTrainingWeaknesses(),
          completed: []
        };

        saveDailyTrainingState(nextState);
        syncDailyTrainingForm(readDailyTrainingState());
        renderDailyTraining();
      });

      resetButton?.addEventListener("click", () => {
        const current = readDailyTrainingState();
        saveDailyTrainingState({ ...current, completed: [] });
        renderDailyTraining();
      });
    }

    function readCustomBooks() {
      const books = readJsonStorage(customBooksStorageKey, []);
      return Array.isArray(books) ? books : [];
    }

    function saveCustomBooks(books) {
      writeJsonStorage(customBooksStorageKey, books);
    }

    function getAllBooks() {
      return [...freeChessBooks, ...readCustomBooks()];
    }

    function createBookText(tag, className, text) {
      const element = document.createElement(tag);
      if (className) element.className = className;
      element.textContent = text;
      return element;
    }

    function readGentleStartState() {
      const fallback = {
        date: getTodayKey(),
        mood: "new",
        minutes: 5,
        energy: "normal",
        completed: []
      };
      const saved = readJsonStorage(gentleStartStorageKey, fallback);
      const state = saved && typeof saved === "object" ? saved : {};
      const nextState = {
        ...fallback,
        ...state,
        minutes: Number(state.minutes) || fallback.minutes,
        completed: Array.isArray(state.completed) ? state.completed : []
      };

      if (nextState.date !== fallback.date) {
        nextState.date = fallback.date;
        nextState.completed = [];
      }

      return nextState;
    }

    function saveGentleStartState(partial) {
      writeJsonStorage(gentleStartStorageKey, {
        ...readGentleStartState(),
        ...partial
      });
    }

    function buildGentleQuest(state) {
      const minutes = Math.max(5, Math.min(12, Number(state.minutes) || 5));
      const warmup = minutes <= 5 ? 1 : 2;
      const learn = minutes <= 5 ? 2 : 3;
      const play = minutes <= 5 ? 2 : 3;
      const moodPlans = {
        new: {
          title: "First move confidence",
          note: "Today is only about recognizing the board and making one legal move feel easy.",
          tasks: [
            ["Board hello", "Open Rules and read piece movement slowly.", "#rules", "Rules"],
            ["Character move", "Try one Adventure mission and notice the piece pattern.", "#adventures", "Adventures"],
            ["Tiny finish", "Solve one beginner puzzle or just read the hint.", "#puzzles", "Puzzle"]
          ]
        },
        blunders: {
          title: "Stop one hanging piece",
          note: "You do not need perfect chess. Just catch one piece before it gets lost.",
          tasks: [
            ["Blunder check", "Before each move ask: is my king safe, is my piece attacked, what do they threaten?", "#rules", "Safety"],
            ["Pattern pop", "Solve one fork or hanging-piece puzzle.", "#puzzles", "Puzzle"],
            ["One sentence", "Write the mistake you understood in Notation.", "#notation", "Review"]
          ]
        },
        fun: {
          title: "Fun challenge sprint",
          note: "Keep it playful. Short, bright, and done before it feels heavy.",
          tasks: [
            ["Watch one spark", "Open Shorts and watch one quick idea.", "#shorts", "Shorts"],
            ["Play the mission", "Try an Adventure like a story level.", "#adventures", "Adventure"],
            ["Finish happy", "Mark one thing you can now recognize faster.", "#plan", "Plan"]
          ]
        },
        opening: {
          title: "Opening without memorizing",
          note: "The goal is not long lines. The goal is knowing what your pieces are trying to do.",
          tasks: [
            ["One rule", "Read one opening card and say the plan out loud.", "#openings", "Openings"],
            ["One clip", "Watch one beginner opening video or Short.", "#videos", "Video"],
            ["One game idea", "Play with only three goals: center, pieces, castle.", "#plan", "Plan"]
          ]
        }
      };
      const energyNotes = {
        calm: "Use calm mode: pause often and stop as soon as the idea is clear.",
        normal: "Use steady mode: finish the three steps, then take the win.",
        spark: "Use spark mode: add one extra puzzle only if you still feel fresh."
      };
      const plan = moodPlans[state.mood] || moodPlans.new;
      const times = [warmup, learn, play];

      return {
        ...plan,
        energyNote: energyNotes[state.energy] || energyNotes.normal,
        tasks: plan.tasks.map(([title, detail, href, cta], index) => ({
          key: `${state.mood}-${index}`,
          title,
          detail,
          href,
          cta,
          minutes: times[index]
        }))
      };
    }

    function syncGentleStartForm(state) {
      const mood = document.getElementById("gentleMood");
      const minutes = document.getElementById("gentleMinutes");
      const energy = document.getElementById("gentleEnergy");
      if (!mood || !minutes || !energy) return;

      mood.value = state.mood;
      minutes.value = String(state.minutes);
      energy.value = state.energy;
    }

    function renderGentleStart() {
      const output = document.getElementById("gentleQuestOutput");
      if (!output) return;

      const state = readGentleStartState();
      const quest = buildGentleQuest(state);
      const completed = new Set(state.completed || []);
      output.innerHTML = "";

      const heading = createBookText("h4", "", quest.title);
      const note = createBookText("p", "", `${quest.note} ${quest.energyNote}`);
      const list = document.createElement("ul");
      const doneCount = quest.tasks.filter((task) => completed.has(task.key)).length;
      const progress = createBookText("p", "trainer-note", `${doneCount}/${quest.tasks.length} tiny wins finished today. No rush.`);
      const nextTask = quest.tasks.find((task) => !completed.has(task.key)) || quest.tasks[0];
      const continueLink = document.createElement("a");

      list.className = "gentle-task-list";
      quest.tasks.forEach((task) => {
        const item = document.createElement("li");
        const checkbox = document.createElement("input");
        const copy = document.createElement("div");
        const title = createBookText("strong", "", task.title);
        const detail = createBookText("small", "", task.detail);
        const link = document.createElement("a");
        const time = createBookText("span", "gentle-time", `${task.minutes} min`);
        const isDone = completed.has(task.key);

        item.className = `gentle-task${isDone ? " is-done" : ""}`;
        checkbox.type = "checkbox";
        checkbox.checked = isDone;
        checkbox.setAttribute("aria-label", `Mark ${task.title} done`);
        checkbox.addEventListener("change", () => {
          const nextState = readGentleStartState();
          const nextCompleted = new Set(nextState.completed || []);
          if (checkbox.checked) {
            nextCompleted.add(task.key);
          } else {
            nextCompleted.delete(task.key);
          }
          saveGentleStartState({ completed: [...nextCompleted] });
          if (nextCompleted.size >= quest.tasks.length) fireConfettiBurst();
          renderGentleStart();
        });

        link.className = "button secondary";
        link.href = task.href;
        link.textContent = task.cta;
        copy.append(title, detail);
        item.append(checkbox, copy, time, link);
        list.appendChild(item);
      });

      continueLink.className = "button";
      continueLink.href = nextTask.href;
      continueLink.textContent = "Continue Learning";
      output.append(heading, note, list, progress, continueLink);
    }

    function setupGentleStart() {
      const form = document.getElementById("gentleStartForm");
      const beginnerButton = document.getElementById("newToChessButton");
      if (!form) return;

      syncGentleStartForm(readGentleStartState());
      renderGentleStart();

      form.addEventListener("submit", (event) => {
        event.preventDefault();
        saveGentleStartState({
          date: getTodayKey(),
          mood: document.getElementById("gentleMood").value,
          minutes: Number(document.getElementById("gentleMinutes").value) || 5,
          energy: document.getElementById("gentleEnergy").value,
          completed: []
        });
        renderGentleStart();
      });

      if (beginnerButton) {
        beginnerButton.addEventListener("click", () => {
          saveGentleStartState({
            date: getTodayKey(),
            mood: "new",
            minutes: 5,
            energy: "calm",
            completed: []
          });
          syncGentleStartForm(readGentleStartState());
          renderGentleStart();
        });
      }
    }

    function createBookTopicList(topics) {
      const list = document.createElement("ul");
      list.className = "topic-list";
      topics.forEach((topic) => {
        list.appendChild(createBookText("li", "", topic));
      });
      return list;
    }

    function createBookSourceLink(book, label = "View source") {
      const link = document.createElement("a");
      link.className = "button";
      link.href = book.sourceUrl;
      link.target = "_blank";
      link.rel = "noopener";
      link.textContent = label;
      return link;
    }

    function bookMatchesSearch(book, query) {
      if (!query) return true;
      const searchable = [
        book.title,
        book.author,
        book.year,
        book.edition,
        book.level,
        book.summary,
        book.bestUse,
        book.sourceName,
        ...(book.categories || []),
        ...(book.topics || []),
        ...(book.importantDetails || [])
      ].join(" ").toLowerCase();

      return searchable.includes(query);
    }

    function bookMatchesCategory(book) {
      return activeBookCategory === "all" || (book.categories || []).includes(activeBookCategory);
    }

    function bookCoverLetters(title) {
      const skipWords = new Set(["and", "of", "the", "to", "a"]);
      const letters = title
        .split(/\s+/)
        .filter((word) => word && !skipWords.has(word.toLowerCase()))
        .slice(0, 2)
        .map((word) => word[0].toUpperCase());

      return letters.join("") || "CB";
    }

    function createBookCard(book) {
      const card = document.createElement("article");
      const main = document.createElement("div");
      const top = document.createElement("div");
      const cover = createBookText("span", `book-cover ${book.level.toLowerCase()}`, bookCoverLetters(book.title));
      const copy = document.createElement("div");
      const level = createBookText("span", "badge", book.level);
      const freeTag = createBookText("span", "book-free-tag", "Free legal source");
      const title = createBookText("h3", "", book.title);
      const summary = createBookText("p", "", book.summary);
      const meta = document.createElement("div");
      const source = createBookText("p", "book-source", `${book.sourceName}: ${book.sourceUrl}`);
      const actions = document.createElement("div");
      const readButton = createBookText("button", "button", "Read Summary");
      const detailsButton = createBookText("button", "button secondary", "Details");

      card.className = "book-card";
      card.id = `book-${book.id}`;
      card.dataset.bookCard = book.id;
      main.className = "book-card-main";
      top.className = "book-card-top";
      copy.className = "book-card-copy";
      meta.className = "book-meta";
      actions.className = "book-actions";
      cover.setAttribute("role", "img");
      cover.setAttribute("aria-label", `${book.title} cover`);
      readButton.type = "button";
      readButton.setAttribute("aria-label", `Read summary for ${book.title}`);
      readButton.addEventListener("click", () => openBookReader(book.id));
      detailsButton.type = "button";
      detailsButton.setAttribute("aria-label", `Show details for ${book.title}`);
      detailsButton.addEventListener("click", () => showBookDetail(book.id));

      meta.append(
        createBookText("span", "", `Author: ${book.author}`),
        createBookText("span", "", `Year: ${book.year}`),
        createBookText("span", "", `Edition: ${book.edition}`)
      );

      copy.append(level, freeTag, title, summary);
      top.append(cover, copy);
      main.append(top, meta, createBookTopicList(book.topics));
      actions.append(readButton, detailsButton, createBookSourceLink(book, "Source"));
      card.append(main, source, actions);
      return card;
    }

    function showBookDetail(bookId, shouldScroll = true) {
      const detail = document.getElementById("bookDetail");
      const book = getAllBooks().find((item) => item.id === bookId);
      if (!detail || !book) return;

      detail.innerHTML = "";
      detail.hidden = false;
      detail.dataset.bookId = book.id;

      const grid = document.createElement("div");
      const metaPanel = document.createElement("div");
      const copyPanel = document.createElement("div");
      const badge = createBookText("span", "badge", book.level);
      const title = createBookText("h3", "", book.title);
      const summary = createBookText("p", "", book.summary);
      const metaList = document.createElement("dl");
      const useHeading = createBookText("h4", "", "Fast use");
      const useNote = createBookText("p", "", book.bestUse || "Read the summary first, then open the legal source for the full text.");
      const keyHeading = createBookText("h4", "", "Important details");
      const topicsHeading = createBookText("h4", "", "Topics covered");
      const printHeading = createBookText("h4", "", "Printing note");
      const printNote = createBookText("p", "", book.printableContent);
      const legalHeading = createBookText("h4", "", "Source and rights");
      const legalNote = createBookText("p", "", book.legal);
      const actions = document.createElement("div");
      const readButton = createBookText("button", "button", "Read Summary");

      grid.className = "book-detail-grid";
      metaList.className = "book-detail-list";
      actions.className = "book-actions";
      readButton.type = "button";
      readButton.addEventListener("click", () => openBookReader(book.id));

      [
        ["Author", book.author],
        ["Publication year", book.year],
        ["Edition", book.edition],
        ["Skill level", book.level],
        ["Source", book.sourceName]
      ].forEach(([label, value]) => {
        metaList.append(createBookText("dt", "", label), createBookText("dd", "", value));
      });

      const sourceTerm = createBookText("dt", "", "Source URL");
      const sourceValue = document.createElement("dd");
      const sourceUrl = document.createElement("a");
      sourceUrl.href = book.sourceUrl;
      sourceUrl.target = "_blank";
      sourceUrl.rel = "noopener";
      sourceUrl.textContent = book.sourceUrl;
      sourceValue.appendChild(sourceUrl);
      metaList.append(sourceTerm, sourceValue);

      actions.append(readButton, createBookSourceLink(book, "Download / View"), createBookText("button", "button secondary", "Print"));
      actions.lastElementChild.type = "button";
      actions.lastElementChild.addEventListener("click", () => window.print());

      metaPanel.append(badge, title, metaList);
      copyPanel.append(
        summary,
        useHeading,
        useNote,
        keyHeading,
        createBookTopicList(book.importantDetails || []),
        topicsHeading,
        createBookTopicList(book.topics || []),
        printHeading,
        printNote,
        legalHeading,
        legalNote,
        actions
      );
      grid.append(metaPanel, copyPanel);
      detail.appendChild(grid);

      document.querySelectorAll("[data-book-card]").forEach((card) => {
        card.classList.toggle("is-selected", card.dataset.bookCard === book.id);
      });

      if (shouldScroll) {
        detail.scrollIntoView({ behavior: "smooth", block: "nearest" });
      }
    }

    function readBookReaderState() {
      const fallback = {
        lastBookId: "",
        lastChapter: 0,
        bookmarks: {},
        theme: "light",
        fontScale: 1.08
      };
      const state = readJsonStorage(bookReaderStorageKey, fallback);
      return {
        ...fallback,
        ...state,
        bookmarks: state && typeof state.bookmarks === "object" ? state.bookmarks : {}
      };
    }

    function saveBookReaderState(partial) {
      const current = readBookReaderState();
      writeJsonStorage(bookReaderStorageKey, {
        ...current,
        ...partial,
        fontScale: Number(partial.fontScale ?? current.fontScale) || 1.08
      });
    }

    function getBookChapters(book) {
      return [
        {
          title: "Fast summary",
          intro: book.summary,
          bullets: book.importantDetails || []
        },
        {
          title: "How to use this book",
          intro: book.bestUse || "Read the key ideas, then open the legal source when you want the full text.",
          bullets: [
            `Skill level: ${book.level}`,
            `Best topics: ${(book.topics || []).join(", ")}`,
            `Category: ${(book.categories || []).join(", ")}`
          ]
        },
        {
          title: "Source and rights",
          intro: book.legal,
          bullets: [
            book.printableContent,
            `Source: ${book.sourceName}`,
            book.sourceUrl
          ]
        }
      ];
    }

    function renderReaderStatus(text) {
      const status = document.getElementById("readerStatus");
      if (status) status.textContent = text;
    }

    function openBookReader(bookId, chapterIndex = null, shouldScroll = true) {
      const reader = document.getElementById("bookReader");
      const book = getAllBooks().find((item) => item.id === bookId);
      if (!reader || !book) return;

      const saved = readBookReaderState();
      const chapters = getBookChapters(book);
      const requestedChapter = chapterIndex === null
        ? (saved.lastBookId === bookId ? Number(saved.lastChapter) || 0 : 0)
        : Number(chapterIndex);

      activeReaderBookId = bookId;
      activeReaderChapter = Math.max(0, Math.min(chapters.length - 1, requestedChapter));
      readerTheme = saved.theme === "dark" ? "dark" : "light";
      readerFontScale = Math.max(0.95, Math.min(1.45, Number(saved.fontScale) || 1.08));
      saveBookReaderState({
        lastBookId: activeReaderBookId,
        lastChapter: activeReaderChapter,
        theme: readerTheme,
        fontScale: readerFontScale
      });

      renderBookReader();
      if (window.history?.replaceState) {
        window.history.replaceState(null, "", `#book-${book.id}`);
      }
      if (shouldScroll) {
        reader.scrollIntoView({ behavior: "smooth", block: "start" });
      }
    }

    function renderBookReader() {
      const reader = document.getElementById("bookReader");
      const book = getAllBooks().find((item) => item.id === activeReaderBookId);
      if (!reader || !book) return;

      const chapters = getBookChapters(book);
      const chapter = chapters[activeReaderChapter] || chapters[0];
      const state = readBookReaderState();
      const bookmarkedChapter = state.bookmarks?.[book.id];
      const isBookmarked = Number(bookmarkedChapter) === activeReaderChapter;

      reader.innerHTML = "";
      reader.hidden = false;
      reader.dataset.readerBook = book.id;

      const toolbar = document.createElement("div");
      const titleWrap = document.createElement("div");
      const controls = document.createElement("div");
      const heading = createBookText("h3", "", book.title);
      const subheading = createBookText("p", "", `${book.author} • Chapter ${activeReaderChapter + 1} of ${chapters.length}`);
      const themeButton = createBookText("button", "button secondary", readerTheme === "dark" ? "Light Mode" : "Dark Mode");
      const bookmarkButton = createBookText("button", "button secondary", isBookmarked ? "Bookmarked" : "Bookmark Page");
      const closeButton = createBookText("button", "button secondary", "Close Reader");
      const fontLabel = document.createElement("label");
      const fontRange = document.createElement("input");
      const layout = document.createElement("div");
      const toc = document.createElement("aside");
      const tocTitle = createBookText("h4", "", "Contents");
      const tocList = document.createElement("div");
      const page = document.createElement("div");
      const pageTitle = createBookText("h4", "", chapter.title);
      const intro = createBookText("p", "", chapter.intro);
      const bulletList = document.createElement("ul");
      const nav = document.createElement("div");
      const previousButton = createBookText("button", "button secondary", "Previous Chapter");
      const nextButton = createBookText("button", "button", "Next Chapter");
      const sourceLink = createBookSourceLink(book, "Open Full Source");
      const status = createBookText("p", "reader-status", "Progress saved.");

      toolbar.className = "reader-toolbar";
      titleWrap.className = "reader-title";
      controls.className = "reader-controls";
      fontLabel.className = "reader-font-control";
      layout.className = "reader-layout";
      toc.className = "reader-toc";
      tocList.className = "reader-toc-list";
      page.className = `reader-page${readerTheme === "dark" ? " dark" : ""}`;
      page.style.fontSize = `${readerFontScale}rem`;
      nav.className = "reader-nav";
      status.id = "readerStatus";

      themeButton.type = "button";
      bookmarkButton.type = "button";
      closeButton.type = "button";
      previousButton.type = "button";
      nextButton.type = "button";
      previousButton.disabled = activeReaderChapter === 0;
      nextButton.disabled = activeReaderChapter >= chapters.length - 1;

      fontRange.type = "range";
      fontRange.min = "95";
      fontRange.max = "145";
      fontRange.step = "5";
      fontRange.value = String(Math.round(readerFontScale * 100));
      fontLabel.append(createBookText("span", "", "Text"), fontRange);

      chapters.forEach((item, index) => {
        const button = createBookText("button", "reader-toc-button", item.title);
        button.type = "button";
        button.setAttribute("aria-current", String(index === activeReaderChapter));
        button.addEventListener("click", () => openBookReader(book.id, index, false));
        tocList.appendChild(button);
      });

      (chapter.bullets || []).forEach((item) => bulletList.appendChild(createBookText("li", "", item)));

      themeButton.addEventListener("click", () => {
        readerTheme = readerTheme === "dark" ? "light" : "dark";
        saveBookReaderState({ theme: readerTheme });
        renderBookReader();
      });

      fontRange.addEventListener("input", () => {
        readerFontScale = Number(fontRange.value) / 100;
        saveBookReaderState({ fontScale: readerFontScale });
        page.style.fontSize = `${readerFontScale}rem`;
      });

      bookmarkButton.addEventListener("click", () => {
        const nextState = readBookReaderState();
        nextState.bookmarks = nextState.bookmarks || {};
        nextState.bookmarks[book.id] = activeReaderChapter;
        writeJsonStorage(bookReaderStorageKey, nextState);
        bookmarkButton.textContent = "Bookmarked";
        renderReaderStatus("Bookmark saved. Continue Reading will bring you back here.");
      });

      closeButton.addEventListener("click", () => {
        reader.hidden = true;
      });

      previousButton.addEventListener("click", () => openBookReader(book.id, activeReaderChapter - 1, false));
      nextButton.addEventListener("click", () => openBookReader(book.id, activeReaderChapter + 1, false));

      titleWrap.append(heading, subheading);
      controls.append(themeButton, fontLabel, bookmarkButton, closeButton);
      toolbar.append(titleWrap, controls);
      toc.append(tocTitle, tocList);
      nav.append(previousButton, nextButton, sourceLink);
      page.append(pageTitle, intro, bulletList, nav, status);
      layout.append(toc, page);
      reader.append(toolbar, layout);
    }

    function renderBooks() {
      const grid = document.getElementById("bookGrid");
      const searchInput = document.getElementById("bookSearch");
      const detail = document.getElementById("bookDetail");
      const reader = document.getElementById("bookReader");
      if (!grid || !searchInput) return;

      const allBooks = getAllBooks();
      const query = searchInput.value.trim().toLowerCase();
      const filteredBooks = allBooks.filter((book) => (
        (activeBookLevel === "all" || book.level === activeBookLevel)
        && bookMatchesCategory(book)
        && bookMatchesSearch(book, query)
      ));
      const totalStat = document.querySelector("#books .book-stat strong");
      if (totalStat) totalStat.textContent = String(allBooks.length);

      grid.innerHTML = "";

      if (!filteredBooks.length) {
        const empty = createBookText("p", "book-empty", "No legal free book matched that search. Try a broader topic like strategy, tactics, endgames, or openings.");
        grid.appendChild(empty);
        if (detail) detail.hidden = true;
        if (reader) reader.hidden = true;
        return;
      }

      const levelsToRender = activeBookLevel === "all" ? bookLevels : [activeBookLevel];
      levelsToRender.forEach((levelName) => {
        const levelBooks = filteredBooks.filter((book) => book.level === levelName);
        if (!levelBooks.length) return;

        const section = document.createElement("section");
        const head = document.createElement("div");
        const copy = document.createElement("div");
        const title = createBookText("h3", "", `${levelName} shelf`);
        const note = createBookText("p", "", bookLevelNotes[levelName] || "");
        const count = createBookText("span", "", `${levelBooks.length} ${levelBooks.length === 1 ? "book" : "books"}`);
        const list = document.createElement("div");

        section.className = "book-level-section";
        head.className = "book-level-head";
        list.className = "book-level-grid";

        copy.append(title, note);
        head.append(copy, count);
        levelBooks.forEach((book) => list.appendChild(createBookCard(book)));
        section.append(head, list);
        grid.appendChild(section);
      });

      const activeDetailId = detail?.dataset.bookId;
      const shouldRefreshDetail = !activeDetailId || !filteredBooks.some((book) => book.id === activeDetailId);
      if (shouldRefreshDetail) {
        showBookDetail(filteredBooks[0].id, false);
      } else {
        showBookDetail(activeDetailId, false);
      }
    }

    function renderAdminBookList() {
      const list = document.getElementById("adminBookList");
      if (!list) return;

      const books = readCustomBooks();
      list.innerHTML = "";

      if (!books.length) {
        list.appendChild(createBookText("p", "", "No local books yet. Add a verified free source above to test the admin flow."));
        return;
      }

      books.forEach((book) => {
        const row = document.createElement("div");
        const copy = document.createElement("div");
        const title = createBookText("strong", "", book.title);
        const meta = createBookText("span", "", `${book.level} • ${book.author}`);
        const remove = createBookText("button", "button secondary", "Remove");

        row.className = "admin-row";
        remove.type = "button";
        remove.addEventListener("click", () => {
          saveCustomBooks(readCustomBooks().filter((item) => item.id !== book.id));
          renderAdminBookList();
          renderBooks();
        });

        copy.append(title, document.createElement("br"), meta);
        row.append(copy, remove);
        list.appendChild(row);
      });
    }

    function setupBookAdmin() {
      const form = document.getElementById("bookAdminForm");
      const clearButton = document.getElementById("clearLocalBooks");
      if (!form) return;

      form.addEventListener("submit", (event) => {
        event.preventDefault();

        const title = document.getElementById("adminTitle").value.trim();
        const author = document.getElementById("adminAuthor").value.trim();
        const level = document.getElementById("adminLevel").value;
        const category = document.getElementById("adminCategory").value;
        const sourceUrl = document.getElementById("adminSource").value.trim();
        const summary = document.getElementById("adminSummary").value.trim();
        const fileInput = document.getElementById("adminFile");
        const fileName = fileInput?.files?.[0]?.name || "";

        if (!title || !author || !summary) return;

        try {
          const parsed = new URL(sourceUrl);
          if (!/^https?:$/.test(parsed.protocol)) throw new Error("Only web sources are allowed.");
        } catch {
          alert("Please enter a valid public-domain or rights-holder source URL.");
          return;
        }

        const customBook = {
          id: `local-${Date.now()}-${slugify(title)}`,
          title,
          author,
          year: "Local sample",
          edition: fileName ? `Local admin demo record: ${fileName}` : "Local admin demo record",
          level,
          categories: [category],
          topics: [category, "Local sample", "Reader demo"],
          summary,
          bestUse: "Use this local record as a reading shortcut, then verify the source before sharing it publicly.",
          importantDetails: [
            "This book was added locally in this browser.",
            "Verify copyright status before publishing or distributing files.",
            "Open the source link for the complete book."
          ],
          printableContent: "The reader prints this summary and metadata. Print full book content from the verified source.",
          sourceName: "Local admin sample",
          sourceUrl,
          legal: "Local sample only. Confirm this is public domain or legally distributed by the rights holder before publishing."
        };

        saveCustomBooks([...readCustomBooks(), customBook]);
        form.reset();
        renderAdminBookList();
        renderBooks();
        openBookReader(customBook.id);
      });

      clearButton?.addEventListener("click", () => {
        saveCustomBooks([]);
        renderAdminBookList();
        renderBooks();
      });

      renderAdminBookList();
    }

    function setupBooks() {
      const searchInput = document.getElementById("bookSearch");
      const filterButtons = document.querySelectorAll("[data-book-level]");
      const categoryButtons = document.querySelectorAll("[data-book-category]");
      const printButton = document.getElementById("printBooks");
      const continueButton = document.getElementById("continueReadingBook");
      if (!searchInput) return;

      searchInput.addEventListener("input", renderBooks);
      filterButtons.forEach((button) => {
        button.addEventListener("click", () => {
          activeBookLevel = button.dataset.bookLevel || "all";
          filterButtons.forEach((item) => {
            item.setAttribute("aria-pressed", String(item === button));
          });
          renderBooks();
        });
      });

      categoryButtons.forEach((button) => {
        button.addEventListener("click", () => {
          activeBookCategory = button.dataset.bookCategory || "all";
          categoryButtons.forEach((item) => {
            item.setAttribute("aria-pressed", String(item === button));
          });
          renderBooks();
        });
      });

      printButton?.addEventListener("click", () => window.print());
      continueButton?.addEventListener("click", () => {
        const state = readBookReaderState();
        const fallbackBook = getAllBooks()[0]?.id || "";
        const bookId = state.lastBookId || fallbackBook;
        if (bookId) openBookReader(bookId, Number(state.lastChapter) || 0);
      });
      setupBookAdmin();
      renderBooks();

      const hashBookId = window.location.hash.startsWith("#book-")
        ? window.location.hash.replace("#book-", "")
        : "";
      if (hashBookId && getAllBooks().some((book) => book.id === hashBookId)) {
        openBookReader(hashBookId, null, false);
      }
    }

    function getEmbedOrigin() {
      return /^https?:$/.test(window.location.protocol) && window.location.origin !== "null"
        ? window.location.origin
        : "https://nschess.github.io";
    }

    function getEmbedReferrer() {
      return /^https?:$/.test(window.location.protocol)
        ? window.location.href
        : "https://nschess.github.io/Nschess/";
    }

    function buildYouTubeEmbedSrc(videoId, params = {}) {
      const url = new URL(`https://www.youtube.com/embed/${videoId}`);
      Object.entries({
        rel: "0",
        modestbranding: "1",
        playsinline: "1",
        origin: getEmbedOrigin(),
        widget_referrer: getEmbedReferrer(),
        ...params
      }).forEach(([key, value]) => url.searchParams.set(key, value));
      return url.toString();
    }

    function renderShortVideos() {
      const levels = document.getElementById("shortsLevels");
      if (!levels) return;

      const videoLookup = new Map(shortVideos.map((video) => [video.id, video]));
      let runningIndex = 0;
      levels.innerHTML = "";

      function createShortCard(video) {
        const card = document.createElement("article");
        const frame = document.createElement("div");
        const iframe = document.createElement("iframe");
        const body = document.createElement("div");
        const indexBadge = document.createElement("span");
        const topicBadge = document.createElement("span");
        const creatorBadge = document.createElement("span");
        const durationBadge = document.createElement("span");
        const heading = document.createElement("h3");
        const note = document.createElement("p");

        card.className = "video-card";
        frame.className = "video-frame";
        body.className = "video-body";
        indexBadge.className = "badge";
        topicBadge.className = "badge";
        creatorBadge.className = "badge creator";
        durationBadge.className = "badge duration";

        iframe.loading = "lazy";
        iframe.src = buildYouTubeEmbedSrc(video.id);
        iframe.title = video.title;
        iframe.allow = "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen";
        iframe.referrerPolicy = "origin-when-cross-origin";
        iframe.dataset.format = "short";
        iframe.setAttribute("allowfullscreen", "");

        runningIndex += 1;
        indexBadge.textContent = `Short ${String(runningIndex).padStart(2, "0")}`;
        topicBadge.textContent = video.topic;
        creatorBadge.textContent = video.creator || "";
        durationBadge.textContent = video.duration;
        heading.textContent = video.headline;
        note.textContent = video.note;

        frame.appendChild(iframe);
        body.append(indexBadge, topicBadge);
        if (video.creator) body.appendChild(creatorBadge);
        body.append(durationBadge, heading, note);
        card.append(frame, body);
        return card;
      }

      shortLevelGroups.forEach((group) => {
        const section = document.createElement("section");
        const head = document.createElement("div");
        const copy = document.createElement("div");
        const title = document.createElement("h4");
        const description = document.createElement("p");
        const badge = document.createElement("span");
        const grid = document.createElement("div");
        const videos = group.ids.map((id) => videoLookup.get(id)).filter(Boolean);

        section.className = "shorts-level";
        head.className = "shorts-level-head";
        badge.className = "shorts-level-badge";
        grid.className = "video-grid tier-grid shorts-grid";

        title.textContent = group.title;
        description.textContent = group.description;
        badge.textContent = `${group.tag} · ${videos.length}`;
        grid.setAttribute("aria-label", group.title);

        copy.append(title, description);
        head.append(copy, badge);
        videos.forEach((video) => grid.appendChild(createShortCard(video)));
        section.append(head, grid);
        levels.appendChild(section);
      });
    }

    function renderShortFeed() {
      const feed = document.getElementById("shortsLevels");
      if (!feed) return;

      const videoLookup = new Map(shortVideos.map((video) => [video.id, video]));
      const orderedShorts = [];
      feed.innerHTML = "";
      feed.className = "shorts-feed";

      shortLevelGroups.forEach((group) => {
        const videos = group.ids.map((id) => videoLookup.get(id)).filter(Boolean);
        videos.forEach((video, levelIndex) => {
          orderedShorts.push({
            video,
            level: group.title,
            difficulty: shortDifficultyFromLevel(group.title),
            categoryTags: shortCategoryTags(video),
            levelTag: group.tag,
            levelIndex: levelIndex + 1,
            levelTotal: videos.length
          });
        });
      });

      function createPill(text, extraClass = "") {
        const pill = document.createElement("span");
        pill.className = `short-pill${extraClass ? ` ${extraClass}` : ""}`;
        pill.textContent = text;
        return pill;
      }

      function createActionButton(action, icon, label, pressed = false) {
        const button = document.createElement("button");
        button.className = `short-action-button short-${action}`;
        button.type = "button";
        button.dataset.shortAction = action;
        button.textContent = icon;
        button.title = label;
        button.setAttribute("aria-label", label);
        if (pressed) button.setAttribute("aria-pressed", "false");
        return button;
      }

      orderedShorts.forEach((item, index) => {
        const { video } = item;
        const slide = document.createElement("article");
        const stage = document.createElement("div");
        const frame = document.createElement("div");
        const placeholder = document.createElement("div");
        const gestureLayer = document.createElement("div");
        const position = document.createElement("span");
        const actions = document.createElement("div");
        const fullscreenButton = createActionButton("fullscreen", "\u26F6", "Fullscreen");
        const completeButton = createActionButton("complete", "\u2713", "Mark lesson completed", true);
        const likeButton = createActionButton("like", "\u2665", "Like lesson", true);
        const bookmarkButton = createActionButton("bookmark", "\u2605", "Bookmark lesson", true);
        const shareButton = createActionButton("share", "\u21AA", "Share lesson");
        const meta = document.createElement("div");
        const pills = document.createElement("div");
        const heading = document.createElement("h4");
        const note = document.createElement("p");

        slide.className = "short-slide";
        slide.id = `short-${video.id}`;
        slide.dataset.index = String(index);
        slide.dataset.videoId = video.id;
        slide.dataset.title = video.title;
        slide.dataset.level = item.level;
        slide.dataset.difficulty = item.difficulty;
        slide.dataset.category = item.categoryTags.join(" ");
        slide.dataset.creator = video.creator || "";
        stage.className = "short-stage";
        frame.className = "short-frame";
        placeholder.className = "short-placeholder";
        gestureLayer.className = "short-gesture-layer";
        gestureLayer.setAttribute("aria-hidden", "true");
        position.className = "short-position";
        actions.className = "short-actions";
        fullscreenButton.classList.add("short-fullscreen");
        fullscreenButton.setAttribute("aria-label", `Open ${video.headline} fullscreen`);
        meta.className = "short-meta";
        pills.className = "short-pill-row";

        placeholder.style.backgroundImage = `url("https://i.ytimg.com/vi/${video.id}/hqdefault.jpg")`;
        placeholder.innerHTML = '<span class="play-mark" aria-hidden="true"></span>';
        position.textContent = `${index + 1} / ${orderedShorts.length}`;
        pills.append(
          createPill(item.difficulty, "difficulty"),
          createPill(`${item.levelTag} ${item.levelIndex}/${item.levelTotal}`),
          createPill(video.duration)
        );
        item.categoryTags.forEach((tag) => pills.appendChild(createPill(tag, "category")));
        if (video.creator) pills.appendChild(createPill(video.creator, "creator"));
        heading.textContent = video.headline;
        note.textContent = video.note;

        frame.appendChild(placeholder);
        actions.append(fullscreenButton, completeButton, likeButton, bookmarkButton, shareButton);
        meta.append(pills, heading, note);
        stage.append(frame, gestureLayer, position, actions, meta);
        slide.appendChild(stage);
        feed.appendChild(slide);
      });

      setupShortsFeed(feed, orderedShorts);
    }

    function setupShortsFeed(feed, orderedShorts) {
      const slides = [...feed.querySelectorAll(".short-slide")];
      const levelTabs = [...document.querySelectorAll("[data-shorts-level], [data-shorts-creator]")];
      const soundToggle = document.getElementById("shortsSoundToggle");
      const volumeRange = document.getElementById("shortsVolumeRange");
      const resumeButton = document.getElementById("shortsResumeButton");
      const progressBadge = document.getElementById("shortsProgress");
      const storedLessonState = readShortLessonState();
      const validVideoIds = new Set(slides.map((slide) => slide.dataset.videoId));
      const completedLessons = new Set((storedLessonState.completed || []).filter((id) => validVideoIds.has(id)));
      const likedLessons = new Set((storedLessonState.liked || []).filter((id) => validVideoIds.has(id)));
      const bookmarkedLessons = new Set((storedLessonState.bookmarked || []).filter((id) => validVideoIds.has(id)));
      let activeIndex = getInitialShortIndex();
      let feedInView = false;
      let shortsMuted = true;
      let shortsVolume = Number(volumeRange?.value || 80);
      let touchStartY = 0;
      let scrollStepLocked = false;
      let lastScrollTop = feed.scrollTop;
      let lastScrollDirection = 1;
      let scrollWarmFrame = 0;
      let trimTimer = 0;
      let preloadTimer = 0;
      let preloadRunId = 0;
      let playTimer = 0;
      let lastPlayCommandAt = 0;
      let playerLoadSeq = 0;
      let fastScrollingUntil = 0;
      let activeShortFilter = "all";
      let activeShortLevelFilter = "";
      const compactShortFeed = window.matchMedia("(pointer: coarse), (max-width: 760px)").matches;
      const prefersReducedMotion = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
      const maxLoadedPlayers = compactShortFeed ? 4 : 5;
      const trimDelay = compactShortFeed ? 140 : 180;
      const preloadDelay = compactShortFeed ? 45 : 35;
      const scrollStepDelay = compactShortFeed ? 115 : 95;
      const recentShortIndexes = [];

      function normalizeIndex(index) {
        if (!slides.length) return 0;
        return ((index % slides.length) + slides.length) % slides.length;
      }

      function clampPhysicalIndex(index) {
        if (!slides.length) return 0;
        return Math.max(0, Math.min(slides.length - 1, index));
      }

      function circularDistance(a, b) {
        if (!slides.length) return 0;

        const distance = Math.abs(normalizeIndex(a) - normalizeIndex(b));
        return Math.min(distance, slides.length - distance);
      }

      function loadedPlayerCount() {
        return feed.querySelectorAll(".short-frame iframe").length;
      }

      function hasActiveShortFilter() {
        return activeShortFilter !== "all" || Boolean(activeShortLevelFilter);
      }

      function slideMatchesFilter(slide) {
        if (activeShortFilter !== "all") {
          return slide.dataset.creator === activeShortFilter;
        }

        return !activeShortLevelFilter || slide.dataset.level === activeShortLevelFilter;
      }

      function getNavigableIndexes() {
        return slides
          .map((slide, index) => slideMatchesFilter(slide) ? index : -1)
          .filter((index) => index >= 0);
      }

      function getNearestNavigableIndex(index, direction = 1) {
        const navigable = getNavigableIndexes();
        if (!navigable.length) return normalizeIndex(index);

        const normalized = normalizeIndex(index);
        if (navigable.includes(normalized)) return normalized;

        const sorted = direction >= 0 ? navigable : [...navigable].reverse();
        return sorted.find((candidate) => direction >= 0 ? candidate > normalized : candidate < normalized)
          ?? sorted[0];
      }

      function getRelativeNavigableIndex(index, direction) {
        const navigable = getNavigableIndexes();
        if (!navigable.length) return normalizeIndex(index + direction);

        const normalized = getNearestNavigableIndex(index, direction);
        const currentPosition = navigable.indexOf(normalized);
        if (currentPosition < 0) return navigable[0];

        return navigable[(currentPosition + direction + navigable.length) % navigable.length];
      }

      function getNearestScrollIndex() {
        const navigable = getNavigableIndexes();
        const candidates = navigable.length ? navigable : slides.map((_, index) => index);
        const currentTop = feed.scrollTop;

        return candidates.reduce((best, candidate) => (
          Math.abs(slides[candidate].offsetTop - currentTop) < Math.abs(slides[best].offsetTop - currentTop)
            ? candidate
            : best
        ), candidates[0] || 0);
      }

      function getInitialShortIndex() {
        const hashId = window.location.hash.startsWith("#short-")
          ? window.location.hash.replace("#short-", "")
          : "";
        const hashIndex = slides.findIndex((slide) => slide.dataset.videoId === hashId);
        if (hashIndex >= 0) return hashIndex;

        const savedIdIndex = slides.findIndex((slide) => slide.dataset.videoId === storedLessonState.lastVideoId);
        if (savedIdIndex >= 0) return savedIdIndex;

        return normalizeIndex(Number(storedLessonState.lastIndex) || 0);
      }

      function persistLessonState() {
        saveShortLessonState({
          completed: completedLessons,
          liked: likedLessons,
          bookmarked: bookmarkedLessons,
          lastVideoId: slides[activeIndex]?.dataset.videoId || "",
          lastIndex: activeIndex
        });
      }

      function buildShortFeedSrc(videoId) {
        return buildYouTubeEmbedSrc(videoId, {
          enablejsapi: "1",
          controls: "1",
          fs: "0",
          autoplay: "1",
          mute: "1"
        });
      }

      function createPlaceholder(video) {
        const placeholder = document.createElement("div");
        placeholder.className = "short-placeholder";
        placeholder.style.backgroundImage = `url("https://i.ytimg.com/vi/${video.id}/hqdefault.jpg")`;
        placeholder.innerHTML = '<span class="play-mark" aria-hidden="true"></span>';
        return placeholder;
      }

      function postPlayerCommand(iframe, func, args = []) {
        iframe?.contentWindow?.postMessage(JSON.stringify({
          event: "command",
          func,
          args
        }), "*");
      }

      function registerStateEvents(iframe) {
        postPlayerCommand(iframe, "addEventListener", ["onStateChange"]);
      }

      function updateSoundToggle() {
        if (!soundToggle) return;

        soundToggle.textContent = shortsMuted ? "Sound Off" : "Sound On";
        soundToggle.setAttribute("aria-pressed", String(!shortsMuted));
        soundToggle.setAttribute("aria-label", shortsMuted ? "Turn Shorts sound on" : "Turn Shorts sound off");
        if (volumeRange) volumeRange.setAttribute("aria-valuetext", `${shortsVolume}%`);
      }

      function applySoundPreference(iframe, shouldUnmute = false) {
        if (!iframe) return;

        postPlayerCommand(iframe, "setVolume", [shortsVolume]);
        postPlayerCommand(iframe, shouldUnmute ? "unMute" : "mute");
      }

      function applySoundToLoadedPlayers() {
        slides.forEach((slide, index) => {
          applySoundPreference(slide.querySelector(".short-frame iframe"), !shortsMuted && index === activeIndex);
        });
      }

      function updateLevelTabs(level) {
        levelTabs.forEach((tab) => {
          const selected = activeShortFilter !== "all"
            ? tab.dataset.shortsCreator === activeShortFilter
            : tab.dataset.shortsLevel === (activeShortLevelFilter || level);
          tab.setAttribute("aria-selected", String(selected));
        });
      }

      function applyShortFilter(filter = "all", level = "") {
        activeShortFilter = filter;
        activeShortLevelFilter = filter === "all" ? level : "";
        slides.forEach((slide, index) => {
          const visible = slideMatchesFilter(slide);
          slide.classList.toggle("is-filtered-out", !visible);
          if (!visible) releasePlayer(index);
        });
      }

      function updateActionButton(button, active, activeLabel, inactiveLabel) {
        if (!button) return;

        button.setAttribute("aria-pressed", String(active));
        button.setAttribute("aria-label", active ? activeLabel : inactiveLabel);
        button.title = active ? activeLabel : inactiveLabel;
      }

      function updateSlideLessonState(slide) {
        const id = slide.dataset.videoId;
        const title = slide.querySelector(".short-meta h4")?.textContent || slide.dataset.title || "lesson";
        const completed = completedLessons.has(id);
        const liked = likedLessons.has(id);
        const bookmarked = bookmarkedLessons.has(id);

        slide.classList.toggle("is-completed", completed);
        updateActionButton(
          slide.querySelector('[data-short-action="complete"]'),
          completed,
          `Mark ${title} incomplete`,
          `Mark ${title} completed`
        );
        updateActionButton(
          slide.querySelector('[data-short-action="like"]'),
          liked,
          `Unlike ${title}`,
          `Like ${title}`
        );
        updateActionButton(
          slide.querySelector('[data-short-action="bookmark"]'),
          bookmarked,
          `Remove bookmark from ${title}`,
          `Bookmark ${title}`
        );
      }

      function updateLessonProgress() {
        if (progressBadge) {
          progressBadge.textContent = `${completedLessons.size}/${slides.length} Done`;
        }

        if (resumeButton) {
          const title = slides[activeIndex]?.querySelector(".short-meta h4")?.textContent || "last lesson";
          resumeButton.textContent = `Resume ${activeIndex + 1}/${slides.length}`;
          resumeButton.setAttribute("aria-label", `Resume ${title}`);
        }
      }

      function refreshLessonState() {
        slides.forEach(updateSlideLessonState);
        updateLessonProgress();
      }

      function setLessonState(set, id, shouldAdd) {
        if (shouldAdd) {
          set.add(id);
        } else {
          set.delete(id);
        }
      }

      function markLessonCompleted(index, shouldComplete = true) {
        const slide = slides[normalizeIndex(index)];
        if (!slide) return;

        setLessonState(completedLessons, slide.dataset.videoId, shouldComplete);
        persistLessonState();
        refreshLessonState();
        renderBeginnerProgress();
      }

      function toggleLessonAction(button) {
        const slide = button.closest(".short-slide");
        if (!slide) return;

        const id = slide.dataset.videoId;
        const action = button.dataset.shortAction;
        const stateMap = {
          complete: completedLessons,
          like: likedLessons,
          bookmark: bookmarkedLessons
        };
        const targetSet = stateMap[action];
        if (!targetSet) return;

        setLessonState(targetSet, id, !targetSet.has(id));
        persistLessonState();
        refreshLessonState();
        if (action === "complete") renderBeginnerProgress();
      }

      function ensurePlayer(index, priority = "warm") {
        index = normalizeIndex(index);
        const slide = slides[index];
        const item = orderedShorts[index];
        if (!slide || !item) return null;

        const frame = slide.querySelector(".short-frame");
        const existing = frame.querySelector("iframe");
        if (existing) return existing;

        const iframe = document.createElement("iframe");
        const loadId = String(++playerLoadSeq);
        const closeToActive = circularDistance(index, activeIndex) <= 1;
        slide.dataset.loadId = loadId;
        iframe.dataset.loadId = loadId;
        iframe.loading = priority === "warm" ? "lazy" : "eager";
        iframe.fetchPriority = priority === "active" || closeToActive ? "high" : "low";
        iframe.src = buildShortFeedSrc(item.video.id);
        iframe.title = item.video.title;
        iframe.allow = "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen";
        iframe.allowFullscreen = true;
        iframe.referrerPolicy = "origin-when-cross-origin";
        iframe.dataset.preloadPriority = priority;
        iframe.setAttribute("allowfullscreen", "");
        iframe.addEventListener("load", () => {
          if (!iframe.isConnected || slide.dataset.loadId !== loadId) return;

          registerStateEvents(iframe);
          applySoundPreference(iframe, !shortsMuted && index === activeIndex);
          slide.classList.remove("is-loading");
          slide.classList.add("is-loaded");
          slide.dataset.playerState = "loaded";
          if ((feedInView || isShortFeedFullscreen()) && index === activeIndex) {
            window.setTimeout(() => postPlayerCommand(iframe, "playVideo"), 15);
          }
        });

        frame.replaceChildren(createPlaceholder(item.video), iframe);
        slide.classList.add("is-loading");
        slide.classList.remove("is-loaded", "is-virtualized");
        return iframe;
      }

      function pauseSlide(index) {
        const iframe = slides[index]?.querySelector(".short-frame iframe");
        if (iframe) {
          applySoundPreference(iframe, false);
          postPlayerCommand(iframe, "pauseVideo");
          slides[index].dataset.playerState = "2";
        }
      }

      function releasePlayer(slideIndex) {
        const slide = slides[slideIndex];
        const item = orderedShorts[slideIndex];
        const frame = slide?.querySelector(".short-frame");
        const iframe = frame?.querySelector("iframe");
        if (!slide || !item || !frame || !iframe) return;

        postPlayerCommand(iframe, "pauseVideo");
        postPlayerCommand(iframe, "stopVideo");
        delete slide.dataset.loadId;
        delete slide.dataset.playerState;
        iframe.src = "about:blank";
        frame.replaceChildren(createPlaceholder(item.video));
        slide.classList.remove("is-loaded", "is-loading");
        slide.classList.add("is-virtualized");
      }

      function playSlide(index) {
        const targetIndex = normalizeIndex(index);
        const iframe = ensurePlayer(targetIndex, "active");
        if (!iframe || (!feedInView && !isShortFeedFullscreen())) return;

        applySoundToLoadedPlayers();
        const now = Date.now();
        if (targetIndex === activeIndex && now - lastPlayCommandAt < 90) return;
        lastPlayCommandAt = now;
        window.clearTimeout(playTimer);
        playTimer = window.setTimeout(() => {
          if (targetIndex === activeIndex) {
            postPlayerCommand(iframe, "playVideo");
            slides[targetIndex].dataset.playerState = "1";
          }
        }, 10);
      }

      function toggleSlidePlayback(index = activeIndex) {
        const targetIndex = normalizeIndex(index);
        const slide = slides[targetIndex];
        const iframe = ensurePlayer(targetIndex, "active");
        if (!slide || !iframe) return;

        if (targetIndex !== activeIndex) {
          setActive(targetIndex);
          return;
        }

        if (slide.dataset.playerState === "1") {
          pauseSlide(targetIndex);
        } else {
          playSlide(targetIndex);
        }
      }

      function trimPlayers(index, direction = lastScrollDirection) {
        const keepIndexes = new Set(getKeepIndexes(index, direction));

        slides.forEach((slide, slideIndex) => {
          const shouldKeep = keepIndexes.has(slideIndex);
          const iframe = slide.querySelector(".short-frame iframe");
          if (shouldKeep || !iframe) return;

          releasePlayer(slideIndex);
        });
      }

      function getPreloadIndexes(index, direction = lastScrollDirection) {
        const active = hasActiveShortFilter()
          ? getNearestNavigableIndex(index, direction)
          : normalizeIndex(index);

        if (hasActiveShortFilter()) {
          const nextOne = getRelativeNavigableIndex(active, direction);
          const nextTwo = getRelativeNavigableIndex(nextOne, direction);
          const previousOne = getRelativeNavigableIndex(active, -direction);
          return compactShortFeed
            ? [...new Set([active, nextOne, previousOne])]
            : [...new Set([active, nextOne, nextTwo, previousOne])];
        }

        const offsets = compactShortFeed
          ? [0, direction, -direction]
          : [0, direction, direction * 2, -direction];
        return [...new Set(offsets.map((offset) => normalizeIndex(active + offset)))];
      }

      function getKeepIndexes(index, direction = lastScrollDirection) {
        return [...new Set([...getPreloadIndexes(index, direction), ...recentShortIndexes])];
      }

      function rememberRecentShort(index) {
        const normalized = normalizeIndex(index);
        const existing = recentShortIndexes.indexOf(normalized);
        if (existing >= 0) recentShortIndexes.splice(existing, 1);
        recentShortIndexes.unshift(normalized);
        recentShortIndexes.splice(compactShortFeed ? 1 : 2);
      }

      function scheduleTrim(index, direction = lastScrollDirection) {
        window.clearTimeout(trimTimer);

        if (loadedPlayerCount() > maxLoadedPlayers) {
          trimPlayers(index, direction);
          return;
        }

        trimTimer = window.setTimeout(() => {
          trimPlayers(index, direction);
        }, Date.now() < fastScrollingUntil ? 0 : trimDelay);
      }

      function preloadWindow(index, direction = lastScrollDirection) {
        const targetIndex = normalizeIndex(index);
        const runId = ++preloadRunId;
        const preloadIndexes = getPreloadIndexes(targetIndex, direction);
        const immediateIndex = hasActiveShortFilter()
          ? getNearestNavigableIndex(targetIndex, direction)
          : targetIndex;

        window.clearTimeout(preloadTimer);
        ensurePlayer(immediateIndex, immediateIndex === activeIndex ? "active" : "near");
        scheduleTrim(targetIndex, direction);

        if (Date.now() < fastScrollingUntil) {
          preloadIndexes
            .filter((candidate) => candidate !== immediateIndex)
            .slice(0, 1)
            .forEach((candidate) => ensurePlayer(candidate, "near"));
          scheduleTrim(targetIndex, direction);
          return;
        }

        preloadTimer = window.setTimeout(() => {
          if (runId !== preloadRunId || Date.now() < fastScrollingUntil) return;

          preloadIndexes
            .filter((candidate) => candidate !== immediateIndex)
            .slice(0, compactShortFeed ? 2 : 3)
            .forEach((candidate, preloadIndex) => ensurePlayer(candidate, preloadIndex === 0 ? "near" : "warm"));
          scheduleTrim(targetIndex, direction);
        }, preloadDelay);
      }

      async function requestFullscreenFor(element) {
        if (!element) return false;

        const request = element.requestFullscreen
          || element.webkitRequestFullscreen
          || element.msRequestFullscreen;
        if (!request) return false;

        try {
          if (element.requestFullscreen) {
            await element.requestFullscreen({ navigationUI: "hide" });
          } else {
            await request.call(element);
          }
          return true;
        } catch {
          return false;
        }
      }

      function lockPortraitIfPossible() {
        try {
          const lock = screen.orientation?.lock?.("portrait");
          if (lock?.catch) lock.catch(() => {});
        } catch {
          // Orientation locking is optional; the 9:16 layout still stays vertical.
        }
      }

      function unlockPortraitIfPossible() {
        try {
          screen.orientation?.unlock?.();
        } catch {
          // Some browsers do not expose orientation unlock.
        }
      }

      function isShortFeedFullscreen() {
        return document.fullscreenElement === feed
          || document.webkitFullscreenElement === feed
          || feed.classList.contains("is-feed-fullscreen");
      }

      function updateFullscreenButtons() {
        const active = isShortFeedFullscreen();
        feed.querySelectorAll('[data-short-action="fullscreen"]').forEach((button) => {
          button.setAttribute("aria-pressed", String(active));
          button.setAttribute("aria-label", active ? "Exit fullscreen Shorts feed" : "Open Shorts feed fullscreen");
          button.title = active ? "Exit fullscreen" : "Fullscreen";
        });
      }

      function syncShortFullscreenState() {
        const active = isShortFeedFullscreen();
        document.body.classList.toggle("short-feed-locked", active);
        if (!active) {
          feed.classList.remove("is-feed-fullscreen", "is-mobile-portrait-fullscreen");
          unlockPortraitIfPossible();
        }
        updateFullscreenButtons();

        if (active) {
          if (compactShortFeed) {
            feed.classList.add("is-mobile-portrait-fullscreen");
            lockPortraitIfPossible();
          }
          window.requestAnimationFrame(() => {
            scrollToShort(activeIndex, "auto");
            feed.focus({ preventScroll: true });
            playSlide(activeIndex);
          });
        }
      }

      async function exitShortFullscreen() {
        const nativeFullscreen = document.fullscreenElement === feed || document.webkitFullscreenElement === feed;

        if (document.fullscreenElement === feed && document.exitFullscreen) {
          await document.exitFullscreen();
        } else if (document.webkitFullscreenElement === feed && document.webkitExitFullscreen) {
          document.webkitExitFullscreen();
        }

        if (!nativeFullscreen || feed.classList.contains("is-feed-fullscreen")) {
          feed.classList.remove("is-feed-fullscreen", "is-mobile-portrait-fullscreen");
          syncShortFullscreenState();
        } else {
          window.setTimeout(syncShortFullscreenState, 120);
        }
      }

      async function enterShortFullscreen(button) {
        const slide = button.closest(".short-slide");
        const index = Number(slide?.dataset.index);
        if (Number.isInteger(index)) setActive(index);

        if (isShortFeedFullscreen()) {
          exitShortFullscreen();
          return;
        }

        ensurePlayer(activeIndex);
        feed.setAttribute("tabindex", "-1");

        const openedFeed = await requestFullscreenFor(feed);

        if (!openedFeed) {
          feed.classList.add("is-feed-fullscreen");
          if (compactShortFeed) feed.classList.add("is-mobile-portrait-fullscreen");
          syncShortFullscreenState();
        } else {
          if (compactShortFeed) feed.classList.add("is-mobile-portrait-fullscreen");
          syncShortFullscreenState();
        }
      }

      async function shareLesson(button) {
        const slide = button.closest(".short-slide");
        const index = normalizeIndex(Number(slide?.dataset.index) || 0);
        const item = orderedShorts[index];
        if (!slide || !item) return;

        const url = `${window.location.href.split("#")[0]}#${slide.id}`;
        const payload = {
          title: item.video.headline,
          text: item.video.note,
          url
        };

        try {
          if (navigator.share) {
            await navigator.share(payload);
          } else if (navigator.clipboard?.writeText) {
            await navigator.clipboard.writeText(`${payload.title} ${payload.url}`);
          }

          button.classList.add("is-copied");
          button.setAttribute("aria-label", "Lesson link copied");
          window.setTimeout(() => {
            button.classList.remove("is-copied");
            button.setAttribute("aria-label", `Share ${payload.title}`);
          }, 1600);
        } catch {
          button.classList.remove("is-copied");
        }
      }

      function loopFromFeedEdge(direction) {
        if (direction > 0 && activeIndex === slides.length - 1) {
          scrollToShort(0);
          return true;
        }

        if (direction < 0 && activeIndex === 0) {
          scrollToShort(slides.length - 1);
          return true;
        }

        return false;
      }

      function stepShort(direction) {
        if (!direction || scrollStepLocked) return;

        scrollStepLocked = true;
        const targetIndex = hasActiveShortFilter()
          ? getRelativeNavigableIndex(activeIndex, direction)
          : activeIndex + direction;
        preloadWindow(targetIndex, direction);
        scrollToShort(targetIndex, "auto");
        window.setTimeout(() => {
          scrollStepLocked = false;
        }, scrollStepDelay);
      }

      function setActive(index) {
        if (!slides.length) return;

        const nextIndex = normalizeIndex(index);
        if (nextIndex === activeIndex) {
          preloadWindow(activeIndex, lastScrollDirection);
          playSlide(activeIndex);
          return;
        }

        const previousIndex = activeIndex;
        lastScrollDirection = nextIndex > previousIndex ? 1 : -1;
        if (previousIndex === slides.length - 1 && nextIndex === 0) lastScrollDirection = 1;
        if (previousIndex === 0 && nextIndex === slides.length - 1) lastScrollDirection = -1;
        pauseSlide(previousIndex);
        rememberRecentShort(previousIndex);

        activeIndex = nextIndex;
        slides[previousIndex]?.classList.remove("is-active");
        slides[activeIndex]?.classList.add("is-active");
        playSlide(activeIndex);
        updateLevelTabs(slides[activeIndex]?.dataset.level || "");
        preloadWindow(activeIndex, lastScrollDirection);
        persistLessonState();
        updateLessonProgress();
      }

      function scrollToShort(index, behavior = "smooth") {
        const targetIndex = getNearestNavigableIndex(index, lastScrollDirection);
        const slide = slides[targetIndex];
        if (!slide) return;
        if (targetIndex !== activeIndex) {
          lastScrollDirection = targetIndex > activeIndex ? 1 : -1;
          if (activeIndex === slides.length - 1 && targetIndex === 0) lastScrollDirection = 1;
          if (activeIndex === 0 && targetIndex === slides.length - 1) lastScrollDirection = -1;
        }
        feed.scrollTo({
          top: slide.offsetTop,
          behavior
        });
        setActive(targetIndex);
      }

      function warmFromScrollPosition() {
        scrollWarmFrame = 0;

        const currentTop = feed.scrollTop;
        const delta = currentTop - lastScrollTop;
        const fastDelta = Math.abs(delta) > Math.max(80, feed.clientHeight * 0.38);
        if (Math.abs(delta) > 2) {
          lastScrollDirection = delta > 0 ? 1 : -1;
        }
        lastScrollTop = currentTop;

        if (fastDelta) {
          fastScrollingUntil = Date.now() + 260;
          const nearestIndex = getNearestScrollIndex();
          if (nearestIndex !== activeIndex) {
            setActive(nearestIndex);
          } else {
            ensurePlayer(nearestIndex, "active");
            playSlide(nearestIndex);
          }
          scheduleTrim(nearestIndex, lastScrollDirection);
          return;
        }

        preloadWindow(getNearestScrollIndex(), lastScrollDirection);
      }

      function scheduleScrollWarmup() {
        if (scrollWarmFrame) return;
        scrollWarmFrame = window.requestAnimationFrame(warmFromScrollPosition);
      }

      const slideObserver = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.intersectionRatio < 0.28) {
            pauseSlide(Number(entry.target.dataset.index));
          }
        });

        const strongest = entries
          .filter((entry) => entry.isIntersecting && entry.intersectionRatio >= 0.5)
          .sort((a, b) => b.intersectionRatio - a.intersectionRatio)[0];

        if (strongest) setActive(Number(strongest.target.dataset.index));
      }, {
        root: feed,
        threshold: [0, 0.28, 0.5, 0.72]
      });

      const feedObserver = new IntersectionObserver(([entry]) => {
        feedInView = entry.isIntersecting && entry.intersectionRatio > 0.26;
        if (feedInView) {
          playSlide(activeIndex);
        } else {
          pauseSlide(activeIndex);
        }
      }, {
        threshold: [0, 0.26, 0.55]
      });

      slides.forEach((slide) => slideObserver.observe(slide));
      feedObserver.observe(feed);
      applyShortFilter("all", slides[activeIndex]?.dataset.level || "");
      preloadWindow(activeIndex);
      slides[activeIndex]?.classList.add("is-active");
      updateSoundToggle();
      updateLevelTabs(slides[activeIndex]?.dataset.level || "");
      refreshLessonState();
      updateFullscreenButtons();
      window.requestAnimationFrame(() => {
        if (slides[activeIndex]) {
          feed.scrollTo({
            top: slides[activeIndex].offsetTop,
            behavior: "auto"
          });
        }
      });

      levelTabs.forEach((tab) => {
        tab.addEventListener("click", () => {
          if (tab.dataset.shortsCreator) {
            applyShortFilter(tab.dataset.shortsCreator);
            const targetIndex = slides.findIndex((slide) => slideMatchesFilter(slide));
            if (targetIndex >= 0) scrollToShort(targetIndex, "smooth");
            updateLevelTabs(slides[targetIndex]?.dataset.level || "");
            return;
          }

          applyShortFilter("all", tab.dataset.shortsLevel);
          const targetIndex = slides.findIndex((slide) => slideMatchesFilter(slide));
          if (targetIndex >= 0) scrollToShort(targetIndex, "smooth");
        });
      });

      resumeButton?.addEventListener("click", () => {
        scrollToShort(activeIndex);
      });

      feed.querySelectorAll("[data-short-action]").forEach((button) => {
        button.addEventListener("click", () => {
          const action = button.dataset.shortAction;
          if (action === "fullscreen") {
            enterShortFullscreen(button);
          } else if (action === "share") {
            shareLesson(button);
          } else {
            toggleLessonAction(button);
          }
        });
      });

      feed.querySelectorAll(".short-gesture-layer").forEach((layer) => {
        layer.addEventListener("click", (event) => {
          if (!isShortFeedFullscreen()) return;
          event.preventDefault();
          const slide = layer.closest(".short-slide");
          toggleSlidePlayback(Number(slide?.dataset.index) || activeIndex);
        });
      });

      feed.addEventListener("scroll", scheduleScrollWarmup, { passive: true });

      feed.addEventListener("wheel", (event) => {
        const direction = Math.sign(event.deltaY);
        if (isShortFeedFullscreen()) {
          if (Math.abs(event.deltaY) > 8 && direction) {
            event.preventDefault();
            stepShort(direction);
          }
          return;
        }

        const atBottom = feed.scrollTop + feed.clientHeight >= feed.scrollHeight - 4;
        const atTop = feed.scrollTop <= 4;
        const wantsNextLoop = event.deltaY > 28 && atBottom;
        const wantsPreviousLoop = event.deltaY < -28 && atTop;

        if ((wantsNextLoop && loopFromFeedEdge(1)) || (wantsPreviousLoop && loopFromFeedEdge(-1))) {
          event.preventDefault();
        }
      }, { passive: false });

      feed.addEventListener("touchstart", (event) => {
        touchStartY = event.touches[0]?.clientY || 0;
      }, { passive: true });

      feed.addEventListener("touchend", (event) => {
        const endY = event.changedTouches[0]?.clientY || touchStartY;
        const swipeDistance = touchStartY - endY;
        const atBottom = feed.scrollTop + feed.clientHeight >= feed.scrollHeight - 4;
        const atTop = feed.scrollTop <= 4;

        if (isShortFeedFullscreen() && Math.abs(swipeDistance) > 36) {
          stepShort(swipeDistance > 0 ? 1 : -1);
          return;
        }

        if (swipeDistance > 52 && atBottom) {
          loopFromFeedEdge(1);
        } else if (swipeDistance < -52 && atTop) {
          loopFromFeedEdge(-1);
        }
      }, { passive: true });

      ["fullscreenchange", "webkitfullscreenchange"].forEach((eventName) => {
        document.addEventListener(eventName, syncShortFullscreenState);
      });

      document.addEventListener("keydown", (event) => {
        if (!isShortFeedFullscreen()) return;

        const nextKeys = ["ArrowDown", "PageDown", " ", "Spacebar"];
        const previousKeys = ["ArrowUp", "PageUp"];

        if (nextKeys.includes(event.key)) {
          event.preventDefault();
          stepShort(1);
        } else if (previousKeys.includes(event.key)) {
          event.preventDefault();
          stepShort(-1);
        } else if (event.key === "Home") {
          event.preventDefault();
          scrollToShort(0);
        } else if (event.key === "End") {
          event.preventDefault();
          scrollToShort(slides.length - 1);
        } else if (event.key === "Escape" && feed.classList.contains("is-feed-fullscreen")) {
          event.preventDefault();
          exitShortFullscreen();
        }
      });

      soundToggle?.addEventListener("click", () => {
        shortsMuted = !shortsMuted;
        if (!shortsMuted && shortsVolume === 0) shortsVolume = 80;
        if (volumeRange) volumeRange.value = String(shortsVolume);
        updateSoundToggle();
        applySoundToLoadedPlayers();
        playSlide(activeIndex);
      });

      volumeRange?.addEventListener("input", () => {
        shortsVolume = Number(volumeRange.value);
        shortsMuted = shortsVolume === 0;
        updateSoundToggle();
        applySoundToLoadedPlayers();
        if (!shortsMuted) playSlide(activeIndex);
      });

      window.addEventListener("message", (event) => {
        const iframe = slides
          .map((slide) => slide.querySelector(".short-frame iframe"))
          .find((candidate) => candidate?.contentWindow === event.source);
        if (!iframe) return;

        let data = event.data;
        if (typeof data === "string") {
          try {
            data = JSON.parse(data);
          } catch {
            return;
          }
        }

        const directState = data?.event === "onStateChange" ? data.info : undefined;
        const deliveryState = data?.event === "infoDelivery" ? data.info?.playerState : undefined;
        const playerState = directState ?? deliveryState;
        const owningSlide = iframe.closest(".short-slide");
        if (typeof playerState === "number" && owningSlide) {
          owningSlide.dataset.playerState = String(playerState);
        }
        const ended = directState === 0 || deliveryState === 0;
        if (ended && Number(iframe.closest(".short-slide")?.dataset.index) === activeIndex) {
          markLessonCompleted(activeIndex);
          window.setTimeout(() => {
            scrollToShort(activeIndex + 1);
          }, isShortFeedFullscreen() ? 260 : 120);
        }
      });

      document.addEventListener("visibilitychange", () => {
        if (document.hidden) {
          pauseSlide(activeIndex);
        } else if (feedInView) {
          playSlide(activeIndex);
        }
      });
    }

    function setupVideoTheater() {
      const modal = document.getElementById("videoModal");
      const modalTitle = document.getElementById("videoModalTitle");
      const modalFrame = document.getElementById("videoModalFrame");
      const closeButton = document.getElementById("videoClose");
      let activeVideoButton = null;
      let activeVideoCard = null;
      let activeVideoWasShort = false;
      let activeVideoEnded = false;

      function buildPlayerSrc(src, isShort) {
        const url = new URL(src, window.location.href);
        const idMatch = url.pathname.match(/\/embed\/([^/]+)/);
        if (idMatch) {
          return buildYouTubeEmbedSrc(idMatch[1], {
            ...Object.fromEntries(url.searchParams.entries()),
            autoplay: "1",
            ...(isShort ? { enablejsapi: "1" } : {})
          });
        }
        url.searchParams.set("autoplay", "1");

        if (isShort) {
          url.searchParams.set("enablejsapi", "1");
        }

        return url.toString();
      }

      function resumeVideoScroll() {
        const shortCards = [...document.querySelectorAll(".shorts-grid .video-card")];
        const activeShortIndex = shortCards.indexOf(activeVideoCard);
        const nextShortCard = activeVideoWasShort && activeShortIndex > -1 ? shortCards[activeShortIndex + 1] : null;
        const targetCard = nextShortCard || activeVideoCard;
        const targetButton = targetCard?.querySelector(".video-thumb") || activeVideoButton;

        if (!targetCard) return;

        window.setTimeout(() => {
          targetCard.scrollIntoView({
            behavior: "smooth",
            block: activeVideoWasShort ? "center" : "nearest"
          });
          targetCard.classList.add("video-resume");
          window.setTimeout(() => targetCard.classList.remove("video-resume"), 900);
          targetButton?.focus({ preventScroll: true });
        }, 80);
      }

      function finishShortVideo() {
        if (!activeVideoWasShort || activeVideoEnded || modal.hidden) return;
        activeVideoEnded = true;
        closeVideo();
      }

      function listenForShortEnd(player) {
        const command = JSON.stringify({
          event: "command",
          func: "addEventListener",
          args: ["onStateChange"]
        });

        function requestStateEvents() {
          player.contentWindow?.postMessage(command, "*");
        }

        player.addEventListener("load", requestStateEvents);
        window.setTimeout(requestStateEvents, 700);
      }

      function closeVideo() {
        const shouldResume = Boolean(activeVideoCard);
        modal.hidden = true;
        modal.setAttribute("aria-hidden", "true");
        modal.classList.remove("is-short");
        modalFrame.innerHTML = "";
        if (shouldResume) resumeVideoScroll();
      }

      function openVideo(src, title, isShort = false, trigger = null) {
        modalTitle.textContent = title;
        modal.classList.toggle("is-short", isShort);
        modalFrame.innerHTML = "";
        activeVideoButton = trigger;
        activeVideoCard = trigger?.closest(".video-card") || null;
        activeVideoWasShort = isShort;
        activeVideoEnded = false;

        const player = document.createElement("iframe");
        player.src = buildPlayerSrc(src, isShort);
        player.title = title;
        player.allow = "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen";
        player.allowFullscreen = true;
        player.referrerPolicy = "origin-when-cross-origin";
        if (isShort) listenForShortEnd(player);
        modalFrame.appendChild(player);

        modal.hidden = false;
        modal.setAttribute("aria-hidden", "false");
        closeButton.focus();
      }

      document.querySelectorAll(".video-frame iframe").forEach((iframe) => {
        const src = iframe.getAttribute("src");
        const title = iframe.getAttribute("title") || "Chess lesson";
        const idMatch = src.match(/embed\/([^?"]+)/);
        const videoId = idMatch ? idMatch[1] : "";
        const isShort = iframe.dataset.format === "short";
        const button = document.createElement("button");

        button.type = "button";
        button.className = "video-thumb is-thumb-loading";
        button.setAttribute("aria-label", `Play ${title}`);
        if (videoId) {
          button.dataset.thumbnail = `https://i.ytimg.com/vi/${videoId}/hqdefault.jpg`;
        }
        button.innerHTML = '<span class="play-mark" aria-hidden="true"></span>';
        button.addEventListener("click", () => openVideo(src, title, isShort, button));

        iframe.parentElement.replaceChildren(button);
      });

      const loadThumbnail = (button) => {
        if (!button?.dataset.thumbnail) return;
        button.style.backgroundImage = `url("${button.dataset.thumbnail}")`;
        button.classList.remove("is-thumb-loading");
        delete button.dataset.thumbnail;
      };

      const thumbs = [...document.querySelectorAll(".video-thumb")];
      if ("IntersectionObserver" in window) {
        const thumbObserver = new IntersectionObserver((entries) => {
          entries.forEach((entry) => {
            if (!entry.isIntersecting) return;
            loadThumbnail(entry.target);
            thumbObserver.unobserve(entry.target);
          });
        }, {
          rootMargin: "700px 0px"
        });

        thumbs.forEach((button) => thumbObserver.observe(button));
      } else {
        thumbs.forEach(loadThumbnail);
      }

      closeButton.addEventListener("click", closeVideo);
      modal.addEventListener("click", (event) => {
        if (event.target === modal) closeVideo();
      });
      document.addEventListener("keydown", (event) => {
        if (event.key === "Escape" && !modal.hidden) closeVideo();
      });
      window.addEventListener("message", (event) => {
        if (!activeVideoWasShort || modal.hidden) return;
        if (typeof event.origin === "string" && !event.origin.includes("youtube")) return;

        let data = event.data;
        if (typeof data === "string") {
          try {
            data = JSON.parse(data);
          } catch {
            return;
          }
        }

        const directState = data?.event === "onStateChange" ? data.info : undefined;
        const deliveryState = data?.event === "infoDelivery" ? data.info?.playerState : undefined;
        if (directState === 0 || deliveryState === 0) finishShortVideo();
      });
    }

    document.getElementById("nextPuzzle").addEventListener("click", () => {
      currentPuzzle = getNextPuzzleIndex();
      renderPuzzle();
    });

    document.getElementById("startPuzzle").addEventListener("click", startPuzzle);
    document.getElementById("flipPuzzle").addEventListener("click", flipPuzzleBoard);
    document.getElementById("soundPuzzle").addEventListener("click", togglePuzzleSound);
    document.getElementById("retryPuzzle").addEventListener("click", retryPuzzle);
    document.getElementById("analyzePuzzle").addEventListener("click", toggleAnalyzePuzzle);
    document.getElementById("replayPuzzle").addEventListener("click", replayPuzzleSolution);

    document.querySelectorAll("[data-puzzle-plan]").forEach((button) => {
      button.addEventListener("click", () => setPuzzlePlan(button.dataset.puzzlePlan));
    });

    document.getElementById("dailyPuzzle").addEventListener("click", () => {
      activePuzzlePlan = "all";
      currentPuzzle = getDailyPuzzleIndex();
      renderPuzzle();
    });

    document.getElementById("resetPuzzle").addEventListener("click", () => {
      currentPuzzle = 0;
      streak = 0;
      puzzleAttempts = 0;
      puzzleCorrect = 0;
      spacedReview = null;
      solvedPuzzles.clear();
      renderPuzzle();
    });

    document.getElementById("hintPuzzle").addEventListener("click", () => {
      showNextPuzzleHint();
    });

    document.getElementById("revealPuzzle").addEventListener("click", () => {
      if (activeAnswered) return;
      if (puzzleHintStep < 2) showNextPuzzleHint();
      else revealPuzzleSolution();
    });

    document.getElementById("visionAnswer").addEventListener("click", () => {
      const answer = document.getElementById("visionAnswerText");
      answer.hidden = !answer.hidden;
      document.getElementById("visionAnswer").textContent = answer.hidden ? "Show Answer" : "Hide Answer";
    });

    document.getElementById("nextAdventure").addEventListener("click", () => {
      currentAdventure = (currentAdventure + 1) % adventureMissions.length;
      renderAdventureMission();
    });

    document.getElementById("restartAdventure").addEventListener("click", renderAdventureMission);

    setupLearnerPreferences();
    buildHeroBoard();
    setupLessonFlow();
    renderAdventureMission();
    renderMiniBoards();
    setupOpeningFavorites();
    renderCoordinates();
    renderPuzzle();
    setupPuzzleChess();
    wireTabs();
    setupSiteTabs();
    setupGentleStart();
    setupDailyTraining();
    setupPlayableChess();
    setupBooks();
    renderShortFeed();
    setupVideoTheater();
  </script>
</body>
</html>
