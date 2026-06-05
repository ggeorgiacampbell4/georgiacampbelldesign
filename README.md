<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Georgia Campbell — Portfolio</title>
  <link rel="stylesheet" href="style.css">
  <style>
    /* ---- HERO ---- */
    #hero {
      display: grid;
      grid-template-columns: 1fr 1fr;
      min-height: 100vh;
      max-width: 100%;
      border-bottom: 1px solid var(--line);
    }
    .hero-photo {
      position: relative;
      overflow: hidden;
    }
    .hero-photo img {
      width: 100%; height: 100%;
      object-fit: cover; object-position: center top;
      display: block;
    }
    .hero-right {
      background: #2C2A26;
      display: flex; flex-direction: column; justify-content: flex-end;
      padding: 5rem 4rem;
    }
    .hero-tag {
      font-size: 0.72rem; letter-spacing: 0.18em; text-transform: uppercase;
      color: var(--accent-light); margin-bottom: 1.5rem;
      display: flex; align-items: center; gap: 0.75rem;
    }
    .hero-tag::before {
      content: ''; display: block; width: 2.5rem; height: 1px;
      background: var(--accent-light);
    }
    h1 {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3.5rem, 6vw, 7rem);
      font-weight: 300; line-height: 0.92;
      letter-spacing: -0.01em; color: #F7F4EF;
      margin-bottom: 2rem;
    }
    h1 em { font-style: italic; color: var(--accent-light); }
    .hero-desc {
      color: rgba(247,244,239,0.65); font-size: 0.95rem; line-height: 1.75;
      margin-bottom: 2rem; max-width: 420px;
    }
    .hero-meta {
      font-size: 0.8rem; color: rgba(247,244,239,0.45); line-height: 1.8;
      border-top: 1px solid rgba(247,244,239,0.1); padding-top: 1.5rem;
    }
    .hero-meta strong { color: rgba(247,244,239,0.85); font-weight: 500; display: block; }
    @media (max-width: 768px) {
      #hero { grid-template-columns: 1fr; }
      .hero-photo { height: 60vw; }
      .hero-right { padding: 3rem 1.5rem; }
    }

    /* ---- ABOUT ---- */
    .about-grid {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 5rem; align-items: start;
    }
    .about-text p {
      color: var(--mid); line-height: 1.85;
      margin-bottom: 1.25rem; font-size: 0.95rem;
    }
    .skills-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 0; }
    .skill-cat { border-top: 1px solid var(--line); padding: 1.25rem 0; }
    .skill-cat:nth-child(odd) { padding-right: 1.5rem; }
    .skill-cat:nth-child(even) { padding-left: 1.5rem; border-left: 1px solid var(--line); }
    .skill-cat-name {
      font-size: 0.68rem; letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--accent); margin-bottom: 0.6rem;
    }
    .skill-cat ul { list-style: none; }
    .skill-cat li { font-size: 0.85rem; color: var(--mid); padding: 0.2rem 0; }

    /* ---- RESEARCH ---- */
    .research-list { display: flex; flex-direction: column; }
    .research-item {
      display: grid; grid-template-columns: 3.5rem 1fr;
      gap: 0 2rem; border-top: 1px solid var(--line); padding: 2rem 0;
    }
    .research-item:last-child { border-bottom: 1px solid var(--line); }
    .r-year {
      font-family: 'Cormorant Garamond', serif;
      font-size: 0.85rem; color: var(--muted); padding-top: 0.1rem;
    }
    .r-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.5rem; font-weight: 400; color: var(--dark); margin-bottom: 0.4rem;
    }
    .r-org {
      font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase;
      color: var(--accent); margin-bottom: 0.75rem;
    }
    .r-desc { font-size: 0.88rem; color: var(--mid); line-height: 1.75; max-width: 640px; }
    .r-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.9rem; }

    /* ---- PROJECTS GRID ---- */
    .projects-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
    .project-card {
      background: var(--card-bg); border: 1px solid var(--line);
      border-radius: 4px; overflow: hidden; text-decoration: none;
      display: block; color: inherit;
      transition: transform 0.25s, box-shadow 0.25s;
    }
    .project-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 40px rgba(28,28,26,0.1);
    }
    .project-card-top {
      height: 7rem; display: flex; align-items: center; justify-content: center;
      font-size: 2.5rem;
      background: linear-gradient(135deg, #EDE8E0 0%, #DDD5C8 100%);
    }
    .project-card-body { padding: 1.25rem; }
    .project-card-year { font-size: 0.68rem; color: var(--muted); letter-spacing: 0.1em; margin-bottom: 0.4rem; }
    .project-card-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.2rem; font-weight: 400; color: var(--dark); margin-bottom: 0.5rem; line-height: 1.3;
    }
    .project-card-desc { font-size: 0.8rem; color: var(--mid); line-height: 1.65; }
    .project-card-award {
      display: inline-flex; align-items: center; gap: 0.35rem; margin-top: 0.75rem;
      font-size: 0.68rem; letter-spacing: 0.06em; color: var(--accent); text-transform: uppercase;
    }
    .award-dot { width: 5px; height: 5px; border-radius: 50%; background: var(--accent); flex-shrink: 0; }
    .card-link-hint {
      display: flex; align-items: center; gap: 0.3rem; margin-top: 1rem;
      font-size: 0.72rem; color: var(--accent); letter-spacing: 0.06em; text-transform: uppercase;
    }

    /* ---- EXPERIENCE ---- */
    .exp-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 3rem 5rem; }
    .exp-role {
      font-family: 'Cormorant Garamond', serif; font-size: 1.3rem; color: var(--dark); margin-bottom: 0.2rem;
    }
    .exp-place {
      font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--accent); margin-bottom: 0.3rem;
    }
    .exp-dates { font-size: 0.78rem; color: var(--muted); margin-bottom: 0.75rem; }
    .exp-desc { font-size: 0.85rem; color: var(--mid); line-height: 1.75; }

    /* ---- HONOURS ---- */
    .honours-list { display: flex; flex-direction: column; }
    .honour-item {
      display: flex; align-items: baseline; justify-content: space-between;
      gap: 2rem; border-top: 1px solid var(--line); padding: 1.1rem 0; flex-wrap: wrap;
    }
    .honour-item:last-child { border-bottom: 1px solid var(--line); }
    .honour-name {
      font-family: 'Cormorant Garamond', serif; font-size: 1.2rem; font-weight: 400; color: var(--dark);
    }
    .honour-detail { font-size: 0.8rem; color: var(--mid); max-width: 360px; text-align: right; }
    .honour-year { font-size: 0.75rem; color: var(--muted); white-space: nowrap; text-align: right; }

    /* ---- CONTACT ---- */
    .contact-inner {
      display: flex; justify-content: space-between; align-items: flex-end;
      flex-wrap: wrap; gap: 2rem;
    }
    .contact-cta {
      font-family: 'Cormorant Garamond', serif;
      font-size: 3.5rem; font-weight: 300; line-height: 1.1;
      color: var(--dark); max-width: 500px;
    }
    .contact-cta em { font-style: italic; color: var(--accent); }
    .contact-links { display: flex; flex-direction: column; gap: 0.75rem; align-items: flex-end; }
    .contact-link {
      font-size: 0.8rem; letter-spacing: 0.08em; text-transform: uppercase;
      color: var(--mid); text-decoration: none;
      display: flex; align-items: center; gap: 0.5rem; transition: color 0.2s;
    }
    .contact-link:hover { color: var(--accent); }

    /* ---- RESPONSIVE ---- */
    @media (max-width: 768px) {
      #hero { padding: 7rem 1.5rem 3rem; }
      h1 { font-size: 4rem; }
      .about-grid { grid-template-columns: 1fr; gap: 2.5rem; }
      .projects-grid { grid-template-columns: 1fr; }
      .exp-grid { grid-template-columns: 1fr; gap: 2rem; }
      .research-item { grid-template-columns: 2.5rem 1fr; }
    }
  </style>
