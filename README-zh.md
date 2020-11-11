# types

[![Build Status](https://badgen.net/travis/FEMessage/types/main)](https://travis-ci.com/FEMessage/types)
[![NPM Download](https://badgen.net/npm/dm/@femessage/types)](https://www.npmjs.com/package/@femessage/types)
[![NPM Version](https://badgen.net/npm/v/@femessage/types)](https://www.npmjs.com/package/@femessage/types)
[![NPM License](https://badgen.net/npm/license/@femessage/types)](https://github.com/FEMessage/types/blob/main/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/FEMessage/types/pulls)
[![Automated Release Notes by gren](https://img.shields.io/badge/%F0%9F%A4%96-release%20notes-00B2EE.svg)](https://github-tools.github.io/github-release-notes/)

FEMessage 基础 TypeScript 类型声明文件

## Table of Contents

- [Introduction](#introduction)
- [Install](#install)
- [Usage](#Usage)
- [FAQ](#FAQ)
- [Contributors](#contributors)
- [License](#license)

## Introduction

主要用于存放 FEMessage 组件库的底层依赖包的 TypeScript 类型声明，让 FEMessage 组件库的使用者无论安装哪个 Fork 版的底层依赖，都能正常使用类型声明。

目前已有的依赖库类型声明：
- [Element](https://github.com/ElemeFE/element/tree/dev/types)
- 后续有需要会增加其它...

此仓库的类型声明文件是由官方包复制出来的，没有作任何修改。

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

### 这个仓库解决了什么问题？

给 FEMessage 组件库增加 `.d.ts` 文件时发现存在这个问题：由于有部分组件需要依赖 Element 导出的类型声明，FEMessage 组件库依赖的是官方的 Element，但有可能 FEMessage 组件库的使用者在使用其它 Fork 出来的 Element（例如 [@femessage/element-ui](https://github.com/FEMessage/element)），这将导致部分 FEMessage 的类型声明无法正常使用。 

综合考虑，解决方案是将 Element 的类型声明文件拷贝到此仓库，FEMessage 组件库需要依赖 Element 导出的类型，则使用这里的类型文件。

这就意味着，无论 FEMessage 的使用者安装的是官方 Element 还是 Fork 的 Element，都不会影响 FEMessage 组件的类型声明。

上面只是拿 Element 举个例子，实际上 FEMessage 组件库所依赖到的 UI 库都会存在该问题，例如：Vant。

### 如果底层依赖库 API 与官方 API 不一致要怎么做？
而如果 FEMessage 的使用者安装的 Element 是一个进行较大改动，影响到 `API`，那应该怎么办呢？

举个例子，假设使用者安装的是一个对 `el-table` 组件进行过 `API` 改动的 Fork Element，由于 `API` 已经不一致，这也导致类型声明对应不上，所以无法正常使用依赖了此仓库的 FEMessage 组件。

如果出现这种情况，解决方案的操作步骤：
1. 将类型声明对应不上的 FEMessage 组件的 `.d.ts` 文件拷贝到项目本地
2. 将本地的 `.d.ts` 文件中的 `@femessage/types` 替换成项目使用的 Element 路径

```diff
- import { Table } from '@femessage/types/element-ui'
+ import { Table } from 'element-ui'
```

### 哪些 FEMessage 组件在依赖这里？
目前有以下组件在依赖：
- el-data-table
- el-data-tree
- el-form-renderer

注意：此列表不一定能够及时更新，实际情况可以看组件的 `package.json`

[⬆ Back to Top](#table-of-contents)

## Contributors

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

[⬆ Back to Top](#table-of-contents)

## License

[MIT](./LICENSE)

[⬆ Back to Top](#table-of-contents)
