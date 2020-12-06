---
title: "VS Code插件"
date: 2020-08-14T13:59:24+08:00
draft: false
weight: 3
enableToc: true
---

[VS Code官网](https://code.visualstudio.com/)

编辑器从`Eclipse`->`MyEclipse`->`IDEA`->`webstorm`，觉得自己找到了真爱，打死不换，每每同事安利的时候，都坚定地站队`webstorm`。直到升级版本后...webstorm打击盗版真的是太狠了。遂决定大步奔向`VS Code`的怀抱，简单配置、装了些插件之后，真香～～

*2020-09-01：重新转回`webstorm`了，主要原因是最近多人协作的一个大项目，频繁git各种操作和查看依赖上下文，暂时没找到替代方案，为了效率换回来了。但是文本编辑和小型静态项目还是推荐vs的～*

{{< img src="/images/tools/vscode-keyboard-shortcuts.jpg" title="快捷键" caption="MAC版" alt="快捷键">}}

## 基础配置篇

### Chinese(Simplified) Language Pack for Visual Studio Code

{{< img src="/images/tools/vscode-language-pack.jpg" title="Language Pack" caption="汉化语言包" alt="Language Pack">}}

### Darcula Theme

主题插件，在其他编辑器上用习惯了`Darcula`的配色方案，装上之后一下子亲切不少～

主题这个是因人而异的啦，大家可以直接在插件那搜索`theme`,诸多款式任君挑选

{{< img src="/images/tools/vscode-darcula-theme.jpg" title="Darcula Theme" caption="主题配色" alt="Darcula Theme">}}

### Eclipse Keymap

快捷键。习惯了`Eclipse`的快捷键，所有编辑器用的都是这套。
插件装到这里已经感觉很畅快了，而且启动速度比`webstorm`快，赞一个～

{{< img src="/images/tools/vscode-eclipse-keymap.jpg" title="Eclipse Keymap" caption="快捷键" alt="Eclipse Keymap">}}

### indent-rainbow

缩进颜色区分，未正常缩进时会变红。舒舒服服看代码～

{{< img src="/images/tools/vscode-indent-rainbow.jpg" title="indent-rainbow" caption="缩进标志" alt="indent-rainbow">}}

### Markdown Preview Enhanced

{{< img src="/images/tools/vscode-markdown-preview.jpg" title="Markdown Preview Enhanced" caption="markdown预览" alt="Markdown Preview Enhanced">}}


## 开发利器

### ESLint

{{< img src="/images/tools/vscode-eslint.jpg" title="ESLint" caption="代码检查" alt="ESLint">}}

### Vetur

详细介绍移步：https://github.com/vuejs/vetur

{{< img src="/images/tools/vscode-vetur.jpg" title="Vetur" caption="vue开发者必备" alt="Vetur">}}

### Prettier

{{< img src="/images/tools/vscode-prettier.jpg" title="Vetur" caption="代码格式化" alt="Prettier">}}

### Less intelliSense

{{< img src="/images/tools/vscode-less-intellisense.jpg" title="Less intelliSense" caption="less变量与混合提示" alt="Less intelliSense">}}

### npm Intellisense

使用require()导入模块代码时，npm Intellisense组件会自发进行包提示。

{{< img src="/images/tools/vscode-npm-intellisense.jpg" title="npm Intellisense" caption="包导入提示" alt="npm Intellisense">}}

### Image preview

光标悬浮在图片路径上时，显示图片预览。能快速检查到引用是否正确

{{< img src="/images/tools/vscode-image-preview.jpg" title="Image preview" caption="图片预览" alt="Image preview">}}

### Live Server

适合前端开发。这个插件能实现页面实时预览，保存即更新。

{{< img src="/images/tools/vscode-live-server.jpg" title="Live Server" caption="实时预览" alt="Live Server">}}

### CSS Peek

前端开发。鼠标悬停在元素的类名或元素ID上，就可以看到应用于这个元素的 CSS 规则。

{{< img src="/images/tools/vscode-css-peek.gif" title="CSS Peek" caption="鼠标悬停查看css样式" alt="CSS Peek">}}

### Beautify

代码格式化。支持自定义规则。

{{< img src="/images/tools/vscode-beautify.jpg" title="Live Server" caption="实时预览" alt="Live Server">}}

### Auto Close Tag

自动补全标签。

### Auto Rename Tag

自动重命名成对的标签。

{{< img src="/images/tools/vscode-css-peek.gif" title="Live Server" caption="实时预览" alt="Live Server">}}

### Code Runner

一键运行代码，支持很多语言。包括C、C++、JAVA、JS、PHP、Python、Perl...

### Comment Translate

插件使用 Google Translate API 翻译注释，功能强大，在看开源项目源代码的时候很有用(英文好的话请忽略)。

### Image preview

图片预览，可以在代码行号左侧槽位(或hover时)预览图片。

### WakaTime

编程时间记录工具，在官网 Dashboard 中以图形化方式展示编程时间，支持邮件订阅。


## Git

Tip: 修改代码时，VS code会对不同的修改进行不同形式的标注：红色箭头代表有删除行，蓝色开头代表修改，绿色开头代表新增。`Ctrl + shift + G`打开代码管理工具，可以查看修改文件。

### Git history

查看/搜索文件提交历史

呼出命令`git log`

{{< img src="/images/tools/vscode-git-history.jpg" title="Git history" caption="Git提交记录查看" alt="Git history">}}