</head>
<body>

<nav>
  <a href="index.html" class="nav-name">Georgia Campbell</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#research">Research</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<div id="hero">
  <div class="hero-photo">
    <img src="images/gcamp_headshot.jpg" alt="Georgia Campbell">
  </div>
  <div class="hero-right">
    <div class="hero-tag">Mechanical &amp; Biomedical Engineering</div>
    <h1>Georgia<br><em>Campbell</em></h1>
    <p class="hero-desc">
      Fourth-year engineering student at McMaster University with experience in mechanical design, biomechanical research, and policy development, driven by a passion for human-centred design and accessible healthcare innovation.
     </p>

          <a href="files/GCampbell_CV.pdf" target="_blank" class="contact-link" style="display:inline-flex; margin-bottom:2.5rem; color:#F7F4EF;">
            View Full CV →
          </a>

    <div class="hero-meta">
      <strong>McMaster University</strong>
      Hamilton, Ontario<br>
      Year IV · 2022–2028<br>
      2022 Ralph M. Barford Loran Scholar
      
    </div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-header">
    <span class="section-label">About</span>
    <div class="section-line"></div>
    <span class="section-num">01</span>
  </div>
  <div class="about-grid">
    <div class="about-text">
      <p>I'm a Métis engineering student pursuing a dual degree in Mechanical and Biomedical Engineering, motivated by the intersection of biomechanics, assistive technology, and Indigenous health equity.</p>
      <p>My work spans mechanical design and manufacturing, biomechanical research, human-centered and data-driven design, all grounded in a commitment to community and accessible innovation.</p>
      <p>Outside the lab, I choreograph for the McMaster Engineering Musical, enjoy spending time outside, and advocate for Indigenous students in STEM.</p>
    </div>
    <div>
      <div class="skills-grid">
        <div class="skill-cat">
          <div class="skill-cat-name">Software</div>
          <ul>
            <li>SolidWorks</li><li>Autodesk Fusion 360</li><li>Autodesk Inventor</li>
            <li>MATLAB</li><li>Python</li>
          </ul>
        </div>
        <div class="skill-cat">
          <div class="skill-cat-name">Engineering</div>
          <ul>
            <li>Biomechanics &amp; kinematics</li><li>3D printing &amp; CAD</li>
            <li>ASTM-based testing</li><li>Ergonomic & Anthropomorphic design</li><li>Carbon fiber fabrication</li>
          </ul>
        </div>
        <div class="skill-cat">
          <div class="skill-cat-name">Wet Lab Techniques</div>
          <ul>
            <li>Molecular cloning</li><li>Gel electrophoresis / PCR</li>
            <li>Protein purification</li><li>Cell culturing</li><li>SDS-PAGE</li>
          </ul>
        </div>
        <div class="skill-cat">
          <div class="skill-cat-name">Interests</div>
          <ul>
            <li>Indigenous health equity</li><li>Assistive technology</li>
            <li>Accessible biomechanics</li><li>Automotive Safety</li><li>Community advocacy</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- RESEARCH -->
