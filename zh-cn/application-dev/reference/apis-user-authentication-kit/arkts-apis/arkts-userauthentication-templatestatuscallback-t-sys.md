# TemplateStatusCallback（系统接口）

```TypeScript
type TemplateStatusCallback = (templateStatusList: TemplateStatus[]) => void
```

回调函数，用于接收模板状态变化通知。当模板状态发生变化（如添加、删除、有效性变更等）时，系统会通过此回调通知应用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateStatusList | TemplateStatus[] | 是 | 模板状态列表。包含当前用户下所有已注册模板的状态信息，应用可根据列表中的isValid字段判断模板有效性，根据isConfirmed字段判断数据是否为实时数据。 |

