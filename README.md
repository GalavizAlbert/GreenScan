# GreenScan AI — setup

Frontend: https://galavizalbert.github.io/GreenScan/
Backend: https://greenscan-ai-api.albertogalavizferrari.workers.dev

1. In Cloudflare Workers > greenscan-ai-api > Edit code, replace the default Worker with the contents of `worker.js`. Deploy.
2. Ensure `OPENAI_API_KEY` is configured as a Cloudflare **Secret**, never in GitHub.
3. In GitHub repo GreenScan, upload the updated `index.html` (and manifest and sw.js if missing) to the repository root and commit.
4. Wait for GitHub Pages to publish, hard-refresh, and test camera upload and AI classification.
5. Visiting the Worker URL should return JSON `status: ok`; it does not test OpenAI access.

The Worker accepts JPEG data URLs from the allowed origin `https://galavizalbert.github.io`. Classification is educational, not authoritative; ambiguous or hazardous items require verification. Avoid sending sensitive photos. Add rate limiting and abuse protection before broad public use, as the endpoint consumes paid API credits.
