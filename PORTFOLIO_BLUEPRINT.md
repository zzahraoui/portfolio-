# PORTFOLIO BLUEPRINT — ZAHRAOUI ZAKARIA
## Prompt Spec for Antigraphity (AI Code Generator)

> **Mission:** Reproduce the exact site architecture from `https://hamzabouda.github.io/portfolio/` with Zakaria's personal data and a LinkedIn-blue color palette. Deliver a single `index.html` file (CSS + JS inline) that is production-ready, responsive, and deployable on GitHub Pages / Netlify with zero external build steps.

---

## 1. REFERENCE ARCHITECTURE — HAMZA BOUDA PORTFOLIO

### 1.1 Overall Layout Pattern
- **Single-page application** (SPA) — all sections on one scrollable page
- **Fixed sidebar navigation** (left, ~60px wide on desktop) — vertical nav dots or icon links
- **Full-width sticky top navbar** — logo monogram `<ZZ/>` left + horizontal nav links right
- **7 numbered sections**, each occupying `min-height: 100vh`
- **Animated code block** (Python class) displayed in the hero — right panel, dark terminal style
- **Animated typing cursor** on the subtitle (role title)
- **Animated stat counters** (count-up on scroll) in About section
- **Skill progress bars** (animated on scroll entry)
- **Project cards grid** — featured cards larger/highlighted, others standard
- **Certification cards grid** — issuer badge + title + date + tags + link
- **Education timeline** (vertical, left-line)
- **Language badges** in Education section
- **Contact section** — left: text + info list; right: email CTA button
- **Footer** — centered, name + social icons

### 1.2 Navigation Structure
```
Navbar:  [<ZZ/>]  À propos | Expérience | Compétences | Projets | Certifications | Formation | Contact
```

### 1.3 Section Number Prefixes
Each section title is prefixed with a two-digit number:
```
01. À propos de moi
02. Expérience professionnelle
03. Compétences
04. Projets
05. Certifications
06. Formation
07. Contact
```

### 1.4 Scroll & Animation Behavior
- **IntersectionObserver** triggers `.visible` class on all `.section` elements
- Stat counters animate from 0 to target value when `#about` enters viewport
- Skill bars animate `width` from 0% to target% on scroll entry
- Hero code block has a **typewriter effect** (line-by-line reveal, ~40ms/char)
- Typing cursor `|` blinks on the subtitle role line
- Navbar background transitions from `transparent` → `rgba(dark, 0.95)` on scroll past hero
- Project cards: `transform: translateY(30px)` → `translateY(0)` + `opacity: 0` → `1` on entry
- **Smooth scroll** behavior on all anchor links

### 1.5 Responsive Breakpoints
```
Desktop  ≥ 1024px  — full sidebar + navbar, 2–3 col grids
Tablet   768–1023px — sidebar hidden, hamburger menu
Mobile   < 768px   — stacked single-col layout, hamburger menu
```

---

## 2. COLOR PALETTE — LinkedIn Blue Theme

Replace Hamza's green/teal accent with **LinkedIn Blue**. Apply consistently to all accents, borders, highlights, skill bars, counters, tags, links, and CTAs.

```css
:root {
  /* ── Core Background ── */
  --bg-primary:    #0a0f1e;   /* deepest dark navy */
  --bg-secondary:  #0d1428;   /* dark navy sections */
  --bg-card:       #111c35;   /* card backgrounds */
  --bg-code:       #0d1117;   /* code block / terminal */

  /* ── LinkedIn Blue Accent Scale ── */
  --accent-primary:  #0077b5;  /* LinkedIn signature blue */
  --accent-hover:    #0a66c2;  /* slightly brighter on hover */
  --accent-light:    #00a0dc;  /* lighter blue for glows / tags */
  --accent-glow:     rgba(0, 119, 181, 0.20);  /* glow / shadow */
  --accent-border:   rgba(0, 119, 181, 0.35);  /* subtle border */

  /* ── Text ── */
  --text-primary:   #e8edf5;   /* main body text */
  --text-secondary: #8892a4;   /* muted / metadata */
  --text-muted:     #4a5568;   /* very muted */
  --text-accent:    #00a0dc;   /* highlighted / code text */

  /* ── Monogram / Logo ── */
  --logo-color:     #0077b5;

  /* ── Navbar ── */
  --nav-bg:         rgba(10, 15, 30, 0.95);
  --nav-border:     rgba(0, 119, 181, 0.15);

  /* ── Section Divider Numbers ── */
  --section-num-color: rgba(0, 119, 181, 0.12);  /* large ghost numbers */

  /* ── Skill Bar ── */
  --skill-bar-bg:   rgba(0, 119, 181, 0.12);
  --skill-bar-fill: linear-gradient(90deg, #0077b5, #00a0dc);

  /* ── Featured Badge ── */
  --featured-badge: #0077b5;
  --featured-border: rgba(0, 119, 181, 0.50);

  /* ── Buttons ── */
  --btn-primary-bg:    transparent;
  --btn-primary-text:  #0077b5;
  --btn-primary-border:#0077b5;
  --btn-primary-hover-bg: rgba(0, 119, 181, 0.12);

  --btn-cta-bg:    #0077b5;
  --btn-cta-text:  #ffffff;
  --btn-cta-hover: #0a66c2;
}
```

---

## 3. TYPOGRAPHY

```css
/* Import in <head> */
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500&family=Inter:wght@300;400;500;600;700&display=swap');

:root {
  --font-primary: 'Inter', sans-serif;       /* body, headings */
  --font-mono:    'Fira Code', monospace;    /* code block, monogram, tags */
}

/* Scale */
--fs-hero-name:   clamp(2.5rem, 6vw, 4.5rem);
--fs-hero-role:   clamp(1.2rem, 2.5vw, 1.8rem);
--fs-section-num: clamp(6rem, 15vw, 12rem);   /* ghost background number */
--fs-section-title: clamp(1.6rem, 3vw, 2.2rem);
--fs-card-title:  1.1rem;
--fs-body:        0.95rem;
--fs-small:       0.82rem;
--fs-tag:         0.72rem;
--font-mono-size: 0.85rem;
```

---

## 4. COMPLETE PERSONAL DATA — ZAHRAOUI ZAKARIA

### 4.1 Identity & Hero

```
Full Name:    Zahraoui Zakaria
Monogram:     <ZZ/>
Role (typed): Ingénieur Logiciel & IA  [cycle through these with typing effect]
              Entrepreneur & Fondateur de Startups
              Étudiant GI3 — ENSAO

Location:     Oujda, Maroc (actuellement à Témara, Rabat)
Email:        [use placeholder: zakaria.zahraoui@etu.uae.ac.ma — update as needed]
GitHub:       https://github.com/zakaria-zahraoui    [update if known]
LinkedIn:     https://www.linkedin.com/in/zahraoui-zakaria
```

**Hero intro text (left column):**
```
Bonjour, je suis
```
**Name:** `Zahraoui Zakaria`

