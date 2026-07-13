# CheckboxGroup

多选框群组，用于控制多选框全选或者不全选状态。

> **说明：**


## CheckboxGroup

```TypeScript
CheckboxGroup(options?: CheckboxGroupOptions)
```

创建多选框群组，用于控制群组内Checkbox的全选或取消全选状态，具有相同group值的Checkbox和CheckboxGroup属于同一群组。

在结合带缓存功能的组件使用时（如[List]{@link list}），未被创建的Checkbox选中状态需要应用手动控制。详细示例请参考
[示例4](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-checkboxgroup.md#示例4设置全选)。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | CheckboxGroupOptions | 否 | 配置多选框群组参数。 <br/> 未设置时，按照CheckboxGroupOptions中各参数的默认值配置。 |

## 汇总

- [CheckBoxGroupConfiguration](arkts-arkui-checkboxgroup-checkboxgroupconfiguration-i.md)
- [CheckboxGroupOptions](arkts-arkui-checkboxgroup-checkboxgroupoptions-i.md)
- [CheckboxGroupResult](arkts-arkui-checkboxgroup-checkboxgroupresult-i.md)
- [OnCheckboxGroupChangeCallback](arkts-arkui-checkboxgroup-oncheckboxgroupchangecallback-t.md)
- [SelectStatus](arkts-arkui-checkboxgroup-selectstatus-e.md)
