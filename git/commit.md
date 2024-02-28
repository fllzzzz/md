## 格式
Commit message 包括三个部分：Header，Body 和 Footer。可以用下方的格式表示它的结构。

`<type>(<scope>): <subject>// 空一行<body>// 空一行<footer>`

其中，Header 是必需的，Body 和 Footer 可以省略 (默认忽略)，一般我们在 git commit 提交时指定的 -m 参数，就相当于默认指定 Header。 不管是哪一个部分，任何一行都不得超过 72 个字符（或 100 个字符）。这是为了避免自动换行影响美观。

### Header
Header 部分只有一行，包括三个字段：type（必需）、scope（可选）和 subject（必需）。

#### type 
- fix：修补 bug
- feat：新功能（feature）
- docs：文档（documentation）
- style：格式（不影响代码运行的变动）
- refactor：重构（即不是新增功能，也不是修改 bug 的代码变动）
- test：增加测试
- chore：构建过程或辅助工具的变动

feat 和 fix，则该 commit 将肯定出现在 Change log 之中

#### scope
scope 用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视仓库不同而不同。

#### subject
subject 是 commit 目的的简短描述，不超过 50 个字符。

- 以动词开头，使用第一人称现在时，比如 change，而不是 changed 或 changes
- 第一个字母小写
- 结尾不加句号（.）

## Revert
还有一种特殊情况，如果当前 commit 用于撤销以前的 commit，则必须以 revert:开头，后面跟着被撤销 Commit 的 Header。

revert: feat(pencil): add 'graphiteWidth' option

This reverts commit 667ecc1654a317a13331b17617d973392f415f02.

Body 部分的格式是固定的，必须写成 This reverts commit .，其中的 hash 是被撤销 commit 的 SHA 标识符。