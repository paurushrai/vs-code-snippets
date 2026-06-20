# Setup & sync

How this repo is wired so **one clone** feeds the snippets to **every editor** on the
machine — VS Code, Antigravity, and any other VS Code‑based IDE — without copying files
around.

## The idea

VS Code‑based editors read user snippets from a fixed folder
(`…/<Product>/User/snippets/`) and give you **no setting to relocate it**. So instead of
copying snippets into each editor's folder (and re‑copying on every change), we keep a
single git clone in a neutral location and replace each editor's `snippets` folder with a
**symlink** pointing at that clone.

```
~/Developer/personal/vs-code-snippets        ← the one real clone (git lives here)
        ▲                 ▲
        │ symlink         │ symlink
.../Code/User/snippets    .../Antigravity IDE/User/snippets
```

Result:

- Edit a snippet in **any** editor → the change lands in the clone → `git push` shares it.
- `git pull` on the clone → **every** linked editor updates at once.
- Add a new editor → one more symlink, done.

## Snippet folder locations

Each editor stores user snippets at `…/<Product>/User/snippets/`. The `<Product>` name per
editor:

| Editor          | macOS base                                   | Linux base                  | Windows base            |
| --------------- | -------------------------------------------- | --------------------------- | ----------------------- |
| VS Code         | `~/Library/Application Support/Code`         | `~/.config/Code`            | `%APPDATA%\Code`        |
| Antigravity     | `~/Library/Application Support/Antigravity IDE` | `~/.config/Antigravity IDE` | `%APPDATA%\Antigravity IDE` |
| Cursor          | `~/Library/Application Support/Cursor`       | `~/.config/Cursor`          | `%APPDATA%\Cursor`      |
| Windsurf        | `~/Library/Application Support/Windsurf`     | `~/.config/Windsurf`        | `%APPDATA%\Windsurf`    |
| VSCodium        | `~/Library/Application Support/VSCodium`     | `~/.config/VSCodium`        | `%APPDATA%\VSCodium`    |

> Any VS Code fork works the same way — find its app‑support folder and append
> `/User/snippets`.

## Fresh machine — from scratch

```bash
# 1. Clone once to the canonical location
git clone https://github.com/paurushrai/vs-code-snippets \
  ~/Developer/personal/vs-code-snippets

REPO=~/Developer/personal/vs-code-snippets

# 2. For EACH editor: remove its snippets folder and symlink it to the clone.
#    (Quit the editor first. Back up the folder if it has snippets you want to keep.)

# --- VS Code ---
rm -rf ~/Library/Application\ Support/Code/User/snippets
ln -s "$REPO" ~/Library/Application\ Support/Code/User/snippets

# --- Antigravity ---
rm -rf ~/Library/Application\ Support/Antigravity\ IDE/User/snippets
ln -s "$REPO" ~/Library/Application\ Support/Antigravity\ IDE/User/snippets
```

> The `User/` folder must already exist (it does after the editor has launched once). If it
> doesn't, run the editor once or `mkdir -p` the parent before `ln -s`.

Verify a link resolves to a real snippet file:

```bash
ls -l ~/Library/Application\ Support/Code/User/snippets        # -> .../vs-code-snippets
ls    ~/Library/Application\ Support/Code/User/snippets/react.code-snippets
```

Reload the editor (Command Palette → **Developer: Reload Window**) and the snippets are live.

## Daily sync

```bash
cd ~/Developer/personal/vs-code-snippets
git pull            # get snippets edited on another machine
git add -A && git commit -m "..." && git push   # share edits made here
```

No per‑editor step — the symlinks mean every editor already sees the clone's current state.

## Adding another editor later

```bash
REPO=~/Developer/personal/vs-code-snippets
rm -rf ~/Library/Application\ Support/<Product>/User/snippets
ln -s "$REPO" ~/Library/Application\ Support/<Product>/User/snippets
```

## If a snippet folder path changes

An editor rename/update can change `<Product>` (e.g. the folder is recreated, or the app is
renamed), which **breaks or replaces** the symlink. Fix = just point a fresh symlink at the
clone again:

```bash
REPO=~/Developer/personal/vs-code-snippets
NEW=~/Library/Application\ Support/<New Product Name>/User/snippets
rm -rf "$NEW"            # removes a broken link or an editor‑recreated empty folder
ln -s "$REPO" "$NEW"
```

If instead you want to **move the clone itself** (e.g. out of `~/Developer/personal`):

```bash
mv ~/Developer/personal/vs-code-snippets ~/new/location/vs-code-snippets
# Then re‑create every editor's symlink to the new path (a symlink to the old path is
# now dangling):
REPO=~/new/location/vs-code-snippets
for P in "Code" "Antigravity IDE"; do
  L=~/Library/Application\ Support/"$P"/User/snippets
  rm -rf "$L"; ln -s "$REPO" "$L"
done
```

## Troubleshooting

- **Snippets not showing up** — confirm the path is a symlink, not a folder:
  `ls -ld ~/Library/Application\ Support/Code/User/snippets` should print `… -> …/vs-code-snippets`.
  If it's a plain directory, an editor recreated it — re‑run the `rm -rf` + `ln -s` for it.
- **Dangling link** (`ls -l` shows the target in red / `No such file`) — the clone moved or
  was deleted; re‑clone or re‑point per the section above.
- **Scope‑restricted snippets silent** — some (`prisma`, `dockercompose`) need the matching
  language extension installed in that editor to activate.
- **Don't put the clone inside an editor's config dir** — an editor reset would wipe your
  repo. Keep it neutral (here: `~/Developer/personal`).
