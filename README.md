# Localix Community

Mini apps and plugins that people publish in their own repositories, listed for
[Localix](https://github.com/rsaryev/localix) and Claude Code.

This repository holds no code. It is two lists:

| File                                 | Lists     | Each entry names                                                              |
| ------------------------------------ | --------- | ----------------------------------------------------------------------------- |
| `.localix-mini-app/marketplace.json` | Mini apps | The author's own marketplace: a GitHub repository's release, or an address.   |
| `.claude-plugin/marketplace.json`    | Plugins   | The repository the plugin lives in, as a Claude Code marketplace does.        |

Both have the shape of a Claude Code `marketplace.json`: a `name`, an `owner`, `metadata`, and
entries with a `name`, a `description` and a `source`. Each change to the mini app list is released,
signed, as `mini-app-marketplace.json`: that release is what Localix reads.

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
- A mini app is read from its author's marketplace, which says what it is. That marketplace's
  signature decides how it updates: **Signed** apps update on their own, **Not signed** apps update
  when you choose **Update**, and an app whose **Signature changed** installs or updates nothing.
- A mini app is known as `<name>@localix-community`, never as one of Localix's own
  (`<name>@localix`), and updates only from the marketplace it was installed from.
- Nothing here is featured, installed on its own or suggested: Localix takes no curation from this
  list.

What the list says about an entry (its description, category, homepage) fills in only what the
author's own marketplace leaves out.

## Adding yours

See [CONTRIBUTING.md](CONTRIBUTING.md). In short: publish the app from its own repository, then open
a pull request that adds one entry.

## Reporting a problem

Open an issue naming the entry. An entry that misleads, harms people or no longer resolves is
removed.
