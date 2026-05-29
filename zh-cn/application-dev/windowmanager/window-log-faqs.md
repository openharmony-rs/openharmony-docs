# 窗口开发常见日志问题与定位
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @liangryan-->
<!--Designer: @liangryan-->
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

检查创建子窗口时是否在SubWindowOptions中将`decorEnabled`设置为`true`。

对于调用该接口的子窗口，要保证子窗口已开启窗口装饰栏。

**正反案例**

错误示例

```ts
windowStage.createSubWindowWithOptions('mySubWindow', {
  title: "",
  decorEnabled: false,    // 错误：未开启装饰栏
  isModal: false,
  maximizeSupported: true
})
```

正确示例

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