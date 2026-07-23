# @ohos.nearlink.ssap (星闪SSAP连接能力)(系统接口)
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->


本模块提供了SSAP（星闪服务交互协议 SparkLink Service Access Protocol）连接功能。


**起始版本：** 26.0.0

> **说明：**
>
> 本模块接口为系统接口。


## 导入模块

```typescript
import { ssap } from '@kit.ConnectivityKit';
```


## Client

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base


### setPropertyIndication

setPropertyIndication(property: Property, enable: boolean): Promise&lt;void&gt;

启用或禁用属性值更改时的指示。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| property | [Property](js-apis-nearlink-ssap.md#property) | 是 | 服务端属性。 |
| enable | boolean | 是 | 是否启用属性值。true: 启用属性值更改。false: 禁用属性值更改。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[NearLink错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100030 | The connection is not established. |
| 36100043 | Invalid UUID in property. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

**示例：** 
```typescript
import { ssap } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let addr: string = '00:11:22:33:AA:FF'; // 扫描获取到的远端设备地址
let client: ssap.Client;
try {
  let arrayBufferProperty = new ArrayBuffer(1);
  let properV = new Uint8Array(arrayBufferProperty);
  properV[0] = 1;
  let property: ssap.Property = {
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    value: arrayBufferProperty
  };
  client = ssap.createClient(addr);
  client.setPropertyIndication(property, true).then(() => {
    console.info('setPropertyIndication successfully');
  }).catch ((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### callMethod

callMethod(method: Method): Promise&lt;Method&gt;

调用服务端方法。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| method | [Method](#method) | 是 | 服务端方法。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[Method](#method)&gt; | Promise对象，返回Method对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[NearLink错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100043 | Invalid UUID. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

**示例：** 
```typescript
import { ssap } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let addr: string = '00:11:22:33:AA:FF'; // 扫描获取到的远端设备地址
let client: ssap.Client;
try {
  client = ssap.createClient(addr); // 一个应用针对一个远端设备只需要创建一次实例
  client.connect().then(() => {
    console.info('connect success');
  }).catch ((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
  let arrayBufferC = new ArrayBuffer(8);
  let method: ssap.Method = { // 这里要求method对应的服务发现时对端Service里带的method
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    methodUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    parameter: arrayBufferC
  };
  // 连接耗时较长，等待连接完成才能获取服务，实际开发者根据连接速度调整定时器长度
  setTimeout(() => {
    client.callMethod(method).then((result: ssap.Method) => {
      console.info('callMethod successfully: ' + JSON.stringify(result));
    }).catch ((err: BusinessError) => {
      console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
    });
  }, 3000);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### readDescriptor

readDescriptor(descriptor: PropertyDescriptor): Promise&lt;PropertyDescriptor&gt;

读取服务端描述符。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [PropertyDescriptor](js-apis-nearlink-ssap.md#propertydescriptor) | 是 | 服务端属性描述符。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PropertyDescriptor](js-apis-nearlink-ssap.md#propertydescriptor)&gt; | Promise对象，返回服务端属性描述符对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[NearLink错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100043 | Invalid UUID in descriptor. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

**示例：** 
```typescript
import { ssap } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let addr: string = '00:11:22:33:AA:FF'; // 扫描获取到的远端设备地址
let client: ssap.Client;
try {
  client = ssap.createClient(addr); // 一个应用针对一个远端设备只需要创建一次实例
  client.connect().then(() => {
    console.info('connect success');
  }).catch ((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
  let arrayBufferC = new ArrayBuffer(8);
  let descriptor: ssap.PropertyDescriptor = { // 这里要求descriptor对应的服务发现时对端Service里带的descriptor
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    value: arrayBufferC,
    descriptorType: ssap.PropertyDescriptorType.PROPERTY,
    isWriteable: true
  };
  // 连接耗时较长，等待连接完成才能获取服务，实际开发者根据连接速度调整定时器长度
  setTimeout(() => {
    client.readDescriptor(descriptor).then((result: ssap.PropertyDescriptor) => {
      console.info('readDescriptor successfully: ' + JSON.stringify(result));
    }).catch ((err: BusinessError) => {
      console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
    });
  }, 3000);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### writeDescriptor

writeDescriptor(descriptor: PropertyDescriptor): Promise&lt;void&gt;

改写服务端的描述符。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [PropertyDescriptor](js-apis-nearlink-ssap.md#propertydescriptor) | 是 | 服务端属性描述符。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[NearLink错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Non-system applications are not allowed to use system APIs. |
| 36100003 | NearLink disabled. |
| 36100043 | Invalid UUID in descriptor. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

**示例：** 
```typescript
import { ssap } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let addr: string = '00:11:22:33:AA:FF'; // 扫描获取到的远端设备地址
let client: ssap.Client;
try {
  client = ssap.createClient(addr); // 一个应用针对一个远端设备只需要创建一次实例
  client.connect().then(() => {
    console.info('connect success');
  }).catch ((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
  let arrayBufferC = new ArrayBuffer(8);
  let descriptor: ssap.PropertyDescriptor = { // 这里要求descriptor对应的服务发现时对端Service里带的descriptor
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    value: arrayBufferC,
    descriptorType: ssap.PropertyDescriptorType.PROPERTY,
    isWriteable: true
  };
  // 连接耗时较长，等待连接完成才能获取服务，实际开发者根据连接速度调整定时器长度
  setTimeout(() => {
    client.writeDescriptor(descriptor).then(() => {
      console.info('writeDescriptor successfully');
    }).catch ((err: BusinessError) => {
      console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
    });
  }, 3000);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### onEventNotify

onEventNotify(callback: Callback&lt;Event&gt;): void

订阅事件通知事件。使用callback异步回调。

应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：**  此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[Event](#event)&gt; | 是 | 回调函数，返回服务的事件对象。 |

**示例：**
```typescript
import { ssap } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let onEventNotify:(data: ssap.Event) => void = (data: ssap.Event) => {
  console.info('eventNotify data:' + JSON.stringify(data));
};
let addr: string = '00:11:22:33:AA:FF'; // 扫描获取到的远端设备地址
let client: ssap.Client;
try {
  client = ssap.createClient(addr); // 一个应用针对一个远端设备只需要创建一次实例
  client.onEventNotify(onEventNotify);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### offEventNotify

offEventNotify(callback?: Callback&lt;Event&gt;): void

取消订阅事件通知事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：**  此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[Event](#event)&gt; | 否 | 回调函数，返回服务的事件对象。<br/>不填写该参数则取消该type对应的所有回调。 |

**示例：**
```typescript
import { ssap } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let onEventNotify:(data: ssap.Event) => void = (data: ssap.Event) => {
  console.info('eventNotify data:' + JSON.stringify(data));
};
let addr: string = '00:11:22:33:AA:FF'; // 扫描获取到的远端设备地址
let client: ssap.Client;
try {
  client = ssap.createClient(addr); // 一个应用针对一个远端设备只需要创建一次实例
  client.onEventNotify(onEventNotify);
  client.offEventNotify(onEventNotify);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## Service

表示星闪服务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| serviceUuid | string | 否 | 否 | 星闪服务UUID，长度必须为36字节，该值由36个十六进制数字和连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用NearLink标准UUID。 |
| properties | Array&lt;[Property](js-apis-nearlink-ssap.md#property)&gt; | 否 | 否 | 表示服务的Property列表。 |
| methods | Array&lt;[Method](#method)&gt; | 否 | 是 | 表示服务的方法列表。 |
| events | Array&lt;[Event](#event)&gt; | 否 | 是 | 表示服务的事件列表。 |


## Method

表示服务的方法。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| serviceUuid | string | 否 | 否 | 星闪服务UUID，长度必须为36字节，该值由36个十六进制数字和连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用NearLink标准UUID。 |
| methodUuid | string | 否 | 否 | 表示方法UUID。数据格式同serviceUuid。 |
| parameter | ArrayBuffer | 否 | 是 | 表示方法的参数。若未配置则默认不携带该字段。 |
| result | ArrayBuffer | 否 | 是 | 表示方法的返回值。若未配置则默认不携带该字段。 |


## Event

表示服务的事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| serviceUuid | string | 否 | 否 | 星闪服务UUID，长度必须为36字节，该值由36个十六进制数字和连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用NearLink标准UUID。 |
| eventUuid | string | 否 | 否 | 表示事件UUID。数据格式同serviceUuid。 |
| parameter | ArrayBuffer | 否 | 是 | 表示事件的参数。若未配置则默认不携带该字段。 |