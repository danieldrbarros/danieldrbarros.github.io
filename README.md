# danieldrbarros.github.io

This repository hosts my personal website and CV, automatically published via **GitHub Pages**. The site includes an `index.html` landing page and an HTML‑based CV (`cv.html`). A GitHub Action generates a print‑ready PDF version of the CV (`cv.pdf`) every time `cv.html` is updated.

## 🔍 Project Overview

- **Live website**: [https://danieldrbarros.github.io](https://danieldrbarros.github.io)  
- **Purpose**: Personal portfolio / CV website  
- **Key files**:
  - `index.html` – Main entry point of the website.
  - `cv.html` – Detailed CV in HTML format (styled for both screen and print).
  - `cv.pdf` – Auto‑generated PDF version of the CV (committed to the repo).
  - `.github/workflows/generate-cv-pdf.yml` – GitHub Action that creates `cv.pdf` from `cv.html`.

## ⚙️ How the PDF Generation Works

The workflow (`.github/workflows/generate-cv-pdf.yml`) is triggered:

- Automatically on every `git push` that modifies `cv.html`.
- Manually via the **Actions** tab in GitHub (`workflow_dispatch`).

It performs the following steps:

1. **Checks out** the repository.
2. **Sets up Node.js** (version 20).
3. **Installs Puppeteer** – a headless Chrome browser for rendering.
4. **Runs a Node script** that:
   - Launches Puppeteer with appropriate sandbox flags.
   - Loads `cv.html` from the local file system.
   - Sets a viewport width of 1200px and height to match the full document.
   - Exports the page to a **PDF** with A4 format, background graphics enabled, and scaling adjusted to fit the content without clipping.
5. **Commits and pushes** the generated `cv.pdf` back to the repository (if changed).

> 💡 The PDF is **automatically kept in sync** with the HTML version – no manual conversion needed.

## 📄 Editing My CV

To update my CV:

1. Edit `cv.html` locally or directly on GitHub.
2. Push the changes to the `main` branch (or your default branch).
3. The GitHub Action will run and regenerate `cv.pdf`.
4. After a few seconds/minutes, the updated PDF will appear in the repository and be served alongside your site.
5. You might locally run `git pull` to get the new `cv.pdf` generated before commiting new things.

You can also trigger the workflow manually from the **Actions** tab if needed.

## 🖨️ Generating the PDF Locally (Optional)

If you want to generate `cv.pdf` on your own machine:

```bash
# Clone the repo
git clone https://github.com/danieldrbarros/danieldrbarros.github.io
cd danieldrbarros.github.io

# Install Puppeteer
npm install puppeteer

# Run the same generation script (copy it from the workflow or create a separate .js file)
node generate-pdf.js
```

Make sure the script loads `cv.html` from the correct path and writes `cv.pdf` to the repository root.

## 🌐 GitHub Pages Deployment

Because the repository is named `<username>.github.io`, GitHub Pages automatically publishes the contents of the `main` branch at `https://danieldrbarros.github.io`. No extra configuration is required – just push `index.html`, `cv.html`, and any assets (CSS, images, etc.).

## 📝 License

You are free to use this repository as a template for your own personal site. If you include any third‑party libraries or assets, please respect their respective licenses.

---

**Maintainer:** [Daniel D. R. Barros](https://github.com/danieldrbarros)  
*Last updated: 2026*