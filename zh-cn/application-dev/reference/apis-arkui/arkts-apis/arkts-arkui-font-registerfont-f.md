# registerFont

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## registerFont

```TypeScript
function registerFont(options: FontOptions): void
```

在字体管理中注册自定义字体。

该接口为异步接口，不支持并发调用。

> **说明：**  
>  
> -registerFont需要先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取  
> [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用registerFont可能导致  
> [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的  
> [Font](arkts-arkui-uicontext.md)对象。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** registerFont

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-font-function registerFont(options: FontOptions): void--><!--Device-font-function registerFont(options: FontOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FontOptions](arkts-arkui-font-fontoptions-i.md) | 是 | 注册的自定义字体信息。 |

