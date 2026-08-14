# configure（系统接口）

## configure

```TypeScript
function configure(featureId: UserStatusFeature, detail: string): int
```

配置特性参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userStatus-function configure(featureId: UserStatusFeature, detail: string): int--><!--Device-userStatus-function configure(featureId: UserStatusFeature, detail: string): int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | 是 | 要配置的特性。 |
| detail | string | 是 | JSON格式的详细特性参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 操作成功返回0，否则返回非0值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33900001](../../apis-multimodalawareness-kit/errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes: &lt;br&gt;1. System error, such as a null pointer and container-related exception. &lt;br&gt;2. Node-API invocation exception, such as invalid Node-API status. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

