# getUIFontConfig

## 导入模块

```TypeScript
import { font } from '@kit.ArkUI';
```

## getUIFontConfig

```TypeScript
function getUIFontConfig(): UIFontConfig
```

获取系统字体配置文件的UI字体配置信息。常用于需要分析或查看系统字体配置的场景，例如：字体管理工具、字体调试与诊断、字体配置信息展示等。

该接口仅支持获取配置文件内的信息以及当UI上下文不明确时可能返回undefined，如需获取全量的字体配置信息，推荐使用字体引擎的[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md)接口获取系统最新支持的字体列表数据。

> **说明：** 
> 
> 需要先通过[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[getFont](arkts-arkui-arkui-uicontext-uicontext-c.md#getfont)方法获取
> [Font](arkts-arkui-arkui-uicontext-uicontext-c.md)对象，然后通过该对象进行调用。且直接使用getUIFontConfig可能导致
> [UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | UI font configuration of the system, including the font directory, generic font group, and fallback font group. |