<section id="research">
  <div class="section-header">
    <span class="section-label">Research</span>
    <div class="section-line"></div>
    <span class="section-num">02</span>
  </div>
  <h2>Research<br>Experience</h2><br>
    <div class="research-item">
      <div class="r-year">2026</div>
      <div>
        <div class="r-org">McMaster Injury Biomechanics Lab · Undergraduate Researcher</div>
        <div class="r-title">TPU–Silicone Soft-Tissue Surrogate for Crash Test Devices</div>
        <p class="r-desc">Designed and prototyped a composite soft-tissue surrogate for anthropomorphic test devices (ATDs), including CAD development of interlocking geometries and casting molds. Evaluated candidate materials and planned ASTM-based compression and impact testing to validate biofidelity and durability.</p>
        <div class="r-tags">
          <span class="tag">TPU / Silicone</span><span class="tag">CAD Mold Design</span>
          <span class="tag">ASTM Testing</span><span class="tag">Biofidelity</span>
        </div>
      </div>
    </div>
    <div class="research-list">
    <div class="research-item">
      <div class="r-year">2026</div>
      <div>
        <div class="r-org">McMaster University · Computational Biomechanics</div>
        <div class="r-title">Markerless Motion Capture for Soccer Kick Kinematics</div>
        <p class="r-desc">Designed and conducted an ethics-approved study using smartphone-based OpenCap to quantify 3D lower-extremity kinematics during an inside-of-the-foot soccer kick. Performed multi-view camera calibration and OpenSim-based inverse kinematics to extract hip, knee, ankle, and pelvis motion — with emphasis on dominant vs. non-dominant limb asymmetries.</p>
        <div class="r-tags">
          <span class="tag">OpenCap</span><span class="tag">OpenSim</span>
          <span class="tag">Inverse Kinematics</span><span class="tag">Motion Capture</span>
        </div>
      </div>
    </div>
    <div class="research-item">
      <div class="r-year">2023</div>
      <div>
        <div class="r-org">McMaster University · BBS Summer Scholar</div>
        <div class="r-title">Molecular Cloning &amp; Protein Purification of MamJ</div>
        <p class="r-desc">Conducted molecular cloning and protein purification of MamJ — a protein critical for magnetotactic bacteria — using gel electrophoresis, PCR, Bradford Assay, Gibson Assembly, and bacterial transformations to create and validate transformed plasmid vectors.</p>
        <div class="r-tags">
          <span class="tag">Gibson Assembly</span><span class="tag">PCR</span>
          <span class="tag">Protein Purification</span><span class="tag">Molecular Cloning</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-header">
    <span class="section-label">Projects</span>
    <div class="section-line"></div>
    <span class="section-num">03</span>
  </div>
  <h2>Design &amp;<br>Project Work</h2><br>
  <div class="projects-grid">

    <a class="project-card" href="projects/formula-sae.html">
      <div class="project-card-top">
        <img src="images/MACFE_cover.JPG" alt="McMaster Formula SAE Electic" style="width:100%; height:100%; object-fit:cover;">
      </div>
      <div class="project-card-body">
        <div class="project-card-year">2025–Present</div>
        <div class="project-card-title">Formula SAE Electric — Driver Interface</div>
        <p class="project-card-desc">Designed the 2026 driver interface in SolidWorks for a quarter-scale Formula car, reducing weight by 5%.</p>
        <div class="card-link-hint">View project →</div>
      </div>
    </a>

    <a class="project-card" href="projects/atd-surrogate.html">
      <div class="project-card-top">
        <img src="images/research_question.png" alt="ATD Surrogate" style="width:100%; height:100%; object-fit:cover;">
      </div>
      <div class="project-card-body">
        <div class="project-card-year">2025–2026</div>
        <div class="project-card-title">ATD Soft-Tissue Surrogate</div>
        <p class="project-card-desc">TPU–silicone composite surrogate for anthropomorphic test devices (crash test dummies) with ASTM-validated biofidelity testing.</p>
        <div class="card-link-hint">View project →</div>
      </div>
    </a>

    <a class="project-card" href="projects/plant-watering.html">
      <div class="project-card-top">
        <img src="images/plart_team.jpg" alt="Automated Plant-Watering System" style="width:100%; height:100%; object-fit:cover;">
      </div>
      <div class="project-card-body">
        <div class="project-card-year">Winter 2025</div>
        <div class="project-card-title">Automated Plant-Watering System</div>
        <p class="project-card-desc">Arduino-controlled peristaltic pump with a Python-based input database for scheduled, species-specific water dosing.</p>
        <div class="project-card-award"><span class="award-dot"></span>Project Distinction Award</div>
        <div class="card-link-hint">View project →</div>
      </div>
    </a>

    <a class="project-card" href="projects/dexterity-device.html">
      <div class="project-card-top">
        <img src="images/bb_cover.jpg" alt="BackingBuddy Earring Backing Applicator" style="width:100%; height:100%; object-fit:cover;">
      </div>
      <div class="project-card-body">
        <div class="project-card-year">Winter 2023</div>
        <div class="project-card-title">Assistive Dexterity Device for MS Users</div>
        <p class="project-card-desc">Assistive device for earring backing application, designed for individuals with impaired hand dexterity.</p>
        <div class="project-card-award"><span class="award-dot"></span>Project Distinction Award</div>
        <div class="card-link-hint">View project →</div>
      </div>
    </a>

        <a class="project-card" href="projects/swimmer-device.html">
      <div class="project-card-top">
        <img src="images/swim_cover.JPEG" alt="Wall-detecting goggle attachment for Visually Impaired Swimmers" style="width:100%; height:100%; object-fit:cover;">
      </div>
      <div class="project-card-body">
        <div class="project-card-year">Winter 2023</div>
        <div class="project-card-title">Wearable for Visually Impaired Swimmers</div>
        <p class="project-card-desc">Mechanical feedback wearable device enabling visually impaired swimmers to navigate pool boundaries independently.</p>
        <div class="card-link-hint">View project →</div>
      </div>
    </a>

