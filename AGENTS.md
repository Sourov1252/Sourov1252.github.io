# Agent Guidelines & Operational Rules (AGENTS.md)

## 1. Core Operating Context & Project Identity
- **Project**: Sourov.dev (`Sourov1252/Sourov1252.github.io`)
- **Tagline**: Learn. Build. Document. Share.
- **Owner**: MD Sourov Islam (B.Sc. in Electrical and Electronic Engineering, KUET)
- **Domain Focus**: Python, SQL, Data Analytics, Statistics, Data Science, Machine Learning, Deep Learning.
- **Sole Framework**: Quarto Website (`quarto` CLI).
- **Environment**: Windows Native, PowerShell 7 (`pwsh.exe` 7.6.9+), Python 3.12+, Quarto 1.11.9+.
- **Specification Authority**: All development and content creation must strictly align with the root-level [SPEC.md](SPEC.md).

---

## 2. Absolute Ground-Truth & Anti-Hallucination Rules
- **No Fictional Profile Data**: Never invent, assume, or extrapolate employment history, job titles, university degrees, academic honors, certifications, corporate affiliations, or client projects for MD Sourov Islam.
- **No Fabricated Metrics**: Never manufacture project outcomes, model accuracies, training loss benchmarks, or performance figures. All technical numbers must come from authentic experiments.
- **Missing Information Protocol**: If profile details, background info, or project results are missing, place a clear marker (e.g., `<!-- TODO: To be provided by Sourov -->`) and ask the user rather than filling in imaginary details.

---

## 3. Language & Editorial Compliance
- **Strict Bengali Script**: All reader-facing educational tutorials, conceptual explanations, intros, and explanatory prose must be written in proper Bengali script (বাংলা লিপি).
- **Zero Banglish Rule**: Never generate Romanized Bengali / Banglish (e.g., "apni eikhane click korun" is strictly forbidden).
- **Technical English**: Keep technical terminology, programming code, variable/function identifiers, file paths, library names, and system commands in English (e.g., `pandas`, `LinearRegression`, `train_test_split`, `_quarto.yml`).
- **Permitted English Elements**: Navigation labels, UI labels, brand text ("Sourov.dev"), project titles, category tags, and technical metadata may remain in English where appropriate.
- **Typography Standards**: Ensure all Bengali typography is styled with `Hind Siliguri`, comfortable line-height (1.7–1.8), and zero artificial letter spacing.

---

## 4. Architectural & Technology Constraints
- **Sole SSG Mandate**: Quarto is the only site generator permitted. Never introduce or recommend switching to Next.js, React, Astro, MkDocs, Hugo, or Vue unless authorized.
- **Static MVP Boundary**: No databases (SQL/NoSQL), no server-side authentication (OAuth, Firebase), and no active backend APIs. Everything compiles to static files.
- **Dependency Discipline**: Do not run `npm install`, `pip install`, or install global/local CLI tools without explicit user authorization.

---

## 5. Notebook & Computational Workflow
- **Saved Output Rule**: Understand that Quarto renders `.ipynb` notebooks using their existing saved cell outputs by default. It does **not** re-execute notebook cells during ordinary site rendering.
- **Computational `.qmd`**: Apply `execute.freeze: auto` for executable computational `.qmd` documents so that unchanged calculations are cached. Do not misattribute this freeze setting to default `.ipynb` behavior.
- **No Heavy Execution**: Heavy model training, gradient calculations, or massive dataset iterations must **never** be run during site rendering. Run them offline or in Google Colab, and save the lightweight artifacts.
- **Interactive Links**: All published notebooks in `notebooks/` must include:
  1. `Open in Google Colab` badge/link referencing `Sourov1252/Sourov1252.github.io`.
  2. `View on GitHub` link.
- **No In-Browser Execution Claims**: Do not promise or attempt in-browser Python execution in the MVP.

---

## 6. Directory Conventions & File Hygiene
All website assets and content must conform to this canonical structure:
- `tutorials/`: Bengali technical tutorials (`.qmd`).
- `notebooks/`: Practical Jupyter Notebooks (`.ipynb`).
- `projects/`: Real-world project case studies (`.qmd`).
- `updates/`: Learning logs and engineering journal entries (`.qmd`).
- `resources/`: Curated reference guides and study materials (`.qmd`).
- `_templates/`: Reusable blueprints for tutorials, projects, and notebooks.
- `_drafts/`: Unpublished drafts in progress.
- `styles/`: Custom SCSS files (`light.scss`, `dark.scss`, `custom.scss`).
- `assets/`: Static media (`assets/images/`, `assets/fonts/`).

### Naming Conventions:
- All content files and directories must use lowercase, hyphen-separated characters (e.g., `python-data-types.qmd`, `eda-customer-churn.ipynb`).
- Never use spaces or special characters in filenames.

---

## 7. Deployment & Hosting Protocol (MVP)
- **Deployment Target**: GitHub Pages serving the user site `Sourov1252/Sourov1252.github.io`.
- **Output Directory**: `project.output-dir: docs` inside `_quarto.yml`.
- **Git Tracking**: The compiled `docs/` output directory must remain tracked in Git on the `main` branch.
- **Jekyll Bypass**: Retain the root-level `.nojekyll` file. Quarto recognizes and copies `.nojekyll` into the output directory (`docs/`) during rendering to prevent GitHub Pages from running Jekyll processing.
- **GitHub Managed Deployment**: GitHub Pages will deploy from the `main` branch `/docs` folder using GitHub's native, managed Pages deployment process.
- **No Custom GitHub Actions Workflow**: Do not create or maintain a custom GitHub Actions publishing workflow for the MVP. Build locally, verify, and commit `docs/`. Future migration to a custom GitHub Actions workflow may be considered when a genuine need arises.

---

## 8. Antigravity & Tool Execution Discipline
- **Shell Standard**: Always execute shell commands using PowerShell 7 (`pwsh`), never CMD or legacy Windows PowerShell 5.1.
- **Git State Hygiene**:
  - Always run `git status` **before** planning or making file modifications.
  - Always run `git status` **after** making file modifications to inspect changed, untracked, or staged files.
  - Make small, incremental, focused changes. Avoid monolithic multi-file rewrites.
- **History Preservation**:
  - Never execute `git push --force`.
  - Never run commands that rewrite or destroy existing repository history.
- **Protected Files**:
  - Do not modify or overwrite the existing `README.md` without explicit user instruction.
  - Do not overwrite existing working files without prior consent.
- **Verification First**: Verify rendered output and check for errors before declaring any task complete.
