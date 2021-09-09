---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

Code in backtick-fenced block w/ lang:

```ts
/**
 * An entity is just an ID. This is used to look up its associated
 * Components.
 */
type Entity = number

type ComponentClass<T extends Component> = new (...args: any[]) => T
```
<style>
pre, code {
    background-color: #f0f0f0;
}
</style>
<link rel="stylesheet" href="https://unpkg.com/@highlightjs/cdn-assets@11.2.0/styles/default.min.css">
<script src="//unpkg.com/@highlightjs/cdn-assets@11.2.0/highlight.min.js"></script>
<script type="module">
    import prettier from "https://unpkg.com/prettier@2.4.0/esm/standalone.mjs";
    import parserTS from "https://unpkg.com/prettier@2.4.0/esm/parser-typescript.mjs";
    // import hljs from "https://unpkg.com/@highlightjs/cdn-assets@11.2.0/highlight.min.js";
    let tsBlocks = document.querySelectorAll("code.language-ts");
    for (let tsBlock of tsBlocks) {
        let fmt = prettier.format(tsBlock.innerText, {
            parser: "typescript",
            plugins: [parserTS],
            printWidth: 40,
        });
        tsBlock.innerHTML = fmt;
    }
    hljs.highlightAll();
</script>

<!-- <script>hljs.highlightAll();</script> -->

<!--

Code in backtick-fenced block w/o lang:

```
/**
 * An entity is just an ID. This is used to look up its associated
 * Components.
 */
type Entity = number
```

Code in backtick-fenced block w/ custom lang:

```lang:ts
/**
 * An entity is just an ID. This is used to look up its associated
 * Components.
 */
type Entity = number
```


Code in Liquid block:

{% highlight ts %}
/**
 * An entity is just an ID. This is used to look up its associated
 * Components.
 */
type Entity = number
{% endhighlight %}

 -->
