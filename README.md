# Xelvo public site upload

This directory is a build-free static site for:

`https://xelvo-org.github.io/`

Publish the directory contents at the developer website root, preserving the `assets/` directory.

Expected public URLs:

- `https://xelvo-org.github.io/`
- `https://xelvo-org.github.io/privacy.html`
- `https://xelvo-org.github.io/terms.html`
- `https://xelvo-org.github.io/support.html`

The Google Play privacy-policy URL is:

`https://xelvo-org.github.io/privacy.html`

The Google Play developer website is:

`https://xelvo-org.github.io/`

Before publishing, verify the links and layout from the final HTTPS URLs. No build step or server-side feature is required.

The site keeps its runtime assets local. `assets/xelvo-ribbon.webp` is derived from the repository's Xelvo feature graphic, and `assets/google-play-lockup.png` is Google's official Google Play lockup from `https://www.gstatic.com/android/market_images/web/play_prism_hlock_2x.png`, used only for the link to Xelvo's Google Play listing.

Manual website publication order:

1. Open the repository that publishes `xelvo-org.github.io`.
2. Replace its site root with this directory's `index.html`, Privacy, Terms, Support, and `assets/` contents.
3. Keep `store/google-play/app-ads.txt` published separately as the root-level `app-ads.txt`.
4. Commit and push through the repository's normal GitHub Pages source branch.
5. After deployment, open the four expected page URLs and `app-ads.txt` without signing in, then update the Play developer website and privacy-policy fields.

Publish each release's candidate-bound native license packet as immutable GitHub Release assets in the separate public repository `xelvo-org/xelvo-open-source`, rather than committing the archives to the website or Git history:

- `xelvo-<versionName>-<versionCode>-lgpl-relink.tar.gz`
- `xelvo-<versionName>-<versionCode>-lgpl-relink.tar.gz.sha256`

Keep old release assets available and retain a separate backup. The public download location is:

`https://github.com/xelvo-org/xelvo-open-source/releases`

Each packet's `CANDIDATE.txt` identifies the application ID, version code, version name, Git revision, AAB SHA-256, and upload-signing certificate SHA-256. The packet proves that all three ABI variants can be relinked from the included material and preserve the candidate's exported native ABI; it does not claim that the relinked files are byte-identical after object merging and stripping.

Manual publication order:

1. Confirm the public GitHub repository `xelvo-org/xelvo-open-source` is accessible without signing in; it does not need GitHub Pages.
2. Generate the packet from the clean, signed final candidate using `android/tools/prepare_native_license_packet.sh`.
3. Create a GitHub Release whose title identifies the candidate `versionName` and `versionCode`.
4. Upload the generated `.tar.gz` and `.tar.gz.sha256` as immutable Release assets.
5. Confirm both assets can be downloaded without signing in, their checksum matches, and the release remains available after newer versions are published.

`app-ads.txt` is maintained one directory above this site at `store/google-play/app-ads.txt` and published at:

`https://xelvo-org.github.io/app-ads.txt`
