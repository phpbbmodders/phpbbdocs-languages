# Czech (cs)

Czech has no terminology audit, glossary, or translation in this project
yet (it is a Tier 2 candidate in phpbbdocs-hugo's
`docs/TODO/todo-language-priority.md`). This page records where the real
Czech language pack lives and what was found when checking it against the
phpBB Language Pack Validation Policy, so the next person starting Czech
does not have to rediscover it. Nothing here is a translator task.

## Who is involved

This project belongs to the [phpbbmodders](https://github.com/phpbbmodders)
organization. Any contact with the Czech pack's maintainers or with
phpBB.com about the points below comes from William Jacoby
([bonelifer](https://github.com/bonelifer)).

## Reference source

Use [R3gi/phpbb-cz](https://github.com/R3gi/phpbb-cz) as the reference for
phpBB's real Czech UI strings when a terminology audit is started (see
phpbbdocs-hugo's `docs/translation-process-prompt.md`). It describes
itself as the official Czech localization, is maintained by the phpBB.cz
community, and was still being updated on 08/23/2026 (release
`2026.08.23.21.07`, pack updated for phpBB 3.3.17).

Do not use the phpBB.com Customisation Database listing for Czech as the
reference: when last checked (09/15/2026) it had not been updated since
January 2017 and was validated only for phpBB 3.2.0.

## Language pack validation status

The pack's own issue,
[R3gi/phpbb-cz#14](https://github.com/R3gi/phpbb-cz/issues/14) ("Adapt to
Language Pack Validation Policy", open since 01/08/2023), tracks getting it
to meet the [Language Pack Validation Policy](https://area51.phpbb.com/docs/dev/3.3.x/language/validation.html)
needed to publish a current revision on phpBB.com.

On 09/21/2026 Claude ran the
[phpBB Translation Validator](https://github.com/phpbb/phpbb-translation-validator)
(`1.6.x` branch, the one that supports 3.3) on the pack's `master` against
the English files of the official phpBB 3.3.17 release zip:

- Result: **5 fatal, 4 error** (24 warnings).
- Email templates used variables from the wrong English template
  (`report_pm_closed`, `short/report_pm`), carried extra links from the
  long templates (`short/bookmark`, `short/topic_notify`), or missed one
  (`newtopic_notify`).
- `install.php` `INTRODUCTION_BODY` had a hardcoded guide link instead of
  `%1$s`; `ucp.php` had an outdated GPL URL and a stray `<br />`.
- The root `README.md` and `SECURITY.md` are not allowed inside a release
  zip; the zip must hold only `ext/`, `language/` and `styles/`.

Claude prepared fixes for all of these; with them the validator reports 0
fatal and 0 error (20 warnings remain). They have not been sent to the
maintainers as of this writing. Update this page once a pull request or
comment exists on R3gi/phpbb-cz. Two things the validator cannot judge
still need a Czech speaker: the Czech `TERMS_OF_USE_CONTENT` and
`PRIVACY_POLICY` have fewer paragraphs than the English, and two sentences
in the fixes are new Czech wording.

To repeat the check, validate a pack folder against the official English
files:

```bash
php translation.php validate cs --package-dir=<dir> --phpbb-version=3.3 --safe-mode
```

`<dir>` holds `en/` (from the phpBB 3.3.17 release zip: `language/en`,
`ext/phpbb/viglink/language/en`, `styles/prosilver/theme/en`) and `cs/`
(the pack). Use the official release zip, not viglink's `master` branch,
as the source for the viglink files.
