# Verity AI Website — GitHub Pages + API backend

## Why it looked unstyled
The custom UI lives in `css/style.css`; JavaScript and mascot files are separate. Publish the *contents* of this project folder, not only `index.html` and not a nested `verity-ai-website/` folder. The root published directory must contain `index.html`, `css/`, `js/`, and `assets/`. Paths are project-relative and the CSS/JS links include a cache-busting version.

## Publish the custom UI on GitHub Pages
1. Extract this ZIP.
2. Copy the contents of this folder into the root of the repository (or into the exact folder selected in Settings → Pages). You should see `index.html`, `css`, `js`, `assets`, and `.nojekyll` together.
3. Commit/push, then hard-refresh the site. On Android Chrome, open the site and reload; if necessary clear site cache.
4. Test the CSS address directly by appending `/css/style.css?v=4` to your site URL. It should display CSS source, not a 404 page.

## Important: GitHub Pages cannot run API code
GitHub Pages only serves static files. It cannot execute `server.js`, so chat, CodeBox, Fish Audio, and image generation will not work until the API server is deployed separately. The UI will display a useful error instead of a vague fetch failure.

## Deploy the API server
Deploy `server.js` as a Node.js web service on a host such as Render or Railway. Deploy the `server.js` file and `package.json` from this project. Node.js 18+ is required; no `npm install` is needed for this server. The server listens on the host-provided `PORT`, binds to `0.0.0.0` in production, and supports CORS for browser requests. Set `VERITY_ALLOWED_ORIGIN` to your GitHub Pages origin (for example `https://YOURNAME.github.io`) for a tighter CORS policy. The default `*` is convenient for testing but is not the most restrictive production configuration.

Once the API service is live:
1. Open your GitHub Pages site.
2. Go to **Settings & API** (or enter it on the setup screen).
3. Put your hosted backend's HTTPS base URL in **API server URL**, without an `/api` suffix, for example `https://your-service.onrender.com`.
4. Save settings and test Groq.
5. Add a Fish Audio key for voice and an OpenAI API key for image generation.

## Local run
Requires Node.js 18+. Run `node server.js` (or the included launch script) and open `http://127.0.0.1:8787`. Leave API server URL blank in local/same-origin mode.

## Security note
Never put provider API keys into source code or commit them. This browser app stores keys in local storage and sends them in request bodies to the backend. Use only a backend you control; set the allowed origin, and do not expose an unprotected relay to the public internet. OpenAI image generation may incur charges and requires access to the selected model.
