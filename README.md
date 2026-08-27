[index.html](https://github.com/user-attachments/files/31517108/index.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TechTerm | أكاديمية المصطلحات التقنية بالإنجليزية</title>
<style>
  :root{
    --bg:#0A0E17;
    --bg-soft:#0F1522;
    --panel:#141B2B;
    --panel-2:#1A2236;
    --line:#26314A;
    --text:#E7ECF7;
    --text-dim:#8B96AE;
    --text-dimmer:#5C6680;
    --good:#22C55E;
    --bad:#EF4444;
    --warn:#EAB308;
    --accent:#3B82F6;      /* default / overridden per-track */
    --accent-soft:rgba(59,130,246,0.14);
    --mono:"Consolas","SFMono-Regular","Menlo","Courier New",monospace;
    --sans:"Segoe UI","Tahoma","Arial",sans-serif;
  }
  body.track-cs{ --accent:#3B9DE0; --accent-soft:rgba(59,157,224,0.14); }
  body.track-ai{ --accent:#9B6BF2; --accent-soft:rgba(155,107,242,0.16); }
  body.track-sec{ --accent:#22C77E; --accent-soft:rgba(34,199,126,0.14); }

  *{box-sizing:border-box;}
  html,body{height:100%;}
  body{
    margin:0;
    background:
      radial-gradient(circle at 85% -10%, rgba(59,130,246,0.10), transparent 45%),
      radial-gradient(circle at -10% 110%, rgba(34,199,126,0.08), transparent 45%),
      var(--bg);
    color:var(--text);
    font-family:var(--sans);
    line-height:1.75;
    min-height:100vh;
  }
  .app{max-width:980px; margin:0 auto; padding:20px 16px 80px;}

  /* ---------------- header ---------------- */
  header.top{
    display:flex; align-items:center; justify-content:space-between;
    padding:10px 4px 20px;
    border-bottom:1px solid var(--line);
    margin-bottom:22px;
    flex-wrap:wrap;
    gap:10px;
  }
  .brand{display:flex; align-items:center; gap:12px; cursor:pointer;}
  .brand .logo{
    width:42px;height:42px;border-radius:10px;
    background:linear-gradient(145deg,#3B9DE0,#9B6BF2,#22C77E);
    display:flex;align-items:center;justify-content:center;
    font-family:var(--mono); font-weight:bold; color:#fff; font-size:15px;
    flex-shrink:0;
  }
  .brand h1{margin:0; font-size:18px; color:var(--text);}
  .brand p{margin:0; font-size:11.5px; color:var(--text-dim);}
  .header-actions{display:flex; gap:8px; align-items:center;}

  .icon-btn{
    background:var(--panel);
    border:1px solid var(--line);
    color:var(--text);
    border-radius:9px;
    padding:9px 14px;
    font-size:13.5px;
    cursor:pointer;
    display:inline-flex; align-items:center; gap:6px;
    font-family:var(--sans);
  }
  .icon-btn:hover{border-color:var(--accent); color:var(--accent);}

  /* ---------------- generic ---------------- */
  .screen{display:none;}
  .screen.active{display:block; animation:fadeIn .25s ease;}
  @keyframes fadeIn{from{opacity:0; transform:translateY(6px);} to{opacity:1; transform:translateY(0);}}

  .panel{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:14px;
    padding:24px;
  }
  .term-window{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:12px;
    overflow:hidden;
  }
  .term-bar{
    display:flex; align-items:center; gap:6px;
    padding:9px 14px;
    background:var(--panel-2);
    border-bottom:1px solid var(--line);
  }
  .term-bar span{width:10px;height:10px;border-radius:50%; display:inline-block;}
  .term-bar .r{background:#EF4444;} .term-bar .y{background:#EAB308;} .term-bar .g{background:#22C55E;}
  .term-bar .label{
    margin-inline-start:10px; font-family:var(--mono); font-size:11.5px; color:var(--text-dim);
  }
  .term-body{padding:22px;}

  h2.title{
    margin:0 0 6px;
    font-size:21px;
    color:var(--text);
  }
  h2.title .accent{color:var(--accent);}
  p.lead{color:var(--text-dim); font-size:14.5px; margin-top:4px;}

  .btn{
    display:inline-flex; align-items:center; gap:8px;
    background:var(--accent); color:#0A0E17;
    border:none; border-radius:9px;
    padding:12px 22px; font-size:15px; font-weight:600;
    cursor:pointer; font-family:var(--sans);
    transition:filter .15s, transform .12s;
  }
  .btn:hover{filter:brightness(1.12); transform:translateY(-1px);}
  .btn:disabled{opacity:.4; cursor:not-allowed; transform:none;}
  .btn.outline{
    background:transparent; color:var(--text); border:1.5px solid var(--line);
  }
  .btn.outline:hover{border-color:var(--accent); color:var(--accent);}
  .btn.small{padding:8px 14px; font-size:13px; border-radius:7px; font-weight:500;}
  .row-actions{display:flex; flex-wrap:wrap; gap:12px; margin-top:22px;}

  .en{font-family:var(--mono); direction:ltr; unicode-bidi:isolate;}

  /* ---------------- home / tracks ---------------- */
  .track-grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(240px,1fr)); gap:16px; margin-top:20px;}
  .track-card{
    position:relative;
    border-radius:14px;
    padding:22px;
    cursor:pointer;
    border:1px solid var(--line);
    background:var(--panel);
    overflow:hidden;
    transition:transform .15s, border-color .15s;
  }
  .track-card:hover{transform:translateY(-3px);}
  .track-card::before{
    content:""; position:absolute; inset:0 0 auto 0; height:4px;
  }
  .track-card.cs{--tc:#3B9DE0;} .track-card.ai{--tc:#9B6BF2;} .track-card.sec{--tc:#22C77E;}
  .track-card::before{background:var(--tc);}
  .track-card:hover{border-color:var(--tc);}
  .track-card .ic{font-size:30px; margin-bottom:10px;}
  .track-card h3{margin:0 0 6px; font-size:17px; color:var(--text);}
  .track-card p{margin:0; font-size:13px; color:var(--text-dim);}
  .track-card .cnt{margin-top:12px; font-family:var(--mono); font-size:11.5px; color:var(--tc);}

  /* ---------------- level grid ---------------- */
  .level-grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(190px,1fr)); gap:14px; margin-top:20px;}
  .level-card{
    border:1.5px solid var(--line);
    border-radius:12px;
    padding:18px;
    cursor:pointer;
    background:var(--panel-2);
    position:relative;
  }
  .level-card:hover{border-color:var(--accent);}
  .level-card.locked{opacity:.45; cursor:not-allowed;}
  .level-card .lv-num{font-family:var(--mono); font-size:11px; color:var(--text-dim);}
  .level-card .lv-name{font-size:17px; font-weight:bold; color:var(--text); margin:4px 0 8px;}
  .level-card .lv-status{font-size:12px; color:var(--text-dim);}
  .level-card .lv-status.done{color:var(--good);}
  .badge-lock{position:absolute; top:14px; left:14px; font-size:16px;}

  /* ---------------- lesson selector ---------------- */
  .lesson-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:14px;margin-top:20px;}
  .lesson-card{
    border:1.5px solid var(--line);border-radius:12px;padding:18px;background:var(--panel-2);
    cursor:pointer;position:relative;transition:transform .15s,border-color .15s;
  }
  .lesson-card:hover{border-color:var(--accent);transform:translateY(-2px);}
  .lesson-card.locked{opacity:.5;cursor:not-allowed;transform:none;}
  .lesson-card .lesson-num{font-family:var(--mono);font-size:11px;color:var(--text-dim);}
  .lesson-card h3{margin:5px 0 4px;font-size:16px;color:var(--text);}
  .lesson-card .lesson-en{font-family:var(--mono);font-size:11px;color:var(--accent);direction:ltr;text-align:left;}
  .lesson-card .lesson-status{font-size:12px;margin-top:10px;color:var(--text-dim);}
  .lesson-card .lesson-status.done{color:var(--good);}
  .lesson-card .lesson-status.locked{color:var(--bad);}
  .exam-card{border-color:var(--accent);background:var(--accent-soft);}
  .exam-card .lesson-status{font-weight:600;}

  /* ---------------- vocab flashcards ---------------- */
  .vocab-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(190px,1fr)); gap:14px; margin-top:14px;}
  .flashcard{height:130px; perspective:1200px; cursor:pointer;}
  .flashcard-inner{position:relative; width:100%; height:100%; transition:transform .5s; transform-style:preserve-3d;}
  .flashcard.flipped .flashcard-inner{transform:rotateY(180deg);}
  .flashcard-face{
    position:absolute; inset:0; backface-visibility:hidden;
    border-radius:11px; border:1px solid var(--line);
    padding:14px; display:flex; flex-direction:column; justify-content:center;
  }
  .flashcard-front{background:var(--panel-2);}
  .flashcard-front .term{font-family:var(--mono); font-size:15.5px; color:var(--accent); font-weight:bold; direction:ltr; text-align:left;}
  .flashcard-front .hint{font-size:11px; color:var(--text-dimmer); margin-top:8px;}
  .flashcard-back{background:var(--accent-soft); transform:rotateY(180deg); overflow:auto;}
  .flashcard-back .ar{font-size:15px; font-weight:bold; color:var(--text);}
  .flashcard-back .def{font-size:11.5px; color:var(--text-dim); margin-top:6px; line-height:1.6;}

  /* ---------------- passage / translation ---------------- */
  .passage-box{
    direction:ltr; text-align:left;
    font-family:Georgia,'Times New Roman',serif;
    font-size:17.5px; line-height:2.05;
    color:var(--text);
  }
  .word{cursor:pointer; padding:1px 2px; border-radius:4px;}
  .word:hover{background:var(--accent-soft); color:var(--accent);}
  mark.term-hit, .word.term{
    background:none;
    color:var(--accent);
    font-weight:600;
    border-bottom:2px dotted var(--accent);
    cursor:pointer;
    padding:1px 2px;
    border-radius:4px;
  }
  mark.term-hit:hover, .word.term:hover{background:var(--accent-soft);}

  .translation-panel{
    margin-top:16px;
    border:1px dashed var(--line);
    border-radius:12px;
    padding:16px 18px;
    min-height:56px;
    background:var(--panel-2);
  }
  .translation-panel.active{border-style:solid; border-color:var(--accent);}
  .tp-placeholder{color:var(--text-dimmer); font-size:13.5px;}
  .tp-row{display:flex; align-items:center; justify-content:space-between; gap:10px;}
  .tp-en{font-family:var(--mono); font-size:17px; color:var(--accent); font-weight:bold;}
  .tp-speak{
    background:var(--panel); border:1px solid var(--line); color:var(--text);
    border-radius:8px; width:34px; height:34px; cursor:pointer; font-size:15px; flex-shrink:0;
  }
  .tp-speak:hover{border-color:var(--accent);}
  .tp-ar{font-size:17px; font-weight:bold; margin-top:8px; color:var(--text);}
  .tp-def{font-size:13.5px; color:var(--text-dim); margin-top:6px; line-height:1.7;}
  .tp-notfound{font-size:13px; color:var(--text-dimmer); margin-top:8px;}

  .section-label{
    font-size:12.5px; letter-spacing:.4px; text-transform:uppercase;
    color:var(--text-dimmer); margin:26px 0 10px; font-family:var(--mono);
  }

  /* ---------------- quiz ---------------- */
  .progress-track{height:6px; background:var(--panel-2); border-radius:4px; overflow:hidden; margin-bottom:22px;}
  .progress-fill{height:100%; background:var(--accent); width:0%; transition:width .3s;}
  .quiz-prompt{font-size:16.5px; margin-bottom:16px;}
  .quiz-options{display:grid; gap:10px;}
  .quiz-opt{
    border:1.5px solid var(--line); border-radius:10px; padding:13px 16px;
    background:var(--panel-2); cursor:pointer; font-size:15px; text-align:right;
    display:flex; justify-content:space-between; align-items:center;
  }
  .quiz-opt:hover{border-color:var(--accent);}
  .quiz-opt.correct{border-color:var(--good); background:rgba(34,197,94,0.12); color:var(--good);}
  .quiz-opt.incorrect{border-color:var(--bad); background:rgba(239,68,68,0.12); color:var(--bad);}
  .quiz-opt.disabled{pointer-events:none;}

  .score-ring{
    width:120px; height:120px; border-radius:50%;
    display:flex; align-items:center; justify-content:center; flex-direction:column;
    border:6px solid var(--line); margin:0 auto 18px;
  }
  .score-ring.pass{border-color:var(--good); color:var(--good);}
  .score-ring.fail{border-color:var(--bad); color:var(--bad);}
  .score-ring .pct{font-size:26px; font-weight:bold; font-family:var(--mono);}
  .score-ring .of{font-size:11px; color:var(--text-dim);}

  .missed-list{margin-top:20px; display:flex; flex-direction:column; gap:8px;}
  .missed-item{
    display:flex; justify-content:space-between; align-items:center;
    background:var(--panel-2); border:1px solid var(--line); border-radius:9px; padding:10px 14px;
  }

  /* ---------------- dictionary tool ---------------- */
  .dict-search{
    width:100%; padding:14px 16px; border-radius:10px;
    border:1.5px solid var(--line); background:var(--panel-2); color:var(--text);
    font-size:16px; font-family:var(--sans);
  }
  .dict-search:focus{outline:none; border-color:var(--accent);}
  .dict-results{margin-top:16px; display:flex; flex-direction:column; gap:10px;}
  .dict-item{
    border:1px solid var(--line); border-radius:10px; padding:12px 16px;
    background:var(--panel-2);
  }
  .dict-item .row{display:flex; justify-content:space-between; align-items:center; gap:10px;}
  .dict-item .en{color:var(--accent); font-weight:bold; font-size:15px;}
  .dict-item .ar{font-weight:bold; font-size:15px;}
  .dict-item .def{font-size:12.5px; color:var(--text-dim); margin-top:6px;}
  .dict-tag{font-size:10.5px; color:var(--text-dimmer); font-family:var(--mono);}
  .empty-note{color:var(--text-dimmer); font-size:13.5px; text-align:center; padding:20px 0;}

  footer.tip{text-align:center; font-size:12px; color:var(--text-dimmer); margin-top:34px;}

  @media (max-width:520px){
    .term-body{padding:16px;}
    .panel{padding:18px;}
  }
