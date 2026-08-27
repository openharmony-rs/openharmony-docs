# CdsmClient

CDSM客户端类，提供了获取远端设备的合作设备集合信息等操作方法。  
- 使用该类的方法前，需通过[cdsm.createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md)方法构造该类的实例。  
适用于需要获知一组星闪设备（合作设备集合）的成员组成及连接状态变化并据此进行业务联动的场景。例如，手机与耳机配对后，手机可通过CDSM查询左右耳机信息并感知其连接状态变化。同一应用针对同一远端设备创建一个 [CdsmClient](#cdsmclient) 实例即可，重复创建会增加不必要的资源开销。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## getCdsmInfo

```TypeScript
getCdsmInfo(): CdsmInfo
```

查询远端设备的合作设备集合信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md) | 远端设备的合作设备集合信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## offCdsmInfoChange

```TypeScript
offCdsmInfoChange(callback?: Callback<CdsmInfo>): void
```

取消订阅远端设备合作设备集合信息变化事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md)&gt; | 否 | 事件回调类型，返回远端设备合作设备集合信息。 填写该参数则取消当前callback订阅。不填写该参数则取消远端设备合作设备集合信息变化事件对应的所有回调。 |

## onCdsmInfoChange

```TypeScript
onCdsmInfoChange(callback: Callback<CdsmInfo>): void
```

订阅远端设备合作设备集合信息变化事件。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md)&gt; | 是 | 事件回调类型，返回远端设备合作设备集合信息。 |
