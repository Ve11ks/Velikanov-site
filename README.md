# Velikanov-site
<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Андрей Великанов</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Oswald:wght@500;600;700&family=Golos+Text:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap">
<style>
/* Layout: протокол спортсмена. Шапка-табло, затем подиум, образование как линия лет, опыт в часах, навыки списками. */
:root {
  --bg: #F2F5FA;
  --surface: #FFFFFF;
  --fg: #0E1A33;
  --muted: #56627B;
  --line: #D3DAE8;
  --accent: #D9481C;
  --court: #1B3A8A;
  --on-accent: #FFFFFF;
  --f-display: "Oswald", "Arial Narrow", Impact, sans-serif;
  --f-body: "Golos Text", system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  --f-data: "JetBrains Mono", ui-monospace, "SF Mono", Menlo, Consolas, monospace;
}
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --bg: #0A1226; --surface: #111B37; --fg: #EAF0FF; --muted: #9AA7C4;
    --line: #24335A; --accent: #FF7B4F; --court: #86A6FF; --on-accent: #0A1226;
    color-scheme: dark;
  }
}
:root[data-theme="dark"] {
  --bg: #0A1226; --surface: #111B37; --fg: #EAF0FF; --muted: #9AA7C4;
  --line: #24335A; --accent: #FF7B4F; --court: #86A6FF; --on-accent: #0A1226;
  color-scheme: dark;
}

* { box-sizing: border-box; }
html { color-scheme: light; }
body { margin: 0; }
body {
  background: var(--bg);
  color: var(--fg);
  font-family: var(--f-body);
  font-size: 16px;
  line-height: 1.55;
  padding-inline: 20px;
  padding-block: 0 56px;
}
.wrap { max-width: 960px; margin-inline: auto; }
h1, h2, h3, p, ul { margin: 0; }
ul { padding: 0; list-style: none; }
a { color: inherit; }
:focus-visible { outline: 3px solid var(--accent); outline-offset: 3px; }

.label {
  font-family: var(--f-data);
  font-size: 12px;
  letter-spacing: .12em;
  text-transform: uppercase;
  color: var(--muted);
}
h2 {
  font-family: var(--f-display);
  font-weight: 600;
  font-size: clamp(26px, 5vw, 34px);
  text-transform: uppercase;
  letter-spacing: .02em;
  line-height: 1.1;
  text-wrap: balance;
}
section { padding-block: 44px 0; }
.sec-head { display: flex; flex-direction: column; gap: 6px; margin-bottom: 22px; }

/* Шапка */
.hero { position: relative; padding-block: 40px 8px; overflow: hidden; }
.court {
  position: absolute; right: -90px; top: -40px; width: 380px; height: 380px;
  color: var(--line); pointer-events: none;
}
.hero-in { position: relative; display: flex; flex-direction: column; gap: 18px; }
.name {
  font-family: var(--f-display);
  font-weight: 700;
  text-transform: uppercase;
  line-height: .95;
  font-size: clamp(48px, 13vw, 112px);
  letter-spacing: .005em;
}
.name span { display: block; }
.name .last { color: var(--accent); overflow-wrap: anywhere; }
.lead { max-width: 52ch; font-size: 18px; color: var(--fg); }
.lead b { font-weight: 600; }
.meta { display: flex; flex-wrap: wrap; gap: 8px 22px; }
.meta li { font-size: 14px; color: var(--muted); }
.meta li b { color: var(--fg); font-weight: 500; }

.board {
  margin-top: 26px;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  border-block: 2px solid var(--fg);
}
.board > div { padding: 14px 12px 14px 0; display: flex; flex-direction: column; gap: 2px; min-width: 0; }
.board > div + div { padding-left: 14px; border-left: 1px solid var(--line); }
.board .num {
  font-family: var(--f-display); font-weight: 700;
  font-size: clamp(34px, 8vw, 56px); line-height: 1;
  font-variant-numeric: tabular-nums;
}
.board .num small { font-size: .5em; font-weight: 600; color: var(--accent); margin-left: 2px; }
.board .cap { font-size: 13px; color: var(--muted); line-height: 1.3; }

