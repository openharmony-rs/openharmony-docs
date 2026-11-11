# @ohos.nearlink.ssap (星闪SSAP连接能力)(系统接口)
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->


本模块提供了SSAP（星闪服务交互协议 SparkLink Service Access Protocol）连接功能，包括调用服务端方法、读写描述符、订阅事件通知、设置属性指示等系统接口。


**起始版本：** 26.0.0

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.nearlink.ssap (星闪SSAP连接能力)](js-apis-nearlink-ssap.md)。


## 导入模块

```typescript
import { ssap } from '@kit.ConnectivityKit';
```


## Client

SSAP客户端类，提供了和服务端进行连接和数据传输等操作方法。

使用该类的方法前，需通过[ssap.createClient](js-apis-nearlink-ssap.md#ssapcreateclient)方法构造该类的实例。

同一应用针对同一远端设备创建一个[Client](#client)实例即可，重复创建会增加不必要的资源开销。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base


### setPropertyIndication

setPropertyIndication(property: Property, enable: boolean): Promise&lt;void&gt;

启用或禁用服务端属性值更改时的指示（当属性值发生变化时，服务端主动向客户端发送通知）。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| property | [Property](js-apis-nearlink-ssap.md#property) | 是 | 服务端属性。 |
| enable | boolean | 是 | 是否启用属性值更改指示。true：启用指示。false：禁用指示。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[星闪错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  let valueBuffer = new ArrayBuffer(1);
  let propertyValue = new Uint8Array(valueBuffer);
  propertyValue[0] = 1;
  let property: ssap.Property = {
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    value: valueBuffer
  };
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
  client.setPropertyIndication(property, true).then(() => {
    console.info('setPropertyIndication successfully');
  }).catch((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### callMethod

callMethod(method: Method): Promise&lt;Method&gt;

调用服务端方法。例如，在设备控制场景中，客户端可调用服务端提供的配置方法来远程设置设备参数或触发特定操作。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| method | [Method](#method) | 是 | 服务端方法。需与服务发现时获取的对端Service中的method对应。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[Method](#method)&gt; | Promise对象，返回调用结果对应的Method对象，其中result字段为服务端方法执行后的返回值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[星闪错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
  client.connect().then(() => {
    console.info('connect success');
  }).catch((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
  let valueBuffer = new ArrayBuffer(8);
  let method: ssap.Method = { // 这里要求method对应的服务发现时对端Service里带的method
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    methodUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    parameter: valueBuffer
  };
  // 连接耗时较长，等待连接完成才能获取服务，实际开发者根据连接速度调整定时器长度
  setTimeout(() => {
    client.callMethod(method).then((result: ssap.Method) => {
      console.info('callMethod successfully: ' + JSON.stringify(result));
    }).catch((err: BusinessError) => {
      console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
    });
  }, 3000);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### getServicesByUuid

getServicesByUuid(service: Service): Promise&lt;Service[]&gt;

获取服务端支持的服务中与指定服务UUID匹配的服务。使用Promise异步回调。

与[getServices](js-apis-nearlink-ssap.md#getservices)不同，本接口仅获取与指定UUID匹配的服务，且仅使用传入service的serviceUuid字段在服务端匹配目标服务，其余字段不参与匹配。无匹配服务时返回空数组。

需在调用[connect](js-apis-nearlink-ssap.md#connect)建立连接成功后使用。

> **说明：**
>
> serviceUuid若为星闪标准UUID（以"37BEA880-FC70-11EA-B720"为前缀的UUID），接口将返回36100044错误，请使用自定义UUID。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| service | [Service](js-apis-nearlink-ssap.md#service) | 是 | 待获取的服务。仅serviceUuid字段用于在服务端匹配目标服务。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[Service](js-apis-nearlink-ssap.md#service)[]&gt; | Promise对象，返回与指定UUID匹配的服务列表。无匹配服务时返回空数组。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[星闪错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
  client.connect().then((): Promise<ssap.Service[]> => {
    console.info('connect success');
    let service: ssap.Service = { // 仅serviceUuid字段用于匹配目标服务；properties为类型必填字段，本接口不使用
      serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386', // 自定义UUID，不能使用星闪标准UUID
      properties: []
    };
    return client.getServicesByUuid(service);
  }).then((result: ssap.Service[]) => {
    console.info('getServicesByUuid successfully: ' + JSON.stringify(result));
  }).catch((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### readPropertiesByUuid

readPropertiesByUuid(property: Property): Promise&lt;Property[]&gt;

根据属性UUID读取服务端属性。使用Promise异步回调。

与[readProperty](js-apis-nearlink-ssap.md#readproperty)（读取单个属性）不同，本接口读取与指定属性UUID匹配的所有属性，仅使用传入property的propertyUuid字段匹配待读取的属性，匹配范围为服务端全部服务，不限定在serviceUuid对应的服务内。无匹配属性时返回空数组。

需在调用[connect](js-apis-nearlink-ssap.md#connect)建立连接成功后使用。

> **说明：**
>
> propertyUuid或serviceUuid若为星闪标准UUID（以"37BEA880-FC70-11EA-B720"为前缀的UUID），接口将返回36100044错误，请使用自定义UUID。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| property | [Property](js-apis-nearlink-ssap.md#property) | 是 | 待读取的服务端属性。仅propertyUuid字段用于匹配待读取的属性；serviceUuid与value为[Property](js-apis-nearlink-ssap.md#property)类型的必填字段，本接口不使用：serviceUuid传入任意合法的自定义UUID即可，value传入空ArrayBuffer即可（其大小与内容不参与读取，读取到的属性值在返回结果中）。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[Property](js-apis-nearlink-ssap.md#property)[]&gt; | Promise对象，返回读取到的服务端属性列表。无匹配属性时返回空数组。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[星闪错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
  client.connect().then((): Promise<ssap.Property[]> => {
    console.info('connect success');
    let property: ssap.Property = { // 仅propertyUuid字段用于匹配待读取的属性；serviceUuid、value为类型必填字段，本接口不使用
      serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386', // 自定义UUID，不能使用星闪标准UUID
      propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234', // 自定义UUID，不能使用星闪标准UUID
      value: new ArrayBuffer(0)
    };
    return client.readPropertiesByUuid(property);
  }).then((result: ssap.Property[]) => {
    console.info('readPropertiesByUuid successfully: ' + JSON.stringify(result));
  }).catch((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### readDescriptor

readDescriptor(descriptor: PropertyDescriptor): Promise&lt;PropertyDescriptor&gt;

读取服务端描述符。需在调用[connect](js-apis-nearlink-ssap.md#connect)建立连接成功后使用，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [PropertyDescriptor](js-apis-nearlink-ssap.md#propertydescriptor) | 是 | 服务端属性描述符。需与服务发现时获取的对端Service中的descriptor对应。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PropertyDescriptor](js-apis-nearlink-ssap.md#propertydescriptor)&gt; | Promise对象，返回从服务端读取到的属性描述符对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[星闪错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
  client.connect().then(() => {
    console.info('connect success');
  }).catch((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
  let valueBuffer = new ArrayBuffer(8);
  let descriptor: ssap.PropertyDescriptor = { // 这里要求descriptor对应的服务发现时对端Service里带的descriptor
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    value: valueBuffer,
    descriptorType: ssap.PropertyDescriptorType.PROPERTY,
    isWriteable: true
  };
  // 连接耗时较长，等待连接完成才能获取服务，实际开发者根据连接速度调整定时器长度
  setTimeout(() => {
    client.readDescriptor(descriptor).then((result: ssap.PropertyDescriptor) => {
      console.info('readDescriptor successfully: ' + JSON.stringify(result));
    }).catch((err: BusinessError) => {
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

> **说明：**
>
> 此接口不支持写入客户端属性值配置描述符（CLIENT_PROPERTY_CONFIG），如需配置客户端属性通知或指示，请使用[setPropertyNotification](js-apis-nearlink-ssap.md#setpropertynotification)或[setPropertyIndication](#setpropertyindication)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：**  此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| descriptor | [PropertyDescriptor](js-apis-nearlink-ssap.md#propertydescriptor) | 是 | 服务端属性描述符。需与服务发现时获取的对端Service中的descriptor对应。 |

**返回值：** 

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[星闪错误码](errorcode-nearlink-service.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
  client.connect().then(() => {
    console.info('connect success');
  }).catch((err: BusinessError) => {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
  });
  let valueBuffer = new ArrayBuffer(8);
  let descriptor: ssap.PropertyDescriptor = { // 这里要求descriptor对应的服务发现时对端Service里带的descriptor
    serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000004386',
    propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
    value: valueBuffer,
    descriptorType: ssap.PropertyDescriptorType.PROPERTY,
    isWriteable: true
  };
  // 连接耗时较长，等待连接完成才能获取服务，实际开发者根据连接速度调整定时器长度
  setTimeout(() => {
    client.writeDescriptor(descriptor).then(() => {
      console.info('writeDescriptor successfully');
    }).catch((err: BusinessError) => {
      console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
    });
  }, 3000);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### onEventNotify

onEventNotify(callback: Callback&lt;Event&gt;): void

订阅事件通知事件。例如，在设备状态监控场景中，客户端通过订阅事件来实时接收服务端推送的状态变化通知（如设备告警、数据更新等）。使用callback异步回调。

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
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
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

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[Event](#event)&gt; | 否 | 回调函数，返回服务的事件对象。<br>填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

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
  client = ssap.createClient(addr); // 同一应用针对同一远端设备只需创建一个实例
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

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| methods | [Method](#method)[] | 否 | 是 | 表示服务的方法列表。若未配置，该服务不提供任何方法。 |
| events | [Event](#event)[] | 否 | 是 | 表示服务的事件列表。若未配置，该服务不提供任何事件。 |

## Method

表示服务的方法。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| serviceUuid | string | 否 | 否 | 星闪服务UUID，长度必须为36个字符，由32个十六进制数字和4个连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用星闪标准UUID。 |
| methodUuid | string | 否 | 否 | 表示方法UUID。数据格式同serviceUuid。 |
| parameter | ArrayBuffer | 否 | 是 | 表示方法的参数，数据格式由具体服务定义。若未配置则默认不携带该字段。 |
| result | ArrayBuffer | 否 | 是 | 表示方法的返回值，数据格式由具体服务定义。若未配置则默认不携带该字段。 |


## Event

表示服务的事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统接口：**  此接口为系统接口。

**系统能力：** SystemCapability.Communication.NearLink.Base

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| serviceUuid | string | 否 | 否 | 星闪服务UUID，长度必须为36个字符，由32个十六进制数字和4个连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用星闪标准UUID。 |
| eventUuid | string | 否 | 否 | 表示事件UUID。数据格式同serviceUuid。 |
| parameter | ArrayBuffer | 否 | 是 | 表示事件的参数，数据格式由具体服务定义。若未配置则默认不携带该字段。 |
