# WithThemeAttribute

不支持通用属性和通用事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface WithThemeAttribute--><!--Device-unnamed-export declare interface WithThemeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyAttributesFinish

```TypeScript
applyAttributesFinish(): void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-WithThemeAttribute-applyAttributesFinish(): void--><!--Device-WithThemeAttribute-applyAttributesFinish(): void-End-->

## debugLine

```TypeScript
debugLine(sourceLine: string, moduleName?: string): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-WithThemeAttribute-debugLine(sourceLine: string, moduleName?: string): this--><!--Device-WithThemeAttribute-debugLine(sourceLine: string, moduleName?: string): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceLine | string | 是 |  |
| moduleName | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setWithThemeOptions

```TypeScript
setWithThemeOptions(options: WithThemeOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-WithThemeAttribute-setWithThemeOptions(options: WithThemeOptions | undefined): this--><!--Device-WithThemeAttribute-setWithThemeOptions(options: WithThemeOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WithThemeOptions](arkts-arkui-withtheme-withthemeoptions-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

通知组件已完成设置其属性。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithThemeAttribute-default--><!--Device-WithThemeAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

