# 自定义组件使用说明
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1-->
<!--SE: @shiyu_huang-->
<!--TSE: @TerryTsao-->


>  **说明：**
>
> 从API Version 8 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


自定义组件是用户根据业务需求，将已有的组件组合，封装成的新组件，可以在工程中多次调用，提高代码的可读性。自定义组件通过element引入到宿主页面，使用方法：

```html
<element name='comp' src='../../common/component/comp.hml'></element>
<div>
  <comp prop1='xxxx' @child1="bindParentVmMethod"></comp>
</div>
```

- name属性指自定义组件名称(非必填)，组件名称对大小写不敏感，默认使用小写。src属性指自定义组件hml文件路径(必填)，若没有设置name属性，则默认使用hml文件名作为组件名。

- 事件绑定：自定义组件中绑定子组件事件使用(on|\@)child1语法，子组件中通过{action:"proxy", method: "eventName"}触发事件并进行传值，父组件执行bindParentVmMethod方法并接收子组件传递的参数。

## 自定义组件配置文件标签

| 属性 | 类型 | 描述 |
| -------- | -------- | -------- |
| data | Object | 页面的数据模型，类型是对象。属性名不能以$或_开头，不要使用保留字for,&nbsp;if,&nbsp;show,&nbsp;tid。 |
| props | Array/Object | props用于组件之间的通信，可以通过&lt;tag&nbsp;xxxx='value'&gt;方式传递给组件；props名称必须用小写，不能以$或_开头，不要使用保留字for,&nbsp;if,&nbsp;show,&nbsp;tid。目前props的数据类型不支持Function。 |


## 添加自定义事件

自定义组件内支持自定义事件，该事件的标识需要action类型指定为proxy，事件名则通过method指定。使用该自定义组件的卡片页面可以通过该事件名注册相应的事件回调，当自定义组件内该自定义事件触发时，会触发卡片页面上注册的回调事件。

>  **说明：**
>
>  事件名不支持大写字母。

**自定义子组件示例：**

```html
<!-- comp.hml -->
<div class="container">
    <div class="row-3" if="true">
        <button onclick="buttonClicked" value="click"></button>
    </div>
</div>
```

```css
/* comp.css */
.container {
    flex-direction:column;
    background-color: green;
    width: 100%;
    height: 100%;
}

.row-3 {
    width: 100%;
    height: 50px;
    background-color: orange;
    font-size:15px;
}
```

```json
{
    "data": {
    },
    "actions": {
        "buttonClicked": {
            "action": "proxy",        
            "method":"event_1"
        }
    }
}
```
**父组件示例：**

```html
<!-- xxx.hml --> 
<element name='comp' src='../../common/customComponent/customComponent.hml'></element>

<div class="container">
    <comp @event_1="click"></comp>
    <button value="parentClick" @click="buttonClick"></button>
</div>
```

```css
/* xxx.css */
.container {
  background-color: red;
  height: 500px;
  width: 500px;
}
```

```json
{
  "data": {
  },
  "actions": {
    "click": {
      "action": "message",
      "params": {
        "message": "click event"
      }
    },
    "buttonClick": {
      "action": "message",
      "params": {
        "message": "click event 2"
      }
    }
  }
}
```


## props

自定义组件可以通过props声明自定义属性，父组件通过设置属性向子组件传递参数。

### 添加默认值

子组件可以通过固定值default设置默认值，当父组件没有设置该属性时，将使用其默认值。此情况下props属性必须为对象形式，不能用数组形式，示例如下：

```html
<!-- comp.hml -->
<div class="container">
    <div class="row-1">
        <div class="box-1">
            <text>xiaoziti</text>
        </div>
        <div class="box-2">
            <text>{{text}}</text>
        </div>
        <div class="box-3">
            <text>{{textdata[0]}}</text>
        </div>
    </div>
    <div class="row-2" if="true">
        <button value="{{progress}}"></button>
    </div>
    <div class="row-3" if="true">
        <button onclick="buttonClicked" value="click"></button>
    </div>
</div>
```

```json
{
  "data": {
    "progress": {
      "default": "80"
    }
  },
  "props": {
    "textdata": {
      "default": ["a","b"]
    },
    "progress": {
      "default": 60
    },
    "text": {
      "default": "ha"
    }
  },
  "actions": {
    "buttonClicked": {
      "action": "proxy",
      "method": "event_1"
    }
  }
}
```

引用子组件comp的父组件示例如下：

```html
<!-- xxx.hml -->
<element name='comp' src='../../common/customComponent/customComponent.hml'></element>

<div class="container">
    <comp progress="{{clicknow}}" textdata="{{texts}}" if="false" @event_1="click"></comp>
</div>
```

### 数据单向性

父子组件之间数据的传递是单向的，只能从父组件传递给子组件，子组件不能直接修改父组件传递下来的值，可以将props传入的值用data接收后作为默认值，再对data的值进行修改。

更多说明请参考[props](../arkui-js/js-components-custom-props.md)文档。