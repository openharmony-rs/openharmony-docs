# @ohos.arkui.inspector(布局回调)

提供注册组件布局和组件绘制送显完成回调通知的能力。适用于需要在组件布局或绘制送显完成后执行自定义逻辑的场景，帮助开发者精准掌控组件渲染时机。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { inspector } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createComponentObserver](arkts-arkui-inspector-createcomponentobserver-f.md) | 绑定指定组件，返回对应的监听句柄。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | 组件布局和组件绘制送显完成回调的句柄，通过该句柄可调用以下方法。 |
