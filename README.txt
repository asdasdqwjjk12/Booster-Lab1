Booster Lab — online Google Sites + jsDelivr export

This package has no Replit API dependency. It supports anonymous friend trades
after you deploy the API server and set its HTTPS origin in
booster-api-config.js. Until that is set, the trade screen stays disabled and
solo play still works. This export does not include account sign-in or cloud
saves. All money, grading and rewards are simulated gameplay.

Friend-trading backend:
1. Deploy the API source in artifacts/api-server from the complete repository.
   It requires PostgreSQL and the DATABASE_URL environment variable.
2. Apply the schema once to a new database with:
   pnpm --filter @workspace/db run push
3. Set the API host's PORT environment variable (your host normally supplies it)
   and NODE_ENV=production, then start it with:
   pnpm --filter @workspace/api-server run build
   pnpm --filter @workspace/api-server run start
4. Check that https://YOUR-API-HOST/api/healthz returns JSON.
5. Edit booster-api-config.js and set window.BOOSTER_API_BASE to the HTTPS
   origin only, for example https://booster-api.example.com (no /api suffix).
   Upload that file to the root of your public GitHub repository.
6. The API must allow browser requests from the page where the game is hosted.
   This export uses anonymous player tokens and does not send account cookies.

Update an existing public repo (small ZIP):
1. Extract booster-lab-jsdelivr-online.zip and upload the new versioned .js and .css files,
   booster-api-config.js, booster-lab.svg, and included pack photos to the ROOT
   of https://github.com/asdasdqwjjk12/booster-lab-pack-simulator. Upload google-sites-embed.html and embed-code.txt for your
   records. If you set BOOSTER_API_BASE before exporting, the config is already
   filled in. Otherwise edit it after deploying your own backend.
2. Keep older versioned JS/CSS files: an already-published embed may still use
   one of those immutable URLs. Do not rename the new files to booster-lab.js/css.
3. Paste all of embed-code.txt in Google Sites: Insert > Embed > Embed code.
   The document includes a viewport meta tag and a small iframe-safe reset.
   Set the Sites embed tall enough for the app and publish.
4. Open the published page and test trading between two devices. If you edited
   booster-api-config.js after uploading, allow time for the CDN to refresh.

To open the game directly through jsDelivr instead of Google Sites, upload
booster-lab.svg to the repository root, then open:
https://cdn.jsdelivr.net/gh/asdasdqwjjk12/booster-lab-pack-simulator@main/booster-lab.svg#/
For this update, use the cache-safe versioned link:
https://cdn.jsdelivr.net/gh/asdasdqwjjk12/booster-lab-pack-simulator@main/booster-lab.d4613e875d2a.svg#/
Open this as a webpage, not as an image element: scripts are disabled when SVG
is loaded through an img tag. The SVG launches the online guest frontend inside
a regular HTML frame; your externally hosted API is still required for trading.

For a mounted QA preview, place local-preview.html and its hashed JS/CSS files
beside one another at /cdn-check/. It uses this repo's CDN as its image base, so
the two large image folders do not need to be copied to the web app.

The small update ZIP includes pack photos at its root. Upload those files with
the new JS, CSS and SVG. Crown Zenith scans now also load from the repository
root, matching the flat upload layout. The full ZIP includes all 230 root-level
scans. The three crown-image batch ZIPs can be uploaded separately in smaller
batches. Upload their image FILES at the repository root, not inside a folder.


NEW REPOSITORY / COMPLETE FILE PACKAGE
Extract the full ZIP, then upload the CONTENTS of booster-lab-jsdelivr-online to your new
repository root (not the outer booster-lab-jsdelivr-online folder). Include all root files.
All 230 Crown Zenith scans and the pack photos are now root-level files.
No image folders are required for the CDN game. Do not rename the card images.
If uploading through GitHub's browser, use the small game update ZIP plus the
three crown-image batch ZIPs; each image batch contains fewer than 100 files.

The SVG launcher automatically uses the repository URL it was opened from:
https://cdn.jsdelivr.net/gh/asdasdqwjjk12/booster-lab-pack-simulator@main/booster-lab.d4613e875d2a.svg#/
You do not need to edit the SVG or JavaScript for the new repository.
index.html also works with relative assets on GitHub Pages or another static host.
jsDelivr serves HTML as text, so open the SVG when using jsDelivr directly.
Google Sites embed-code.txt is already configured for https://github.com/asdasdqwjjk12/booster-lab-pack-simulator.
Friend trading uses the URL in booster-api-config.js; deploy the API separately.
