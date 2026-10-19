# NearLink FAQs
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=334711649411ef71eccb3a29729079fa474e252c translatedAt=2026-09-29T10:56:50.739Z pushedAt=2026-09-30T06:48:42.240Z -->

## What Is the Difference Between Standard UUIDs and Custom UUIDs

A universally unique identifier (UUID) identifies a NearLink service and its members (properties, methods, events, and so on). Based on how identifiers are assigned, UUIDs in NearLink fall into two categories:

- **Standard UUID**: 16 bits long, uniformly assigned by the NearLink Alliance, globally unique, and used to identify a standard service or a member of a standard service (for example, a standard service or a standard property). The complete UUID is 128 bits long and is formed by concatenating the first 112 bits of the base identifier (Base UUID, fixed value 37BEA880-FC70-11EA-B720-000000000000) with the 16-bit standard identifier, for example, 37BEA880-FC70-11EA-B720-00000000FDEE. Through the identifier, the client can determine whether an entry carries a service, property, method, event, or the like. For details, see [NearLink Standard Service Identifiers](https://www.isla.org/trial/identCid/identListSsid).
- **Custom UUID**: 128 bits long, defined by developers, and used to identify a custom service or a member of a custom service. You can define it on your own within the 128-bit range, for example, FFFFFFFF-1234-5678-ABCD-000000001234. A custom UUID must not use the first 112 bits of the base identifier as its prefix (that is, it must not start with 37BEA880-FC70-11EA-B720-00000000); otherwise, it is recognized as a standard UUID.

> **NOTE**
>
> A custom service must use a custom UUID. Using a standard UUID is prohibited.

For UUID fields that identify a service and its members, such as [ssap.Service.serviceUuid](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#service) and [ssap.Property.serviceUuid](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#property) of a custom service, the value must be a 128-bit custom UUID. If a standard UUID is used, the API returns the error [36100044 Standard NearLink Service UUID Not Allowed](../../reference/apis-connectivity-kit/errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed).


## Permission Requirements for Event Subscription APIs

NearLink event subscription APIs come in `onXXX` / `offXXX` pairs:

- `onXXX(callback)` subscribes to a type of event and invokes `callback` when the event occurs.
- `offXXX(callback?)` cancels the subscription. If `callback` is not passed, all callbacks of that type are canceled.

NearLink event subscription APIs generally have no mandatory permission requirements. No error is reported for a missing permission at subscription time, but an application that has not obtained the corresponding permission cannot receive event callbacks. For the permissions required for event subscription, see the corresponding API description in the API reference. For how to request permissions, see [Development Preparations](nearlink-preparations-guide.md).

> **NOTE**
>
> A successful call to a subscription API does not necessarily mean that events will be received. You must also confirm that the corresponding permission has been obtained.

## What Is the Role of the SSAP Property Descriptor

A property descriptor is an optional component of a property (`ssap.Property`). It consists of a descriptor type (`descriptorType`) and a descriptor value (`value`), and is used to explain the property data value, parse its format, or control how it is operated.

The descriptor types are as follows:

- `PROPERTY`: a property description descriptor that stores a textual description of the property data value;
- `CLIENT_PROPERTY_CONFIG`: a client property configuration descriptor ([CPCD](nearlink-glossary-guide.md#client-property-configuration-descriptor-cpcd)) that defines how the client configures the property value;
- `SERVER_PROPERTY_CONFIG`: a server property value configuration descriptor that defines how the property value on the server is configured. Once written, it takes effect for all clients;
- `PROPERTY_FORMAT`: a property format descriptor that describes the format of the property value;
- `TYPE_VENDOR`: a vendor-defined descriptor used for vendor-specific functions.

Among them, a property can contain at most one client property configuration descriptor and at most one server property value configuration descriptor.

When a property supports the notify (`NOTIFY`) operation, a client property configuration descriptor must be declared for it: the client calls [setPropertyNotification()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#setpropertynotification) to enable or disable notification for the property, and the server calls [notifyPropertyChanged()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#notifypropertychanged) to push property changes to the clients that have enabled notification.

## How Does the Client Receive Property Change Notifications

For the client to receive a property change notification (that is, to receive the [onPropertyChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#onpropertychange) callback), all of the following conditions must be met:

1. When creating the property, the server declares the `NOTIFY` operation and the client property configuration descriptor (`CLIENT_PROPERTY_CONFIG`).
2. The client has successfully established an SSAP connection with the server.
3. The client has obtained the property through [getServices()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#getservices).
4. The client has enabled notifications for the property by calling [setPropertyNotification()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#setpropertynotification).
5. The client has registered the property change callback by calling [onPropertyChange()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#onpropertychange).

After the preceding conditions are met, when the server updates the property value by calling [notifyPropertyChanged()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#notifypropertychanged), it sends a property change notification to the client. If any of the preceding conditions is not met, the client will not receive the notification.

> **NOTE**
>
> After the connection is disconnected, the enabled notifications become invalid. After reconnection, call [setPropertyNotification()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#setpropertynotification) again to enable them.

## What Is a NearLink Device Random Address

A NearLink device address is a 6-byte Media Access Control (MAC) address. Its string consists of 12 hexadecimal characters and colon separators (17 characters in total), for example, 11:22:33:AA:BB:FF.

The device address returned in the scan result (`scan.ScanResults.address`) is a random address: to protect device privacy, the system does not directly expose the real address of a device. Instead, it converts the real address into a random address before reporting it, and maintains the mapping between the two. The random address of the same device remains unchanged within the mapping retention period (the mapping of a paired device is retained for a long time). After the mapping is cleared, a new random address is generated upon the next scan.

Do not persist the scanned address as a long-term identifier. To identify a device over the long term, make a comprehensive judgment based on information such as the device name and pairing relationship. The address of a paired device can be obtained through manager.[getPairedDevices()](../../reference/apis-connectivity-kit/js-apis-nearlink-manager.md#managergetpaireddevices). The random address does not affect device connection: you can initiate a connection using the current address obtained from the scan (for example, [SSAP connection](nearlink-ssap-connection-guide.md) and [port data transmission](nearlink-data-transfer-guide.md)).

## How to Select a NearLink Data Transfer Mode

NearLink provides two data transfer modes: SSAP-based and port-based.

- [SSAP-based data transfer](nearlink-ssap-connection-guide.md): adopts a server-client interaction model, in which the server provides service capabilities and the client accesses the services on the server. The interaction is initiated by the client, making it suitable for small-data scenarios such as device control data interaction and status update reporting.
- [Port-based data transfer](nearlink-data-transfer-guide.md): the two ends do not assume server or client roles. Both ends must register a port first, and either end can initiate a connection. After the channel is established, the two ends directly send and receive data. It is suitable for high-rate, high-traffic scenarios such as large file transfer and device upgrade.

For low-power, small-data services, SSAP interaction is sufficient. When continuous high-traffic transfer is required, use port-based transfer.

## Why Can't a NearLink Connection Be Established Between Phones, Tablets, and PCs/2-in-1 Devices via Settings

NearLink pairing can be completed between phones, tablets, and PCs/2-in-1 devices, but a connection cannot be established through the **Settings** interface. A connection initiated from the **Settings** interface follows the system connection process, which is different from connections initiated by an application through NearLink APIs (such as [SSAP connection](nearlink-ssap-connection-guide.md) and [port-based data transfer](nearlink-data-transfer-guide.md)): after the link is established, the system checks whether the peer device provides services available to the local device. If no available service exists, the connection is immediately disconnected.

Phones, tablets, and PCs/2-in-1 devices generally act as central devices that use the services provided by peripheral devices (such as the services provided by HID devices like keyboards, mice, and styluses). They are service consumers rather than providers, and no services are available between these devices. Therefore, a connection cannot be established from the **Settings** interface. To establish a business connection between devices, you should initiate the connection through APIs such as [ssap.Client.connect()](../../reference/apis-connectivity-kit/js-apis-nearlink-ssap.md#connect) (SSAP connection) or [dataTransfer.connect()](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md#datatransferconnect) (port-based data transfer), with the application explicitly specifying the service.

## Why Does Calling writeData() Consecutively Cause Send Failures?

Calling [writeData()](../../reference/apis-connectivity-kit/js-apis-nearlink-data-transfer-api.md#datatransferwritedata) multiple times consecutively may congest the sending queue and cause the transmission to fail.

You can resolve the failure in continuous data transmission by setting a data sending interval. Use [setInterval()](../../reference/common/js-apis-timer.md#setinterval) to set the interval between function calls. The recommended data sending interval is 10 ms.
