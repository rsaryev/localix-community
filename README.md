# Localix Community

Mini apps and plugins that people publish in their own repositories, listed for
[Localix](https://github.com/rsaryev/localix) and Claude Code.

This repository holds no code. It is two lists:

| File                              | Lists      | Each entry names                                                         |
| --------------------------------- | ---------- | ------------------------------------------------------------------------ |
| `.mini-app/marketplace.json`      | Mini apps  | The author's own catalog: a GitHub repository's release, or an address.  |
| `.claude-plugin/marketplace.json` | Plugins    | The repository the plugin lives in, as a Claude Code marketplace does.   |

Both have the shape of a Claude Code `marketplace.json`: a `name`, an `owner`, `metadata`, and
entries with a `name`, a `description` and a `source`.

## Using it

**Localix** lists it from the start: open the Store, and the apps and plugins here show under
**Localix Community**.

**Claude Code** reads its plugins:

```bash
claude plugin marketplace add rsaryev/localix-community
claude plugin install <plugin>@localix-community
```

## What Localix vouches for

Nothing here. Every entry is its author's, and Localix treats it that way:

- Installing asks first, and says the publisher is not verified.
- A mini app is read from its author's catalog, which says what it is. That catalog's signature
  decides how it updates: **Signed** apps update on their own, **Not signed** apps update when you
  choose **Update**, and an app whose **Signature changed** installs nothing until you decide.
- A mini app updates only from the catalog it was installed from, and never takes the name of an app
  in Localix's own catalog.
- Nothing here is featured or recommended.

What the list says about an entry (its description, category, homepage) fills in only what the
author's own catalog or manifest leaves out.

## Adding yours

See [CONTRIBUTING.md](CONTRIBUTING.md). In short: publish the app from its own repository, then open
a pull request that adds one entry.

## Reporting a problem

Open an issue naming the entry. An entry that misleads, harms people or no longer resolves is
removed.
