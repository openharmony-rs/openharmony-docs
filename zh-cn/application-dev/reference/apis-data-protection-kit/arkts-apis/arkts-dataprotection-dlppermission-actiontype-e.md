# ActionType

表示在文件设定的权限时间到期后所执行的动作枚举，默认为NOT\_OPEN。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-dlpPermission-export enum ActionType--><!--Device-dlpPermission-export enum ActionType-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## NOT_OPEN

```TypeScript
NOT_OPEN = 0
```

表示超过权限管控时间后，用户无权限打开DLP文件。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-ActionType-NOT_OPEN = 0--><!--Device-ActionType-NOT_OPEN = 0-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## OPEN

```TypeScript
OPEN = 1
```

表示超过权限管控时间后，登录账号仍可打开DLP文件，且拥有编辑权限。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-ActionType-OPEN = 1--><!--Device-ActionType-OPEN = 1-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

