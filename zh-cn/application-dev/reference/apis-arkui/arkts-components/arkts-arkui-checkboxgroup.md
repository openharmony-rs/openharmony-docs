# CheckboxGroup

多选框群组，用于控制多选框全选或取消全选状态。适用于需要批量管理多个Checkbox选择状态的场景，如列表项批量选择、表单全选等，可简化用户操作，提升交互体验。 > **说明：**

## 子组件 无

## CheckboxGroup

```TypeScript
CheckboxGroup(options?: CheckboxGroupOptions)
```

创建多选框群组，用于控制群组内Checkbox的全选或取消全选状态，具有相同group值的Checkbox和CheckboxGroup属于同一群组。 在结合带缓存功能的组件使用时（如[List]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_），未被创建的Checkbox选中状态需要应用手动控制。详细示例请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CheckboxGroupInterface-(options?: CheckboxGroupOptions): CheckboxGroupAttribute--><!--Device-CheckboxGroupInterface-(options?: CheckboxGroupOptions): CheckboxGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 配置多选框群组参数。 \_\_\_HTML\_TAG\_USD\_0\_\_\_ 未设置时，按照CheckboxGroupOptions中各参数的默认值配置。  |

## 汇总

