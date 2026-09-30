# SafePromiseResolve demo

Open `index.html` directly in Firefox, open the Web Console, and click **Run demo**. No server, dependencies, or build step is required.

The page compares ordinary `Promise.resolve(thenable)` with a thenable returned from `ReadableStream`'s `start()` callback. The `then` getter makes the ordering difference observable. Firefox's `ReadableStreamDefaultController` calls `MaybeSafeResolve` on this result, so builds containing that implementation do not need `dom.promise.experimental_safe_resolve` enabled.

The native console warning additionally requires the warning patch. The page does not fake that warning or attempt to detect it. Repeat the demo to check once-per-document suppression; reload to allow a new warning. Other browsers or older builds may show synchronous stream resolution instead.

## Publish later

1. Create a GitHub repository and push this repository's `main` branch to it.
2. In **Settings → Pages**, choose **Deploy from a branch**, then **main** and **/(root)**.
3. Save. GitHub Pages serves `index.html`; `.nojekyll` keeps the site static.

See [GitHub's publishing-source instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

There are no absolute asset paths, so this works at a GitHub Pages project URL as well as a custom domain. Nothing is published by creating this local repository.
