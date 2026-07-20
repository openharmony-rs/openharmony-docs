# ThemeControl

ThemeControl将自定义Theme应用于App组件内，实现App组件风格跟随Theme切换。

**起始版本：** 12

<!--Device-unnamed-export declare class ThemeControl--><!--Device-unnamed-export declare class ThemeControl-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CustomColors, ThemeControl, Colors, CustomDarkColors, Theme, CustomTheme } from '@kit.ArkUI';
```

<a id="setdefaulttheme"></a>
## setDefaultTheme

```TypeScript
static setDefaultTheme(theme: CustomTheme): void
```

将用户自定义Theme设置应用级默认主题，以实现应用风格跟随Theme切换。若在页面中使用此接口设置应用级默认主题，需确保该接口在页面build前执行。若在UIAbility中使用此接口设置应用级默认主题，需确保该接口在onWindowStageCreate阶段里windowStage.[loadContent](docroot://reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)接口调用完成的回调函数中执行。详细代码可参考[设置应用内组件自定义主题色](docroot://ui/theme_skinning.md#设置应用内组件自定义主题色)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThemeControl-static setDefaultTheme(theme: CustomTheme): void--><!--Device-ThemeControl-static setDefaultTheme(theme: CustomTheme): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| theme | [CustomTheme](arkts-arkui-customtheme-t.md) | 是 |  |

