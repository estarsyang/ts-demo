# ts

### init
1. ```vue create ts```
2. 选择默认就好了 ❯ default (babel, eslint)
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
            "import { Vue, Component } from 'vue-property-decorator';",
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