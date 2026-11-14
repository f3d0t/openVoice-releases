# openVoice releases

Public release hosting for openVoice, separate from the private application
source repository. GitHub Pages publishes the root of this `gh-pages` branch.

## Files

- `index.html`: placeholder release download page.
- `latest.json`: valid, empty JSON object (`{}`). Replace it with the metadata
  expected by the updater when publishing a release; it is not yet a usable
  update feed.
- `releases/`: placeholder directory for release downloads.
- `.nojekyll`: publish static files directly without Jekyll processing.

## Enable GitHub Pages

1. Keep `f3d0t/openVoice-releases` public to use Pages on GitHub Free.
2. Open [Settings → Pages](https://github.com/f3d0t/openVoice-releases/settings/pages).
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Select **gh-pages** and **/(root)**, then save.
5. Enable **Enforce HTTPS** when available and wait for deployment to finish.

Expected public URLs:

- Site: <https://f3d0t.github.io/openVoice-releases/>
- Feed: <https://f3d0t.github.io/openVoice-releases/latest.json>
- Downloads: `https://f3d0t.github.io/openVoice-releases/releases/<filename>`

## Publish a release

Add the download files under `releases/`, update `index.html`, and replace
`latest.json` with the release metadata required by the app. Commit and push to
`gh-pages` to redeploy. Point the app's updater at the public feed URL above.

For files larger than GitHub's 100 MiB per-file Git limit, upload them as assets
on a GitHub Release in this public repository and use their public download URLs
in the page and feed instead.

## Acceptance status

Owner Pages configuration, HTTPS deployment, and anonymous live verification
are pending. The current page and feed are placeholders.

After deployment, run without credentials:

```sh
curl --fail --show-error --location https://f3d0t.github.io/openVoice-releases/
curl --fail --show-error --location https://f3d0t.github.io/openVoice-releases/latest.json
```

Both URLs must return HTTP 200 over HTTPS. A successful placeholder response
checks public hosting only; release/update acceptance requires real metadata
and a downloadable release.
