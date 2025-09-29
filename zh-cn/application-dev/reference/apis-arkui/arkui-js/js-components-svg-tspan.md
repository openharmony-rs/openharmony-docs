# tspan
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

添加文本样式。


>  **说明：**
>  - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
>  - 文本的展示内容需要写在元素标签内，可嵌套子元素标签tspan分段。
>
>  - 文本分段，只支持被父元素标签svg嵌套。

## 权限列表

无


## 子组件

支持[tspan](js-components-svg-tspan.md)。


支持以下表格中的属性。


| 名称             | 类型                                 | 默认值   | 必填   | 描述                                       |
| -------------- | ---------------------------------- | ----- | ---- | ---------------------------------------- |
| id             | string                             | -     | 否    | 组件的唯一标识。                                 |
| x              | &lt;length&gt;\|&lt;percentage&gt; | 0     | 否    | 设置组件左上角x轴坐标。                             |
| y              | &lt;length&gt;\|&lt;percentage&gt; | 0     | 否    | 设置组件左上角y轴坐标。作为textpath子组件时失效。            |
| dx             | &lt;length&gt;\|&lt;percentage&gt; | 0     | 否    | 设置文本x轴偏移。                                |
| dy             | &lt;length&gt;\|&lt;percentage&gt; | 0     | 否    | 设置文本y轴偏移。作为textpath子组件时失效。               |
| rotate         | number                             | 0     | 否    | 字体以左下角为圆心旋转角度，正数顺时针，负数逆时针。               |
| font-size      | &lt;length&gt;                     | 30px  | 否    | 设置文本的尺寸。                                 |
| fill           | &lt;color&gt;                      | black | 否    | 字体填充颜色。                                  |
| opacity        | number                             | 1     | 否    | 元素的透明度，取值范围为0到1，1表示为不透明，0表示为完全透明。支持属性动画。 |
| fill-opacity   | number                             | 1.0   | 否    | 字体填充透明度。                                 |
| stroke         | &lt;color&gt;                      | black | 否    | 绘制字体边框并指定颜色。                             |
| stroke-width   | number                             | 1px   | 否    | 字体边框宽度。                                  |
| stroke-opacity | number                             | 1.0   | 否    | 字体边框透明度。                                 |

## 示例

```html
<!-- xxx.hml -->
<div class="container">
  <svg >
    <text x="20" y="500" fill="#D2691E" font-size="20">
      zero text.
      <tspan>first span.</tspan>
      <tspan fill="red" font-size="35">second span.</tspan>
      <tspan fill="#D2691E" font-size="40" rotate="10">third span.</tspan>
    </text>
    <text x="20" y="550" fill="#D2691E" font-size="20">
      <tspan dx="-5" fill-opacity="0.2">first span.</tspan>
      <tspan dx="5" fill="red" font-size="25" fill-opacity="0.4">second span.</tspan>
      <tspan dy="-5" fill="#D2691E" font-size="35" rotate="-10" fill-opacity="0.6">third span.</tspan>
      <tspan fill="#blue" font-size="40" rotate="10" fill-opacity="0.8" stroke="#00FF00" stroke-width="1px">forth span.</tspan>
    </text>
  </svg>
</div>
```

```css
/* xxx.css */
.container {    
    flex-direction: row;
    justify-content: flex-start;
    align-items: flex-start;
    height: 1000px;
    width: 1080px;
}
```

![zh-cn_image_0000001127125196](figures/zh-cn_image_0000001127125196.png)

属性动画示例

```html
<!-- xxx.hml -->
<div class="container">
  <svg>
    <text y="300" font-size="30" fill="blue">
      <tspan>
        tspan attribute x|opacity|rotate
        <animate attributeName="x" from="-100" to="400" dur="3s" repeatCount="indefinite"></animate>
        <animate attributeName="opacity" from="0.01" to="0.99" dur="3s" repeatCount="indefinite"></animate>
        <animate attributeName="rotate" from="0" to="360" dur="3s" repeatCount="indefinite"></animate>
      </tspan>
    </text>

    <text y="350" font-size="30" fill="blue">
      <tspan>
        tspan attribute dx
        <animate attributeName="dx" from="-100" to="400" dur="3s" repeatCount="indefinite"></animate>
      </tspan>
    </text>
  </svg>
</div>
```

```css
/* xxx.css */
.container {
    flex-direction: row;
    justify-content: flex-start;
    align-items: flex-start;
    height: 3000px;
    width: 1080px;
}
```

![zh-cn_image_0000001127285008](figures/zh-cn_image_0000001127285008.gif)

```html
<!-- xxx.hml -->
<div class="container">
  <svg>
    <text>
      <tspan x="0" y="550" font-size="30">
        tspan attribute fill|fill-opacity
        <animate attributeName="fill" from="blue" to="red" dur="3s" repeatCount="indefinite"></animate>
        <animate attributeName="fill-opacity" from="0.01" to="0.99" dur="3s" repeatCount="indefinite"></animate>
      </tspan>
    </text>
  </svg>
</div>
```

![zh-cn_image_0000001127125198](figures/zh-cn_image_0000001127125198.gif)

```html
<!-- xxx.hml -->
<div class="container">
  <svg>
     <text>
       <tspan x="20" y="600" fill="red">
         tspan attribute font-size
         <animate attributeName="font-size" from="10" to="50" dur="3s" repeatCount="indefinite"></animate>
       </tspan>
    </text>
  </svg>
</div>
```

![zh-cn_image_0000001173164863](figures/zh-cn_image_0000001173164863.gif)

```html
<!-- xxx.hml -->
<div class="container">
  <svg>
    <text>
      <tspan x="20" y="650" font-size="25" fill="blue" stroke="red">
        tspan attribute stroke
        <animate attributeName="stroke" from="red" to="#00FF00" dur="3s" repeatCount="indefinite"></animate>
      </tspan>
    </text>
    <text>
      <tspan x="300" y="650" font-size="25" fill="white" stroke="red">
        tspan attribute stroke-width-opacity
        <animate attributeName="stroke-width" from="1" to="5" dur="3s" repeatCount="indefinite"></animate>
        <animate attributeName="stroke-opacity" from="0.01" to="0.99" dur="3s" repeatCount="indefinite"></animate>
      </tspan>
    </text>
  </svg>
</div>
```

![zh-cn_image_0000001127125200](figures/zh-cn_image_0000001127125200.gif)
