# vue-markdown

[![npm](https://img.shields.io/npm/v/@adapttive/vue-markdown.svg?style=flat)](https://www.npmjs.com/package/vue-markdown@adapttive/)
[![npm](https://img.shields.io/npm/l/@adapttive/vue-markdown.svg?style=flat)](https://www.npmjs.com/package/vue-markdown@adapttive/)
[![npm](https://img.shields.io/david/adapttive/vue-markdown)](https://www.npmjs.com/package/@adapttive/vue-markdown)
[![npm](https://img.shields.io/bundlephobia/min/@adapttive/vue-markdown)](https://www.npmjs.com/package/@adapttive/vue-markdown)
[![npm](https://img.shields.io/npm/dt/@adapttive/vue-markdown.svg?style=flat)](https://www.npmjs.com/package/@adapttive/vue-markdown)

> If you want vue-markdown for `vue1.X.X`, please checkout [vue-markdown1.X.X](https://github.com/adapttive/vue-markdown/tree/v1).

A Powerful and Highspeed Markdown Parser for Vue.

Quick start: `<vue-markdown>i am a ~~tast~~ **test**.</vue-markdown>`

Supported Markdown Syntax:

* [x] automatic table of contents
* [x] table & class customize
* [x] *SyntaxHighlighter
* [x] definition list
* [x] strikethrough
* [x] GFM task list
* [x] abbreviation
* [x] superscript
* [x] subscript
* [x] footnote
* [x] insert
* [x] emoji
* [x] mark
* [x] *katex

`*SyntaxHighlighter` work with [Prism](https://prismjs.com) recommend

`*katex` need add [katex css](https://unpkg.com/katex/dist/katex.min.css).

# Example

[simple](https://github.com/adapttive/vue-markdown/blob/master/example/simple)

[webpack-simple](https://github.com/adapttive/vue-markdown/blob/master/example/webpack-simple)

[Live Demo](https://adapttive.github.io/vue-markdown/)

# Installation

### Browser globals

> The **dist** folder contains `vue-markdown.js` with the component exported in the `window.VueMarkdown` object.

```html
<body>
  <vue-markdown>i am a ~~tast~~ **test**.</vue-markdown>
</body>
<script src="path/to/vue.js"></script>
<script src="path/to/vue-markdown.js"></script>
<script>
    Vue.use(VueMarkdown);
    var vm = new Vue({
        el: "body"
    });
</script>
```

### NPM

```shell
$ npm install --save @adapttive/vue-markdown
```

### Yarn

```shell
$ yarn add @adapttive/vue-markdown --save
```

### Migrating from vue-markdown 2.3

- You just need to replace the dependencies in `package.json`:

```
{
  "dependencies": {
-  "vue-markdown": "^2.2.4
+  "vue-markdown": "npm:@adapttive/vue-markdown@^X.X.X"
  }
}
```

## CommonJS

```js
var VueMarkdown = require('@adapttive/vue-markdown');

new Vue({
  components: {
    'vue-markdown': VueMarkdown
  }
})
```

## ES6 (Vue-CLI users)

After installing via Yarn or NPM, use the following snippet in the script portion of the Vue component which you wish to render the Markdown.

```js
import VueMarkdown from '@adapttive/vue-markdown'

new Vue({
  components: {
    VueMarkdown
  }
})
```

# Slots

```html
<vue-markdown>this is the default slot</vue-markdown>
```

After setting up the middleware in your vue component above, using the embedded markdown is as easy as writing it between the `vue-markdown` tags.

VueMarkdown has a default slot which is used to write the `markdown` source.

TIP: The default slot only renders **once** at the beginning, and it will overwrite the prop of `source`!

# Props

| Prop                   | Type                     | Default                     | Describe                                                                                                                   |
| ---------------------- | ------------------------ | --------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| watches                | Array                    | `["source", "show", "toc"]` | HTML refresh automatically when the prop in this array changed                                                             |
| source                 | String                   | `null`                      | the markdown source code                                                                                                   |
| show                   | Boolean                  | `true`                      | enable render to the default slot automatically                                                                            |
| html                   | Boolean                  | `true`                      | enable HTML syntax in source                                                                                               |
| xhtml-out              | Boolean                  | `true`                      | `<br></br>` => `<br />`                                                                                                    |
| breaks                 | Boolean                  | `true`                      | `\n` => `<br>`                                                                                                             |
| linkify                | Boolean                  | `true`                      | autoconvert URL-like text to link                                                                                          |
| emoji                  | Boolean                  | `true`                      | `:)` => `😃`                                                                                                               |
| typographer            | Boolean                  | `true`                      | enable some language-neutral replacement and quotes beautification                                                         |
| update-prism           | Boolean                  | `true`                      | if true, vue-markdown will automatically call a re-render of all code blocks through Prism.js ([Using Prism.js](#using-prism.js)) |
| lang-prefix            | String                   | `language-`                 | CSS language prefix for fenced blocks                                                                                      |
| quotes                 | String                   | `“”‘’`                      | use `“”‘’` for Chinese, `„“‚‘` for German, `«»„“` for Russian                                                              |
| table-class            | String                   | `table`                     | customize html class of the `<table>`                                                                                      |
| task-lists             | Boolean                  | `true`                      | Makes GFM task lists mutable, `false` shows GFM as readonly checkboxes                                                     |
| toc                    | Boolean                  | `false`                     | enable automatic table of contents                                                                                         |
| toc-id                 | String                   | `undefined`                 | the HTML id to render TOC                                                                                                  |
| toc-class              | String                   | `table`                     | customize html class of the `<ul>` wrapping the TOC                                                                        |
| toc-first-level        | Number                   | `2`                         | use `2` if you want to skip `<h1>` from the TOC                                                                            |
| toc-last-level         | Number                   | `'toc-first-level' + 1`     | use `5` if you want to skip `<h6>` from the TOC                                                                            |
| toc-anchor-link        | Boolean                  | `true`                      | enable the automatic anchor link in the headings                                                                           |
| toc-anchor-class       | String                   | `toc-anchor`                | customize the anchor class name                                                                                            |
| toc-anchor-link-symbol | String                   | `#`                         | customize the anchor link symbol                                                                                           |
| toc-anchor-link-space  | Boolean                  | `true`                      | enable inserting a space between the anchor link and heading                                                               |
| toc-anchor-link-class  | String                   | `toc-anchor-link`           | customize the anchor link symbol class name                                                                                |
| toc-anchor-link-before | Boolean                  | `true`                      | allows you to prepend/append the anchor link in the headings                                                               |
| anchorAttributes       | Object                   | `{}`                        | anchor tag attributes such as `target: '_blank'` or `rel: 'nofollow'`                                                      |
| prerender              | Function (String) String | `null`                      | filter function before markdown parse                                                                                      |
| postrender             | Function (String) String | `null`                      | filter function after markdown parse                                                                                       |
| inline                 | Boolean                  | `false`                     | result will NOT be wrapped into `<p>` tags                                                                                 |

# Events

| Name | Param[Type] | Describe |
| ---- | --------- | -------- |
| rendered | outHtml[String] | dispatch when render finish |
| toc-rendered | tocHtml[String] | dispatch when TOC render finish, never dispatch if the toc[prop] is `false` |

# Using Prism.js

1. Visit the [download page](https://prismjs.com/download.html#themes=prism&languages=markup+css+clike+javascript)
2. Select all the options that apply for your project
3. At the bottom of the page download both the JS and CSS
4. Include them in your `index.html` **MAKE SURE to include Prism before your** `app.js`


# Plugins

```html
 <template>
   <div>
     <vue3-markdown-it :source='source' :plugins='plugins' />
   </div>
 </template>

 <script>
 import katex from 'markdown-it-katex';
 import tasklists from 'markdown-it-task-lists';
 import externalPreview from 'markdown-it-external-preview';
 import VueMarkdown from 'vue-markdown';

 export default {
   components: {
     VueMarkdown
   },
   data() {
     return {
       plugins: [
         {
           plugin: katex,
           options: { throwOnError: false, errorColor: ' #cc0000' }
         },
         {
           plugin: tasklists,
           options: { enabled: this.taskLists }
         },
         {
           plugin: externalPreview
         }
       ]
     }
   }
 }
 </script>
```

- Make sure you add dependencies for plugins:
    - `"highlight.js": "^10.4.0"`
    - `"markdown-it-external-preview": "^1.0.4"`
    - `"markdown-it-katex": "npm:@iktakahiro/markdown-it-katex@^4.0.1"`

# Thanks

- [markdown-it](https://github.com/markdown-it/markdown-it)
- [transtone](https://github.com/transtone)
- [**brandonferens**](https://github.com/brandonferens)

# Contributions

- [miaolz123](https://github.com/miaolz123)
- [brandonferens](https://github.com/brandonferens)
- [brianbancroft](https://github.com/brianbancroft)
- [nikolasp](https://github.com/nikolasp)
- [mbackonja](https://github.com/mbackonja)
- [Endi1](https://github.com/Endi1)
- [printscreen](https://github.com/printscreen)
- [killix](https://github.com/killix)
- [LeFnord](https://github.com/lefnord)
- [FlorianWendelborn](https://github.com/FlorianWendelborn)
- [NoahCardoza](https://github.com/NoahCardoza)
- [milindsingh](https://github.com/milindsingh)

# License

Copyright (c) 2016

 - [miaolz123](https://github.com/miaolz123) by [MIT](https://opensource.org/licenses/MIT)
 - [milindsingh](https://github.com/milindsingh) by [MIT](https://opensource.org/licenses/MIT)
