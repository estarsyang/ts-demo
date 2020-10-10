# ts

### init
1. ```vue create ts```
2. 选择默认就好了 ❯ default (babel, eslint)。如果选择了ts的模板，直接看第4点。
3. ```vue add typescript```
    - Use class-style component syntax? No  
    - Use Babel alongside TypeScript (required for modern mode, auto-detected polyfi
lls, transpiling JSX)? Yes
    - Convert all .js files to .ts? Yes
    - Allow .js files to be compiled? Yes
    - Skip type checking of all declaration files (recommended for apps)? No    
    1. 这里新增了几个文件，可以一起看下。
        - tsconfig.json // ts配置文件
        - shims-tsx.d.ts
        - shims-vue.d.ts // 定义vue文件告知loader如何处理vue文件
        - 重写了main.js ，转成了 main.ts
        - package.json 新增了typescript文件。
        - HelloWorld.vue 修改了写法，使用了ts的写法。
4. 手动添加ts模板文件，方便我们开发。
    1. 项目根目录新建 .vscode 文件夹。这个文件夹是vscode配置文件夹，我们可以新建一些配置给vscode
    2. 新建 xxx.code-snippets 文件，xxx任意名字，我这里取了tstemplate。
    3. 编辑tstemplate.code-snippets,复制以下内容。如果不喜欢这个模板，可以自己定义并修改      
    ```json
    {
        "TS Vue Template": {
            "prefix": "tsvue",
            "body": [
            "<template>",
            "  <div class=\"${1:page}\">\n",
            "  </div>",
            "</template>\n",
            "<script lang=\"ts\">",
            "import { Vue, Component, Prop, Watch } from 'vue-property-decorator';",
            "@Component",
            "export default class ${2:Index} extends Vue {",
            "// @Prop({ default: () => [] })",
            "// private readonly menu!: Array<Record<string, unknown>>;\n",
            "// computed",
            "// get computedMsg () {}\n",
            "// lifecycle\n",
            "created () { }\n",
            "mounted () {}\n",
            "// methods \n",
            "}",
            "</script>\n",
            "<style scoped lang=\"scss\">",
            "  .${1:page} {",
            "  }",
            "</style>",
            ""
            ],
            "description": "Log output to console"
        }
        }
    ```
    4. 新建 vue文件，输入 ts,出现 tsvue提示，确定，自动生成ts模板

5. 注意看我们的模板中引用了 [vue-property-decorator](https://github.com/kaorun343/vue-property-decorator)库，那么这里就要安装相应的依赖了
    1. 安装成功后运行报异常。版本安装不对，可以降到8的版本
        ```js
        // error
        This dependency was not found:

        * vue-class-component in ./node_modules/vue-property-decorator/lib/vue-property-decorator.js

        To install it, you can run: npm install --save vue-class-component
        xxxxx
        // reason 安装过程中已经提示没有安装依赖了。9的版本没有安装有依赖，那么你可以自己安装 8的版本，之前我开发自动安装了 8.5.1 ，那么就重新装一下8
        warning " > vue-property-decorator@9.0.0" has unmet peer dependency "vue-class-component@*".
        // 先remove 再安装，安装结束后，再次启动，搞定。
        yarn remove vue-property-decorator
        yarn add vue-property-decorator@8.5.1
        ```
    2. 第二个报错 [修复方法](https://stackoverflow.com/questions/38271273/experimental-decorators-warning-in-typescript-compilation)
        ```js
        // error
        Experimental support for decorators is a feature that is subject to change in a future release. Set the 'experimentalDecorators' option in your 'tsconfig' or 'jsconfig' to remove this warning.
        import {Vue, Component} from 'vue-property-decorator'
        @Component
        export default class HelloWorld extends Vue {
                                      ^
          private msg = 'HelloWorld'
        }
        // fix tsconfig中添加属性
        {
            "compilerOptions": {
                "experimentalDecorators": true,
                "allowJs": true
            }
        }
        ```