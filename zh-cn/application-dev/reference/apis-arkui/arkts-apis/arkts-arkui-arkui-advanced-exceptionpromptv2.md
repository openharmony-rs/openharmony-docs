# @ohos.arkui.advanced.ExceptionPromptV2

异常提示V2组件，适用于有异常需要提示异常内容的情况。

该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于
 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组
 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制异常提示的数据和状态，实现更高效的用户界面刷新。

> **说明：**
 >
 > - 该组件仅可在Stage模型下使用。
 >
 > - 如果ExceptionPromptV2设置通用属性和
 > 通用事件，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到
 > ExceptionPromptV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ExceptionPromptV2设置通用属性和通用事件。

## 子组件

无

## 事件

不支持通用事件。

## 导入模块

```TypeScript
import { MarginTypeV2, PromptOptionsV2, PromptOptionsV2Config, ExceptionPromptV2 } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [PromptOptionsV2](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2-c.md) | PromptOptionsV2用于定义异常提示组件的配置信息。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ExceptionPromptV2](arkts-arkui-arkui-advanced-exceptionpromptv2-exceptionpromptv2-s.md) | 异常提示，适用于有异常需要提示异常内容的情况。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PromptOptionsV2Config](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2config-i.md) | PromptOptionsV2Config定义用于构造PromptOptionsV2对象的配置信息接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MarginTypeV2](arkts-arkui-arkui-advanced-exceptionpromptv2-margintypev2-e.md) | 异常提示的边距样式类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnActionTextClickCallback](arkts-arkui-onactiontextclickcallback-t.md) | OnActionTextClickCallback定义点击右侧图标按钮的回调函数类型。 |
| [OnTipClickCallback](arkts-arkui-ontipclickcallback-t.md) | OnTipClickCallback定义点击左侧提示文本的回调函数类型。 |

## 示例

```TypeScript
### 示例1（设置异常提示）

从API版本26.0.0开始，该示例展示了如何设置异常提示的异常图标、异常提示的文字、边距样式和右侧图标按钮的文字内容。


```

```TypeScript
### 示例2（设置弹窗类型的异常提示）

从API版本26.0.0开始，该示例使用自定义弹窗设置弹窗类型的异常提示。


```

```TypeScript
### 示例3（设置Symbol类型图标）

从API版本26.0.0开始，该示例通过设置PromptOptionsV2的属性symbolStyle，展示了自定义Symbol类型图标。
```