</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-header">
    <span class="section-label">Experience</span>
    <div class="section-line"></div>
    <span class="section-num">04</span>
  </div>
  <h2>Work &amp;<br>Leadership</h2><br>
  <div class="exp-grid">
    <div class="exp-item">
      <div class="exp-role">Human Factors &amp; Ergonomics Lead</div>
      <div class="exp-place">McMaster Formula SAE Electric</div>
      <div class="exp-dates">Sept 2025–Present</div>
      <p class="exp-desc">Led a team of 10 engineers designing the 2026 vehicle driver interface. Oversaw carbon fibre fabrication and managed sponsorship outreach.</p>
    </div>
    <div class="exp-item">
      <div class="exp-role">Instructional Teaching Assistant</div>
      <div class="exp-place">McMaster University</div>
      <div class="exp-dates">Sept 2023–Present · Hamilton, ON</div>
      <p class="exp-desc">Led weekly tutorials reinforcing engineering design principles; evaluated student projects and delivered constructive feedback on technical execution.</p>
    </div>
    <div class="exp-item">
      <div class="exp-role">Program Development Intern</div>
      <div class="exp-place">Hotchkiss Brain Institute</div>
      <div class="exp-dates">May–Aug 2025 · Calgary, AB</div>
      <p class="exp-desc">Implemented a new office inventory platform and compiled 3 data banks supporting 200+ neuroscience researchers. Coordinated HBI's Annual Research Day (300+ attendees) and the G7 Brain Economy Summit.</p>
    </div>
    <div class="exp-item">
      <div class="exp-role">Biomedical Systems Co-op</div>
      <div class="exp-place">Victoria Hand Project</div>
      <div class="exp-dates">May–Aug 2024 · Victoria, BC</div>
      <p class="exp-desc">Conducted safety tests and modified 5+ upper-limb prosthetic components in SolidWorks and Fusion 360. Collaborated with engineers, clinicians, and suppliers to resolve manufacturing challenges.</p>
    </div>
    <div class="exp-item">
      <div class="exp-role">Secretary &amp; Conference Representative</div>
      <div class="exp-place">AISES McMaster Chapter</div>
      <div class="exp-dates">Sept 2023–Present</div>
      <p class="exp-desc">Represented the chapter at national conferences in Vancouver (2024), Toronto (2025), and Minneapolis (2025). Organized chapter meetings and supported member engagement.</p>
    </div>
    <div class="exp-item">
      <div class="exp-role">Co-Chair &amp; Internal Liaison</div>
      <div class="exp-place">McMaster Indigenous Health Movement</div>
      <div class="exp-dates">Sept 2023–Present</div>
      <p class="exp-desc">As Co-Chair, launched a podcast amplifying Indigenous voices and managed 35+ members. Led logistical planning for the 2024 Annual Conference (75+ attendees).</p>
    </div>
  </div>
