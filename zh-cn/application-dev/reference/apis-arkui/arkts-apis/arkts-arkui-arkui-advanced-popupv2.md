# @ohos.arkui.advanced.PopupV2

## 导入模块

```TypeScript
import { PopupV2, PopupV2InitInfo, PopupV2Button } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [PopupV2](arkts-arkui-arkui-advanced-popupv2-popupv2-f.md) | PopupV2用于显示特定样式的气泡，适用于提示信息、操作确认或信息通知等需要用户关注或响应的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PopupV2Button](arkts-arkui-arkui-advanced-popupv2-popupv2button-i.md) | PopupV2Button定义按钮的相关属性和事件。 |
| [PopupV2InitInfo](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md) | 定义PopupV2的具体样式参数。 |

## 示例

```TypeScript
### 示例1（设置气泡样式）

该示例通过配置[titleModifier](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)、[messageModifier](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)、[PopupV2Button](arkts-arkui-arkui-advanced-popupv2-popupv2button-i.md)实现气泡样式。

从API版本26.0.0开始，新增titleModifier、messageModifier、PopupV2Button。


```

```TypeScript
### 示例2（设置布局方向）

该示例通过配置[direction](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)实现镜像布局效果，适用于国际化场景下的RTL（从右到左）布局需求。

从API版本26.0.0开始，新增direction参数。


```

```TypeScript
### 示例3（设置自定义宽度）

该示例通过配置[maxWidth](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md)实现自定义宽度效果，适用于内容较长的消息通知等需要调整显示宽度的场景。

从API版本26.0.0开始，新增maxWidth参数。
```
