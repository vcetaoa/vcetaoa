<svg xmlns="http://www.w3.org/2000/svg" width="900" height="1800" viewBox="0 0 900 1800">
  <defs>
    <!-- CRT scanline pattern -->
    <pattern id="scanlines" x="0" y="0" width="900" height="4" patternUnits="userSpaceOnUse">
      <rect width="900" height="2" y="0" fill="rgba(0,0,0,0)" />
      <rect width="900" height="2" y="2" fill="rgba(0,0,0,0.18)" />
    </pattern>

    <!-- Grid pattern -->
    <pattern id="grid" x="0" y="0" width="40" height="40" patternUnits="userSpaceOnUse">
      <path d="M 40 0 L 0 0 0 40" fill="none" stroke="rgba(0,255,65,0.06)" stroke-width="0.5"/>
    </pattern>

    <!-- Noise filter -->
    <filter id="noise">
      <feTurbulence type="fractalNoise" baseFrequency="0.65" numOctaves="3" stitchTiles="stitch" result="noiseOut"/>
      <feColorMatrix type="saturate" values="0" in="noiseOut" result="grayNoise"/>
      <feBlend in="SourceGraphic" in2="grayNoise" mode="overlay" result="blend"/>
      <feComposite in="blend" in2="SourceGraphic" operator="in"/>
    </filter>

    <!-- Glow filter -->
    <filter id="glow" x="-20%" y="-20%" width="140%" height="140%">
      <feGaussianBlur stdDeviation="3" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="glow-strong" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="6" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="glow-text" x="-10%" y="-50%" width="120%" height="200%">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>

    <!-- Glitch clip paths -->
    <clipPath id="clip-top">
      <rect x="0" y="0" width="900" height="120"/>
    </clipPath>
    <clipPath id="clip-mid">
      <rect x="0" y="120" width="900" height="60"/>
    </clipPath>
    <clipPath id="clip-bot">
      <rect x="0" y="180" width="900" height="60"/>
    </clipPath>
  </defs>

  <!-- VOID BACKGROUND -->
  <rect width="900" height="1800" fill="#000000"/>

  <!-- GRID -->
  <rect width="900" height="1800" fill="url(#grid)" opacity="0.8"/>

  <!-- VIGNETTE -->
  <radialGradient id="vignette" cx="50%" cy="50%" r="70%">
    <stop offset="0%" stop-color="transparent"/>
    <stop offset="100%" stop-color="rgba(0,0,0,0.75)"/>
  </radialGradient>
  <rect width="900" height="1800" fill="url(#vignette)"/>

  <!-- CRT SCANLINES -->
  <rect width="900" height="1800" fill="url(#scanlines)" opacity="0.5"/>

  <!-- TOP BORDER LINE (animated) -->
  <line x1="0" y1="1" x2="900" y2="1" stroke="#00FF41" stroke-width="1" opacity="0.4">
    <animate attributeName="opacity" values="0.4;0.8;0.4;0.2;0.4" dur="4s" repeatCount="indefinite"/>
  </line>
  <line x1="0" y1="1799" x2="900" y2="1799" stroke="#00FF41" stroke-width="1" opacity="0.4">
    <animate attributeName="opacity" values="0.4;0.2;0.8;0.4" dur="5s" repeatCount="indefinite"/>
  </line>

  <!-- CORNER BRACKETS -->
  <!-- TL -->
  <polyline points="10,30 10,10 30,10" fill="none" stroke="#00FF41" stroke-width="1.5" opacity="0.5"/>
  <!-- TR -->
  <polyline points="870,10 890,10 890,30" fill="none" stroke="#00FF41" stroke-width="1.5" opacity="0.5"/>
  <!-- BL -->
  <polyline points="10,1770 10,1790 30,1790" fill="none" stroke="#00FF41" stroke-width="1.5" opacity="0.5"/>
  <!-- BR -->
  <polyline points="870,1790 890,1790 890,1770" fill="none" stroke="#00FF41" stroke-width="1.5" opacity="0.5"/>

  <!-- STATUS BAR TOP -->
  <rect x="0" y="0" width="900" height="28" fill="rgba(0,255,65,0.04)" />
  <rect x="0" y="27" width="900" height="1" fill="rgba(0,255,65,0.2)"/>
  <text x="16" y="18" font-family="'Courier New', monospace" font-size="10" fill="#00FF41" opacity="0.5" letter-spacing="2">VCETAOA.EXE</text>
  <text x="450" y="18" font-family="'Courier New', monospace" font-size="10" fill="#FF00FF" opacity="0.5" letter-spacing="2" text-anchor="middle">▶ PROCESS TERMINATED ◀</text>
  <text x="884" y="18" font-family="'Courier New', monospace" font-size="10" fill="#00FFFF" opacity="0.5" letter-spacing="2" text-anchor="end">APR 20 2083</text>

  <!-- ═══════════════════════════ HERO ═══════════════════════════ -->

  <!-- EYEBROW -->
  <text x="450" y="82" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF" letter-spacing="8" text-anchor="middle" filter="url(#glow)">
    ▶ SYSTEM: VCETAOA.EXE ◀ PROCESS TERMINATED
    <animate attributeName="opacity" values="1;0.3;1;1;0.3;1" dur="5s" repeatCount="indefinite"/>
  </text>

  <!-- MAIN TITLE — THE REPO (layered glitch) -->
  <!-- Shadow layers -->
  <text x="453" y="155" font-family="'Courier New', monospace" font-size="72" font-weight="900" fill="#FF00FF" letter-spacing="-2" text-anchor="middle" opacity="0" clip-path="url(#clip-top)">
    THE REPO
    <animate attributeName="opacity" values="0;0;0;0;0;0.8;0;0;0;0.6;0;0" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="x" values="453;457;449;453" dur="4s" repeatCount="indefinite"/>
  </text>
  <text x="447" y="157" font-family="'Courier New', monospace" font-size="72" font-weight="900" fill="#00FFFF" letter-spacing="-2" text-anchor="middle" opacity="0" clip-path="url(#clip-bot)">
    THE REPO
    <animate attributeName="opacity" values="0;0;0;0;0;0;0.8;0;0;0;0.6;0" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="x" values="447;443;451;447" dur="4s" repeatCount="indefinite"/>
  </text>
  <!-- Main title -->
  <text x="450" y="156" font-family="'Courier New', monospace" font-size="72" font-weight="900" fill="#00FF41" letter-spacing="-2" text-anchor="middle" filter="url(#glow-strong)">
    THE REPO
    <animate attributeName="opacity" values="1;1;1;1;0.9;1;1;0.8;1;1" dur="4s" repeatCount="indefinite"/>
  </text>

  <!-- SUBTITLE -->
  <text x="450" y="190" font-family="'Courier New', monospace" font-size="16" fill="#00FFFF" letter-spacing="6" text-anchor="middle" filter="url(#glow)">THE MYTH.  THE LEGEND.  THE MACHINE.</text>

  <!-- STATUS BADGES ROW -->
  <!-- Badge 1 -->
  <rect x="62" y="208" width="170" height="26" rx="2" fill="#000" stroke="#00FF41" stroke-width="1"/>
  <text x="147" y="225" font-family="'Courier New', monospace" font-size="10" fill="#00FF41" text-anchor="middle" letter-spacing="1" filter="url(#glow)">UPTIME: 730 DAYS</text>
  <!-- Badge 2 -->
  <rect x="245" y="208" width="150" height="26" rx="2" fill="#000" stroke="#FF00FF" stroke-width="1"/>
  <text x="320" y="225" font-family="'Courier New', monospace" font-size="10" fill="#FF00FF" text-anchor="middle" letter-spacing="1" filter="url(#glow)">STATUS: ARCHIVED</text>
  <!-- Badge 3 -->
  <rect x="408" y="208" width="140" height="26" rx="2" fill="#000" stroke="#00FFFF" stroke-width="1"/>
  <text x="478" y="225" font-family="'Courier New', monospace" font-size="10" fill="#00FFFF" text-anchor="middle" letter-spacing="1" filter="url(#glow)">EXIT CODE: 0x00</text>
  <!-- Badge 4 -->
  <rect x="561" y="208" width="130" height="26" rx="2" fill="#000" stroke="#FFFF00" stroke-width="1"/>
  <text x="626" y="225" font-family="'Courier New', monospace" font-size="10" fill="#FFFF00" text-anchor="middle" letter-spacing="1" filter="url(#glow)">EXAMS: ALL ✓</text>
  <!-- Badge 5 -->
  <rect x="704" y="208" width="140" height="26" rx="2" fill="#000" stroke="#FF0040" stroke-width="1"/>
  <text x="774" y="225" font-family="'Courier New', monospace" font-size="10" fill="#FF0040" text-anchor="middle" letter-spacing="1" filter="url(#glow)">GRADUATED 🎓</text>

  <!-- SCAN LINE ANIMATION across hero -->
  <rect x="0" y="40" width="900" height="2" fill="rgba(0,255,65,0.25)">
    <animate attributeName="y" from="40" to="240" dur="3s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0;0.5;0.5;0" dur="3s" repeatCount="indefinite"/>
  </rect>

  <!-- DIVIDER 1 -->
  <line x1="0" y1="248" x2="900" y2="248" stroke="rgba(0,255,65,0.15)" stroke-width="1"/>
  <text x="450" y="261" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.3)" text-anchor="middle" letter-spacing="4">⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡ ⚡</text>
  <line x1="0" y1="270" x2="900" y2="270" stroke="rgba(0,255,65,0.15)" stroke-width="1"/>

  <!-- ═══════════════════════════ 001 ORIGIN ═══════════════════════════ -->
  <text x="30" y="300" font-family="'Courier New', monospace" font-size="10" fill="#FF00FF" opacity="0.6" letter-spacing="2">// 001</text>
  <text x="80" y="300" font-family="'Courier New', monospace" font-size="14" font-weight="bold" fill="#00FF41" letter-spacing="4" filter="url(#glow)">ORIGIN.TXT</text>
  <line x1="222" y1="294" x2="870" y2="294" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>

  <!-- Terminal box -->
  <rect x="30" y="312" width="840" height="195" rx="2" fill="rgba(0,255,65,0.02)" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>
  <rect x="30" y="312" width="840" height="22" fill="rgba(0,255,65,0.05)"/>
  <rect x="30" y="312" width="3" height="195" fill="#00FF41"/>
  <!-- terminal dots -->
  <circle cx="46" cy="323" r="4" fill="#FF0040"/>
  <circle cx="60" cy="323" r="4" fill="#FFFF00"/>
  <circle cx="74" cy="323" r="4" fill="#00FF41"/>
  <text x="88" y="327" font-family="'Courier New', monospace" font-size="9" fill="rgba(0,255,65,0.4)" letter-spacing="2">ORIGIN.TXT</text>

  <text x="50" y="357" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.4)">DATE</text>
  <text x="130" y="357" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.25)">:</text>
  <text x="150" y="357" font-family="'Courier New', monospace" font-size="12" fill="#00FFFF">April 21, 2081</text>

  <text x="50" y="377" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.4)">LOCATION</text>
  <text x="130" y="377" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.25)">:</text>
  <text x="150" y="377" font-family="'Courier New', monospace" font-size="12" fill="#ffffff" opacity="0.85">college lab. corner seat. back row. god mode.</text>

  <text x="50" y="397" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.4)">STATUS</text>
  <text x="130" y="397" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.25)">:</text>
  <text x="150" y="397" font-family="'Courier New', monospace" font-size="12" fill="#FF0040">exam in 10 mins.  zero prep.  pure panic.</text>

  <text x="50" y="417" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.4)">ACTION</text>
  <text x="130" y="417" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.25)">:</text>
  <text x="150" y="417" font-family="'Courier New', monospace" font-size="12" fill="#00FF41">bag → corner.  phone → inside.  hotspot → </text>
  <text x="592" y="417" font-family="'Courier New', monospace" font-size="12" fill="#00FF41" font-weight="bold" filter="url(#glow)">ON.</text>

  <text x="50" y="437" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.4)">RESULT</text>
  <text x="130" y="437" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.25)">:</text>
  <text x="150" y="437" font-family="'Courier New', monospace" font-size="12" fill="#00FF41" font-weight="bold" filter="url(#glow)">PASSED ✓</text>

  <text x="50" y="457" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.4)">DECISION</text>
  <text x="130" y="457" font-family="'Courier New', monospace" font-size="12" fill="rgba(0,255,65,0.25)">:</text>
  <text x="150" y="457" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF" filter="url(#glow)">never. delete. this. repo. ever.</text>

  <text x="50" y="490" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.35)" font-style="italic"># and that was just day one.  🫡</text>

  <!-- ═══════════════════════════ 002 RITUAL ═══════════════════════════ -->
  <text x="30" y="540" font-family="'Courier New', monospace" font-size="10" fill="#FF00FF" opacity="0.6" letter-spacing="2">// 002</text>
  <text x="80" y="540" font-family="'Courier New', monospace" font-size="14" font-weight="bold" fill="#00FF41" letter-spacing="4" filter="url(#glow)">EXAM_RITUAL.SH</text>
  <line x1="308" y1="534" x2="870" y2="534" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>

  <rect x="30" y="552" width="840" height="230" rx="2" fill="rgba(0,255,65,0.02)" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>
  <rect x="30" y="552" width="840" height="22" fill="rgba(0,255,65,0.05)"/>
  <rect x="30" y="552" width="3" height="230" fill="#00FF41"/>
  <circle cx="46" cy="563" r="4" fill="#FF0040"/>
  <circle cx="60" cy="563" r="4" fill="#FFFF00"/>
  <circle cx="74" cy="563" r="4" fill="#00FF41"/>
  <text x="88" y="567" font-family="'Courier New', monospace" font-size="9" fill="rgba(0,255,65,0.4)" letter-spacing="2">./exam_ritual.sh</text>

  <text x="50" y="596" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># THE SACRED PROTOCOL — 9:55 AM sharp. no exceptions. no mercy.</text>
  <text x="50" y="618" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF">bag_corner</text>
  <text x="162" y="618" font-family="'Courier New', monospace" font-size="12" fill="rgba(255,255,255,0.6)">--wall-side</text>
  <text x="350" y="618" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># natural. invisible. certified ghost.</text>

  <text x="50" y="638" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF">phone.hotspot</text>
  <text x="196" y="638" font-family="'Courier New', monospace" font-size="12" fill="rgba(255,255,255,0.6)">--on --dnd --silent</text>
  <text x="396" y="638" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># silent as death.</text>

  <text x="50" y="658" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF">wifi.connect</text>
  <text x="185" y="658" font-family="'Courier New', monospace" font-size="12" fill="rgba(255,255,255,0.6)">--act-normal</text>
  <text x="350" y="658" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># connect. breathe. say nothing.</text>

  <text x="50" y="678" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF">github.open</text>
  <text x="175" y="678" font-family="'Courier New', monospace" font-size="12" fill="#00FF41" filter="url(#glow)">vcetaoa/&lt;repo&gt;</text>
  <text x="348" y="678" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># HOME. this is always home. 🏠</text>

  <text x="50" y="698" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF">code.copy</text>
  <text x="162" y="698" font-family="'Courier New', monospace" font-size="12" fill="rgba(255,255,255,0.6)">--paste --rename-vars</text>
  <text x="398" y="698" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># SMART. always rename.</text>

  <text x="50" y="718" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF">submit</text>
  <text x="122" y="718" font-family="'Courier New', monospace" font-size="12" fill="rgba(255,255,255,0.6)">--poker-face --walk-up</text>
  <text x="388" y="718" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># act like you wrote it. 😐</text>

  <text x="50" y="738" font-family="'Courier New', monospace" font-size="12" fill="#FF00FF">bag.pickup</text>
  <text x="162" y="738" font-family="'Courier New', monospace" font-size="12" fill="rgba(255,255,255,0.35)">&amp;&amp;</text>
  <text x="188" y="738" font-family="'Courier New', monospace" font-size="12" fill="#00FF41" font-weight="bold" filter="url(#glow)">exit 0</text>
  <text x="280" y="738" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.3)" font-style="italic"># out like a ghost. legend confirmed. 😎</text>

  <text x="50" y="766" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.35)" font-style="italic"># return code 0.  every single time.  for two years.  undefeated.</text>

  <!-- ═══════════════════════════ 003 TACTICAL MAP ═══════════════════════════ -->
  <text x="30" y="816" font-family="'Courier New', monospace" font-size="10" fill="#FF00FF" opacity="0.6" letter-spacing="2">// 003</text>
  <text x="80" y="816" font-family="'Courier New', monospace" font-size="14" font-weight="bold" fill="#00FF41" letter-spacing="4" filter="url(#glow)">TACTICAL MAP</text>
  <line x1="268" y1="810" x2="870" y2="810" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>

  <!-- Card: SAFE -->
  <rect x="30" y="828" width="198" height="105" fill="rgba(0,255,65,0.03)" stroke="rgba(0,255,65,0.25)" stroke-width="1"/>
  <rect x="30" y="828" width="3" height="105" fill="#00FF41" filter="url(#glow)"/>
  <text x="46" y="850" font-family="'Courier New', monospace" font-size="20">✅</text>
  <text x="46" y="872" font-family="'Courier New', monospace" font-size="9" fill="#00FF41" letter-spacing="2" font-weight="bold">CORNER · WALL SIDE</text>
  <text x="46" y="890" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.6)">Safest. Classic.</text>
  <text x="46" y="906" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.6)">730 days approved.</text>
  <text x="46" y="922" font-family="'Courier New', monospace" font-size="9" fill="rgba(0,255,65,0.3)">battle-tested. never failed.</text>

  <!-- Card: WARN -->
  <rect x="240" y="828" width="198" height="105" fill="rgba(255,255,0,0.02)" stroke="rgba(255,255,0,0.2)" stroke-width="1"/>
  <rect x="240" y="828" width="3" height="105" fill="#FFFF00" filter="url(#glow)"/>
  <text x="256" y="850" font-family="'Courier New', monospace" font-size="20">⚠️</text>
  <text x="256" y="872" font-family="'Courier New', monospace" font-size="9" fill="#FFFF00" letter-spacing="2" font-weight="bold">UNDER YOUR SEAT</text>
  <text x="256" y="890" font-family="'Courier New', monospace" font-size="10" fill="rgba(255,255,0,0.6)">Risky. Teacher</text>
  <text x="256" y="906" font-family="'Courier New', monospace" font-size="10" fill="rgba(255,255,0,0.6)">checks here too.</text>
  <text x="256" y="922" font-family="'Courier New', monospace" font-size="9" fill="rgba(255,255,0,0.3)">proceed with prayer.</text>

  <!-- Card: DEAD -->
  <rect x="450" y="828" width="198" height="105" fill="rgba(255,0,64,0.03)" stroke="rgba(255,0,64,0.25)" stroke-width="1"/>
  <rect x="450" y="828" width="3" height="105" fill="#FF0040" filter="url(#glow)"/>
  <text x="466" y="850" font-family="'Courier New', monospace" font-size="20">💀</text>
  <text x="466" y="872" font-family="'Courier New', monospace" font-size="9" fill="#FF0040" letter-spacing="2" font-weight="bold">ON THE TABLE</text>
  <text x="466" y="890" font-family="'Courier New', monospace" font-size="10" fill="rgba(255,0,64,0.7)">ABSOLUTELY NOT.</text>
  <text x="466" y="906" font-family="'Courier New', monospace" font-size="10" fill="rgba(255,0,64,0.7)">Instant execution.</text>
  <text x="466" y="922" font-family="'Courier New', monospace" font-size="9" fill="rgba(255,0,64,0.4)">expulsion.exe loading.</text>

  <!-- Card: GALAXY -->
  <rect x="660" y="828" width="210" height="105" fill="rgba(255,0,255,0.03)" stroke="rgba(255,0,255,0.2)" stroke-width="1"/>
  <rect x="660" y="828" width="3" height="105" fill="#FF00FF" filter="url(#glow)"/>
  <text x="676" y="850" font-family="'Courier New', monospace" font-size="20">🧠</text>
  <text x="676" y="872" font-family="'Courier New', monospace" font-size="9" fill="#FF00FF" letter-spacing="2" font-weight="bold">SOMEONE ELSE'S BAG</text>
  <text x="676" y="890" font-family="'Courier New', monospace" font-size="10" fill="rgba(255,0,255,0.7)">Galaxy-brain tier.</text>
  <text x="676" y="906" font-family="'Courier New', monospace" font-size="10" fill="rgba(255,0,255,0.7)">Coordinate first.</text>
  <text x="676" y="922" font-family="'Courier New', monospace" font-size="9" fill="rgba(255,0,255,0.4)">mutual trust required.</text>

  <!-- Pro tip bar -->
  <rect x="30" y="944" width="840" height="28" fill="rgba(255,255,0,0.04)" stroke="rgba(255,255,0,0.15)" stroke-width="1"/>
  <rect x="30" y="944" width="3" height="28" fill="#FFFF00"/>
  <text x="46" y="962" font-family="'Courier New', monospace" font-size="11" fill="#FFFF00" opacity="0.8">// pro tip:  DND before entering.  charge 100%.  set PUBLIC.  every. single. time. ✅</text>

  <!-- ═══════════════════════════ 004 HALL OF FAME ═══════════════════════════ -->
  <text x="30" y="1010" font-family="'Courier New', monospace" font-size="10" fill="#FF00FF" opacity="0.6" letter-spacing="2">// 004</text>
  <text x="80" y="1010" font-family="'Courier New', monospace" font-size="14" font-weight="bold" fill="#00FF41" letter-spacing="4" filter="url(#glow)">HALL OF FAME</text>
  <line x1="260" y1="1004" x2="870" y2="1004" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>

  <rect x="30" y="1022" width="840" height="270" rx="2" fill="rgba(0,255,65,0.02)" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>
  <rect x="30" y="1022" width="840" height="22" fill="rgba(0,255,65,0.05)"/>
  <rect x="30" y="1022" width="3" height="270" fill="#00FF41"/>
  <circle cx="46" cy="1033" r="4" fill="#FF0040"/>
  <circle cx="60" cy="1033" r="4" fill="#FFFF00"/>
  <circle cx="74" cy="1033" r="4" fill="#00FF41"/>
  <text x="88" y="1037" font-family="'Courier New', monospace" font-size="9" fill="rgba(0,255,65,0.4)" letter-spacing="2">$ git blame --hall-of-fame</text>

  <!-- 🥇 -->
  <text x="50" y="1074" font-family="'Courier New', monospace" font-size="32">🥇</text>
  <text x="100" y="1058" font-family="'Courier New', monospace" font-size="9" fill="#FF00FF" letter-spacing="3">RANK 001 · MVP · THE BACKBONE</text>
  <text x="100" y="1076" font-family="'Courier New', monospace" font-size="15" fill="#00FF41" font-weight="bold" filter="url(#glow)">THE HOTSPOT BEARER</text>
  <text x="100" y="1094" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.55)">Ran hotspot from the bag. every exam. without you, nothing compiles.</text>
  <text x="100" y="1110" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.55)">The silent pillar. The true legend. The real Dhurandhar.</text>
  <line x1="50" y1="1122" x2="860" y2="1122" stroke="rgba(0,255,65,0.08)" stroke-width="1"/>

  <!-- 🥈 -->
  <text x="50" y="1158" font-family="'Courier New', monospace" font-size="32">🥈</text>
  <text x="100" y="1142" font-family="'Courier New', monospace" font-size="9" fill="#FF00FF" letter-spacing="3">RANK 002 · STRATEGIST · PRE-GAME IQ</text>
  <text x="100" y="1160" font-family="'Courier New', monospace" font-size="15" fill="#00FF41" font-weight="bold" filter="url(#glow)">THE LINK SENDER</text>
  <text x="100" y="1178" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.55)">Sent the GitHub link on WhatsApp at 9:58 AM. before entering the lab.</text>
  <text x="100" y="1194" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.55)">That 2-minute head start changed everything. Senior dev energy.</text>
  <line x1="50" y1="1206" x2="860" y2="1206" stroke="rgba(0,255,65,0.08)" stroke-width="1"/>

  <!-- 🥉 -->
  <text x="50" y="1242" font-family="'Courier New', monospace" font-size="32">🥉</text>
  <text x="100" y="1226" font-family="'Courier New', monospace" font-size="9" fill="#FF00FF" letter-spacing="3">RANK 003 · DISTRACTION · UNSUNG HERO</text>
  <text x="100" y="1244" font-family="'Courier New', monospace" font-size="15" fill="#00FF41" font-weight="bold" filter="url(#glow)">THE DECOY</text>
  <text x="100" y="1262" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.55)">Sat near the teacher. asked questions. acted confused. gave cover.</text>
  <text x="100" y="1278" font-family="'Courier New', monospace" font-size="11" fill="rgba(0,255,65,0.55)">The shield. The legend in disguise. The unsung hero of every op.</text>

  <!-- ═══════════════════════════ 005 ERRORS ═══════════════════════════ -->
  <text x="30" y="1330" font-family="'Courier New', monospace" font-size="10" fill="#FF00FF" opacity="0.6" letter-spacing="2">// 005</text>
  <text x="80" y="1330" font-family="'Courier New', monospace" font-size="14" font-weight="bold" fill="#00FF41" letter-spacing="4" filter="url(#glow)">ERRORS.LOG</text>
  <line x1="232" y1="1324" x2="870" y2="1324" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>

  <rect x="30" y="1342" width="840" height="232" rx="2" fill="rgba(0,255,65,0.02)" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>
  <rect x="30" y="1342" width="840" height="22" fill="rgba(0,255,65,0.05)"/>
  <rect x="30" y="1342" width="3" height="232" fill="#FF0040"/>
  <circle cx="46" cy="1353" r="4" fill="#FF0040"/>
  <circle cx="60" cy="1353" r="4" fill="#FFFF00"/>
  <circle cx="74" cy="1353" r="4" fill="#00FF41"/>
  <text x="88" y="1357" font-family="'Courier New', monospace" font-size="9" fill="rgba(0,255,65,0.4)" letter-spacing="2">errors.log</text>

  <!-- Error lines -->
  <rect x="50" y="1371" width="72" height="16" rx="1" fill="rgba(255,0,255,0.15)" stroke="#FF00FF" stroke-width="0.5"/>
  <text x="86" y="1382" font-family="'Courier New', monospace" font-size="8" fill="#FF00FF" text-anchor="middle" font-weight="bold">CRITICAL</text>
  <text x="134" y="1383" font-family="'Courier New', monospace" font-size="11" fill="rgba(255,255,255,0.8)">someone's phone rang mid-exam. bag vibrated. 💀</text>
  <text x="134" y="1397" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.4)">  → 15 hearts stopped. teacher looked. time froze.</text>

  <rect x="50" y="1413" width="52" height="16" rx="1" fill="rgba(255,255,0,0.1)" stroke="#FFFF00" stroke-width="0.5"/>
  <text x="76" y="1424" font-family="'Courier New', monospace" font-size="8" fill="#FFFF00" text-anchor="middle" font-weight="bold">ERROR</text>
  <text x="114" y="1424" font-family="'Courier New', monospace" font-size="11" fill="rgba(255,255,255,0.8)">hotspot name was "FBI Surveillance Van". 💀</text>
  <text x="114" y="1438" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.4)">  → teacher connected by accident. pure silence.</text>

  <rect x="50" y="1453" width="52" height="16" rx="1" fill="rgba(255,255,0,0.1)" stroke="#FFFF00" stroke-width="0.5"/>
  <text x="76" y="1464" font-family="'Courier New', monospace" font-size="8" fill="#FFFF00" text-anchor="middle" font-weight="bold">ERROR</text>
  <text x="114" y="1464" font-family="'Courier New', monospace" font-size="11" fill="rgba(255,255,255,0.8)">copy kiya variable name bhi. teacher noticed. 💀</text>
  <text x="114" y="1478" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.4)">  → int studentName = 5;  in THREE submissions.</text>

  <rect x="50" y="1493" width="42" height="16" rx="1" fill="rgba(255,0,64,0.2)" stroke="#FF0040" stroke-width="0.5"/>
  <text x="71" y="1504" font-family="'Courier New', monospace" font-size="8" fill="#FF0040" text-anchor="middle" font-weight="bold">FATAL</text>
  <text x="104" y="1504" font-family="'Courier New', monospace" font-size="11" fill="rgba(255,255,255,0.8)">repo was PRIVATE on exam day. 15 people locked out. 💀</text>
  <text x="104" y="1518" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.4)">  → The Great Blackout. never forgotten. never repeated.</text>

  <rect x="50" y="1533" width="42" height="16" rx="1" fill="rgba(255,0,64,0.2)" stroke="#FF0040" stroke-width="0.5"/>
  <text x="71" y="1544" font-family="'Courier New', monospace" font-size="8" fill="#FF0040" text-anchor="middle" font-weight="bold">FATAL</text>
  <text x="104" y="1544" font-family="'Courier New', monospace" font-size="11" fill="rgba(255,255,255,0.8)">phone battery: 2%. hotspot died mid-copy. 💀</text>
  <text x="104" y="1558" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.4)">  → half code. full panic. found out what you remembered.</text>

  <!-- ═══════════════════════════ FINAL COMMIT ═══════════════════════════ -->
  <!-- Top gradient bar -->
  <linearGradient id="final-top" x1="0%" y1="0%" x2="100%" y2="0%">
    <stop offset="0%" stop-color="#FF00FF"/>
    <stop offset="50%" stop-color="#00FF41"/>
    <stop offset="100%" stop-color="#00FFFF"/>
  </linearGradient>
  <rect x="30" y="1598" width="840" height="2" fill="url(#final-top)"/>
  <rect x="30" y="1598" width="840" height="160" fill="rgba(0,255,65,0.02)" stroke="rgba(0,255,65,0.2)" stroke-width="1"/>

  <text x="450" y="1630" font-family="'Courier New', monospace" font-size="9" fill="rgba(0,255,65,0.35)" text-anchor="middle" letter-spacing="3">──── COMMIT [LAST_COMMIT] · SUN APR 20 2083 · author: vcetaoa ────</text>

  <!-- SIGNING OFF glitch title -->
  <text x="453" y="1672" font-family="'Courier New', monospace" font-size="40" font-weight="900" fill="#FF00FF" text-anchor="middle" opacity="0">
    SIGNING OFF
    <animate attributeName="opacity" values="0;0;0;0;0.7;0;0;0;0.5;0" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="x" values="453;457;449;453" dur="4s" repeatCount="indefinite"/>
  </text>
  <text x="447" y="1674" font-family="'Courier New', monospace" font-size="40" font-weight="900" fill="#00FFFF" text-anchor="middle" opacity="0">
    SIGNING OFF
    <animate attributeName="opacity" values="0;0;0;0;0;0.7;0;0;0.5;0" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="x" values="447;443;451;447" dur="4s" repeatCount="indefinite"/>
  </text>
  <text x="450" y="1673" font-family="'Courier New', monospace" font-size="40" font-weight="900" fill="#00FF41" text-anchor="middle" filter="url(#glow-strong)">
    SIGNING OFF
    <animate attributeName="opacity" values="1;1;1;1;0.9;1;0.8;1;1" dur="4s" repeatCount="indefinite"/>
  </text>

  <text x="450" y="1700" font-family="'Courier New', monospace" font-size="13" fill="#00FFFF" text-anchor="middle" opacity="0.75" font-style="italic">"to everyone who used it — tu pass hua. that's enough. that was always enough."</text>

  <text x="450" y="1730" font-family="'Courier New', monospace" font-size="28" font-weight="900" fill="#00FF41" text-anchor="middle" letter-spacing="10" filter="url(#glow-strong)">
    [ EOF ]
    <animate attributeName="opacity" values="1;1;1;1;0.7;1;0;1;1;0.8;1" dur="5s" repeatCount="indefinite"/>
  </text>

  <!-- ═══════════════════════════ FOOTER ═══════════════════════════ -->
  <line x1="0" y1="1762" x2="900" y2="1762" stroke="rgba(0,255,65,0.15)" stroke-width="1"/>

  <!-- Timeline -->
  <text x="100" y="1780" font-family="'Courier New', monospace" font-size="11" fill="#00FF41" font-weight="bold" filter="url(#glow)" text-anchor="middle">APR 21 2081</text>
  <line x1="170" y1="1779" x2="560" y2="1779" stroke="#00FF41" stroke-width="1.5" filter="url(#glow)"/>
  <line x1="170" y1="1779" x2="560" y2="1779" stroke="url(#final-top)" stroke-width="1.5"/>
  <text x="365" y="1773" font-family="'Courier New', monospace" font-size="8" fill="rgba(0,255,65,0.4)" text-anchor="middle" letter-spacing="3">730 DAYS</text>
  <text x="640" y="1780" font-family="'Courier New', monospace" font-size="11" fill="#FF00FF" font-weight="bold" filter="url(#glow)" text-anchor="middle">APR 20 2083</text>

  <text x="450" y="1797" font-family="'Courier New', monospace" font-size="10" fill="rgba(0,255,65,0.3)" text-anchor="middle" letter-spacing="3">repo: ARCHIVED  ·  status: GRADUATED  ·  $ shutdown -h now</text>

  <!-- FINAL SCAN LINE across whole thing -->
  <rect x="0" y="0" width="900" height="3" fill="rgba(0,255,65,0.2)">
    <animate attributeName="y" from="-10" to="1810" dur="8s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0;0.4;0.4;0" dur="8s" repeatCount="indefinite"/>
  </rect>

  <!-- GLITCH HORIZONTAL TEAR (random flicker) -->
  <rect x="0" y="300" width="900" height="4" fill="#000" opacity="0">
    <animate attributeName="y" values="300;650;1100;250;800" dur="7s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0;0;0;0;0;0;0;0.8;0;0;0;0;0;0;0;0.6;0;0;0;0" dur="7s" repeatCount="indefinite"/>
  </rect>
  <rect x="20" y="500" width="860" height="2" fill="#00FF41" opacity="0">
    <animate attributeName="y" values="500;900;400;1200;700" dur="9s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0;0;0;0;0;0;0.3;0;0;0;0;0;0;0.2;0;0;0" dur="9s" repeatCount="indefinite"/>
  </rect>

  <!-- FINAL CRT OVERLAY ON TOP -->
  <rect width="900" height="1800" fill="url(#scanlines)" opacity="0.3"/>
</svg>
