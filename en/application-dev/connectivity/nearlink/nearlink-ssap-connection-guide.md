# Managing SSAP Connections and Services
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=334711649411ef71eccb3a29729079fa474e252c translatedAt=2026-09-29T11:01:28.613Z pushedAt=2026-09-30T09:52:16.502Z -->

Service management and interaction between NearLink devices are implemented based on the SparkLink Service Access Protocol (SSAP). This protocol defines the structure, discovery, and access process of services, as well as the signaling used in the process, enabling NearLink devices to interconnect at the service layer. An application can participate as a server or a client:

- Server: the bearer of services. It creates services and declares the properties in them, receives and responds to read and write requests from clients for properties, and can push updates to clients that have enabled notifications when a property value changes.
- Client: the consumer of services. It scans for and discovers server devices and initiates a connection. After the connection is established, it can obtain the service list supported by the server, read or write properties, and subscribe to property change notifications.

After the server creates services and declares properties, the client can scan for, discover, and connect to the server, obtain the service list, read and write properties, and subscribe to property change notifications. After the interaction is complete, the connection is disconnected.

A typical development scenario is as follows: peripheral devices such as keyboards and mice act as servers to provide input services to a central device, and applications on the central device act as clients to access the services and properties of the peripheral devices.

Before development, complete the permission declaration and runtime request as described in [Getting Started](nearlink-preparations-guide.md), and ensure that NearLink is enabled on the device (see [Getting Started > Querying the NearLink Switch State](nearlink-preparations-guide.md#querying-the-nearlink-switch-state)).

## SSAP Server Development

The SSAP server is the bearer of services: it creates services and declares properties, receives and responds to property read and write requests from clients, and can push property changes to clients that have enabled notifications through [notifyPropertyChanged()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#notifypropertychanged).

> **NOTE**
>
> After an SSAP connection is established, the SSAP server advertising stops automatically. If you want the server to be discovered by clients later, see [Discovering NearLink Devices > Initiating NearLink Advertising](nearlink-device-discovery-guide.md#initiating-nearlink-advertising) to start advertising again.

### Available APIs

The following table lists the APIs for SSAP server management. For the complete API descriptions and sample code, see [@ohos.nearlink.ssap (NearLink SSAP Connection Capability)](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md).

| API | Description |
| -------- | -------- |
| createServer(): Server | Creates an SSAP server instance. |
| addService(service: Service): void | Adds a service to the server. |
| onConnectionStateChange(callback: Callback&lt;ConnectionChangeState&gt;): void | Subscribes to connection state change events. This API uses an asynchronous callback to return the result. |
| onPropertyRead(callback: Callback&lt;PropertyReadRequest&gt;): void | Subscribes to client property read request events. This API uses an asynchronous callback to return the result. |
| onPropertyWrite(callback: Callback&lt;PropertyWriteRequest&gt;): void | Subscribes to client property write request events. This API uses an asynchronous callback to return the result. |
| notifyPropertyChanged(address: string, property: Property): Promise&lt;void&gt; | Notifies the client of property value updates. This API uses a Promise to return the result. |

### How to Develop

1. Import the required modules.

    <!-- @[ssap_server_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { ssap } from '@kit.ConnectivityKit';
    ```

2. Define SSAP server variables for use in subsequent steps.

    <!-- @[ssap_server_declare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    let server: ssap.Server;
    let propertyValue1: number;
    let propertyValue2: number;
    ```

3. Create an SSAP server instance.

    <!-- @[ssap_server_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      server = ssap.createServer();
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

4. Add the services supported by the server. Services and properties use custom UUIDs (standard UUIDs are prohibited). For details, see [NearLink FAQ > What Is the Difference Between Standard UUIDs and Custom UUIDs](nearlink-faq-guide.md#what-is-the-difference-between-standard-uuids-and-custom-uuids). Properties that support notifications must declare the client property configuration descriptor. For details, see [NearLink FAQ > What Is the Role of the SSAP Property Descriptor](nearlink-faq-guide.md#what-is-the-role-of-the-ssap-property-descriptor). If you want clients to discover the server through scanning and establish a connection, the server must call [advertising.startAdvertising()](../../reference/apis-connectivity-kit/js-apis-nearlink-advertising.md#advertisingstartadvertising) to actively start advertising. For details, see [Discovering NearLink Devices > Initiating NearLink Advertising](nearlink-device-discovery-guide.md#initiating-nearlink-advertising).

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

5. Subscribe to connection state change events, and save the client address in the callback for subsequent notifications. When you no longer need to subscribe to the events, call [offConnectionStateChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offconnectionstatechange) to unsubscribe.

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

6. Subscribe to client property read request events. After the server receives a read request, the framework automatically replies with the current value of the property.

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

7. Subscribe to the client property write request event and save the written value to the corresponding property. When the event subscription is no longer needed, call [offPropertyWrite()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offpropertywrite) to unsubscribe.

    <!-- @[ssap_server_on_property_write](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      // Write property request: save the written value to the corresponding property.
      server.onPropertyWrite((data: ssap.PropertyWriteRequest) => {
        hilog.info(0x0000, 'testTag', `Property write: ${JSON.stringify(data)}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

8. Notify the client of the property value update. Here, `connectedAddress` is the address of the connected client, which is assigned and saved in the connection state callback in step 5.

    <!-- @[ssap_server_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapServerPage.ets) -->
    
    ``` TypeScript
    try {
      // Update the property with a fixed sample value. Replace it with service data in actual development.
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

## SSAP Client Development

An SSAP client is the consumer of services: it discovers server devices by scanning and initiates a connection. After the connection is established, it can obtain the list of services supported by the server, read and write properties, and subscribe to property change notifications.

### Available APIs

The following table lists the APIs for SSAP client connection. For the complete API descriptions and sample code, see [@ohos.nearlink.ssap (NearLink SSAP Connection Capability)](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md).

| API | Description |
| -------- | -------- |
| createClient(address: string): Client | Creates an SSAP client instance. |
| connect(): Promise&lt;void&gt; | Initiates a connection to the server. This API uses a Promise to return the result. |
| disconnect(): Promise&lt;void&gt; | Initiates disconnection from the server to disconnect an existing connection or terminate a connection being established. This API uses a Promise to return the result. |
| getServices(): Promise&lt;Array&lt;Service&gt;&gt; | Obtains the list of services supported by the server. This API uses a Promise to return the result. |
| readProperty(property: Property): Promise&lt;Property&gt; | Reads a property from the server. This API uses a Promise to return the result. |
| writeProperty(property: Property, writeType: PropertyWriteType): Promise&lt;void&gt; | Writes a property to the server. This API uses a Promise to return the result. |
| setPropertyNotification(property: Property, enable: boolean): Promise&lt;void&gt; | Enables or disables property change notifications. This API uses a Promise to return the result. |
| onPropertyChange(callback: Callback&lt;Property&gt;): void | Subscribes to property change events. This API uses an asynchronous callback to return the result. |
| onConnectionStateChange(callback: Callback&lt;ConnectionChangeState&gt;): void | Subscribes to connection state change events. This API uses an asynchronous callback to return the result. |

### How to Develop

1. Import the required modules.

    <!-- @[ssap_client_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { ssap } from '@kit.ConnectivityKit';
    ```

2. Define SSAP client variables for use in subsequent steps.

    <!-- @[ssap_client_declare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    let client: ssap.Client;
    ```

3. Create an SSAP client instance. The `address` parameter is the remote device address obtained through the [NearLink scan](nearlink-device-discovery-guide.md#initiating-a-nearlink-scan).

    <!-- @[ssap_client_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/SsapClientPage.ets) -->
    
    ``` TypeScript
    try {
      client = ssap.createClient(address);
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

4. Subscribe to connection state change events.

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

5. Subscribe to property change events. When you no longer need to subscribe to events, call [offConnectionStateChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offconnectionstatechange) and [offPropertyChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#offpropertychange) to unsubscribe.

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

6. Initiate a connection to the server. After the connection is established, the connection state change event subscribed to in step 4 is triggered, and you can confirm the connection result in the callback.

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

7. Obtain the list of services supported by the server. The service list is used to confirm the service capabilities provided by the server. The services and properties specified when reading or writing properties later must be included in the service list.

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

8. Enable property change notifications. Call [setPropertyNotification()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#setpropertynotification) to enable notifications for a specified property. The corresponding property on the server must declare the `NOTIFY` operation and the client property configuration descriptor; otherwise, the client cannot receive property change notifications. For the complete conditions, see [NearLink FAQ > How Does the Client Receive Property Change Notifications](nearlink-faq-guide.md#how-does-the-client-receive-property-change-notifications).

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

9. Read the property value of a specified service. `property` is the property to read, which can be obtained from the service list returned by [getServices()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#getservices). The service and property UUIDs must be custom UUIDs and must be consistent with the UUIDs declared on the server. For details, see [NearLink FAQ > What Is the Difference Between Standard UUIDs and Custom UUIDs](nearlink-faq-guide.md#what-is-the-difference-between-standard-uuids-and-custom-uuids).

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

10. Write the property value of a specified service. `property` is the property to write, which can be obtained from the service list.

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
