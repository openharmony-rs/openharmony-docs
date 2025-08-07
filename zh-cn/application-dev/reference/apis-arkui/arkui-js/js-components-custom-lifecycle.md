# 生命周期定义
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--SE: @jiangdayuan-->
<!--TSE: @lxl007-->

>  **说明：**
>
>  从API Version 5 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


我们为自定义组件提供了一系列生命周期回调方法，便于开发者管理自定义组件的内部逻辑。生命周期主要包括：onInit，onAttached，onDetached，onLayoutReady，onDestroy，onShow和onHide。下面我们依次介绍一下各个生命周期回调的时机。


| 属性          | 类型     | 描述               | 触发时机                                                     |
| ------------- | -------- | ------------------ | ------------------------------------------------------------ |
| onInit        | Function | 初始化自定义组件   | 自定义组件初始化生命周期回调，当自定义组件创建时，触发该回调，主要用于自定义组件中必须使用的数据初始化，该回调只会触发一次调用。 |
| onAttached    | Function | 自定义组件装载     | 自定义组件被创建后，加入到Page组件树时，触发该回调，该回调触发时，表示组件将被进行显示，该生命周期可用于初始化显示相关数据，通常用于加载图片资源、开始执行动画等场景。 |
| onLayoutReady | Function | 自定义组件布局完成 | 自定义组件插入Page组件树后，将会对自定义组件进行布局计算，调整其内容元素尺寸与位置，当布局计算结束后触发该回调。 |
| onDetached    | Function | 自定义组件卸载     | 自定义组件卸载时，触发该回调，常用于停止动画或异步逻辑停止执行的场景。 |
| onDestroy     | Function | 自定义组件销毁     | 自定义组件销毁时，触发该回调，常用于资源释放。               |
| onShow        | Function | 自定义组件Page显示 | 自定义组件所在Page显示后，触发该回调。                       |
| onHide        | Function | 自定义组件Page隐藏 | 自定义组件所在Page隐藏后，触发该回调。                       |


## 示例

```html
<!-- comp.hml -->
<div class="item">  
   <text class="text-style">{{ value }}</text>  
</div>
```

```js
//comp.js
export default {
  data: {
    value: "组件创建"
  },
  onInit() {
    console.log("组件创建")
  },
  onAttached() {
    this.value = "组件挂载",
    console.log("组件挂载")
  },
  onShow() {
    console.log("Page显示")
  },
  onHide() {
    console.log("Page隐藏")
  }
}
```
