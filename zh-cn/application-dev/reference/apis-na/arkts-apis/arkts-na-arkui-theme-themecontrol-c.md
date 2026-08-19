# ThemeControl

ThemeControl将自定义Theme应用于App组件内，实现App组件风格跟随Theme切换。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ThemeControl--><!--Device-unnamed-export declare class ThemeControl-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## setDefaultTheme

```TypeScript
static setDefaultTheme(theme: CustomTheme | undefined): void
```

将用户自定义Theme设置应用级默认主题，以实现应用风格跟随Theme切换。 需确保在页面build前执行。因运行于静态类型上下文中的ArkTS不存在全局作用域，因此需要在入口组件的static闭包或aboutToAppear生命周期函数中调用该接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ThemeControl-static setDefaultTheme(theme: CustomTheme | undefined): void--><!--Device-ThemeControl-static setDefaultTheme(theme: CustomTheme | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| theme | [CustomTheme](../../apis-arkui/arkts-apis/arkts-arkui-arkui-theme-customtheme-i.md) \| undefined | 是 |  |

