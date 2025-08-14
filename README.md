<!DOCTYPE html>
<html lang="ckb" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>کارتى دیجیتاڵی – یادی دوو مانگەی خۆشەویستیەکەمان</title>
  <style>
    :root{
      --pink:#ffd6e7; /* پەمەی */
      --pink-2:#ffebf3;
      --red:#e11d48;  /* سور */
      --red-2:#fb7185;
      --ink:#3b082c;
      --white:#fff;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;}
    body{
      font-family: ui-rounded, system-ui, -apple-system, Segoe UI, Roboto, "Noto Naskh Arabic", "Noto Kufi Arabic", "Geeza Pro", Arial, sans-serif;
      color:var(--ink);
      background: radial-gradient(1200px 800px at 80% -10%, var(--red-2), transparent 60%),
                  radial-gradient(900px 700px at 10% 110%, var(--pink), transparent 60%),
                  linear-gradient(160deg, var(--pink-2), #fff 30%, var(--pink) 100%);
      overflow:hidden;
    }

    /* Slideshow container */
    .wrap{position:relative; height:100%; width:100%;}
    .slides{height:100%; width:100%; position:relative;}
    .slide{position:absolute; inset:0; padding:clamp(16px, 4vw, 48px);
      display:grid; place-items:center; text-align:center;
      opacity:0; transform:translateX(40px) scale(.98);
      transition:opacity .6s ease, transform .6s ease;
    }
    .slide.active{opacity:1; transform:translateX(0) scale(1);}

    /* Card look */
    .card{max-width: min(900px, 92vw); background:rgba(255,255,255,.8);
      border-radius:28px; padding:clamp(18px, 3.5vw, 36px);
      box-shadow:0 20px 60px rgba(225,29,72,.18), 0 8px 24px rgba(225,29,72,.12);
      backdrop-filter:saturate(1.2) blur(6px);
      border:1px solid rgba(225,29,72,.15);
    }
    h1{margin:.2em 0 .1em; font-size:clamp(26px, 4.2vw, 44px); color:var(--red)}
    .subtitle{font-size:clamp(16px, 2.4vw, 22px); color:var(--red-2); margin-bottom:1rem}
    .hr{height:2px; width:60%; margin:1rem auto 1.25rem; background:linear-gradient(90deg, transparent, var(--red), transparent); opacity:.5}

    .content{ text-align:justify; line-height:1.9; font-size:clamp(15px, 2.2vw, 20px); color:#5b143f; }
    .scroll{ max-height:min(58vh, 700px); overflow:auto; padding-inline: .5rem; }
    .scroll::-webkit-scrollbar{width:10px}
    .scroll::-webkit-scrollbar-thumb{background:linear-gradient(var(--red), var(--red-2)); border-radius:999px}

    /* Controls */
    .nav{position:fixed; inset-inline:0; bottom:18px; display:flex; justify-content:center; align-items:center; gap:10px; z-index:10}
    .dot{width:10px; height:10px; border-radius:50%; background:#eab5c7; border:2px solid #fff; box-shadow:0 0 0 2px rgba(225,29,72,.25); cursor:pointer; transition:transform .2s}
    .dot.active{background:var(--red); transform:scale(1.2)}

    .btn{position:fixed; top:50%; translate:0 -50%; background:var(--red); color:#fff; border:none; padding:.8rem 1rem; border-radius:999px; cursor:pointer; box-shadow:0 10px 24px rgba(225,29,72,.32); z-index:11}
    .btn:hover{filter:brightness(1.05)}
    .prev{inset-inline-start:12px}
    .next{inset-inline-end:12px}

    /* Floating popples/hearts */
    .floaters{position:fixed; inset:0; pointer-events:none; overflow:hidden; z-index:0}
    .floater{position:absolute; font-size:clamp(16px, 2.8vw, 28px); opacity:.75; animation:rise linear infinite;}
    @keyframes rise{from{transform:translateY(0) rotate(0)} to{transform:translateY(-120vh) rotate(360deg)}}

    /* Dahlia sticker (SVG) gentle breathing */
    .sticker{position:fixed; z-index:1; opacity:.9; animation:breath 5s ease-in-out infinite}
    .sticker.tl{top:8px; inset-inline-start:8px; width:90px}
    .sticker.tr{top:8px; inset-inline-end:8px; width:90px}
    .sticker.bl{bottom:8px; inset-inline-start:8px; width:100px}
    .sticker.br{bottom:8px; inset-inline-end:8px; width:110px}
    @keyframes breath{0%{transform:scale(1)} 50%{transform:scale(1.06)} 100%{transform:scale(1)}}

    /* Cute micro-anim for title letters */
    .wavy span{display:inline-block; animation:wave 1.6s ease-in-out infinite}
    .wavy span:nth-child(odd){animation-delay:.1s}
    .wavy span:nth-child(even){animation-delay:.25s}
    @keyframes wave{0%,100%{transform:translateY(0)} 50%{transform:translateY(-4px)}}

    @media (max-width:520px){ .btn{padding:.6rem .8rem} .sticker{opacity:.75} }
  </style>
</head>
<body>
  <div class="wrap" aria-live="polite">

    <!-- Stickers: Dahlia SVGs at corners -->
    <img class="sticker tl" alt="dahlia" src="data:image/svg+xml;utf8,<?xml version='1.0' encoding='UTF-8'?><svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 200'><defs><radialGradient id='g' cx='50%'><stop offset='0%' stop-color='%23ffd6e7'/><stop offset='60%' stop-color='%23ffb3c7'/><stop offset='100%' stop-color='%23e11d48'/></radialGradient></defs><g><circle cx='100' cy='100' r='14' fill='%23e11d48'/><?xml version='1.0'?><!-- petals --><?xml version='1.0'?><g fill='url(%23g)'>"+Array(12).fill(0).map((_,i)=>`<ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(${i*30} 100 100)'/>`).join('')+"</g></g></svg>" />
    <img class="sticker tr" alt="dahlia" src="data:image/svg+xml;utf8,<?xml version='1.0' encoding='UTF-8'?><svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 200'><defs><radialGradient id='g' cx='50%'><stop offset='0%' stop-color='%23ffe1ec'/><stop offset='60%' stop-color='%23ffc4d8'/><stop offset='100%' stop-color='%23fb7185'/></radialGradient></defs><g><circle cx='100' cy='100' r='14' fill='%23fb7185'/><g fill='url(%23g)'><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(0 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(30 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(60 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(90 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(120 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(150 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(180 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(210 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(240 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(270 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(300 100 100)'/><ellipse cx='100' cy='35' rx='16' ry='46' transform='rotate(330 100 100)'/></g></g></svg>" />
    <img class="sticker bl" alt="dahlia" src="data:image/svg+xml;utf8,<?xml version='1.0' encoding='UTF-8'?><svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 200'><defs><radialGradient id='g' cx='50%'><stop offset='0%' stop-color='%23ffd6e7'/><stop offset='60%' stop-color='%23ffc7db'/><stop offset='100%' stop-color='%23e11d48'/></radialGradient></defs><g><circle cx='100' cy='100' r='12' fill='%23e11d48'/><g fill='url(%23g)'>"+Array(10).fill(0).map((_,i)=>`<ellipse cx='100' cy='40' rx='14' ry='42' transform='rotate(${i*36} 100 100)'/>`).join('')+"</g></g></svg>" />
    <img class="sticker br" alt="dahlia" src="data:image/svg+xml;utf8,<?xml version='1.0' encoding='UTF-8'?><svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 200'><defs><radialGradient id='g' cx='50%'><stop offset='0%' stop-color='%23ffe6f0'/><stop offset='60%' stop-color='%23ffcfe0'/><stop offset='100%' stop-color='%23fb7185'/></radialGradient></defs><g><circle cx='100' cy='100' r='12' fill='%23fb7185'/><g fill='url(%23g)'>"+Array(16).fill(0).map((_,i)=>`<ellipse cx='100' cy='30' rx='12' ry='38' transform='rotate(${i*22.5} 100 100)'/>`).join('')+"</g></g></svg>" />

    <!-- Slides -->
    <div class="slides" id="slides">
      <!-- Slide 1: Title -->
      <section class="slide active" aria-label="title">
        <div class="card">
          <h1 class="wavy">
            <span>ی</span><span>ا</span><span>د</span><span>ی</span>
            <span>&nbsp;</span>
            <span>د</span><span>و</span><span>و</span>
            <span>&nbsp;</span>
            <span>م</span><span>ا</span><span>ن</span><span>گە</span><span>ی</span>
            <span>&nbsp;</span>
            <span>خ</span><span>ۆ</span><span>ش</span><span>ە</span><span>و</span><span>ی</span><span>س</span><span>ت</span><span>ی</span><span>ە</span><span>ک</span><span>ە</span><span>م</span>
          </h1>
          <div class="subtitle">(بۆ دالیایــی عبدالله)</div>
          <div class="hr"></div>
          <div class="content" style="text-align:center">💗🌸💍 هەموو شتەکانمان بۆ یەکترە 💍🌸💗</div>
        </div>
      </section>

      <!-- Slide 2: Full message (intact) -->
      <section class="slide" aria-label="message">
        <div class="card">
          <div class="content scroll">
            <p>
(یادی دوو مانگە….<br/>
ئێستا کاتژمێر ١٢یشەو ڕۆژی هەینی بەرواری ١٥/٨/٢٠٢٥ واتای ئەوەیە دوو مانگی ڕێک تێپەڕی بە پەیوەندی نێوان منو گوڵە سپیەکەی من🌚🤍💍جا ئەمەوێت بە چەند وشەیەکی سادە پیرۆزبایی بکەم لە خۆم و خۆت بەشکم بتوانم تۆزێک لەو حالە ناخۆشەی ئێستا تێیداین تۆزێک بیرت بچێتەوە شازادەکەی من….ئازیزی من بونی تۆ لەسەر ئەم هەسارەیە شتێکە کە دڵنیابە زۆر زۆر گرنگە بۆمن چونکە جێگایەک هەیە بە تۆ نەبێت بە کەسیتر پڕ ناکرێتەوە و وەکەسیش ناتوانیت پڕی کاتەوە بۆم چونکە ئەو شوێنە کۆمەڵێکی زۆر لە داواکاری و مەرجی گرانی هەیە کەتەنها تۆ پێت قبوڵ ئەکرێت🌚💍🫂💕تەنها لەپێناو منیش قبوڵت کردوە هەر بۆیە من ئەڵێم الحمدلله کەخودای گەورە رۆحێکی داوە بەتۆ… من پێت ناڵێم دڵخۆشبە چونکە ئەوە ئیشی منە تۆ دڵخۆشت بکەم..ئەوەی من لەمڕۆژەی یادی دوو مانگەمان و لەوحالەی تێیداین لێتم ئەوێت ئەمەوێت ئەوەیە کە هەمووکات بە هیواوە بژی هیچ کات لەبیری مەکە ناخۆشییەکانی ژیان هەمیشەی نین بۆیە تۆ لە خۆشییەکانت خۆشی ببینە وەلەوکێشانەی دێتە پێشمان دەرس وەربگرین ئەزانم ئەو کێشانەش ناخۆشە دڵی تۆ منی ئەوێت بەس گیانەکەم ئەبێت سەبر بگرین و چاک ئەبێت بەخوا هەر دوعا ئەکام ئەو ناخۆشەیانە بە خۆشیەکی حەلال کۆتایبێت من زۆر لەوە دڵیان ئەوە باجی ئەە هەڵانە بوو کە کردبومان باجی ئەو بەڵێنانەبو کەە دابومانوو بەڵام ئەمان شکاند بەڵام بەهەر حال ان شااءالله بەیەکجاری کۆتای هات لەلایان خوداوە ئاگادار کراینەوە..با ئەم مەسەلەیە جاڕی ببەینە لایە تر ئەمرۆ پێویستە منو تۆ دڵخۆشبین بۆیە بەو شتانە دڵی خۆمان توند ناکەین…شازادەکەی من’من هەمووکات لەگەڵتم هەرگیز جێت ناهێڵم هەر شتێکیش ڕو بدات هەرر شتێک…!!!مەگەر بەس مردن ئەویش چونکە لەدەسەڵاتی من نیە بەڵام دوای مردنیشم لە دونایاکەی تر دێمەوە ڕێت بەڵێن بێت…
            </p>
            <p>
‏‎قسەکانی من بۆتۆ زۆر زۆر زۆرن بەڵام نازانم بەچی وشەیەک دەریان ببڕم هیچ وشەیەک نادۆزمەوە هەستەکانی ناخمی بە ١٠٠٪ تێدا دەرببرم….<br/>
ئەزانیئەمڕۆ وا هەستەکەم ئاسمان لە هەموو ڕۆژەکانی تر گەشاوەترە..؟؟لەبەر ئەوەی ئەمڕۆ پەیوەبدیەکەم لەگەڵ گەوهەرێکی درەوشاوەتر لەوانی تر بوو بە ٢ مانگ هەرچەندە ٢ مانگ زۆر نیە هێشتان بەس بۆمن زۆر زۆر زۆر زۆرە هەر دەقەیەکی نا هەرچرکەیەکی ئەم دوو مانگە پڕبوە لە یادگاری خۆش و کەمترین شتی ناخۆش ئەسڵەن شتە ناخۆشەکانی تۆش بۆمن زۆر زۆر خۆشبوە هەموی چێژێکی تایبەتیان هەبوە تورە بونەکانت عاجز بونەکانت ئەوکاتانەی ئەتووت تورەم با جیابینەوە😂🥹💍والله پێکەنین دای ئەگرتم چونکە ئەمزانی ئەگەر لەبەردەمم بویتایە ئەو قسەو کردایە چ لار و لەنجەیەکو بۆ ئەکردم🥹😂جا خۆری خۆشبەختی من ئەمەوێت لەگەڵ زەرەخەنەکانت و پێکەنینەکانت ولەگەڵ دەنگت و لەگەڵ چاوە گەشەكانت لەگەڵ قژە تەیارەکاڵەکەو و لەگەڵ هەموو شتێک کە پەیوەندی بەتۆوە هەیە بم….بۆ هەتا هەتایە تاا مردن لە دونیا لە بەهەشتیش تا هەتا هەتایە..
            </p>
            <p>
ئەیگەورەتریب دیاری خودا بۆمن ئەزانی تۆ ئەگەر هەر چەندە دڵم توند بکەیت و خەفەتم پێ بدەیت و قسەی ڕەق و ناخۆش بکەی هێشتا من هەر تۆم ئەوێت و تۆم خۆشدەوێی تەنها یەک نازی بچوک یان یەک زەردەخەنەی بچوک هەموی لەبیری من ئەباتەوە🥹💍ئەوەش لەبەر زۆری ڕێژەی خۆشەویستیم بۆتۆ کە ئەوەنە زۆرە هەر نواتنم بڵێم بۆشتی پێوەرکەم…بەجدی لە گیانی خۆم خۆشترم ئەوێیت نامەوێت هەرگیز دڵت توند بێت یان بگریت یان ئازارو خەفەتت هەبێت هەرکاتێک کە ئەگریت دڵم ژان ئەکان ئەڵێم خۆزگە لای بوماییەو فرمێسکەکانیم بۆ بسڕیبوایە و چاویم مقچ کردایە لەباوەشم بکردایە بۆ سارێژی ئازار و خەفەتەکانی سەریم لەسەر سنگم دابنایەو ماچی سەریم بکردایە بەس لێک دورین وا ناتانم بەس هەر هیچ نەبێت ئەتوانم بە قسە تۆزێک ئازارەکانت کەم بکەمەوە توخوا دایم دڵخۆشبە چونکە دڵخۆشی تۆ دڵخۆشی منە🌚💍جا ان شااءالله لەگەڵت ئەبم تا ئەبەد نایەڵم تەنیا بیت ئەزانی بۆ...؟چونکە خۆشم ئەوێی و پێمەکرێ😏😏ئەزانی چەند ؟ نەوالله چوزانێ🥹😂من خۆم نازانم چونکە ئەوەندە زۆرە بەس بتوانیم بەشێکی بچوکی وەسف بکەم بەشکم بتوانم…بەقەد دنیا نااا دنیا زۆر لەتۆ بچوکترە بەقەد هەر ٧ چینەکەی ئاسمان کە دایمەن لە فراوان بوندایە وا خۆشەویستی منیش بۆتۆ لە زیادبون دایە..! 
            </p>
            <p>
ئەە ماوەیە بەهۆی ئەوەی کەم قسە ئەکەین بەس من هەر حالم باشە ئەزانی بۆ ؟تۆ کە بەس یەکجار یەک نامەم بۆ ئەنێری تا سەدەیەک من باش و ئاسودە ئەبم…تۆ نازانی ژیانی منت چەند جوان کردووە بە شیرینی قسەکانت،بەوەی کە داوای هەرشتێک ئەکەم بەگوێم ئەکەیت…! بە جوانی چاوە گەشە كانت و برژانگە درێژەکانت..!ڕووناکی ژیانم تۆ باشترینی دنیای منی ئەمەوێ دووکات لەگەڵ تۆبم ئێستا کاتێک زیندوم دووەم کاتێک دیسان زیندو ئەکرێمەوە… ئەی لە رۆحم شیرینتر دیسانەوە ئەڵێم یادی دوو مانگەمان لێپیرۆز بێت من ئەمەوێت تا ئەمرین بەیەکەوە بین…نااا وا ئەزانی ئەوەنەم ئەوێ؟؟هەڵەی ئەمەوێت کە دوبارەش زیندوو بوینەوە هەر بەیەکەو بین.!!لە بەهەشت ان شااءالله
            </p>
            <p>
‏‎خوا ویستی لەسەر بوو بە قەدەری خۆی دڵی ئێمەی بەیەک گەیاند وە بوین بەوەی کە ئێستا بەیەک ئەلێین..ھـاوڕۆح و ھاودڵ و هاو ‎ژیان…! ئەزانی ژیانمانایەکی تری ھەیە لەگەڵ تۆ.؟ھێندەی هەموو گەردون دڵخۆش و بەختەوەرم بە بوونت زۆر ئاسودەم کەتۆ هەیت لەژیانم….نااا ئاسودە نیم کەتۆم هەیە تۆ ئاسودەیی منیت چونکە..!من و تۆ لە سەرەتای یەکتر ناسینمان نەبوین بە خۆشەویستی یەکتری بەڵام دەمەوێت ئێستس کە خۆشەویست و هاوژیانی یەکترین تە هەتا هەتایە لەگەل یەکتری بین💍🌚💕دیسانەوە یادی دوو مانگەمان پیرۆزبێت ان شااءالله هەموو ژیانمان لەگەل یەکتری بەسەر ئەبەین ئەی جوانترین و باشترینو خۆشەویسترین و ئازیزترینی دڵی من💍🌚🥹🫂🤍🎀🫰🏽💕🫶🏽🫀بشمبورە نامەکان زۆرن ماندوو ئەبیت بە خوێندەوەیان بەڵام هێشتان کەمن لەلای من🥲💍)
            </p>
          </div>
        </div>
      </section>
    </div>

    <!-- Controls -->
    <button class="btn prev" aria-label="پێشتر">⟨</button>
    <button class="btn next" aria-label="دواتر">⟩</button>
    <div class="nav" id="dots" aria-label="ناڤیگەیشنی شیتەکان"></div>

    <!-- Floating hearts/popples layer -->
    <div class="floaters" id="floaters" aria-hidden="true"></div>
  </div>

  <script>
    // --- Slideshow logic ---
    const slides = Array.from(document.querySelectorAll('.slide'));
    const dots = document.getElementById('dots');
    let i = 0;
    function show(n){
      slides.forEach((s,idx)=> s.classList.toggle('active', idx===n));
      Array.from(dots.children).forEach((d,idx)=> d.classList.toggle('active', idx===n));
      i = n;
    }
    function next(){ show((i+1)%slides.length) }
    function prev(){ show((i-1+slides.length)%slides.length) }
    document.querySelector('.next').onclick = next;
    document.querySelector('.prev').onclick = prev;
    // dots
    slides.forEach((_,idx)=>{
      const b=document.createElement('button'); b.className='dot'; b.ariaLabel = `شیت ${idx+1}`; b.onclick=()=>show(idx); dots.appendChild(b);
    });
    show(0);

    // Optional auto-play (comment out if not needed)
    let auto = setInterval(next, 9000);
    document.addEventListener('visibilitychange',()=>{ if(document.hidden){ clearInterval(auto) } else { auto = setInterval(next, 9000) } });

    // --- Floating emojis (hearts, sparkles, popples) ---
    const EMOJIS = ['💖','💕','💍','🌸','✨','💗','🫶🏽','🎀','🌚','🤍'];
    const floaters = document.getElementById('floaters');
    function spawn(){
      const e = document.createElement('div');
      e.className='floater';
      e.textContent = EMOJIS[Math.floor(Math.random()*EMOJIS.length)];
      const left = Math.random()*100; // vw
      const dur = 8 + Math.random()*8;
      const delay = -Math.random()*10;
      e.style.left = left+'vw';
      e.style.bottom = '-40px';
      e.style.animationDuration = dur+'s';
      e.style.animationDelay = delay+'s';
      floaters.appendChild(e);
      setTimeout(()=> e.remove(), (dur+2)*1000);
    }
    for(let k=0;k<20;k++) spawn();
    setInterval(spawn, 900);
  </script>
</body>
</html>
