 # TZ - Timezone Converter

 A simple static web app to parse natural language date/time strings and convert them across multiple timezones. Built with TypeScript, Sugar.js, and a brutalist CSS style.

 ## Features
- Natural language parsing (e.g., "tomorrow at 3pm", "next Friday").
- Accepts Unix epoch timestamps (seconds or milliseconds).
- Support for multiple timezones with autocomplete and localStorage persistence.
- Timezone selections persist in your browser. Use the **Reset Timezones** button to clear them.
- Defaults to your browser's local timezone on first load.
- 24-hour timeline visualization showing the hour of each timezone.
- Format toggles: **Long**, **Short**, and **ISO** representations.
- Copy-to-clipboard buttons for each converted timestamp.
- Optional dark mode toggle to switch themes.

 ## Live Demo
 Just open `index.html` in any modern browser. No server required (can be hosted on Cloudflare Workers or any static host).

 ## Getting Started
 ### Prerequisites
 - Node.js (v14+)
 - bun

 ### Installation
 ```bash
 git clone <repo-url>
 cd tz
 # Install dependencies (after removing node_modules or on fresh clone)
 bun install
 # Build the static site into ./public
 bun run build
 # Serve locally (install if needed):
 bun install -g serve
 serve public       # serve from the generated public directory
 ```

 ### Usage
 1. **Enter a date/time** in the top input (e.g., "today at 14:30").
 2. **Add timezones** by typing into the timezone box and pressing Enter (e.g., "UTC", "America/New_York").
3. **Select an output format**: Long, Short, or ISO.
4. **Click Convert** to see:
    - A 24-hour timeline for each timezone with the converted hour highlighted.
    - A list of converted timestamps with copy buttons.
5. **Reset Timezones** anytime using the button under the timezone input.
6. **Toggle Dark Mode** using the button in the header.

 ## Deployment
 Copy the entire `public/` directory to your static hosting environment (it contains `index.html`, `styles.css`, and `dist/`).

### Cloudflare Pages
1. Create a Pages project and connect your repository.
2. In **Settings → Build & deploy**, set:
   - **Production branch**: your default branch (e.g., `main`).
   - **Build command**: (leave empty if pre-built) or `bun run build`.
   - **Build output directory**: `.` (or `public` if you copy assets there).

### Cloudflare Workers (Wrangler)
1. Install Wrangler: `bun install -g wrangler`.
2. Create or update `wrangler.toml` in the project root:
   ```toml
   name = "tz"
   type = "javascript"

   account_id = "YOUR_ACCOUNT_ID"
   workers_dev = true

  [site]
   bucket = "./public"     # path to your generated static site
   entry-point = "workers-site"
   ```
3. Ensure `index.html`, `styles.css`, and `dist/` live under the `bucket` directory (root or `workers-site`).
4. Run `wrangler publish` to deploy.

 ## Development
 - Source code lives in `src/`; output is in `dist/`.
 - Autocomplete logic: `src/autocomplete.ts`
 - Conversion engine: `src/dateTimeConverter.ts`
 - UI main: `src/main.ts`
 - Styles: `styles.css`

 ## Contributing
 Feel free to open issues or PRs. Follow the brutalist style and minimal patch philosophy. Update documentation as needed.

 ## License
 MIT (see LICENSE file)
