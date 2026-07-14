# FontSettingOptions

字体配置项。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableVariableFontWeight

```TypeScript
enableVariableFontWeight?: boolean
```

是否启用可变字重调节。字体配置项作为
[fontWeight](TextAttribute#fontWeight(weight: number | FontWeight | ResourceStr, options?: FontSettingOptions))
接口的入参，fontWeight接口中weight取值为[100, 900]内非整百数值时，enableVariableFontWeight用于设置weight的值是否生效。

默认值：false

true：启用可变字重调节。此时如果weight取值为[100, 900]范围内任意整数，字重取值为weight。

false：禁用可变字重调节。此时如果weight取值为[100, 900]范围内的整百数值，字重取值为weight；weight是非整百数值时，字重取默认值400。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

