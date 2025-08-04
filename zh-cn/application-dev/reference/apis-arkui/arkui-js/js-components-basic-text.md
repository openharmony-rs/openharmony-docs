# text
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--SE: @pssea-->
<!--TSE: @jiaoaozihao-->

>  **说明：**
>
>  - 该组件从API version 4开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
>  - 文本的展示内容需要写在元素标签内。

文本，用于呈现一段信息。

## 权限列表

无


## 子组件

支持&lt;[span](js-components-basic-span.md)&gt;。


## 属性

支持[通用属性](js-components-common-attributes.md)。


## 样式

除支持[通用样式](js-components-common-styles.md)外，还支持如下样式：

| 名称                               | 类型                                                         | 默认值                                    | 必填 | 描述                                                         |
| ---------------------------------- | ------------------------------------------------------------ | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| color                              | &lt;color&gt;                                                | #e5000000                                 | 否   | 设置文本的颜色。                                             |
| font-size                          | &lt;length&gt;                                               | 30px                                      | 否   | 设置文本的尺寸。                                             |
| allow-scale                        | boolean                                                      | true                                      | 否   | 文本尺寸是否跟随系统设置字体缩放尺寸进行放大缩小。<br/>如果需要支持动态生效，请参看config描述文件中config-changes标签。 |
| letter-spacing                     | &lt;length&gt;                                               | 0px                                       | 否   | 设置文本的字符间距。                                         |
| word-spacing<sup>7+</sup>          | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt;&nbsp;\|&nbsp;string | normal                                    | 否   | 设置文本之间的间距，string可选值为：<br/>normal：默认的字间距。 |
| font-style                         | string                                                       | normal                                    | 否   | 设置文本的字体样式，可选值为：<br/>-&nbsp;normal：标准的字体样式。<br/>-&nbsp;italic：斜体的字体样式。 |
| font-weight                        | number&nbsp;\|&nbsp;string                                   | normal                                    | 否   | 设置文本的字体粗细，number类型取值[100,&nbsp;900]，默认为400，取值越大，字体越粗。number取值必须为100的整数倍。<br/>string类型取值支持如下四个值：lighter、normal、bold、bolder。 |
| text-decoration                    | string                                                       | none                                      | 否   | 设置文本的文本修饰，可选值为：<br/>-&nbsp;underline：文字下划线修饰。<br/>-&nbsp;line-through：穿过文本的修饰线。<br/>-&nbsp;none：标准文本。 |
| text-decoration-color<sup>7+</sup> | &lt;color&gt;                                                | -                                         | 否   | 设置文本修饰线的颜色。                                       |
| text-align                         | string                                                       | start<br/>                                | 否   | 设置文本的文本对齐方式，可选值为：<br/>-&nbsp;left：文本左对齐。<br/>-&nbsp;center：文本居中对齐。<br/>-&nbsp;right：文本右对齐。<br/>-&nbsp;start：根据文字书写相同的方向对齐。<br/>-&nbsp;end：根据文字书写相反的方向对齐。<br/>如果文本宽度未指定大小，文本的宽度和父容器的宽度大小相等的情况下，对齐效果可能会不明显。 |
| line-height                        | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt;<sup>7+</sup>&nbsp;\|&nbsp;string<sup>7+</sup> | 0px<sup>1-6</sup><br/>normal<sup>7+</sup> | 否   | 设置文本的文本行高，设置为0px时，不限制文本行高，自适应字体大小。string可选值为：<br/>normal<sup>7+</sup>：默认的行高。 |
| text-overflow                      | string                                                       | clip                                      | 否   | 在设置了最大行数的情况下生效，可选值为：<br/>-&nbsp;clip：将文本根据父容器大小进行裁剪显示；<br/>-&nbsp;ellipsis：根据父容器大小显示，显示不下的文本用省略号代替。需配合max-lines使用。 |
| font-family                        | string                                                       | sans-serif                                | 否   | 设置文本的字体列表，用逗号分隔，每个字体用字体名或者字体族名设置。列表中第一个系统中存在的或者通过[自定义字体](js-components-common-customizing-font.md)指定的字体，会被选中作为文本的字体。 |
| max-lines                          | number&nbsp;\|&nbsp;string<sup>7+</sup>                      | -                                         | 否   | 设置文本的最大行数，string类型可选值为：<br/>-&nbsp;auto<sup>7+</sup>：文本行数自适应容器高度。 |
| min-font-size                      | &lt;length&gt;                                               | -                                         | 否   | 文本最小字号，需要和文本最大字号同时设置，支持文本字号动态变化。设置最大最小字体样式后，font-size不生效。 |
| max-font-size                      | &lt;length&gt;                                               | -                                         | 否   | 文本最大字号，需要和文本最小字号同时设置，支持文本字号动态变化。设置最大最小字体样式后，font-size不生效。 |
| font-size-step                     | &lt;length&gt;                                               | 1px                                       | 否   | 文本动态调整字号时的步长，需要设置最小，最大字号样式生效。   |
| prefer-font-sizes                  | &lt;array&gt;                                                | -                                         | 否   | 预设的字号集合，在动态尺寸调整时，优先使用预设字号集合中的字号匹配设置的最大行数，如果预设字号集合未设置，则使用最大最小和步长调整字号。针对仍然无法满足最大行数要求的情况，使用text-overflow设置项进行截断，设置预设尺寸集后，font-size、max-font-size、min-font-size和font-size-step不生效。<br/>如：prefer-font-sizes:&nbsp;12px,14px,16px |
| word-break<sup>6+</sup>            | string                                                       | normal                                    | 否   | 设置文本折行模式，可选值为：<br/>-&nbsp;normal：默认换行规则，依据各自语言的规则，允许在字间发生换行。<br/>-&nbsp;break-all：对于非中文/日文/韩文的文本，可在任意字符间断行。<br/>-&nbsp;break-word：与break-all相同，不同的地方在于它要求一个没有断行破发点的词必须保持为一个整体单位。 |
| text-indent<sup>7+</sup>           | &lt;length&gt;                                               | -                                         | 否   | 设置首行缩进量。                                             |
| white-space<sup>7+</sup>           | string                                                       | pre                                       | 否   | 设置处理元素中空白的模式，可选值为：<br/>-&nbsp;normal：所有空格、回车、制表符都合并成一个空格，文本自动换行。<br/>-&nbsp;nowrap：所有空格、回车、制表符都合并成一个空格，文本不换行。<br/>-&nbsp;pre：所有东西原样输出。<br/>-&nbsp;pre-wrap：所有东西原样输出，文本换行。<br/>-&nbsp;pre-line：所有空格、制表符合并成一个空格，回车不变，文本换行。 |
| adapt-height<sup>7+</sup>          | boolean                                                      | false                                     | 否   | 文本大小是否自适应容器高度。<br/>设置字体大小自适应相关样式后生效。 |