</style>
</head>
<body>
<div class="app">

  <header class="top">
    <div class="brand" id="brandHome">
      <div class="logo">&lt;/&gt;</div>
      <div>
        <h1>TechTerm</h1>
        <p>أكاديمية المصطلحات التقنية — حاسوب · ذكاء اصطناعي · أمن سيبراني</p>
      </div>
    </div>
    <div class="header-actions">
      <button class="icon-btn" id="dictBtn">📖 القاموس</button>
      <button class="icon-btn" id="homeBtn">🏠 الرئيسية</button>
    </div>
  </header>

  <!-- ============ HOME / TRACKS ============ -->
  <section class="screen active" id="screen-home">
    <h2 class="title">اختر مسارك</h2>
    <p class="lead">تعلّم مئات المصطلحات التقنية المتخصصة عبر دروس وقطع قراءة مصمَّمة لطلاب الحاسوب وتكنولوجيا المعلومات، الذكاء الاصطناعي، والأمن السيبراني — من المستوى المبتدئ إلى الاحترافي.</p>
    <div class="track-grid" id="trackGrid"></div>
  </section>

  <!-- ============ LEVELS ============ -->
  <section class="screen" id="screen-levels">
    <h2 class="title" id="levelsTitle"></h2>
    <p class="lead" id="levelsLead"></p>
    <div class="level-grid" id="levelGrid"></div>
    <div class="row-actions"><button class="btn outline small" id="backHomeBtn">↩ المسارات</button></div>
  </section>

  <!-- ============ LESSONS IN LEVEL ============ -->
  <section class="screen" id="screen-lessons">
    <div class="panel">
      <h2 class="title" id="lessonsTitle"></h2>
      <p class="lead" id="lessonsLead"></p>
      <div class="lesson-grid" id="lessonGrid"></div>
      <div class="row-actions">
        <button class="btn outline small" id="backToLevelsBtn">↩ رجوع للمستويات</button>
      </div>
    </div>
  </section>

  <!-- ============ LESSON ============ -->
  <section class="screen" id="screen-lesson">
    <div class="term-window">
      <div class="term-bar">
        <span class="r"></span><span class="y"></span><span class="g"></span>
        <span class="label" id="lessonBarLabel">lesson.md</span>
      </div>
      <div class="term-body">
        <h2 class="title" id="lessonTitle"></h2>
        <p class="lead" id="lessonLead"></p>\n        <div class="section-label" id="lessonProgressLabel"></div>

        <div class="section-label">// المفردات — اضغط على البطاقة لعرض الترجمة</div>
        <div class="vocab-grid" id="vocabGrid"></div>

        <div class="section-label">// نص القراءة — اضغط أي كلمة لعرض ترجمتها</div>
        <div class="passage-box" id="passageBox"></div>
        <div class="row-actions" style="margin-top:12px;">
          <button class="btn outline small" id="listenPassageBtn">🔊 استماع للنص</button>
        </div>

        <div class="translation-panel" id="translationPanel">
          <div class="tp-placeholder">اضغط أي كلمة في النص أو أي بطاقة لعرض ترجمتها هنا.</div>
        </div>

        <div class="row-actions">
          <button class="btn" id="startLessonQuizBtn">📝 ابدأ اختبار الدرس</button>
          <button class="btn outline" id="backLevelsBtn2">↩ رجوع للمستويات</button>
        </div>
      </div>
    </div>
  </section>

  <!-- ============ QUIZ ============ -->
  <section class="screen" id="screen-quiz">
    <div class="panel">
      <h2 class="title" id="quizTitle"></h2>
      <div class="progress-track"><div class="progress-fill" id="quizProgressFill"></div></div>
      <div class="quiz-prompt" id="quizPrompt"></div>
      <div class="quiz-options" id="quizOptions"></div>
      <div class="row-actions">
        <button class="btn" id="quizNextBtn" style="display:none;">السؤال التالي</button>
      </div>
    </div>
  </section>

  <!-- ============ QUIZ RESULT ============ -->
  <section class="screen" id="screen-quiz-result">
    <div class="panel" style="text-align:center;">
      <div class="score-ring" id="scoreRing">
        <div class="pct" id="scorePct">0%</div>
        <div class="of" id="scoreOf">0 / 0</div>
      </div>
      <h2 class="title" id="resultTitle" style="text-align:center; display:block;"></h2>
      <p class="lead" id="resultText"></p>
      <div class="missed-list" id="missedList" style="text-align:right;"></div>
      <div class="row-actions" style="justify-content:center;" id="resultActions"></div>
    </div>
  </section>

  <!-- ============ DICTIONARY ============ -->
  <section class="screen" id="screen-dict">
    <h2 class="title">📖 قاموس المصطلحات التقنية</h2>
    <p class="lead">اكتب أي كلمة بالعربية أو الإنجليزية للحصول على ترجمتها العلمية بطريقة أكاديمية دقيقة، في أي من الاتجاهين.</p>
    <input type="text" class="dict-search" id="dictSearch" placeholder="اكتب مثلاً: خوارزمية أو algorithm ...">
    <div class="dict-results" id="dictResults"></div>
  </section>

  <footer class="tip">جميع الدروس والقاموس تعمل بالكامل من ملف واحد على جهازك — بدون إنترنت.</footer>
</div>

<script>
/* =========================================================
   DATA — TRACKS
========================================================= */
const TRACKS = {
  cs:{ key:"cs", name:"علوم الحاسوب وتكنولوجيا المعلومات", short:"Computer Science & IT", icon:"💻", cls:"cs" },
  ai:{ key:"ai", name:"الذكاء الاصطناعي", short:"Artificial Intelligence", icon:"🤖", cls:"ai" },
  sec:{ key:"sec", name:"الأمن السيبراني", short:"Cybersecurity", icon:"🛡️", cls:"sec" }
};
const LEVEL_KEYS = ["beginner","intermediate","advanced","professional"];
const LEVEL_LABELS = { beginner:"مبتدئ", intermediate:"متوسط", advanced:"متقدم", professional:"احترافي" };

