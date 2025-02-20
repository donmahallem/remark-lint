<!--This file is generated-->

# remark-lint-table-pipe-alignment

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][size-badge]][size]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

Warn when table pipes are not aligned.

## Fix

[`remark-stringify`](https://github.com/remarkjs/remark/tree/HEAD/packages/remark-stringify)
tries to align tables by default.
Pass
[`paddedTable: false`](https://github.com/remarkjs/remark/tree/HEAD/packages/remark-stringify#optionspaddedtable)
to not align cells.

Aligning cells perfectly is impossible as some characters (such as emoji or
Chinese characters) are rendered differently in different browsers,
terminals, and editors.
You can pass your own
[`stringLength`](https://github.com/remarkjs/remark/tree/HEAD/packages/remark-stringify#optionsstringlength)
function to customize how cells are aligned.
In that case, this rule must be turned off.

See [Using remark to fix your Markdown](https://github.com/remarkjs/remark-lint#using-remark-to-fix-your-markdown)
on how to automatically fix warnings for this rule.

## Presets

This rule is included in the following presets:

| Preset | Setting |
| - | - |
| [`remark-preset-lint-markdown-style-guide`](https://github.com/remarkjs/remark-lint/tree/main/packages/remark-preset-lint-markdown-style-guide) | |

## Example

##### `ok.md`

###### In

Note: this example uses [GFM][].

```markdown
| A     | B     |
| ----- | ----- |
| Alpha | Bravo |
```

###### Out

No messages.

##### `not-ok.md`

###### In

Note: this example uses [GFM][].

```markdown
| A | B |
| -- | -- |
| Alpha | Bravo |
```

###### Out

```text
3:9-3:10: Misaligned table fence
3:17-3:18: Misaligned table fence
```

## Install

This package is [ESM only][esm]:
Node 12+ is needed to use it and it must be `imported`ed instead of `required`d.

[npm][]:

```sh
npm install remark-lint-table-pipe-alignment
```

This package exports no identifiers.
The default export is `remarkLintTablePipeAlignment`.

## Use

You probably want to use it on the CLI through a config file:

```diff
 …
 "remarkConfig": {
   "plugins": [
     …
     "lint",
+    "lint-table-pipe-alignment",
     …
   ]
 }
 …
```

Or use it on the CLI directly

```sh
remark -u lint -u lint-table-pipe-alignment readme.md
```

Or use this on the API:

```diff
 import {remark} from 'remark'
 import {reporter} from 'vfile-reporter'
 import remarkLint from 'remark-lint'
 import remarkLintTablePipeAlignment from 'remark-lint-table-pipe-alignment'

 remark()
   .use(remarkLint)
+  .use(remarkLintTablePipeAlignment)
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

[downloads-badge]: https://img.shields.io/npm/dm/remark-lint-table-pipe-alignment.svg

[downloads]: https://www.npmjs.com/package/remark-lint-table-pipe-alignment

[size-badge]: https://img.shields.io/bundlephobia/minzip/remark-lint-table-pipe-alignment.svg

[size]: https://bundlephobia.com/result?p=remark-lint-table-pipe-alignment

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

[gfm]: https://github.com/remarkjs/remark-gfm
