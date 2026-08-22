# my_portfolio
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vaishnavi — Mathematics Educator &amp; Atal Tinkering Lab Incharge</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --navy:#0F1E27;
    --navy-line:#1D3444;
    --paper:#F2EEE2;
    --paper-line:#DAD3BF;
    --ink:#141311;
    --cream:#EEEAE0;
    --teal:#4BDAC2;
    --teal-dim:#245349;
    --brass:#D9A441;
    --radius:2px;
  }

  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    font-family:'IBM Plex Sans', sans-serif;
    color:var(--ink);
    background:var(--paper);
    line-height:1.55;
    overflow-x:hidden;
  }
  h1,h2,h3{font-family:'Space Grotesk', sans-serif; letter-spacing:-0.01em;}
  .mono{font-family:'IBM Plex Mono', monospace;}
  a{color:inherit; text-decoration:none;}
  img{max-width:100%; display:block;}

  .wrap{max-width:1180px; margin:0 auto; padding:0 40px;}
  @media (max-width:720px){.wrap{padding:0 22px;}}

  /* ---------- grid textures ---------- */
  .grid-dark{
    background-image:
      linear-gradient(var(--navy-line) 1px, transparent 1px),
      linear-gradient(90deg, var(--navy-line) 1px, transparent 1px);
    background-size:38px 38px;
    background-color:var(--navy);
  }
  .grid-light{
    background-image:
      linear-gradient(var(--paper-line) 1px, transparent 1px),
      linear-gradient(90deg, var(--paper-line) 1px, transparent 1px);
    background-size:34px 34px;
    background-color:var(--paper);
  }

  /* ---------- nav ---------- */
  nav{
    position:fixed; top:0; left:0; right:0; z-index:50;
    display:flex; align-items:center; justify-content:space-between;
    padding:18px 40px;
    background:rgba(15,30,39,0.86);
    backdrop-filter:blur(6px);
    border-bottom:1px solid var(--navy-line);
  }
  .brandmark{
    display:flex; align-items:center; gap:10px;
    color:var(--cream); font-family:'Space Grotesk',sans-serif; font-weight:600; font-size:15px;
  }
  .brandmark .node{
    width:9px; height:9px; border-radius:50%;
    background:var(--teal); box-shadow:0 0 8px var(--teal);
  }
  nav ul{list-style:none; display:flex; gap:30px;}
  nav a{
    color:var(--cream); opacity:.72; font-size:13px;
    font-family:'IBM Plex Mono',monospace; letter-spacing:.03em; text-transform:uppercase;
    transition:opacity .2s;
  }
  nav a:hover{opacity:1; color:var(--teal);}
  .nav-toggle{display:none; flex-direction:column; gap:4px; background:none; border:none; cursor:pointer;}
  .nav-toggle span{width:22px; height:2px; background:var(--cream);}
  @media (max-width:820px){
    nav ul{
      position:fixed; top:58px; right:0; left:0;
      flex-direction:column; gap:0; background:var(--navy);
      border-bottom:1px solid var(--navy-line);
      max-height:0; overflow:hidden; transition:max-height .3s ease;
    }
    nav ul.open{max-height:320px;}
    nav ul li{border-top:1px solid var(--navy-line);}
    nav ul a{display:block; padding:16px 22px;}
    .nav-toggle{display:flex;}
  }

  /* ---------- section shell w/ trace rail ---------- */
  section{position:relative; padding:100px 0;}
  .rail-row{display:grid; grid-template-columns:70px 1fr; column-gap:6px;}
  @media (max-width:720px){.rail-row{grid-template-columns:34px 1fr;}}
  .rail{position:relative;}
  .rail::before{
    content:"";
    position:absolute; left:50%; top:0; bottom:0; width:1px;
    background:repeating-linear-gradient(to bottom, currentColor 0 6px, transparent 6px 12px);
    color:var(--navy-line);
    transform:translateX(-50%);
  }
  .grid-light .rail::before{color:var(--paper-line);}
  .rail .tp{
    position:sticky; top:130px;
    display:flex; flex-direction:column; align-items:center; gap:8px;
  }
  .rail .tp .dot{
    width:13px; height:13px; border-radius:50%;
    background:var(--navy); border:2px solid var(--navy-line);
    transition:all .4s ease;
  }
  .grid-light .rail .tp .dot{background:var(--paper); border-color:var(--paper-line);}
  .rail .tp .dot.lit{
    background:var(--teal); border-color:var(--teal);
    box-shadow:0 0 10px var(--teal);
  }
  .rail .tp .label{
    font-family:'IBM Plex Mono',monospace; font-size:10px; letter-spacing:.06em;
    color:var(--navy-line); writing-mode:vertical-rl; text-transform:uppercase;
  }
  .grid-light .rail .tp .label{color:var(--paper-line);}

  .reveal{opacity:0; transform:translateY(18px); transition:opacity .7s ease, transform .7s ease;}
  .reveal.in{opacity:1; transform:translateY(0);}

  .eyebrow{
    font-family:'IBM Plex Mono',monospace; font-size:12px; letter-spacing:.14em;
    text-transform:uppercase; color:var(--teal); margin-bottom:14px; display:block;
  }

  /* ---------- hero ---------- */
  .hero{
    padding-top:170px; padding-bottom:120px; color:var(--cream); position:relative;
  }
  .hero-grid{
    display:grid; grid-template-columns:1.3fr 0.9fr; gap:50px; align-items:center;
  }
  @media (max-width:900px){.hero-grid{grid-template-columns:1fr;}}
  .hero-fn{
    font-family:'IBM Plex Mono',monospace; color:var(--brass); font-size:14px; margin-bottom:18px;
    letter-spacing:.02em;
  }
  .hero h1{
    font-size:clamp(48px,8vw,96px); line-height:0.94; text-transform:uppercase; color:var(--cream);
  }
  .hero .role{
    font-family:'IBM Plex Mono',monospace; color:var(--teal); font-size:15px; letter-spacing:.05em;
    margin-top:20px; text-transform:uppercase;
  }
  .hero p.tagline{
    max-width:520px; margin-top:22px; color:#C9D3D6; font-size:16px;
  }
  .cta-row{margin-top:36px; display:flex; gap:16px; flex-wrap:wrap;}
  .btn{
    display:inline-flex; align-items:center; gap:8px;
    padding:13px 22px; font-family:'IBM Plex Mono',monospace; font-size:13px;
    letter-spacing:.04em; text-transform:uppercase; border-radius:var(--radius);
    transition:transform .2s ease, background .2s ease;
  }
  .btn-primary{background:var(--teal); color:var(--navy); font-weight:600;}
  .btn-primary:hover{transform:translateY(-2px);}
  .btn-ghost{border:1px solid var(--navy-line); color:var(--cream);}
  .btn-ghost:hover{border-color:var(--teal); color:var(--teal);}

  .scope{
    background:rgba(255,255,255,0.02);
    border:1px solid var(--navy-line);
    border-radius:4px; padding:20px;
  }
  .scope svg{width:100%; height:auto; display:block;}
  .scope-caption{
    font-family:'IBM Plex Mono',monospace; font-size:11px; color:#7C93A0;
    margin-top:12px; letter-spacing:.04em; display:flex; justify-content:space-between;
  }
  .curve-path{
    stroke-dasharray:600; stroke-dashoffset:600;
    animation:draw 2.2s ease forwards .3s;
  }
  @keyframes draw{to{stroke-dashoffset:0;}}

  /* ---------- headings / body ---------- */
  h2.section-title{
    font-size:clamp(28px,4vw,40px); text-transform:uppercase; margin-bottom:6px;
  }
  .grid-dark h2.section-title{color:var(--cream);}
  .section-sub{
    font-family:'IBM Plex Mono',monospace; font-size:13px; color:var(--teal-dim);
    margin-bottom:34px;
  }
  .grid-dark .section-sub{color:#7C93A0;}

  /* ---------- about ---------- */
  .about-cols{display:grid; grid-template-columns:1.1fr 0.9fr; gap:50px;}
  @media (max-width:800px){.about-cols{grid-template-columns:1fr;}}
  .about-cols p{margin-bottom:16px; font-size:16px;}
  .credential-card{
    border:1px solid var(--paper-line); background:#fff; padding:26px;
    border-radius:4px;
  }
  .credential-card .cred{display:flex; justify-content:space-between; padding:12px 0; border-bottom:1px dashed var(--paper-line); font-size:14px;}
  .credential-card .cred:last-child{border-bottom:none;}
  .credential-card .cred span:first-child{color:#6b6558;}
  .credential-card .cred span:last-child{font-family:'IBM Plex Mono',monospace; font-weight:500;}

  /* ---------- experience ---------- */
  .exp-item{
    padding:26px 0; border-bottom:1px solid var(--navy-line);
  }
  .exp-item:first-child{padding-top:0;}
  .exp-head{display:flex; flex-wrap:wrap; justify-content:space-between; align-items:baseline; gap:8px; color:var(--cream);}
  .exp-head h3{font-size:20px;}
  .exp-head .period{font-family:'IBM Plex Mono',monospace; font-size:12px; color:var(--teal);}
  .exp-org{font-family:'IBM Plex Mono',monospace; font-size:13px; color:#8FA5B0; margin-top:4px;}
  .exp-item p{color:#C9D3D6; margin-top:12px; max-width:640px; font-size:15px;}

  /* ---------- ATL problem sets ---------- */
  .pset{
    display:grid; grid-template-columns:90px 1fr; gap:24px;
    padding:28px 0; border-bottom:1px dashed var(--paper-line);
  }
  .pset:first-child{padding-top:0;}
  .pset-num{font-family:'IBM Plex Mono',monospace; font-size:34px; color:var(--brass); font-weight:500;}
  .pset h3{font-size:19px; margin-bottom:8px;}
  .pset p{font-size:15px; color:#4A463C;}

  /* ---------- skills ---------- */
  .skills-grid{display:grid; grid-template-columns:1fr 1fr; gap:60px;}
  @media (max-width:800px){.skills-grid{grid-template-columns:1fr;}}
  .bar-item{margin-bottom:20px;}
  .bar-item .bl{
    display:flex; justify-content:space-between; font-size:13px; color:var(--cream);
    margin-bottom:8px; font-family:'IBM Plex Mono',monospace;
  }
  .bar-track{height:6px; background:var(--navy-line); border-radius:3px; overflow:hidden;}
  .bar-fill{height:100%; background:linear-gradient(90deg,var(--teal-dim),var(--teal)); border-radius:3px; width:0; transition:width 1.2s ease;}
  .chip-cloud{display:flex; flex-wrap:wrap; gap:10px;}
  .chip{
    font-family:'IBM Plex Mono',monospace; font-size:12px; padding:8px 14px;
    border:1px solid var(--navy-line); border-radius:20px; color:#C9D3D6;
  }

  /* ---------- stats + quote ---------- */
  .stats-row{display:grid; grid-template-columns:repeat(3,1fr); gap:30px; margin-bottom:56px;}
  @media (max-width:700px){.stats-row{grid-template-columns:1fr 1fr;}}
  .stat{border-top:2px solid var(--ink); padding-top:14px;}
  .stat .num{font-size:44px; font-family:'Space Grotesk',sans-serif; font-weight:600;}
  .stat .lbl{font-family:'IBM Plex Mono',monospace; font-size:12px; text-transform:uppercase; color:#6b6558; margin-top:6px;}
  blockquote{
    border-left:3px solid var(--brass); padding-left:24px; font-size:20px;
    font-family:'Space Grotesk',sans-serif; max-width:620px; color:var(--ink);
  }
  blockquote cite{
    display:block; margin-top:14px; font-family:'IBM Plex Mono',monospace;
    font-size:12px; font-style:normal; color:#6b6558;
  }

  /* ---------- contact / footer ---------- */
  footer{padding:90px 0 40px; color:var(--cream); position:relative;}
  .contact-grid{display:grid; grid-template-columns:1.2fr 1fr; gap:50px;}
  @media (max-width:800px){.contact-grid{grid-template-columns:1fr;}}
  footer h2{font-size:clamp(30px,5vw,46px); text-transform:uppercase; margin-bottom:18px;}
  footer p.lead{color:#C9D3D6; max-width:440px; margin-bottom:30px;}
  .contact-list{display:flex; flex-direction:column; gap:18px;}
  .contact-list .row{display:flex; gap:14px; align-items:center; font-size:15px;}
  .contact-list .k{
    font-family:'IBM Plex Mono',monospace; font-size:11px; text-transform:uppercase;
    color:var(--teal); width:90px; flex:none;
  }
  .avail-card{
    border:1px solid var(--navy-line); border-radius:4px; padding:26px;
    background:rgba(255,255,255,0.02);
  }
  .avail-card .dot-live{display:inline-flex; align-items:center; gap:8px; font-family:'IBM Plex Mono',monospace; font-size:12px; color:var(--teal); text-transform:uppercase; margin-bottom:14px;}
  .avail-card .dot-live::before{content:""; width:8px; height:8px; border-radius:50%; background:var(--teal); box-shadow:0 0 8px var(--teal);}
  .foot-bottom{
    margin-top:70px; padding-top:20px; border-top:1px solid var(--navy-line);
    display:flex; justify-content:space-between; flex-wrap:wrap; gap:10px;
    font-family:'IBM Plex Mono',monospace; font-size:11px; color:#6b7c86;
  }

  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.01ms !important; transition-duration:0.01ms !important;}
  }
</style>
</head>
<body>

<nav>
  <div class="brandmark"><span class="node"></span>VAISHNAVI</div>
  <button class="nav-toggle" id="navToggle" aria-label="Toggle menu"><span></span><span></span><span></span></button>
  <ul id="navList">
    <li><a href="#about">About</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#atl">ATL Lab</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<header class="hero grid-dark">
  <div class="wrap">
    <div class="hero-grid">
      <div>
        <div class="hero-fn">f(x) = teaching × tinkering</div>
        <h1>Vaishnavi</h1>
        <div class="role">Mathematics Educator — Atal Tinkering Lab Incharge</div>
        <p class="tagline">I teach mathematics the way a good circuit is built: from first principles, tested piece by piece. As ATL Incharge, I help students move ideas off the page and onto the breadboard.</p>
        <div class="cta-row">
          <a href="#contact" class="btn btn-primary">Get in touch →</a>
          <a href="#atl" class="btn btn-ghost">View ATL Work</a>
        </div>
      </div>
      <div class="scope">
        <svg viewBox="0 0 320 220" fill="none" xmlns="http://www.w3.org/2000/svg">
          <line x1="20" y1="190" x2="300" y2="190" stroke="#1D3444" stroke-width="1"/>
          <line x1="20" y1="190" x2="20" y2="20" stroke="#1D3444" stroke-width="1"/>
          <g stroke="#16303e" stroke-width="1">
            <line x1="60" y1="20" x2="60" y2="190"/><line x1="100" y1="20" x2="100" y2="190"/>
            <line x1="140" y1="20" x2="140" y2="190"/><line x1="180" y1="20" x2="180" y2="190"/>
            <line x1="220" y1="20" x2="220" y2="190"/><line x1="260" y1="20" x2="260" y2="190"/>
            <line x1="20" y1="150" x2="300" y2="150"/><line x1="20" y1="110" x2="300" y2="110"/>
            <line x1="20" y1="70" x2="300" y2="70"/>
          </g>
          <path class="curve-path" d="M20 170 L60 168 L90 150 Q110 90 140 70 L165 90 Q185 130 210 60 L235 50 L300 40"
                stroke="#4BDAC2" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/>
          <circle cx="140" cy="70" r="4" fill="#D9A441"/>
          <circle cx="300" cy="40" r="4" fill="#4BDAC2"/>
        </svg>
        <div class="scope-caption"><span>CH1 · STUDENT OUTCOMES</span><span>ATL.SCOPE</span></div>
      </div>
    </div>
  </div>
</header>

<!-- ABOUT -->
<section id="about" class="grid-light">
  <div class="wrap rail-row">
    <div class="rail"><div class="tp"><div class="dot" data-target="about"></div><span class="label mono">TP-01</span></div></div>
    <div class="reveal">
      <span class="eyebrow" style="color:var(--teal-dim)">About</span>
      <div class="about-cols">
        <div>
          <p>I'm a mathematics teacher with a Master's degree in Mathematics, currently teaching at <strong>[School Name]</strong>. Alongside the classroom, I run the school's <strong>Atal Tinkering Lab</strong> — introducing students to electronics, robotics kits, 3D design, and hands-on problem solving.</p>
          <p>My approach treats mathematics and tinkering as two ends of the same skill: both reward precision, iteration, and comfort with getting something wrong before getting it right. I use that overlap to make abstract topics — functions, geometry, probability — visible through circuits, sensors, and small builds.</p>
          <p>I'm continuing to build my own foundation in electronics alongside the students I mentor, and I'm always looking for new ways to connect the two disciplines in the classroom.</p>
        </div>
        <div class="credential-card">
          <div class="cred"><span>Degree</span><span>M.Sc. Mathematics</span></div>
          <div class="cred"><span>Current Role</span><span>Mathematics Teacher</span></div>
          <div class="cred"><span>Additional Charge</span><span>ATL Incharge</span></div>
          <div class="cred"><span>Focus Areas</span><span>Math Pedagogy · Electronics</span></div>
          <div class="cred"><span>Based In</span><span>[City, State]</span></div>
          <div class="cred"><span>Status</span><span>Open to Collaborate</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience" class="grid-dark">
  <div class="wrap rail-row">
    <div class="rail"><div class="tp"><div class="dot" data-target="experience"></div><span class="label mono">TP-02</span></div></div>
    <div class="reveal">
      <span class="eyebrow">Experience</span>
      <h2 class="section-title" style="color:var(--cream)">Where I work</h2>
      <div class="section-sub">Classroom and lab, side by side</div>

      <div class="exp-item">
        <div class="exp-head">
          <h3>Mathematics Teacher</h3>
          <span class="period mono">[Year] — Present</span>
        </div>
        <div class="exp-org">[School Name] · [City]</div>
        <p>Teaching mathematics to grades [X–X], covering algebra, geometry, and statistics. Design lesson plans that connect abstract concepts to real-world problem solving, and assess learning through applied, project-based tasks where possible.</p>
      </div>

      <div class="exp-item">
        <div class="exp-head">
          <h3>Atal Tinkering Lab Incharge</h3>
          <span class="period mono">[Year] — Present</span>
        </div>
        <div class="exp-org">[School Name] · ATL / AIM, NITI Aayog</div>
        <p>Manage the school's Atal Tinkering Lab — including its electronics kits, 3D printer, robotics equipment, and basic prototyping tools. Mentor student teams from idea to working prototype, run introductory electronics sessions, and coordinate participation in innovation challenges and exhibitions.</p>
      </div>
    </div>
  </div>
</section>

<!-- ATL PROBLEM SETS -->
<section id="atl" class="grid-light">
  <div class="wrap rail-row">
    <div class="rail"><div class="tp"><div class="dot" data-target="atl"></div><span class="label mono">TP-03</span></div></div>
    <div class="reveal">
      <span class="eyebrow" style="color:var(--teal-dim)">ATL Lab</span>
      <h2 class="section-title">Selected initiatives</h2>
      <div class="section-sub">Logged as problem sets, the way a worksheet would number them</div>

      <div class="pset">
        <div class="pset-num">01</div>
        <div>
          <h3>Circuit Foundations Workshop</h3>
          <p>An introductory series on breadboards, LEDs, resistors, and simple series/parallel circuits — built for students with no prior electronics background.</p>
        </div>
      </div>
      <div class="pset">
        <div class="pset-num">02</div>
        <div>
          <h3>Student Innovation Challenge</h3>
          <p>Guided student teams through the full build cycle — problem framing, sensor selection, prototyping, and testing — culminating in a working demonstration.</p>
        </div>
      </div>
      <div class="pset">
        <div class="pset-num">03</div>
        <div>
          <h3>Math Through Making</h3>
          <p>Sessions that use ATL tools to make geometry and measurement tangible — scale, proportion, and angles applied directly to physical builds.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills" class="grid-dark">
  <div class="wrap rail-row">
    <div class="rail"><div class="tp"><div class="dot" data-target="skills"></div><span class="label mono">TP-04</span></div></div>
    <div class="reveal">
      <span class="eyebrow">Skills &amp; Toolkit</span>
      <h2 class="section-title" style="color:var(--cream)">What I bring</h2>
      <div class="section-sub">Two disciplines, one habit of mind</div>

      <div class="skills-grid">
        <div>
          <div class="bar-item"><div class="bl"><span>Mathematics Pedagogy</span><span>95%</span></div><div class="bar-track"><div class="bar-fill" data-w="95"></div></div></div>
          <div class="bar-item"><div class="bl"><span>Curriculum &amp; Lesson Design</span><span>90%</span></div><div class="bar-track"><div class="bar-fill" data-w="90"></div></div></div>
          <div class="bar-item"><div class="bl"><span>ATL Lab Management</span><span>88%</span></div><div class="bar-track"><div class="bar-fill" data-w="88"></div></div></div>
          <div class="bar-item"><div class="bl"><span>Basic Electronics</span><span>75%</span></div><div class="bar-track"><div class="bar-fill" data-w="75"></div></div></div>
          <div class="bar-item"><div class="bl"><span>Student Mentorship</span><span>92%</span></div><div class="bar-track"><div class="bar-fill" data-w="92"></div></div></div>
        </div>
        <div>
          <p class="mono" style="font-size:12px; color:#7C93A0; text-transform:uppercase; margin-bottom:16px;">Tools &amp; Concepts</p>
          <div class="chip-cloud">
            <span class="chip">Algebra</span><span class="chip">Geometry</span><span class="chip">Statistics</span>
            <span class="chip">Arduino</span><span class="chip">Breadboarding</span><span class="chip">Sensors</span>
            <span class="chip">3D Printing</span><span class="chip">Robotics Kits</span><span class="chip">Lesson Planning</span>
            <span class="chip">Workshop Facilitation</span><span class="chip">Project-Based Learning</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- IMPACT + QUOTE -->
<section class="grid-light">
  <div class="wrap rail-row">
    <div class="rail"><div class="tp"><div class="dot" data-target="impact"></div><span class="label mono">TP-05</span></div></div>
    <div class="reveal" id="impact">
      <span class="eyebrow" style="color:var(--teal-dim)">Impact</span>
      <h2 class="section-title">In numbers</h2>
      <div class="section-sub">Update with your own figures</div>
      <div class="stats-row">
        <div class="stat"><div class="num">[X]+</div><div class="lbl">Years Teaching</div></div>
        <div class="stat"><div class="num">[X]+</div><div class="lbl">Students Mentored in ATL</div></div>
        <div class="stat"><div class="num">[X]+</div><div class="lbl">Workshops Conducted</div></div>
      </div>
      <blockquote>
        Mathematics is the language in which the universe is written.
        <cite>— Galileo Galilei</cite>
      </blockquote>
    </div>
  </div>
</section>

<!-- CONTACT -->
<footer id="contact" class="grid-dark">
  <div class="wrap">
    <div class="contact-grid">
      <div>
        <span class="eyebrow">Let's Connect</span>
        <h2>Let's build something worth testing.</h2>
        <p class="lead">Open to collaborations, guest sessions, and conversations about STEM education, ATL programs, or mathematics teaching.</p>
        <div class="contact-list">
          <div class="row"><span class="k mono">Email</span><span>[your.email@example.com]</span></div>
          <div class="row"><span class="k mono">Phone</span><span>[+91 XXXXX XXXXX]</span></div>
          <div class="row"><span class="k mono">Location</span><span>[City, State]</span></div>
          <div class="row"><span class="k mono">LinkedIn</span><span>[linkedin.com/in/your-profile]</span></div>
        </div>
      </div>
      <div class="avail-card">
        <div class="dot-live">Open to Opportunities</div>
        <p style="color:#C9D3D6; font-size:14px;">Currently teaching and running the ATL at [School Name]. Happy to discuss guest workshops, ATL mentorship exchanges, or curriculum collaboration.</p>
      </div>
    </div>
    <div class="foot-bottom">
      <span>© <span id="year"></span> VAISHNAVI</span>
      <span>DESIGNED FOR MATH + MAKING</span>
    </div>
  </div>
</footer>

<script>
  document.getElementById('year').textContent = new Date().getFullYear();

  const navToggle = document.getElementById('navToggle');
  const navList = document.getElementById('navList');
  navToggle.addEventListener('click', () => navList.classList.toggle('open'));
  navList.querySelectorAll('a').forEach(a => a.addEventListener('click', () => navList.classList.remove('open')));

  // reveal on scroll
  const revealEls = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('in'); });
  }, {threshold:0.15});
  revealEls.forEach(el => io.observe(el));

  // light up rail dots as their section is in view
  const dots = document.querySelectorAll('.rail .dot');
  const sectionIds = ['about','experience','atl','skills','impact'];
  const sectionEls = sectionIds.map(id => document.getElementById(id)).filter(Boolean);
  const dotIo = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      const dot = document.querySelector(`.dot[data-target="${entry.target.id}"]`);
      if(dot){ dot.classList.toggle('lit', entry.isIntersecting); }
    });
  }, {threshold:0.3});
  sectionEls.forEach(el => dotIo.observe(el));

  // animate skill bars once visible
  const bars = document.querySelectorAll('.bar-fill');
  const barIo = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if(e.isIntersecting){
        e.target.style.width = e.target.dataset.w + '%';
        barIo.unobserve(e.target);
      }
    });
  }, {threshold:0.4});
  bars.forEach(b => barIo.observe(b));
</script>
</body>
</html>
