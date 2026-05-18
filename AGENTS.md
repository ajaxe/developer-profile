# AGENTS.md

## Project Mission
A high-performance, responsive developer portfolio and blog for **Ajay Sharma**. It serves as a centralized, static-site-generated hub to showcase professional experience, technical skills, and a diverse portfolio of projects ranging from CLI tools to self-hosted cloud services.

## Tech Stack & Core Dependencies
*   **Static Site Generator:** **Hugo** (v0.87.0 or higher).
*   **Theme:** **hugo-profile** (Bootstrap-based, mobile-first).
*   **Content Management:** **YAML** (`hugo.yaml`), **Markdown** (`content/`), and supplemental **JSON** (`profile-data.json`, `projects.json`).
*   **Styling:** **CSS/Bootstrap** integrated via the theme; configured through Hugo parameters.
*   **Runtime:** Hugo binary is the primary requirement for development and builds.

## Architecture & Design Patterns
*   **Theme-Driven SSG:** The site architecture is defined by the **hugo-profile** theme. Most UI components (Hero, About, Experience) are standard theme partials.
*   **Data-Driven Configuration:** The **`hugo.yaml`** file acts as the primary source of truth for site content. Section data is stored in the `params` block, allowing for rapid content updates without layout modifications.
*   **Override Pattern:** Utilizes Hugo’s lookup order for customization. Local overrides are placed in the root `layouts/` folder to modify theme behavior while keeping the `themes/hugo-profile` directory pristine.
*   **Static Media Hub:** Images and assets are served from the `static/` directory, organized by category (e.g., `static/images/projects/`).

## Directory Mental Model
*   **`/hugo.yaml`**: **The Site Brain**. Contains all global settings, section content, social links, and feature toggles.
*   **`/content/`**: Contains **Markdown-based pages**. Subfolders like `blogs/` house long-form content.
*   **`/static/`**: **Static Assets**. Images (`/images/`), icons, and favicons. Referenced in config via root-relative paths.
*   **`/layouts/`**: **Template Overrides**. Currently used for local custom partials or overriding theme-provided HTML.
*   **`/themes/hugo-profile/`**: **The Engine**. Contains the core logic, assets, and base layouts. Should remain unmodified.
*   **`/profile-data.json` & `/projects.json`**: **Data Snapshots**. Portable JSON representations of the user's profile and projects for external use or future migrations.

## Development Standards
*   **Content Updates:** Prefer updating **`hugo.yaml`** for structural and section-based content (Experience, Projects, Education).
*   **Asset Management:** New project images should be placed in `static/images/projects/` and referenced in the config as `/images/projects/[filename]`.
*   **Convention over Modification:** Do **not** modify files in `themes/`. If a change is needed, copy the file to the root `layouts/` directory maintaining the same sub-path.
*   **Naming:** Use kebab-case for filenames in `content/blogs/` and `static/images/`.

## Hard Constraints & Anti-Patterns
*   **DO NOT** modify the `themes/hugo-profile/` folder directly.
*   **DO NOT** use absolute file system paths for assets; always use root-relative paths (e.g., `/images/hero.png`).
*   **DO NOT** add large binary files directly to the repo; optimize images before committing.
*   **ANTI-PATTERN:** Hardcoding personal details into `.html` templates. Use `hugo.yaml` params instead.

## Operational Commands
*   **`hugo server`**: Starts the local development server with live reload. Default: `http://localhost:1313`.
*   **`hugo server -D`**: Includes content marked as `draft: true`.
*   **`hugo`**: Generates the final static site in the `public/` directory.
*   **`rm -rf public/ && hugo`**: Performs a clean production build.
