# Adding an entry

Open a pull request that adds one entry, in alphabetical order by `name`. The checks run on it; a
maintainer reviews and merges it.

## A mini app

1. Publish it from its own public repository with the Localix authoring plugin
   (`/mini-app-authoring:publish`). Each tag `v<version>` then releases its marketplace, at
   `https://github.com/<owner>/<repo>/releases/latest/download/mini-app-marketplace.json`. Signing
   it (`mini-app keygen` and the `MINI_APP_SIGNING_KEY` secret) lets installed copies update on their
   own.
2. Add it to `.localix-mini-app/marketplace.json`:

   ```json
   {
     "name": "notes",
     "source": { "source": "github", "repo": "ada/notes" },
     "description": "Notes beside every chat, kept by you and the agent.",
     "category": "utilities",
     "homepage": "https://github.com/ada/notes"
   }
   ```

   `name` is the app's name in its `.localix-mini-app/mini-app.json`. `source` is `github` (`repo`:
   the repository whose latest release publishes its marketplace) or `url` (`url`: the released
   marketplace's `https://` address). `category`, `displayName` and `homepage` are optional;
   `featured`, `installByDefault`, `suggestFor` and `collections` are refused here.

3. Check it locally with the authoring plugin's CLI:

   ```bash
   mini-app marketplace validate --fetch
   ```

## A plugin

Add it to `.claude-plugin/marketplace.json` as a Claude Code marketplace entry whose `source` names
its repository, pinned to a commit:

```json
{
  "name": "formatter",
  "description": "Formats the files Claude edits, with the formatter the project already uses.",
  "source": {
    "source": "git-subdir",
    "url": "https://github.com/ada/tools.git",
    "path": "plugins/formatter",
    "ref": "v1.0.0",
    "sha": "<40-character commit>"
  },
  "homepage": "https://github.com/ada/tools"
}
```

`source` may also be `github` (`repo`) or `url` (a git URL), with `ref` and `sha`. Check it with
`claude plugin validate .` and `claude plugin validate --strict <the plugin's folder>`.

## The rules

- **One entry per name.** Names are unique and sorted. A mini app here is `<name>@localix-community`,
  so it never stands in for one of Localix's own.
- **A description of 10 to 2000 characters** that says what it does, with no invisible characters.
- **`https://` sources only**, on GitHub, GitLab or Bitbucket for plugins.
- **It works as described** and does nothing it does not say. It does not collect data it does not
  need or send it anywhere unannounced.
- **It stays reachable.** An entry whose repository or marketplace disappears is removed.
- **Taking one back.** An entry that harms people is revoked rather than deleted
  (`"revoked": { "reason": "…" }`): installed copies stop, and say why.
