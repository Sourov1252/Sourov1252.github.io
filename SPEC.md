# Product & Technical Specification (SPEC.md)

## 1. Project Overview & Identity
- **Brand**: Sourov.dev
- **Tagline**: Learn. Build. Document. Share.
- **Project Purpose**: Build a professional personal developer portfolio combined with a Bengali technical learning platform, machine learning/data science project showcase, and Jupyter Notebook publishing laboratory.
- **Repository**: `Sourov1252/Sourov1252.github.io`
- **Owner**: MD Sourov Islam
- **Academic Background**: B.Sc. in Electrical and Electronic Engineering (EEE), Khulna University of Engineering & Technology (KUET)
- **Domain & Learning Focus**: Python, SQL, Data Analytics, Statistics, Data Science, Machine Learning, Deep Learning.
- **Target Audience**: Students, self-learners, researchers, and software engineers in Bangladesh and the global Bengali-speaking diaspora, alongside international engineering peers and recruiters.

---

## 2. Technical Architecture & Decisions

### 2.1 Core Framework
- **Primary Generator**: Quarto Website (`quarto` CLI v1.11.9+).
- **Sole SSG Mandate**: Quarto is the sole primary website generator. Do not introduce Next.js, Astro, React, MkDocs, Hugo, or any alternate framework without explicit authorization.
- **Runtime Environment**: Windows Native, PowerShell 7 (pwsh 7.6.9+), Python 3.12+.

### 2.2 Notebook & Execution Architecture
- **Rendering Mechanism**: Quarto renders `.ipynb` notebooks using previously saved cell outputs by default. It does **not** execute notebook cells during normal rendering.
- **Computational `.qmd` Execution**: Use `execute.freeze: auto` where appropriate for computational `.qmd` files so that only changed documents re-execute. This must not be mischaracterized as a requirement to stop default `.ipynb` execution.
- **Computation Boundary**: Heavy ML/DL training or data-heavy evaluations must **never** run during standard website rendering. All notebook computations must be executed locally or in the cloud prior to committing.
- **Interactive Badges**: Every published notebook in `notebooks/` must provide:
  - `Open in Google Colab` badge/link pointing directly to the notebook in `Sourov1252/Sourov1252.github.io`.
  - `View on GitHub` link.
- **Execution Promise**: No in-browser Python execution (e.g., Pyodide/WebAssembly) is promised in the MVP.

### 2.3 Math & Formula Rendering
- Start with Quarto's built-in default math rendering.
- Evaluate KaTeX vs MathJax during the styling and layout prototype phase.
- Avoid introducing unnecessary external dependencies or third-party plugins.

### 2.4 Deployment & Hosting Architecture (MVP)
- **Host**: GitHub Pages on user site repository `Sourov1252/Sourov1252.github.io`.
- **Output Directory**: Configured via `_quarto.yml` as `project.output-dir: docs`.
- **Version Control Policy**: The generated `docs/` build directory remains tracked in Git on the `main` branch.
- **Static Asset Flag (.nojekyll)**: Retain the root-level `.nojekyll` file. Quarto automatically recognizes and copies `.nojekyll` into the output directory (`docs/`) during site rendering to prevent Jekyll processing on GitHub Pages.
- **Deployment Source & Managed Pipeline**: GitHub Pages deploys from branch `main` and directory `/docs` using GitHub's native, managed Pages deployment process.
- **No Custom GitHub Actions Workflow in MVP**: We do not configure or maintain a custom GitHub Actions publishing workflow for the MVP. Builds remain local, deterministic, and transparently verified before committing. Future migration to a custom GitHub Actions workflow may be considered when a genuine need arises.

---

## 3. Information Architecture & Canonical Directories

### 3.1 Canonical Content Directories
- `tutorials/`: Step-by-step educational articles, guides, and conceptual explanations written in `.qmd`.
- `notebooks/`: Practical, code-driven Jupyter Notebooks (`.ipynb`) with accompanying explanations and Colab links.
- `projects/`: Real-world project case studies, machine learning workflows, and data analyses (`.qmd`).
- `updates/`: Learning logs, engineering journal entries, milestones, and technical reflections (`.qmd`).
- `resources/`: Curated roadmaps, cheat-sheets, reference guides, book notes, and learning resources (`.qmd`).
- `_templates/`: Standardized starter templates for tutorials, project case studies, and notebooks.
- `_drafts/`: Work-in-progress content excluded from website publishing until reviewed.

### 3.2 Root Pages & Sections
- `index.qmd`: Homepage featuring hero intro, mission statement, featured tutorials, latest projects, and learning updates.
- `about.qmd`: Detailed profile of MD Sourov Islam (EEE KUET background, transition to Data/ML, values, journey).
- `contact.qmd`: Verified social links, GitHub profile, LinkedIn, and contact methods.

### 3.3 Asset & Styling Directories
- `styles/light.scss`: Light theme SCSS variables and custom style rules.
- `styles/dark.scss`: Dark theme SCSS variables and custom style rules.
- `styles/custom.scss`: Global typography, Bengali line-height rules, layout adjustments, and component styles.
- `assets/images/`: Optimized diagrams, project covers, screenshots, and profile imagery.
- `assets/fonts/`: Fallback or local web font declarations.

