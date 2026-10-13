# Discovering NearLink Devices
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=0331a80a2631c55d2d3d88a8180d5918e41aad9c translatedAt=2026-09-29T10:56:52.387Z pushedAt=2026-09-30T06:22:44.414Z -->

NearLink device discovery consists of two phases: advertising and scanning. A peripheral device announces itself by sending NearLink advertisements, and a central device discovers advertising peripheral devices by initiating a NearLink scan. Advertising and scanning can be used independently or together to enable discovery and connection between devices.

Before development, complete the permission declaration and runtime request as described in [Getting Started](nearlink-preparations-guide.md), and ensure that NearLink is enabled on the device (see [Getting Started > Querying the NearLink Switch State](nearlink-preparations-guide.md#querying-the-nearlink-switch-state)).

## Initiating NearLink Advertising

Send a NearLink advertisement. The advertising data can be scanned by central devices that support the NearLink capability.

### Available APIs

To send a NearLink advertisement, for the complete API description and sample code, see [@ohos.nearlink.advertising (NearLink Advertising Capability)](../../reference/apis-connectivity-kit/js-apis-nearlink-advertising.md).

| API | Description |
| -------- | -------- |
| startAdvertising(advertisingParams: AdvertisingParams): Promise&lt;number&gt; | Starts NearLink advertising. This API uses a Promise to return the result asynchronously. |
| stopAdvertising(advertisingId: number): Promise&lt;void&gt; | Stops NearLink advertising. This API uses a Promise to return the result asynchronously. |
| onAdvertisingStateChange(callback: Callback&lt;AdvertisingStateChangeInfo&gt;): void | Subscribes to NearLink advertising state change events. This API uses a callback to return the result asynchronously. |
| offAdvertisingStateChange(callback?: Callback&lt;AdvertisingStateChangeInfo&gt;): void | Unsubscribes from NearLink advertising state change events. This API uses a callback to return the result asynchronously. |

### How to Develop

1. Import the required modules.

    <!-- @[advertising_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/AdvertisingPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { advertising } from '@kit.ConnectivityKit';
    ```

2. Subscribe to NearLink advertising state change events.

    <!-- @[advertising_on_state_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/AdvertisingPage.ets) -->
    
    ``` TypeScript
    try {
      advertising.onAdvertisingStateChange((data: advertising.AdvertisingStateChangeInfo) => {
        hilog.info(0x0000, 'testTag',
          `Advertising state changed: id=${data.advertisingId}, state=${data.state}`);
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

3. Construct the advertising parameters and data required by the user. The service UUID carried in the advertisement must be a custom UUID. For details, see [NearLink FAQs > What Is the Difference Between Standard UUIDs and Custom UUIDs](nearlink-faq-guide.md#what-is-the-difference-between-standard-uuids-and-custom-uuids).

    <!-- @[advertising_build_params](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/AdvertisingPage.ets) -->
    
    ``` TypeScript
    let manufacturerData = new Uint8Array([0x01, 0x02, 0x03, 0x04]);
    
    let serviceValueBuffer = new Uint8Array(4);
    serviceValueBuffer[0] = 0x0A;
    serviceValueBuffer[1] = 0x0B;
    serviceValueBuffer[2] = 0x0C;
    serviceValueBuffer[3] = 0x0D;
    
    let setting: advertising.AdvertisingSettings = {
      interval: 160,
      power: advertising.TxPowerMode.ADV_TX_POWER_MEDIUM,
      isConnectable: true
    };
    
    let manufactureDataUnit: advertising.ManufacturerData = {
      manufacturerId: 0x1234,
      manufacturerData: manufacturerData.buffer
    };
    
    let serviceDataUnit: advertising.ServiceData = {
      serviceUuid: 'FFFFFFFF-1234-5678-ABCD-000000001254',
      serviceData: serviceValueBuffer.buffer
    };
    
    let advData: advertising.AdvertisingData = {
      serviceUuids: ['FFFFFFFF-1234-5678-ABCD-000000001254'],
      manufacturerData: [manufactureDataUnit],
      serviceData: [serviceDataUnit],
      includeDeviceName: true
    };
    
    let advertisingParams: advertising.AdvertisingParams = {
      advertisingSettings: setting,
      advertisingData: advData
    };
    ```

4. Start NearLink advertising. The returned advId indicates the ID of this broadcast. `advertisingParams` is the advertising parameters constructed in step 3.

    <!-- @[advertising_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/AdvertisingPage.ets) -->
    
    ``` TypeScript
    try {
      let advId: number = await advertising.startAdvertising(advertisingParams);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

5. Stop NearLink advertising. `advId` is the advertising ID returned when the advertising is started in step 4.

    <!-- @[advertising_stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/AdvertisingPage.ets) -->
    
    ``` TypeScript
    try {
      await advertising.stopAdvertising(advId);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

6. Unsubscribe from NearLink advertising state change events.

    <!-- @[advertising_off_state_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/AdvertisingPage.ets) -->
    
    ``` TypeScript
    try {
      advertising.offAdvertisingStateChange();
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

## Initiating a NearLink Scan

Initiate a NearLink scan to discover peripheral devices that are sending NearLink advertisements.

### Available APIs

The following table lists the APIs for initiating NearLink scans. For the complete API description and sample code, see [@ohos.nearlink.scan (NearLink Scan)](../../reference/apis-connectivity-kit/js-apis-nearlink-scan.md).

| API | Description |
| -------- | -------- |
| startScan(filters: Array&lt;ScanFilters&gt; \| null, options?: ScanOptions): Promise&lt;void&gt; | Starts a NearLink scan. This API uses a Promise to return the result asynchronously. |
| stopScan(): Promise&lt;void&gt; | Stops a NearLink scan. This API uses a Promise to return the result asynchronously. |
| onDeviceFound(callback: Callback&lt;Array&lt;ScanResults&gt;&gt;): void | Subscribes to NearLink scan results. This API uses a callback to return the result asynchronously. |
| offDeviceFound(callback?: Callback&lt;Array&lt;ScanResults&gt;&gt;): void | Unsubscribes from NearLink scan results. This API uses a callback to return the result asynchronously. |

### How to Develop

1. Import the required modules.

    <!-- @[scan_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { scan } from '@kit.ConnectivityKit';
    import { util } from '@kit.ArkTS';
    ```

2. Subscribe to scan results. To avoid duplicate subscriptions, first call [offDeviceFound()](../../reference/apis-connectivity-kit/js-apis-nearlink-scan.md#scanoffdevicefound) to cancel the existing subscription, and then call [onDeviceFound()](../../reference/apis-connectivity-kit/js-apis-nearlink-scan.md#scanondevicefound) to subscribe to scan results. The callback is triggered when a device is discovered. The `parseScanResult` parsing method called in the callback is defined in step 3.

    <!-- @[scan_on_device_found](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    try {
      scan.offDeviceFound();
      scan.onDeviceFound((data: scan.ScanResults[]) => {
        data.forEach((item) => {
          hilog.info(0x0000, 'testTag',
            `Scan result: addr=${item.address}, name=${item.deviceName}, rssi=${item.rssi}`);
          this.parseScanResult(item.data);
        });
        // ...
      });
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

3. Parse the scan results (advertising data). The `data` field in the scan results is the raw data of the advertising packet, organized in the TLV (Type-Length-Value) format. For the definition of each data type, see the data types of device public information in *NearLink Wireless Communication System Basic Service Layer Device Discovery and Service Management* in the [NearLink standard](https://www.isla.org/trial). By parsing the data, you can obtain information such as the discovery level, service data, service UUID list, local name, and manufacturer data:

    <!-- @[scan_parse_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    const ADV_DATA_TYPE_DISCOVERY_LEVEL = 0x01; // Discovery level
    const ADV_DATA_TYPE_SERVICE_DATA_16_BIT_UUID = 0x03; // Standard service data
    const ADV_DATA_TYPE_SERVICE_DATA_128_BIT_UUID = 0x04; // Custom service data
    const ADV_DATA_TYPE_COMPLETE_LIST_16_BIT_SERVICE_UUIDS = 0x05; // Complete list of standard service UUIDs
    const ADV_DATA_TYPE_COMPLETE_LIST_128_BIT_SERVICE_UUIDS = 0x06; // Complete list of custom service UUIDs
    const ADV_DATA_TYPE_INCOMPLETE_LIST_16_BIT_SERVICE_UUIDS = 0x07; // Incomplete list of standard service UUIDs
    const ADV_DATA_TYPE_INCOMPLETE_LIST_128_BIT_SERVICE_UUIDS = 0x08; // Incomplete list of custom service UUIDs
    const ADV_DATA_TYPE_SHORTENED_LOCAL_NAME = 0x0A; // Shortened local name of the device
    const ADV_DATA_TYPE_COMPLETE_LOCAL_NAME = 0x0B; // Complete local name of the device
    const ADV_DATA_TYPE_MANUFACTURER_SPECIFIC_DATA = 0xFF; // Manufacturer-specific data
    
    const NEARLINK_UUID_16_BIT_LENGTH = 2;
    const NEARLINK_UUID_128_BIT_LENGTH = 16;
    const NEARLINK_MANUFACTURER_ID_LENGTH = 2;
    // Base identifier prefix of a standard UUID (112 bits).
    const STANDARD_UUID_BASE_PREFIX = '37BEA880-FC70-11EA-B720-00000000';
    
    // Parsing result of the advertising packet data.
    interface ScanResultData {
      discoveryLevel: number;
      serviceData: Record<string, Uint8Array>;
      standardServiceUuids: string[];
      customServiceUuids: string[];
      localName: string;
      manufacturerData: Record<number, Uint8Array>;
    }
    ```

    <!-- @[scan_parse_result_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    parseScanResult(data: ArrayBuffer): ScanResultData {
      let advData = new Uint8Array(data);
      let result: ScanResultData = {
        discoveryLevel: -1,
        serviceData: {},
        standardServiceUuids: [],
        customServiceUuids: [],
        localName: '',
        manufacturerData: {}
      };
      if (advData.byteLength === 0) {
        hilog.info(0x0000, 'testTag', 'adv data length is 0');
        return result;
      }
      let curPos = 0;
      while (curPos < advData.byteLength) {
        // Each data item consists of a 1-byte type, a 1-byte length, and the data content.
        let dataType = advData[curPos++];
        let dataLength = advData[curPos++];
        if (dataLength === 0) {
          break; // A length of 0 indicates the end of the data.
        }
        switch (dataType) {
          case ADV_DATA_TYPE_DISCOVERY_LEVEL:
            result.discoveryLevel = advData[curPos];
            break;
          case ADV_DATA_TYPE_SERVICE_DATA_16_BIT_UUID:
            this.parseServiceData(NEARLINK_UUID_16_BIT_LENGTH, curPos, dataLength, advData, result.serviceData);
            break;
          case ADV_DATA_TYPE_SERVICE_DATA_128_BIT_UUID:
            this.parseServiceData(NEARLINK_UUID_128_BIT_LENGTH, curPos, dataLength, advData, result.serviceData);
            break;
          case ADV_DATA_TYPE_COMPLETE_LIST_16_BIT_SERVICE_UUIDS:
          case ADV_DATA_TYPE_INCOMPLETE_LIST_16_BIT_SERVICE_UUIDS:
            this.parseServiceUuids(NEARLINK_UUID_16_BIT_LENGTH, curPos, dataLength, advData,
              result.standardServiceUuids);
            break;
          case ADV_DATA_TYPE_COMPLETE_LIST_128_BIT_SERVICE_UUIDS:
          case ADV_DATA_TYPE_INCOMPLETE_LIST_128_BIT_SERVICE_UUIDS:
            this.parseServiceUuids(NEARLINK_UUID_128_BIT_LENGTH, curPos, dataLength, advData,
              result.customServiceUuids);
            break;
          case ADV_DATA_TYPE_SHORTENED_LOCAL_NAME:
          case ADV_DATA_TYPE_COMPLETE_LOCAL_NAME:
            let decoder = util.TextDecoder.create('utf-8');
            result.localName = decoder.decodeToString(advData.slice(curPos, curPos + dataLength));
            break;
          case ADV_DATA_TYPE_MANUFACTURER_SPECIFIC_DATA:
            this.parseManufacturerData(curPos, dataLength, advData, result.manufacturerData);
            break;
          default:
            break;
        }
        curPos += dataLength; // Move to the next data item.
      }
      hilog.info(0x0000, 'testTag',
        `discoveryLevel: ${result.discoveryLevel}, serviceData: ${JSON.stringify(result.serviceData)}, ` +
        `standardServiceUuids: ${JSON.stringify(result.standardServiceUuids)}, ` +
        `customServiceUuids: ${JSON.stringify(result.customServiceUuids)}, ` +
        `localName: ${result.localName}, manufacturerData: ${JSON.stringify(result.manufacturerData)}`);
      return result;
    }
    
    parseServiceData(uuidLength: number, curPos: number, dataLength: number,
      advData: Uint8Array, serviceData: Record<string, Uint8Array>): void {
      let uuid = advData.slice(curPos, curPos + uuidLength);
      let value = advData.slice(curPos + uuidLength, curPos + dataLength);
      serviceData[this.getUuidFromUint8Array(uuidLength, uuid)] = value;
    }
    
    parseServiceUuids(uuidLength: number, curPos: number, dataLength: number,
      advData: Uint8Array, serviceUuids: string[]): void {
      while (dataLength > 0) {
        let uuid = advData.slice(curPos, curPos + uuidLength);
        serviceUuids.push(this.getUuidFromUint8Array(uuidLength, uuid));
        dataLength -= uuidLength;
        curPos += uuidLength;
      }
    }
    
    parseManufacturerData(curPos: number, dataLength: number,
      advData: Uint8Array, manufacturerData: Record<number, Uint8Array>): void {
      let manufacturerId = (advData[curPos + 1] << 8) + advData[curPos];
      let value = advData.slice(curPos + NEARLINK_MANUFACTURER_ID_LENGTH, curPos + dataLength);
      manufacturerData[manufacturerId] = value;
    }
    
    getUuidFromUint8Array(uuidLength: number, uuidData: Uint8Array): string {
      let hex = '';
      for (let i = uuidLength - 1; i > -1; i--) {
        hex += uuidData[i].toString(16).padStart(2, '0');
      }
      switch (uuidLength) {
        case NEARLINK_UUID_16_BIT_LENGTH:
          return STANDARD_UUID_BASE_PREFIX + hex;
        case NEARLINK_UUID_128_BIT_LENGTH:
          return `${hex.substring(0, 8)}-${hex.substring(8, 12)}-${hex.substring(12, 16)}-` +
            `${hex.substring(16, 20)}-${hex.substring(20, 32)}`;
        default:
          return '';
      }
    }
    ```

4. Configure the scan filter and set the expected device name, address, and other information. A filter must carry at least one filtering condition. You can configure multiple filters. The conditions between multiple filters are in an OR relationship, and the conditions within a single filter are in an AND relationship. Passing `null` to `filters` means no filtering. Passing an empty array or a filter array with all fields empty returns the [36100042 empty array](../../reference/apis-connectivity-kit/errorcode-nearlink-service.md#36100042-empty-array) error.

    <!-- @[scan_config_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    let deviceNameFilter: string = 'deviceName1';
    let addressFilter: string = '11:22:33:44:AA:BB';
    
    let filters: scan.ScanFilters[] = [];
    if (deviceNameFilter.length > 0) {
      filters.push({ deviceName: deviceNameFilter });
    }
    if (addressFilter.length > 0) {
      filters.push({ address: addressFilter });
    }
    ```

5. Start the NearLink scan. Here, `filters` is the scan filter configured in step 4, and `scanOptions` is the scan parameter.

    <!-- @[scan_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    try {
      let scanOptions: scan.ScanOptions = {
        scanMode: scan.ScanMode.SCAN_MODE_LOW_POWER
      };
      await scan.startScan(filters, scanOptions);
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```

6. Stop the NearLink scan.

    <!-- @[scan_stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    try {
      await scan.stopScan();
      // ...
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
      // ...
    }
    ```

7. Unsubscribe from the scan results.

    <!-- @[scan_off_device_found](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/NearLink/entry/src/main/ets/nearlink/pages/ScanConfigPage.ets) -->
    
    ``` TypeScript
    try {
      scan.offDeviceFound();
    } catch (err) {
      hilog.error(0x0000, 'testTag',
        `errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
    }
    ```
