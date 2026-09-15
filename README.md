# phpbbdocs-languages

Canonical PO translation catalogs for
[phpbbdocs-hugo](https://github.com/phpbbmodders/phpbbdocs-hugo)'s
gettext-based translation pipeline. This repository holds only
translation data — the English source, build tooling, and generated
Hugo site all live in phpbbdocs-hugo; see that project's
`translations.sh` and `docs/phpbb-gettext-translation-plan.md` for the
full workflow.

## Layout

```text
<lang>/
├── language.toml        # code, name, native_name, locale, status
└── documentation/
    └── <chapter>.po      # one catalog per end-user chapter
metadata/
└── source.json           # per-language recorded upstream source revision
terminology/               # shared translator reference (not yet populated)
```

Generated POT templates and reconstructed output are never committed
here — see phpbbdocs-hugo's `translation.conf`/`.gitignore` for where
those live as build artifacts.

## Contributing

Contributions are welcome!

- **Bug reports**: [Open an issue](https://github.com/phpbbmodders/phpbbdocs-languages/issues).
- **Everything else** (questions, feature requests, ideas, general discussion): open an issue in [phpbbdocs-hugo](https://github.com/phpbbmodders/phpbbdocs-hugo) instead — this repository is data-only and doesn't run its own discussion space.
- Pull requests updating a `.po` catalog are welcome; run `./translations.sh check <lang>` in phpbbdocs-hugo before submitting.

## License

This entire repository — the PO translation catalogs, being translations of phpBB's own documentation content &copy; phpBB Limited — is licensed under the [CC Attribution-NonCommercial-ShareAlike 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/) license, matching phpbbdocs-hugo and phpBB's own upstream documentation repository. See [LICENSE](LICENSE).
