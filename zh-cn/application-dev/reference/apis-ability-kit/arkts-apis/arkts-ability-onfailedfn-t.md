# OnFailedFn

```TypeScript
type OnFailedFn = (code: int) => void
```

与指定的后台服务建立连接失败时，会触发该回调，返回连接失败的错误码。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-type OnFailedFn = (code: int) => void--><!--Device-unnamed-type OnFailedFn = (code: int) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 连接指定Ability失败返回的错误码。 错误码详细介绍请参考\_\_\_MD\_LINK\_USD\_0\_\_\_和\_\_\_MD\_LINK\_USD\_1\_\_\_。 201 - The application does not have permission to call the interface. 16000001 - The specified ability does not exist. 16000002 - Incorrect ability type. 16000004 - Cannot start an invisible component. 16000005 - The specified process does not have the permission. 16000006 - Cross-user operations are not allowed. 16000008 - The crowdtesting application expires. 16000053 - The ability is not on the top of the UI. 16000055 - Installation-free timed out. 16000050 - Internal error.  |