</section>

<!-- HONOURS -->
<section id="honours">
  <div class="section-header">
    <span class="section-label">Distinctions</span>
    <div class="section-line"></div>
    <span class="section-num">05</span>
  </div>
  <h2>Honours &amp;<br>Awards</h2><br>
  <div class="honours-list">
    <div class="honour-item">
      <div class="honour-name">Ralph M. Barford Loran Scholar</div>
      <div class="honour-detail">Selected as 1 of 35 Scholars from 5,174 applicants. $100,000 value including tuition waiver, stipends, mentorship, and internship support.</div>
      <div class="honour-year">2022</div>
    </div>
    <div class="honour-item">
      <div class="honour-name">William Barry Hill Scholarship</div>
      <div class="honour-detail">$8,000 award to an Indigenous engineering student with high GPA.</div>
      <div class="honour-year">2025</div>
    </div>
    <div class="honour-item">
      <div class="honour-name">McMaster Award of Excellence</div>
      <div class="honour-detail">$3,000 award to the Top 10% of Engineering Faculty GPAs for iBioMed Year 1.</div>
      <div class="honour-year">2023</div>
    </div>
    <div class="honour-item">
      <div class="honour-name">McMaster Dean's Honour List</div>
      <div class="honour-detail">Awarded for maintaining a sessional average above 85% on a full-time course load.</div>
      <div class="honour-year">2022–Present</div>
    </div>
    <div class="honour-item">
      <div class="honour-name">Métis Health Policy Forum Representative</div>
      <div class="honour-detail">Represented Métis youth in Ontario in discussions on health inequities and policy.</div>
      <div class="honour-year">Feb 2025</div>
    </div>
    <div class="honour-item">
      <div class="honour-name">Indigenous Wellness Strategy Panelist</div>
      <div class="honour-detail">Selected panelist to share perspectives on Indigenous wellness, and community-led health initiatives.</div>
      <div class="honour-year">Oct 2024</div>
    </div>

