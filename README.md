<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
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
      gap: 24px;
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
      min-height: 68px;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-weight: 800;
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
      font-size: 1.2rem;
      line-height: 1;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 6px;
      flex-wrap: wrap;
      justify-content: flex-end;
    }

    .nav-links a {
      padding: 8px 10px;
      border-radius: 6px;
      color: var(--muted);
      font-size: 0.93rem;
      transition: background 160ms ease, color 160ms ease;
    }

    .nav-links a:hover,
    .nav-links a:focus-visible {
      color: var(--text);
      background: rgba(255, 255, 255, 0.08);
      outline: none;
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

    .hero-copy {
      max-width: 650px;
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
      margin-top: 30px;
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
    .video-card,
    .puzzle-shell {
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--panel);
      box-shadow: 0 16px 35px rgba(0, 0, 0, 0.16);
    }

    .lesson-card {
      min-height: 270px;
      padding: 20px;
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

    .video-body p {
      margin-bottom: 0;
      font-size: 0.95rem;
    }

    .puzzle-shell {
      display: grid;
      grid-template-columns: minmax(300px, 520px) 1fr;
      gap: 28px;
      padding: 22px;
      align-items: stretch;
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
      display: flex;
      flex-direction: column;
      min-width: 0;
    }

    .puzzle-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 16px;
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
      margin-bottom: 14px;
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
      margin-bottom: 18px;
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
      display: grid;
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

    .puzzle-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: auto;
    }

    .study-plan {
      display: grid;
      grid-template-columns: 1fr 1fr;
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
      .notation-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .video-grid,
      .video-grid.tier-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .adventure-play,
      .puzzle-shell,
      .study-plan {
        grid-template-columns: 1fr;
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
        padding-bottom: 3px;
      }

      .hero {
        min-height: auto;
      }

      .hero-inner {
        padding: 56px 0 44px;
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
      .notation-grid,
      .video-grid,
      .video-grid.tier-grid,
      .mission-selector,
      .puzzle-shell,
      .study-plan,
      .puzzle-stats {
        grid-template-columns: 1fr;
      }

      .hero-metrics {
        grid-template-columns: 1fr;
      }

      .hero-actions {
        align-items: stretch;
      }

      .button {
        width: 100%;
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
  </style>
</head>
<body>
  <header class="site-header">
    <nav class="nav" aria-label="Main navigation">
      <a class="brand" href="#top" aria-label="Checkmate Quest home">
        <span class="brand-mark" aria-hidden="true">♟</span>
        <span>Checkmate Quest</span>
      </a>
      <div class="nav-links">
        <a href="#paths">Lessons</a>
        <a href="#adventures">Adventures</a>
        <a href="#rules">Rules</a>
        <a href="#openings">Openings</a>
        <a href="#videos">Videos</a>
        <a href="#shorts">Shorts</a>
        <a href="#notation">Notation</a>
        <a href="#puzzles">Puzzles</a>
        <a href="#plan">Study Plan</a>
      </div>
    </nav>
  </header>

  <main id="top">
    <section class="hero" aria-labelledby="hero-title">
      <div class="hero-board" aria-hidden="true">
        <div class="hero-board-grid" id="heroBoard"></div>
      </div>
      <div class="hero-inner">
        <div class="hero-copy">
          <p class="eyebrow">Lichess-inspired chess tutorial</p>
          <h1 id="hero-title">Checkmate Quest</h1>
          <p>Move from legal moves to confident plans with a clean learning path, focused rules, hand-picked videos, and tactical puzzles you can solve right on the board.</p>
          <div class="hero-actions">
            <a class="button" href="#paths">Start Learning</a>
            <a class="button secondary" href="#puzzles">Try a Puzzle</a>
          </div>
          <div class="hero-metrics" aria-label="Course summary">
            <div class="metric">
              <strong>3</strong>
              <span>skill levels</span>
            </div>
            <div class="metric">
              <strong>8</strong>
              <span>core rules</span>
            </div>
            <div class="metric">
              <strong>6</strong>
              <span>board puzzles</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="paths" class="section-dark" aria-labelledby="paths-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Learning paths</p>
            <h2 id="paths-title">Choose your level</h2>
          </div>
          <p class="section-intro">Each path builds one practical layer at a time: first the board, then tactics, then strategic decisions that hold up in real games.</p>
        </div>

        <div class="path-tabs" role="tablist" aria-label="Lesson levels">
          <button class="tab-button" type="button" role="tab" aria-selected="true" aria-controls="beginner" id="tab-beginner" data-level="beginner">Beginner</button>
          <button class="tab-button" type="button" role="tab" aria-selected="false" aria-controls="intermediate" id="tab-intermediate" data-level="intermediate">Intermediate</button>
          <button class="tab-button" type="button" role="tab" aria-selected="false" aria-controls="advanced" id="tab-advanced" data-level="advanced">Advanced</button>
        </div>

        <div class="lesson-grid" id="beginner" role="tabpanel" aria-labelledby="tab-beginner">
          <article class="lesson-card">
            <span class="lesson-number">1</span>
            <h3>Board and Setup</h3>
            <p>Place the light square on your right, line up pieces in the usual back-rank order, and remember that queens start on their own color.</p>
            <ul class="topic-list">
              <li>Coordinates</li>
              <li>Starting position</li>
              <li>Piece values</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">2</span>
            <h3>How Pieces Move</h3>
            <p>Learn the movement patterns, captures, and special limits that keep bishops diagonal, rooks straight, knights jumping, and kings cautious.</p>
            <ul class="topic-list">
              <li>Movement</li>
              <li>Captures</li>
              <li>King safety</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">3</span>
            <h3>Check and Mate</h3>
            <p>Spot checks, escape checks legally, and recognize when the enemy king has no safe square, capture, or block left.</p>
            <ul class="topic-list">
              <li>Check</li>
              <li>Checkmate</li>
              <li>Stalemate</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">4</span>
            <h3>First Opening Habits</h3>
            <p>Control the center, develop minor pieces, castle early, and avoid moving the same piece repeatedly without a concrete reason.</p>
            <ul class="topic-list">
              <li>Center</li>
              <li>Development</li>
              <li>Castling</li>
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
          <p class="section-intro">A tiered video library with 87 embedded lessons, including 52 verified Shorts for fast tactics, traps, openings, mates, and puzzle reps.</p>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Beginner videos</h3>
            <p>Start here for rules, piece movement, opening basics, checkmates, and first endgames.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/OCSbzArwB10?rel=0&modestbranding=1&playsinline=1" title="How To Play Chess: The Ultimate Beginner Guide" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 1</span>
                <h3>Complete beginner guide</h3>
                <p>Learn the board, pieces, legal moves, and the first decisions that matter.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/IU6k-4rKf-g?rel=0&modestbranding=1&playsinline=1" title="Learn How to Play Chess for Beginners in Less Than 8 Minutes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 2</span>
                <h3>Piece movement</h3>
                <p>A quick pass through how every chess piece moves and captures.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/8IlJ3v8I4Z8?rel=0&modestbranding=1&playsinline=1" title="Basic Chess Openings Explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 3</span>
                <h3>Opening principles</h3>
                <p>Develop pieces, fight for the center, and castle before chasing attacks.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/I9n8sDRZLZ8?rel=0&modestbranding=1&playsinline=1" title="Checkmate for chess beginners" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 4</span>
                <h3>Basic checkmates</h3>
                <p>Build the pattern vocabulary for finishing games instead of only winning pieces.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/LPK6_QRJRA0?rel=0&modestbranding=1&playsinline=1" title="King Opposition: Draw King and Pawn Endgame" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
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
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/MbMslp2WcI0?rel=0&modestbranding=1&playsinline=1" title="The Chess Tactics Guide For Beginners" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 1</span>
                <h3>Forks, pins, skewers</h3>
                <p>Train the tactical patterns that decide most improving-player games.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/9Ga9dP3bvN8?rel=0&modestbranding=1&playsinline=1" title="How To Calculate In Chess" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 2</span>
                <h3>Calculation method</h3>
                <p>Learn how to compare candidate moves and check forcing lines clearly.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/yAnNQY2Ac6w?rel=0&modestbranding=1&playsinline=1" title="Top 5 Pawn Structures You Should Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 3</span>
                <h3>Pawn structures</h3>
                <p>Use pawn shapes to understand where pieces belong after the opening.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/kTON84W-b2Q?rel=0&modestbranding=1&playsinline=1" title="The ONLY Chess Middlegame Guide You Need" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 4</span>
                <h3>Middlegame plans</h3>
                <p>Turn development into real plans: attacks, trades, files, and weak squares.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/zOvaUJdtYTc?rel=0&modestbranding=1&playsinline=1" title="EASY Rook Checkmate!" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
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
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/wsOQBe5yBqk?rel=0&modestbranding=1&playsinline=1" title="Distant and Rectangular Opposition" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 1</span>
                <h3>Distant opposition</h3>
                <p>Study exact king geometry for pawn endings where one tempo changes everything.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/s8RDioKrLx8?rel=0&modestbranding=1&playsinline=1" title="The Principle of Positional Imbalances" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 2</span>
                <h3>Positional imbalances</h3>
                <p>Evaluate space, minor pieces, pawn weaknesses, initiative, and king safety.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/N6WmHGKLaa8?rel=0&modestbranding=1&playsinline=1" title="PROPHYLAXIS in Chess. GM Johan Hellsten explains." allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 3</span>
                <h3>Prophylaxis</h3>
                <p>Learn to ask what your opponent wants before choosing your own plan.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/aMIRnzCeD64?rel=0&modestbranding=1&playsinline=1" title="Lucena Position Explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 4</span>
                <h3>Lucena technique</h3>
                <p>Master bridge-building, one of the most important winning rook endgames.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/5rEqhhYYOrQ?rel=0&modestbranding=1&playsinline=1" title="How to Choose Candidate Moves" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
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
            <h3>Fast-track tutorials</h3>
            <p>Twenty short, focused lessons for openings, tactics, checkmates, pawn play, middlegames, and endgames.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/6IegDENuxU4?rel=0&modestbranding=1&playsinline=1" title="How To Learn and Study Chess Openings" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Openings</span><span class="badge duration">22:41</span>
                <h3>Study openings smarter</h3>
                <p>Learn how to build opening knowledge around ideas, not random memorization.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/jfcVjIa1EGM?rel=0&modestbranding=1&playsinline=1" title="Every Chess Opening Principle Explained In 18 Minutes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Openings</span><span class="badge duration">17:41</span>
                <h3>Opening principles</h3>
                <p>A fast overview of the rules that keep your first moves clean and purposeful.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/kURU67G98O8?rel=0&modestbranding=1&playsinline=1" title="Chess Basics: Opening Principles" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Openings</span><span class="badge duration">8:08</span>
                <h3>Opening basics</h3>
                <p>Quickly connect center control, development, and king safety into one routine.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/nXyJdetptXg?rel=0&modestbranding=1&playsinline=1" title="35 Vital Chess Principles" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Strategy</span><span class="badge duration">18:51</span>
                <h3>35 vital principles</h3>
                <p>Connect opening, middlegame, and endgame ideas in one practical lesson.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/W1gWHIpQNVU?rel=0&modestbranding=1&playsinline=1" title="All The Chess Tactics You Need To Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Tactics</span><span class="badge duration">15:59</span>
                <h3>Essential tactics</h3>
                <p>Build a tactical checklist that makes threats easier to spot during games.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/hcmMtNqEm4o?rel=0&modestbranding=1&playsinline=1" title="Chess Strategies - Skewers and Pins" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Tactics</span><span class="badge duration">7:37</span>
                <h3>Pins and skewers</h3>
                <p>See how line pieces trap valuable targets behind defenders.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/qMfXy648KIY?rel=0&modestbranding=1&playsinline=1" title="Chess pins, skewers and forks explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Tactics</span><span class="badge duration">11:09</span>
                <h3>Forks, pins, skewers</h3>
                <p>A beginner-friendly breakdown of the three patterns that win material fast.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/iBZLU1FXhcI?rel=0&modestbranding=1&playsinline=1" title="6 Checkmate Patterns You Must Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">21:46</span>
                <h3>Six checkmate patterns</h3>
                <p>Learn mating shapes that come back again and again in real games.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/spj8bTeZpdk?rel=0&modestbranding=1&playsinline=1" title="Learn Every Checkmate Pattern in 8 Minutes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">8:09</span>
                <h3>Checkmate pattern sprint</h3>
                <p>A compact pattern review for recognizing mate threats faster.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/Wjvy_TH1qQs?rel=0&modestbranding=1&playsinline=1" title="5 Basic Checkmate Patterns You Must Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">11:21</span>
                <h3>Five basic mates</h3>
                <p>Turn attacks into finishes with a small set of reliable mating patterns.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/Bo93mIhnDz4?rel=0&modestbranding=1&playsinline=1" title="The Top 23 Checkmate Patterns" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Mate</span><span class="badge duration">22:49</span>
                <h3>Top checkmate patterns</h3>
                <p>A broader pattern library for players ready to sharpen attacking vision.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/uszf3ZRxYMo?rel=0&modestbranding=1&playsinline=1" title="Top 10 Chess Endgame Principles Crash Course" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">14:51</span>
                <h3>Endgame crash course</h3>
                <p>Learn the principles that keep simple endings from slipping away.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/mCsc24k-Q8M?rel=0&modestbranding=1&playsinline=1" title="Easy Chess Endgames: King and Pawns" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">21:15</span>
                <h3>King and pawn endings</h3>
                <p>Practice opposition, passed pawns, and king activity in beginner endings.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/JMZJ9P2Hnq0?rel=0&modestbranding=1&playsinline=1" title="Easy Chess Endgames: Rook and Pawn" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">23:00</span>
                <h3>Rook and pawn endings</h3>
                <p>A clear intro to rook activity, pawn races, and practical conversion.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/FaYmAoJxjUY?rel=0&modestbranding=1&playsinline=1" title="15 Rules For The Endgame" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">22:38</span>
                <h3>Endgame rules</h3>
                <p>Memorable endgame rules that help choose plans when pieces disappear.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/nR8ULRlk9HA?rel=0&modestbranding=1&playsinline=1" title="Rook Endgames Crash Course" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">23:32</span>
                <h3>Rook endgame crash course</h3>
                <p>Learn active rooks, checking distance, and pawn support in rook endings.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/XZeTKbB_LWg?rel=0&modestbranding=1&playsinline=1" title="Top 25 Chess Endgame Principles" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Endgame</span><span class="badge duration">16:56</span>
                <h3>Endgame principles</h3>
                <p>A wider principle list for converting advantages and defending tough endings.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/lYX-VO1ut7U?rel=0&modestbranding=1&playsinline=1" title="5 Most Common Chess Pawn Structure Mistakes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Pawns</span><span class="badge duration">21:06</span>
                <h3>Pawn structure mistakes</h3>
                <p>Spot the pawn decisions that create long-term weaknesses or strong plans.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/VL9F0xs0yHg?rel=0&modestbranding=1&playsinline=1" title="6 Rules That Will Make You A Pawn Genius" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Pawns</span><span class="badge duration">7:37</span>
                <h3>Pawn rules</h3>
                <p>Six quick rules for making pawn moves that support your pieces.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/F98JdnLyUXA?rel=0&modestbranding=1&playsinline=1" title="The 10 Best Chess Plans For The Middlegame" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen" allowfullscreen referrerpolicy="strict-origin-when-cross-origin" sandbox="allow-scripts allow-same-origin allow-presentation"></iframe>
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
              <p>Fifty-two bite-size chess tutorials and puzzle sparks, all checked as embed-ready clips that play inside Checkmate Quest.</p>
            </div>
            <span class="shorts-count">52 Shorts</span>
          </div>
          <div class="video-grid tier-grid shorts-grid" id="shortsGrid" aria-label="YouTube Shorts chess tutorials"></div>
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

    <section id="puzzles" class="section-warm" aria-labelledby="puzzles-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Puzzle board</p>
            <h2 id="puzzles-title">Find the move</h2>
          </div>
          <p class="section-intro">Solve positions by pattern: mate threats, forks, and overloaded defenders. The feedback explains the idea behind the answer.</p>
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
            <h3 id="puzzleTitle">Puzzle title</h3>
            <p id="puzzlePrompt">Puzzle prompt</p>
            <p class="puzzle-hint hidden" id="puzzleHint">Hint text</p>
            <div class="answers" id="answers"></div>
            <p class="feedback" id="feedback">Choose the strongest move.</p>
            <div class="puzzle-actions">
              <button class="button secondary" type="button" id="hintPuzzle">Hint</button>
              <button class="button secondary" type="button" id="revealPuzzle">Reveal</button>
              <button class="button" type="button" id="nextPuzzle">Next Puzzle</button>
              <button class="button secondary" type="button" id="resetPuzzle">Reset Score</button>
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
            <h2 id="plan-title">A simple weekly plan</h2>
          </div>
          <p class="section-intro">A steady mix of play, puzzles, review, and endgames beats random marathon sessions.</p>
        </div>

        <div class="study-plan">
          <article class="plan-panel">
            <h3>Three-day loop</h3>
            <ul class="plan-list">
              <li><span>1</span><div>Play one slower game and write down the move where the position first felt unclear.</div></li>
              <li><span>2</span><div>Solve ten tactics by theme, then replay the mistakes until the pattern is automatic.</div></li>
              <li><span>3</span><div>Study one endgame position and test it from both sides against a board or engine.</div></li>
            </ul>
          </article>
          <article class="plan-panel">
            <h3>Review checklist</h3>
            <ul class="plan-list">
              <li><span>✓</span><div>Was the king safe before launching an attack?</div></li>
              <li><span>✓</span><div>Did every trade improve the position or solve a concrete problem?</div></li>
              <li><span>✓</span><div>Were checks, captures, and threats examined before the final move?</div></li>
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

    function pieceColorClass(piece) {
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
      }
    ];

    let currentPuzzle = 0;
    let activeAnswered = false;
    let streak = 0;
    const solvedPuzzles = new Set();
    let currentAdventure = 0;
    let selectedAdventureSquare = "";
    let adventureBoardState = [];

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

    function updatePuzzleStats() {
      document.getElementById("puzzleCounter").textContent = `${currentPuzzle + 1} / ${puzzles.length}`;
      document.getElementById("puzzleSolved").textContent = solvedPuzzles.size;
      document.getElementById("puzzleStreak").textContent = streak;
      document.getElementById("puzzleProgress").style.width = `${(solvedPuzzles.size / puzzles.length) * 100}%`;
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

      const puzzle = puzzles[currentPuzzle];
      activeAnswered = true;
      lockAnswers(button, answer.correct);

      if (answer.correct) {
        if (!solvedPuzzles.has(currentPuzzle)) {
          solvedPuzzles.add(currentPuzzle);
          streak += 1;
        }
        document.getElementById("feedback").textContent = puzzle.feedback;
      } else {
        streak = 0;
        document.getElementById("feedback").textContent = `Not quite. ${puzzle.feedback}`;
      }

      updatePuzzleStats();
    }

    function renderPuzzle() {
      const puzzle = puzzles[currentPuzzle];
      const board = document.getElementById("puzzleBoard");
      const answers = document.getElementById("answers");
      const feedback = document.getElementById("feedback");
      const hint = document.getElementById("puzzleHint");
      const squares = fenToSquares(puzzle.fen);

      activeAnswered = false;
      document.getElementById("puzzleLevel").textContent = puzzle.level;
      document.getElementById("puzzleSide").textContent = puzzle.side;
      document.getElementById("puzzleTitle").textContent = puzzle.title;
      document.getElementById("puzzlePrompt").textContent = puzzle.prompt;
      hint.textContent = puzzle.hint;
      hint.classList.add("hidden");
      feedback.textContent = "Choose the strongest move.";
      document.getElementById("hintPuzzle").disabled = false;
      document.getElementById("revealPuzzle").disabled = false;
      updatePuzzleStats();

      board.innerHTML = "";
      squares.forEach((piece, index) => {
        const row = Math.floor(index / 8);
        const col = index % 8;
        const square = document.createElement("span");
        const name = squareName(index);
        square.className = `puzzle-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;
        if (puzzle.targets.includes(name)) square.classList.add("target");
        const colorClass = pieceColorClass(piece);
        if (colorClass) square.classList.add(colorClass);
        square.textContent = piece;
        square.setAttribute("aria-label", `${name}${piece ? ` ${piece}` : ""}`);
        board.appendChild(square);
      });

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

    function wireTabs() {
      const tabs = document.querySelectorAll(".tab-button");
      const panels = ["beginner", "intermediate", "advanced"].map((id) => document.getElementById(id));

      tabs.forEach((tab) => {
        tab.addEventListener("click", () => {
          const level = tab.dataset.level;
          tabs.forEach((item) => item.setAttribute("aria-selected", String(item === tab)));
          panels.forEach((panel) => panel.classList.toggle("hidden", panel.id !== level));
        });
      });
    }

    function renderShortVideos() {
      const grid = document.getElementById("shortsGrid");
      if (!grid) return;

      shortVideos.forEach((video, index) => {
        const card = document.createElement("article");
        const frame = document.createElement("div");
        const iframe = document.createElement("iframe");
        const body = document.createElement("div");
        const indexBadge = document.createElement("span");
        const topicBadge = document.createElement("span");
        const durationBadge = document.createElement("span");
        const heading = document.createElement("h3");
        const note = document.createElement("p");

        card.className = "video-card";
        frame.className = "video-frame";
        body.className = "video-body";
        indexBadge.className = "badge";
        topicBadge.className = "badge";
        durationBadge.className = "badge duration";

        iframe.loading = "lazy";
        iframe.src = `https://www.youtube-nocookie.com/embed/${video.id}?rel=0&modestbranding=1&playsinline=1`;
        iframe.title = video.title;
        iframe.allow = "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen";
        iframe.referrerPolicy = "strict-origin-when-cross-origin";
        iframe.dataset.format = "short";
        iframe.setAttribute("allowfullscreen", "");
        iframe.setAttribute("sandbox", "allow-scripts allow-same-origin allow-presentation");

        indexBadge.textContent = `Short ${String(index + 1).padStart(2, "0")}`;
        topicBadge.textContent = video.topic;
        durationBadge.textContent = video.duration;
        heading.textContent = video.headline;
        note.textContent = video.note;

        frame.appendChild(iframe);
        body.append(indexBadge, topicBadge, durationBadge, heading, note);
        card.append(frame, body);
        grid.appendChild(card);
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
        url.searchParams.set("autoplay", "1");

        if (isShort) {
          url.searchParams.set("enablejsapi", "1");
          if (window.location.origin && window.location.origin !== "null") {
            url.searchParams.set("origin", window.location.origin);
          }
        }

        return url.toString();
      }

      function resumeVideoScroll() {
        const nextShortCard = activeVideoWasShort ? activeVideoCard?.nextElementSibling : null;
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
        player.referrerPolicy = "strict-origin-when-cross-origin";
        player.sandbox = "allow-scripts allow-same-origin allow-presentation";
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
        button.className = "video-thumb";
        button.setAttribute("aria-label", `Play ${title}`);
        if (videoId) {
          button.style.backgroundImage = `url("https://i.ytimg.com/vi/${videoId}/hqdefault.jpg")`;
        }
        button.innerHTML = '<span class="play-mark" aria-hidden="true"></span>';
        button.addEventListener("click", () => openVideo(src, title, isShort, button));

        iframe.parentElement.replaceChildren(button);
      });

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
      currentPuzzle = (currentPuzzle + 1) % puzzles.length;
      renderPuzzle();
    });

    document.getElementById("resetPuzzle").addEventListener("click", () => {
      currentPuzzle = 0;
      streak = 0;
      solvedPuzzles.clear();
      renderPuzzle();
    });

    document.getElementById("hintPuzzle").addEventListener("click", () => {
      document.getElementById("puzzleHint").classList.remove("hidden");
    });

    document.getElementById("revealPuzzle").addEventListener("click", () => {
      if (activeAnswered) return;

      const puzzle = puzzles[currentPuzzle];
      const correct = puzzle.answers.find((answer) => answer.correct);
      activeAnswered = true;
      streak = 0;
      lockAnswers(null, false);
      document.getElementById("feedback").textContent = `Solution: ${correct.move}. ${puzzle.feedback}`;
      updatePuzzleStats();
    });

    document.getElementById("nextAdventure").addEventListener("click", () => {
      currentAdventure = (currentAdventure + 1) % adventureMissions.length;
      renderAdventureMission();
    });

    document.getElementById("restartAdventure").addEventListener("click", renderAdventureMission);

    buildHeroBoard();
    renderAdventureMission();
    renderMiniBoards();
    renderCoordinates();
    renderPuzzle();
    wireTabs();
    renderShortVideos();
    setupVideoTheater();
  </script>
</body>
</html>
