# gh-activity

A tiny zsh script that renders your GitHub contribution graph in the terminal.

![demo](assets/demo.png)

## Requirements

- [`gh`](https://cli.github.com/) — the GitHub CLI, authenticated (`gh auth login`)
- [`jq`](https://jqlang.github.io/jq/) — JSON processor
- `zsh` — shell (uses zsh-specific word splitting)
- A terminal with 256-color support (most modern terminals: kitty, foot, alacritty, wezterm, etc.)

## Install

```sh
curl -o ~/.local/bin/gh-activity https://raw.githubusercontent.com/Alex-T-27/gh-activity/main/gh-activity
chmod +x ~/.local/bin/gh-activity
```

Make sure `~/.local/bin` is on your `PATH`.

## Usage

```sh
gh-activity
```

That's it. Prints the last year of your GitHub contributions as a 7-row grid of colored squares.

> Note: the username is currently hardcoded to `Alex-T-27` in the script. To use it for your own account, edit the `login:` field in the GraphQL query inside `gh-activity`. A username-as-argument version is planned.

## How it works

1. Calls the GitHub GraphQL API via `gh api graphql` to fetch the contribution calendar.
2. Uses `jq` to flatten and `transpose` the weeks-by-days matrix into 7 rows × ~53 columns.
3. Maps each contribution count to a color level (matching GitHub's 5 buckets).
4. Prints each cell as a colored Unicode square with ANSI escape codes.

## License

MIT
