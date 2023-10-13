项目初始化
`pnpm i eslint -D -w`

eslint
`npx eslint --init`

相关依赖
`pnpm i -D -w @typescript-eslint/eslint-plugin @typescript-eslint/parser`

`pnpm i -D -w typescript`

```json
{
    "env": {
        "browser": true,
        "es2021": true
    },
    "extends": [
        "eslint:recommended",
        "plugin:@typescript-eslint/recommended",
        "prettier",
        "plugin:prettier/recommended"
    ],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaVersion": "latest",
        "sourceType": "module"
    },
    "plugins": [
        "@typescript-eslint",
        "prettier"
    ],
    "rules": {
        "prettier/prettier": "error",
        "no-case-declarations": "off",
        "no-constant-condition": "off",
        "@typescript-eslint/ban-ts-comment": "off"
    }
}

```

安装ts-eslint
`pnpm i -D -w @typescript-eslint/eslint-plugin`

#### 代码风格
`pnpm i prettier -D -w`

prettier配置 `.prettierrc.json`
```json

{
    "printWidth": 80,
    "tabWidth": 2,
    "useTabs": true,
    "singleQuote": true,
    "semi": true,
    "trailingComma": "none",
    "bracketSpacing": true
}

```

prettier集成到eslint中
`pnpm i eslint-config-prettier eslint-plugin-prettier -D -w` 


#### commit规范
安装husky
`pnpm i husky -D -w`
初始化
`npx husky install`

将eslint 加入husky
`npx husky add .husky/pre-commit "pnpm lint" husky - created .husky/pre-commit`

后期需要加入 lint-staged 只对暂存区的代码及逆行检查

使用commitlint对commit信息进行检查
`pnpm i commitlint @commitlint/cli @commitlint/config-conventional -D -w`

新建`.commitlintrc.js`
```js
module.exports = {
    extends: ["@commitlint/config-conventional"]
}
```

commitlint 集成到husky中
`npx husky add .husky/commit-msg "npx --no-install commitlint -e $HUSKY_GIT_PARAMS"`

conventional 规范集意义：
```
// 提交的类型
<type>: <subject> 
```
常用`type`值如下：
- `feat`:添加新功能
- `fix`
- `chore`:一些不影响功能的修改
- `docs`
- `perf`
- `refatcor`:重构
- `test`

初始化`tsconfig.json`
```json
{
    "compileOnSave": true,
    "compilerOptions": {
        "target": "ESNext",
        "useDefineForClassFields": true,
        "module": "ESNext",
        "lib": ["ESNext","DOM"],
        "moduleResolution": "Node",
        "strict": true,
        "sourceMap": true,
        "resolveJsonModule": true,
        "isolatedModules": true,
        "esModuleInterop": true,
        "noEmit": true,
        "noUnusedLocals": true,
        "noUnusedParameters": true,
        "noImplicitReturns": false,
        "skipLibCheck": true,
        "baseUrl": "./packages"
    }
}
```

 项目打包工具
 `pnpm i -D -w rollup`