<!-- CONTACT -->
<section id="contact" style="border-top: 1px solid var(--line);">
  <div class="section-header">
    <span class="section-label">Contact</span>
    <div class="section-line"></div>
    <span class="section-num">06</span>
  </div>
  <div class="contact-inner">
    <div class="contact-links" style="display:flex; flex-direction: row; gap: 1rem; align-items:center; flex-wrap:wrap;">
      <a href="mailto:campbg20@mcmaster.ca" class="contact-link">campbg20@mcmaster.ca</a>
      <span style="color:var(--accent-light);">|</span>
      <a href="tel:8076335334" class="contact-link">807 633 5334</a>
      <span style="color:var(--accent-light);">|</span>
      <a href="https://www.linkedin.com/in/georgia-campbell-372471249" class="contact-link">LinkedIn</a>
</div>

    </div>
  </div>
</section>

<footer>
  <span>© 2026 Georgia Campbell</span>
  <span>Mechanical &amp; Biomedical Engineering · McMaster University</span>
</footer>

</body>
</html>

/* =========================================
   GEORGIA CAMPBELL PORTFOLIO — SHARED STYLES
   ========================================= */

@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --cream: #F7F4EF;
  --dark: #1C1C1A;
  --mid: #4A4843;
  --muted: #8A8782;
  --accent: #8B5C3E;
  --accent-light: #D4A88A;
  --line: rgba(28,28,26,0.12);
  --card-bg: #FDFAF6;
}

html { scroll-behavior: smooth; }

body {
  font-family: 'DM Sans', sans-serif;
  background: var(--cream);
  color: var(--dark);
  font-size: 15px;
  line-height: 1.65;
}

/* ---- NAV ---- */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 1.25rem 4rem;
  background: rgba(247,244,239,0.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--line);
}
.nav-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.1rem; font-weight: 400;
  letter-spacing: 0.02em;
  color: var(--dark); text-decoration: none;
}
.nav-links { display: flex; gap: 2.5rem; list-style: none; }
.nav-links a {
  font-size: 0.8rem; letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--mid); text-decoration: none;
  transition: color 0.2s;
}
.nav-links a:hover { color: var(--accent); }

/* ---- SECTION SCAFFOLDING ---- */
section { padding: 7rem 4rem; max-width: 1100px; margin: 0 auto; }

.section-header {
  display: flex; align-items: center; gap: 1.5rem;
  margin-bottom: 3.5rem;
}
.section-label {
  font-size: 0.68rem; letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--accent); white-space: nowrap;
}
.section-line { flex: 1; height: 1px; background: var(--line); }
.section-num {
  font-family: 'Cormorant Garamond', serif;
  font-size: 0.85rem; color: var(--muted);
}

h2 {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2.8rem; font-weight: 300;
  margin-bottom: 1rem; line-height: 1.1;
  color: var(--dark);
}

/* ---- TAG ---- */
.tag {
  font-size: 0.68rem; letter-spacing: 0.08em; text-transform: uppercase;
  color: var(--accent); border: 1px solid var(--accent-light);
  padding: 0.2rem 0.6rem; border-radius: 2px;
}

/* ---- FOOTER ---- */
footer {
  padding: 2rem 4rem;
  border-top: 1px solid var(--line);
  display: flex; justify-content: space-between;
  font-size: 0.75rem; color: var(--muted);
}

/* ---- RESPONSIVE ---- */
@media (max-width: 768px) {
  nav { padding: 1rem 1.5rem; }
  .nav-links { gap: 1.25rem; }
  section { padding: 5rem 1.5rem; }
  footer { padding: 1.5rem; flex-direction: column; gap: 0.5rem; }
}
