# @ohos.arkui.advanced.ExceptionPrompt

异常提示，适用于有异常需要提示异常内容的情况。

> **说明：**
 >
 > - 该组件仅可在Stage模型下使用。
 >
 > - 如果ExceptionPrompt设置通用属性和通用事件，
 > 编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ExceptionPrompt本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议
 > ExceptionPrompt设置通用属性和通用事件。

## 子组件

无

## ExceptionPromptAttribute

不支持通用事件。

## 导入模块

```TypeScript
import { MarginType, PromptOptions, ExceptionPrompt } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ExceptionPrompt](arkts-arkui-arkui-advanced-exceptionprompt-exceptionprompt-s.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PromptOptions](arkts-arkui-arkui-advanced-exceptionprompt-promptoptions-i.md) | PromptOptions定义options的类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MarginType](arkts-arkui-arkui-advanced-exceptionprompt-margintype-e.md) | MarginType定义marginType的类型。 |

## 示例

```TypeScript
### 示例1（设置异常提示）

该示例展示了如何设置异常提示的异常图标、异常提示的文字、边距样式和右侧图标按钮的文字内容。


```

```TypeScript
### 示例2（设置弹窗类型的异常提示）

该示例使用自定义弹窗设置弹窗类型的异常提示。


```

```TypeScript
### 示例3（设置Symbol类型图标）

从API version 18开始，该示例通过设置PromptOptions的属性symbolStyle，展示了自定义Symbol类型图标。
```
