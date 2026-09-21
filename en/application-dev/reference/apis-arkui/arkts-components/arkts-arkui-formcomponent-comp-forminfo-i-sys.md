# FormInfo (System API)

```TypeScript
declare interface FormInfo
```

Provides the widget information.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ability

```TypeScript
ability: string
```

Ability name of the widget.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bundle

```TypeScript
bundle: string
```

Bundle name of the widget.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## dimension

```TypeScript
dimension?: FormDimension
```

Dimensions of the widget. The 2 x 2, 4 x 4, 4 x 2, and more options are available.

Default value: **Dimension_2_2**

**Type:** [FormDimension](arkts-arkui-formcomponent-comp-formdimension-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## exemptAppLock

```TypeScript
exemptAppLock?: boolean
```

Whether the widget is exempt from app lock. **true**: The widget is exempt from app lock management. No app lock overlay is displayed when an app lock is applied to the host application. **false**: The widget is managed by app lock. The app lock overlay is displayed when an app lock is applied to the host application.

Default value: **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## id

```TypeScript
id: number | string
```

Widget ID. Set this parameter to **0** for a new widget.

**NOTE:** 

Different widget hosts cannot use the same ID.

If a widget host uses the same ID for two widgets, the one added later is displayed.

**Type:** number &#124; string

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## module

```TypeScript
module: string
```

Module name of the widget.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Widget name.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## renderingMode

```TypeScript
renderingMode?: FormRenderingMode
```

Widget rendering mode. Default value: **FULL_COLOR**. The options are as follows:

- **FULL_COLOR**: full color mode, where the widget framework does not change the widget effect, which means that  
the widget is displayed in the effect as you set it.  
- **SINGLE_COLOR**: single color mode, where the widget framework sets the widget background to transparent. In  
this mode you need to set the widget style based on the best practices.

**NOTE:** 

If the system does not support unified rendering, the widget framework does not set the widget background to transparent in single color mode.

**Type:** [FormRenderingMode](arkts-arkui-formcomponent-comp-formrenderingmode-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## shape

```TypeScript
shape?: FormShape
```

The shape of the form.

**Type:** [FormShape](arkts-arkui-formcomponent-comp-formshape-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## temporary

```TypeScript
temporary?: boolean
```

Whether the widget is a temporary widget. **true**: The widget is a temporary widget. **false**: The widget is not a temporary widget.

Default value: **false**.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

The want of the form.

**Type:** import('../api/@ohos.app.ability.Want').default

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
