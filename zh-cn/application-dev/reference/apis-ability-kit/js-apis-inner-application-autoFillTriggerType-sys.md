# AutoFillTriggerType (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

自动填充服务的拉起类型，通过用户手势操作来选择不同的自动填充服务拉起方式。

> **说明：**
>
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口仅可在Stage模型下使用。
> - 本模块接口为系统接口。

## 导入模块

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## AutoFillTriggerType

表示自动填充服务的拉起类型，共定义三种自动填充服务拉起方式，包括AUTO_REQUEST、MANUAL_REQUEST、PASTE_REQUEST。AutoFillTriggerType是[FillRequest.triggerType](./js-apis-inner-application-autoFillRequest-sys.md#fillrequest)系统接口的枚举类型。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

| 名称           | 值  | 说明                               |
| -------------- | --- | --------------------------------- |
| AUTO_REQUEST | 0 | 自动拉起自动填充服务，可通过[TextInput](../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)控件获焦后自动拉起。 |
| MANUAL_REQUEST | 1 | 手动拉起自动填充服务，可通过长按任意输入控件弹出二级菜单，选择自动填充，拉起自动填充服务。 |
| PASTE_REQUEST | 2 | 粘贴拉起自动填充服务，可通过在密码保险箱内长按用户名或密码选择安全复制后，再长按任意输入控件弹出二级菜单，选择粘贴，拉起自动填充服务。 |
