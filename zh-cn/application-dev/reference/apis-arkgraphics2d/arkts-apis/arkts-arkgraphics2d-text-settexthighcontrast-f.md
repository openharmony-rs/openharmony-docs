# setTextHighContrast

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

<a id="settexthighcontrast"></a>
## setTextHighContrast

```TypeScript
function setTextHighContrast(action : TextHighContrast): void
```

用于设置文字渲染高对比度模式。

该接口设置后整个进程都会生效，进程内所有页面共用相同模式。

可调用此接口设置，也可通过系统设置界面中**高对比度文字配置开关**进行开启/关闭。使用此接口设置开启/关闭文字渲染高对比度配置的优先级高于系统开关设置。

该接口针对应用的文字自绘制场景不生效。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-text-function setTextHighContrast(action : TextHighContrast): void--><!--Device-text-function setTextHighContrast(action : TextHighContrast): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [TextHighContrast](arkts-arkgraphics2d-text-texthighcontrast-e.md) | 是 | 文字渲染高对比度模式。 |

**示例：**

```TypeScript
text.setTextHighContrast(text.TextHighContrast.TEXT_APP_DISABLE_HIGH_CONTRAST)

```

