<div align="center">

![Link Alcove — Find it again.](docs/assets/banner.svg)

### Open-source alternative to Raindrop.io for personal bookmarks and research collections

A quiet home for links worth keeping.

**MIT licensed** · **Own your data** · **No AI service required**

[**Run it →**](#run-it) · [Workflow](#the-workflow) · [MIT license](LICENSE)

</div>

> Local candidate. No cloud sync or page archiving; native browser HTML import acceptance remains pending.

![Link Alcove application workflow](artifacts/demo.png)

*Actual application screenshot with the included public-reference collection.*

## The workflow

**Save a link → organize collections and tags → search → export a portable backup.**

Open-source alternative to **Raindrop.io** for saving and organizing bookmarks. Local-first, with collections, tags, notes, search, JSON backups and browser-compatible HTML export. MIT licensed.

## Run it

Download the source, extract it, and run from its directory:

```sh
python3 -m http.server 5130 --bind 127.0.0.1
```

Open http://127.0.0.1:5130 in a current Chrome, Firefox or Safari. JavaScript modules and safe cross-tab writes require localhost or HTTPS; double-clicking index.html is not supported. No npm install, database or account is needed to use the app. Python is only a local static server.

For a hosted installation, serve `index.html`, `style.css`, `app.js`, `core.js` and `storage.js` from a dedicated HTTPS origin. Keep that origin stable: bookmarks live in the browser's localStorage and do not follow a domain, port or protocol change. This candidate has not yet been verified on public HTTPS.

## First collection

1. Save a complete HTTP(S) URL and title. Add a collection name, comma-separated tags and notes.
2. Search across titles, URLs, tags, collections and notes. Use the collection selector to narrow the list.
3. Edit or delete from a bookmark card. URLs open in a separate tab without sharing a referrer.
4. Export JSON regularly. It preserves all fields and can be imported into another installation. The app supports merge or confirmed replacement; conflicts abort the whole merge.
5. Export browser HTML for the Netscape bookmark interchange format. Folder names, tags and notes are included; downstream browsers may ignore tags or notes. Native browser import compatibility is pending manual acceptance.

To try a non-private collection, import `examples/research.json` under **Import & recovery**. It contains three explicitly curated reference links; nothing is automatically fetched.

## Raindrop.io comparison

[Raindrop.io](https://raindrop.io/) advertises collections, tags and filters, full-text search, archives and collaboration (vendor page reviewed November 15, 2026 IST). This app implements a narrower personal workflow:

| Workflow | Link Alcove |
|---|---|
| Save, edit and delete links | Yes, manual URL/title entry |
| Collections, tags, notes | Yes, flat collection names |
| Search | Saved metadata only; all query words must match |
| Portable backup | JSON import/export; HTML export |
| Cloud sync or collaborative collections | No |
| Full-text page search, screenshots or archived copies | No |
| Browser extension or automatic metadata fetching | No |
| Raindrop export import | Not yet; only this app's JSON schema is accepted |

No affiliation or feature-parity claim. This is a local candidate, not a public release.

## Data safety and limits

No analytics, third-party scripts, favicon calls or automatic requests to saved URLs. Visiting a saved link contacts that site. localStorage is not encrypted; anyone with access to your browser profile can read it. Private browsing and clearing site data can erase the library. Backups may contain private URLs and notes: store them privately.

Libraries are limited to 5,000 links and 2 MB serialized data. Browser quota errors retain the editor draft. Cross-tab writes use Web Locks and revision checks; stale drafts fail with an explanation rather than replacing newer data. A broken saved library is never silently reset: export raw recovery data, then explicitly restore a valid backup. Unsupported browsers refuse unsafe writes.

## Development and verification

Node.js 22+, Python 3, and Chromium for tests:

```sh
npm ci
npm test
npx playwright install --with-deps chromium
# In another terminal, run the local server above.
npm run test:browser
```

Ten unit tests cover URL safety, duplicate canonical URLs, merge conflicts, HTML escaping, malformed backups, quota failure, revision conflicts and recovery. Browser acceptance exercises saving/reloading, search, exports, stale tabs, invalid imports, replacement, deletion and raw-data recovery. CI repeats both suites. Local desktop and mobile screenshots were inspected; hosted acceptance and native browser HTML import remain pending.

The storage adapter was adapted from our MIT-licensed Snippet Cabinet implementation. Runtime code has no third-party dependencies; Playwright is used only for testing.

## Distribution path

Start with a reproducible personal-research workflow: import the included reference collection, add a link, search it, export and restore into a separate browser profile. Publish that demonstrated workflow alongside the independent repository once available. The source and browser HTML export are the concrete integration surface. Native browser import and a public HTTPS demo must be verified before describing those as tested. No directory listing or external PR acceptance is claimed.

## Interface languages

English · Deutsch · Español · 日本語 · 简体中文 · 繁體中文

The interface follows your browser preferences until you choose a language. Switching keeps your draft and saves your choice locally. Translations are bundled; no translation service or telemetry is used. Your content is never translated. Unknown technical diagnostics fall back to English. See [localization notes](I18N.md) for scope and testing.

## Bring your existing bookmarks

Import a browser bookmark HTML export, review the new/duplicate/skipped counts, and add links without replacing saved entries. Nested folder paths become collections; notes and tags are retained when present. Your editor draft stays intact. [Migration guide and supported limits](docs/MIGRATION.md).

![Browser import review in German, with a preserved editor draft](docs/assets/browser-import.png)

## Current verification

See the [26 November audit checkpoint](docs/AUDIT.md) for the verified repository, release links, fresh core test result and remaining deployment/browser gates. Earlier validation records remain dated evidence.
