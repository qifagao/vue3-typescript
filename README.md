# vue3-te-cms

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# Editorconfig 配置

# prettier

{
"useTabs": false,
"tabWidth": 2,
"printWidth": 80,
"singleQuote": false,
"trailingComma": "none",
"semi": true
}

# npm install eslint-plugin-prettier eslint-config-prettier -D


# GIT规范操作

# commitizen 是一个 cli 工具，用于规范化 git commit 信息，可以代替 git commit
npm install -g commitizen cz-conventional-changelog  # 安装规范化提交插件
echo '{"path": "cz-conventional-changelog"}' > ~/.czrc # 配置
git cz 
# ? Select the type of change that you're committing: docs:     Documentation only changes
# ? What is the scope of this change (e.g. component or file name): (press enter to skip) readme
# ? Write a short, imperative tense description of the change (max 86 chars):
# (46) update readme.md, add init project description
# ? Provide a longer description of the change: (press enter to skip) 

# ? Are there any breaking changes? No
# ? Does this change affect any open issues? No
# [main caae82e] docs(readme): update readme.md, add init project description
# 1 file changed, 7 insertions(+)
# zuo@zmac comitizen-practice-demo % 

# husk 安装
安装 husky
npm install husky --save-dev
安装 husky git hooks
# 方法1：
npx husky install
# 方法2：配置 package.json, scripts："prepare": "husky install"
npm run prepare

# husky - Git hooks installed
测试 husky 钩子作用，添加 pre-commit 钩子
npx husky add .husky/pre-commit "npm test"
# 查看当前目录 .husky 目录是否有生成 pre-commit 文件
# 如果需要删除这个钩子，直接 删除 .husky/pre-commit 文件即可

commitlint 安装配置
npm install -g @commitlint/cli @commitlint/config-conventional
# Configure commitlint to use conventional config
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js

npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'

测试

git add .
git commit -m 'xx'
zuo@zmac comitizen-practice-demo % git commit -m 'xxx'
# ⧗   input: xxx
# ✖   subject may not be empty [subject-empty]
# ✖   type may not be empty [type-empty]

# ✖   found 2 problems, 0 warnings
# ⓘ   Get help: https://github.com/conventional-changelog/commitlint/#what-is-commitlint

# husky - commit-msg hook exited with code 1 (error)
# zuo@zmac comitizen-practice-demo % 
提示缺少 subject 就是提交信息、type 就是提交类型，按照规范提交就 ok 了

standard-version（自动生成、打tag）
npm install standard-version --save-dev
# scripts 设置
"release": "standard-version"