**Subtitle (typed cycling):**
`Ingénieur Logiciel & IA`

**Bio paragraph (below name):**
```
Étudiant ingénieur en 3ème année (GI3) à l'ENSAO, spécialité IA & Génie Logiciel.
Fondateur de startups FinTech et MarketTech, je construis des solutions d'intelligence
artificielle pour le marché marocain — de l'idée au MVP, du hackathon à la levée de fonds.
```

**CTA Buttons:**
- `[Voir mes projets]` → `#projects`
- `[Me contacter]` → `#contact`

**Hero code block (right column) — Python:**
```python
# zakaria.py
class IngenieurIA:
    def __init__(self):
        self.name = "Zahraoui Zakaria"
        self.role = "Ingénieur IA & Fondateur"
        self.stack = [
            "Python", "React", "Flutter",
            "scikit-learn", "Firebase"
        ]
        self.startups = ["Fin IA", "PORT2REGION IA"]
        self.building = True

    def solve(self, problem):
        return "ai_powered_solution"
```

**Scroll label:** `Scroll`

---

### 4.2 About Section (01)

**Section title:** `01. À propos de moi`

**Paragraph 1:**
```
Passionné par l'**intelligence artificielle** et le **génie logiciel**,
je suis actuellement en 3ème année cycle ingénieur (GI3) à l'**École Nationale
des Sciences Appliquées d'Oujda (ENSAO)**, spécialité IA & Software Engineering.
```

**Paragraph 2:**
```
Mon parcours m'a permis de maîtriser le **Machine Learning**, le développement
**Full-Stack** et le **Product Management** appliqué aux startups technologiques.
J'ai fondé **Fin IA**, une plateforme FinTech AI-powered pour startups marocaines,
et **PORT2REGION IA**, une solution ML de matching entre PME régionales et
opportunités de marchés du Port Nador Med — lauréate du Prix Créativité & Innovation
au **Hackathon Ramadan IA 2025**.
```

**Paragraph 3:**
```
Je recherche un **stage d'observation/initiation** pour l'été 2026 dans l'axe
Casablanca–Rabat, dans une entreprise tech (Oracle, Capgemini, IBM, Atos, CGI ou équivalent).
```

**Stat Counters (animated count-up):**
```
3       → Années de formation ingénieur
2       → Startups fondées
5+      → Projets réalisés
1       → Prix hackathon remporté
```

---

### 4.3 Experience Section (02)

**Section title:** `02. Expérience professionnelle`

**No formal internships yet — use this card structure instead:**

#### Card 1 — Active (In Progress)
```
Title:    Co-Fondateur & Lead Développeur — Fin IA
Company:  Startup Personnelle
Period:   Janv. 2025 – Présent
Badge:    [En cours]

Bullets:
• Conception d'une plateforme FinTech AI-powered ciblant les startups et scale-ups marocains
• Développement du MVP : scoring financier automatisé, dashboard analytique, intégration LLM
• Préparation d'un dossier de levée de fonds Seed et pitch deck pour investisseurs
• Recherche de résidence startup (StartGate UM6P) et d'accélérateurs marocains

Tags:  Python  React  scikit-learn  Firebase  LLM  FinTech
```

#### Card 2 — Completed
```
Title:    Co-Fondateur — PORT2REGION IA (P2R)
Company:  Projet Hackathon → Startup
Period:   Mars 2025 – Présent
Badge:    [Prix Créativité & Innovation]

Bullets:
• Conception d'une plateforme ML de matching entre PME régionales et marchés du Port Nador Med
• Développement d'un algorithme de scoring ML pour l'éligibilité aux marchés publics
• Remporté le Prix Créativité & Innovation au Hackathon Ramadan IA 2025
• Dossier de candidature soumis pour la résidence StartGate — UM6P, Ben Guerir

Tags:  Python  scikit-learn  Machine Learning  React  API REST
```

#### Card 3 — Student Activity
```
Title:    Membre Actif — Enactus ENSAO & Club GI ENSAO
Company:  ENSAO — Oujda
Period:   2022 – Présent

Bullets:
• Participation à des projets d'entrepreneuriat social et des compétitions nationales Enactus
• Organisation et participation à des hackathons, workshops et événements tech
• Co-animation d'ateliers de développement logiciel et de sensibilisation à l'IA

Tags:  Entrepreneuriat  Leadership  Travail d'équipe
```

---

### 4.4 Skills Section (03)

**Section title:** `03. Compétences`

#### Subsection A — Programmation & Dev
```
Python         90%
JavaScript     80%
PHP            70%
Dart/Flutter   75%
SQL            80%
C              65%
```

#### Subsection B — Intelligence Artificielle
```
[Badge pills — no bar, just chip tags]
Machine Learning    Deep Learning      scikit-learn
LLM / Prompt Eng.  NLP                Supervised ML
Andrew Ng ML Cert. Feature Engineering Regression / Classification
```

#### Subsection C — Frameworks & Outils
```
React    Firebase    Flask    Node.js    MySQL
Git      Figma       FlutterFlow        n8n / MCP
Obsidian Linux       Jupyter  Pandas     NumPy
```

#### Subsection D — Méthodologies & Soft Skills
```
Agile / Scrum    Product Management    Pitch & Fundraising
Entrepreneuriat  Esprit analytique     Communication
Leadership       Autonomie             Veille technologique
```

---

### 4.5 Projects Section (04)

**Section title:** `04. Projets`

#### Project 1 — FEATURED (large card)
```
Badge:       Featured
Status:      En cours
Title:       Fin IA — Plateforme FinTech AI-Powered
Description:
  Plateforme d'intelligence financière destinée aux startups et scale-ups marocains.
  Intègre un scoring financier automatisé via ML, un dashboard analytique en temps réel
  et une interface de simulation de levée de fonds. MVP en phase de pre-revenue,
  préparation d'un Seed round.

Tags:  Python  React  scikit-learn  Firebase  LLM  FinTech  API REST
Links: [GitHub] [En savoir plus]
```

#### Project 2 — FEATURED (large card)
```
Badge:       Featured — 🏆 Prix Créativité & Innovation
Title:       PORT2REGION IA (P2R)
Description:
  Plateforme ML de matching entre PME de la région Oriental et les opportunités
  de marchés de fourniture du Port Nador Med. Algorithme de scoring d'éligibilité,
  module de recommandation, et interface de suivi des appels d'offres.
  Lauréat Hackathon Ramadan IA 2025.

Tags:  Python  scikit-learn  Machine Learning  React  API REST  MarketTech
Links: [GitHub]
```

#### Project 3 — Standard card
```
Title:       Artouris (ex-RIADI)
Description:
  Plateforme de tourisme et artisanat marocain. Prototype Figma, MVP FlutterFlow,
  étude de marché terrain à Oujda. Participation au bootcamp Enactus / Tamwilcom
  InnovInvest pour la première mise en marché.

Tags:  Flutter  FlutterFlow  Figma  Firebase  Tourisme  MobileApp
Links: [GitHub]
```

