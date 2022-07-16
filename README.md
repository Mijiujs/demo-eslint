eslint 

# eslint是代码校验工具
- ESLint 使用 Espree 解析 JavaScript。
- ESLint 使用 AST 去分析代码中的模式
- ESLint 是完全插件化的。每一个规则都是一个插件并且你可以在运行时添加更多的规则。

# 文档链接
https://cn.eslint.org/docs/user-guide/configuring

# 安装
```
npm install -D eslint 

./node_modules/.bin/eslint --init

./node_modules/.bin/eslint .
```

# 配置方式
- .eslintrc.js
- package.json中的eslintConfig字段
  
# 支持es6
支持es语法和变量 { "env":{ "es6": true } }

支持es6语法 { "parserOptions": { "ecmaVersion": 6 } }

# env
指定脚本的运行环境。每种环境都有一组特定的预定义全局变量


# globals
脚本在执行期间访问的额外的全局变量

- 使用字符串 "off" 禁用全局变量
- 布尔值 false 和字符串值 "readable" 等价于 "readonly"
- 布尔值 true 和字符串值 "writeable" 等价于 "writable"

# plugins
esLint支持使用第三方插件。在使用插件之前，你必须使用npm安装它

# extends
指定eslint规范

# 解析器 parser
默认解析器parser，也可以使用其他解析器，只要解析器符合以下要求
1. 它必须是一个 Node 模块，可以从它出现的配置文件中加载。通常，这意味着应该使用 npm 单独安装解析器包。
2. 它必须符合 parser interface
以下解析器与 ESLint 兼容：
- Esprima
- Babel-ESLint，一个对Babel解析器的包装，使其能够与ESLint兼容
- @typescript-eslint/parser，将TypeScript转换成与estree兼容的形式，以便在ESLint中使用

# 解析器选项 parserOptions
- ecmaVersion，指定ECMAScript版本，5（默认）、6、7、8、9或10。也可以年份2015（同6）、2019（同10）
- sourceType，script（默认）、module
- ecmaFeatures，是一个对象，额外的语言特性
> - globalReturn，允许在全局作用于下使用return语句
> - impliedStrict，启用全局 strict mode (如果 ecmaVersion 是 5 或更高)
> - jsx，启用JSX
> - experimentalObjectRestSpread，启用实验性的支持，不建议开启

# rules
启用的规则及其各自的错误级别
- off或0，关闭规则
- warn或1，警告
- error或2，错误

### Disabling Rules with Inline Comments
/* eslint-disable */

/* eslint-enable */

/* eslint-disable no-alert, no-console */

/* eslint-disable-line */

/* eslint-disable-next-line */

/* eslint-disable-line no-alert */

### Disabling Rules Only for a Group of Files
```
{
  "rules": {...},
  "overrides": [
    {
      "files": ["*-test.js","*.spec.js"],
      "rules": {
        "no-unused-expressions": "off"
      }
    }
  ]
}
```
