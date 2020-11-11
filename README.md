# types

[![Build Status](https://badgen.net/travis/FEMessage/types/main)](https://travis-ci.com/FEMessage/types)
[![NPM Download](https://badgen.net/npm/dm/@femessage/types)](https://www.npmjs.com/package/@femessage/types)
[![NPM Version](https://badgen.net/npm/v/@femessage/types)](https://www.npmjs.com/package/@femessage/types)
[![NPM License](https://badgen.net/npm/license/@femessage/types)](https://github.com/FEMessage/types/blob/main/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/FEMessage/types/pulls)
[![Automated Release Notes by gren](https://img.shields.io/badge/%F0%9F%A4%96-release%20notes-00B2EE.svg)](https://github-tools.github.io/github-release-notes/)

FEMessage basic Typescript type declaration files

[中文文档](./README-zh.md)

## Table of Contents

- [Introduction](#introduction)
- [Install](#install)
- [Usage](#Usage)
- [FAQ](#FAQ)
- [Contributors](#contributors)
- [License](#license)

## Introduction

It is mainly used to store the TypeScript type declaration of the underlying dependency package of the FEMessage component library, so that users of the FEMessage component library can use the type declaration normally regardless of which Fork version of the underlying dependency is installed.

Existing Dependency Library type declarations:
- [Element](https://github.com/ElemeFE/element/tree/dev/types)
- We'll add others as needed...

The type declaration file of this repository is copied from the official package without any modification.

## Install

```bash
yarn add -D @femessage/types
```

[⬆ Back to Top](#table-of-contents)

## Usage

```js
import { Table,Form } from '@femessage/types/element-ui'
```

## FAQ

### What problem was solved?

Add to FEMessage Component Library .d.ts This problem was found during the File: because some components need to rely on the type declaration exported by the Element, FEMessage depends on the official Element, however, it is possible that the user of the FEMessage component library is using another Fork Element (e.g. [@femessage/element-ui](https://github.com/FEMessage/element)), which will cause some FEMessage type declarations to fail.

the solution is to copy the type declaration file of the Element to this repository. FEMessage component libraries depend on the type exported by the Element, so use the type file here.

This means that the type declaration of the FEMessage component will not be affected regardless of whether the FEMessage user installs the official Element or the Fork Element.

Actually, it's just Element as an example. In fact, the UI libraries on which the FEMessage component library depends have this problem, such.

### If the underlying dependency library API is inconsistent with the official API?
However, if the Element installed by FEMessage users is a major change, it will affect API , what should I do?

For example, let's say the user has installed a Fork Element that has made `API` changes to the `el-table` component. The FEMessage component that relies on this repository cannot be used properly because the `API` has become inconsistent, which also causes the type declarations to not match.

If this happens, the solution steps:
1. Copy the `.d.ts` file from the FEMessage component to the project locally.
2. Replace `@femessage/types` in the local `.d.ts` file with the Element path used by the project.

```diff
- import { Table,Form } from '@femessage/types/element-ui'
+ import { Table,Form } from 'element-ui' // node_modules
```

### Which FEMessage components are using it?
The following components are currently in use.
- el-data-table
- el-data-tree
- el-form-renderer

Note: This list may not be updated in time. The actual situation depends on the component's package.json

[⬆ Back to Top](#table-of-contents)

## Contributors

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://4ark.me/"><img src="https://avatars0.githubusercontent.com/u/27952659?v=4?s=100" width="100px;" alt=""/><br /><sub><b>4Ark</b></sub></a><br /><a href="https://github.com/FEMessage/@femessage/types/commits?author=gd4Ark" title="Documentation">📖</a> <a href="#translation-gd4Ark" title="Translation">🌍</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

[⬆ Back to Top](#table-of-contents)

## License

[MIT](./LICENSE)

[⬆ Back to Top](#table-of-contents)