#### Project 4 — Standard card
```
Title:       Seismo Safe
Description:
  Application mobile d'alerte sismique développée dans le cadre du NASA Space Apps
  Challenge 2023. Détection et notification en temps réel des événements sismiques.

Tags:  Flutter  API  NASA  Mobile  Alerting
Links: [GitHub]
```

#### Project 5 — Standard card
```
Title:       Portfolio Personnel v2
Description:
  Portfolio web personnel (ce site). Développé en HTML/CSS/JS vanilla,
  hébergé sur Netlify. Design dark brutalist, animations au scroll.

Tags:  HTML  CSS  JavaScript  Netlify  Dark Theme
Links: [GitHub] [Live]
```

---

### 4.6 Certifications Section (05)

**Section title:** `05. Certifications`

```
Issuer:   DeepLearning.AI / Coursera
Title:    Supervised Machine Learning: Regression & Classification
Date:     2024
Tags:     Machine Learning  Supervised  Andrew Ng
Link:     https://www.coursera.org/account/accomplishments/verify/[CERT_ID]

---

Issuer:   DeepLearning.AI / Coursera
Title:    Spécialisation Machine Learning — Andrew Ng
Date:     2024
Tags:     ML  Unsupervised  Reinforcement  Coursera
Link:     https://www.coursera.org/account/accomplishments/specialization/[CERT_ID]

---

Issuer:   ENSAO / Formations académiques
Title:    Génie Informatique — Spécialité IA & Software Engineering
Date:     2022 – Présent (GI3)
Tags:     Computer Engineering  AI  Software Engineering

---

Issuer:   NASA / Space Apps Challenge
Title:    Participation — NASA Space Apps Challenge 2023
Date:     Oct. 2023
Tags:     Hackathon  NASA  Innovation  Mobile

---

Issuer:   Hackathon Ramadan IA 2025
Title:    Prix Créativité & Innovation — PORT2REGION IA
Date:     2025
Tags:     Prix  Hackathon  IA  Innovation  Maroc
```

> **Note to Antigraphity:** Populate certification links once Zakaria provides exact Coursera certificate URLs. Use `#` as placeholder href for now.

---

### 4.7 Education Section (06)

**Section title:** `06. Formation`

#### Timeline Entry 1 (current)
```
Period:      2022 – Présent
Title:       Cycle Ingénieur en Génie Informatique (GI3)
Subtitle:    Spécialité : Intelligence Artificielle & Génie Logiciel
Institution: École Nationale des Sciences Appliquées d'Oujda (ENSAO)
Location:    Oujda, Maroc
Badge:       [En cours]
```

#### Timeline Entry 2
```
Period:      2020 – 2022
Title:       Classes Préparatoires — MPSI / MP
Institution: [Nom à confirmer ou supprimer si non applicable]
Location:    Maroc
```

#### Languages subsection
```
AR  Arabe     Langue maternelle
FR  Français  Courant
EN  Anglais   Intermédiaire (en progression)
```

---

### 4.8 Contact Section (07)

**Section title:** `07. Contact`

**Headline:** `Travaillons ensemble !`

**Body text:**
```
Je suis actuellement à la recherche d'un stage d'observation/initiation
pour l'été 2026 dans l'axe Casablanca–Rabat. Fondateur actif de deux startups IA,
je suis ouvert à toute collaboration, opportunité ou discussion stratégique.
N'hésitez pas à me contacter !
```

**Contact info list:**
```
📧  zakaria.zahraoui@etu.uae.ac.ma     (update with real email)
🔗  linkedin.com/in/zahraoui-zakaria
💻  github.com/zakaria-zahraoui         (update if different)
📍  Oujda / Témara–Rabat, Maroc
```

**CTA Button:** `[Envoyer un message]` → `mailto:zakaria.zahraoui@etu.uae.ac.ma`

---

## 5. HTML STRUCTURE BLUEPRINT

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Zahraoui Zakaria | Ingénieur IA & Fondateur</title>

  <!-- SEO Meta -->
  <meta name="description" content="Portfolio de Zahraoui Zakaria — Ingénieur Logiciel & IA, ENSAO GI3, fondateur de Fin IA et PORT2REGION IA." />
  <meta property="og:title" content="Zahraoui Zakaria | Ingénieur IA & Fondateur" />
  <meta property="og:type" content="website" />

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />

  <!-- Icons (Lucide or Feather via CDN) -->
  <script src="https://unpkg.com/lucide@latest/dist/umd/lucide.js"></script>

  <style>/* ALL CSS INLINE HERE */</style>
</head>

