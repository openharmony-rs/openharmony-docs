# Participant（系统接口）

端云共享的参与者。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## attachInfo

```TypeScript
attachInfo?: string
```

附加信息，用于扩展额外的参与者信息。如用于参与者身份校验的校验码等，默认为空字符串。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## identity

```TypeScript
identity: string
```

参与者的ID。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## privilege

```TypeScript
privilege?: Privilege
```

指定的共享数据权限。默认为Privilege的默认值。

**类型：** Privilege

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## role

```TypeScript
role?: Role
```

参与者的角色，为邀请者或被邀请者。默认为undefined。

**类型：** Role

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state?: State
```

共享的状态。默认为undefined。

**类型：** State

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

