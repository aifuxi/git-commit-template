# 这是一个 git commit 提交模板

## 1. 全局安装 commitizen 工具

```shell
# npm全局安装commitizen
$ npm install commitizen -g

# 或者用yarn
$ yarn global add commitizen
```

## 2. 利用`cz-conventional-changelog`初始化项目

```shell
# npm
$ commitizen init cz-conventional-changelog --save-dev --save-exact

# 或者yarn
$ commitizen init cz-conventional-changelog --yarn --dev --exact
```

执行完成后，`package.json`文件后面会多出一些东西:

```json
  "config": {
    "commitizen": {
      "path": "./node_modules/cz-conventional-changelog"
    }
```

## 3. 测试提交

做完第二步后，`git add .` 添加修改的文件到暂存区。最后要提交的时候，不用`git commit`命令，统一换成`git cz`，然后跟着提示一步步填写就行了。

## 4. 自定义提示的信息

`git cz`后，我们的默认提示信息都是英文的，我们喜欢的话也可以自定义。

首先得安装一个包`cz-customizable`

```shell
# npm
$ npm install cz-customizable

# 或者用yarn
$ yarn add cz-customizable
```

然后，创建`.cz-config.js`配置文件。以下给个内容参考：

```js
'use strict';
module.exports = {
  types: [
    { value: '✨  特性', name: '特性:    一个新的特性' },
    { value: '🐞  修复', name: '修复:    修复一个Bug' },
    { value: '📚  文档', name: '文档:    变更的只有文档' },
    { value: '🌈  格式', name: '格式:    空格, 分号等格式修复' },
    { value: '🛠  重构', name: '重构:    代码重构，注意和特性、修复区分开' },
    { value: '⚡️  性能', name: '性能:    提升性能' },
    { value: '✅  测试', name: '测试:    添加一个测试' },
    { value: '🔧  工具', name: '工具:    开发工具变动(构建、脚手架工具等)' },
    { value: '⏪  回滚', name: '回滚:    代码回退' },
  ],
  scopes: [
    { name: 'src' },
    { name: 'assets' },
    { name: 'static' },
    { name: 'config' },
  ],
  // it needs to match the value for field type. Eg.: 'fix'
  /*  scopeOverrides: {
    fix: [
      {name: 'merge'},
      {name: 'style'},
      {name: 'e2eTest'},
      {name: 'unitTest'}
    ]
  },  */
  // override the messages, defaults are as follows
  messages: {
    type: '选择一种你的提交类型:',
    scope: '选择一个scope (可选):',
    // used if allowCustomScopes is true
    customScope: 'Denote the SCOPE of this change:',
    subject: '短说明:\n',
    body: '长说明，使用"|"换行(可选)：\n',
    breaking: '非兼容性说明 (可选):\n',
    footer: '关联关闭的issue，例如：#31, #34(可选):\n',
    confirmCommit: '确定提交说明?',
  },
  allowCustomScopes: true,
  allowBreakingChanges: ['特性', '修复'],
  // limit subject length
  subjectLimit: 100,
};
```

最后，将`package.json`里的配置文件 config 部分修改为如下。

```json
"config": {
    "commitizen": {
      "path": "./node_modules/cz-customizable"
    }
  }
```
