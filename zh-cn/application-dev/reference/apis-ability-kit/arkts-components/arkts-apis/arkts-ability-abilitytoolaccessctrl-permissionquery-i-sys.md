# PermissionQuery（系统接口）

```TypeScript
interface PermissionQuery
```

权限查询信息。

**起始版本：** 26.0.0

<!--Device-abilityToolAccessCtrl-interface PermissionQuery--><!--Device-abilityToolAccessCtrl-interface PermissionQuery-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## callerTokenId

```TypeScript
callerTokenId?: number
```

主叫token标识。取值范围：(-∞,+∞)。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-PermissionQuery-callerTokenId?: long--><!--Device-PermissionQuery-callerTokenId?: long-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## domainId

```TypeScript
domainId?: string
```

域ID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-PermissionQuery-domainId?: string--><!--Device-PermissionQuery-domainId?: string-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## needTicket

```TypeScript
needTicket?: boolean
```

是否需要ticket

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-PermissionQuery-needTicket?: boolean--><!--Device-PermissionQuery-needTicket?: boolean-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## operationInfo

```TypeScript
operationInfo: OperationInfo[]
```

操作信息列表。

**类型：** [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-PermissionQuery-operationInfo: OperationInfo[]--><!--Device-PermissionQuery-operationInfo: OperationInfo[]-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## remoteInfo

```TypeScript
remoteInfo?: RemoteInfo
```

远端设备信息。

**类型：** [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-PermissionQuery-remoteInfo?: RemoteInfo--><!--Device-PermissionQuery-remoteInfo?: RemoteInfo-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## ticketExpireTimeMs

```TypeScript
ticketExpireTimeMs?: number
```

凭据过期时间，单位为毫秒。取值范围：(-∞,+∞)。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-PermissionQuery-ticketExpireTimeMs?: long--><!--Device-PermissionQuery-ticketExpireTimeMs?: long-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。
