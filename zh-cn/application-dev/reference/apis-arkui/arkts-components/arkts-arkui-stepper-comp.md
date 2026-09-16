# Stepper

步骤导航器组件，适用于引导用户按照步骤完成任务的导航场景。

> **说明：**

> - 从API version 8开始支持，从API version 22开始废弃，建议使用Swiper替代。详细示例请参考 > 示例2。

## 子组件

仅能包含子组件StepperItem。

## Stepper

```TypeScript
Stepper(value?: { index?: number })
```

Called when the stepper component is used.

**起始版本：** 8

**废弃版本：** 22

**替代接口：** index

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { index?: number } | 否 | Index of the **StepperItem** that is currently displayed.<br>Default value: **0**<br> Since API version 10, this parameter supports two-way binding through [&#36;&#36;](../../../ui/state-management/arkts-two-way-sync.md). |

## 汇总

## 示例

```TypeScript
### 示例1（使用Stepper）

该示例主要演示如何使用步骤导航器组件。


```

```TypeScript
### 示例2（使用Swiper替代Stepper）

该示例主要演示如何使用[Swiper](ts-container-swiper.md)组件实现Stepper组件的功能，示例效果图同示例1。
```
