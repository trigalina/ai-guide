<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI-инструменты для SMM команды</title>
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@400;700;900&family=Manrope:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #13131c;
    --card: #1a1a26;
    --border: #2a2a40;
    --accent1: #7c5cfc;
    --accent2: #fc5c7d;
    --accent3: #5cf8c8;
    --accent4: #fcb85c;
    --accent5: #5cb8fc;
    --text: #f0eeff;
    --muted: #8888aa;
    --glow1: rgba(124,92,252,0.25);
    --glow2: rgba(252,92,125,0.2);
    --glow3: rgba(92,248,200,0.2);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Manrope', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 9999; opacity: 0.4;
  }

  .wrap { max-width: 1100px; margin: 0 auto; padding: 0 32px; }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: center;
    position: relative;
    padding: 80px 0;
    overflow: hidden;
  }

  .hero-bg {
  position: absolute; inset: 0;
  background:
    radial-gradient(ellipse 70% 60% at 75% 15%, rgba(124,92,252,0.35), transparent),
    radial-gradient(ellipse 50% 45% at 20% 85%, rgba(92,248,200,0.15), transparent),
    radial-gradient(ellipse 20% 20% at 10% 80%, rgba(252,92,125,0.15), transparent),
    radial-gradient(ellipse 90% 80% at 50% 55%, rgba(92,184,252,0.1), transparent);
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(124,92,252,0.12);
    border: 1px solid rgba(124,92,252,0.3);
    border-radius: 100px;
    padding: 6px 16px;
    font-size: 12px; font-weight: 600; letter-spacing: 0.1em;
    text-transform: uppercase; color: var(--accent1);
    margin-bottom: 32px;
    width: fit-content;
    animation: fadeUp 0.6s ease both;
  }

  .hero h1 {
    font-family: 'Unbounded', sans-serif;
    font-size: clamp(36px, 6vw, 72px);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -0.02em;
    margin-bottom: 24px;
    animation: fadeUp 0.6s 0.1s ease both;
  }

  .hero h1 span.grad {
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .hero h1 span.grad2 {
    background: linear-gradient(135deg, var(--accent3), var(--accent5));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }

  .hero-sub {
    font-size: 18px; color: var(--muted); max-width: 600px;
    animation: fadeUp 0.6s 0.2s ease both;
    margin-bottom: 48px;
  }

  .hero-stats {
    display: flex; gap: 40px; flex-wrap: wrap;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .stat { display: flex; flex-direction: column; gap: 4px; }
  .stat-num {
    font-family: 'Unbounded', sans-serif; font-size: 28px; font-weight: 700;
    background: linear-gradient(135deg, var(--accent3), var(--accent5));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .stat-label { font-size: 12px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.08em; }

  /* SCROLL INDICATOR */
  .scroll-hint {
    position: absolute; bottom: 32px; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    color: var(--muted); font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase;
    animation: bounce 2s infinite;
  }
  .scroll-hint svg { width: 20px; opacity: 0.5; }

  /* SECTION */
  section { padding: 80px 0; }
  .section-label {
    font-size: 11px; letter-spacing: 0.18em; text-transform: uppercase;
    color: var(--accent1); font-weight: 600; margin-bottom: 12px;
  }
  .section-title {
    font-family: 'Unbounded', sans-serif;
    font-size: clamp(24px, 4vw, 40px);
    font-weight: 700; line-height: 1.2;
    margin-bottom: 16px;
  }
  .section-desc { color: var(--muted); max-width: 560px; margin-bottom: 48px; font-size: 16px; }

  /* TOOLS GRID */
  .tools-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
  }

  .tool-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 28px;
    position: relative; overflow: hidden;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
  }
  .tool-card:hover {
    transform: translateY(-4px);
  }
  .tool-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: var(--card-accent, var(--accent1));
  }
  .tool-card:hover {
    border-color: var(--card-accent, var(--accent1));
    box-shadow: 0 8px 40px var(--card-glow, var(--glow1));
  }

  .tool-icon {
    width: 52px; height: 52px; border-radius: 14px;
    display: flex; align-items: center; justify-content: center;
    font-size: 24px; margin-bottom: 20px;
    background: var(--card-icon-bg, rgba(124,92,252,0.12));
  }

  .tool-name {
    font-family: 'Unbounded', sans-serif; font-size: 16px; font-weight: 700;
    margin-bottom: 6px;
  }
  .tool-role {
    font-size: 12px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.1em;
    color: var(--card-accent, var(--accent1)); margin-bottom: 12px;
  }
  .tool-desc { font-size: 14px; color: var(--muted); line-height: 1.6; margin-bottom: 20px; }

  .tool-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    font-size: 11px; padding: 3px 10px; border-radius: 100px;
    background: rgba(255,255,255,0.05); border: 1px solid var(--border);
    color: var(--muted);
  }

  /* WORKFLOW */
  .workflow { position: relative; }
  .workflow-steps {
    display: flex; flex-direction: column; gap: 0;
    position: relative;
  }
  .workflow-steps::before {
    content: '';
    position: absolute; left: 27px; top: 0; bottom: 0; width: 2px;
    background: linear-gradient(to bottom, var(--accent1), var(--accent2), var(--accent3), var(--accent4));
    border-radius: 2px;
  }

  .step {
    display: flex; gap: 28px; align-items: flex-start;
    padding: 24px 0;
    opacity: 0; animation: fadeUp 0.5s ease both;
  }
  .step:nth-child(1) { animation-delay: 0.1s; }
  .step:nth-child(2) { animation-delay: 0.2s; }
  .step:nth-child(3) { animation-delay: 0.3s; }
  .step:nth-child(4) { animation-delay: 0.4s; }
  .step:nth-child(5) { animation-delay: 0.5s; }

  .step-num {
    width: 56px; height: 56px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Unbounded', sans-serif; font-size: 18px; font-weight: 900;
    flex-shrink: 0; z-index: 1;
    border: 2px solid;
  }

  .step-content {
    flex: 1;
    background: var(--card); border: 1px solid var(--border); border-radius: 16px;
    padding: 24px; margin-top: 4px;
    transition: border-color 0.3s;
  }
  .step-content:hover { border-color: rgba(255,255,255,0.15); }

  .step-title {
    font-family: 'Unbounded', sans-serif; font-size: 15px; font-weight: 700;
    margin-bottom: 8px;
  }
  .step-text { font-size: 14px; color: var(--muted); margin-bottom: 16px; }

  .step-tools { display: flex; flex-wrap: wrap; gap: 8px; }
  .step-tool {
    display: flex; align-items: center; gap: 6px;
    font-size: 12px; font-weight: 600; padding: 5px 12px; border-radius: 8px;
    border: 1px solid; 
  }

  /* PROMPT FORMULAS */
  .formula-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); gap: 20px; }

  .formula-card {
    background: var(--card); border: 1px solid var(--border); border-radius: 20px;
    padding: 28px; position: relative; overflow: hidden;
    transition: transform 0.3s;
  }
  .formula-card:hover { transform: translateY(-3px); }

  .formula-name {
    font-family: 'Unbounded', sans-serif; font-size: 22px; font-weight: 900;
    margin-bottom: 6px;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .formula-full { font-size: 12px; color: var(--muted); margin-bottom: 16px; letter-spacing: 0.05em; }
  .formula-parts { display: flex; flex-direction: column; gap: 8px; margin-bottom: 20px; }
  .formula-part {
    display: flex; align-items: flex-start; gap: 10px;
    background: rgba(255,255,255,0.03); border-radius: 10px; padding: 10px 12px;
  }
  .fp-letter {
    font-family: 'Unbounded', sans-serif; font-size: 13px; font-weight: 900;
    min-width: 20px; color: var(--accent1);
  }
  .fp-label { font-size: 13px; font-weight: 600; }
  .fp-desc { font-size: 12px; color: var(--muted); }
  .formula-example {
    background: rgba(124,92,252,0.06); border: 1px solid rgba(124,92,252,0.15);
    border-radius: 10px; padding: 14px;
    font-size: 13px; color: #b0a8d0; font-style: italic;
    line-height: 1.6;
  }
  .formula-example strong { color: var(--accent1); font-style: normal; }

  /* CALENDAR TABLE */
  .cal-wrap {
    overflow-x: auto;
    border-radius: 16px;
    border: 1px solid var(--border);
  }
  table {
    width: 100%; border-collapse: collapse;
    font-size: 13px;
  }
  thead { background: rgba(124,92,252,0.1); }
  th {
    padding: 14px 16px; text-align: left;
    font-family: 'Unbounded', sans-serif; font-size: 11px; font-weight: 700;
    text-transform: uppercase; letter-spacing: 0.08em;
    color: var(--accent1); border-bottom: 1px solid var(--border);
    white-space: nowrap;
  }
  td { padding: 14px 16px; border-bottom: 1px solid rgba(255,255,255,0.04); vertical-align: top; }
 tr:last-child td { border-bottom: none; }
  tr:hover td { background: rgba(255,255,255,0.02); }
  .cal-day { font-weight: 600; white-space: nowrap; }
  .cal-format {
    display: inline-block; font-size: 11px; font-weight: 600; padding: 2px 8px;
    border-radius: 6px; white-space: nowrap;
  }
  .fmt-post { background: rgba(124,92,252,0.15); color: var(--accent1); }
  .fmt-reel { background: rgba(252,92,125,0.15); color: var(--accent2); }
  .fmt-story { background: rgba(92,248,200,0.15); color: var(--accent3); }
  .fmt-article { background: rgba(252,184,92,0.15); color: var(--accent4); }
  .fmt-video { background: rgba(92,184,252,0.15); color: var(--accent5); }
  .ai-chip {
    display: inline-flex; align-items: center; gap: 4px;
    font-size: 11px; padding: 2px 8px; border-radius: 6px;
    background: rgba(255,255,255,0.05); border: 1px solid var(--border);
    color: var(--muted); margin: 2px;
  }

  /* TIPS */
  .tips-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 16px; }
  .tip-card {
    background: var(--card); border: 1px solid var(--border); border-radius: 16px;
    padding: 22px; display: flex; gap: 14px;
  }
  .tip-icon { font-size: 22px; flex-shrink: 0; margin-top: 2px; }
  .tip-title { font-weight: 600; font-size: 14px; margin-bottom: 4px; }
  .tip-text { font-size: 13px; color: var(--muted); }

  /* DIVIDER */
  .divider {
    height: 1px; background: linear-gradient(to right, transparent, var(--border), transparent);
    margin: 0;
  }

  /* FOOTER */
  footer {
    padding: 60px 0 40px;
    text-align: center;
    color: var(--muted); font-size: 13px;
  }
  footer .logo-text {
    font-family: 'Unbounded', sans-serif; font-size: 20px; font-weight: 900;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    margin-bottom: 12px;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes bounce {
    0%, 100% { transform: translateX(-50%) translateY(0); }
    50% { transform: translateX(-50%) translateY(6px); }
  }

  /* RESPONSIVE */
  @media (max-width: 600px) {
    .wrap { padding: 0 16px; }
    .hero-stats { gap: 24px; }
    .workflow-steps::before { left: 23px; }
  }

  /* HIGHLIGHT BOX */
  .highlight-box {
    background: linear-gradient(135deg, rgba(124,92,252,0.08), rgba(252,92,125,0.05));
    border: 1px solid rgba(124,92,252,0.2);
    border-radius: 16px; padding: 24px 28px;
    margin-bottom: 40px;
    font-size: 15px; color: #c8c0f0; line-height: 1.7;
  }
  .highlight-box strong { color: var(--text); }

  /* NUMBERING */
  .numbered { counter-reset: items; }
  .numbered > * { counter-increment: items; }

</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
  <div class="hero-bg"></div>
  <div class="wrap" style="position:relative; z-index:1;">
    <div class="hero-badge">
      <svg width="12" height="12" viewBox="0 0 12 12" fill="none"><circle cx="6" cy="6" r="6" fill="currentColor"/></svg>
      Руководство для SMM команды
    </div>
    <h1>
      <span class="grad">AI-инструменты</span><br>
      для создания<br>
      <span class="grad2">контента</span>
    </h1>
    <p class="hero-sub">Пошаговый гайд: какой нейросетью пользоваться, когда и зачем — от идеи до публикации</p>
    <div class="hero-stats">
      <div class="stat">
        <span class="stat-num">5+</span>
        <span class="stat-label">AI-инструментов</span>
      </div>
      <div class="stat">
        <span class="stat-num">6</span>
        <span class="stat-label">формул промптов</span>
      </div>
      <div class="stat">
        <span class="stat-num">×3</span>
        <span class="stat-label">быстрее создание</span>
      </div>
    </div>
  </div>
  <div class="scroll-hint">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 5v14M5 12l7 7 7-7"/></svg>
    прокрутите вниз
  </div>
</div>

<div class="divider"></div>

<!-- ИНСТРУМЕНТЫ -->
<section>
  <div class="wrap">
    <div class="section-label">Шаг 1 — Знакомство с инструментами</div>
    <h2 class="section-title">Кто за что отвечает?</h2>
    <p class="section-desc">Каждый AI-инструмент — это специалист в своей области. Запомните распределение ролей раз и навсегда.</p>

    <div class="tools-grid">

      <!-- ChatGPT -->
      <div class="tool-card" style="--card-accent: #5cb8fc; --card-glow: rgba(92,184,252,0.2); --card-icon-bg: rgba(92,184,252,0.1);">
        <div class="tool-icon">🧠</div>
        <div class="tool-name">ChatGPT</div>
        <div class="tool-role">Мозг команды — Текст и стратегия</div>
        <div class="tool-desc">Генерирует тексты, подписи, заголовки, контент-планы, отвечает на вопросы, составляет промпты для других нейросетей, помогает с брейнштормом и анализом.</div>
        <div class="tool-tags">
          <span class="tag">Посты</span>
          <span class="tag">Сторителлинг</span>
          <span class="tag">SEO-тексты</span>
          <span class="tag">Идеи</span>
          <span class="tag">Промпты</span>
        </div>
      </div>

      <!-- Claude -->
      <div class="tool-card" style="--card-accent: #fc5c7d; --card-glow: rgba(252,92,125,0.2); --card-icon-bg: rgba(252,92,125,0.1);">
        <div class="tool-icon">✍️</div>
        <div class="tool-name">Claude</div>
        <div class="tool-role">Копирайтер — Длинные тексты и анализ</div>
        <div class="tool-desc">Лучший для длинных, структурированных материалов: статьи, гайды, сценарии, аналитика. Глубже понимает контекст и тонкие нюансы тона бренда.</div>
        <div class="tool-tags">
          <span class="tag">Статьи</span>
          <span class="tag">Сценарии</span>
          <span class="tag">Гайды</span>
          <span class="tag">Анализ</span>
        </div>
      </div>

      <!-- Midjourney -->
      <div class="tool-card" style="--card-accent: #7c5cfc; --card-glow: rgba(124,92,252,0.25); --card-icon-bg: rgba(124,92,252,0.1);">
        <div class="tool-icon">🎨</div>
        <div class="tool-name">Midjourney</div>
        <div class="tool-role">Арт-директор — Фото и иллюстрации</div>
        <div class="tool-desc">Создаёт реалистичные фото и художественные иллюстрации высокого качества. Идеален для обложек, фонов, lifestyle-контента и брендовых визуалов.</div>
        <div class="tool-tags">
          <span class="tag">Обложки</span>
          <span class="tag">Lifestyle</span>
          <span class="tag">Портреты</span>
          <span class="tag">Фоны</span>
        </div>
      </div>

      <!-- Nano Banana -->
      <div class="tool-card" style="--card-accent: #fcb85c; --card-glow: rgba(252,184,92,0.2); --card-icon-bg: rgba(252,184,92,0.1);">
        <div class="tool-icon">🍌</div>
        <div class="tool-name">Nano Banana</div>
        <div class="tool-role">Дизайнер — Классные нестандартные картинки</div>
        <div class="tool-desc">Генерирует яркий, нестандартный визуал с уникальным стилем. Отлично подходит для мемов, трендовых форматов, карточек и eye-catching графики для ленты.</div>
        <div class="tool-tags">
          <span class="tag">Мемы</span>
          <span class="tag">Карточки</span>
          <span class="tag">Тренды</span>
          <span class="tag">Stories</span>
        </div>
      </div>

      <!-- Kling -->
      <div class="tool-card" style="--card-accent: #5cf8c8; --card-glow: rgba(92,248,200,0.2); --card-icon-bg: rgba(92,248,200,0.1);">
        <div class="tool-icon">🎬</div>
        <div class="tool-name">Kling AI</div>
        <div class="tool-role">Режиссёр — Оживляет картинки в видео</div>
        <div class="tool-desc">Превращает статичные изображения в динамичные видео. Добавляет движение, анимирует фото, создаёт Reels и TikTok-видео из готовых картинок Midjourney/Nano Banana.</div>
        <div class="tool-tags">
          <span class="tag">Reels</span>
          <span class="tag">TikTok</span>
          <span class="tag">Анимация</span>
          <span class="tag">Motion</span>
        </div>
      </div>

      <!-- Suno / ElevenLabs -->
      <div class="tool-card" style="--card-accent: #fc5c7d; --card-glow: rgba(252,92,125,0.15); --card-icon-bg: rgba(252,92,125,0.08);">
        <div class="tool-icon">🎵</div>
        <div class="tool-name">Suno / ElevenLabs</div>
        <div class="tool-role">Саунд-продюсер — Музыка и голос</div>
        <div class="tool-desc">Suno создаёт фоновую музыку для видео, ElevenLabs — озвучивает тексты реалистичным голосом. Идеально для Reels без авторских прав и voiceover.</div>
        <div class="tool-tags">
          <span class="tag">Музыка</span>
          <span class="tag">Voiceover</span>
          <span class="tag">Подкасты</span>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ВОРКФЛОУ -->
<section>
  <div class="wrap">
    <div class="section-label">Шаг 2 — Процесс работы</div>
    <h2 class="section-title">От идеи до публикации</h2>
    <p class="section-desc">Следуй этим шагам при создании каждой единицы контента. Не пропускай этапы!</p>

    <div class="workflow-steps numbered">

      <div class="step">
        <div class="step-num" style="background: rgba(124,92,252,0.1); border-color: var(--accent1); color: var(--accent1);">01</div>
        <div class="step-content">
          <div class="step-title">Определи формат и цель</div>
          <div class="step-text">Что ты создаёшь? Пост в ленту, сторис, Reel, статью? Какая цель: охват, вовлечение, продажи, узнаваемость? Ответ на эти вопросы определяет всё остальное.</div>
          <div class="step-tools">
            <span class="step-tool" style="background: rgba(92,184,252,0.08); border-color: rgba(92,184,252,0.3); color: var(--accent5);">🧠 ChatGPT — брейншторм идей</span>
          </div>
        </div>
      </div>

      <div class="step">
        <div class="step-num" style="background: rgba(252,92,125,0.1); border-color: var(--accent2); color: var(--accent2);">02</div>
        <div class="step-content">
          <div class="step-title">Напиши промпт для текста</div>
          <div class="step-text">Используй одну из формул промптов (RTF, BAB, CARE, RISE и др.) Чем точнее промпт — тем лучше результат. Укажи: роль, задачу, тон, длину, формат.</div>
          <div class="step-tools">
            <span class="step-tool" style="background: rgba(92,184,252,0.08); border-color: rgba(92,184,252,0.3); color: var(--accent5);">🧠 ChatGPT — короткие тексты</span>
            <span class="step-tool" style="background: rgba(252,92,125,0.08); border-color: rgba(252,92,125,0.3); color: var(--accent2);">✍️ Claude — длинные тексты</span>
          </div>
        </div>
      </div>

      <div class="step">
        <div class="step-num" style="background: rgba(92,248,200,0.1); border-color: var(--accent3); color: var(--accent3);">03</div>
        <div class="step-content">
          <div class="step-title">Создай визуал</div>
          <div class="step-text">Выбери инструмент под задачу: реалистичные изображения → Midjourney, яркие нестандартные картинки → Nano Banana. Используй стиль бренда в промпте.</div>
          <div class="step-tools">
            <span class="step-tool" style="background: rgba(124,92,252,0.08); border-color: rgba(124,92,252,0.3); color: var(--accent1);">🎨 Midjourney — реалистичное фото/арт</span>
            <span class="step-tool" style="background: rgba(252,184,92,0.08); border-color: rgba(252,184,92,0.3); color: var(--accent4);">🍌 Nano Banana — стильные карточки</span>
          </div>
        </div>
      </div>

      <div class="step">
        <div class="step-num" style="background: rgba(252,184,92,0.1); border-color: var(--accent4); color: var(--accent4);">04</div>
        <div class="step-content">
          <div class="step-title">Оживи картинку (если нужно видео)</div>
          <div class="step-text">Загрузи готовое изображение в Kling AI. Опиши движение: «камера медленно приближается», «волосы развеваются на ветру», «логотип вращается». Выгрузи видео 5–10 сек.</div>
          <div class="step-tools">
            <span class="step-tool" style="background: rgba(92,248,200,0.08); border-color: rgba(92,248,200,0.3); color: var(--accent3);">🎬 Kling AI — image-to-video</span>
          </div>
        </div>
      </div>

      <div class="step">
        <div class="step-num" style="background: rgba(252,92,125,0.1); border-color: var(--accent2); color: var(--accent2);">05</div>
        <div class="step-content">
          <div class="step-title">Добавь звук (для видео)</div>
          <div class="step-text">Создай фоновую музыку в Suno (укажи настроение: «вдохновляющий, современный, без слов») или озвучь текст в ElevenLabs для voiceover. Всегда проверяй бесплатные права.</div>
          <div class="step-tools">
            <span class="step-tool" style="background: rgba(252,92,125,0.08); border-color: rgba(252,92,125,0.3); color: var(--accent2);">🎵 Suno — музыка</span>
            <span class="step-tool" style="background: rgba(252,92,125,0.08); border-color: rgba(252,92,125,0.3); color: var(--accent2);">🎙 ElevenLabs — voiceover</span>
          </div>
        </div>
      </div>

      <div class="step">
        <div class="step-num" style="background: rgba(92,184,252,0.1); border-color: var(--accent5); color: var(--accent5);">06</div>
        <div class="step-content">
          <div class="step-title">Финальная проверка и публикация</div>
          <div class="step-text">Проверь текст на соответствие тону бренда, проверь визуал на качество и соответствие формату площадки. Добавь хэштеги, теги, CTA. Запланируй время публикации.</div>
          <div class="step-tools">
            <span class="step-tool" style="background: rgba(92,184,252,0.08); border-color: rgba(92,184,252,0.3); color: var(--accent5);">🧠 ChatGPT — хэштеги и CTA</span>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ФОРМУЛЫ ПРОМПТОВ -->
<section>
  <div class="wrap">
    <div class="section-label">Шаг 3 — Формулы промптов</div>
    <h2 class="section-title">Как правильно ставить задачи нейросети</h2>
    <p class="section-desc">Промпт — это техническое задание для AI. Используй эти проверенные формулы для разных задач.</p>

    <div class="highlight-box">
      💡 <strong>Золотое правило:</strong> Чем конкретнее промпт — тем лучше результат. Всегда указывай: <strong>роль</strong> (кто ты), <strong>контекст</strong> (что за продукт/бренд), <strong>задачу</strong> (что нужно сделать) и <strong>формат</strong> (как должен выглядеть результат).
    </div>

    <div class="formula-grid">

      <div class="formula-card">
        <div class="formula-name">RTF</div>
        <div class="formula-full">Role · Task · Format</div>
        <div class="formula-parts">
          <div class="formula-part">
            <span class="fp-letter">R</span>
            <div><div class="fp-label">Role — Роль</div><div class="fp-desc">Кем должна выступать нейросеть</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">T</span>
            <div><div class="fp-label">Task — Задача</div><div class="fp-desc">Что конкретно нужно сделать</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">F</span>
            <div><div class="fp-label">Format — Формат</div><div class="fp-desc">Как должен выглядеть ответ</div></div>
          </div>
        </div>
        <div class="formula-example">
          <strong>Пример:</strong> «Ты — контент-маркетолог. Разработай контент-план для нового продукта. Представь результат в виде таблицы с неделями, темами и форматами.»
        </div>
      </div>

      <div class="formula-card">
        <div class="formula-name">BAB</div>
        <div class="formula-full">Before · After · Bridge</div>
        <div class="formula-parts">
          <div class="formula-part">
            <span class="fp-letter">B</span>
            <div><div class="fp-label">Before — Проблема</div><div class="fp-desc">Опиши текущую ситуацию/боль</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">A</span>
            <div><div class="fp-label">After — Результат</div><div class="fp-desc">Каким должен быть итог</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">B</span>
            <div><div class="fp-label">Bridge — Мост</div><div class="fp-desc">Попроси создать путь между ними</div></div>
          </div>
        </div>
        <div class="formula-example">
          <strong>Пример:</strong> «Сайт не получает трафика, мы вне ТОП-10. Цель — войти в ТОП-10 за 90 дней. Составь пошаговый план: аудит SEO, ключевые слова, оптимизация контента.»
        </div>
      </div>

      <div class="formula-card">
        <div class="formula-name">CARE</div>
        <div class="formula-full">Context · Action · Result · Example</div>
        <div class="formula-parts">
          <div class="formula-part">
            <span class="fp-letter">C</span>
            <div><div class="fp-label">Context — Контекст</div><div class="fp-desc">Фон и ситуация</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">A</span>
            <div><div class="fp-label">Action — Действие</div><div class="fp-desc">Что нужно сделать</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">R</span>
            <div><div class="fp-label">Result — Результат</div><div class="fp-desc">Желаемый итог</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">E</span>
            <div><div class="fp-label">Example — Пример</div><div class="fp-desc">Образец для вдохновения</div></div>
          </div>
        </div>
        <div class="formula-example">
          <strong>Пример:</strong> «Мы запускаем продукт на рынок Казахстана. Создай рекламную кампанию, подчёркивающую надёжность. Цель: узнаваемость + лиды. Пример: [прикрепить].»
        </div>
      </div>

      <div class="formula-card">
        <div class="formula-name">RISE</div>
        <div class="formula-full">Role · Input · Steps · Expectation</div>
        <div class="formula-parts">
          <div class="formula-part">
            <span class="fp-letter">R</span>
            <div><div class="fp-label">Role — Роль</div><div class="fp-desc">Роль для нейросети</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">I</span>
            <div><div class="fp-label">Input — Вводные данные</div><div class="fp-desc">Что уже есть / информация</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">S</span>
            <div><div class="fp-label">Steps — Шаги</div><div class="fp-desc">Что нужно сделать поэтапно</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">E</span>
            <div><div class="fp-label">Expectation — Ожидания</div><div class="fp-desc">Конкретный измеримый результат</div></div>
          </div>
        </div>
        <div class="formula-example">
          <strong>Пример:</strong> «Контент-стратег. У меня есть данные о ЦА. Составь: ключевые темы → редакционный календарь → план контента. Цель: +40% посетителей блога.»
        </div>
      </div>

      <div class="formula-card">
        <div class="formula-name">TAG</div>
        <div class="formula-full">Task · Action · Goal</div>
        <div class="formula-parts">
          <div class="formula-part">
            <span class="fp-letter">T</span>
            <div><div class="fp-label">Task — Задача</div><div class="fp-desc">Что нужно оценить/создать</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">A</span>
            <div><div class="fp-label">Action — Действие</div><div class="fp-desc">Конкретное действие AI</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">G</span>
            <div><div class="fp-label">Goal — Цель</div><div class="fp-desc">Измеримый результат</div></div>
          </div>
        </div>
        <div class="formula-example">
          <strong>Пример:</strong> «Задача: оценить команду. Действие: выступи руководителем, оцени сильные/слабые стороны. Цель: поднять удовлетворённость клиентов с 6 до 7,5 за квартал.»
        </div>
      </div>

      <div class="formula-card">
        <div class="formula-name">5P</div>
        <div class="formula-full">Prompt · Purpose · Persona · Platform · Parameters</div>
        <div class="formula-parts">
          <div class="formula-part">
            <span class="fp-letter">P</span>
            <div><div class="fp-label">Prompt — Запрос</div><div class="fp-desc">Конкретная задача</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">P</span>
            <div><div class="fp-label">Purpose — Цель</div><div class="fp-desc">Зачем это нужно</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">P</span>
            <div><div class="fp-label">Persona — Аудитория</div><div class="fp-desc">Для кого этот контент</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">P</span>
            <div><div class="fp-label">Platform — Площадка</div><div class="fp-desc">Где будет размещён контент</div></div>
          </div>
          <div class="formula-part">
            <span class="fp-letter">P</span>
            <div><div class="fp-label">Parameters — Параметры</div><div class="fp-desc">Длина, тон, ограничения</div></div>
          </div>
        </div>
        <div class="formula-example">
          <strong>Пример:</strong> «Напиши пост о продукте. Цель — продажи. Аудитория — женщины 25–35. Платформа — Instagram. Тон: дружелюбный, без сложных слов, до 150 символов.»
        </div>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>


<!-- СОВЕТЫ -->
<section>
  <div class="wrap">
    <div class="section-label">Шаг 4 — Советы и ошибки</div>
    <h2 class="section-title">Что важно помнить</h2>
    <p class="section-desc">Частые ошибки новичков и главные принципы работы с AI-контентом.</p>

    <div class="tips-grid">
      <div class="tip-card">
        <div class="tip-icon">🎯</div>
        <div>
          <div class="tip-title">Всегда указывай тон бренда</div>
          <div class="tip-text">В каждом промпте добавляй: «Тон: дружелюбный и экспертный», «стиль: молодёжный, с юмором» — иначе нейросеть говорит «своим» языком, не вашим.</div>
        </div>
      </div>
      <div class="tip-card">
        <div class="tip-icon">🔄</div>
        <div>
          <div class="tip-title">Итерируй, не бойся переспрашивать</div>
          <div class="tip-text">Первый ответ — черновик. Всегда можно написать: «Сделай короче», «Добавь эмоций», «Перепиши от первого лица» — ChatGPT и Claude помнят контекст.</div>
        </div>
      </div>
      <div class="tip-card">
        <div class="tip-icon">📐</div>
        <div>
          <div class="tip-title">Соблюдай форматы площадок</div>
          <div class="tip-text">Для Instagram Stories — 9:16, для ленты — 1:1 или 4:5, для Reels — 9:16. Указывай формат при генерации изображений в Midjourney: «--ar 9:16».</div>
        </div>
      </div>
      <div class="tip-card">
        <div class="tip-icon">✅</div>
        <div>
          <div class="tip-title">Всегда проверяй AI-текст</div>
          <div class="tip-text">Нейросети могут ошибаться в фактах, датах, именах. Никогда не публикуй без вычитки. AI — помощник, решение остаётся за человеком.</div>
        </div>
      </div>
      <div class="tip-card">
        <div class="tip-icon">🗂</div>
        <div>
          <div class="tip-title">Сохраняй удачные промпты</div>
          <div class="tip-text">Создай общий документ команды с лучшими промптами для ваших задач. Это сэкономит часы работы. Организуй по категориям: тексты, визуал, видео.</div>
        </div>
      </div>
      <div class="tip-card">
        <div class="tip-icon">🚫</div>
        <div>
          <div class="tip-title">Не публикуй без адаптации</div>
          <div class="tip-text">AI-контент — заготовка, не финальный продукт. Всегда добавляй личный голос бренда, локальный контекст и убедись, что это соответствует коммуникационной стратегии.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- QUICK REFERENCE -->
<section>
  <div class="wrap">
    <div class="section-label">Quick Reference</div>
    <h2 class="section-title">Шпаргалка: какой инструмент выбрать?</h2>
    <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 16px; margin-top: 40px;">
      <div style="background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 24px;">
        <div style="font-size: 13px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 16px; font-weight: 600;">Нужен текст для поста?</div>
        <div style="font-size: 15px; font-weight: 600; color: var(--accent5);">🧠 ChatGPT</div>
        <div style="font-size: 13px; color: var(--muted); margin-top: 4px;">Короткие тексты, подписи, заголовки, хэштеги</div>
      </div>
      <div style="background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 24px;">
        <div style="font-size: 13px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 16px; font-weight: 600;">Нужна статья или гайд?</div>
        <div style="font-size: 15px; font-weight: 600; color: var(--accent2);">✍️ Claude</div>
        <div style="font-size: 13px; color: var(--muted); margin-top: 4px;">Длинные тексты, сценарии, стратегии</div>
      </div>
      <div style="background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 24px;">
        <div style="font-size: 13px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 16px; font-weight: 600;">Нужно красивое фото/арт?</div>
        <div style="font-size: 15px; font-weight: 600; color: var(--accent1);">🎨 Midjourney</div>
        <div style="font-size: 13px; color: var(--muted); margin-top: 4px;">Реалистичные фото, lifestyle, обложки</div>
      </div>
      <div style="background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 24px;">
        <div style="font-size: 13px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 16px; font-weight: 600;">Нужна яркая карточка/мем?</div>
        <div style="font-size: 15px; font-weight: 600; color: var(--accent4);">🍌 Nano Banana</div>
        <div style="font-size: 13px; color: var(--muted); margin-top: 4px;">Карточки, мемы, нестандартный стиль</div>
      </div>
      <div style="background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 24px;">
        <div style="font-size: 13px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 16px; font-weight: 600;">Нужен Reel / видео?</div>
        <div style="font-size: 15px; font-weight: 600; color: var(--accent3);">🎬 Kling AI</div>
        <div style="font-size: 13px; color: var(--muted); margin-top: 4px;">Оживить картинку, image-to-video</div>
      </div>
      <div style="background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 24px;">
        <div style="font-size: 13px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 16px; font-weight: 600;">Нужна музыка или голос?</div>
        <div style="font-size: 15px; font-weight: 600; color: var(--accent2);">🎵 Suno / ElevenLabs</div>
        <div style="font-size: 13px; color: var(--muted); margin-top: 4px;">Музыка без авторских прав, озвучка</div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ПРОМПТЫ ДЛЯ ГЕНЕРАЦИИ ИЗОБРАЖЕНИЙ -->
<section>
  <div class="wrap">
    <div class="section-label">Шаг 5 — Библиотека промптов для визуала</div>
    <h2 class="section-title">Готовые промпты для<br><span style="background: linear-gradient(135deg, var(--accent4), var(--accent2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">генерации изображений</span></h2>
    <p class="section-desc">Скопируй, подставь свои данные в {фигурных скобках} — и отправь в Midjourney или Nano Banana.</p>

    <!-- FILTER TABS -->
    <div style="display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 36px;" id="promptTabs">
      <button class="ptab active" onclick="filterPrompts('all', this)">Все</button>
      <button class="ptab" onclick="filterPrompts('banner', this)">🖼 Баннеры</button>
      <button class="ptab" onclick="filterPrompts('product', this)">📦 Продукт</button>
      <button class="ptab" onclick="filterPrompts('reels', this)">🎬 Reels/YouTube</button>
      <button class="ptab" onclick="filterPrompts('sticker', this)">😂 Стикеры</button>
      <button class="ptab" onclick="filterPrompts('ugc', this)">📱 UGC</button>
      <button class="ptab" onclick="filterPrompts('3d', this)">🏠 3D / Мини</button>
      <button class="ptab" onclick="filterPrompts('style', this)">🎭 Стилизация</button>
    </div>

    <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(340px, 1fr)); gap: 20px;" id="promptGrid">

      <!-- БАННЕР ДЛЯ РЕКЛАМЫ -->
      <div class="prompt-card" data-cat="banner">
        <div class="pc-header">
          <div class="pc-emoji">🖼</div>
          <div>
            <div class="pc-title">Рекламный баннер Instagram</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span><span class="ptool-badge" style="background:rgba(252,184,92,0.15);color:var(--accent4);">🍌 Nano Banana</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Таргетированный баннер с лицом эксперта, фоном-роботом и призывом к действию</p>
          <div class="pc-prompt" id="p1">Рекламный баннер для Instagram. На фоне — робот с логотипом OpenAI. Синий градиент. Лицо эксперта на переднем плане. Заголовок: «<strong>{Заголовок}</strong>». Текст в плашке: «<strong>{Подзаголовок}</strong>». Слоган: «<strong>{Призыв}</strong>». Внизу синяя кнопка-плашка: «<strong>{CTA}</strong>». Формат 4:5, вертикальный.</div>

        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Заголовок: «ChatGPT для SMM» · Подзаголовок: «Бесплатный урок по созданию контента в ChatGPT» · Призыв: «Первые результаты уже завтра» · CTA: «Записаться»
        </div>
      </div>

      <!-- ИНФОГРАФИКА ВПИСЫВАНИЕ -->
      <div class="prompt-card" data-cat="product">
        <div class="pc-header">
          <div class="pc-emoji">📦</div>
          <div>
            <div class="pc-title">Вписывание продукта в сцену</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Реалистично вписывает продукт в любую сцену с учётом света и теней</p>
          <div class="pc-prompt" id="p2">Профессиональное рекламное фото продукта <strong>{название продукта}</strong> на основе прикреплённой композиции. Продукт стоит среди <strong>{описание окружения}</strong>. На фоне — <strong>{описание фона}</strong>. Впиши продукт в сцену с учётом освещения, не меняя его форму. Стиль: <strong>{реалистичный / художественный / минималистичный}</strong>. Формат 1:1.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Продукт стоит среди зелёной травы с фиолетовыми цветами в прозрачной воде. На фоне вдалеке — белая стиральная машина, за ней небо с облаками.
        </div>
      </div>

      <!-- ОБЛОЖКА REELS / YOUTUBE -->
      <div class="prompt-card" data-cat="reels">
        <div class="pc-header">
          <div class="pc-emoji">🎬</div>
          <div>
            <div class="pc-title">Обложка для Reels / YouTube</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span><span class="ptool-badge" style="background:rgba(252,184,92,0.15);color:var(--accent4);">🍌 Nano Banana</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Кинематографичная обложка с человеком-голограммой, заголовком и контровым светом</p>
          <div class="pc-prompt" id="p3">Реалистичный баннер. Заголовок — «<strong>{Главный заголовок}</strong>». Текст «<strong>{Подзаголовок}</strong>» написан небольшим шрифтом в синей плашке. Шрифт — Dela Gothic Pro. Человек справа наполовину состоит из голограммы компьютерного кода, как в фильме Матрица. В левом нижнем углу — объёмный светящийся логотип <strong>{ChatGPT / бренда}</strong>. Контровой свет. На фоне суперкомпьютер. Формат 16:9.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Заголовок: «Нейросети» · Подзаголовок: «для маркетинга» · Логотип ChatGPT в углу · Контровой свет
        </div>
      </div>

      <!-- СТИКЕРПАК -->
      <div class="prompt-card" data-cat="sticker">
        <div class="pc-header">
          <div class="pc-emoji">😂</div>
          <div>
            <div class="pc-title">Стикерпак для Telegram</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(252,184,92,0.15);color:var(--accent4);">🍌 Nano Banana</span><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Сетка мультяшных стикеров с подписями и белой обводкой в едином стиле</p>
          <div class="pc-prompt" id="p4">Сетка из 4 мультяшных стикеров для Telegram с белой обводкой, единый стиль. Персонаж — <strong>{описание персонажа}</strong>. 1) <strong>{Эмоция 1}</strong> — <strong>{сцена 1}</strong>. Подпись: «<strong>{текст 1}</strong>». 2) <strong>{Эмоция 2}</strong> — <strong>{сцена 2}</strong>. Подпись: «<strong>{текст 2}</strong>». 3) <strong>{Эмоция 3}</strong> — <strong>{сцена 3}</strong>. Подпись: «<strong>{текст 3}</strong>». 4) <strong>{Эмоция 4}</strong> — <strong>{сцена 4}</strong>. Подпись: «<strong>{текст 4}</strong>». Прозрачный фон, PNG.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          1) Злой с горящим MacBook → «Дедлайны» · 2) Счастливый с роботом ChatGPT → «Нейросети» · 3) Взволнованный в шапочке из фольги · 4) На своё усмотрение
        </div>
      </div>

      <!-- UGC КОНТЕНТ -->
      <div class="prompt-card" data-cat="ugc">
        <div class="pc-header">
          <div class="pc-emoji">📱</div>
          <div>
            <div class="pc-title">UGC-контент с продуктом</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Реалистичное «живое» фото человека с продуктом, как будто снятое на смартфон</p>
          <div class="pc-prompt" id="p5">Реалистичное фото <strong>{описание модели: молодая девушка / парень / возраст}</strong>, сделанное на iPhone. <strong>{Описание внешности}</strong>. Натуральная текстура кожи. Держит <strong>{продукт с фото}</strong> в руках и показывает его в камеру. На фоне — <strong>{локация: ванная / кухня / улица}</strong>. Сохрани внешний вид продукта, впиши с учётом освещения в сцене. Формат 2:3, вертикальный.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Молодая русская девушка, светлые волосы, несколько покраснений на коже · Держит крем · Фон: ванная комната · Формат 2:3
        </div>
      </div>

      <!-- ГИБЛИЗАЦИЯ / ЭКШН-ФИГУРКА -->
      <div class="prompt-card" data-cat="style">
        <div class="pc-header">
          <div class="pc-emoji">🎭</div>
          <div>
            <div class="pc-title">Экшн-фигурка (Гиблизация)</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span><span class="ptool-badge" style="background:rgba(252,184,92,0.15);color:var(--accent4);">🍌 Nano Banana</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Превращает фото человека в реалистичную коллекционную игрушку в упаковке</p>
          <div class="pc-prompt" id="p6">Создай игрушку человека с прикреплённого фото. Это должна быть экшн-фигурка в коллекционном стиле. Игрушка стоит внутри прозрачной коробки. Рядом с фигуркой аксессуары: [<strong>{аксессуар 1}</strong>], [<strong>{аксессуар 2}</strong>], [<strong>{аксессуар 3}</strong>]. На коробке вверху написано «<strong>{Имя / название}</strong>», под ним — «<strong>{Должность / описание}</strong>». Максимально реалистично, студийное освещение, формат 4:5.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Аксессуары: камера, микрофон, ноутбук · Имя на коробке: «Алина» · Должность: «Ai-креатор»
        </div>
      </div>

      <!-- МИНИАТЮРНЫЙ ДОМИК -->
      <div class="prompt-card" data-cat="3d">
        <div class="pc-header">
          <div class="pc-emoji">🏠</div>
          <div>
            <div class="pc-title">Миниатюрный 3D-домик</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span><span class="ptool-badge" style="background:rgba(252,184,92,0.15);color:var(--accent4);">🍌 Nano Banana</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Уютная Q-version иллюстрация: предмет превращается в жилое пространство с персонажем</p>
          <div class="pc-prompt" id="p7">Миниатюрная 3D-иллюстрация в мультяшном Q-version стиле. Предмет в форме <strong>{iPhone / Happy Meal / фотоаппарата / стакана Starbucks / вашего варианта}</strong> превращён в уютное пространство. Внутри — персонаж (<strong>{девушка / парень / ребёнок}</strong>) в ситуации: <strong>{сидит с ноутбуком / держит кофе / работает / отдыхает}</strong>. Свет: <strong>{дневной / тёплый вечерний / мягкий студийный}</strong>. Фон: <strong>{городская улица / комната с лампой / кафе}</strong>. Округлый мультяшный стиль, детализированный. Формат 3:4.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Предмет: iPhone · Персонаж: девушка с кофе · Свет: тёплый вечерний · Ситуация: отдыхает · Свет:тёплый вечерний · Фон: уютная комната с лампой
        </div>
      </div>

      <!-- КАРУСЕЛЬ 3D -->
      <div class="prompt-card" data-cat="3d">
        <div class="pc-header">
          <div class="pc-emoji">🎠</div>
          <div>
            <div class="pc-title">3D-карусель с товаром</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Стильный 3D-рендер карусели с товарами, пастельные тона, симметричная композиция</p>
          <div class="pc-prompt" id="p8">3D-рендер карусели, на которой представлен товар: <strong>{название и описание товара}</strong>. Среда: <strong>{пустыня / облачное небо / нейтральная студия / минималистичный фон}</strong>. Стиль: пастельные тона, мягкое естественное освещение, гладкие текстуры. Карусель стилизованная, с равномерно распределёнными экземплярами товара, акцент на аккуратность и симметрию. Сохрани внешний вид товара, впиши его в сцену с учётом освещения. Формат 1:1.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Товар: крем для лица в белом флаконе · Среда: нейтральная студия · Пастельные розово-бежевые тона
        </div>
      </div>

      <!-- КОМИКС / СТИЛИЗАЦИЯ -->
      <div class="prompt-card" data-cat="style">
        <div class="pc-header">
          <div class="pc-emoji">🎨</div>
          <div>
            <div class="pc-title">Стилизация / Комикс</div>
            <div class="pc-tool"><span class="ptool-badge" style="background:rgba(124,92,252,0.15);color:var(--accent1);">🎨 Midjourney</span><span class="ptool-badge" style="background:rgba(252,184,92,0.15);color:var(--accent4);">🍌 Nano Banana</span></div>
          </div>
        </div>
        <div class="pc-body">
          <p class="pc-desc">Переводит фото в комикс, аниме, мультяшный или любой другой художественный стиль</p>
          <div class="pc-prompt" id="p9">Переведи прикреплённое фото в стиль <strong>{комикс Marvel / аниме / мультфильм Pixar / акварель / масляная живопись / поп-арт}</strong>. Сохрани черты лица. Фон: <strong>{описание фона или «оставить как есть»}</strong>. Добавить текстовый пузырь с фразой: «<strong>{фраза / оставить пусто}</strong>». Цветовая палитра: <strong>{яркая / пастельная / монохромная}</strong>. Формат <strong>{1:1 / 9:16 / 16:9}</strong>.</div>
          
        </div>
        <div class="pc-example">
          <div class="pc-example-label">Заполненный пример:</div>
          Стиль: аниме · Фон: городская улица ночью · Палитра: яркая, неон · Формат 9:16
        </div>
      </div>

    </div>

    <!-- ПОДСКАЗКА -->
    <div style="margin-top: 32px; background: linear-gradient(135deg, rgba(252,184,92,0.07), rgba(252,92,125,0.05)); border: 1px solid rgba(252,184,92,0.2); border-radius: 16px; padding: 24px 28px;">
      <div style="font-size: 13px; font-weight: 700; color: var(--accent4); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 10px;">💡 Как использовать промпты</div>
      <div style="font-size: 14px; color: #c8c0f0; line-height: 1.7;">
        1. Выдели текст промпта → скопируй и вставь в Midjourney или Nano Banana<br>
        2. Замени всё, что в <strong style="color:var(--accent4)">{фигурных скобках}</strong> — на свои данные<br>
        3. Если нужно фото с лицом — <strong style="color:var(--text)">прикрепи референс</strong> перед отправкой промпта<br>
        4. Для Midjourney добавляй параметры в конец промпта:<br>
        <div style="margin-top:10px; display:flex; flex-direction:column; gap:8px;">
          <div style="background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);border-radius:10px;padding:10px 14px;display:flex;align-items:flex-start;gap:12px;">
            <code style="background:rgba(124,92,252,0.15);color:var(--accent1);padding:2px 8px;border-radius:6px;font-size:12px;white-space:nowrap;margin-top:1px;">--ar 4:5</code>
            <span style="font-size:13px;color:#c8c0f0;"><strong style="color:var(--text)">Aspect Ratio — соотношение сторон.</strong> 4:5 идеально для ленты Instagram. Меняй на <code style="background:rgba(255,255,255,0.06);padding:1px 5px;border-radius:4px;font-size:11px;">9:16</code> для Stories и Reels, <code style="background:rgba(255,255,255,0.06);padding:1px 5px;border-radius:4px;font-size:11px;">16:9</code> для YouTube-обложек, <code style="background:rgba(255,255,255,0.06);padding:1px 5px;border-radius:4px;font-size:11px;">1:1</code> для квадратных постов.</span>
          </div>
          <div style="background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);border-radius:10px;padding:10px 14px;display:flex;align-items:flex-start;gap:12px;">
            <code style="background:rgba(92,248,200,0.15);color:var(--accent3);padding:2px 8px;border-radius:6px;font-size:12px;white-space:nowrap;margin-top:1px;">--v 6 </code>
            <span style="font-size:13px;color:#c8c0f0;"><strong style="color:var(--text)">Version — версия модели.</strong> Даёт хорошее качество, реализм и детализацию.</span>
          </div>
          <div style="background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);border-radius:10px;padding:10px 14px;display:flex;align-items:flex-start;gap:12px;">
            <code style="background:rgba(252,184,92,0.15);color:var(--accent4);padding:2px 8px;border-radius:6px;font-size:12px;white-space:nowrap;margin-top:1px;">--style raw</code>
            <span style="font-size:13px;color:#c8c0f0;"><strong style="color:var(--text)">Style — стиль обработки.</strong> Raw отключает «украшательства» Midjourney и даёт более честный, фотографичный результат. Используй для реалистичных фото, UGC и продуктовых съёмок. Без этого параметра изображение будет более «художественным» и стилизованным.</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  /* PROMPT CARDS */
  .prompt-card {
    background: var(--card); border: 1px solid var(--border); border-radius: 20px;
    overflow: hidden; display: flex; flex-direction: column;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
  }
  .prompt-card:hover {
    transform: translateY(-3px);
    border-color: rgba(252,184,92,0.3);
    box-shadow: 0 8px 32px rgba(252,184,92,0.1);
  }
  .prompt-card.hidden { display: none; }

  .pc-header {
    display: flex; gap: 14px; align-items: flex-start;
    padding: 22px 22px 0;
  }
  .pc-emoji { font-size: 28px; margin-top: 2px; flex-shrink: 0; }
  .pc-title { font-family: 'Unbounded', sans-serif; font-size: 14px; font-weight: 700; margin-bottom: 6px; }
  .pc-tool { display: flex; flex-wrap: wrap; gap: 4px; }
  .ptool-badge { font-size: 11px; font-weight: 600; padding: 2px 8px; border-radius: 6px; }

  .pc-body { padding: 16px 22px; flex: 1; display: flex; flex-direction: column; gap: 12px; }
  .pc-desc { font-size: 13px; color: var(--muted); }
  .pc-prompt {
    background: rgba(255,255,255,0.04); border: 1px solid var(--border);
    border-radius: 10px; padding: 14px; font-size: 13px; color: #c8c0f0;
    line-height: 1.65; font-family: 'Manrope', sans-serif;
    flex: 1;
  }
  .pc-prompt strong { color: var(--accent4); font-weight: 600; }

  .copy-btn {
    background: rgba(124,92,252,0.12); border: 1px solid rgba(124,92,252,0.25);
    color: var(--accent1); border-radius: 8px; padding: 8px 16px;
    font-size: 12px; font-weight: 600; cursor: pointer;
    transition: background 0.2s, transform 0.1s;
    width: fit-content;
    font-family: 'Manrope', sans-serif;
  }
  .copy-btn:hover { background: rgba(124,92,252,0.22); }
  .copy-btn:active { transform: scale(0.97); }
  .copy-btn.copied { background: rgba(92,248,200,0.12); border-color: rgba(92,248,200,0.3); color: var(--accent3); }

  .pc-example {
    background: rgba(255,255,255,0.02); border-top: 1px solid var(--border);
    padding: 14px 22px; font-size: 12px; color: var(--muted); line-height: 1.6;
  }
  .pc-example-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.1em; color: var(--accent4); font-weight: 700; margin-bottom: 4px; }

  /* FILTER TABS */
  .ptab {
    background: rgba(255,255,255,0.04); border: 1px solid var(--border);
    color: var(--muted); border-radius: 100px; padding: 7px 18px;
    font-size: 13px; font-weight: 600; cursor: pointer;
    transition: all 0.2s; font-family: 'Manrope', sans-serif;
  }
  .ptab:hover { background: rgba(255,255,255,0.08); color: var(--text); }
  .ptab.active { background: rgba(252,184,92,0.12); border-color: rgba(252,184,92,0.4); color: var(--accent4); }
</style>

<script>
  function filterPrompts(cat, btn) {
    document.querySelectorAll('.ptab').forEach(t => t.classList.remove('active'));
    btn.classList.add('active');
    document.querySelectorAll('.prompt-card').forEach(card => {
      if (cat === 'all' || card.dataset.cat === cat) {
        card.classList.remove('hidden');
      } else {
        card.classList.add('hidden');
      }
    });
  }

  function copyPrompt(id, btn) {
    const el = document.getElementById(id);
    const text = el.innerText;
    navigator.clipboard.writeText(text).then(() => {
      btn.textContent = '✅ Скопировано!';
      btn.classList.add('copied');
      setTimeout(() => {
        btn.textContent = '📋 Скопировать';
        btn.classList.remove('copied');
      }, 2000);
    });
  }
</script>

<div class="divider"></div>

<!-- FOOTER -->
<footer>
  <div class="wrap">
    <div class="logo-text">AI × SMM</div>
    <p style="margin-top: 8px;"> Blashkova Alina </p>
<p style="margin-top: 8px;">Telegram: @trigalina</p>
  </div>
</footer>

</body>
</html>
