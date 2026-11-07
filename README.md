# Shubham & Chahat · Wedding Music

A personal wedding music desk designed for GitHub Pages. Static HTML, CSS and JavaScript; no build, backend, paid hosting, or client secret required.

## Publish on GitHub Pages

1. Create a public GitHub repository, such as `shaadi-sound`.
2. Upload `index.html`, `style.css`, `app.js`, `README.md`, and `.nojekyll` to its root.
3. Under **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Open the HTTPS URL GitHub provides, usually `https://YOUR-USERNAME.github.io/shaadi-sound/`.

Public site: https://gavriankur.github.io/shubham-chahat-music/

Source repository: https://github.com/gavriankur/shubham-chahat-music

## Connect Spotify

The included Client ID is already configured for your wedding app and `http://127.0.0.1:8000/`. Open **Connect Spotify → Continue to Spotify** to sign in. For GitHub Pages, add the final HTTPS page URL to this existing app’s redirect URIs first. The Client ID is public and safe to include; no client secret is used.

To configure a different app:

1. Sign in to https://developer.spotify.com/dashboard with your Spotify Premium account.
2. Create an app; enable **Web API** and **Web Playback SDK** where offered.
3. Open your deployed webpage and click **Connect Spotify**. Copy the redirect URL shown there.
4. Add that **exact URL**, including the path and trailing slash if shown, to your Spotify app's redirect URIs. Save the app settings.
5. Copy the app's **Client ID**, paste it into Shaadi Sound, and connect. A Client ID is public; never paste or publish a client secret or private key.
6. Development-mode apps support a limited set of users. Add other authorized users under the developer dashboard's user access settings. This is intended to run from your own account, not to let every wedding guest sign in.

Spotify authorization uses PKCE with a state check. The Client ID is stored in local browser storage. Access and refresh tokens stay in session storage for this origin/tab; they are not included in plan backups. Disconnect to clear this page's session; you can also revoke access from your Spotify account's Apps settings. Anyone using your signed-in browser can control playback, so use your own device.

## Set your soundtrack

- Click **Edit moments** and paste a Spotify playlist, album, or song share link into each wedding card. All six moments include your created Spotify playlists: Baraat (5 songs), Shubham’s Entry (4), Family Dance (13), Bollywood (5), Punjabi (5), and Last Few Songs (5). There is some overlap between sets. You can replace any link.
- Click **Done editing**. Clicking a configured card starts that music on the selected device.
- To control the Spotify app: open Spotify, start a song, then return here, refresh playback, and select the device.
- For audio directly from the webpage, select **This device** under Playing on, or click **Enable this device**, then choose a moment. Clicking a moment also starts the local browser player if needed. The app defaults to This device, so it will not automatically pick an Alexa speaker. Requires a supported browser, Spotify Premium, protected-content playback, and internet. Some mobile browsers require an additional tap to start audio.
- Connect your laptop/phone audio to your speaker system. Test the exact device, browser and venue connection ahead of time.
- Requests are a manually entered checklist; they do not search Spotify or automatically join its playback queue. They are saved only in this browser.
- **Back up my plan** exports moment links and requests. **Restore plan** replaces the current moments and requests with that backup. Transfers between devices are manual.

## Limits and troubleshooting

- Music streaming needs internet. This webpage cannot use Spotify/Apple Music downloads or provide offline streaming. Have the official Spotify app's offline playlists as a separate fallback.
- This controls normal playback; it does not mix, crossfade, overlay effects, download songs, or provide Apple Music playback.
- Browser playback may not work in private browsing or when protected content is disabled. Use an existing Spotify device instead.
- Redirect error: compare the URL shown in setup with the developer app's saved redirect URL, character for character.
- 403/access denied: check Premium, the app's allowed users, and track/device restrictions.
- No device: play a song in the Spotify app and refresh, or select **This device**.
- Rate limits: the page backs off after Spotify's retry interval; developer quota errors may require waiting longer.
- Tokens and playback capabilities cannot be fully verified until you connect a real developer app/account. Browser/OS volume is controlled outside this page.
- The supplied Google Fonts are optional; the page falls back to system fonts if they cannot load.

## Local preview

Serve this folder with any static HTTP server at `http://127.0.0.1:8000/`. Add that exact URL as an additional redirect URI for local Spotify testing. Do not use `localhost` as the Spotify redirect hostname. Opening `index.html` as a file is insufficient for Spotify sign-in.

## References

- https://developer.spotify.com/documentation/web-api/tutorials/code-pkce-flow
- https://developer.spotify.com/documentation/web-playback-sdk
- https://developer.spotify.com/documentation/web-api/concepts/quota-modes
- https://developer.spotify.com/policy
- https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages


## Live console

Search Spotify by song/artist or paste a full Spotify track link. Each result has Play now and Add to queue. Play now immediately starts that recording; Add to queue appends it after songs already queued. Spotify does not expose insertion, removal or queue reordering through this API. The upcoming list displays up to 20 songs from the active Spotify queue and refreshes periodically or when requested.

The seek bar, Start, and ten-second jumps work on the current track. Pause for announcement pauses Spotify; Resume music continues on the same device and song. No microphone is captured or amplified by this page. Space toggles play/pause and N skips, unless focus is in a form or button.

The six source files include console.js; upload it alongside app.js, index.html, style.css, README.md and .nojekyll. Live search, queue access and playback still require an authorized Spotify Premium account and Spotify developer access. Restrictions and rate limits are shown in the interface.
