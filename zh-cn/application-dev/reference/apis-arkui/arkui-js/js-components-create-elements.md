# 动态创建组件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1-->
<!--SE: @shiyu_huang-->
<!--TSE: @TerryTsao-->

提供在页面中动态添加组件，并为动态添加的组件设置属性与样式的能力。

>  **说明：**
>
> - 从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## createElement

createElement(tag: string): Element

创建一个组件对象。

**参数：** 

| 参数名     | 类型       | 必填   | 说明      |
| ------- | ------------ | ---- | ------- |
| tag | string | 是    | 组件名称。 |

**返回值：** 

| 类型        | 说明            |
| ----------- | ------------- |
| Element | 对应tag名称的组件对象。 |

```js
let newImage = dom.createElement('image')
```


## setAttribute

setAttribute(name: string, value: string): void

动态设置组件的属性。

**参数：** 

| 参数名     | 类型       | 必填   | 说明      |
| ------- | ------------ | ---- | ------- |
| name | string | 是    | 属性名称。 |
| value | string | 是    | 属性值。 |

```js
newImage.setAttribute('src', 'common/testImage.jpg')
```


## setStyle

setStyle(name: string, value: string): boolean

动态设置组件的样式。

**参数：** 

| 参数名     | 类型       | 必填   | 说明      |
| ------- | ------------ | ---- | ------- |
| name | string |  是    | 样式名称。 |
| value | string |  是    | 样式值。 |

**返回值：** 

| 类型        | 说明            |
| ----------- | ------------- |
| boolean | 设置成功时返回true，失败时返回false。 |

```js
newImage.setStyle('width', '120px')
```


## addChild

addChild(child: Element): void

将动态创建的组件添加到父组件当中。

**参数：** 

| 参数名     | 类型       | 必填   | 说明    |
| ------- | ------------ | ---- | ------- |
| child | Element | 是    | 组件对象。 |

```js
newDiv.addChild(newImage)
```


## 示例

```html
<!-- xxx.hml -->
<div class="container">
  <div id="parentDiv" class="parent"></div>
  <button onclick="appendDiv" class="btn">动态创建div</button>
  <button onclick="appendImage" class="btn">动态创建image到创建的div中</button>
</div>
```

```css
/* xxx.css */
.container {
  flex-direction: column;
  align-items: center;
  width: 100%;
}

.parent {
  flex-direction: column;
}

.btn {
  width: 70%;
  height: 60px;
  margin: 15px;
}
```

```js
// xxx.js
let newDiv = null
let newImage = null

export default {
  appendDiv() {
    let parent = this.$element('parentDiv')
    newDiv = dom.createElement('div')
    newDiv.setStyle('width', '150px')
    newDiv.setStyle('height', '150px')
    newDiv.setStyle('backgroundColor', '#AEEEEE')
    newDiv.setStyle('marginTop', '15px')
    parent.addChild(newDiv)
  },
  appendImage() {
    newImage = dom.createElement('image')
    newImage.setAttribute('src', 'common/testImage.jpg')
    newImage.setStyle('width', '120px')
    newImage.setStyle('height', '120px')
    newDiv.addChild(newImage)
  }
}
```