<body>

  <!-- ════════════════════════════════════════════
       NAVBAR
  ════════════════════════════════════════════ -->
  <nav id="navbar">
    <a href="#hero" class="nav-logo">&lt;ZZ/&gt;</a>
    <ul class="nav-links">
      <li><a href="#about">À propos</a></li>
      <li><a href="#experience">Expérience</a></li>
      <li><a href="#skills">Compétences</a></li>
      <li><a href="#projects">Projets</a></li>
      <li><a href="#certifications">Certifications</a></li>
      <li><a href="#education">Formation</a></li>
      <li><a href="#contact" class="nav-cta">Contact</a></li>
    </ul>
    <button class="hamburger" aria-label="Menu">
      <span></span><span></span><span></span>
    </button>
  </nav>

  <!-- Mobile Menu Overlay -->
  <div class="mobile-menu" id="mobileMenu">
    <ul>
      <li><a href="#about">À propos</a></li>
      <li><a href="#experience">Expérience</a></li>
      <li><a href="#skills">Compétences</a></li>
      <li><a href="#projects">Projets</a></li>
      <li><a href="#certifications">Certifications</a></li>
      <li><a href="#education">Formation</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </div>

  <!-- ════════════════════════════════════════════
       SIDEBAR (desktop only)
  ════════════════════════════════════════════ -->
  <aside class="sidebar">
    <div class="sidebar-line"></div>
    <div class="social-links">
      <a href="https://github.com/zakaria-zahraoui" target="_blank" rel="noopener" aria-label="GitHub">
        <i data-lucide="github"></i>
      </a>
      <a href="https://www.linkedin.com/in/zahraoui-zakaria" target="_blank" rel="noopener" aria-label="LinkedIn">
        <i data-lucide="linkedin"></i>
      </a>
      <a href="mailto:zakaria.zahraoui@etu.uae.ac.ma" aria-label="Email">
        <i data-lucide="mail"></i>
      </a>
    </div>
    <div class="sidebar-line"></div>
    <span class="sidebar-email">zakaria.zahraoui@etu.uae.ac.ma</span>
  </aside>

  <!-- ════════════════════════════════════════════
       HERO — SECTION 0
  ════════════════════════════════════════════ -->
  <section id="hero">
    <div class="hero-content">
      <div class="hero-left">
        <p class="hero-greeting">Bonjour, je suis</p>
        <h1 class="hero-name">Zahraoui Zakaria</h1>
        <h2 class="hero-role">
          <span class="typed-text" id="typedText"></span>
          <span class="cursor">|</span>
        </h2>
        <p class="hero-bio">
          Étudiant ingénieur en 3ème année (GI3) à l'ENSAO, spécialité IA & Génie Logiciel.
          Fondateur de startups FinTech et MarketTech, je construis des solutions d'intelligence
          artificielle pour le marché marocain — de l'idée au MVP, du hackathon à la levée de fonds.
        </p>
        <div class="hero-ctas">
          <a href="#projects" class="btn btn-primary">Voir mes projets</a>
          <a href="#contact" class="btn btn-outline">Me contacter</a>
        </div>
        <div class="hero-socials">
          <a href="https://github.com/zakaria-zahraoui" target="_blank" rel="noopener">
            <i data-lucide="github"></i>
          </a>
          <a href="https://www.linkedin.com/in/zahraoui-zakaria" target="_blank" rel="noopener">
            <i data-lucide="linkedin"></i>
          </a>
          <a href="mailto:zakaria.zahraoui@etu.uae.ac.ma">
            <i data-lucide="mail"></i>
          </a>
        </div>
      </div>

      <div class="hero-right">
        <div class="code-block">
          <div class="code-header">
            <span class="dot red"></span>
            <span class="dot yellow"></span>
            <span class="dot green"></span>
            <span class="code-filename">zakaria.py</span>
          </div>
          <pre class="code-body"><code id="codeContent"></code></pre>
        </div>
      </div>
    </div>

    <div class="scroll-indicator">
      <span>Scroll</span>
      <div class="scroll-line"></div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       ABOUT — SECTION 01
  ════════════════════════════════════════════ -->
  <section id="about" class="section">
    <div class="section-number">01</div>
    <div class="container">
      <h2 class="section-title">À propos de moi</h2>

      <div class="about-grid">
        <div class="about-text">
          <p>
            Passionné par l'<strong>intelligence artificielle</strong> et le <strong>génie logiciel</strong>,
            je suis actuellement en 3ème année cycle ingénieur (GI3) à l'<strong>École Nationale
            des Sciences Appliquées d'Oujda (ENSAO)</strong>, spécialité IA & Software Engineering.
          </p>
          <p>
            Mon parcours m'a permis de maîtriser le <strong>Machine Learning</strong>, le développement
            <strong>Full-Stack</strong> et le <strong>Product Management</strong> appliqué aux startups technologiques.
            J'ai fondé <strong>Fin IA</strong>, une plateforme FinTech AI-powered pour startups marocaines,
            et <strong>PORT2REGION IA</strong>, lauréate du Prix Créativité & Innovation au
            <strong>Hackathon Ramadan IA 2025</strong>.
          </p>
          <p>
            Je recherche un <strong>stage d'observation/initiation</strong> pour l'été 2026 dans l'axe
            Casablanca–Rabat, dans une entreprise tech (Oracle, Capgemini, IBM, Atos, CGI ou équivalent).
          </p>
        </div>

        <div class="about-stats">
          <!-- Each stat: counter + label -->
          <div class="stat-item">
            <span class="stat-number" data-target="3">0</span>
            <span class="stat-label">Années de formation ingénieur</span>
          </div>
          <div class="stat-item">
            <span class="stat-number" data-target="2">0</span>
            <span class="stat-label">Startups fondées</span>
          </div>
          <div class="stat-item">
            <span class="stat-number" data-target="5">0</span>
            <span class="stat-label">Projets réalisés</span>
          </div>
          <div class="stat-item">
            <span class="stat-number" data-target="1">0</span>
            <span class="stat-label">Prix hackathon remporté</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       EXPERIENCE — SECTION 02
  ════════════════════════════════════════════ -->
  <section id="experience" class="section">
    <div class="section-number">02</div>
    <div class="container">
      <h2 class="section-title">Expérience professionnelle</h2>

      <div class="experience-list">

        <!-- Experience Card Component:
             .exp-card
               .exp-header
                 .exp-badge (optional: "En cours" | "Prix X")
                 .exp-title
                 .exp-company
                 .exp-period
               .exp-bullets (ul > li)
               .exp-tags (.tag × N)
        -->

        <!-- Card 1: Fin IA -->
        <div class="exp-card exp-featured">
          <div class="exp-header">
            <span class="exp-status-badge badge-active">En cours</span>
            <h3 class="exp-title">Co-Fondateur & Lead Développeur — Fin IA</h3>
            <p class="exp-company">Startup Personnelle</p>
            <p class="exp-period">Janv. 2025 – Présent</p>
          </div>
          <ul class="exp-bullets">
            <li>Conception d'une plateforme FinTech AI-powered ciblant les startups et scale-ups marocains</li>
            <li>Développement du MVP : scoring financier automatisé, dashboard analytique, intégration LLM</li>
            <li>Préparation d'un dossier de levée de fonds Seed et pitch deck pour investisseurs</li>
            <li>Recherche de résidence startup (StartGate UM6P) et d'accélérateurs marocains</li>
          </ul>
          <div class="exp-tags">
            <span class="tag">Python</span>
            <span class="tag">React</span>
            <span class="tag">scikit-learn</span>
            <span class="tag">Firebase</span>
            <span class="tag">LLM</span>
            <span class="tag">FinTech</span>
          </div>
        </div>

        <!-- Card 2: PORT2REGION IA -->
        <div class="exp-card">
          <div class="exp-header">
            <span class="exp-status-badge badge-award">🏆 Prix Créativité & Innovation</span>
            <h3 class="exp-title">Co-Fondateur — PORT2REGION IA (P2R)</h3>
            <p class="exp-company">Projet Hackathon → Startup</p>
            <p class="exp-period">Mars 2025 – Présent</p>
          </div>
          <ul class="exp-bullets">
            <li>Conception d'une plateforme ML de matching entre PME régionales et marchés du Port Nador Med</li>
            <li>Développement d'un algorithme de scoring ML pour l'éligibilité aux marchés publics</li>
            <li>Remporté le Prix Créativité & Innovation au Hackathon Ramadan IA 2025</li>
            <li>Dossier de candidature soumis pour la résidence StartGate — UM6P, Ben Guerir</li>
          </ul>
          <div class="exp-tags">
            <span class="tag">Python</span>
            <span class="tag">scikit-learn</span>
            <span class="tag">Machine Learning</span>
            <span class="tag">React</span>
            <span class="tag">API REST</span>
          </div>
        </div>

        <!-- Card 3: Enactus -->
        <div class="exp-card">
          <div class="exp-header">
            <h3 class="exp-title">Membre Actif — Enactus ENSAO & Club GI ENSAO</h3>
            <p class="exp-company">ENSAO — Oujda</p>
            <p class="exp-period">2022 – Présent</p>
          </div>
          <ul class="exp-bullets">
            <li>Participation à des projets d'entrepreneuriat social et des compétitions nationales Enactus</li>
            <li>Organisation et participation à des hackathons, workshops et événements tech</li>
            <li>Co-animation d'ateliers de développement logiciel et de sensibilisation à l'IA</li>
          </ul>
          <div class="exp-tags">
            <span class="tag">Entrepreneuriat</span>
            <span class="tag">Leadership</span>
            <span class="tag">Travail d'équipe</span>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       SKILLS — SECTION 03
  ════════════════════════════════════════════ -->
  <section id="skills" class="section">
    <div class="section-number">03</div>
    <div class="container">
      <h2 class="section-title">Compétences</h2>

      <div class="skills-grid">

        <!-- Subsection: Programmation & Dev (progress bars) -->
        <div class="skills-group">
          <h3 class="skills-group-title">Programmation & Développement</h3>
          <div class="skill-bars">
            <!-- .skill-bar-item > .skill-info (name + %) + .bar > .fill[data-width="90"] -->
            <div class="skill-bar-item">
              <div class="skill-info"><span>Python</span><span>90%</span></div>
              <div class="bar"><div class="fill" data-width="90"></div></div>
            </div>
            <div class="skill-bar-item">
              <div class="skill-info"><span>JavaScript</span><span>80%</span></div>
              <div class="bar"><div class="fill" data-width="80"></div></div>
            </div>
            <div class="skill-bar-item">
              <div class="skill-info"><span>Dart / Flutter</span><span>75%</span></div>
              <div class="bar"><div class="fill" data-width="75"></div></div>
            </div>
            <div class="skill-bar-item">
              <div class="skill-info"><span>SQL</span><span>80%</span></div>
              <div class="bar"><div class="fill" data-width="80"></div></div>
            </div>
            <div class="skill-bar-item">
              <div class="skill-info"><span>PHP</span><span>70%</span></div>
              <div class="bar"><div class="fill" data-width="70"></div></div>
            </div>
            <div class="skill-bar-item">
              <div class="skill-info"><span>C</span><span>65%</span></div>
              <div class="bar"><div class="fill" data-width="65"></div></div>
            </div>
          </div>
        </div>

        <!-- Subsection: IA (badge pills) -->
        <div class="skills-group">
          <h3 class="skills-group-title">Intelligence Artificielle</h3>
          <div class="skill-pills">
            <span class="pill">Machine Learning</span>
            <span class="pill">scikit-learn</span>
            <span class="pill">Supervised ML</span>
            <span class="pill">Unsupervised ML</span>
            <span class="pill">Feature Engineering</span>
            <span class="pill">LLM / Prompt Engineering</span>
            <span class="pill">NLP</span>
            <span class="pill">Pandas / NumPy</span>
            <span class="pill">Jupyter</span>
            <span class="pill">Andrew Ng Certification</span>
          </div>
        </div>

        <!-- Subsection: Frameworks (badge pills) -->
        <div class="skills-group">
          <h3 class="skills-group-title">Frameworks & Outils</h3>
          <div class="skill-pills">
            <span class="pill">React</span>
            <span class="pill">Firebase</span>
            <span class="pill">Flask</span>
            <span class="pill">MySQL</span>
            <span class="pill">Git / GitHub</span>
            <span class="pill">Figma</span>
            <span class="pill">FlutterFlow</span>
            <span class="pill">n8n / MCP</span>
            <span class="pill">Linux</span>
            <span class="pill">Obsidian</span>
          </div>
        </div>

        <!-- Subsection: Soft Skills (badge pills) -->
        <div class="skills-group">
          <h3 class="skills-group-title">Méthodologies & Soft Skills</h3>
          <div class="skill-pills">
            <span class="pill">Agile / Scrum</span>
            <span class="pill">Product Management</span>
            <span class="pill">Pitch & Fundraising</span>
            <span class="pill">Entrepreneuriat</span>
            <span class="pill">Esprit analytique</span>
            <span class="pill">Leadership</span>
            <span class="pill">Communication</span>
            <span class="pill">Veille technologique</span>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       PROJECTS — SECTION 04
  ════════════════════════════════════════════ -->
  <section id="projects" class="section">
    <div class="section-number">04</div>
    <div class="container">
      <h2 class="section-title">Projets</h2>

      <div class="projects-grid">

        <!-- FEATURED PROJECT CARD (larger, spanning 2 cols on desktop) -->
        <div class="project-card project-featured">
          <div class="project-header">
            <span class="project-badge">Featured</span>
            <span class="project-status status-progress">En cours</span>
          </div>
          <h3 class="project-title">Fin IA — Plateforme FinTech AI-Powered</h3>
          <p class="project-desc">
            Plateforme d'intelligence financière destinée aux startups et scale-ups marocains.
            Intègre un scoring financier automatisé via ML, un dashboard analytique en temps réel
            et une interface de simulation de levée de fonds. MVP en phase de pre-revenue,
            préparation d'un Seed round.
          </p>
          <div class="project-tags">
            <span class="tag">Python</span><span class="tag">React</span>
            <span class="tag">scikit-learn</span><span class="tag">Firebase</span>
            <span class="tag">LLM</span><span class="tag">FinTech</span>
          </div>
          <div class="project-links">
            <a href="#" class="proj-link"><i data-lucide="github"></i> GitHub</a>
          </div>
        </div>

        <!-- FEATURED PROJECT CARD 2 -->
        <div class="project-card project-featured">
          <div class="project-header">
            <span class="project-badge">Featured</span>
            <span class="project-status status-award">🏆 Prix Créativité & Innovation</span>
          </div>
          <h3 class="project-title">PORT2REGION IA (P2R)</h3>
          <p class="project-desc">
            Plateforme ML de matching entre PME de la région Oriental et les opportunités
            de marchés du Port Nador Med. Algorithme de scoring d'éligibilité, module de
            recommandation, et interface de suivi des appels d'offres. Lauréat Hackathon Ramadan IA 2025.
          </p>
          <div class="project-tags">
            <span class="tag">Python</span><span class="tag">scikit-learn</span>
            <span class="tag">Machine Learning</span><span class="tag">React</span>
            <span class="tag">API REST</span>
          </div>
          <div class="project-links">
            <a href="#" class="proj-link"><i data-lucide="github"></i> GitHub</a>
          </div>
        </div>

        <!-- STANDARD PROJECT CARDS -->
        <div class="project-card">
          <h3 class="project-title">Artouris (ex-RIADI)</h3>
          <p class="project-desc">
            Plateforme de tourisme et artisanat marocain. Prototype Figma, MVP FlutterFlow,
            étude de marché terrain à Oujda. Participation bootcamp Enactus / Tamwilcom InnovInvest.
          </p>
          <div class="project-tags">
            <span class="tag">Flutter</span><span class="tag">FlutterFlow</span>
            <span class="tag">Figma</span><span class="tag">Firebase</span>
          </div>
          <div class="project-links">
            <a href="#" class="proj-link"><i data-lucide="github"></i> GitHub</a>
          </div>
        </div>

        <div class="project-card">
          <h3 class="project-title">Seismo Safe</h3>
          <p class="project-desc">
            Application mobile d'alerte sismique — NASA Space Apps Challenge 2023.
            Détection et notification en temps réel des événements sismiques.
          </p>
          <div class="project-tags">
            <span class="tag">Flutter</span><span class="tag">API</span>
            <span class="tag">NASA</span><span class="tag">Mobile</span>
          </div>
          <div class="project-links">
            <a href="#" class="proj-link"><i data-lucide="github"></i> GitHub</a>
          </div>
        </div>

        <div class="project-card">
          <h3 class="project-title">Portfolio Personnel</h3>
          <p class="project-desc">
            Portfolio web développé en HTML/CSS/JS vanilla, hébergé sur Netlify.
            Design dark, animations au scroll, responsive.
          </p>
          <div class="project-tags">
            <span class="tag">HTML</span><span class="tag">CSS</span>
            <span class="tag">JavaScript</span><span class="tag">Netlify</span>
          </div>
          <div class="project-links">
            <a href="#" class="proj-link"><i data-lucide="github"></i> GitHub</a>
            <a href="https://cerulean-boba-7e7d22.netlify.app/" target="_blank" class="proj-link">
              <i data-lucide="external-link"></i> Live
            </a>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       CERTIFICATIONS — SECTION 05
  ════════════════════════════════════════════ -->
  <section id="certifications" class="section">
    <div class="section-number">05</div>
    <div class="container">
      <h2 class="section-title">Certifications</h2>

      <div class="certs-grid">

        <!-- Cert Card Component:
             .cert-card
               .cert-issuer (issuer name, small, accent)
               .cert-title (bold)
               .cert-date
               .cert-tags
               .cert-link (optional)
        -->

        <div class="cert-card">
          <p class="cert-issuer">DeepLearning.AI / Coursera</p>
          <h3 class="cert-title">Supervised ML: Regression & Classification</h3>
          <p class="cert-date">2024</p>
          <div class="cert-tags">
            <span class="tag">Machine Learning</span>
            <span class="tag">Supervised</span>
            <span class="tag">Andrew Ng</span>
          </div>
          <a href="#" class="cert-link" target="_blank">
            <i data-lucide="external-link"></i> Voir le certificat
          </a>
        </div>

        <div class="cert-card">
          <p class="cert-issuer">DeepLearning.AI / Coursera</p>
          <h3 class="cert-title">Spécialisation Machine Learning</h3>
          <p class="cert-date">2024</p>
          <div class="cert-tags">
            <span class="tag">ML</span>
            <span class="tag">Unsupervised</span>
            <span class="tag">Reinforcement</span>
          </div>
          <a href="#" class="cert-link" target="_blank">
            <i data-lucide="external-link"></i> Voir le certificat
          </a>
        </div>

        <div class="cert-card cert-award">
          <p class="cert-issuer">Hackathon Ramadan IA 2025</p>
          <h3 class="cert-title">🏆 Prix Créativité & Innovation — PORT2REGION IA</h3>
          <p class="cert-date">2025</p>
          <div class="cert-tags">
            <span class="tag">Prix</span>
            <span class="tag">Hackathon</span>
            <span class="tag">IA</span>
            <span class="tag">Innovation</span>
          </div>
        </div>

        <div class="cert-card">
          <p class="cert-issuer">NASA / Space Apps Challenge</p>
          <h3 class="cert-title">Participation — NASA Space Apps Challenge</h3>
          <p class="cert-date">Oct. 2023</p>
          <div class="cert-tags">
            <span class="tag">Hackathon</span>
            <span class="tag">NASA</span>
            <span class="tag">Innovation</span>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       EDUCATION — SECTION 06
  ════════════════════════════════════════════ -->
  <section id="education" class="section">
    <div class="section-number">06</div>
    <div class="container">
      <h2 class="section-title">Formation</h2>

      <div class="education-layout">
        <div class="timeline">

          <!-- Timeline Item Component:
               .timeline-item
                 .timeline-dot
                 .timeline-content
                   .timeline-period
                   .timeline-title
                   .timeline-subtitle
                   .timeline-institution + location
                   .timeline-badge (optional)
          -->

          <div class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-content">
              <span class="timeline-period">2022 – Présent</span>
              <h3 class="timeline-title">Cycle Ingénieur en Génie Informatique (GI3)</h3>
              <p class="timeline-subtitle">Spécialité : Intelligence Artificielle & Génie Logiciel</p>
              <p class="timeline-institution">École Nationale des Sciences Appliquées d'Oujda (ENSAO)</p>
              <p class="timeline-location">Oujda, Maroc</p>
              <span class="timeline-badge badge-active">En cours</span>
            </div>
          </div>

        </div>

        <!-- Languages -->
        <div class="languages">
          <h3 class="languages-title">Langues</h3>
          <div class="lang-grid">
            <div class="lang-item">
              <span class="lang-code">AR</span>
              <div class="lang-info">
                <strong>Arabe</strong>
                <span>Langue maternelle</span>
              </div>
            </div>
            <div class="lang-item">
              <span class="lang-code">FR</span>
              <div class="lang-info">
                <strong>Français</strong>
                <span>Courant</span>
              </div>
            </div>
            <div class="lang-item">
              <span class="lang-code">EN</span>
              <div class="lang-info">
                <strong>Anglais</strong>
                <span>Intermédiaire (en progression)</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       CONTACT — SECTION 07
  ════════════════════════════════════════════ -->
  <section id="contact" class="section">
    <div class="section-number">07</div>
    <div class="container">
      <h2 class="section-title">Contact</h2>

      <div class="contact-layout">
        <div class="contact-left">
          <h3 class="contact-headline">Travaillons ensemble !</h3>
          <p class="contact-text">
            Je suis actuellement à la recherche d'un stage d'observation/initiation
            pour l'été 2026 dans l'axe Casablanca–Rabat. Fondateur actif de deux startups IA,
            je suis ouvert à toute collaboration, opportunité ou discussion stratégique.
            N'hésitez pas à me contacter !
          </p>
          <ul class="contact-info">
            <li>
              <i data-lucide="mail"></i>
              <a href="mailto:zakaria.zahraoui@etu.uae.ac.ma">zakaria.zahraoui@etu.uae.ac.ma</a>
            </li>
            <li>
              <i data-lucide="linkedin"></i>
              <a href="https://www.linkedin.com/in/zahraoui-zakaria" target="_blank">
                linkedin.com/in/zahraoui-zakaria
              </a>
            </li>
            <li>
              <i data-lucide="github"></i>
              <a href="https://github.com/zakaria-zahraoui" target="_blank">
                github.com/zakaria-zahraoui
              </a>
            </li>
            <li>
              <i data-lucide="map-pin"></i>
              <span>Oujda / Témara–Rabat, Maroc</span>
            </li>
          </ul>
        </div>
        <div class="contact-right">
          <a href="mailto:zakaria.zahraoui@etu.uae.ac.ma" class="btn btn-cta btn-large">
            Envoyer un message
          </a>
        </div>
      </div>
    </div>
  </section>

  <!-- ════════════════════════════════════════════
       FOOTER
  ════════════════════════════════════════════ -->
  <footer>
    <p>Conçu & développé par <strong>Zahraoui Zakaria</strong></p>
    <div class="footer-socials">
      <a href="https://github.com/zakaria-zahraoui" target="_blank" rel="noopener">
        <i data-lucide="github"></i>
      </a>
      <a href="https://www.linkedin.com/in/zahraoui-zakaria" target="_blank" rel="noopener">
        <i data-lucide="linkedin"></i>
      </a>
    </div>
  </footer>

  <script>/* ALL JS INLINE HERE */</script>
