# If (ArkTS-Sta)

ArkTS-Sta提供了渲染控制能力。条件渲染可根据应用状态，使用If组件配合其属性渲染相应的UI内容。

> **说明：**
> 
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

开发者指南见：[ArkTS-Sta If 开发者指南](../../../ui/state-management/arkts-rendering-control-ifelse-sta.md)。

## 导入模块

```ts
import { If } from '@ohos.arkui.component';
```

## 接口

If(condition: boolean)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明 |
| ------ | ---------- | -------- | -------- |
| condition  | boolean | 是 | 分支判断条件。<br>true: 执行该分支的UI描述。<br>false: 不执行该分支的UI描述。 |

**示例：**
```ts
If(true) {
    Text('true condition')
}
```

## 属性

### ElseIf

ElseIf(condition: boolean)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明 |
| ------ | ---------- | -------- | -------- |
| condition  | boolean | 是 | 分支判断条件。<br>true: 执行该分支的UI描述。<br>false: 不执行该分支的UI描述。 |

**示例：**
```ts
If(false) {
    Text('false condition')
}.ElseIf(false) {
    Text('false condition')
}.ElseIf(true) {
    Text('true condition')
}
```

### Else

Else()

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**
```ts
If(false) {
    Text('false condition')
}.Else() {
    Text('true condition')
}

If(false) {
    Text('false condition')
}.ElseIf(false) {
    Text('false condition')
}.Else() {
    Text('true condition')
}
```