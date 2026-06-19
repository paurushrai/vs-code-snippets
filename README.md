# vs-code-snippets

A personal [VS Code snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets) library for fast full-stack development — **185 snippets** spanning frontend (React, Vue, Astro, TS, JS, HTML, CSS, Tailwind), backend & data (Node/Next.js, SQL, Prisma/Drizzle/Mongo, Zod, Python, Rust), and DevOps tooling (Docker, GitHub Actions, Bash, testing, Markdown, dotfiles, regex).

## The one rule

Every trigger follows the same shape, so you can **derive it instead of memorizing it**:

```
<lang>-<thing you already call it>
```

- **`<lang>`** is the language/tool: `react` `vue` `astro` `ts` `js` `html` `css` `tw` `node` `sql` `db` `zod` `py` `rust` `docker` `yml` `sh` `test` `md` `regex`. Type it first and IntelliSense shows the whole family.
- **`<thing>`** is the real name you already use — the API (`react-usestate`, `vue-computed`), the tag (`html-table`), the property/at-rule (`css-grid`, `css-keyframes`), the keyword (`sql-select`, `rust-struct`), or a shared concept word.

Shared concept words mean the **same thing in every language**, so once you know one you know them all:

| Concept | Trigger | Examples |
| --- | --- | --- |
| Component | `-comp` | `react-comp`, `vue-comp`, `astro-comp` |
| Function | `-fn` / `-arrow` / `-afn` | `ts-fn`, `js-arrow`, `py-fn`, `rust-fn` |
| HTTP request | `-fetch` / `-route` | `ts-fetch`, `js-fetch`, `node-route-get` |
| Console log | `-log` | `ts-log`, `js-log` |
| Conditional | `-if` | `react-if`, `vue-if`, `sh-if` |
| List / loop | `-map` / `-for` | `react-map`, `vue-for`, `sh-for` |
| Test | `test-*` | `test-it`, `test-rtl`, `py-pytest`, `rust-test` |

After typing a trigger, press <kbd>Tab</kbd> to jump between the placeholders.

### Global vs. scoped

- **Frontend files** (`react` `vue` `astro` `ts` `js` `html` `css` `tw`) and a few cross-cutting ones (`regex`, `dotfiles`) are **global** — they appear everywhere. That's deliberate: Astro and Vue single-file components mix TS + HTML + CSS in one file, so you want those families available together.
- **Backend, data, and DevOps files** (`node` `sql` `db` `zod` `py` `rust` `docker` `yml` `sh` `test` `md`) are **`scope`-restricted** to their language, so `sql-`/`py-`/`go-` suggestions never pollute autocomplete in unrelated files.

> **Tailwind note:** `tw-*` snippets expand to bare class strings (e.g. `flex items-center justify-center`) so they drop into any `class`/`className`/`@apply`. Inside a `class="..."` attribute you may need <kbd>Ctrl</kbd>+<kbd>Space</kbd> to surface them past Tailwind IntelliSense.

## Usage

These are global (user-level) snippet files, so they work in every project:

1. Open the Command Palette (<kbd>Cmd/Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>) and run **`Snippets: Configure Snippets`** → **New Global Snippets file** (or open the folder directly):
   - **macOS:** `~/Library/Application Support/Code/User/snippets/`
   - **Linux:** `~/.config/Code/User/snippets/`
   - **Windows:** `%APPDATA%\Code\User\snippets\`
2. Copy the `.code-snippets` files you want into that folder.
3. Start typing a trigger and accept the IntelliSense suggestion.

> Some scopes (`prisma`, `dockercompose`) require the matching language extension to be installed for the snippet to activate in those files.

## Cheat sheet

<!-- Generated from the snippet files. -->
### Frontend

<details>
<summary><strong>react</strong> &mdash; <code>react.code-snippets</code> (14) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `react-comp` | Function component with a typed props interface |
| `react-comp-bare` | Minimal function component without props |
| `react-usestate` | useState hook with typed state |
| `react-useeffect` | useEffect hook with a dependency array |
| `react-useeffect-clean` | useEffect hook with a cleanup function |
| `react-useref` | useRef hook with an element type |
| `react-usecontext` | Consume a context value |
| `react-usereducer` | useReducer hook |
| `react-usememo` | Memoize an expensive computed value |
| `react-usecallback` | Memoize a callback |
| `react-hook` | Custom hook scaffold |
| `react-provider` | Typed context with a provider and a safe consumer hook |
| `react-map` | Render a list with .map() and a key |
| `react-if` | Short-circuit conditional rendering |

</details>

<details>
<summary><strong>vue</strong> &mdash; <code>vue.code-snippets</code> (16) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `vue-comp` | Single-file component with script setup |
| `vue-comp-ts` | Single-file component with TypeScript script setup |
| `vue-comp-starter` | Component starter with nested wrapper markup |
| `vue-props` | defineProps declaration |
| `vue-emits` | defineEmits declaration |
| `vue-ref` | Reactive ref |
| `vue-reactive` | Reactive object |
| `vue-computed` | Computed property |
| `vue-watch` | Watch a reactive source |
| `vue-watch-log` | Watch a source and log it with styling |
| `vue-mounted` | onMounted lifecycle hook |
| `vue-if` | Conditional rendering with v-if/v-else |
| `vue-elif` | Conditional rendering with v-else-if |
| `vue-show` | Toggle visibility with v-show |
| `vue-for` | List rendering with v-for and a key |
| `vue-model` | Two-way binding with v-model |

</details>

<details>
<summary><strong>astro</strong> &mdash; <code>astro.code-snippets</code> (10) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `astro-comp` | Minimal component with frontmatter and markup |
| `astro-comp-starter` | Component starter with nested wrapper markup |
| `astro-props` | Typed Props interface with Astro.props |
| `astro-fetch` | Top-level await fetch inside frontmatter |
| `astro-paths` | getStaticPaths for dynamic routes |
| `astro-map` | Render a list with .map() |
| `astro-slot` | Slot for child content |
| `astro-import` | Named import inside frontmatter |
| `astro-mdx` | MDX page frontmatter starter |
| `astro-head` | Import styles and include fonts/analytics |

</details>

<details>
<summary><strong>ts</strong> &mdash; <code>ts.code-snippets</code> (14) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `ts-import` | Default import statement |
| `ts-import-named` | Named import statement |
| `ts-log` | Log a message to the console |
| `ts-fn` | Typed function declaration |
| `ts-arrow` | Typed arrow function |
| `ts-afn` | Async function with a typed Promise return |
| `ts-fetch` | Typed fetch helper with error handling |
| `ts-fetch-auth` | Fetch with a bearer auth header (token from a variable) |
| `ts-try` | try/catch block |
| `ts-interface` | TypeScript interface |
| `ts-type` | TypeScript type alias |
| `ts-enum` | TypeScript string enum |
| `ts-stringify` | Serialize a value to a JSON string |
| `ts-parse` | Parse a JSON string |

</details>

<details>
<summary><strong>js</strong> &mdash; <code>js.code-snippets</code> (13) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `js-log` | Console log with CSS styling and a data value |
| `js-fn` | Function declaration |
| `js-arrow` | Arrow function |
| `js-afn` | Async function |
| `js-foreach` | Array forEach loop |
| `js-map` | Array map |
| `js-filter` | Array filter |
| `js-reduce` | Array reduce |
| `js-fetch` | Fetch with async/await and error handling |
| `js-event` | Attach an event listener |
| `js-timeout` | Run code after a delay |
| `js-interval` | Run code on an interval |
| `js-destructure` | Destructure properties from an object |

</details>

<details>
<summary><strong>html</strong> &mdash; <code>html.code-snippets</code> (25) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `html-doc` | Full HTML5 document boilerplate |
| `html-section` | Nested container/content section wrapper |
| `html-head` | Stylesheet, script, fonts and analytics includes |
| `html-seo-basic` | Title, favicon, canonical and charset |
| `html-seo-meta` | General SEO meta tags |
| `html-seo-og` | Open Graph meta tags for social sharing |
| `html-seo-twitter` | Twitter card meta tags |
| `html-seo-robots` | Crawler and caching instruction meta tags |
| `html-css` | Link a stylesheet |
| `html-js` | Link a script file |
| `html-ol` | Ordered list |
| `html-ul` | Unordered list |
| `html-nav` | Navigation bar with anchor links |
| `html-button` | Anchor styled as a button |
| `html-form` | Form with a labelled input and submit button |
| `html-input` | Labelled input field |
| `html-table` | Table with header and body rows |
| `html-img` | Image tag with common attributes |
| `html-figure` | Figure with an image and caption |
| `html-picture` | Responsive picture with a WebP source |
| `html-video` | Video element with a source |
| `html-cols` | Two side-by-side content blocks |
| `html-mail` | Mailto link |
| `html-select` | Select dropdown with options |
| `html-details` | Native disclosure/accordion element |

</details>

<details>
<summary><strong>css</strong> &mdash; <code>css.code-snippets</code> (10) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `css-normalize` | Normalize CSS |
| `css-reset` | Minimal box-sizing and margin/padding reset |
| `css-center` | Center children with flexbox |
| `css-flex` | Flexbox container |
| `css-grid` | Auto-fit responsive grid |
| `css-vars` | Custom properties on :root |
| `css-media` | Media query breakpoint |
| `css-transition` | CSS transition shorthand |
| `css-keyframes` | Keyframes animation block |
| `css-clamp` | Fluid font-size using clamp() |

</details>

<details>
<summary><strong>tailwind</strong> &mdash; <code>tailwind.code-snippets</code> (19) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `tw-center` | Center children horizontally and vertically with flex |
| `tw-center-abs` | Center absolutely within a relative parent |
| `tw-stack` | Vertical flex column with gap |
| `tw-row` | Horizontal flex row, vertically centered, with gap |
| `tw-between` | Push children apart with justify-between |
| `tw-grid` | Responsive grid: 1 / 2 / N columns |
| `tw-container` | Centered max-width container with responsive padding |
| `tw-section` | Vertical section padding |
| `tw-card` | Card surface with border, padding and shadow |
| `tw-btn` | Primary button with hover, focus-ring and disabled states |
| `tw-input` | Text input with focus ring |
| `tw-badge` | Pill-shaped badge / tag |
| `tw-hero` | Full-height centered hero container |
| `tw-aspect` | Aspect-ratio media container |
| `tw-truncate` | Truncate overflowing text with an ellipsis |
| `tw-clamp` | Clamp text to N lines |
| `tw-skeleton` | Animated loading skeleton bar |
| `tw-sticky` | Sticky, blurred top header bar |
| `tw-overlay` | Full-screen modal backdrop, centered content |

</details>

### Backend & data

<details>
<summary><strong>node</strong> &mdash; <code>node.code-snippets</code> (7)</summary>

| Trigger | Inserts |
| --- | --- |
| `node-route-get` | Next.js App Router GET route handler |
| `node-route-post` | Next.js App Router POST route handler |
| `node-action` | Next.js server action reading FormData |
| `node-middleware` | Next.js middleware with a matcher config |
| `node-env` | Read a required environment variable with a guard |
| `node-async` | Async function wrapped in try/catch |
| `node-script` | Self-invoking async main with error exit |

</details>

<details>
<summary><strong>sql</strong> &mdash; <code>sql.code-snippets</code> (8)</summary>

| Trigger | Inserts |
| --- | --- |
| `sql-select` | Parameterized SELECT with a WHERE clause |
| `sql-insert` | Parameterized INSERT with RETURNING |
| `sql-update` | Parameterized UPDATE |
| `sql-delete` | Parameterized DELETE |
| `sql-join` | SELECT with a JOIN |
| `sql-table` | CREATE TABLE with identity PK and timestamp |
| `sql-index` | CREATE INDEX |
| `sql-cte` | Common table expression (WITH) |

</details>

<details>
<summary><strong>db</strong> &mdash; <code>db.code-snippets</code> (4)</summary>

| Trigger | Inserts |
| --- | --- |
| `db-prisma-model` | Prisma model with id and timestamps |
| `db-prisma-query` | Prisma findMany query |
| `db-drizzle` | Drizzle ORM select query |
| `db-mongo` | MongoDB find query |

</details>

<details>
<summary><strong>zod</strong> &mdash; <code>zod.code-snippets</code> (3)</summary>

| Trigger | Inserts |
| --- | --- |
| `zod-schema` | Zod object schema |
| `zod-infer` | Infer a TypeScript type from a Zod schema |
| `zod-parse` | Safely parse and validate external input |

</details>

<details>
<summary><strong>py</strong> &mdash; <code>py.code-snippets</code> (6)</summary>

| Trigger | Inserts |
| --- | --- |
| `py-main` | Script entrypoint with __main__ guard |
| `py-fn` | Typed function with a docstring |
| `py-afn` | Async function |
| `py-dataclass` | Dataclass with typed fields |
| `py-fastapi` | FastAPI path operation |
| `py-pytest` | Pytest test with arrange/act/assert |

</details>

<details>
<summary><strong>rust</strong> &mdash; <code>rust.code-snippets</code> (5)</summary>

| Trigger | Inserts |
| --- | --- |
| `rust-main` | Main function |
| `rust-fn` | Function with a Result return type |
| `rust-struct` | Struct with derives |
| `rust-match` | match expression |
| `rust-test` | Unit test function |

</details>

### DevOps & tooling

<details>
<summary><strong>docker</strong> &mdash; <code>docker.code-snippets</code> (3)</summary>

| Trigger | Inserts |
| --- | --- |
| `docker-node` | Multi-stage Node Dockerfile (deps/build/runner) |
| `docker-compose` | Docker Compose service block |
| `docker-ignore` | .dockerignore contents |

</details>

<details>
<summary><strong>yml</strong> &mdash; <code>yml.code-snippets</code> (2)</summary>

| Trigger | Inserts |
| --- | --- |
| `yml-gha` | GitHub Actions CI workflow for Node |
| `yml-gha-deploy` | GitHub Actions deploy job using a repository secret |

</details>

<details>
<summary><strong>sh</strong> &mdash; <code>sh.code-snippets</code> (5)</summary>

| Trigger | Inserts |
| --- | --- |
| `sh-script` | Bash shebang with strict mode (set -euo pipefail) |
| `sh-fn` | Bash function reading a positional argument |
| `sh-if` | Exit if a required variable is unset or empty |
| `sh-for` | Loop over an array, quoting expansion |
| `sh-case` | Bash case statement |

</details>

<details>
<summary><strong>test</strong> &mdash; <code>test.code-snippets</code> (8)</summary>

| Trigger | Inserts |
| --- | --- |
| `test-describe` | Test suite (Vitest/Jest) |
| `test-it` | Single test case with arrange/act/assert |
| `test-async` | Async test case |
| `test-expect` | Assertion |
| `test-mock` | Mock function (Vitest; use jest.fn for Jest) |
| `test-beforeeach` | Run setup before each test |
| `test-rtl` | Render a component and query with React Testing Library |
| `test-pw` | Playwright end-to-end test |

</details>

<details>
<summary><strong>md</strong> &mdash; <code>md.code-snippets</code> (5)</summary>

| Trigger | Inserts |
| --- | --- |
| `md-readme` | Project README skeleton |
| `md-pr` | PR description: what / why / how to test |
| `md-table` | Markdown table |
| `md-code` | Fenced code block |
| `md-details` | Collapsible details/summary block |

</details>

<details>
<summary><strong>dotfiles</strong> &mdash; <code>dotfiles.code-snippets</code> (3) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `gitignore-node` | Node project .gitignore |
| `env-example` | .env.example template (no real values) |
| `editorconfig` | .editorconfig defaults |

</details>

<details>
<summary><strong>regex</strong> &mdash; <code>regex.code-snippets</code> (5) · _global_</summary>

| Trigger | Inserts |
| --- | --- |
| `regex-email` | Email address pattern |
| `regex-slug` | URL slug (lowercase, hyphen-separated) |
| `regex-uuid` | UUID v1-v5 pattern |
| `regex-ipv4` | IPv4 address pattern |
| `regex-hex` | Hex color code (#rgb or #rrggbb) |

</details>


## Contributing

Issues and pull requests are welcome. New snippets must follow the `<lang>-<name>` rule above, and language-specific families should set `scope`. The [snippet-generator.app](https://snippet-generator.app/) tool helps produce the JSON body.

## License

[MIT](LICENSE)