/* =========================================================
   DATA — VOCAB + PASSAGES
========================================================= */
const VOCAB = {
cs:{
 beginner:[
  {en:"computer", ar:"حاسوب", def:"جهاز إلكتروني يقوم بمعالجة البيانات وتنفيذ التعليمات وفق برنامج مخزَّن."},
  {en:"hardware", ar:"عتاد (مكونات مادية)", def:"المكونات المادية الملموسة للحاسوب مثل المعالج والذاكرة والشاشة."},
  {en:"software", ar:"برمجيات", def:"مجموعة البرامج والتعليمات التي تشغّل الحاسوب وتوجّه عمل عتاده."},
  {en:"file", ar:"ملف", def:"وحدة مخزَّنة من البيانات تحمل اسمًا ويمكن حفظها أو فتحها أو نقلها."},
  {en:"folder", ar:"مجلد", def:"حاوية تنظيمية تُستخدم لتجميع الملفات ذات الصلة داخل نظام التشغيل."},
  {en:"keyboard", ar:"لوحة مفاتيح", def:"وحدة إدخال تُستخدم لكتابة النصوص والأوامر إلى الحاسوب."},
  {en:"mouse", ar:"فأرة", def:"وحدة إدخال تُستخدم للتأشير والنقر على عناصر واجهة المستخدم."},
  {en:"internet", ar:"إنترنت", def:"شبكة عالمية تربط ملايين الحواسيب وتتيح تبادل المعلومات بينها."},
  {en:"password", ar:"كلمة مرور", def:"سلسلة سرّية من الرموز تُستخدم للتحقق من هوية المستخدم والوصول إلى نظام أو حساب."},
  {en:"operating system", ar:"نظام التشغيل", def:"برنامج أساسي يدير موارد الحاسوب ويوفر بيئة لتشغيل بقية البرمجيات."}
 ],
 intermediate:[
  {en:"algorithm", ar:"خوارزمية", def:"مجموعة منظمة من الخطوات المتسلسلة لحل مسألة أو تنفيذ مهمة محددة."},
  {en:"variable", ar:"متغيّر", def:"عنصر برمجي يُستخدم لتخزين قيمة يمكن أن تتغيّر أثناء تنفيذ البرنامج."},
  {en:"function", ar:"دالة", def:"وحدة برمجية مستقلة تنفّذ مهمة محددة ويمكن استدعاؤها عدة مرات."},
  {en:"loop", ar:"حلقة تكرارية", def:"بنية برمجية تُستخدم لتكرار تنفيذ مجموعة من التعليمات عدة مرات."},
  {en:"array", ar:"مصفوفة", def:"بنية بيانات تخزّن مجموعة من العناصر المتشابهة النوع تحت اسم واحد."},
  {en:"database", ar:"قاعدة بيانات", def:"نظام منظم لتخزين البيانات واسترجاعها وإدارتها بكفاءة."},
  {en:"debugging", ar:"تنقيح الأخطاء", def:"عملية اكتشاف الأخطاء البرمجية وتصحيحها داخل الشيفرة المصدرية."},
  {en:"compiler", ar:"مترجم (مصرّف)", def:"برنامج يحوّل الشيفرة المصدرية المكتوبة بلغة برمجة عالية إلى لغة الآلة."},
  {en:"syntax", ar:"قواعد الصياغة اللغوية", def:"مجموعة القواعد التي تحدد الشكل الصحيح لكتابة تعليمات لغة برمجية معينة."},
  {en:"version control", ar:"إدارة الإصدارات", def:"نظام يسجّل التغييرات على الشيفرة البرمجية بمرور الوقت ويتيح الرجوع إليها."}
 ],
 advanced:[
  {en:"api", ar:"واجهة برمجة التطبيقات (API)", def:"مجموعة من القواعد والبروتوكولات التي تتيح لبرنامج ما التواصل مع برنامج آخر."},
  {en:"framework", ar:"إطار عمل", def:"بنية برمجية جاهزة توفر أدوات وقواعد لتسريع بناء التطبيقات ضمن معايير موحدة."},
  {en:"cloud computing", ar:"الحوسبة السحابية", def:"تقديم موارد حاسوبية (تخزين، معالجة، برمجيات) عبر الإنترنت بدلًا من الأجهزة المحلية."},
  {en:"scalability", ar:"قابلية التوسع", def:"قدرة النظام على التعامل مع زيادة الحمل أو عدد المستخدمين دون تدهور الأداء."},
  {en:"microservices", ar:"الخدمات المصغّرة", def:"أسلوب معماري يقسّم التطبيق إلى خدمات مستقلة صغيرة تتواصل فيما بينها."},
  {en:"latency", ar:"زمن الاستجابة (الكمون)", def:"الفترة الزمنية التي يستغرقها النظام للاستجابة لطلب معين."},
  {en:"concurrency", ar:"التزامن", def:"قدرة النظام على تنفيذ عدة مهام في الوقت نفسه أو التداخل بينها."},
  {en:"containerization", ar:"الحوسبة بالحاويات", def:"تقنية لتغليف التطبيق مع بيئته التشغيلية في وحدة معزولة قابلة للنقل تُسمى حاوية."},
  {en:"load balancing", ar:"موازنة الحمل", def:"توزيع الطلبات الواردة على عدة خوادم لتحسين الأداء وضمان الاستقرار."},
  {en:"technical debt", ar:"الدين التقني", def:"التكلفة المستقبلية الناتجة عن اختيار حلول برمجية سريعة وغير مثالية لتوفير الوقت حاليًا."}
 ],
 professional:[
  {en:"distributed systems", ar:"الأنظمة الموزعة", def:"أنظمة تتكون من عدة حواسيب مستقلة تتعاون فيما بينها لتبدو للمستخدم كنظام واحد متكامل."},
  {en:"fault tolerance", ar:"تحمّل الأعطال", def:"قدرة النظام على مواصلة العمل بشكل صحيح حتى عند حدوث أعطال في بعض مكوناته."},
  {en:"consensus algorithm", ar:"خوارزمية الإجماع", def:"إجراء يتيح لعدة عقد في نظام موزّع الاتفاق على قيمة واحدة رغم احتمال حدوث أعطال."},
  {en:"eventual consistency", ar:"الاتساق النهائي", def:"نموذج بيانات يضمن أن جميع نسخ البيانات ستتطابق في النهاية دون ضمان تطابقها الفوري."},
  {en:"asynchronous programming", ar:"البرمجة غير المتزامنة", def:"أسلوب برمجي يسمح بتنفيذ عمليات متعددة دون انتظار انتهاء كل عملية قبل بدء التالية."},
  {en:"software architecture", ar:"هندسة البرمجيات المعمارية", def:"التصميم البنيوي رفيع المستوى لنظام برمجي، يحدد مكوناته وعلاقاتها ومبادئه التوجيهية."},
  {en:"formal verification", ar:"التحقق الصوري (الرسمي)", def:"أسلوب رياضي يُستخدم لإثبات صحة البرنامج مقابل مواصفات محددة إثباتًا قاطعًا."},
  {en:"computational complexity", ar:"التعقيد الحسابي", def:"دراسة الموارد (الزمن والذاكرة) اللازمة لتنفيذ خوارزمية معينة مع نمو حجم المدخلات."},
  {en:"idempotency", ar:"اللاتغيّرية (الإدمبوتنسية)", def:"خاصية العملية التي تعطي النتيجة نفسها بغض النظر عن عدد مرات تنفيذها."},
  {en:"observability", ar:"قابلية الرصد", def:"القدرة على فهم الحالة الداخلية للنظام من خلال مخرجاته مثل السجلات والمقاييس والتتبع."}
 ]
},
ai:{
 beginner:[
  {en:"artificial intelligence", ar:"الذكاء الاصطناعي", def:"فرع من علوم الحاسوب يهدف إلى بناء أنظمة قادرة على أداء مهام تتطلب عادة ذكاءً بشريًا."},
  {en:"machine learning", ar:"تعلّم الآلة", def:"فرع من الذكاء الاصطناعي يمكّن الحاسوب من التعلّم من البيانات وتحسين أدائه دون برمجة صريحة لكل حالة."},
  {en:"data", ar:"بيانات", def:"مجموعة من الحقائق أو القيم الخام التي تُجمع وتُعالج لاستخلاص معلومات مفيدة منها."},
  {en:"model", ar:"نموذج", def:"تمثيل رياضي أو حسابي يتعلّمه النظام من البيانات لأداء مهمة مثل التصنيف أو التنبؤ."},
  {en:"training", ar:"تدريب (النموذج)", def:"عملية تعليم النموذج من خلال عرض بيانات عليه وتعديل معاملاته لتحسين أدائه."},
  {en:"prediction", ar:"تنبؤ", def:"الناتج الذي يقدّمه النموذج بناءً على مدخلات جديدة استنادًا لما تعلّمه سابقًا."},
  {en:"dataset", ar:"مجموعة بيانات", def:"مجموعة منظمة من البيانات تُستخدم لتدريب النموذج أو اختباره."},
  {en:"chatbot", ar:"روبوت محادثة", def:"برنامج يحاكي المحادثة البشرية ويتفاعل مع المستخدمين عبر النص أو الصوت."},
  {en:"accuracy", ar:"الدقة", def:"مقياس يوضح نسبة التنبؤات الصحيحة التي يحققها النموذج من إجمالي التنبؤات."},
  {en:"automation", ar:"الأتمتة", def:"استخدام التقنية لتنفيذ مهام كانت تتطلب تدخلًا بشريًا دون تدخل مباشر من الإنسان."}
 ],
 intermediate:[
  {en:"neural network", ar:"الشبكة العصبية", def:"نموذج حاسوبي مستوحى من بنية الدماغ البشري، يتكوّن من طبقات مترابطة من العقد الاصطناعية."},
  {en:"deep learning", ar:"التعلّم العميق", def:"فرع من تعلّم الآلة يعتمد على شبكات عصبية متعددة الطبقات لمعالجة بيانات معقدة كالصور والنصوص."},
  {en:"supervised learning", ar:"التعلّم الموجَّه (تحت الإشراف)", def:"أسلوب تعلّم يُدرَّب فيه النموذج على بيانات موسومة تحمل إجابات صحيحة معروفة مسبقًا."},
  {en:"unsupervised learning", ar:"التعلّم غير الموجَّه", def:"أسلوب تعلّم يكتشف فيه النموذج الأنماط في بيانات غير موسومة دون إجابات معروفة مسبقًا."},
  {en:"overfitting", ar:"الإفراط في التخصيص (فرط التوافق)", def:"حالة يحفظ فيها النموذج بيانات التدريب بدقة عالية لكنه يفشل في التعميم على بيانات جديدة."},
  {en:"feature", ar:"سمة (خاصية)", def:"متغيّر مُدخل يُستخدم لوصف البيانات ويساعد النموذج على التعلّم واتخاذ القرار."},
  {en:"natural language processing", ar:"معالجة اللغة الطبيعية", def:"فرع من الذكاء الاصطناعي يُعنى بتمكين الحاسوب من فهم اللغة البشرية ومعالجتها وتوليدها."},
  {en:"computer vision", ar:"الرؤية الحاسوبية", def:"فرع من الذكاء الاصطناعي يُعنى بتمكين الحاسوب من فهم الصور ومقاطع الفيديو وتحليلها."},
  {en:"classification", ar:"التصنيف", def:"مهمة تعلّم آلي تهدف إلى تحديد الفئة التي تنتمي إليها بيانات مُدخلة معينة."},
  {en:"hyperparameter", ar:"معامل فائق", def:"إعداد يُحدَّد قبل بدء عملية تدريب النموذج ويؤثر في كيفية تعلّمه، كمعدل التعلّم."}
 ],
 advanced:[
  {en:"transformer", ar:"المحوّل (المُحوِّل العصبي)", def:"بنية شبكة عصبية تعتمد على آلية الانتباه، وتُعد الأساس وراء أغلب نماذج اللغة الحديثة."},
  {en:"attention mechanism", ar:"آلية الانتباه", def:"آلية تتيح للنموذج التركيز على الأجزاء الأكثر أهمية من المدخلات عند معالجة كل عنصر فيها."},
  {en:"embedding", ar:"التضمين", def:"تمثيل رقمي كثيف للكلمات أو البيانات في فضاء متعدد الأبعاد بحيث تعكس المسافات بينها التشابه في المعنى."},
  {en:"fine-tuning", ar:"الضبط الدقيق", def:"عملية إعادة تدريب نموذج مُدرَّب مسبقًا على بيانات محددة لتخصيصه لمهمة أو مجال جديد."},
  {en:"reinforcement learning", ar:"التعلّم المعزَّز", def:"أسلوب تعلّم يتخذ فيه عميل ذكي قرارات ضمن بيئة، ويتعلّم من خلال المكافآت والعقوبات."},
  {en:"gradient descent", ar:"الانحدار التدريجي", def:"خوارزمية تحسين تُستخدم لتعديل معاملات النموذج تدريجيًا بهدف تقليل قيمة دالة الخسارة."},
  {en:"loss function", ar:"دالة الخسارة", def:"دالة رياضية تقيس مدى ابتعاد تنبؤات النموذج عن القيم الصحيحة الفعلية."},
  {en:"generative model", ar:"النموذج التوليدي", def:"نموذج قادر على إنشاء بيانات جديدة (نصوص أو صور) مشابهة للبيانات التي تدرّب عليها."},
  {en:"bias", ar:"التحيّز (في الذكاء الاصطناعي)", def:"ميل منهجي غير مقصود في تنبؤات النموذج، غالبًا بسبب عدم توازن في بيانات التدريب."},
  {en:"inference", ar:"الاستدلال", def:"مرحلة استخدام نموذج مدرَّب لتوليد تنبؤات على بيانات جديدة بعد انتهاء مرحلة التدريب."}
 ],
 professional:[
  {en:"large language model", ar:"النموذج اللغوي الكبير (LLM)", def:"نموذج تعلّم عميق ضخم مُدرَّب على كميات هائلة من النصوص، قادر على فهم اللغة الطبيعية وتوليدها."},
  {en:"llm", ar:"النموذج اللغوي الكبير", def:"اختصار Large Language Model — نموذج تعلّم عميق ضخم مُدرَّب على كميات هائلة من النصوص."},
  {en:"tokenization", ar:"التقطيع الرمزي (التوكنة)", def:"عملية تقسيم النص إلى وحدات أصغر تسمى رموزًا (tokens) قابلة للمعالجة من قبل النموذج."},
  {en:"hallucination", ar:"الهلوسة (في الذكاء الاصطناعي)", def:"إنتاج النموذج لمعلومات تبدو منطقية لكنها غير صحيحة أو غير مدعومة بالحقائق."},
  {en:"alignment", ar:"المواءمة (التوافق القيمي)", def:"مجال بحثي يهدف إلى جعل سلوك أنظمة الذكاء الاصطناعي متوافقًا مع قيم وأهداف الإنسان."},
  {en:"prompt engineering", ar:"هندسة التوجيه (هندسة المُدخلات)", def:"ممارسة صياغة المُدخلات النصية بعناية للحصول على أفضل استجابة ممكنة من نموذج لغوي."},
  {en:"retrieval-augmented generation", ar:"التوليد المعزَّز بالاسترجاع (RAG)", def:"أسلوب يدمج بحثًا في مصادر خارجية مع توليد النص لتحسين دقة إجابات النموذج."},
  {en:"model interpretability", ar:"قابلية تفسير النموذج", def:"القدرة على فهم وشرح كيفية اتخاذ نموذج الذكاء الاصطناعي لقراراته الداخلية."},
  {en:"emergent capability", ar:"القدرة الناشئة", def:"سلوك أو قدرة تظهر فجأة في نموذج كبير دون أن تكون موجودة أو متوقعة في النماذج الأصغر."},
  {en:"multimodal model", ar:"النموذج متعدد الوسائط", def:"نموذج قادر على معالجة وفهم أكثر من نوع واحد من البيانات في آنٍ واحد، كالنص والصورة."}
 ]
},
sec:{
 beginner:[
  {en:"cybersecurity", ar:"الأمن السيبراني", def:"مجال يُعنى بحماية الأنظمة والشبكات والبيانات من الوصول غير المصرّح به أو الهجمات."},
  {en:"malware", ar:"برمجية خبيثة", def:"برنامج مصمَّم عمدًا لإلحاق الضرر بنظام حاسوبي أو سرقة بياناته أو تعطيل عمله."},
  {en:"virus", ar:"فيروس (حاسوبي)", def:"نوع من البرمجيات الخبيثة يُلحق نفسه ببرنامج آخر وينتشر عند تشغيله."},
  {en:"firewall", ar:"جدار ناري", def:"نظام أمني يراقب حركة البيانات الداخلة والخارجة من الشبكة ويتحكم فيها وفق قواعد محددة."},
  {en:"phishing", ar:"التصيّد الاحتيالي", def:"أسلوب احتيال يهدف إلى خداع الضحية لإفشاء معلومات حساسة عبر رسائل أو مواقع مزيّفة."},
  {en:"encryption", ar:"التشفير", def:"عملية تحويل البيانات إلى صيغة غير مفهومة لحمايتها من الوصول غير المصرّح به."},
  {en:"antivirus", ar:"برنامج مكافحة الفيروسات", def:"برنامج مصمَّم لاكتشاف البرمجيات الخبيثة ومنعها وإزالتها من النظام."},
  {en:"backup", ar:"نسخة احتياطية", def:"نسخة إضافية من البيانات تُحفظ لاستعادتها في حال فقدان البيانات الأصلية أو تلفها."},
  {en:"two-factor authentication", ar:"المصادقة الثنائية العوامل", def:"إجراء أمني يتطلب إثباتين مستقلين لهوية المستخدم قبل السماح له بالدخول."},
  {en:"vulnerability", ar:"ثغرة أمنية", def:"نقطة ضعف في نظام أو برنامج يمكن استغلالها من قِبل مهاجم للوصول غير المصرّح به."}
 ],
 intermediate:[
  {en:"authentication", ar:"المصادقة", def:"عملية التحقق من هوية مستخدم أو نظام قبل منحه صلاحية الوصول إلى مورد معين."},
  {en:"authorization", ar:"التفويض (منح الصلاحيات)", def:"عملية تحديد الصلاحيات والموارد التي يُسمح لمستخدم مُصادَق عليه بالوصول إليها."},
  {en:"brute-force attack", ar:"هجوم القوة الغاشمة", def:"أسلوب هجوم يعتمد على تجربة جميع الاحتمالات الممكنة بشكل منهجي حتى الوصول إلى القيمة الصحيحة."},
  {en:"denial-of-service attack", ar:"هجوم حجب الخدمة (DoS)", def:"هجوم يهدف إلى إغراق نظام أو خادم بطلبات زائفة لجعل الخدمة غير متاحة للمستخدمين الشرعيين."},
  {en:"social engineering", ar:"الهندسة الاجتماعية", def:"أسلوب خداع نفسي يستغل الثقة البشرية للحصول على معلومات سرية أو دفع الضحية لتنفيذ إجراء."},
  {en:"ransomware", ar:"برمجية الفدية", def:"نوع من البرمجيات الخبيثة يشفّر بيانات الضحية ويطالب بدفع فدية مقابل استعادة الوصول إليها."},
  {en:"patch", ar:"رقعة أمنية (تحديث إصلاحي)", def:"تحديث برمجي صغير يهدف إلى إصلاح ثغرة أمنية أو خطأ في نظام أو برنامج."},
  {en:"intrusion detection system", ar:"نظام كشف التسلل", def:"نظام يراقب الشبكة أو النظام بحثًا عن أنشطة مشبوهة وينبّه المسؤولين عند اكتشافها."},
  {en:"vpn", ar:"الشبكة الافتراضية الخاصة (VPN)", def:"تقنية تنشئ اتصالًا مشفَّرًا وآمنًا عبر شبكة عامة، مما يخفي هوية المستخدم ويحمي بياناته."},
  {en:"penetration testing", ar:"اختبار الاختراق", def:"عملية محاكاة هجوم حقيقي على نظام بإذن مسبق، بهدف اكتشاف الثغرات الأمنية قبل استغلالها."}
 ],
 advanced:[
  {en:"zero-day vulnerability", ar:"ثغرة يوم الصفر", def:"ثغرة أمنية غير معروفة للمُطوِّرين بعد، مما يجعلها قابلة للاستغلال قبل توفر أي إصلاح."},
  {en:"sql injection", ar:"حقن SQL", def:"هجوم يستغل ثغرة في التطبيق لإدراج أوامر SQL خبيثة ضمن الاستعلامات، بهدف التلاعب بقاعدة البيانات."},
  {en:"cross-site scripting", ar:"هجوم البرمجة النصية عبر المواقع (XSS)", def:"هجوم يُدرِج فيه المهاجم شيفرة نصية خبيثة داخل صفحة ويب موثوقة لتُنفَّذ في متصفح الضحية."},
  {en:"privilege escalation", ar:"تصعيد الصلاحيات", def:"أسلوب هجومي يحصل فيه المهاجم على صلاحيات أعلى مما يفترض أن يمتلكه داخل النظام."},
  {en:"threat intelligence", ar:"استخبارات التهديدات", def:"معلومات مُحلَّلة عن التهديدات والمهاجمين المحتملين تُستخدم لاتخاذ قرارات أمنية استباقية."},
  {en:"siem", ar:"إدارة معلومات وأحداث الأمن (SIEM)", def:"نظام يجمع ويحلّل سجلات الأمن من مصادر متعددة لاكتشاف الحوادث والاستجابة لها بسرعة."},
  {en:"incident response", ar:"الاستجابة للحوادث", def:"العملية المنظمة للتعامل مع حادثة أمنية بهدف احتوائها والحد من أضرارها واستعادة النظام."},
  {en:"digital forensics", ar:"التحقيق الجنائي الرقمي", def:"علم جمع الأدلة الرقمية وتحليلها والحفاظ عليها لاستخدامها في التحقيق في حادثة أمنية."},
  {en:"attack surface", ar:"سطح الهجوم", def:"مجموع النقاط أو المسارات المحتملة التي يمكن لمهاجم استغلالها للوصول إلى نظام ما."},
  {en:"sandboxing", ar:"العزل الرقمي (البيئة المعزولة)", def:"تقنية تشغّل برنامجًا مشبوهًا داخل بيئة معزولة عن النظام الأساسي لمراقبة سلوكه دون خطر."}
 ],
 professional:[
  {en:"advanced persistent threat", ar:"التهديد المستمر المتقدم (APT)", def:"هجوم سيبراني معقد وطويل الأمد، غالبًا تنفذه جهات مدعومة بموارد كبيرة، يهدف للبقاء دون اكتشاف."},
  {en:"threat modeling", ar:"نمذجة التهديدات", def:"عملية منهجية لتحديد التهديدات المحتملة على نظام ما وتقييم مخاطرها قبل وقوعها."},
  {en:"zero trust architecture", ar:"بنية الثقة الصفرية", def:"نموذج أمني لا يمنح ثقة تلقائية لأي مستخدم أو جهاز، ويشترط التحقق المستمر من كل طلب وصول."},
  {en:"lateral movement", ar:"الحركة الجانبية", def:"أسلوب يستخدمه المهاجم بعد اختراق نظام أولي للتنقل داخل الشبكة والوصول إلى موارد إضافية."},
  {en:"supply chain attack", ar:"هجوم سلسلة التوريد", def:"هجوم يستهدف مورّدًا أو طرفًا ثالثًا موثوقًا للوصول بشكل غير مباشر إلى الهدف النهائي."},
  {en:"cryptographic protocol", ar:"البروتوكول التشفيري", def:"مجموعة قواعد رسمية تحدد كيفية تبادل البيانات المشفَّرة بأمان بين طرفين أو أكثر."},
  {en:"red team", ar:"الفريق الأحمر", def:"فريق متخصص يحاكي أساليب المهاجمين الحقيقيين لاختبار مدى صمود دفاعات المؤسسة الأمنية."},
  {en:"blue team", ar:"الفريق الأزرق", def:"فريق الدفاع المسؤول عن حماية المؤسسة ومراقبة أنظمتها والاستجابة للتهديدات الأمنية."},
  {en:"security posture", ar:"الوضع الأمني العام", def:"التقييم الشامل لمدى قوة وجاهزية دفاعات المؤسسة الأمنية في مواجهة التهديدات المحتملة."},
  {en:"regulatory compliance", ar:"الامتثال التنظيمي", def:"التزام المؤسسة بالمعايير والقوانين والتشريعات الأمنية المعمول بها في مجالها أو منطقتها."}
 ]
}
};

