# Developer Profile

A developer profile website built with HTML and Tailwind CSS. The content is dynamically populated from `profile-data.json`, making it easy to update your information without touching the HTML structure.

## Features

- **Dynamic Content**: Personal info, skills, and experience are loaded from a JSON file.
- **Responsive Design**: Built with Tailwind CSS for a fully responsive layout.
- **Glassmorphism UI**: Modern aesthetic with glass-card effects.

## Development

The styles are generated using Tailwind CSS (v4).

### Prerequisites

- Node.js
- pnpm

### Setup and Build Styles

1.  **Install dependencies**:

    ```bash
    pnpm install
    ```

2.  **Regenerate Styles (Build)**:
    To compile the CSS once for production:

    ```bash
    pnpm run build
    ```

    This command runs `tailwindcss` to compile `./styles-in.css` into `./styles.css`.

3.  **Development Mode (Watch)**:
    To watch for changes and automatically rebuild the CSS:
    ```bash
    pnpm run dev
    ```
