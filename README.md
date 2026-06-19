# vs-code-snippets

A collection of personal [VS Code user snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets) for faster web development across Astro, Vue, TypeScript, JavaScript, HTML, and CSS.

## What's included

| File | Snippets for |
| --- | --- |
| `astro.code-snippets` | Astro components, config (aliases, fonts), MDX page starters |
| `vue.code-snippets` | Vue component templates, props/emits, conditional rendering, watchers |
| `ts.code-snippets` | Imports, `fetch` API calls, JSON helpers, Directus access |
| `js.code-snippets` | Common JavaScript utilities |
| `html.code-snippets` | Page structure, SEO/Open Graph/Twitter card starters, common elements |
| `css.code-snippets` | CSS resets and utilities |

## Usage

These are global (user-level) snippet files. To use them:

1. Open VS Code and run **`Snippets: Configure Snippets`** from the Command Palette (`Cmd/Ctrl + Shift + P`).
2. Choose **New Global Snippets file** (or open your user snippets folder directly):
   - **macOS:** `~/Library/Application Support/Code/User/snippets/`
   - **Linux:** `~/.config/Code/User/snippets/`
   - **Windows:** `%APPDATA%\Code\User\snippets\`
3. Copy any `.code-snippets` file from this repo into that folder.
4. Start typing a snippet prefix in a matching file and accept the IntelliSense suggestion.

## Contributing

Issues and pull requests are welcome. To add a snippet, the [snippet-generator.app](https://snippet-generator.app/) tool makes it easy to produce the JSON for a `.code-snippets` file.

## License

[MIT](LICENSE)
