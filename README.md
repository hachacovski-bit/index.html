<!DOCTYPE html>
<html lang="ru" class="dark">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no"/>
<title>SELENE // Lunar Dreamcore AI</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,600;0,700;1,400&family=JetBrains+Mono:wght@400;600&family=Space+Grotesk:wght@400;500;600&display=swap" rel="stylesheet"/>
<script src="https://cdn.tailwindcss.com"></script>
<script>
tailwind.config={darkMode:'class',theme:{extend:{colors:{obsidian:'#05060f',indigoNight:'#0b0e1d',silver:'#e2e8f0',lavender:'#c4b5fd',cyanGlow:'#a5f3fc',neon:'#f472b6'},fontFamily:{serif:['"Cormorant Garamond"','serif'],sans:['"Space Grotesk"','sans-serif'],mono:['"JetBrains Mono"','monospace']}}}};
</script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/styles/tokyo-night-dark.min.css"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
<script src="https://unpkg.com/lucide@latest"></script>
<script src="https://js.puter.com/v2/"></script>
<style>
:root{--glitch:0.2;--scan:0.22}
*{box-sizing:border-box;scrollbar-width:thin;scrollbar-color:rgba(196,181,253,.25) transparent}
*::-webkit-scrollbar{width:5px;height:5px}*::-webkit-scrollbar-thumb{background:rgba(196,181,253,.25);border-radius:9px}
html,body{margin:0;height:100%;width:100%;overflow:hidden;background:#05060f;color:#e2e8f0;font-family:'Space Grotesk',sans-serif}
.glass{background:linear-gradient(145deg,rgba(11,14,29,.8),rgba(5,6,15,.9));backdrop-filter:blur(16px);border:1px solid rgba(196,181,253,.16);box-shadow:0 8px 30px rgba(0,0,0,.55)}
.arch{border-radius:999px 999px 18px 18px}
.crt{pointer-events:none;position:fixed;inset:0;z-index:45;background:linear-gradient(transparent 50%,rgba(0,0,0,var(--scan)) 50%),radial-gradient(circle,transparent 58%,rgba(3,4,12,.72) 100%);background-size:100% 3px,100% 100%}
.chroma:hover{text-shadow:-1.5px 0 rgba(244,114,182,.8),1.5px 0 rgba(165,243,252,.8);box-shadow:-2px 0 12px rgba(244,114,182,.2),2px 0 12px rgba(165,243,252,.2)}
@keyframes glitch{0%,94%,100%{transform:none;filter:none}95%{transform:translate(-2px,1px) skew(-1deg);filter:hue-rotate(20deg)}97%{transform:translate(2px,-1px)}}
.glitch-fx{animation:glitch calc(11s - var(--glitch)*7s) infinite}
@keyframes burst{0%{opacity:0}30%{opacity:.75;transform:translateX(-5px)}60%{opacity:.6;transform:translateX(5px)}100%{opacity:0}}
.glitch-burst{animation:burst .3s steps(3) forwards}
@keyframes collapse{0%{filter:none}40%{filter:invert(.8) hue-rotate(160deg);transform:scale(1.03) skewX(3deg)}100%{filter:brightness(0);transform:scale(.05);opacity:0}}
.collapsing{animation:collapse 1.9s ease-in forwards}
@keyframes marquee{0%{transform:translateX(100%)}100%{transform:translateX(-100%)}}
.marquee{display:inline-block;white-space:nowrap;animation:marquee 20s linear infinite}
@keyframes blink{0%,96%,100%{transform:scaleY(1)}98%{transform:scaleY(.08)}}
.eye{animation:blink 6s infinite}.pupil{transition:transform .08s ease-out}
@keyframes spin{to{transform:rotate(360deg)}}.spin{animation:spin 3s linear infinite}
@keyframes orb{0%,100%{transform:scale(1);box-shadow:0 0 40px rgba(196,181,253,.35)}50%{transform:scale(1.07);box-shadow:0 0 85px rgba(244,114,182,.45)}}
.astral-orb{animation:orb 3.5s ease-in-out infinite}
.md{font-size:.93rem;line-height:1.65}.md h1,.md h2,.md h3{font-family:'Cormorant Garamond',serif;color:#fff;margin:.9em 0 .4em;font-weight:600}
.md h1{font-size:1.55rem;border-bottom:1px solid rgba(196,181,253,.2)}.md h2{font-size:1.3rem;color:#c4b5fd}.md h3{font-size:1.1rem;color:#a5f3fc}
.md p{margin-bottom:.65em}.md p:last-child{margin-bottom:0}.md ul{list-style:disc;margin:.4em 0 .7em 1.3em}.md ol{list-style:decimal;margin:.4em 0 .7em 1.3em}
.md blockquote{border-left:3px solid #c4b5fd;background:rgba(196,181,253,.07);padding:.5rem .8rem;margin:.6rem 0;border-radius:0 8px 8px 0;font-style:italic}
.md table{width:100%;border-collapse:collapse;margin:.7rem 0;font-size:.83rem}.md th,.md td{padding:.45rem .65rem;border:1px solid rgba(196,181,253,.18)}
.md th{background:rgba(196,181,253,.14);color:#a5f3fc}.md code:not(pre code){font-family:'JetBrains Mono',monospace;font-size:.84em;background:rgba(196,181,253,.15);color:#a5f3fc;padding:.1rem .35rem;border-radius:4px}
.code-box{margin:.7rem 0;border-radius:10px;overflow:hidden;border:1px solid rgba(196,181,253,.22);background:#070914}
.code-hd{display:flex;justify-content:space-between;align-items:center;padding:.4rem .7rem;background:rgba(196,181,253,.09);font-family:'JetBrains Mono',monospace;font-size:.72rem}
.code-box pre{margin:0;padding:.8rem;overflow-x:auto;font-family:'JetBrains Mono',monospace;font-size:.82rem}
</style>
</head>
<body class="selection:bg-lavender/30">
<canvas id="lunar-cv" class="fixed inset-0 w-full h-full z-0"></canvas>
<div id="crt" class="crt"></div>
<div id="g-flash" class="fixed inset-0 z-50 pointer-events-none opacity-0 bg-gradient-to-r from-neon/20 via-transparent to-cyanGlow/20 mix-blend-screen"></div>

<!-- Broadcast Ticker & Modal -->
<div id="bc-ticker" class="hidden fixed top-0 inset-x-0 z-40 bg-indigoNight/95 border-b border-neon/40 py-1 px-4 flex items-center gap-3">
  <span class="px-2 py-0.5 text-[10px] font-mono bg-neon/20 text-neon border border-neon/50 rounded animate-pulse">СМОТРИТЕЛЬ</span>
  <div class="flex-1 overflow-hidden"><span id="bc-ticker-txt" class="marquee font-mono text-xs text-silver"></span></div>
  <button onclick="hide('bc-ticker')" class="text-slate-400 hover:text-white">&times;</button>
</div>
<div id="bc-modal" class="hidden fixed inset-0 z-[70] flex items-center justify-center p-4 bg-black/80 backdrop-blur-md">
  <div class="glass max-w-md w-full rounded-2xl p-6 border-neon/40 text-center space-y-4">
    <h3 class="font-serif text-2xl text-white">👁️ Видение Смотрителя</h3>
    <p id="bc-modal-txt" class="text-xs font-mono text-slate-200"></p>
    <button onclick="hide('bc-modal')" class="px-5 py-2 rounded-xl bg-neon/20 border border-neon/50 text-neon text-xs font-mono">Принять</button>
  </div>
</div>

<!-- Lockdown & Ban Screens -->
<div id="lock-screen" class="hidden fixed inset-0 z-[80] flex items-center justify-center p-6 text-center bg-obsidian/95 backdrop-blur-xl">
  <div class="glass arch max-w-md w-full p-9 border-lavender/30 space-y-4">
    <button id="lock-moon" class="w-16 h-16 mx-auto rounded-full bg-lavender/15 border border-lavender/40 flex items-center justify-center cursor-pointer"><i data-lucide="moon" class="w-8 h-8 text-lavender"></i></button>
    <div class="font-mono text-[10px] tracking-[0.3em] text-neon">STASIS PROTOCOL</div>
    <h1 class="font-serif text-3xl text-white">Сон прерван</h1>
    <p id="lock-reason" class="text-sm text-slate-300"></p>
    <div id="lock-timer-box" class="hidden inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigoNight border border-cyanGlow/30 font-mono text-xs text-cyanGlow">Возврат: <b id="lock-cd">--:--</b></div>
  </div>
</div>
<div id="ban-screen" class="hidden fixed inset-0 z-[85] flex items-center justify-center p-6 text-center bg-[#060108]/95 backdrop-blur-xl">
  <div class="max-w-md w-full border border-red-500/40 bg-black/80 rounded-2xl p-8 space-y-3">
    <button id="ban-moon" class="w-14 h-14 mx-auto rounded-full bg-red-500/15 border border-red-500/40 flex items-center justify-center text-red-400 cursor-pointer"><i data-lucide="eye-off" class="w-7 h-7"></i></button>
    <div class="font-mono text-xs text-red-400 tracking-widest">ERROR 403 // EXILED</div>
    <h1 class="font-serif text-3xl text-white">Вы изгнаны из Сна</h1>
    <p class="font-mono text-xs text-slate-400">Сессия заблокирована Смотрителем Луны.</p>
  </div>
</div>

<!-- APP SHELL -->
<div class="relative z-10 flex h-full w-full overflow-hidden">
  <div id="sb-bg" onclick="toggleSb(false)" class="hidden fixed inset-0 z-20 bg-black/65 md:hidden"></div>
  <aside id="sidebar" class="fixed md:relative inset-y-0 left-0 z-30 w-72 sm:w-80 -translate-x-full md:translate-x-0 transition-transform duration-300 flex flex-col glass border-r border-lavender/15">
    <div class="p-3.5 border-b border-lavender/15 flex items-center justify-between">
      <div class="flex items-center gap-2.5">
        <button id="moon-trig" title="SELENE" class="relative w-9 h-9 rounded-full bg-lavender/20 border border-lavender/40 flex items-center justify-center cursor-pointer hover:scale-105 transition">
          <i data-lucide="moon-star" class="w-4 h-4 text-lavender"></i><span class="absolute bottom-0 right-0 w-2 h-2 rounded-full bg-cyanGlow"></span>
        </button>
        <div>
          <div class="font-serif text-xl font-bold text-white leading-none flex items-center gap-1.5">SELENE
            <svg class="eye w-5 h-3.5" viewBox="0 0 36 22" fill="none"><path d="M2 11C7 3 13 2 18 2S29 3 34 11C29 19 23 20 18 20S7 19 2 11Z" stroke="#c4b5fd" stroke-width="1.4" fill="#0b0e1d"/><circle class="pupil" cx="18" cy="11" r="4" fill="#a5f3fc"/><circle class="pupil" cx="18" cy="11" r="1.7" fill="#05060f"/></svg>
          </div>
          <p class="font-mono text-[9px] text-slate-400 tracking-widest">LUNAR DREAMCORE</p>
        </div>
      </div>
      <button onclick="toggleSb(false)" class="md:hidden text-slate-400 hover:text-white"><i data-lucide="x" class="w-5 h-5"></i></button>
    </div>

    <div class="p-2.5 space-y-2 border-b border-lavender/10">
      <button onclick="newChat()" class="chroma w-full py-2 px-3 rounded-xl bg-gradient-to-r from-lavender/20 to-cyanGlow/15 border border-lavender/35 text-xs font-medium text-white flex items-center justify-center gap-1.5"><i data-lucide="sparkles" class="w-3.5 h-3.5 text-cyanGlow"></i>Новый сон</button>
      <input id="chat-q" oninput="renderChats()" placeholder="Поиск по снам..." class="w-full px-3 py-1.5 rounded-lg bg-obsidian/70 border border-lavender/15 text-xs font-mono focus:outline-none"/>
    </div>

    <div class="px-2.5 py-2 border-b border-lavender/10">
      <div class="flex justify-between items-center mb-1.5"><span class="font-mono text-[10px] text-slate-400 uppercase">Персоны</span><button onclick="show('bot-modal')" class="text-[11px] font-mono text-cyanGlow hover:underline">+ Создать</button></div>
      <div id="bots-box" class="grid grid-cols-2 gap-1.5 max-h-32 overflow-y-auto"></div>
    </div>

    <div id="chats-box" class="flex-1 overflow-y-auto p-2 space-y-1"></div>

    <div class="p-2.5 border-t border-lavender/15 space-y-1.5 bg-obsidian/50">
      <div class="grid grid-cols-2 gap-1.5">
        <button onclick="openMem()" class="chroma py-1.5 rounded-lg bg-white/5 border border-lavender/15 text-xs flex items-center justify-center gap-1"><i data-lucide="brain" class="w-3.5 h-3.5 text-lavender"></i>Память</button>
        <button onclick="exportMd()" class="chroma py-1.5 rounded-lg bg-white/5 border border-lavender/15 text-xs flex items-center justify-center gap-1"><i data-lucide="download" class="w-3.5 h-3.5 text-cyanGlow"></i>Экспорт .md</button>
      </div>
      <div class="flex justify-between items-center px-2 py-1 rounded bg-black/40 text-[10px] font-mono text-slate-400">
        <span class="flex items-center gap-1.5"><span id="eng-dot" class="w-2 h-2 rounded-full bg-cyanGlow"></span><span id="eng-lbl">Puter Ready</span></span>
        <button onclick="toggleOffline()" class="text-lavender underline">Сменить</button>
      </div>
    </div>
  </aside>

  <!-- CENTER -->
  <main class="flex-1 flex flex-col min-w-0 h-full relative">
    <header class="glass border-b border-lavender/15 px-3 py-2 flex items-center justify-between gap-2 z-20">
      <div class="flex items-center gap-2 min-w-0">
        <button onclick="toggleSb(true)" class="md:hidden p-1.5 rounded-lg bg-white/5"><i data-lucide="menu" class="w-4 h-4"></i></button>
        <span id="hd-bot" class="hidden sm:inline-flex items-center gap-1.5 px-2.5 py-1 rounded-full bg-lavender/10 border border-lavender/25 text-xs text-lavender"></span>
        <select id="model-sel" onchange="onModel(this.value)" class="bg-obsidian/90 border border-lavender/25 rounded-xl px-2.5 py-1 text-xs font-mono max-w-[165px] sm:max-w-[215px]">
          <option value="gemini-2.5-flash">Gemini 2.5 Flash (Puter)</option>
          <option value="gemini-3.5-flash">Gemini 3.5 Flash (Puter)</option>
          <option value="gpt-4o-mini">GPT-4o Mini (Puter)</option>
          <option value="gpt-5-nano">GPT-5 Nano (Puter)</option>
          <option value="claude-sonnet-4">Claude Sonnet 4 (Puter)</option>
          <option value="deepseek-chat">DeepSeek Chat (Puter)</option>
          <option value="offline-oracle">Оракул Снов (Офлайн)</option>
        </select>
      </div>
      <div class="flex items-center gap-1.5">
        <button id="amb-btn" onclick="toggleAmb()" title="Звук сна" class="chroma px-2.5 py-1.5 rounded-xl bg-white/5 border border-lavender/20 text-xs flex items-center gap-1"><i id="amb-ic" data-lucide="volume-x" class="w-4 h-4"></i><span class="hidden lg:inline font-mono text-[11px]">Звук</span></button>
        <button onclick="openVoiceMod()" title="Настройки TTS" class="p-1.5 rounded-xl bg-white/5 border border-lavender/20"><i data-lucide="sliders-horizontal" class="w-4 h-4"></i></button>
        <button onclick="startAstral()" title="Астральный звонок" class="chroma px-2.5 py-1.5 rounded-xl bg-neon/15 border border-neon/35 text-xs text-neon flex items-center gap-1"><i data-lucide="phone-call" class="w-4 h-4"></i><span class="hidden md:inline font-mono text-[11px]">Астрал</span></button>
        <button onclick="toggleMirror()" title="Лунное Зеркало" class="chroma px-2.5 py-1.5 rounded-xl bg-cyanGlow/10 border border-cyanGlow/30 text-xs text-cyanGlow flex items-center gap-1"><i data-lucide="panel-right" class="w-4 h-4"></i><span class="hidden xl:inline font-mono text-[11px]">Зеркало</span></button>
        <button onclick="authPuter()" class="hidden sm:flex items-center gap-1 px-2 py-1.5 rounded-xl bg-white/5 border border-white/15 text-[11px] font-mono"><i data-lucide="key-round" class="w-3.5 h-3.5 text-lavender"></i><span id="puter-usr">Puter</span></button>
      </div>
    </header>

    <div id="chat-scroll" class="flex-1 overflow-y-auto px-3 sm:px-6 py-4 space-y-4">
      <div id="hero" class="max-w-xl mx-auto my-6 text-center space-y-5">
        <div class="glass arch p-7 border-lavender/25 space-y-3">
          <div id="hero-ico" class="w-16 h-16 mx-auto rounded-full bg-lavender/15 border border-lavender/40 flex items-center justify-center text-3xl">🌙</div>
          <h1 class="font-serif text-3xl sm:text-4xl text-white glitch-fx">Добро пожаловать в <span class="text-lavender italic">Сновидение</span></h1>
          <p id="hero-desc" class="text-xs sm:text-sm text-slate-300"></p>
        </div>
        <div id="starters" class="grid sm:grid-cols-2 gap-2 text-left text-xs"></div>
      </div>
      <div id="feed" class="max-w-3xl mx-auto space-y-4 pb-3"></div>
    </div>

    <div id="drop-ov" class="hidden absolute inset-0 z-30 bg-indigoNight/90 border-2 border-dashed border-cyanGlow rounded-xl m-3 flex flex-col items-center justify-center pointer-events-none">
      <p class="font-serif text-2xl text-white">Отпустите картинку или файл с кодом</p>
    </div>

    <div class="p-3 sm:px-6 pb-3 z-20">
      <div class="max-w-3xl mx-auto glass rounded-2xl border-lavender/25 p-2">
        <div id="att-bar" class="hidden flex-wrap gap-2 pb-2 mb-1.5 border-b border-white/10"></div>
        <div id="img-bar" class="hidden justify-between items-center px-2 py-1 mb-1.5 rounded bg-neon/10 border border-neon/30 text-[11px] font-mono text-neon">
          <span>✨ Режим /imagine</span>
          <label class="flex items-center gap-1 text-slate-300 cursor-pointer"><input id="dream-style" type="checkbox" checked class="accent-neon"/>+Lunar Dreamcore</label>
        </div>
        <div class="flex items-end gap-1.5">
          <input id="f-in" type="file" multiple accept="image/*,.txt,.js,.ts,.py,.md,.json,.html,.css" class="hidden" onchange="onFiles(event)"/>
          <button onclick="$('f-in').click()" title="Прикрепить" class="p-2 rounded-xl bg-white/5 hover:text-cyanGlow"><i data-lucide="paperclip" class="w-4 h-4"></i></button>
          <button id="img-btn" onclick="toggleImg()" title="/imagine" class="p-2 rounded-xl bg-white/5 hover:text-neon"><i data-lucide="image-plus" class="w-4 h-4"></i></button>
          <textarea id="in" rows="1" placeholder="Прошепчите запрос Луне..." class="flex-1 bg-transparent text-sm text-white placeholder-slate-500 resize-none max-h-36 py-2 px-1 focus:outline-none"></textarea>
          <button id="stt-lang" onclick="flipLang()" class="px-1.5 py-1 rounded bg-white/5 text-[10px] font-mono text-slate-400">RU</button>
          <button id="mic-btn" onclick="toggleMic()" class="p-2 rounded-xl bg-white/5 hover:text-lavender"><i data-lucide="mic" class="w-4 h-4"></i></button>
          <button id="send-btn" onclick="sendOrStop()" class="chroma p-2 px-3 rounded-xl bg-gradient-to-r from-lavender to-cyanGlow text-obsidian font-bold"><i id="send-ic" data-lucide="arrow-up" class="w-4 h-4"></i></button>
        </div>
      </div>
    </div>
  </main>

  <!-- LUNAR MIRROR -->
  <aside id="mirror" class="hidden fixed md:relative inset-y-0 right-0 z-35 w-full md:w-[45%] glass border-l border-cyanGlow/25 flex flex-col">
    <div class="px-3 py-2.5 border-b border-cyanGlow/20 flex items-center justify-between bg-obsidian/70 text-xs">
      <div class="flex items-center gap-2"><span class="font-serif text-lg text-white">🪞 Зеркало</span><span id="m-lang" class="px-1.5 py-0.5 rounded bg-cyanGlow/15 text-cyanGlow font-mono text-[10px]">HTML</span></div>
      <div class="flex items-center gap-1 font-mono">
        <button onclick="mTab('prev')" id="mt-p" class="px-2 py-1 rounded bg-cyanGlow/20 text-cyanGlow">Вид</button>
        <button onclick="mTab('code')" id="mt-c" class="px-2 py-1 rounded text-slate-400">Код</button>
        <button onclick="dlMirror()" class="p-1.5 text-slate-300 hover:text-white"><i data-lucide="download" class="w-4 h-4"></i></button>
        <button onclick="toggleMirror(false)" class="p-1.5 text-slate-300 hover:text-white"><i data-lucide="x" class="w-4 h-4"></i></button>
      </div>
    </div>
    <div class="flex-1 relative bg-[#04050c] overflow-hidden">
      <iframe id="m-if" sandbox="allow-scripts allow-modals" class="w-full h-full border-0 bg-white"></iframe>
      <div id="m-md" class="hidden w-full h-full overflow-y-auto p-5 md bg-obsidian"></div>
      <div id="m-ed-wrap" class="hidden w-full h-full flex flex-col">
        <textarea id="m-ed" class="flex-1 bg-[#060812] text-cyanGlow font-mono text-xs p-3 focus:outline-none resize-none"></textarea>
        <button onclick="loadMirror($('m-ed').value,rt.mLang)" class="p-2 bg-cyanGlow/20 text-cyanGlow font-mono text-xs border-t border-white/10">Применить изменения</button>
      </div>
    </div>
  </aside>
</div>

<!-- MODALS: ASTRAL, BOT, MEMORY, VOICE, PIN, ADMIN -->
<div id="astral-modal" class="hidden fixed inset-0 z-[65] bg-obsidian/95 backdrop-blur-2xl flex flex-col items-center justify-between p-6 text-center">
  <div class="w-full max-w-md flex justify-between font-mono text-xs text-cyanGlow"><span>✦ АСТРАЛЬНЫЙ ЗВОНОК</span><span id="ast-tm">00:00</span></div>
  <div class="space-y-5 my-auto">
    <div class="astral-orb w-44 h-44 mx-auto rounded-full bg-gradient-to-tr from-lavender/30 via-indigoNight to-cyanGlow/30 border border-lavender/50 flex flex-col items-center justify-center relative">
      <div class="absolute inset-2.5 rounded-full border border-dashed border-cyanGlow/30 spin"></div>
      <span id="ast-av" class="text-5xl">🌙</span><span id="ast-st" class="font-mono text-[10px] text-cyanGlow mt-1">НАЖМИТЕ МИКРОФОН</span>
    </div>
    <h2 id="ast-nm" clas# index.html
