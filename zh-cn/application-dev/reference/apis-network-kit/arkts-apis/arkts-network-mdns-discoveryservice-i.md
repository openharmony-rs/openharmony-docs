# DiscoveryService

指定服务类型的发现服务对象。

**起始版本：** 10

<!--Device-mdns-export interface DiscoveryService--><!--Device-mdns-export interface DiscoveryService-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## 导入模块

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## off('discoveryStart')

```TypeScript
off(type: 'discoveryStart', callback?: Callback<DiscoveryEventInfo>): void
```

取消开启监听MDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-off(type: 'discoveryStart', callback?: Callback<DiscoveryEventInfo>): void--><!--Device-DiscoveryService-off(type: 'discoveryStart', callback?: Callback<DiscoveryEventInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoveryStart' | 是 | 取消订阅的事件，固定为'discoveryStart'。 <br>discoveryStart：开始搜索局域网内的MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | 否 | MDNS服务的信息和事件错误信息。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订 阅。<br>**起始版本：** 11 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 参考mdns.createDiscoveryService。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('discoveryStart', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();

discoveryService.off('discoveryStart', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});
```

## off('discoveryStop')

```TypeScript
off(type: 'discoveryStop', callback?: Callback<DiscoveryEventInfo>): void
```

取消订阅停止监听MDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-off(type: 'discoveryStop', callback?: Callback<DiscoveryEventInfo>): void--><!--Device-DiscoveryService-off(type: 'discoveryStop', callback?: Callback<DiscoveryEventInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoveryStop' | 是 | 取消订阅的事件'discoveryStop'。 <br>discoveryStop：停止搜索局域网内的MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | 否 | MDNS服务的信息和事件错误信息。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订 阅。<br>**起始版本：** 11 |

## off('serviceFound')

```TypeScript
off(type: 'serviceFound', callback?: Callback<LocalServiceInfo>): void
```

取消订阅发现MDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-off(type: 'serviceFound', callback?: Callback<LocalServiceInfo>): void--><!--Device-DiscoveryService-off(type: 'serviceFound', callback?: Callback<LocalServiceInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceFound' | 是 | 取消订阅的事件，固定为'serviceFound'。 <br>serviceFound：发现MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 否 | MDNS服务的信息。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订 阅。<br>**起始版本：** 11 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 参考mdns.createDiscoveryService。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceFound', (data: mdns.LocalServiceInfo) => {
  console.info('serviceFound', JSON.stringify(data));
  mdns.resolveLocalService(context, data, (error: BusinessError, resolveData: mdns.LocalServiceInfo) =>  {
    console.info('serviceFound', JSON.stringify(resolveData));
  });
});

discoveryService.stopSearchingMDNS();

discoveryService.off('serviceFound', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});
```

## off('serviceLost')

```TypeScript
off(type: 'serviceLost', callback?: Callback<LocalServiceInfo>): void
```

取消订阅移除MDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-off(type: 'serviceLost', callback?: Callback<LocalServiceInfo>): void--><!--Device-DiscoveryService-off(type: 'serviceLost', callback?: Callback<LocalServiceInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceLost' | 是 | 取消订阅的事件，固定为'serviceLost'。 <br>serviceLost：移除MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 否 | MDNS服务的信息。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 参考mdns.createDiscoveryService。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceLost', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();

discoveryService.off('serviceLost', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});
```

## on('discoveryStart')

```TypeScript
on(type: 'discoveryStart', callback: Callback<DiscoveryEventInfo>): void
```

订阅开启监听mDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-on(type: 'discoveryStart', callback: Callback<DiscoveryEventInfo>): void--><!--Device-DiscoveryService-on(type: 'discoveryStart', callback: Callback<DiscoveryEventInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoveryStart' | 是 | 订阅事件，固定为'discoveryStart'。 <br>discoveryStart：开始搜索局域网内的MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | 是 | MDNS服务的信息和事件错误信息。<br>**起始版本：** 11 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 参考mdns.createDiscoveryService。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('discoveryStart', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();
```

## on('discoveryStop')

```TypeScript
on(type: 'discoveryStop', callback: Callback<DiscoveryEventInfo>): void
```

订阅停止监听MDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-on(type: 'discoveryStop', callback: Callback<DiscoveryEventInfo>): void--><!--Device-DiscoveryService-on(type: 'discoveryStop', callback: Callback<DiscoveryEventInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoveryStop' | 是 | 订阅事件，固定为'discoveryStop'。 <br>discoveryStop：停止搜索局域网内的MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | 是 | MDNS服务的信息和事件错误信息。<br>**起始版本：** 11 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 参考mdns.createDiscoveryService。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('discoveryStop', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();
```

## on('serviceFound')

```TypeScript
on(type: 'serviceFound', callback: Callback<LocalServiceInfo>): void
```

订阅发现MDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-on(type: 'serviceFound', callback: Callback<LocalServiceInfo>): void--><!--Device-DiscoveryService-on(type: 'serviceFound', callback: Callback<LocalServiceInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceFound' | 是 | 订阅事件，固定为'serviceFound'。 <br>serviceFound：发现MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 是 | MDNS服务的信息，需调用resolveLocalService解析这个MDNS服务信息。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 参考mdns.createDiscoveryService。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceFound', (data: mdns.LocalServiceInfo) => {
  console.info('serviceFound', JSON.stringify(data));
  mdns.resolveLocalService(context, data, (error: BusinessError, resolveData: mdns.LocalServiceInfo) =>  {
    console.info('serviceFound', JSON.stringify(resolveData));
  });
});

discoveryService.stopSearchingMDNS();
```

## on('serviceLost')

```TypeScript
on(type: 'serviceLost', callback: Callback<LocalServiceInfo>): void
```

订阅移除MDNS服务的通知。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-on(type: 'serviceLost', callback: Callback<LocalServiceInfo>): void--><!--Device-DiscoveryService-on(type: 'serviceLost', callback: Callback<LocalServiceInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceLost' | 是 | 订阅事件，固定为'serviceLost'。 <br>serviceLost：移除MDNS服务事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 是 | MDNS服务的信息。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 参考mdns.createDiscoveryService。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceLost', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();
```

## startSearchingMDNS

```TypeScript
startSearchingMDNS(): void
```

开始搜索局域网内的MDNS服务。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-startSearchingMDNS(): void--><!--Device-DiscoveryService-startSearchingMDNS(): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**示例**

Stage模型示例：

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 获取context。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();
```

## stopSearchingMDNS

```TypeScript
stopSearchingMDNS(): void
```

停止搜索局域网内的MDNS服务。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DiscoveryService-stopSearchingMDNS(): void--><!--Device-DiscoveryService-stopSearchingMDNS(): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**示例**

Stage模型示例：

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 获取context。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.stopSearchingMDNS();
```

