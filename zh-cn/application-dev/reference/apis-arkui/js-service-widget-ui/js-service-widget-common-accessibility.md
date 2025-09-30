# 无障碍
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @HelloCrease-->

组件可以设置相应的无障碍属性和事件来更好地使用无障碍能力。

> **说明：**
>
> 从API Version 8 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 无障碍属性

| 名称 | 类型 | 默认值 | 描述 |
| -------- | -------- | -------- | -------- |
| accessibilitygroup | boolean | false | 无障碍组，设置为true时表示该组件及其所有子组件为一整个可以选中的组件，无障碍服务将不再关注其子组件内容；设置为false表示不启用无障碍分组。 |
| accessibilitytext | string | - | 无障碍文本，当组件不包含文本属性时，屏幕朗读选中此组件时不播报，使用者无法清楚地知道当前选中了什么组件。为了解决此场景，开发人员可为不包含文字信息的组件设置无障碍文本，当屏幕朗读选中此组件时播报无障碍文本的内容，帮助屏幕朗读的使用者清楚地知道自己选中了什么组件。若组件既拥有文本属性，又拥有无障碍文本属性，则组件被选中时，仅播报无障碍文本内容。 |
| accessibilitydescription | string | - | 无障碍说明，用于为用户进一步说明当前组件，如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从组件本身属性与无障碍文本中了解到时。开发人员可为组件的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。若组件既拥有文本属性又拥有无障碍说明属性，则组件被选中时，先播报组件的文本属性，再播报无障碍说明属性的内容。 |
| accessibilityimportance | string | auto | 无障碍重要性，用于控制某个组件是否可被无障碍辅助服务所识别。具体值可以设置为auto，yes，no和no-hide-descendants（最后一个值会使屏幕朗读忽略当前组件及其所有子组件）。若设置为yes，当前组件对无障碍辅助服务而言可选中；若设置为no，则当前组件对无障碍辅助服务来说是不可选中的。 |

- accessibilitygroup
  
  ```html
  <div accessibilitygroup="true">
    <text>text1</text>
    <text>text2</text>
  </div>
  ```

- accessibilitytext
  
  ```html
  <image src="common/image/barrierfree.jpg" accessibilitytext="这是一张风景图"></image>
  ```

- accessibilitydescription
  
  ```html
  <button accessibilitydescription="点击此按键会弹出一个对话框" onclick="DialogShow">按键</button>
  ```

- accessibilityimportance
  此情况下，div和text都不会被无障碍框选中。若想让某些默认不会被无障碍框选中的组件可以被选中，则给该组件增加一个accessibilityimportance="yes"即可。

  
  ```html
  <div accessibilityimportance="no-hide-descendants">
    <text>text</text>
  </div>
  ```


## 无障碍事件

| 名称 | 参数 | 描述 |
| -------- | -------- | -------- |
| accessibility | AbilityEvent | 无障碍服务下发的事件。 |

  **表1**AbilityEvent属性列表

| 属性 | 类型 | 说明 |
| -------- | -------- | -------- |
| eventType | number | 事件类型：<br/>-&nbsp;0：custom&nbsp;event<br/>-&nbsp;1：accessibility&nbsp;focus<br/>-&nbsp;2：clear&nbsp;accessibility&nbsp;focus<br/>无障碍系统下发的非焦点相关的事件为0，无障碍系统下发的获焦事件为1，无障碍系统下发的失焦事件为2。 |
| param | Object | 无障碍辅助应用发送自定义事件时需传入对应参数。 |
