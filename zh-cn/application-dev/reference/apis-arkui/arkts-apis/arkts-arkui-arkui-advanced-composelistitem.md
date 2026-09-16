# @ohos.arkui.advanced.ComposeListItem

## 子组件

无

## 事件

不支持通用事件。

## 导入模块

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ContentItem](arkts-arkui-arkui-advanced-composelistitem-contentitem-c.md) | 列表左侧显示的图标、图标大小以及中间元素文字内容。 |
| [OperateButton](arkts-arkui-arkui-advanced-composelistitem-operatebutton-c.md) | 列表右侧按钮元素的类型。 |
| [OperateCheck](arkts-arkui-arkui-advanced-composelistitem-operatecheck-c.md) | 列表右侧元素为Switch、CheckBox、Radio的类型。 |
| [OperateIcon](arkts-arkui-arkui-advanced-composelistitem-operateicon-c.md) | 列表右侧图标元素的类型。 |
| [OperateItem](arkts-arkui-arkui-advanced-composelistitem-operateitem-c.md) | 列表右侧显示的元素类型。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ComposeListItem](arkts-arkui-arkui-advanced-composelistitem-composelistitem-s.md) | 该组件用于展示一系列宽度相同的列表项，适用于展示连续、多行的同类数据组合（如图片与文本）。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IconType](arkts-arkui-arkui-advanced-composelistitem-icontype-e.md) | 列表左侧图标类型。 |

## 示例

```TypeScript
### 示例1（设置简单列表项）

该示例实现了带有主标题、副标题、描述、右侧图标及文本的简单列表项。


```

```TypeScript
### 示例2（设置右侧不同元素自定义播报）

从API version 18开始，该示例通过设置属性accessibilityText、accessibilityDescription、accessibilityLevel，实现右侧图标、按钮、单选框自定义屏幕朗读播报文本。


```

```TypeScript
### 示例3（设置Symbol类型图标）

从API version 18开始，该示例通过设置ContentItem、OperateItem、OperateIcon的属性symbolStyle，展示了自定义Symbol类型图标。
```