---

## 4. Language & Editorial Standards

### 4.1 Strict Bengali Script Policy
- All reader-facing educational text, tutorial prose, explanations, narratives, and pedagogical commentary must be composed in **proper Bengali script (বাংলা লিপি)**.
- **Strictly Prohibited**: Never write "Banglish" or Romanized Bengali (e.g., writing Bengali words using the English alphabet).
- Tone must be clear, intellectually respectful, grammatically sound, and accessible to learners at all stages.

### 4.2 Technical Terminology & Permitted English Elements
- **Technical & Programming Terms**: Keep technical terms, programming syntax, keywords, variable names, function names, library names, system commands, URLs, and filenames in **standard English** (e.g., `DataFrame`, `gradient descent`, `train_test_split`, `quarto render`, `pip install`, `Loss Function`, `Epoch`).
- **UI, Navigation & Metadata**: Navigation labels (e.g., "Tutorials", "Notebooks", "Projects"), UI elements, brand text ("Sourov.dev"), project titles, category tags, and technical metadata may remain in English where appropriate.
- When introducing a technical concept for the first time in a tutorial, provide the English technical term alongside the Bengali conceptual explanation.

---

## 5. Visual Identity & Design System

### 5.1 Design Philosophy
- **Style**: Minimal Editorial + Modern Developer Documentation.
- **Character**: Calm, focused, distraction-free, accessible, responsive, and readable across all device form factors.

### 5.2 Color Tokens
| Token | Light Theme | Dark Theme | Purpose |
| :--- | :--- | :--- | :--- |
| **Background** | `#FAF7F2` (Warm Paper) | `#151A23` (Deep Slate) | Page and canvas background |
| **Text Primary** | `#1E2430` (Charcoal Ink) | `#E6E1D8` (Soft Parchment) | Body copy and primary typography |
| **Accent / Brand** | `#2F7F79` (Earthy Pine Teal) | `#5FB3AB` (Luminous Sage Teal) | Links, highlights, badges, primary buttons |

### 5.3 Typography Stack
- **Bengali Typography**: `Hind Siliguri`, sans-serif.
- **English & UI Typography**: `Inter`, -apple-system, sans-serif.
- **Code & Monospace Typography**: `JetBrains Mono`, monospace.
- **Bengali Line Height**: Enforce `line-height: 1.7` to `1.8` for all Bengali text blocks to preserve vowel signs (*matras*) and prevent clipping.
- **Letter Spacing**: Use natural font spacing; **no** artificial letter-spacing on Bengali text.

---

## 6. Content Standards & Workflow

1. **File Naming**: Strict lowercase, hyphen-separated filenames (e.g., `python-list-comprehension.qmd`, `eda-housing-data.ipynb`).
2. **Metadata Integrity**: Every document must declare consistent YAML frontmatter:
   ```yaml
   ---
   title: "Descriptive Title"
   description: "One or two sentence summary"
   date: "YYYY-MM-DD"
   categories: [Python, Data Science]
   ---
   ```
3. **Factual Honesty**:
   - Never invent, fabricate, or exaggerate personal qualifications, employment history, degrees, certificates, project results, benchmark numbers, or credentials.
   - If a project benchmark or result is pending, explicitly label it as in-progress.
4. **Templates & Drafts**: All new content drafts begin in `_drafts/` utilizing blueprints from `_templates/` before promotion to canonical directories.

---

## 7. MVP Scope & Phased Roadmap

### 7.1 MVP Deliverables
1. **Repository Foundation**: Fully configured `SPEC.md`, `AGENTS.md`, and clean Git structure.
2. **Core Layout & Theming**: Clean responsive Quarto layout with dual light/dark themes (`#FAF7F2` / `#151A23`).
3. **Core Pages**:
   - Homepage (`index.qmd`)
   - About page (`about.qmd`)
   - Contact page (`contact.qmd`)
4. **Technical Tutorials**: 3 beginner-to-intermediate Python tutorials written in grammatically sound Bengali.
5. **Project Case Study**: 1 genuine, verified data science or Python project study with authentic code and documentation.
6. **Notebook Lab**: 1 well-documented `.ipynb` notebook with pre-saved outputs and working Google Colab / GitHub buttons.
7. **Resources & Updates Foundations**: Initial catalog in `resources/` and updates in `updates/`.
8. **Deployment**: Static build output in `docs/`, root `.nojekyll`, live on GitHub Pages under `Sourov1252.github.io`.

### 7.2 Post-MVP Enhancements (Out of Scope for MVP)
- Interactive web apps (Streamlit, Gradio, Hugging Face Spaces integration).
- In-browser interactive Python consoles (WebAssembly/Pyodide).
- Automated GitHub Actions deployment pipeline (to be considered only when manual/local build verification becomes inadequate).
- Complex comments/analytics integrations.
