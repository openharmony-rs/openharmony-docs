# FontWeightConfigs

字体粗细配置项。当传入该配置对象时（包括空对象{}），未显式设置的属性将使用默认值。当传入null或undefined时，不应用默认值，字体粗细行为与父组件文本保持一致。

**起始版本：** 24

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableDeviceFontWeightCategory

```TypeScript
enableDeviceFontWeightCategory?: boolean
```

是否随设备的字体粗细级别自动更新字重。

默认值：true

true：当设备的字体粗细级别发生变化时，字重会自动更新。

false：当设备的字体粗细级别发生变化时，字重不会自动更新。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableVariableFontWeight

```TypeScript
enableVariableFontWeight?: boolean
```

是否启用可变字重调节。当设置字体粗细的值weight为[100, 900]内非整百数值时，enableVariableFontWeight用于设置weight的值是否生效。

默认值：false

true：启用可变字重调节。此时如果weight取值为[100, 900]范围内任意整数，字重取值为weight，否则取默认值400。

false：禁用可变字重调节。此时如果weight取值为[100, 900]范围内的整百数值，字重取值为weight；weight是非整百数值时，字重取默认值400。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

