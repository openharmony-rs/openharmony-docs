# FormInfo（系统接口）

卡片信息。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## ability

```TypeScript
ability: string
```

目标卡片Ability名称。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bundle

```TypeScript
bundle: string
```

目标卡片包名。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## dimension

```TypeScript
dimension?: FormDimension
```

卡片尺寸，支持2 * 2，4 * 4，2 * 4等类型卡片。默认值：Dimension_2_2。

**类型：** [FormDimension](arkts-arkui-formdimension-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## exemptAppLock

```TypeScript
exemptAppLock?: boolean
```

卡片是否豁免应用锁，true表示卡片所属应用添加应用锁时，不受应用锁管控，不显示应用锁蒙层；false表示卡片所属应用添加应用锁时，受应用锁管控，正常展示应用锁蒙层。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: number | string
```

卡片标识（新建卡片填0）。  
**说明：**不同使用方不可使用相同id。同一使用方使用相同id时，显示后添加的卡片。id大于等于0小于2^32。

**类型：** number \| string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## module

```TypeScript
module: string
```

卡片模块名称。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

卡片名称。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## renderingMode

```TypeScript
renderingMode?: FormRenderingMode
```

卡片渲染模式。取值如下，默认值为 FULL_COLOR。  
- FULL_COLOR：代表全色模式，卡片框架不会对卡片效果做出修改，保持和卡片开发者设置的效果不变。  
- SINGLE_COLOR：代表单色模式，卡片框架会把卡片背景设为透明，开发者需按最佳实践设置卡片风格。  
**说明：**如果系统不支持统一渲染模式，卡片框架在单色模式下也不会把卡片背景设为透明。

**类型：** [FormRenderingMode](arkts-arkui-formrenderingmode-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## shape

```TypeScript
shape?: FormShape
```

卡片的形状。

**类型：** [FormShape](arkts-arkui-formshape-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## temporary

```TypeScript
temporary?: boolean
```

卡片是否为临时卡片，true表示是临时卡片，false表示不是临时卡片。默认值：false。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

卡片传递信息的载体。

**类型：** import('../api/@ohos.app.ability.Want').default

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