/* Подиум */
.podium {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 8px;
  align-items: end;
  grid-template-areas: "second first third";
}
.step { display: flex; flex-direction: column; justify-content: space-between; gap: 14px; padding: 14px 12px; min-width: 0; }
.step .sport { font-family: var(--f-display); font-weight: 600; font-size: clamp(18px, 4.6vw, 26px); text-transform: uppercase; letter-spacing: .02em; line-height: 1.1; overflow-wrap: anywhere; }
.step .place { font-family: var(--f-display); font-weight: 700; line-height: .85; font-variant-numeric: tabular-nums; }
.step .sub { font-size: 12.5px; line-height: 1.35; opacity: .85; }
.step.first  { grid-area: first;  min-height: 230px; background: var(--accent); color: var(--on-accent); }
.step.second { grid-area: second; min-height: 180px; background: var(--court); color: var(--bg); }
.step.third  { grid-area: third;  min-height: 140px; background: var(--fg); color: var(--bg); }
.step.first .place { font-size: clamp(64px, 17vw, 110px); }
.step.second .place, .step.third .place { font-size: clamp(52px, 13vw, 84px); }
.podium-note { margin-top: 12px; font-size: 14px; color: var(--muted); }

.docs { margin-top: 26px; display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 12px; }
.doc { background: var(--surface); border: 1px solid var(--line); padding: 16px 18px; display: flex; flex-direction: column; gap: 4px; min-width: 0; }
.doc strong { font-weight: 600; }
.doc span { color: var(--muted); font-size: 14px; }

/* Образование */
.track { display: grid; grid-template-columns: 11fr 5fr; gap: 0; }
.seg { padding-top: 12px; min-width: 0; }
.seg .bar { height: 12px; background: var(--court); }
.seg.uni .bar { background: repeating-linear-gradient(90deg, var(--accent) 0 14px, transparent 14px 20px); }
.seg .yrs { display: flex; justify-content: space-between; margin-top: 8px; font-family: var(--f-data); font-size: 12px; color: var(--muted); font-variant-numeric: tabular-nums; }
.seg h3 { margin-top: 14px; font-family: var(--f-display); font-weight: 600; font-size: 22px; text-transform: uppercase; letter-spacing: .02em; line-height: 1.15; }
.seg p { margin-top: 6px; font-size: 15px; color: var(--muted); padding-right: 14px; }
.seg.uni { padding-left: 4px; }
.seg.uni p { padding-right: 0; }
.edu-extra { margin-top: 28px; display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 24px; border-top: 1px solid var(--line); padding-top: 20px; }
.edu-extra ul { margin-top: 8px; display: flex; flex-direction: column; gap: 4px; }
.edu-extra li::before { content: "— "; color: var(--accent); }

/* Опыт */
.shifts { display: flex; flex-direction: column; }
.shift { display: grid; grid-template-columns: minmax(0, 240px) minmax(0, 1fr); gap: 8px 28px; padding-block: 18px; border-top: 1px solid var(--line); align-items: center; }
.shift:last-child { border-bottom: 1px solid var(--line); }
.shift h3 { font-family: var(--f-display); font-weight: 600; font-size: 22px; text-transform: uppercase; letter-spacing: .02em; line-height: 1.15; }
.shift p { color: var(--muted); font-size: 14px; margin-top: 2px; }
.hours { display: flex; align-items: center; gap: 12px; }
.hours .rail { flex: 1; min-width: 0; height: 12px; background: var(--line); }
.hours .fill { height: 100%; background: var(--accent); }
.hours .val { font-family: var(--f-data); font-size: 14px; font-variant-numeric: tabular-nums; white-space: nowrap; min-width: 4.2em; text-align: right; }
.scale { margin-top: 10px; font-size: 13px; color: var(--muted); }

/* Мероприятие */
.event { background: var(--surface); border: 1px solid var(--line); padding: 20px; display: grid; grid-template-columns: auto minmax(0, 1fr); gap: 20px; align-items: start; }
.date { font-family: var(--f-display); font-weight: 700; text-transform: uppercase; line-height: .95; text-align: center; border: 2px solid var(--fg); padding: 10px 14px; }
.date b { display: block; font-size: 40px; font-variant-numeric: tabular-nums; }
.date i { display: block; font-style: normal; font-size: 14px; letter-spacing: .08em; margin-top: 4px; }
.event h3 { font-family: var(--f-display); font-weight: 600; font-size: 24px; text-transform: uppercase; letter-spacing: .02em; line-height: 1.15; }
.event dl { margin: 10px 0 0; display: grid; grid-template-columns: auto minmax(0, 1fr); gap: 4px 16px; font-size: 14px; }
.event dt { color: var(--muted); }
.event dd { margin: 0; }
.event a { color: var(--court); font-weight: 500; text-underline-offset: 3px; overflow-wrap: anywhere; }

/* Навыки */
.skills { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 28px; }
.skills h3 { font-family: var(--f-data); font-size: 12px; font-weight: 500; letter-spacing: .12em; text-transform: uppercase; color: var(--accent); padding-bottom: 10px; border-bottom: 2px solid var(--fg); }
.skills li { padding-block: 10px; border-bottom: 1px solid var(--line); }

