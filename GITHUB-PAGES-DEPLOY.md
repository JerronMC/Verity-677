# Verity AI — GitHub Pages files

Extract these files directly into the root of your GitHub Pages publication folder. The folder should show `index.html`, `.nojekyll`, `css/`, `js/`, and `assets/` side-by-side. Do not upload only index.html or leave everything nested inside a second `verity-ai-website/` folder.

After publishing, check `https://YOURNAME.github.io/YOURREPO/css/style.css?v=4` (replace the URL with your site's base path). If that URL returns 404, your folder structure or Pages publishing source is wrong. Then hard-refresh the main website.

GitHub Pages serves static files only; it cannot run `server.js`. In Setup or Settings & API, set **API server URL** to the HTTPS URL of a separately deployed Node.js backend based on the complete Verity project ZIP. The API server must allow your GitHub Pages origin through CORS. If you have not deployed a backend, the custom interface will load but real Groq chat, Fish Audio speech, and OpenAI image generation will not work yet.
