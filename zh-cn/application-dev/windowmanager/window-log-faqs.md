# 窗口开发常见日志问题与定位
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 1300002错误码的定位指导

错误码1300002表示窗口状态异常或窗口对象无效。

### 子窗口调用setResizeByDragEnabled接口失败

开发者在子窗口上调用[setResizeByDragEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setresizebydragenabled14)接口设置窗口可拖拽缩放时，返回错误码1300002，无法实现拖拽缩放功能。

**典型日志信息**

通过DevEco Studio或hdc查看错误日志：

```bash
hdc shell hilog | grep -i -E "1300002|setResizeByDragEnabled"
```

典型日志示例：

``` text
SetResizeByDragEnabled: This is not main window or decor enabled sub window
```

关键信息：
- 错误码：1300002（窗口状态异常）
- 错误信息：This is not main window or decor enabled sub window
- 原因：子窗口未启用装饰栏，不支持拖拽缩放

**分析定位及解决**

**步骤1：理解setResizeByDragEnabled接口要求**

该接口用于控制是否允许通过拖拽进行窗口缩放，有以下前提条件：
- 仅支持应用主窗口和子窗口调用。 
- 主窗口仅在[自由窗口](freeform-window-overview.md#自由窗口)状态下调用可立即生效，在非[自由窗口](freeform-window-overview.md#自由窗口)状态下调用时不报错不生效，切换到[自由窗口](freeform-window-overview.md#自由窗口)状态下生效。
- 子窗口必须开启窗口装饰栏（decorEnabled=true）才能调用此接口。

**步骤2：检查子窗口创建配置**

检查创建子窗口时是否设置了窗口装饰：

```ts
// 错误示例：创建子窗口时未开启装饰栏
windowStage.createSubWindowWithOptions('mySubWindow', {
  title: "",
  decorEnabled: false,    // 未开启装饰栏
  isModal: false,
  maximizeSupported: true
})
```

**正确示例**

对于调用该接口的子窗口，要保证子窗口已开启窗口装饰栏，将SubWindowOptions中的`decorEnabled`设置为`true`。

```ts
let options: window.SubWindowOptions = {
  title: "",
  decorEnabled: true,   // 开启窗口装饰栏
  isModal: false,
  maximizeSupported: true
};
windowStage.createSubWindowWithOptions('mySubWindow', options).then((windowClass) => {
  // decorEnabled=true时可正常调用
  windowClass.setResizeByDragEnabled(true, (err: BusinessError) => {
    console.error("setResizeByDragEnabled failed.", ` code: ${err.code}, message: ${err.message}`)
  })
}            
```