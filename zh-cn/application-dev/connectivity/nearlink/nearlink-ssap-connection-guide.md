# 管理SSAP连接及服务
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->

星闪设备间的服务管理与交互基于星闪服务交互协议（SparkLink Service Access Protocol，SSAP）实现。该协议定义了服务的结构、发现与访问过程，以及过程中使用的信令，使星闪设备能够在服务层面互联互通。应用可分别以服务端或客户端角色参与：

- 服务端：服务的承载方，创建服务并声明其中的属性（Property），接收并响应客户端对属性的读写请求；属性值变化时，可向已开启通知的客户端推送更新。
- 客户端：服务的使用方，扫描发现服务端设备并发起连接，连接后可获取服务端支持的服务列表，读取或写入属性，并订阅属性变化通知。

服务端创建服务并声明属性后，客户端可扫描发现并连接服务端，获取服务列表、读写属性并订阅属性变化通知，交互完成后断开连接。

典型开发场景如：键盘、鼠标等外围设备作为服务端向中心设备提供输入服务，中心设备上的应用作为客户端访问外围设备的服务与属性。

开发前需按[开发准备](nearlink-preparations-guide.md)完成权限声明与运行时申请，并确保设备已开启星闪（参见[开发准备 > 查询星闪开关状态](nearlink-preparations-guide.md#查询星闪开关状态)）。

## SSAP服务端开发

SSAP服务端是服务的承载方：创建服务并声明属性，接收和响应客户端的属性读写请求，并可通过[notifyPropertyChanged()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#notifypropertychanged)将属性变化推送给已开启通知的客户端。

> **说明：**
>
> 建立SSAP连接后，SSAP服务端广播会自动停止。后续如果服务端期望被客户端发现，可参见[发现星闪设备 > 发起星闪广播](nearlink-device-discovery-guide.md#发起星闪广播)，重新发起广播。

### 接口说明

SSAP服务端管理功能，完整的API说明以及示例代码请参考：[@ohos.nearlink.ssap (星闪SSAP连接能力)](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md)。

| 接口名 | 描述 |
| -------- | -------- |
| createServer(): Server | 创建SSAP服务端实例。 |
| addService(service: Service): void | 服务端添加服务。 |
| onConnectionStateChange(callback: Callback&lt;ConnectionChangeState&gt;): void | 订阅连接状态变化事件。使用callback异步回调。 |
| onPropertyRead(callback: Callback&lt;PropertyReadRequest&gt;): void | 订阅客户端的读属性请求事件。使用callback异步回调。 |
| onPropertyWrite(callback: Callback&lt;PropertyWriteRequest&gt;): void | 订阅客户端的写属性请求事件。使用callback异步回调。 |
| notifyPropertyChanged(address: string, property: Property): Promise&lt;void&gt; | 通知客户端属性值更新。使用Promise异步回调。 |

### 开发步骤

1. 导入相关模块。

    <!-- @[ssap_server_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { ssap } from '@kit.ConnectivityKit';
    ```

2. 定义SSAP服务端变量，供后续步骤使用。

    <!-- @[ssap_server_declare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    let server: ssap.Server;
    let propertyValue1: number;
    let propertyValue2: number;
    ```

3. 创建SSAP服务端实例。

    <!-- @[ssap_server_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      server = ssap.createServer();
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

4. 添加服务端支持的服务。服务与属性使用自定义UUID（禁止使用标准UUID），参见[星闪常见问题 > 标准UUID与自定义UUID有什么区别](nearlink-faq-guide.md#标准uuid与自定义uuid有什么区别)；支持通知的属性需声明客户端属性值配置描述符，参见[星闪常见问题 > SSAP属性描述符的作用](nearlink-faq-guide.md#ssap属性描述符的作用)。若需客户端通过扫描发现服务端并建立连接，服务端需调用[advertising.startAdvertising()](../../reference/apis-connectivity-kit/js-apis-nearlink-advertising.md#advertisingstartadvertising)主动发起广播，参见[发现星闪设备 > 发起星闪广播](nearlink-device-discovery-guide.md#发起星闪广播)。

    <!-- @[ssap_server_add_service](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      let property1: ssap.Property = {
        serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
        propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001235',
        value: new ArrayBuffer(1),
        operation: ssap.Operation.READABLE | ssap.Operation.WRITE_NO_RESPONSE | ssap.Operation.NOTIFY,
        descriptors: [{
          serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
          propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001235',
          value: new ArrayBuffer(2),
          descriptorType: ssap.PropertyDescriptorType.CLIENT_PROPERTY_CONFIG,
          isWriteable: true
        }]
      };
    
      let property2: ssap.Property = {
        serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
        propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001236',
        value: new ArrayBuffer(1),
        operation: ssap.Operation.READABLE | ssap.Operation.WRITE_WITH_RESPONSE
      };
    
      let service: ssap.Service = {
        serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
        properties: [property1, property2]
      };
    
      server.addService(service);
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

5. 订阅连接状态变化事件，并在回调中保存客户端地址，供后续通知使用。不再需要订阅事件时，调用[offConnectionStateChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offconnectionstatechange)取消订阅。

    <!-- @[ssap_server_on_conn_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      server.onConnectionStateChange((data: ssap.ConnectionChangeState) => {
        hilog.info(0x0000, 'testTag', `Connection state: ${JSON.stringify(data)}`);
        this.connectedAddress = data.address;
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

6. 订阅客户端读属性请求事件，服务端收到读请求后由框架自动回复属性当前值。

    <!-- @[ssap_server_on_property_read](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      server.onPropertyRead((data: ssap.PropertyReadRequest) => {
        hilog.info(0x0000, 'testTag', `Property read: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

7. 订阅客户端写属性请求事件，将写入的值保存到对应属性。不再需要订阅事件时，调用[offPropertyRead()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offpropertyread)、[offPropertyWrite()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offpropertywrite)取消订阅。

    <!-- @[ssap_server_on_property_write](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      // 写属性请求：将写入的值保存到对应属性
      server.onPropertyWrite((data: ssap.PropertyWriteRequest) => {
        hilog.info(0x0000, 'testTag', `Property write: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

8. 通知客户端属性值更新。其中connectedAddress为已连接客户端的地址，在步骤5的连接状态回调中赋值保存。

    <!-- @[ssap_server_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      // 使用固定示例值更新属性，实际开发中替换为业务数据
      propertyValue1 = 0x4E;
      let buffer = new ArrayBuffer(1);
      new Uint8Array(buffer)[0] = propertyValue1;
      let property: ssap.Property = {
        serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000001234',
        propertyUuid: 'FFFFFFFF-1234-5678-ABCD-000000001235',
        value: buffer
      };
      await server.notifyPropertyChanged(this.connectedAddress, property);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

## SSAP客户端开发

SSAP客户端是服务的使用方：通过扫描发现服务端设备并发起连接，连接后可获取服务端支持的服务列表，读取、写入属性，并订阅属性变化通知。

### 接口说明

SSAP客户端连接功能，完整的API说明以及示例代码请参考：[@ohos.nearlink.ssap (星闪SSAP连接能力)](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md)。

| 接口名 | 描述 |
| -------- | -------- |
| createClient(address: string): Client | 创建SSAP客户端实例。 |
| connect(): Promise&lt;void&gt; | 向服务端发起连接。 |
| getServices(): Promise&lt;Array&lt;Service&gt;&gt; | 获取服务端支持的服务列表。使用Promise异步回调。 |
| readProperty(property: Property): Promise&lt;Property&gt; | 读取服务端属性。使用Promise异步回调。 |
| writeProperty(property: Property, writeType: PropertyWriteType): Promise&lt;void&gt; | 写入服务端属性。使用Promise异步回调。 |
| setPropertyNotification(property: Property, enable: boolean): Promise&lt;void&gt; | 启用或禁用属性变化的通知。 |
| onPropertyChange(callback: Callback&lt;Property&gt;): void | 订阅属性变化事件。使用callback异步回调。 |
| onConnectionStateChange(callback: Callback&lt;ConnectionChangeState&gt;): void | 订阅连接状态变化事件。使用callback异步回调。 |

### 开发步骤

1. 导入相关模块。

    <!-- @[ssap_client_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { ssap } from '@kit.ConnectivityKit';
    ```

2. 定义SSAP客户端变量，供后续步骤使用。

    <!-- @[ssap_client_declare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    let client: ssap.Client;
    ```

3. 创建SSAP客户端实例。其中参数address是通过[发起星闪扫描](nearlink-device-discovery-guide.md#发起星闪扫描)获取的远端设备地址。

    <!-- @[ssap_client_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    try {
      client = ssap.createClient(address);
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

4. 订阅连接状态变化事件。

    <!-- @[ssap_client_on_conn_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    try {
      client.onConnectionStateChange((data: ssap.ConnectionChangeState) => {
        hilog.info(0x0000, 'testTag', `Connection state: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

5. 订阅属性变化事件。不再需要订阅事件时，调用[offConnectionStateChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offconnectionstatechange)、[offPropertyChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offpropertychange)取消订阅。

    <!-- @[ssap_client_on_property_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    try {
      client.onPropertyChange((data: ssap.Property) => {
        hilog.info(0x0000, 'testTag', `Property changed: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

6. 向服务端发起连接。连接成功后将触发步骤4订阅的连接状态事件，可在回调中确认连接结果。

    <!-- @[ssap_client_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    try {
      await client.connect();
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

7. 获取服务端支持的服务列表。服务列表用于确认服务端提供的服务能力，后续读取、写入属性时指定的服务与属性必须包含在服务列表中。

    <!-- @[ssap_client_get_services](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    let services: ssap.Service[] = [];
    try {
      services = await client.getServices();
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

8. 设置属性变化通知。仅当服务端对应属性支持通知（NOTIFY）操作并声明了客户端属性值配置描述符时，通知才能生效，参见[星闪常见问题 > SSAP属性描述符的作用](nearlink-faq-guide.md#ssap属性描述符的作用)。

    <!-- @[ssap_client_set_notification](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    try {
      await client.setPropertyNotification(property, true);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

9. 读取指定服务的属性值。property为待读取的属性，可从[getServices()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#getservices)返回的服务列表中获得。服务与属性UUID必须为自定义UUID，且与服务端声明的UUID一致，参见[星闪常见问题 > 标准UUID与自定义UUID有什么区别](nearlink-faq-guide.md#标准uuid与自定义uuid有什么区别)。

    <!-- @[ssap_client_read_property](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    let result: ssap.Property | null = null;
    try {
      result = await client.readProperty(property);
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

10. 写入指定服务的属性值。property为待写入的属性，可从服务列表中获得。

    <!-- @[ssap_client_write_property](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    try {
      let valueBuffer = new ArrayBuffer(1);
      let value = new Uint8Array(valueBuffer);
      value[0] = 1;
      property.value = valueBuffer;
    
      await client.writeProperty(property, ssap.PropertyWriteType.WRITE_NO_RESPONSE);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```