const PASSAGES = {
cs:{
 beginner:{titleAr:"حاسوبي في المنزل", titleEn:"My Computer at Home",
  text:"I use my computer every day for study and fun. My computer has two main parts: hardware and software. The hardware includes the screen, the keyboard, and the mouse. The software includes the operating system and many programs. I save my work in files, and I organize these files inside folders. When I want to go online, I connect to the internet. To protect my account, I always use a strong password and never share it with anyone."},
 intermediate:{titleAr:"تعلّم البرمجة", titleEn:"Learning to Program",
  text:"When you start learning to program, you must first understand a few basic ideas. An algorithm is simply a clear set of steps that solves a problem. Inside your code, a variable stores a value that can change, while a function groups instructions together so you can reuse them. If you need to repeat an action, you use a loop, and if you need to store many values together, you use an array. Most real applications also connect to a database to save information permanently. Beginners often make mistakes, so debugging is an essential skill. Before your code can run, a compiler checks its syntax and translates it into machine language. Finally, professional developers rely on version control to track every change they make."},
 advanced:{titleAr:"تصميم الأنظمة القابلة للتوسّع", titleEn:"Designing Scalable Systems",
  text:"Modern software systems must be built with scalability in mind from the very beginning. Instead of one large application, many companies now rely on microservices, where each service communicates with others through a well-defined api. These services are often deployed using containerization, which packages an application with everything it needs to run consistently across different environments. As traffic grows, load balancing distributes incoming requests across multiple servers, reducing latency and preventing any single server from being overwhelmed. Engineers must also manage concurrency carefully, since many operations happen at the same time. Choosing a proven framework can speed up development, but teams that constantly cut corners under pressure often accumulate technical debt, which becomes expensive to fix later. Most large-scale systems today run on cloud computing platforms, which offer flexibility that traditional physical servers cannot easily match."},
 professional:{titleAr:"هندسة الأنظمة الموزعة الموثوقة", titleEn:"Engineering Reliable Distributed Systems",
  text:"Building large-scale distributed systems requires engineers to reason carefully about failure. Because any component can fail at any time, fault tolerance is not optional; it must be designed into the software architecture from the start. Many distributed databases rely on a consensus algorithm so that independent nodes can agree on a single value even when some of them fail or communicate slowly. To achieve high availability, some systems accept eventual consistency instead of strict, immediate agreement across all replicas. Modern backend services also depend heavily on asynchronous programming, allowing thousands of operations to proceed without blocking one another. Well-designed apis favor idempotency, so that retrying a failed request never produces unintended side effects. Understanding computational complexity remains essential, since an inefficient algorithm can quietly become the bottleneck of an entire platform. Finally, no serious production system can be operated safely without strong observability, which gives engineers the logs, metrics, and traces needed to diagnose problems quickly."}
},
ai:{
 beginner:{titleAr:"ما هو الذكاء الاصطناعي؟", titleEn:"What Is Artificial Intelligence?",
  text:"Artificial intelligence, or AI, is the science of building computer systems that can perform tasks that usually need human intelligence. One important part of AI is machine learning, where a computer learns from data instead of following fixed instructions. To build a system like this, engineers collect a large dataset and use it for training a model. After training, the model can make a prediction on new information it has never seen before. A simple chatbot is a good example of AI in daily life, since it can understand questions and give helpful answers. Engineers often measure the accuracy of a model to know how well it performs. Today, AI is used for automation in many industries, from healthcare to transportation."},
 intermediate:{titleAr:"كيف تتعلم الآلات من البيانات؟", titleEn:"How Machines Learn from Data",
  text:"Most modern AI systems rely on a neural network, a structure loosely inspired by the human brain. When this network has many layers, we call the approach deep learning, which has proven very powerful for tasks like image recognition. There are two common approaches to training a model. In supervised learning, the model learns from labeled examples, where the correct answer is already known. In unsupervised learning, the model looks for hidden patterns in data that has no labels at all. Before training, engineers choose which feature of the data the model should pay attention to, and they carefully set several values called a hyperparameter, such as the learning rate. One common risk during training is overfitting, when a model memorizes the training data instead of learning general patterns. Two major applications of deep learning are natural language processing, which helps computers understand text, and computer vision, which helps computers understand images. A typical task in both fields is classification, where the model decides which category new input belongs to."},
 advanced:{titleAr:"داخل نماذج اللغة الحديثة", titleEn:"Inside Modern Language Models",
  text:"Most large language models today are built on the transformer architecture, which relies on an attention mechanism to decide which parts of the input matter most at every step. Before any text reaches the model, words are converted into an embedding, a dense numerical representation that captures meaning in a way the network can process. During training, a loss function measures how far the model's predictions are from the correct answer, and an algorithm called gradient descent gradually adjusts the model's internal parameters to reduce that error. Once a general-purpose model has been trained, companies often perform fine-tuning on a smaller, specialized dataset to adapt it for a particular task. Some systems go further and use reinforcement learning, where the model improves its behavior through rewards rather than fixed labels. A generative model can then be used to produce new text, images, or code. After training finishes, the model enters the inference stage, where it is actually used to answer real user requests. Researchers must remain careful about bias, since imbalanced training data can quietly shape unfair or inaccurate predictions."},
 professional:{titleAr:"التحديات التي تواجه النماذج اللغوية الكبيرة", titleEn:"Challenges Facing Large Language Models",
  text:"A large language model, often called an llm, begins processing text through tokenization, breaking sentences into smaller units the model can handle mathematically. Despite their impressive fluency, these models sometimes produce a hallucination, generating confident but incorrect information, which makes rigorous evaluation essential before real-world deployment. To reduce this risk, many organizations rely on retrieval-augmented generation, combining the model's language ability with a search over trusted external sources. Getting useful results from these systems also depends heavily on prompt engineering, since small changes in wording can significantly change the output. A deeper research challenge is model interpretability, since it remains difficult to explain exactly why a model produced a particular answer. Researchers have also observed an emergent capability in very large models, meaning certain skills appear only after the model crosses a certain scale. The broader field of alignment focuses on ensuring these increasingly capable systems, including modern multimodal model architectures that combine text, images, and audio, remain safe and genuinely useful to humans."}
},
sec:{
 beginner:{titleAr:"البقاء آمنًا على الإنترنت", titleEn:"Staying Safe Online",
  text:"Cybersecurity is about protecting computers, networks, and data from attacks and unauthorized access. One common danger is malware, which includes harmful programs such as a virus that can damage your files or steal your information. To reduce risk, most companies use a firewall to control traffic entering and leaving their network, along with antivirus software to detect and remove dangerous files. Attackers often try phishing, sending fake messages that trick people into revealing passwords or personal details. To protect sensitive information, experts recommend encryption, which turns readable data into a secret code. It is also wise to keep a regular backup of important files and enable two-factor authentication on your accounts. Finally, every system may contain a vulnerability, a weakness that attackers could try to exploit, so keeping software updated is essential."},
 intermediate:{titleAr:"التهديدات الشائعة وسبل الدفاع", titleEn:"Common Threats and Defenses",
  text:"Before granting access to any system, security relies on two related steps. First comes authentication, verifying that a user really is who they claim to be, followed by authorization, which determines exactly what that user is allowed to do. Attackers use many methods to break through these defenses. A brute-force attack tries every possible password combination, while a denial-of-service attack floods a server with traffic until it becomes unavailable to real users. Not every attack targets technology directly; social engineering manipulates human trust to trick employees into giving away sensitive information. One of the most damaging threats today is ransomware, which encrypts a victim's files and demands payment for their release. To defend against these threats, organizations regularly install a patch to fix known weaknesses, deploy an intrusion detection system to monitor for suspicious activity, and encourage employees to use a vpn when working remotely. Many companies also hire security experts to perform penetration testing, safely simulating real attacks to find weaknesses before criminals do."},
 advanced:{titleAr:"داخل مركز عمليات أمنية حديث", titleEn:"Inside a Modern Security Operations Center",
  text:"Security teams face a constantly shifting landscape of threats. A zero-day vulnerability is especially dangerous because attackers can exploit it before a fix even exists. Web applications remain common targets: a sql injection attack can manipulate a database through unfiltered input, while cross-site scripting allows attackers to run malicious code inside a victim's browser. Once inside a system, attackers often attempt privilege escalation to gain administrator-level control. To stay ahead of these threats, security teams rely on threat intelligence to understand attacker behavior, and they use a siem platform to collect and analyze logs from across the entire organization in real time. When an actual breach occurs, a well-prepared incident response plan helps contain the damage quickly, and digital forensics specialists later examine what happened. Reducing the overall attack surface, the total number of exposed entry points, is one of the most effective long-term defenses. Analysts also frequently use sandboxing to safely observe how suspicious files behave without putting real systems at risk."},
 professional:{titleAr:"الدفاع في مواجهة الخصوم المتقدّمين", titleEn:"Defending Against Advanced Adversaries",
  text:"The most sophisticated attacks organizations face today often come from an advanced persistent threat, a well-resourced adversary willing to remain hidden inside a network for months while pursuing a specific objective. Defending against such adversaries starts with rigorous threat modeling, systematically identifying where a system is most likely to be attacked before any incident occurs. Many organizations are now shifting toward a zero trust architecture, which assumes no user or device should be trusted automatically, even inside the corporate network. Once attackers gain an initial foothold, they frequently attempt lateral movement, quietly spreading through connected systems to reach more valuable targets. Some of the most damaging incidents in recent years have originated from a supply chain attack, where a trusted vendor is compromised in order to reach the real target indirectly. Strong defenses also depend on a well-designed cryptographic protocol to protect data in transit. To continuously test their defenses, mature organizations maintain both a red team, which simulates real attacker techniques, and a blue team, which detects and responds to those simulated attacks. Together, these efforts help leadership understand the organization's overall security posture and ensure ongoing regulatory compliance."}
}
};