>  **说明：**
>  - 字体动态缩放：预设尺寸集合和最小最大字号调节基于是否满足最大行数要求，预设尺寸集合会按照从左到右顺序查看是否满足最大行数要求，最小最大字号调节则基于从大到小顺序查看是否满足最大行数要求。
>
>  - 文本换行：文本可以通过转义字符\r\n进行换行。
>
>  - 文本标签内支持以下转义字符：\a，\b，\f，\n，\r，\t，\v，\'，\"，\0。
>
>  - 当使用子组件span组成文本段落时，如果span属性样式异常，将导致text段落无法显示。
>
>  - letter-spacing、text-align、line-height、text-overflow和max-lines样式作用于text及其子组件（span）组成的文本内容。
>
>  - text组件说明：不支持text内同时存在文本内容和span子组件，（如果同时存在，只显示span内的内容)。


## 事件

支持[通用事件](js-components-common-events.md)。

## 方法

支持[通用方法](js-components-common-methods.md)。


## 示例
```html
<!-- xxx.hml -->
<div class="container">
    <text class="title">default text</text>
    <text class="title textcolor">hello world with color</text>
    <text class="title textsize">hello world with font-size</text>
    <text class="title textletterspacing">hello world with letter-spacing</text>
    <text class="title textwordspacing">hello world with word-spacing</text>
    <text class="title textstyle">hello world with italic</text>
    <text class="title textweight">hello world with font-weight</text>
    <text class="title textdecoration1">hello world with underline</text>
    <text class="title textdecoration2">hello world with line-through</text>
    <text class="title textalign">hello world with text-align:right</text>
</div>
```

```css
/* xxx.css */
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}
.title {
    text-align: center;
    width: 800px;
    height: 60px;
}
.textcolor {
    color: indianred;
}
.textsize {
    font-size: 40px;
}
.textletterspacing {
    letter-spacing: -3px;
}
.textwordspacing {
    word-spacing: 20px;
}
.textstyle {
    font-style: italic;
}
.textweight {
    font-weight: 700;
}
.textdecoration1 {
    text-decoration: underline;
}
.textdecoration2 {
    text-decoration: line-through;
    text-decoration-color: red;
}
.textalign {
    text-align: right;
}
```


![zh-cn_image_0000001167823076](figures/js-text.png)

