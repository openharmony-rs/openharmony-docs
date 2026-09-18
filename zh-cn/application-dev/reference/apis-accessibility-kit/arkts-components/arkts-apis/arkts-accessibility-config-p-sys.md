# 属性（系统接口）

## animationOff

```TypeScript
let animationOff: Config<boolean>
```

表示关闭动画功能启用状态。true表示已启用关闭动画功能，false表示未启用关闭动画功能，默认值为false。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## brightnessDiscount

```TypeScript
let brightnessDiscount: Config<number>
```

表示亮度折扣配置，用于按比例调整屏幕显示亮度。取值范围为0~1.0，0表示无亮度折扣（原始亮度），1.0表示最大亮度折扣。默认值为0.0。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## captions

```TypeScript
let captions: Config<boolean>
```

表示辅助字幕功能启用状态。true表示已启用辅助字幕功能，false表示未启用辅助字幕功能，默认值为false。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## captionsStyle

```TypeScript
let captionsStyle: Config<accessibility.CaptionsStyle>
```

表示辅助字幕样式的配置。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;[accessibility.CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## contentTimeout

```TypeScript
let contentTimeout: Config<number>
```

表示内容显示建议时长配置，用于设置无障碍提示等内容在屏幕上的持续显示时长。取值范围为0~5000，单位为毫秒。默认值为0。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## daltonizationColorFilter

```TypeScript
let daltonizationColorFilter: Config<DaltonizationColorFilter>
```

表示色彩校正颜色滤镜配置。配合daltonizationState使用，仅当daltonizationState设置为true时，此配置生效。默认值为Normal，表示正常类型。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;[DaltonizationColorFilter](arkts-accessibility-config-daltonizationcolorfilter-t-sys.md)&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## highContrastText

```TypeScript
let highContrastText: Config<boolean>
```

表示高对比度文字功能启用状态。true表示已启用高对比度文字功能，false表示未启用高对比度文字功能，默认值为false。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## invertColor

```TypeScript
let invertColor: Config<boolean>
```

表示颜色反转功能启用状态。true表示已启用颜色反转功能，false表示未启用颜色反转功能，默认值为false。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## mouseAutoClick

```TypeScript
let mouseAutoClick: Config<number>
```

表示鼠标自动点击操作的配置。取值范围为0~5000，单位为毫秒，0表示不生效，其他值表示鼠标悬停相应的时长即触发自动点击操作，默认值为0。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;number&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## mouseKey

```TypeScript
let mouseKey: Config<boolean>
```

表示鼠标键功能启用状态。true表示已启用鼠标键功能，false表示未启用鼠标键功能，默认值为false。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## shortkey

```TypeScript
let shortkey: Config<boolean>
```

表示辅助扩展快捷键功能启用状态。配合shortkeyTarget使用。true表示已启用辅助扩展快捷键功能，false表示未启用辅助扩展快捷键功能，默认值为false。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## shortkeyTarget

```TypeScript
let shortkeyTarget: Config<string>
```

表示辅助扩展快捷键的目标配置。取值为辅助扩展应用的名称，格式为：'bundleName/abilityName'。格式不正确或名称无效时，设置不生效。

**类型：** [Config](arkts-accessibility-config-config-i-sys.md)&lt;string&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。