/* Контакты */
.contact { margin-top: 56px; background: var(--fg); color: var(--bg); padding: 28px 22px; display: flex; flex-direction: column; gap: 16px; }
.contact .label { color: inherit; opacity: .7; }
.contact h2 { color: inherit; }
.mail-row { display: flex; flex-wrap: wrap; align-items: center; gap: 12px 16px; }
.mail { font-family: var(--f-data); font-size: clamp(16px, 4.4vw, 22px); overflow-wrap: anywhere; user-select: all; }
.copy { font-family: var(--f-body); font-size: 14px; font-weight: 600; background: var(--accent); color: var(--on-accent); border: 0; padding: 10px 16px; cursor: pointer; }
.copy:hover { filter: brightness(1.08); }
.contact .where { font-size: 14px; opacity: .8; }
footer { margin-top: 20px; font-size: 12.5px; color: var(--muted); }

@media (max-width: 560px) {
  .court { width: 260px; height: 260px; right: -80px; top: -20px; }
  .lead { font-size: 17px; }
  .board > div + div { padding-left: 10px; }
  .board > div { padding-right: 8px; }
  .shift { grid-template-columns: minmax(0, 1fr); }
  .event { grid-template-columns: minmax(0, 1fr); }
  .date { justify-self: start; display: flex; gap: 10px; align-items: baseline; padding: 8px 12px; }
  .date i { margin-top: 0; }
  .track { grid-template-columns: 9fr 6fr; }
  .seg p { padding-right: 8px; }
}
@media (prefers-reduced-motion: no-preference) {
  .fill { transform-origin: left; animation: grow .9s ease-out both; }
  @keyframes grow { from { transform: scaleX(0); } }
}
</style>

