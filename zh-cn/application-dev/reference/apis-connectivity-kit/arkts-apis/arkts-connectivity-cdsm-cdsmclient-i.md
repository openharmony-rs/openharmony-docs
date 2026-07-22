# CdsmClient

管理CDSM客户端实例。在调用任何CDSM客户端方法之前，您必须使用{@link createCdsmClient}来创建CDSM客户端实例。

**起始版本：** 26.0.0

<!--Device-cdsm-interface CdsmClient--><!--Device-cdsm-interface CdsmClient-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## getCdsmInfo

```TypeScript
getCdsmInfo(): CdsmInfo
```

获取合作设备集合信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmClient-getCdsmInfo(): CdsmInfo--><!--Device-CdsmClient-getCdsmInfo(): CdsmInfo-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md) | 返回合作设备集信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

## offCdsmInfoChange

```TypeScript
offCdsmInfoChange(callback?: Callback<CdsmInfo>): void
```

取消订阅协作设备集信息变更事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmClient-offCdsmInfoChange(callback?: Callback<CdsmInfo>): void--><!--Device-CdsmClient-offCdsmInfoChange(callback?: Callback<CdsmInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;CdsmInfo&gt; | 否 | 用于监听合作设备集信息的回调。 |

## onCdsmInfoChange

```TypeScript
onCdsmInfoChange(callback: Callback<CdsmInfo>): void
```

订阅协作设备集信息变更事件。

只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CdsmClient-onCdsmInfoChange(callback: Callback<CdsmInfo>): void--><!--Device-CdsmClient-onCdsmInfoChange(callback: Callback<CdsmInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;CdsmInfo&gt; | 是 | 用于监听合作设备集信息的回调。 |

