# Agent输入管控
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

Agent输入管控用于设置组件对Agent生成输入事件的管控级别，适用于需要限制Agent生成输入事件对敏感或关键组件进行操作的场景，可提升应用对Agent输入操作的可控性。

**起始版本：** 26.1.0

## agentControlMode

agentControlMode(value: AgentControlMode | undefined): T

设置组件对Agent生成事件的输入管控级别。Agent生成的事件包括系统Agent生成的事件，以及具有ohos.permission.CONTROL_COMPONENT权限的应用注入的事件。该设置不影响用户生成的输入事件或其他注入事件。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | [AgentControlMode](ts-appendix-enums.md#agentcontrolmode)&nbsp;\|&nbsp;undefined | 是 | Agent生成事件的输入管控级别。value为undefined时，表示不设置管控级别，组件对Agent生成事件的处理与未设置该属性时保持一致（默认允许Agent生成事件注入）。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件，可用于链式调用。 |