</head>
<body>
<div class="wrap">
  <header class="hero">
    <svg class="court" viewBox="0 0 380 380" fill="none" stroke="currentColor" stroke-width="3" aria-hidden="true">
      <circle cx="190" cy="190" r="150"/>
      <path d="M190 40v300"/>
      <rect x="120" y="190" width="140" height="190"/>
      <path d="M120 190a70 70 0 0 1 140 0"/>
    </svg>
    <div class="hero-in">
      <p class="label">Портфолио · Москва · 2026</p>
      <h1 class="name"><span>Андрей</span><span class="last">Великанов</span></h1>
      <p class="lead">Окончил школу в 2026 году и поступил в <b>РАНХиГС</b> на направление «Государственное и муниципальное управление». Занимается баскетболом, монтирует рилсы и делает базовых ботов для Telegram.</p>
      <ul class="meta">
        <li><b>Увлечение:</b> баскетбол</li>
        <li><b>Языки:</b> русский, немецкий (A2)</li>
        <li><b>Город:</b> Москва</li>
      </ul>
    </div>
    <div class="board hero-in">
      <div><span class="num">186</span><span class="cap">баллов ЕГЭ</span></div>
      <div><span class="num">3</span><span class="cap">призовых места на городских соревнованиях</span></div>
      <div><span class="num">A2</span><span class="cap">диплом по немецкому языку</span></div>
    </div>
  </header>

  <section id="sport">
    <div class="sec-head">
      <p class="label">Городские соревнования</p>
      <h2>Спортивные результаты</h2>
    </div>
    <div class="podium" role="list">
      <div class="step second" role="listitem">
        <p class="sport">Футбол</p>
        <p class="place">2</p>
        <p class="sub">2 место</p>
      </div>
      <div class="step first" role="listitem">
        <p class="sport">Карате</p>
        <p class="place">1</p>
        <p class="sub">1 место</p>
      </div>
      <div class="step third" role="listitem">
        <p class="sport">Кунг-фу</p>
        <p class="place">3</p>
        <p class="sub">3 место</p>
      </div>
    </div>
    <p class="podium-note">Все три результата получены в городских соревнованиях.</p>

    <div class="docs">
      <div class="doc"><strong>Русский медвежонок</strong><span>Грамота</span></div>
      <div class="doc"><strong>Немецкий язык, уровень A2</strong><span>Диплом о повышении уровня знаний</span></div>
    </div>
  </section>

  <section id="education">
    <div class="sec-head">
      <p class="label">Образование · среднее общее</p>
      <h2>Школа и университет</h2>
    </div>
    <div class="track">
      <div class="seg">
        <div class="bar"></div>
        <div class="yrs"><span>01.09.2015</span><span>29.05.2026</span></div>
        <h3>ГБОУ № 1468</h3>
        <p>Школа с углублёнными направлениями: немецкая, инженерная, предпринимательская и общеобразовательная.</p>
      </div>
      <div class="seg uni">
        <div class="bar"></div>
        <div class="yrs"><span>01.09.2026</span><span>→</span></div>
        <h3>РАНХиГС</h3>
        <p>Государственное и муниципальное управление.</p>
      </div>
    </div>
    <div class="edu-extra">
      <div>
        <p class="label">Дополнительное образование</p>
        <ul>
          <li>Инженер-чертёжник</li>
          <li>Оператор ЭВМ</li>
        </ul>
      </div>
      <div>
        <p class="label">Баллы ЕГЭ</p>
        <p style="margin-top:8px"><span style="font-family:var(--f-display);font-weight:700;font-size:34px;line-height:1">186</span></p>
      </div>
    </div>
  </section>

  <section id="skills">
    <div class="sec-head">
      <p class="label">Что умею</p>
      <h2>Навыки</h2>
    </div>
    <div class="skills">
      <div>
        <h3>Профессиональные</h3>
        <ul>
          <li>Монтаж рилсов</li>
          <li>Создание контента в пабликах</li>
          <li>Создание базовых ботов в Telegram</li>
        </ul>
      </div>
      <div>
        <h3>Личные качества</h3>
        <ul>
          <li>Умение слушать людей</li>
          <li>Хорошая память</li>
          <li>Навык договариваться с людьми</li>
        </ul>
      </div>
      <div>
        <h3>Универсальные</h3>
        <ul>
          <li>Умение готовить</li>
          <li>Уверенная работа на ПК</li>
          <li>Умение пользоваться ИИ</li>
        </ul>
      </div>
    </div>
  </section>

  <section id="work">
    <div class="sec-head">
      <p class="label">Опыт работы</p>
      <h2>Первые смены</h2>
    </div>
    <div class="shifts">
      <div class="shift">
        <div>
          <h3>Яндекс</h3>
          <p>Курьер · завершено</p>
        </div>
        <div class="hours" role="img" aria-label="4 часа из 36">
          <div class="rail"><div class="fill" style="width:11.1%"></div></div>
          <span class="val">4 ч</span>
        </div>
      </div>
      <div class="shift">
        <div>
          <h3>Ozon Job</h3>
          <p>Сортировщик товаров на складе · завершено</p>
        </div>
        <div class="hours" role="img" aria-label="36 часов из 36">
          <div class="rail"><div class="fill" style="width:100%"></div></div>
          <span class="val">36 ч</span>
        </div>
      </div>
    </div>
    <p class="scale">Длина полосы показывает отработанные часы, шкала до 36 часов.</p>
  </section>

  <section id="events">
    <div class="sec-head">
      <p class="label">Мероприятия</p>
      <h2>Участие</h2>
    </div>
    <article class="event">
      <div class="date"><b>9–10</b><i>сентября 2023</i></div>
      <div>
        <h3>День города Москва</h3>
        <dl>
          <dt>Уровень</dt><dd>Городской</dd>
          <dt>Срок</dt><dd>2 дня</dd>
          <dt>Статус</dt><dd>Участник</dd>
          <dt>Программа</dt><dd><a href="https://ren.tv/longread/1140452-den-goroda-v-moskve-programma-prazdnichnykh-meropriiatii" target="_blank" rel="noopener">ren.tv: программа праздничных мероприятий</a></dd>
        </dl>
      </div>
    </article>
  </section>

  <div class="contact">
    <p class="label">Связаться</p>
    <h2>Напишите Андрею</h2>
    <div class="mail-row">
      <span class="mail" id="mail">velik.andrey@bk.ru</span>
      <button class="copy" id="copy" type="button">Скопировать адрес</button>
    </div>
    <p class="where">Москва</p>
  </div>
  <footer>Страница собрана из анкеты Андрея Великанова.</footer>
</div>

<script>
(function () {
  var btn = document.getElementById('copy');
  var mail = document.getElementById('mail');
  btn.addEventListener('click', function () {
    var text = mail.textContent;
    function done() {
      btn.textContent = 'Адрес скопирован';
      setTimeout(function () { btn.textContent = 'Скопировать адрес'; }, 2000);
    }
    function fallback() {
      var r = document.createRange();
      r.selectNodeContents(mail);
      var s = window.getSelection();
      s.removeAllRanges();
      s.addRange(r);
      btn.textContent = 'Выделено, нажмите «Копировать»';
    }
    try {
      navigator.clipboard.writeText(text).then(done, fallback);
    } catch (e) { fallback(); }
  });
})();
</script>
</body>
</html>
