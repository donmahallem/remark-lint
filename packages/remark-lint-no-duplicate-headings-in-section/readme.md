<!--This file is generated-->

# remark-lint-no-duplicate-headings-in-section

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][size-badge]][size]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

Warn when duplicate headings are found, but only when on the same level,
“in” the same section.

## Presets

This rule is not included in any default preset

## Example

##### `ok.md`

###### In

```markdown
## Alpha

### Bravo

## Charlie

### Bravo

### Delta

#### Bravo

#### Echo

##### Bravo
```

###### Out

No messages.

##### `not-ok.md`

###### In

```markdown
## Foxtrot

### Golf

### Golf
```

###### Out

```text
5:1-5:9: Do not use headings with similar content per section (3:1)
```

##### `not-ok-tolerant-heading-increment.md`

###### In

```markdown
# Alpha

#### Bravo

###### Charlie

#### Bravo

###### Delta
```

###### Out

```text
7:1-7:11: Do not use headings with similar content per section (3:1)
```

## Install

This package is [ESM only][esm]:
Node 12+ is needed to use it and it must be `imported`ed instead of `required`d.

[npm][]:

```sh
npm install remark-lint-no-duplicate-headings-in-section
```

This package exports no identifiers.
The default export is `remarkLintNoDuplicateHeadingsInSection`.

## Use

You probably want to use it on the CLI through a config file:

```diff
 …
 "remarkConfig": {
   "plugins": [
     …
     "lint",
+    "lint-no-duplicate-headings-in-section",
     …
   ]
 }
 …
```

Or use it on the CLI directly

```sh
remark -u lint -u lint-no-duplicate-headings-in-section readme.md
```

Or use this on the API:

```diff
 import {remark} from 'remark'
 import {reporter} from 'vfile-reporter'
 import remarkLint from 'remark-lint'
 import remarkLintNoDuplicateHeadingsInSection from 'remark-lint-no-duplicate-headings-in-section'

 remark()
   .use(remarkLint)
+  .use(remarkLintNoDuplicateHeadingsInSection)
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

[downloads-badge]: https://img.shields.io/npm/dm/remark-lint-no-duplicate-headings-in-section.svg

[downloads]: https://www.npmjs.com/package/remark-lint-no-duplicate-headings-in-section

[size-badge]: https://img.shields.io/bundlephobia/minzip/remark-lint-no-duplicate-headings-in-section.svg

[size]: https://bundlephobia.com/result?p=remark-lint-no-duplicate-headings-in-section

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