/* =========================================================
   DATA — LESSONS
   كل مستوى يحتوي على 3 دروس مستقلة، ويُبنى محتوى كل درس
   من مصطلحاته وقطعة القراءة الخاصة به.
========================================================= */
const LESSON_META = {"cs":{"beginner":[{"titleAr":"أساسيات الحاسوب ومكوّناته","titleEn":"Lesson 1","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"الملفات وأدوات الاستخدام","titleEn":"Lesson 2","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"نظام التشغيل والاتصال والحماية","titleEn":"Lesson 3","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."}],"intermediate":[{"titleAr":"أساسيات التفكير البرمجي","titleEn":"Lesson 1","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"هياكل البيانات والتكرار","titleEn":"Lesson 2","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"التنقيح والترجمة وإدارة الإصدارات","titleEn":"Lesson 3","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."}],"advanced":[{"titleAr":"واجهات البرمجة والأطر والسحابة","titleEn":"Lesson 1","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"التوسّع والخدمات والأداء","titleEn":"Lesson 2","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"التزامن والحاويات وموازنة الحمل","titleEn":"Lesson 3","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."}],"professional":[{"titleAr":"الأنظمة الموزعة وتحمل الأعطال","titleEn":"Lesson 1","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"الاتساق والبرمجة وهندسة الأنظمة","titleEn":"Lesson 2","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."},{"titleAr":"التحقق والتعقيد والاعتمادية","titleEn":"Lesson 3","lead":"درس متكامل يجمع المصطلحات في سياق عملي باللغة الإنجليزية."}]},"ai":{"beginner":[{"titleAr":"مقدمة في الذكاء الاصطناعي","titleEn":"Lesson 1","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"النموذج والتدريب والتنبؤ","titleEn":"Lesson 2","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"البيانات والتطبيقات وقياس الأداء","titleEn":"Lesson 3","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."}],"intermediate":[{"titleAr":"الشبكات العصبية والتعلّم العميق","titleEn":"Lesson 1","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"التعلّم الموجّه وغير الموجّه","titleEn":"Lesson 2","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"السمات والتطبيقات والتصنيف","titleEn":"Lesson 3","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."}],"advanced":[{"titleAr":"المحوّلات والانتباه والتضمين","titleEn":"Lesson 1","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"الضبط الدقيق والتعلّم المعزّز","titleEn":"Lesson 2","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"الخسارة والتوليد والاستدلال والتحيّز","titleEn":"Lesson 3","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."}],"professional":[{"titleAr":"النماذج اللغوية الكبيرة والتقطيع","titleEn":"Lesson 1","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"الهلوسة والهندسة والمواءمة","titleEn":"Lesson 2","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."},{"titleAr":"RAG والتفسير والقدرات الناشئة والوسائط المتعددة","titleEn":"Lesson 3","lead":"درس متكامل يربط المصطلحات بمفاهيم الذكاء الاصطناعي في سياق عملي."}]},"sec":{"beginner":[{"titleAr":"أساسيات الأمن والبرمجيات الخبيثة","titleEn":"Lesson 1","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"الدفاع عن الشبكة وحماية البيانات","titleEn":"Lesson 2","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"المكافحة والنسخ الاحتياطي وحماية الحسابات","titleEn":"Lesson 3","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."}],"intermediate":[{"titleAr":"المصادقة والصلاحيات والهجمات","titleEn":"Lesson 1","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"الهجمات على الخدمة والهندسة الاجتماعية","titleEn":"Lesson 2","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"التحديث والكشف واختبار الاختراق","titleEn":"Lesson 3","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."}],"advanced":[{"titleAr":"ثغرات الويب وهجمات الحقن","titleEn":"Lesson 1","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"تصعيد الصلاحيات والاستخبارات وSIEM","titleEn":"Lesson 2","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"الاستجابة والتحقيق وتقليل سطح الهجوم","titleEn":"Lesson 3","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."}],"professional":[{"titleAr":"التهديدات المتقدمة ونمذجة المخاطر","titleEn":"Lesson 1","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"الحركة الجانبية وسلسلة التوريد والتشفير","titleEn":"Lesson 2","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."},{"titleAr":"الفريقان الأحمر والأزرق والحوكمة الأمنية","titleEn":"Lesson 3","lead":"درس متكامل يضع المصطلحات الأمنية داخل سياق واقعي باللغة الإنجليزية."}]}};

function getLevelLessons(trackKey, levelKey){
  const vocab = VOCAB[trackKey][levelKey];
  const meta = LESSON_META[trackKey][levelKey];
  const groups = [vocab.slice(0,3), vocab.slice(3,6), vocab.slice(6,10)];
  const originalText = PASSAGES[trackKey][levelKey].text;

  return groups.map((terms, i)=>{
    const info = meta[i];
    const sentences = originalText.split(/(?<=[.!?])\s+/).filter(sentence =>
      terms.some(term => {
        const escaped = term.en.replace(/[.*+?^${}()|[\]\\]/g,"\\$&");
        const pattern = term.en.includes(" ")
          ? new RegExp("\\b" + escaped + "\\b","i")
          : new RegExp("\\b" + escaped + "(?:s|es|ies)?\\b","i");
        return pattern.test(sentence);
      })
    );
    const keyTerms = terms.map(t=>t.en).join(", ");
    const passage = (sentences.length ? sentences.join(" ") : originalText) +
      ` Key terms in this lesson: ${keyTerms}.`;
    return {...info, index:i, terms, passage};
  });
}

/* =========================================================
   DATA — GENERAL DICTIONARY (common English words)
========================================================= */
const GENERAL_DICT = {
 "a":"أداة تنكير", "an":"أداة تنكير", "the":"أداة تعريف",
 "and":"و", "or":"أو", "but":"لكن", "if":"إذا", "so":"لذلك", "because":"لأنّ", "since":"بما أنّ / منذ",
 "while":"بينما", "when":"عندما", "where":"حيث / أين", "that":"أنّ / ذلك", "which":"الذي / التي",
 "who":"مَن", "what":"ماذا", "how":"كيف", "why":"لماذا",
 "this":"هذا", "these":"هؤلاء / هذه", "those":"أولئك / تلك", "it":"هو / هي", "its":"ملكه / خاصته",
 "they":"هم", "them":"إياهم", "their":"ملكهم", "i":"أنا", "my":"ملكي", "you":"أنت", "your":"ملكك",
 "we":"نحن", "our":"ملكنا", "he":"هو", "she":"هي", "his":"ملكه", "her":"ملكها / لها",
 "is":"يكون", "are":"يكونون", "was":"كان", "were":"كانوا", "be":"يكون", "been":"كان", "being":"كائن",
 "have":"يملك / لديه", "has":"يملك", "had":"كان لديه",
 "do":"يفعل", "does":"يفعل", "did":"فعل", "can":"يستطيع", "could":"كان يستطيع",
 "will":"سوف", "would":"كان سوف", "must":"يجب أن", "should":"ينبغي أن", "may":"قد", "might":"ربما",
 "not":"لا / ليس", "no":"لا", "yes":"نعم",
 "of":"مِن", "to":"إلى", "for":"مِن أجل", "with":"مع", "without":"بدون", "from":"مِن",
 "in":"في", "on":"على", "at":"عند", "by":"بواسطة", "about":"حول", "into":"إلى داخل",
 "through":"عبر / خلال", "across":"عبر", "between":"بين", "among":"وسط", "under":"تحت", "over":"فوق",
 "before":"قبل", "after":"بعد", "during":"أثناء", "until":"حتى",
 "also":"أيضًا", "very":"جدًا", "more":"أكثر", "most":"مُعظم", "many":"كثير", "much":"كثير",
 "some":"بعض", "any":"أيّ", "all":"كل", "each":"كل واحد", "every":"كل", "few":"قليل", "several":"عدة",
 "other":"آخر", "another":"آخر", "same":"نفسه", "different":"مختلف",
 "new":"جديد", "old":"قديم", "large":"كبير", "small":"صغير", "main":"رئيسي",
 "important":"مهم", "essential":"أساسي", "common":"شائع", "simple":"بسيط", "complex":"معقّد",
 "real":"حقيقي", "possible":"ممكن", "easy":"سهل", "difficult":"صعب", "strong":"قوي",
 "well":"جيدًا", "good":"جيد", "better":"أفضل", "best":"الأفضل",
 "often":"غالبًا", "always":"دائمًا", "never":"أبدًا", "sometimes":"أحيانًا", "usually":"عادةً",
 "today":"اليوم", "now":"الآن", "then":"ثم", "first":"أولًا", "finally":"أخيرًا",
 "together":"معًا", "instead":"بدلًا من ذلك", "however":"ومع ذلك", "therefore":"لذلك",
 "even":"حتى", "still":"لا يزال", "already":"مسبقًا", "quickly":"بسرعة", "carefully":"بعناية",
 "directly":"مباشرةً", "especially":"خصوصًا", "particularly":"على وجه الخصوص", "including":"بما في ذلك",
 "use":"يستخدم", "uses":"يستخدم", "used":"مُستخدَم", "using":"باستخدام",
 "need":"يحتاج", "needs":"يحتاج", "make":"يصنع / يجعل", "makes":"يجعل", "made":"صنع",
 "help":"يساعد", "helps":"يساعد", "allow":"يسمح", "allows":"يسمح",
 "understand":"يفهم", "learn":"يتعلّم", "learning":"التعلّم", "start":"يبدأ", "begin":"يبدأ",
 "run":"يُشغِّل / يعمل", "runs":"يعمل", "build":"يبني", "built":"مبنيّ",
 "store":"يخزّن", "stores":"يخزّن", "change":"يُغيّر", "solve":"يحل", "solves":"يحل",
 "protect":"يحمي", "protects":"يحمي", "connect":"يتصل / يربط", "process":"يعالج",
 "create":"ينشئ", "provide":"يوفّر", "provides":"يوفّر", "require":"يتطلّب", "requires":"يتطلّب",
 "reduce":"يقلّل", "increase":"يزيد", "improve":"يُحسّن", "ensure":"يضمن",
 "depend":"يعتمد", "depends":"يعتمد", "remain":"يبقى", "remains":"يبقى",
 "become":"يصبح", "becomes":"يصبح", "give":"يُعطي", "gives":"يُعطي", "share":"يشارك",
 "know":"يعرف", "means":"يعني", "called":"يُسمّى",
 "system":"نظام", "systems":"أنظمة", "example":"مثال", "part":"جزء", "parts":"أجزاء",
 "way":"طريقة", "time":"وقت", "information":"معلومات", "screen":"شاشة", "code":"شيفرة / كود",
 "language":"لغة", "machine":"آلة", "human":"بشري", "value":"قيمة", "values":"قيم",
 "network":"شبكة", "networks":"شبكات", "attack":"هجوم", "attacks":"هجمات",
 "companies":"شركات", "company":"شركة", "team":"فريق", "teams":"فرق", "user":"مستخدم", "users":"مستخدمون",
 "server":"خادم", "servers":"خوادم", "application":"تطبيق", "applications":"تطبيقات",
 "problem":"مشكلة", "task":"مهمة", "steps":"خطوات", "step":"خطوة", "step-by-step":"خطوة بخطوة",
 "correct":"صحيح", "incorrect":"غير صحيح", "answer":"إجابة", "question":"سؤال",
 "research":"بحث", "researchers":"باحثون", "engineer":"مهندس", "engineers":"مهندسون",
 "organization":"منظمة", "organizations":"منظمات"
};

/* =========================================================
   BUILD MASTER GLOSSARY MAP
========================================================= */
const MASTER_GLOSSARY_MAP = {};
Object.keys(VOCAB).forEach(trackKey=>{
  Object.keys(VOCAB[trackKey]).forEach(levelKey=>{
    VOCAB[trackKey][levelKey].forEach(v=>{
      MASTER_GLOSSARY_MAP[v.en.toLowerCase()] = { en:v.en, ar:v.ar, def:v.def, track:trackKey, level:levelKey };
    });
  });
});
const ALL_GLOSSARY = Object.values(MASTER_GLOSSARY_MAP);

/* =========================================================
   STATE + PROGRESS PERSISTENCE
========================================================= */
const state = {
  track:null, level:null, lessonIndex:null,
  currentQuiz:null, quizIndex:0, quizScore:0, quizMissed:[],
  quizMode:null // 'lesson' | 'level'
};

function loadProgress(){
  try{
    const raw = localStorage.getItem("techterm_progress_v2");
    if(raw) return JSON.parse(raw);
    // Migrate the old progress format without granting exam completion.
    const old = localStorage.getItem("techterm_progress_v1");
    if(old) return JSON.parse(old);
  }catch(e){}
  return {};
}
function saveProgress(){
  try{ localStorage.setItem("techterm_progress_v2", JSON.stringify(progress)); }catch(e){}
}
let progress = loadProgress();

function ensureProgress(track, level){
  progress[track] = progress[track] || {};
  progress[track][level] = progress[track][level] || {
    lessons:{}, examPassed:false, examScore:0
  };
  const rec = progress[track][level];
  rec.lessons = rec.lessons || {};
  return rec;
}
function isLevelUnlocked(track, levelIndex){
  if(levelIndex === 0) return true;
  const prevLevel = LEVEL_KEYS[levelIndex-1];
  return !!(progress[track] && progress[track][prevLevel] && progress[track][prevLevel].examPassed);
}
function areAllLessonsPassed(track, level){
  const rec = ensureProgress(track, level);
  return getLevelLessons(track, level).every((_,i)=> rec.lessons[i] && rec.lessons[i].passed);
}
function lessonPassed(track, level, lessonIndex){
  const rec = ensureProgress(track, level);
  return !!(rec.lessons[lessonIndex] && rec.lessons[lessonIndex].passed);
}

/* =========================================================
   UTIL
========================================================= */
function escapeHtml(s){
  return String(s).replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;");
}
function showScreen(id){
  document.querySelectorAll(".screen").forEach(s=>s.classList.remove("active"));
  document.getElementById(id).classList.add("active");
  window.scrollTo({top:0, behavior:"smooth"});
}
function setTrackTheme(trackKey){
  document.body.classList.remove("track-cs","track-ai","track-sec");
  if(trackKey) document.body.classList.add("track-"+trackKey);
}
function shuffle(arr){
  const a = arr.slice();
  for(let i=a.length-1;i>0;i--){
    const j = Math.floor(Math.random()*(i+1));
    [a[i],a[j]] = [a[j],a[i]];
  }
  return a;
}
function speak(text, rate){
  if(!('speechSynthesis' in window)) return;
  window.speechSynthesis.cancel();
  const utt = new SpeechSynthesisUtterance(text);
  utt.lang = "en-US";
  utt.rate = rate || 0.92;
  const voices = window.speechSynthesis.getVoices();
  const enVoice = voices.find(v=>v.lang && v.lang.toLowerCase().startsWith("en"));
  if(enVoice) utt.voice = enVoice;
  window.speechSynthesis.speak(utt);
}

function findTranslation(rawWord){
  const key = String(rawWord).toLowerCase().trim();
  if(MASTER_GLOSSARY_MAP[key]) return {found:true, source:"glossary", ...MASTER_GLOSSARY_MAP[key]};
  if(GENERAL_DICT[key]) return {found:true, source:"general", en:key, ar:GENERAL_DICT[key], def:null};
  const stems = [];
  if(key.endsWith("ies")) stems.push(key.slice(0,-3)+"y");
  if(key.endsWith("es")) stems.push(key.slice(0,-2));
  if(key.endsWith("s") && !key.endsWith("ss")) stems.push(key.slice(0,-1));
  if(key.endsWith("ing")) stems.push(key.slice(0,-3));
  if(key.endsWith("ed")) stems.push(key.slice(0,-2));
  if(key.endsWith("ly")) stems.push(key.slice(0,-2));
  for(const s of stems){
    if(MASTER_GLOSSARY_MAP[s]) return {found:true, source:"glossary", ...MASTER_GLOSSARY_MAP[s]};
    if(GENERAL_DICT[s]) return {found:true, source:"general", en:s, ar:GENERAL_DICT[s], def:null};
  }
  return {found:false, en:rawWord};
}

/* =========================================================
   NAVIGATION
========================================================= */
document.getElementById("brandHome").addEventListener("click", goHome);
document.getElementById("homeBtn").addEventListener("click", goHome);
document.getElementById("dictBtn").addEventListener("click", openDictionary);
document.getElementById("backHomeBtn").addEventListener("click", goHome);
document.getElementById("backToLevelsBtn").addEventListener("click", ()=> openLevels(state.track));
document.getElementById("backLevelsBtn2").addEventListener("click", ()=> openLessons(state.track, state.level));

function goHome(){
  setTrackTheme(null);
  showScreen("screen-home");
}

/* =========================================================
   HOME / TRACKS
========================================================= */
function renderTrackGrid(){
  const grid = document.getElementById("trackGrid");
  grid.innerHTML = "";
  Object.values(TRACKS).forEach(t=>{
    const totalTerms = LEVEL_KEYS.reduce((sum,lv)=> sum + VOCAB[t.key][lv].length, 0);
    const div = document.createElement("div");
    div.className = "track-card " + t.cls;
    div.innerHTML = `
      <div class="ic">${t.icon}</div>
      <h3>${t.name}</h3>
      <p class="en">${t.short}</p>
      <div class="cnt">${totalTerms} مصطلح · 4 مستويات · 12 درسًا</div>`;
    div.addEventListener("click", ()=> openLevels(t.key));
    grid.appendChild(div);
  });
}
renderTrackGrid();

/* =========================================================
   LEVELS
========================================================= */
function openLevels(trackKey){
  state.track = trackKey;
  state.level = null;
  state.lessonIndex = null;
  setTrackTheme(trackKey);

  const t = TRACKS[trackKey];
  document.getElementById("levelsTitle").innerHTML = `${t.icon} ${t.name}`;
  document.getElementById("levelsLead").textContent =
    "كل مستوى يحتوي على 3 دروس مختلفة. أكمل اختبارات الدروس ثم اجتز الاختبار النهائي لفتح المستوى التالي.";

  const grid = document.getElementById("levelGrid");
  grid.innerHTML = "";

  LEVEL_KEYS.forEach((lv, idx)=>{
    const unlocked = isLevelUnlocked(trackKey, idx);
    const p = progress[trackKey] && progress[trackKey][lv];
    const div = document.createElement("div");
    div.className = "level-card" + (unlocked ? "" : " locked");

    let status = unlocked ? "لم يبدأ بعد" : "مغلق";
    let statusCls = "";
    if(p && p.examPassed){
      status = "مكتمل ✓ (" + p.examScore + "%)";
      statusCls = "done";
    }else if(unlocked && p){
      const passedCount = getLevelLessons(trackKey,lv).filter((_,i)=>p.lessons && p.lessons[i] && p.lessons[i].passed).length;
      status = `${passedCount}/3 دروس مكتملة`;
    }

    div.innerHTML = `
      ${unlocked ? "" : '<div class="badge-lock">🔒</div>'}
      <div class="lv-num">LEVEL ${idx+1}</div>
      <div class="lv-name">${LEVEL_LABELS[lv]}</div>
      <div class="lv-status ${statusCls}">${status}</div>`;
    if(unlocked) div.addEventListener("click", ()=> openLessons(trackKey, lv));
    grid.appendChild(div);
  });

  showScreen("screen-levels");
}

/* =========================================================
   LESSON SELECTOR
========================================================= */
function openLessons(trackKey, levelKey){
  state.track = trackKey;
  state.level = levelKey;
  state.lessonIndex = null;
  setTrackTheme(trackKey);

  const t = TRACKS[trackKey];
  const idx = LEVEL_KEYS.indexOf(levelKey);
  const rec = ensureProgress(trackKey, levelKey);
  const lessons = getLevelLessons(trackKey, levelKey);
  const passedCount = lessons.filter((_,i)=>rec.lessons[i] && rec.lessons[i].passed).length;
  const allPassed = passedCount === lessons.length;

  document.getElementById("lessonsTitle").innerHTML =
    `${t.icon} ${t.name} — <span class="accent">${LEVEL_LABELS[levelKey]}</span>`;
  document.getElementById("lessonsLead").textContent =
    `اختر درسًا للدراسة. يجب اجتياز اختبار كل درس بنسبة 70% على الأقل قبل دخول الاختبار النهائي. التقدم: ${passedCount}/${lessons.length}.`;

  const grid = document.getElementById("lessonGrid");
  grid.innerHTML = "";

  lessons.forEach((lesson,i)=>{
    const passed = !!(rec.lessons[i] && rec.lessons[i].passed);
    const div = document.createElement("div");
    div.className = "lesson-card";
    div.innerHTML = `
      <div class="lesson-num">LESSON ${i+1} · ${lesson.terms.length} مصطلحات</div>
      <h3>${escapeHtml(lesson.titleAr)}</h3>
      <div class="lesson-en">${escapeHtml(lesson.titleEn)}</div>
      <div class="lesson-status ${passed ? "done" : ""}">
        ${passed ? "✓ اجتزت اختبار هذا الدرس" : "📖 ادرس المصطلحات ثم اختبر نفسك"}
      </div>`;
    div.addEventListener("click", ()=> openLesson(trackKey,levelKey,i));
    grid.appendChild(div);
  });

  const exam = document.createElement("div");
  exam.className = "lesson-card exam-card" + (allPassed ? "" : " locked");
  exam.innerHTML = `
    <div class="lesson-num">FINAL EXAM · 30 سؤالًا</div>
    <h3>🎓 الاختبار النهائي للمستوى</h3>
    <div class="lesson-en">Comprehensive Level Exam</div>
    <div class="lesson-status ${allPassed ? "done" : "locked"}">
      ${allPassed ? "✓ جميع الدروس مكتملة — ابدأ الاختبار النهائي" : `🔒 أكمل اختبارات الدروس أولًا (${passedCount}/${lessons.length})`}
    </div>`;
  if(allPassed) exam.addEventListener("click", ()=> startQuiz("level"));
  grid.appendChild(exam);

  showScreen("screen-lessons");
}

/* =========================================================
   LESSON
========================================================= */
function openLesson(trackKey, levelKey, lessonIndex){
  state.track = trackKey;
  state.level = levelKey;
  state.lessonIndex = lessonIndex;
  setTrackTheme(trackKey);

  const lessons = getLevelLessons(trackKey, levelKey);
  const lesson = lessons[lessonIndex];
  if(!lesson) return;

  const rec = ensureProgress(trackKey, levelKey);
  rec.lessons[lessonIndex] = rec.lessons[lessonIndex] || {seen:true,passed:false,score:0};
  rec.lessons[lessonIndex].seen = true;
  saveProgress();

  const t = TRACKS[trackKey];

  document.getElementById("lessonBarLabel").textContent =
    `${trackKey}/${levelKey}/lesson-${lessonIndex+1}.md`;
  document.getElementById("lessonTitle").innerHTML =
    `${t.icon} ${escapeHtml(lesson.titleAr)} — <span class="accent">${escapeHtml(lesson.titleEn)}</span>`;
  document.getElementById("lessonLead").innerHTML =
    `${escapeHtml(lesson.lead)}`;
  document.getElementById("lessonProgressLabel").textContent =
    `// الدرس ${lessonIndex+1} من ${lessons.length} — ${lesson.terms.length} مصطلحات — اختبار الدرس: 6 أسئلة`;

  const vocabGrid = document.getElementById("vocabGrid");
  vocabGrid.innerHTML = "";
  lesson.terms.forEach(v=>{
    const card = document.createElement("div");
    card.className = "flashcard";
    card.innerHTML = `
      <div class="flashcard-inner">
        <div class="flashcard-face flashcard-front">
          <div class="term en">${escapeHtml(v.en)}</div>
          <div class="hint">اضغط لعرض الترجمة والتعريف</div>
        </div>
        <div class="flashcard-face flashcard-back">
          <div class="ar">${escapeHtml(v.ar)}</div>
          <div class="def">${escapeHtml(v.def)}</div>
        </div>
      </div>`;
    card.addEventListener("click", ()=>{
      card.classList.toggle("flipped");
      renderTranslationPanel({found:true,en:v.en,ar:v.ar,def:v.def},v.en);
    });
    vocabGrid.appendChild(card);
  });

  document.getElementById("passageBox").innerHTML = renderPassageHTML(lesson.passage, lesson.terms);
  document.getElementById("passageBox").onclick = (e)=>{
    const el = e.target.closest(".word, mark.term-hit");
    if(!el) return;
    const key = el.dataset.key;
    const wordAttr = el.dataset.word;
    const result = key
      ? (MASTER_GLOSSARY_MAP[key] ? {found:true,source:"glossary",...MASTER_GLOSSARY_MAP[key]} : findTranslation(key))
      : findTranslation(wordAttr);
    renderTranslationPanel(result, el.textContent);
  };

  document.getElementById("translationPanel").classList.remove("active");
  document.getElementById("translationPanel").innerHTML =
    '<div class="tp-placeholder">اضغط أي كلمة في النص أو أي بطاقة لعرض ترجمتها هنا.</div>';

  document.getElementById("listenPassageBtn").onclick = ()=> speak(lesson.passage,0.9);
  document.getElementById("startLessonQuizBtn").onclick = ()=> startQuiz("lesson");

  showScreen("screen-lesson");
}

function renderPassageHTML(passageText, vocabList){
  const placeholders = [];
  let text = passageText;
  const terms = vocabList.slice().sort((a,b)=>
    b.en.split(" ").length - a.en.split(" ").length || b.en.length - a.en.length
  );
  terms.forEach(v=>{
    const esc = v.en.replace(/[.*+?^${}()|[\]\\]/g,"\\$&");
    const re = new RegExp("\\b(" + esc + ")\\b","gi");
    text = text.replace(re,m=>{
      const idx = placeholders.length;
      placeholders.push({display:m,key:v.en.toLowerCase()});
      return "\u0001"+idx+"\u0002";
    });
  });
  const parts = text.split(/(\u0001\d+\u0002|[A-Za-z']+)/g);
  let html = "";
  parts.forEach(p=>{
    if(p===undefined || p==="") return;
    const m=p.match(/^\u0001(\d+)\u0002$/);
    if(m){
      const ph=placeholders[parseInt(m[1])];
      html += `<mark class="term-hit" data-key="${escapeHtml(ph.key)}">${escapeHtml(ph.display)}</mark>`;
    }else if(/^[A-Za-z']+$/.test(p)){
      html += `<span class="word" data-word="${escapeHtml(p.toLowerCase())}">${escapeHtml(p)}</span>`;
    }else html += escapeHtml(p);
  });
  return html;
}

function renderTranslationPanel(result, originalDisplay){
  const panel=document.getElementById("translationPanel");
  if(result.found){
    panel.innerHTML=`
      <div class="tp-row">
        <bdi dir="ltr" class="tp-en">${escapeHtml(result.en || originalDisplay)}</bdi>
        <button class="tp-speak" data-speak="${escapeHtml(result.en || originalDisplay)}">🔊</button>
      </div>
      <div class="tp-ar">${escapeHtml(result.ar)}</div>
      ${result.def ? `<div class="tp-def">${escapeHtml(result.def)}</div>` : ""}`;
  }else{
    panel.innerHTML=`
      <div class="tp-row">
        <bdi dir="ltr" class="tp-en">${escapeHtml(originalDisplay)}</bdi>
        <button class="tp-speak" data-speak="${escapeHtml(originalDisplay)}">🔊</button>
      </div>
      <div class="tp-notfound">لم يتم العثور على ترجمة لهذه الكلمة في القاموس المتخصص.</div>`;
  }
  panel.classList.add("active");
  const btn=panel.querySelector(".tp-speak");
  if(btn) btn.addEventListener("click",ev=>speak(ev.currentTarget.dataset.speak,0.85));
}

/* =========================================================
   QUIZ ENGINE + AUDIO FEEDBACK
========================================================= */
let audioCtx = null;

function playTone(frequency, duration=0.12, type="sine", volume=0.06, delay=0){
  try{
    const AC = window.AudioContext || window.webkitAudioContext;
    if(!AC) return;
    audioCtx = audioCtx || new AC();
    if(audioCtx.state === "suspended") audioCtx.resume();
    const now = audioCtx.currentTime + delay;
    const osc = audioCtx.createOscillator();
    const gain = audioCtx.createGain();
    osc.type = type;
    osc.frequency.setValueAtTime(frequency, now);
    gain.gain.setValueAtTime(0.0001, now);
    gain.gain.exponentialRampToValueAtTime(volume, now + 0.01);
    gain.gain.exponentialRampToValueAtTime(0.0001, now + duration);
    osc.connect(gain);
    gain.connect(audioCtx.destination);
    osc.start(now);
    osc.stop(now + duration + 0.02);
  }catch(e){}
}

function playFeedbackSound(kind){
  if(kind === "correct"){
    playTone(660,0.09,"sine",0.055,0);
    playTone(880,0.13,"sine",0.055,0.08);
  }else{
    playTone(220,0.16,"sawtooth",0.045,0);
    playTone(160,0.18,"sawtooth",0.04,0.12);
  }
}

function playExamEndSound(passed){
  if(passed){
    playTone(523.25,0.13,"sine",0.06,0);
    playTone(659.25,0.13,"sine",0.06,0.12);
    playTone(783.99,0.18,"sine",0.06,0.24);
    playTone(1046.5,0.28,"sine",0.06,0.42);
  }else{
    playTone(392,0.16,"sine",0.05,0);
    playTone(329.63,0.18,"sine",0.05,0.15);
    playTone(261.63,0.28,"sine",0.05,0.32);
  }
}

function makeQuestion(v, direction, distractorPool){
  const distractors = shuffle(distractorPool.filter(x=>x.en !== v.en)).slice(0,3);
  if(direction === "en2ar"){
    return {
      prompt:`ما الترجمة العربية الصحيحة للمصطلح: <bdi dir="ltr" class="en" style="color:var(--accent);font-weight:bold;">${escapeHtml(v.en)}</bdi> ؟`,
      correctText:v.ar, options:shuffle([v.ar,...distractors.map(d=>d.ar)]),
      direction, term:v, optionType:"ar"
    };
  }
  if(direction === "ar2en"){
    return {
      prompt:`ما المصطلح الإنجليزي المقابل لـ: <b>${escapeHtml(v.ar)}</b> ؟`,
      correctText:v.en, options:shuffle([v.en,...distractors.map(d=>d.en)]),
      direction, term:v, optionType:"en"
    };
  }
  return {
    prompt:`أي مصطلح يطابق التعريف التالي؟<div style="margin-top:8px;color:var(--text-dim);font-size:14px;">${escapeHtml(v.def)}</div>`,
    correctText:v.en, options:shuffle([v.en,...distractors.map(d=>d.en)]),
    direction:"definition2en", term:v, optionType:"en"
  };
}

function buildLessonQuiz(terms){
  const questions=[];
  terms.forEach(v=>{
    questions.push(makeQuestion(v,"en2ar",ALL_GLOSSARY));
    questions.push(makeQuestion(v,"ar2en",ALL_GLOSSARY));
  });
  return shuffle(questions);
}

function buildFinalExam(terms){
  const questions=[];
  terms.forEach(v=>{
    // Every term is tested three ways: English -> Arabic,
    // Arabic -> English, and definition -> English.
    questions.push(makeQuestion(v,"en2ar",terms));
    questions.push(makeQuestion(v,"ar2en",terms));
    questions.push(makeQuestion(v,"definition2en",terms));
  });
  return shuffle(questions);
}

function startQuiz(mode){
  const trackKey=state.track, levelKey=state.level;
  const terms=VOCAB[trackKey][levelKey];

  if(mode === "lesson"){
    const lesson=getLevelLessons(trackKey,levelKey)[state.lessonIndex];
    if(!lesson) return;
    state.currentQuiz=buildLessonQuiz(lesson.terms);
    document.getElementById("quizTitle").textContent =
      `📝 اختبار الدرس ${state.lessonIndex+1} — ${lesson.titleAr}`;
  }else{
    if(!areAllLessonsPassed(trackKey,levelKey)){
      openLessons(trackKey,levelKey);
      return;
    }
    state.currentQuiz=buildFinalExam(terms);
    document.getElementById("quizTitle").textContent =
      `🎓 الاختبار النهائي الشامل — ${LEVEL_LABELS[levelKey]} (30 سؤالًا)`;
  }

  state.quizMode=mode;
  state.quizIndex=0;
  state.quizScore=0;
  state.quizMissed=[];
  renderQuizQuestion();
  showScreen("screen-quiz");
}

function renderQuizQuestion(){
  const q=state.currentQuiz[state.quizIndex];
  const total=state.currentQuiz.length;
  document.getElementById("quizProgressFill").style.width =
    Math.round((state.quizIndex/total)*100)+"%";
  document.getElementById("quizPrompt").innerHTML =
    `(${state.quizIndex+1}/${total}) ${q.prompt}`;

  const optWrap=document.getElementById("quizOptions");
  optWrap.innerHTML="";
  document.getElementById("quizNextBtn").style.display="none";

  q.options.forEach(opt=>{
    const div=document.createElement("div");
    div.className="quiz-opt";
    div.dataset.value=opt;

    if(q.optionType === "en"){
      div.innerHTML=`<bdi dir="ltr" class="en">${escapeHtml(opt)}</bdi>`;
    }else{
      div.textContent=opt;
    }

    div.addEventListener("click",()=>answerQuiz(opt,q,div));
    optWrap.appendChild(div);
  });
}

function answerQuiz(selected,q,selectedEl){
  const allOpts=document.querySelectorAll(".quiz-opt");
  allOpts.forEach(o=>o.classList.add("disabled"));

  const correct=selected===q.correctText;
  if(correct){
    state.quizScore++;
    selectedEl.classList.add("correct");
    playFeedbackSound("correct");
  }else{
    selectedEl.classList.add("incorrect");
    state.quizMissed.push(q.term);
    allOpts.forEach(o=>{
      if(o.dataset.value===q.correctText) o.classList.add("correct");
    });
    playFeedbackSound("wrong");
  }

  const nextBtn=document.getElementById("quizNextBtn");
  nextBtn.style.display="inline-flex";
  nextBtn.textContent =
    state.quizIndex===state.currentQuiz.length-1 ? "عرض النتيجة" : "السؤال التالي";

  nextBtn.onclick=()=>{
    if(state.quizIndex<state.currentQuiz.length-1){
      state.quizIndex++;
      renderQuizQuestion();
    }else{
      showQuizResult();
    }
  };
}

function showQuizResult(){
  document.getElementById("quizProgressFill").style.width="100%";

  const total=state.currentQuiz.length;
  const score=state.quizScore;
  const pct=Math.round((score/total)*100);
  const pass=pct>=70;

  const ring=document.getElementById("scoreRing");
  ring.className="score-ring "+(pass?"pass":"fail");
  document.getElementById("scorePct").textContent=pct+"%";
  document.getElementById("scoreOf").textContent=score+" / "+total;

  const titleEl=document.getElementById("resultTitle");
  const textEl=document.getElementById("resultText");

  if(state.quizMode==="lesson"){
    const rec=ensureProgress(state.track,state.level);
    rec.lessons[state.lessonIndex]=rec.lessons[state.lessonIndex] || {seen:true,passed:false,score:0};
    rec.lessons[state.lessonIndex].score=pct;
    rec.lessons[state.lessonIndex].passed=pass;
    saveProgress();

    if(pass){
      titleEl.textContent="🎉 أحسنت! اجتزت اختبار الدرس";
      textEl.textContent=
        "تم تسجيل إكمال هذا الدرس. أكمل بقية الدروس حتى يفتح لك الاختبار النهائي الشامل للمستوى.";
    }else{
      titleEl.textContent="📚 تحتاج إلى مراجعة هذا الدرس";
      textEl.textContent=
        "نسبة النجاح 70%. راجع البطاقات وقطعة القراءة ثم أعد اختبار الدرس حتى تُتقن مصطلحاته.";
    }
  }else{
    if(pass){
      const rec=ensureProgress(state.track,state.level);
      rec.examPassed=true;
      rec.examScore=pct;
      saveProgress();
      titleEl.textContent="🎓🎉 نجحت في الاختبار النهائي للمستوى!";
      textEl.textContent=
        "أحسنت! أثبتَّ معرفة المصطلحات وترجمتها وتعريفاتها. تم فتح المستوى التالي.";
    }else{
      titleEl.textContent="❌ لم تحقق نسبة النجاح المطلوبة (70%)";
      textEl.textContent=
        "الاختبار النهائي شامل لجميع مصطلحات المستوى. يجب إعادة الاختبار والنجاح فيه قبل الانتقال إلى المستوى التالي.";
    }
  }

  const missedWrap=document.getElementById("missedList");
  missedWrap.innerHTML="";
  if(state.quizMissed.length){
    const heading=document.createElement("div");
    heading.className="section-label";
    heading.style.margin="18px 0 8px";
    heading.textContent="// مصطلحات تحتاج مراجعة";
    missedWrap.appendChild(heading);

    const uniq=[];
    const seen=new Set();
    state.quizMissed.forEach(t=>{
      if(!seen.has(t.en)){
        seen.add(t.en);
        uniq.push(t);
      }
    });

    uniq.forEach(t=>{
      const row=document.createElement("div");
      row.className="missed-item";
      row.innerHTML=`
        <div>
          <bdi dir="ltr" class="en" style="color:var(--accent);font-weight:bold;">${escapeHtml(t.en)}</bdi>
          — ${escapeHtml(t.ar)}
          <div style="font-size:12px;color:var(--text-dim);margin-top:3px;">${escapeHtml(t.def)}</div>
        </div>
        <button class="tp-speak" data-speak="${escapeHtml(t.en)}">🔊</button>`;
      row.querySelector(".tp-speak").addEventListener("click",e=>
        speak(e.currentTarget.dataset.speak,0.85));
      missedWrap.appendChild(row);
    });
  }

  const actions=document.getElementById("resultActions");
  actions.innerHTML="";

  if(state.quizMode==="lesson"){
    if(pass){
      addActionBtn(actions,"📖 الدرس التالي","btn",()=>{
        const lessons=getLevelLessons(state.track,state.level);
        if(state.lessonIndex < lessons.length-1){
          openLesson(state.track,state.level,state.lessonIndex+1);
        }else{
          openLessons(state.track,state.level);
        }
      });
    }else{
      addActionBtn(actions,"🔁 إعادة اختبار الدرس","btn",()=>startQuiz("lesson"));
      addActionBtn(actions,"📖 مراجعة الدرس","btn outline",()=>
        openLesson(state.track,state.level,state.lessonIndex));
    }
    addActionBtn(actions,"📚 دروس المستوى","btn outline",()=>
      openLessons(state.track,state.level));
  }else{
    if(!pass){
      addActionBtn(actions,"🔁 إعادة الاختبار النهائي","btn",()=>startQuiz("level"));
    }else{
      const idx=LEVEL_KEYS.indexOf(state.level);
      if(idx<LEVEL_KEYS.length-1){
        addActionBtn(actions,"➡ المستوى التالي","btn",()=>{
          const nextLevel=LEVEL_KEYS[idx+1];
          openLessons(state.track,nextLevel);
        });
      }else{
        addActionBtn(actions,"🏆 إكمال المسار","btn",()=>
          openLevels(state.track));
      }
    }
    addActionBtn(actions,"📚 دروس المستوى","btn outline",()=>
      openLessons(state.track,state.level));
    addActionBtn(actions,"🏠 الرئيسية","btn outline",goHome);
  }

  // End-of-quiz sound.
  playExamEndSound(pass);
  showScreen("screen-quiz-result");
}

function addActionBtn(container,label,cls,onClick){
  const b=document.createElement("button");
  b.className=cls;
  b.textContent=label;
  b.addEventListener("click",onClick);
  container.appendChild(b);
}

/* =========================================================
   DICTIONARY TOOL
========================================================= */
function openDictionary(){
  setTrackTheme(null);
  document.getElementById("dictResults").innerHTML =
    '<div class="empty-note">اكتب كلمة أعلاه لبدء البحث في أكثر من 250 مصطلحًا وكلمة.</div>';
  document.getElementById("dictSearch").value = "";
  showScreen("screen-dict");
  setTimeout(()=> document.getElementById("dictSearch").focus(), 150);
}

document.getElementById("dictSearch").addEventListener("input", (e)=>{
  const q = e.target.value.trim().toLowerCase();
  const results = document.getElementById("dictResults");
  if(q.length < 1){
    results.innerHTML = '<div class="empty-note">اكتب كلمة أعلاه لبدء البحث في أكثر من 250 مصطلحًا وكلمة.</div>';
    return;
  }
  const glossaryHits = ALL_GLOSSARY.filter(v=>
    v.en.toLowerCase().includes(q) || v.ar.includes(q)
  );
  const generalHits = Object.keys(GENERAL_DICT)
    .filter(en=> en.includes(q) || GENERAL_DICT[en].includes(q))
    .map(en=> ({en, ar:GENERAL_DICT[en], def:null}));

  const all = glossaryHits.concat(generalHits).slice(0, 40);
  if(all.length === 0){
    results.innerHTML = '<div class="empty-note">لم يتم العثور على نتائج مطابقة.</div>';
    return;
  }
  results.innerHTML = "";
  all.forEach(v=>{
    const div = document.createElement("div");
    div.className = "dict-item";
    div.innerHTML = `
      <div class="row">
        <div>
          <bdi dir="ltr" class="en">${escapeHtml(v.en)}</bdi>
          &nbsp;—&nbsp;
          <span class="ar">${escapeHtml(v.ar)}</span>
          ${v.track ? `<div class="dict-tag">${TRACKS[v.track].short} · ${LEVEL_LABELS[v.level]}</div>` : ""}
        </div>
        <button class="tp-speak" data-speak="${escapeHtml(v.en)}">🔊</button>
      </div>
      ${v.def ? `<div class="def">${escapeHtml(v.def)}</div>` : ""}`;
    div.querySelector(".tp-speak").addEventListener("click", (ev)=> speak(ev.currentTarget.dataset.speak, 0.85));
    results.appendChild(div);
  });
});

if('speechSynthesis' in window){
  window.speechSynthesis.onvoiceschanged = ()=>{};
}
</script>
</body>
</html>
