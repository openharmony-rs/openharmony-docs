# Using DNS for Domain Name Resolution
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## Scenario Overview

DNS allows applications to translate host names (domain names) into IP addresses. It supports the conversion between Chinese characters and ASCII codes, the acquisition of the IP address list for a specified domain name, and domain name resolution in different network environments.

The following features are supported:

| Feature              | Description                                       | Available Since|
| :--------------------- | :---------------------------------------------- | :------------- |
| Conversion between Unicode and ASCII    | Conversion between Chinese domain names and ASCII codes.          | API version 23  |
| Obtaining all IP addresses of a host name| Obtains all IP addresses of the default network by resolving the host name.         | API version 23  |
| Resolving the host name by specifying the IP address type  | Resolves the host name by specifying the IP address type (IPv4/IPv6) using the default network.| API version 23  |
| Resolving the host name by specifying the network connection| Resolves the host name by using a specific network connection [NetHandle](../reference/apis-network-kit/js-apis-net-connection.md#nethandle).        | API version 23  |

## Transcoding of Chinese Domain Names

Since API version 23, DNS resolution supports transcoding between Chinese domain names and ASCII codes.

> **NOTE**
>
> In the sample code provided in this topic, **hostName** in the resource file must be changed to an actual Chinese domain name.

For the complete sample code, please refer to [DNS_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case)

1. Import required files.

   <!-- @[Dns_GetAddress_Ascii_Import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/Unicode.ets) -->
   
   ``` TypeScript
   import { connection } from '@kit.NetworkKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. Initialize data members.

   <!-- @[Dns_GetAddress_Ascii_Data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/Unicode.ets) -->
   
   ``` TypeScript
   @State hostVal: string = '';     // Transcoded host name.
   @State ipResult: string = '';    // Obtained IP address.
   private hostName: string = '';   // Initial host name.
   ```

3. Obtain the value of **hostName** from the resource file and assign the value.

   <!-- @[Dns_GetSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/Unicode.ets) -->
   
   ``` TypeScript
   aboutToAppear() {
     this.hostName =
       (this.getUIContext().getHostContext() as Context).resourceManager.getStringSync($r('app.string.hostName').id);
   }
   ```

4. Create a network address resolution function to convert a domain name to an IP address. **isChange** indicates whether to transcode the domain name to ASCII code.

   <!-- @[Dns_GetAddress_Ascii_Fun](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/Unicode.ets) -->
   
   ``` TypeScript
   getAddressName(isChange: boolean) {
     this.ipResult = '';
     connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
       if (netHandle.netId === 0) {
         // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
         return;
       }
       if (isChange) {
         this.hostVal = connection.getDnsAscii(this.hostName);
       } else {
         this.hostVal = '';
       }
       netHandle.getAddressByName(isChange ? this.hostVal : this.hostName,
         (error: BusinessError, data: connection.NetAddress) => {
           if (error) {
             this.ipResult = `Failed to get address. Code:${error.code}, message:${error.message}`;
             hilog.error(0x0000, 'testTag', `Failed to get address. Code:${error.code}, message:${error.message}`);
             return;
           }
           this.ipResult = JSON.stringify(data);
           hilog.info(0x0000, 'testTag', `Succeeded to get data: ${JSON.stringify(data)}`);
         });
     });
   }
   ```

5. Obtain the IP address corresponding to the Chinese domain name. As the IP address is not ASCII-encoded, the expected result is that the IP address fails to be obtained.

   <!-- @[UnChange_Handle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/Unicode.ets) -->
   
   ``` TypeScript
   this.getAddressName(false);
   ```

6. Obtain the IP address after the Chinese domain name is ASCII-encoded.

   <!-- @[Change_Handle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/Unicode.ets) -->
   
   ``` TypeScript
   this.getAddressName(true);
   ```

7. Convert the ASCII code to the original Chinese domain name.

   <!-- @[Change_Unicode_Handle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/Unicode.ets) -->
   
   ``` TypeScript
   this.hostVal = connection.getDnsUnicode(this.hostVal);
   ```

## Configuring the Type of IP Addresses Obtained over the DNS API

Since API version 23, DNS resolution allows you to specify the IP address type (IPv4 or IPv6) using the `options` parameter and resolve host names based on the specified IP address type on a specific network connection **NetHandle**, achieving more accurate address resolution.<br><br>
For the complete sample code, please refer to [DNS_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case)

1. Import required files.

   <!-- @[Get_Ip_Address_Import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/DNS.ets) -->
   
   ``` TypeScript
   import { connection } from '@kit.NetworkKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. Initialize data members.

   <!-- @[Dns_Data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/DNS.ets) -->
   
   ``` TypeScript
   @State hostName: string = 'www.example.com';
   ```

3. Obtain all IP addresses of the default network by resolving the host name.

   <!-- @[Get_All_Ip_Address](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/DNS.ets) -->
   
   ``` TypeScript
   connection.getAddressesByName(this.hostName).then((data: connection.NetAddress[]) => {
     hilog.info(0x0000, 'testTag', `Succeeded to get data: ${JSON.stringify(data)}`);
   })
   ```

4. Obtain all IP addresses of the default network by resolving the host name of the specified IP type.

   <!-- @[Get_Ip_Address_With_Options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/DNS.ets) -->
   
   ``` TypeScript
   let options: connection.QueryOptions = {
     family: connection.FamilyType.FAMILY_TYPE_IPV4
   };
   connection.getAddressesByNameWithOptions(this.hostName, options).then((data: connection.NetAddress[]) => {
     hilog.info(0x0000, 'testTag', `Succeeded to get data: ${JSON.stringify(data)}`);
   });
   ```

5. Resolve the host name by specifying the IP address type using the specified network connection (NetHandle).

   <!-- @[Get_NetHandle_Ip](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case/entry/src/main/ets/pages/DNS.ets) -->
   
   ``` TypeScript
   let netSpecifier: connection.NetSpecifier = {
     netCapabilities: {
       // Assume that the default network is Wi-Fi. If you need to create a cellular network connection, set the network type to CELLULAR.
       bearerTypes: [connection.NetBearType.BEARER_CELLULAR],
       // Set the network capability to INTERNET.
       networkCap: [connection.NetCap.NET_CAPABILITY_INTERNET]
     },
   };
   
   // Set the timeout value to 10s. The default value is 0.
   let timeout = 10 * 1000;
   
   // Create a NetConnection object.
   let conn = connection.createNetConnection(netSpecifier, timeout);
   // Enable listening for network status change events. If the network is available, an on_netAvailable event is returned.
   conn.on('netAvailable', ((handle: connection.NetHandle) => {
     let options: connection.QueryOptions = {
       family: connection.FamilyType.FAMILY_TYPE_IPV4
     }
     // Resolve the host name using the network connection and obtain only IPv4 addresses.
     handle.getAddressesByNameWithOptions(this.hostName, options).then((data: connection.NetAddress[]) => {
       hilog.info(0x0000, 'testTag', `Succeeded to get data: ${JSON.stringify(data)}`);
     })
   }));
   // Enable listening for network status change events. If the network is unavailable, an on_netUnavailable event is returned.
   conn.on('netUnavailable', ((data: void) => {
     hilog.info(0x0000, 'testTag', `net is unavailable, data is ${JSON.stringify(data)}`);
   }));
   ```

## Samples

The following sample is provided to help you better understand how to develop the DNS service:

* [DNS_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/DNS_case)
