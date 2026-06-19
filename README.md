# vs-code-snippets

A personal [VS Code snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets) library for fast web development — **102 snippets** across React, Vue, Astro, TypeScript, JavaScript, HTML, and CSS.

## The one rule

Every trigger follows the same shape, so you can **derive it instead of memorizing it**:

```
<lang>-<thing you already call it>
```

- **`<lang>`** is one of `react` `vue` `astro` `ts` `js` `html` `css`. Type it first and IntelliSense shows the whole family.
- **`<thing>`** is the real name you already use — the API (`react-usestate`, `vue-computed`), the tag (`html-table`, `html-select`), the property/at-rule (`css-grid`, `css-keyframes`), or a shared concept word.

Shared concept words mean the **same thing in every language**, so once you know one you know them all:

| Concept | Trigger | Examples |
| --- | --- | --- |
| Component | `-comp` | `react-comp`, `vue-comp`, `astro-comp` |
| Function | `-fn` / `-arrow` / `-afn` | `ts-fn`, `js-arrow`, `ts-afn` |
| HTTP request | `-fetch` | `ts-fetch`, `js-fetch`, `astro-fetch` |
| Console log | `-log` | `ts-log`, `js-log` |
| Conditional | `-if` | `react-if`, `vue-if` |
| List render | `-map` / `-for` | `react-map`, `astro-map`, `vue-for` |

After typing a trigger, press <kbd>Tab</kbd> to jump between the placeholders.

## Usage

These are global (user-level) snippet files, so they work in every project:

1. Open the Command Palette (<kbd>Cmd/Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>) and run **`Snippets: Configure Snippets`** → **New Global Snippets file** (or open the folder directly):
   - **macOS:** `~/Library/Application Support/Code/User/snippets/`
   - **Linux:** `~/.config/Code/User/snippets/`
   - **Windows:** `%APPDATA%\Code\User\snippets\`
2. Copy any `.code-snippets` file from this repo into that folder.
3. Start typing a trigger and accept the IntelliSense suggestion.

> Snippets are intentionally **unscoped** (global) so the `ts-`, `html-`, and `css-` families still appear inside Astro and Vue single-file components, where one file mixes several languages. The `<lang>-` prefix does the filtering instead.

## Cheat sheet

<!-- Generated from the snippet files. -->
<details>
<summary><strong>react</strong> &mdash; <code>react.code-snippets</code> (14 snippets)</summary>

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
<summary><strong>vue</strong> &mdash; <code>vue.code-snippets</code> (16 snippets)</summary>

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
<summary><strong>astro</strong> &mdash; <code>astro.code-snippets</code> (10 snippets)</summary>

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
<summary><strong>ts</strong> &mdash; <code>ts.code-snippets</code> (14 snippets)</summary>

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
<summary><strong>js</strong> &mdash; <code>js.code-snippets</code> (13 snippets)</summary>

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
<summary><strong>html</strong> &mdash; <code>html.code-snippets</code> (25 snippets)</summary>

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
<summary><strong>css</strong> &mdash; <code>css.code-snippets</code> (10 snippets)</summary>

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

## Contributing

Issues and pull requests are welcome. New snippets must follow the `<lang>-<name>` rule above. The [snippet-generator.app](https://snippet-generator.app/) tool helps produce the JSON body.

## License

[MIT](LICENSE)
