<!--This file is generated-->

# remark-lint-no-missing-blank-lines

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][size-badge]][size]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

Warn when missing blank lines before block content (and frontmatter
content).

This rule can be configured to allow tight list items without blank lines
between their contents by passing `{exceptTightLists: true}` (default:
`false`).

## Fix

[`remark-stringify`](https://github.com/remarkjs/remark/tree/HEAD/packages/remark-stringify)
always uses one blank line between blocks if possible, or two lines when
needed.
The style of the list items persists.

See [Using remark to fix your Markdown](https://github.com/remarkjs/remark-lint#using-remark-to-fix-your-markdown)
on how to automatically fix warnings for this rule.

## Presets

This rule is not included in any default preset

## Example

##### `ok.md`

###### In

```markdown
# Foo

## Bar

- Paragraph

  + List.

Paragraph.
```

###### Out

No messages.

##### `not-ok.md`

###### In

```markdown
# Foo
## Bar

- Paragraph
  + List.

Paragraph.
```

###### Out

```text
2:1-2:7: Missing blank line before block node
5:3-5:10: Missing blank line before block node
```

##### `tight.md`

When configured with `{ exceptTightLists: true }`.

###### In

```markdown
# Foo
## Bar

- Paragraph
  + List.

Paragraph.
```

###### Out

```text
2:1-2:7: Missing blank line before block node
```

## Install

This package is [ESM only][esm]:
Node 12+ is needed to use it and it must be `imported`ed instead of `required`d.

[npm][]:

```sh
npm install remark-lint-no-missing-blank-lines
```

This package exports no identifiers.
The default export is `remarkLintNoMissingBlankLines`.

## Use

You probably want to use it on the CLI through a config file:

```diff
 …
 "remarkConfig": {
   "plugins": [
     …
     "lint",
+    "lint-no-missing-blank-lines",
     …
   ]
 }
 …
```

Or use it on the CLI directly

```sh
remark -u lint -u lint-no-missing-blank-lines readme.md
```

Or use this on the API:

```diff
 import {remark} from 'remark'
 import {reporter} from 'vfile-reporter'
 import remarkLint from 'remark-lint'
 import remarkLintNoMissingBlankLines from 'remark-lint-no-missing-blank-lines'

 remark()
   .use(remarkLint)
+  .use(remarkLintNoMissingBlankLines)
   .process('_Emphasis_ and **importance**')
   .then((file) => {
     console.error(reporter(file))
   })
```

## Contribute

See [`contributing.md`][contributing] in [`remarkjs/.github`][health] for ways
to get started.
See [`support.md`][support] for ways to get help.

This project has a [code of conduct][coc].
By interacting with this repository, organization, or community you agree to
abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]

[build-badge]: https://github.com/remarkjs/remark-lint/workflows/main/badge.svg

[build]: https://github.com/remarkjs/remark-lint/actions

[coverage-badge]: https://img.shields.io/codecov/c/github/remarkjs/remark-lint.svg

[coverage]: https://codecov.io/github/remarkjs/remark-lint

[downloads-badge]: https://img.shields.io/npm/dm/remark-lint-no-missing-blank-lines.svg

[downloads]: https://www.npmjs.com/package/remark-lint-no-missing-blank-lines

[size-badge]: https://img.shields.io/bundlephobia/minzip/remark-lint-no-missing-blank-lines.svg

[size]: https://bundlephobia.com/result?p=remark-lint-no-missing-blank-lines

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[chat-badge]: https://img.shields.io/badge/chat-discussions-success.svg

[chat]: https://github.com/remarkjs/remark/discussions

[esm]: https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c

[npm]: https://docs.npmjs.com/cli/install

[health]: https://github.com/remarkjs/.github

[contributing]: https://github.com/remarkjs/.github/blob/HEAD/contributing.md

[support]: https://github.com/remarkjs/.github/blob/HEAD/support.md

[coc]: https://github.com/remarkjs/.github/blob/HEAD/code-of-conduct.md

[license]: https://github.com/remarkjs/remark-lint/blob/main/license

[author]: https://wooorm.com
