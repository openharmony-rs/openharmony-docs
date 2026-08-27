# GetEuiccProfileInfoListResult（系统接口）

获取配置文件信息列表。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## isRemovable

```TypeScript
isRemovable: boolean
```

eUICC是否可移除。true表示可移除，false表示不可移除。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## profiles

```TypeScript
profiles: Array<EuiccProfile>
```

配置文件数组。

**类型：** Array&lt;[EuiccProfile](arkts-telephony-esim-euiccprofile-i-sys.md)&gt;

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## responseResult

```TypeScript
responseResult: ResultCode
```

返回操作结果码。

**类型：** ResultCode

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。
