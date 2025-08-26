# @ohos.inputMethod.Panel (输入法面板)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

本模块提供对输入法面板的属性管理。

> **说明：**
>
>本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
```

## PanelInfo

输入法面板属性信息。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | [PanelType](#paneltype) | 是 | 输入法面板类型。 |
| flag | [PanelFlag](#panelflag) | 否 | 输入法面板状态类型。<br/>- 默认值为固定态。<br/>- 当前仅用于描述软键盘类型的面板的状态。 |

##  PanelType

输入法面板类型枚举。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

| 名称          | 值   | 说明         |
| ------------- | ---- | ------------ |
| SOFT_KEYBOARD | 0    | 软键盘类型。 |
| STATUS_BAR    | 1    | 状态栏类型。 |

##  PanelFlag

输入法面板状态类型枚举。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

| 名称           | 值   | 说明                                                         |
| -------------- | ---- | ------------------------------------------------------------ |
| FLAG_FIXED     | 0    | 固定态面板类型。                                             |
| FLAG_FLOATING  | 1    | 悬浮态面板类型。                                             |
| FLAG_CANDIDATE | 2    | 候选词态面板类型。<br/>- 当输入面板为候选词态时，面板为显示用户输入候选词的窗口。<br/>- 输入法服务不会主动控制候选词态面板的显示和隐藏，需要开发者根据情况自行控制。 |
