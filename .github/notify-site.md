# Cross-repository website notification

`notify-site.yml` runs only when a push to `main` changes one of the content directories the website indexes: `wiki/`, `competition-rules/`, `technical-sharing/`, `scripts/`, `reading-list/`, `network-open-source/`. Changes confined to `README.md`, `assets/`, `recommended-papers/` or `.github/` do not trigger it. The workflow sends a `wiki-updated` `repository_dispatch` event to `LocoWiki/LocoWiki.github.io`, and the website then refreshes both the remote document index and the contributors cache in one run.

Before enabling it, configure `LOCO_WIKI_SITE_DISPATCH_TOKEN` in this repository's Actions secrets. Use a fine-grained personal access token or GitHub App token scoped only to `LocoWiki/LocoWiki.github.io`, with permission to dispatch repository events.
