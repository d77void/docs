# d77void Docs

Community documentation of d77void: what each variant brings and where to
change things. d77void Immutable has its own documentation, in
[immutable-docs](https://github.com/d77void/immutable-docs).

The pages are plain Markdown in [`src/`](src/), readable on GitHub, in any
editor or with `less`. [`src/SUMMARY.md`](src/SUMMARY.md) is the table of
contents and the only place where the order of the chapters is defined.

## Building the website

The website, <https://d77void.github.io/docs/>, is generated with
[mdBook](https://rust-lang.github.io/mdBook/), with its default theme and no
plugins.

```sh
mdbook build    # the site goes to book/
mdbook serve    # preview at http://localhost:3000, rebuilt on every change
```

A link in `SUMMARY.md` to a page that does not exist stops the build
(`create-missing = false` in `book.toml`).

## SourceForge wiki

On every change to `src/` or `wiki/` on `main`, the workflow `wiki.yml` copies
the pages to the [d77void wiki on SourceForge](https://sourceforge.net/p/d77void/wiki/)
as "d77void - <title>", with the index "d77void Docs", and writes the wiki's
entry page "Home" from [`wiki/Home.md`](wiki/Home.md)
(`tools/sf-wiki-sync.py`, with the `SF_WIKI_TOKEN` secret). Pages are written
here only: the wiki copy is overwritten each time. A page removed from
`SUMMARY.md` stays on the wiki until it is deleted there by hand.

## Rules for the content

- Everything is specific to d77void. General Void Linux topics are in the
  [Void Linux Handbook](https://docs.voidlinux.org/).
- Nothing is written from memory: keys, files and behaviour are checked
  against the files the ISOs are built from
  ([d77void/d77void](https://github.com/d77void/d77void)). What is not
  verified yet says so.
- The documentation shows commands; nothing here runs them.

## License

The documentation is licensed under
[Creative Commons Attribution-ShareAlike 4.0 International](LICENSE)
(CC BY-SA 4.0).
