# list-item-group

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong-->
<!--SE: @yylong-->
<!--TSE: @liuzhenshuo-->

>  **说明：**
>  从API version 4开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

&lt;[list](js-components-container-list.md)&gt;的子组件，用来展示分组，宽度默认充满list组件。


- 使用该组件时父元素list组件的样式columns必须为1，否则功能异常。

- 由于父元素list组件的align-items默认样式为stretch，该组件宽度默认充满list组件。设置父元素list组件的align-items样式为非stretch来生效自定义宽度。

## 权限列表

无


## 子组件

仅支持&lt;[list-item](js-components-container-list-item.md)&gt;。


## 属性

除支持[通用属性](js-components-common-attributes.md)外，还支持如下属性：

| 名称   | 类型     | 默认值     | 必填   | 描述                                       |
| ---- | ------ | ------- | ---- | ---------------------------------------- |
| type | string | default | 否    | list-item-group类型，同一list支持多种type的list-item-group，相同type的list-item-group需要确保渲染后的视图布局也完全相同，当type固定时，使用show属性代替if属性，确保视图布局不变。 |

>  **说明：**
>
>  - 通用属性中的id用来标识一个group。list中相关的函数的入参以及事件的信息皆以此标识一个唯一的group。


## 样式

除支持[通用样式](js-components-common-styles.md)外，还支持如下样式：

| 名称              | 类型     | 默认值        | 必填   | 描述                                       |
| --------------- | ------ | ---------- | ---- | ---------------------------------------- |
| flex-direction  | string | row        | 否    | flex容器主轴方向。可选项有：<br/>-&nbsp;column：垂直方向从上到下<br/>-&nbsp;row：水平方向从左到右 |
| justify-content | string | flex-start | 否    | flex容器当前行的主轴对齐格式。可选项有：<br/>-&nbsp;flex-start：项目位于容器的开头。<br/>-&nbsp;flex-end：项目位于容器的结尾。<br/>-&nbsp;center：项目位于容器的中心。<br/>-&nbsp;space-between：项目位于各行之间留有空白的容器内。<br/>-&nbsp;space-around：项目位于各行之前、之间、之后都留有空白的容器内。<br/>-&nbsp;space-evenly<sup>5+</sup>:&nbsp;&nbsp;均匀排列每个元素，每个元素之间的间隔相等。 |


## 事件

除支持[通用事件](js-components-common-events.md)外，还支持如下事件：

| 名称            | 参数                                 | 描述                                       |
| ------------- | ---------------------------------- | ---------------------------------------- |
| groupclick    | {&nbsp;groupid:&nbsp;string&nbsp;} | group点击事件。<br/>groupid：被点击的group的id。     |
| groupcollapse | {&nbsp;groupid:&nbsp;string&nbsp;} | group收拢事件。<br/>groupid：收拢的group的id。<br/>当不输入参数或者groupid为空时收拢所有分组。 |
| groupexpand   | {&nbsp;groupid:&nbsp;string&nbsp;} | group展开事件。<br/>groupid：展开的group的id。<br/>当不输入参数或者groupid为空时展开所有分组。 |


## 方法

支持[通用方法](js-components-common-methods.md)。


## 示例

```html
<!-- xxx.hml -->
<div class="doc-page">
  <list style="width: 100%;" id="mylist">
    <list-item class="top-list-item" clickeffect="false">
      <div class="item-div">
        <div class="item-child">
          <button type="capsule" value="Collapse first" onclick="collapseOne"></button>
          <button type="capsule" value="Expand first" onclick="expandOne"></button>
        </div>
        <div class="item-child">
          <button type="capsule" value="Collapse all" onclick="collapseAll"></button>
          <button type="capsule" value="Expand all" onclick="expandAll"></button>
        </div>
      </div>
    </list-item>
    <list-item-group for="listgroup in list" id="{{listgroup.value}}" ongroupcollapse="collapse" ongroupexpand="expand">
      <list-item type="item" style="background-color:#FFF0F5;height:95px;">
        <div class="item-group-child">
          <text>One---{{listgroup.value}}</text>
        </div>
      </list-item>
      <list-item type="item" style="background-color: #87CEFA;height:145px;" primary="true">
        <div class="item-group-child">
          <text>Primary---{{listgroup.value}}</text>
        </div>
      </list-item>
    </list-item-group>
  </list>
</div>
```

```css
/* xxx.css */
.doc-page {
  flex-direction: column;
}
.top-list-item {
  width:100%;
  background-color:#D4F2E7;
}
.item-div {
  flex-direction:column;
  align-items:center;
  justify-content:space-around;
  height:240px;
}
.item-child {
  width:100%;
  height:60px;
  justify-content:space-around;
  align-items:center;
}
.item-group-child {
  justify-content: center;
  align-items: center;
  width:100%;
}
```

```js
// xxx.js
import promptAction from '@ohos.promptAction';
export default {
    data: {
        direction: 'column',
        list: [],
        listAdd: []
    },
    onInit() {
        this.list = []
        this.listAdd = []
        for (var i = 1; i <= 3; i++) {
            var dataItem = {
                value: 'GROUP' + i,
            };
            this.list.push(dataItem);
        }
    },
    collapseOne(e) {
        this.$element('mylist').collapseGroup({
            groupid: 'GROUP1'
        })
    },
    expandOne(e) {
        this.$element('mylist').expandGroup({
            groupid: 'GROUP1'
        })
    },
    collapseAll(e) {
        this.$element('mylist').collapseGroup({
            groupid: ''
        })
    },
    expandAll(e) {
        this.$element('mylist').expandGroup({
            groupid: ''
        })
    },
    collapse(e) {
        promptAction.showToast({
            message: 'Close ' + e.groupid
        })
    },
    expand(e) {
        promptAction.showToast({
            message: 'Open ' + e.groupid
        })
    }
}



```

![zh-cn_image_0000001127284978](figures/zh-cn_image_0000001127284978.gif)
