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

做完第二步后，`git add .` 添加修改的文件到暂存区。最后要提交的时候，不用`git commit`命令，统一换成`git cz`