</body>
</html>
```

---

## 6. CSS ARCHITECTURE — KEY RULES

### 6.1 Reset & Base
```css
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  background: var(--bg-primary);
  color: var(--text-primary);
  font-family: var(--font-primary);
  font-size: 16px;
  line-height: 1.6;
  overflow-x: hidden;
}
```

### 6.2 Navbar
```css
#navbar {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 2rem; height: 70px;
  background: transparent;
  border-bottom: 1px solid transparent;
  transition: background 0.3s, border-color 0.3s;
}
#navbar.scrolled {
  background: var(--nav-bg);
  border-bottom-color: var(--nav-border);
}
.nav-logo {
  font-family: var(--font-mono);
  font-size: 1.4rem;
  color: var(--accent-primary);
  text-decoration: none;
  font-weight: 500;
}
.nav-links { display: flex; gap: 2rem; list-style: none; }
.nav-links a {
  color: var(--text-secondary);
  text-decoration: none;
  font-size: 0.88rem;
  letter-spacing: 0.05em;
  transition: color 0.2s;
  font-family: var(--font-mono);
}
.nav-links a:hover { color: var(--accent-primary); }
.nav-cta {
  color: var(--accent-primary) !important;
  border: 1px solid var(--accent-primary);
  padding: 0.4rem 1rem;
  border-radius: 4px;
  transition: background 0.2s !important;
}
.nav-cta:hover { background: var(--accent-glow) !important; }
```

### 6.3 Section Styling
```css
.section {
  position: relative;
  padding: 6rem 0 4rem;
  min-height: 100vh;
  display: flex;
  align-items: flex-start;
}
.section-number {
  position: absolute;
  top: 2rem; right: 2rem;
  font-size: var(--fs-section-num);
  font-family: var(--font-mono);
  font-weight: 700;
  color: var(--section-num-color);
  user-select: none;
  pointer-events: none;
  line-height: 1;
}
.container {
  width: 100%; max-width: 1100px;
  margin: 0 auto;
  padding: 0 2rem;
}
.section-title {
  font-size: var(--fs-section-title);
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 3rem;
  display: flex; align-items: center; gap: 1rem;
}
.section-title::after {
  content: '';
  flex: 1; max-width: 300px;
  height: 1px;
  background: var(--accent-border);
}
/* Section number prefix in title — use ::before */
.section-title::before {
  content: attr(data-num)'. ';
  font-family: var(--font-mono);
  font-size: 0.9em;
  color: var(--accent-primary);
}
```

### 6.4 Scroll Animations
```css
/* Initial hidden state — applied via JS adding .animate class */
.animate-on-scroll {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.animate-on-scroll.visible {
  opacity: 1;
  transform: translateY(0);
}
/* Stagger children */
.animate-on-scroll:nth-child(2) { transition-delay: 0.1s; }
.animate-on-scroll:nth-child(3) { transition-delay: 0.2s; }
.animate-on-scroll:nth-child(4) { transition-delay: 0.3s; }
```

### 6.5 Skill Bars
```css
.bar {
  height: 6px;
  background: var(--skill-bar-bg);
  border-radius: 3px;
  overflow: hidden;
}
.bar .fill {
  height: 100%;
  width: 0;
  background: var(--skill-bar-fill);
  border-radius: 3px;
  transition: width 1.2s cubic-bezier(0.4, 0, 0.2, 1);
}
/* JS sets: fill.style.width = fill.dataset.width + '%' on intersection */
```

### 6.6 Tags / Pills
```css
.tag {
  display: inline-block;
  padding: 0.25rem 0.7rem;
  border-radius: 4px;
  font-family: var(--font-mono);
  font-size: var(--fs-tag);
  color: var(--accent-light);
  background: var(--accent-glow);
  border: 1px solid var(--accent-border);
  white-space: nowrap;
}
.pill {
  display: inline-block;
  padding: 0.35rem 0.85rem;
  border-radius: 20px;
  font-size: 0.8rem;
  color: var(--text-secondary);
  background: var(--bg-card);
  border: 1px solid rgba(255,255,255,0.08);
  transition: border-color 0.2s, color 0.2s;
}
.pill:hover {
  border-color: var(--accent-primary);
  color: var(--accent-primary);
}
```

### 6.7 Project Cards
```css
.projects-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 1.5rem;
}
.project-card {
  grid-column: span 4;
  background: var(--bg-card);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 8px;
  padding: 1.5rem;
  transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
}
.project-card:hover {
  transform: translateY(-6px);
  border-color: var(--accent-border);
  box-shadow: 0 10px 40px var(--accent-glow);
}
.project-featured {
  grid-column: span 6;
  border-color: var(--accent-border);
  background: linear-gradient(135deg, var(--bg-card), rgba(0,119,181,0.05));
}
.project-badge {
  font-family: var(--font-mono);
  font-size: 0.72rem;
  color: var(--accent-primary);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
```

### 6.8 Sidebar
```css
.sidebar {
  position: fixed;
  left: 2rem; bottom: 0;
  z-index: 100;
  display: flex; flex-direction: column;
  align-items: center; gap: 1rem;
}
.sidebar-line {
  width: 1px; height: 80px;
  background: var(--text-muted);
}
.social-links { display: flex; flex-direction: column; gap: 0.75rem; }
.social-links a { color: var(--text-secondary); transition: color 0.2s; }
.social-links a:hover { color: var(--accent-primary); }
.sidebar-email {
  writing-mode: vertical-rl;
  font-family: var(--font-mono);
  font-size: 0.72rem;
  color: var(--text-secondary);
  letter-spacing: 0.12em;
}
```

### 6.9 Code Block (Hero)
```css
.code-block {
  background: var(--bg-code);
  border: 1px solid rgba(0,119,181,0.25);
  border-radius: 10px;
  overflow: hidden;
  max-width: 480px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.5), 0 0 30px var(--accent-glow);
}
.code-header {
  background: rgba(255,255,255,0.04);
  padding: 0.75rem 1rem;
  display: flex; align-items: center; gap: 0.5rem;
  border-bottom: 1px solid rgba(255,255,255,0.06);
}
.dot { width: 12px; height: 12px; border-radius: 50%; }
.dot.red    { background: #ff5f57; }
.dot.yellow { background: #ffbd2e; }
.dot.green  { background: #28ca41; }
.code-filename {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: var(--text-secondary);
  margin-left: 0.5rem;
}
.code-body {
  padding: 1.5rem;
  font-family: var(--font-mono);
  font-size: 0.82rem;
  line-height: 1.7;
  color: var(--text-accent);
  overflow-x: auto;
  min-height: 220px;
}
```

---

## 7. JAVASCRIPT — BEHAVIOR SPECIFICATION

### 7.1 Typing Effect (Hero Role)
```javascript
const roles = [
  "Ingénieur Logiciel & IA",
  "Entrepreneur & Fondateur",
  "Étudiant GI3 — ENSAO"
];
// Cycle through roles: type forward, pause 2s, erase, next role
// typingSpeed: 60ms/char | eraseSpeed: 30ms/char | pauseBetween: 2000ms
```

### 7.2 Code Block Typewriter
```javascript
const codeText = `# zakaria.py
class IngenieurIA:
    def __init__(self):
        self.name = "Zahraoui Zakaria"
        self.role = "Ingénieur IA & Fondateur"
        self.stack = [
            "Python", "React", "Flutter",
            "scikit-learn", "Firebase"
        ]
        self.startups = ["Fin IA", "PORT2REGION IA"]
        self.building = True

    def solve(self, problem):
        return "ai_powered_solution"`;
// Reveal line by line with 80ms delay between lines
// Each line types character by character at 25ms/char
```

### 7.3 Navbar Scroll Detection
```javascript
window.addEventListener('scroll', () => {
  const nav = document.getElementById('navbar');
  if (window.scrollY > 80) nav.classList.add('scrolled');
  else nav.classList.remove('scrolled');
});
```

### 7.4 IntersectionObserver — All Animations
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      // If skill fill bar: set width
      // If stat counter: start count-up
    }
  });
}, { threshold: 0.15 });

document.querySelectorAll('.animate-on-scroll').forEach(el => observer.observe(el));
```

### 7.5 Counter Animation
```javascript
function animateCounter(el, target, duration = 2000) {
  let start = 0;
  const step = target / (duration / 16);
  const timer = setInterval(() => {
    start = Math.min(start + step, target);
    el.textContent = Math.floor(start) + (target >= 5 ? '+' : '');
    if (start >= target) clearInterval(timer);
  }, 16);
}
// Triggered once when #about enters viewport
```

### 7.6 Hamburger Menu (Mobile)
```javascript
const hamburger = document.querySelector('.hamburger');
const mobileMenu = document.getElementById('mobileMenu');
hamburger.addEventListener('click', () => {
  hamburger.classList.toggle('active');
  mobileMenu.classList.toggle('open');
});
// Close on link click
document.querySelectorAll('#mobileMenu a').forEach(link => {
  link.addEventListener('click', () => {
    hamburger.classList.remove('active');
    mobileMenu.classList.remove('open');
  });
});
```

### 7.7 Active Section Highlight (Navbar)
```javascript
// Use IntersectionObserver on each section, update nav link active state
// Add .active class to corresponding nav link when section is in view
```

### 7.8 Lucide Icons Init
```javascript
// At bottom of body, after all HTML rendered:
lucide.createIcons();
```

---

## 8. RESPONSIVE CSS — BREAKPOINTS

```css
/* Tablet */
@media (max-width: 1023px) {
  .sidebar { display: none; }
  .hamburger { display: flex; }
  .nav-links { display: none; }
  .hero-content { flex-direction: column; }
  .hero-right { display: none; } /* or shrink */
  .projects-grid .project-featured { grid-column: span 12; }
  .projects-grid .project-card { grid-column: span 6; }
  .skills-grid { grid-template-columns: 1fr; }
}

/* Mobile */
@media (max-width: 767px) {
  .projects-grid .project-card { grid-column: span 12; }
  .certs-grid { grid-template-columns: 1fr; }
  .contact-layout { flex-direction: column; }
  .about-grid { flex-direction: column; }
  .section-number { font-size: 5rem; }
  .hero-name { font-size: 2.2rem; }
}
```

---

## 9. ADDITIONAL FEATURES (vs. Hamza's original)

These are **NEW** features to add on top of the reference architecture:

### 9.1 Startup Badge on Project Cards
- Featured projects with `status-award` get a gold/yellow glow border instead of blue
- `border-color: #f6b73c` + `box-shadow: 0 0 20px rgba(246,183,60,0.15)`

### 9.2 "Founding" Label
- In the navbar or hero, add a small badge `🚀 Fondateur` under the monogram on desktop sidebar

### 9.3 Floating CTA (mobile only)
```css
/* Fixed bottom CTA on mobile */
.mobile-cta {
  display: none;
}
@media (max-width: 767px) {
  .mobile-cta {
    display: block;
    position: fixed; bottom: 1rem; right: 1rem; z-index: 999;
    background: var(--accent-primary);
    color: white;
    padding: 0.75rem 1.25rem;
    border-radius: 50px;
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 600;
    box-shadow: 0 4px 20px var(--accent-glow);
  }
}
```

### 9.4 Section Active Indicator
- Left sidebar vertical dots (one per section) — clicking scrolls to section
- Active dot glows blue, others are muted

---

## 10. FILE DELIVERABLE REQUIREMENTS

```
Output:        index.html  (single file, all CSS + JS inline)
Hosting:       Netlify / GitHub Pages (zero build)
Dependencies:  Google Fonts CDN + Lucide Icons CDN (both loaded in <head>)
No frameworks: Vanilla HTML/CSS/JS only (no React, no Vite, no npm)
Browser:       Chrome, Firefox, Safari, Edge — latest 2 versions
Performance:   < 200KB unminified, no external images required
```

---

## 11. DATA PLACEHOLDER CHECKLIST

Before deploying, update these values:

| Field | Placeholder | Action |
|---|---|---|
| Email | `zakaria.zahraoui@etu.uae.ac.ma` | Confirm real email |
| GitHub URL | `github.com/zakaria-zahraoui` | Confirm correct username |
| Coursera cert link (ML) | `#` | Add real Coursera verify URL |
| Coursera cert link (Spec) | `#` | Add real Coursera verify URL |
| Fin IA GitHub | `#` | Add repo URL when public |
| P2R GitHub | `#` | Add repo URL when public |
| Artouris GitHub | `#` | Add repo URL |
| Seismo Safe GitHub | `#` | Add repo URL |

---

*Blueprint authored by Claude (Anthropic) — Senior Prompt Engineering Mode*
*Target: Antigraphity — Single-file HTML generation*
*Version: 1.0 — June 2026*
