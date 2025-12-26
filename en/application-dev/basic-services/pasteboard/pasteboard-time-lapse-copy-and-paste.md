# Using the Delayed Copy and Paste Feature of the Pasteboard
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## When to Use

The [pasteboard service](../../reference/apis-basic-services-kit/js-apis-pasteboard.md) provides the capability of managing the pasteboard of the system to support the copy and paste functions of the system.

When copy is performed repeatedly, redundant data is stored in the pasteboard cache, which increases the memory usage. To optimize the memory and support the paste of specified data types, the pasteboard provides the delayed copy and paste function.

When a user copies data in an application that uses the delayed copy and paste function, the real data is not immediately written into the cache of the pasteboard service, but is obtained from the application when the data needs to be pasted.

## Constraints

- The pasteboard content, including system service metadata and application settings, has a maximum size of 128 MB by default. For PCs/2-in-1 devices, the maximum size can be changed through system settings, with a valid range from 128 MB to 2 GB.

- NDK APIs support only record-based delayed copy and paste.

- ArkTS APIs support only data-based delayed copy and paste.

- If the amount of data to be copied is small and the time required for preparing data does not affect user experience, avoid using the delayed copy feature. Instead, you are advised to write data directly to the pasteboard.

## Using Record-based Delayed Copy and Paste (Recommended)

This solution allows you to query the data type before pasting. Applications can determine whether to request data from the pasteboard based on the query result.

Since API version 21, when an application exits, it can call [OH_Pasteboard_SetData](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_setdata) to submit all copied data and call [OH_Pasteboard_SyncDelayedDataAsync](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_syncdelayeddataasync) to notify the pasteboard to obtain all data.

1. When the application uses the delayed copy feature, only the data types supported by the application are written to the pasteboard. Before exiting, the application should call [OH_Pasteboard_SetData](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_setdata) to submit all copied data or call [OH_Pasteboard_SyncDelayedDataAsync](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_syncdelayeddataasync) to sync data to the pasteboard. The application can exit only after data sync is complete. Otherwise, other applications may fail to obtain data.

2. Calling the [OH_Pasteboard_SyncDelayedDataAsync](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_syncdelayeddataasync) API prolongs the exit process. Applications should copy data to the pasteboard directly instead of calling the [OH_UdmfRecordProvider_SetData](../../reference/apis-arkdata/capi-udmf-h.md#oh_udmfrecordprovider_setdata) and [OH_Pasteboard_SyncDelayedDataAsync](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_syncdelayeddataasync) APIs.

3. If an application exits abnormally when it uses the delayed copy feature, the data sync cannot be triggered. As a result, other applications cannot obtain data to paste.

### Available APIs

For details about the APIs, see [Pasteboard](../../reference/apis-basic-services-kit/capi-pasteboard.md) and [UDMF](../../reference/apis-arkdata/capi-udmf.md).

| Name| Description                                                                  |
| -------- |----------------------------------------------------------------------|
| OH_UdmfRecordProvider* OH_UdmfRecordProvider_Create()        | Creates a pointer to the **OH_UdmfRecordProvider** instance.                         |
| int OH_UdmfRecordProvider_SetData(OH_UdmfRecordProvider* provider, void* context, const OH_UdmfRecordProvider_GetData callback, const UdmfData_Finalize finalize) | Sets a callback for the **OH_UdmfRecordProvider**.                             |
| int OH_UdmfRecord_SetProvider(OH_UdmfRecord* pThis, const char* const* types, unsigned int count, OH_UdmfRecordProvider* provider) | Sets **OH_UdmfRecordProvider** in an **OH_UdmfRecord** instance.                    |
| int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data) | Writes data to the pasteboard.                                   |
| OH_UdmfData * OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status) | Obtains data from the pasteboard.|
| OH_UdmfRecord** OH_UdmfData_GetRecords(OH_UdmfData* pThis, unsigned int* count) | Obtains all data records from an **OH_UdmfData** instance.                          |
| void OH_Pasteboard_SyncDelayedDataAsync(OH_Pasteboard* pasteboard, void (*callback)(int errorCode)) | Syncs all delayed data from the application to the pasteboard. When the application uses the delayed copy feature, only the data types supported by the application are written to the pasteboard. Before exiting, the application should call [OH_Pasteboard_SetData](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_setdata) to submit all copied data or call [OH_Pasteboard_SyncDelayedDataAsync](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_syncdelayeddataasync) to sync data to the pasteboard. The application can exit only after data sync is complete. Otherwise, other applications may fail to obtain data.|

### How to Develop

The following uses plain text and HTML data as an example to describe how to set delayed data copy to the pasteboard service.

For better code readability, the operation result verification of each step is omitted in the following code. In actual development, you need to check whether each call is successful.

1. Include header files.
   
   <!-- @[pasteboard_timelapse_Record1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->    
   
   ``` C++
   #include <cstring>
   #include <hilog/log.h>
   #include <database/pasteboard/oh_pasteboard.h>
   #include <database/udmf/udmf.h>
   #include <database/udmf/uds.h>
   #include <database/udmf/udmf_meta.h>
   #include <accesstoken/ability_access_control.h>
   ```


2. Define a data providing function for **OH_UdmfRecordProvider** and a callback function for destroying this instance.

   <!-- @[pasteboard_timelapse_Record2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 1. Define a callback to be invoked to return the pasteboard data obtained.
   void* GetDataCallback(void* context, const char* type)
   {
       // Plain text type.
       if (memcmp(type, UDMF_META_PLAIN_TEXT, sizeof(UDMF_META_PLAIN_TEXT) - 1) == 0) {
           // Create a Uds object of the plain text type.
           OH_UdsPlainText* udsText = OH_UdsPlainText_Create();
           // Set the plain text content.
           OH_UdsPlainText_SetContent(udsText, "hello world");
           return udsText;
       } else if (strcmp(type, UDMF_META_HTML) == 0) {
           // Create a Uds object of the HTML type.
           OH_UdsHtml* udsHtml = OH_UdsHtml_Create();
           // Set the HTML content.
           OH_UdsHtml_SetContent(udsHtml, "<div>hello world</div>");
           return udsHtml;
       }
       return nullptr;
   }
   // 2. Define a callback to be invoked when OH_UdmfRecordProvider is destroyed.
   void ProviderFinalizeCallback(void* context)
   {
       OH_LOG_INFO(LOG_APP, "OH_UdmfRecordProvider finalize.");
   }
   ```


3. Define the **OH_Pasteboard_SyncDelayedDataAsync** callback.

   <!-- @[pasteboard_timelapse_Record3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 3. Define the callback triggered when the application exits and calls the delayed data sync API.
   void SyncCallback(int errorCode)
   {
       // Application exits.
   }
   ```


4. Prepare the data for delayed copy in the pasteboard. The plain text and HTML data is not written to the pasteboard until the **GetDataCallback** function is triggered when the data consumer obtains **OH_UdsPlainText** or **OH_UdsHtml** from **OH_UdmfRecord**.
   
   <!-- @[pasteboard_timelapse_Record4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->    
   
   ``` C++
   OH_Pasteboard* CreateAndSetPasteboardData()
   {
       // 4. Create an OH_UdmfRecord object.
       OH_UdmfRecord* record = OH_UdmfRecord_Create();
       // 5. Create an OH_UdmfRecordProvider object and set two callback functions used to provide and destruct data.
       OH_UdmfRecordProvider* provider = OH_UdmfRecordProvider_Create();
       OH_UdmfRecordProvider_SetData(provider, (void *)record, GetDataCallback, ProviderFinalizeCallback);
       // 6. Bind the provider to the record and set the supported data type.
       #define TYPE_COUNT 2
       const char* types[TYPE_COUNT] = {UDMF_META_PLAIN_TEXT, UDMF_META_HTML};
       OH_UdmfRecord_SetProvider(record, types, TYPE_COUNT, provider);
       // 7. Create an OH_UdmfData object and add OH_UdmfRecord to it.
       OH_UdmfData* setData = OH_UdmfData_Create();
       if (setData != nullptr) {
           OH_UdmfData_AddRecord(setData, record);
       }
       // 8. Create an OH_Pasteboard object and write data to the pasteboard.
       OH_Pasteboard* pasteboard = OH_Pasteboard_Create();
       if (setData != nullptr) {
           OH_Pasteboard_SetData(pasteboard, setData);
       }
       OH_UdmfRecordProvider_Destroy(provider);
       OH_UdmfRecord_Destroy(record);
       OH_UdmfData_Destroy(setData);
       return pasteboard;
   }
   ```


5. Obtain the data for delayed copy from the pasteboard.
   
   <!-- @[pasteboard_timelapse_Record5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->    
   
   ``` C++
   void ProcessRecordType(OH_UdmfRecord* record, const char* recordType)
   {
       OH_UdsPlainText* udsText = nullptr;
       OH_UdsHtml* udsHtml = nullptr;
       if (strcmp(recordType, UDMF_META_PLAIN_TEXT) == 0) {
           // Create a Uds object of the plain text type.
           udsText = OH_UdsPlainText_Create();
           if (udsText != nullptr) {
               // Obtain the Uds object of the plain text type from record.
               OH_UdmfRecord_GetPlainText(record, udsText);
               // Obtain the content from the Uds object.
               const char* content = OH_UdsPlainText_GetContent(udsText);
           } else if (strcmp(recordType, UDMF_META_HTML) == 0) {
               // Create a Uds object of the HTML type.
               udsHtml = OH_UdsHtml_Create();
               if (udsHtml != nullptr) {
                   // Obtain the Uds object of the HTML type from record.
                   OH_UdmfRecord_GetHtml(record, udsHtml);
                   // Obtain the content from the Uds object.
                   const char* content = OH_UdsHtml_GetContent(udsHtml);
               }
           }
       }
   }
   void ProcessRecord(OH_UdmfRecord* record)
   {
       // 13. Query the data types in OH_UdmfRecord.
       unsigned typeCount = 0;
       char** recordTypes = OH_UdmfRecord_GetTypes(record, &typeCount);
       // 14. Traverse data types.
       for (unsigned int typeIndex = 0; typeIndex < typeCount; ++typeIndex) {
           const char* recordType = recordTypes[typeIndex];
           ProcessRecordType(record, recordType);
       }
   }
   
   static napi_value NAPI_Pasteboard_time(napi_env env, napi_callback_info info)
   {
       OH_Pasteboard* pasteboard = CreateAndSetPasteboardData();
       // 9. Record the number of changes to pasteboard data.
       uint32_t changeCount = OH_Pasteboard_GetChangeCount(pasteboard);
       // 10. Obtain OH_UdmfData from the pasteboard.
       int status = -1;
       bool hasPermission = OH_AT_CheckSelfPermission("ohos.permission.READ_PASTEBOARD");
       if (!hasPermission) {
           OH_LOG_ERROR(LOG_APP, "No Permission READ_PASTEBOARD");
       };
       OH_UdmfData* getData = OH_Pasteboard_GetData(pasteboard, &status);
       if (getData == nullptr) {
           // Handle the error case and clear resources.
           OH_LOG_ERROR(LOG_APP, "Failed to get data from pasteboard, status: %d\n", status);
       }
       // 11. Obtain all OH_UdmfRecord objects from OH_UdmfData.
       unsigned int recordCount = 0;
       OH_UdmfRecord** getRecords = OH_UdmfData_GetRecords(getData, &recordCount);
       OH_UdsPlainText* udsText = nullptr;
       OH_UdsHtml* udsHtml = nullptr;
       // 12. Traverse OH_UdmfRecord.
       for (unsigned int recordIndex = 0; recordIndex < recordCount; ++recordIndex) {
           OH_UdmfRecord* record = getRecords[recordIndex];
           ProcessRecord(record);
       }
   ```


6. If the data in the pasteboard does not change, the application notifies the pasteboard to obtain all data before exiting and exits only after the callback is complete. Otherwise, other applications may fail to obtain data.

   <!-- @[pasteboard_timelapse_Record6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->    
   
   ``` C++
   // 15. Check whether the data in the pasteboard changes.
   uint32_t newChangeCount = OH_Pasteboard_GetChangeCount(pasteboard);
   if (newChangeCount == changeCount) {
       // 16. Notify the pasteboard to obtain all data.
       OH_Pasteboard_SyncDelayedDataAsync(pasteboard, SyncCallback);
       // The application exits only after SyncCallback is complete.
   } else {
       // Application exits.
       OH_LOG_INFO(LOG_APP, "No newChangeCount in pasteboard.");
   }
   ```

7. Release the memory after the objects are used.
   
   <!-- @[pasteboard_timelapse_Record7](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->    
   
   ``` C++
       OH_UdsPlainText_Destroy(udsText);
       OH_UdsHtml_Destroy(udsHtml);
       OH_UdmfData_Destroy(getData);
       OH_Pasteboard_Destroy(pasteboard);
   }
   ```



## Using Data-based Delayed Copy and Paste (Not Recommended)

You are not allowed to query data type before pasting.

### Available APIs

| Name| Description                                                                  |
| -------- |----------------------------------------------------------------------|
| setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise\<void> | Writes data of the unified data type to the system pasteboard. This API cannot be called in the same thread as **getUnifiedDataSync** when the delayed copy and paste function is used.|
| setUnifiedDataSync(data: unifiedDataChannel.UnifiedData): void | Writes data of the unified data type to the system pasteboard. This API returns the result synchronously and cannot be called in the same thread as **getUnifiedDataSync** when the delayed copy and paste function is used.|
| getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData> | Reads data of the unified data type from the system pasteboard.|
| getUnifiedDataSync(): unifiedDataChannel.UnifiedData | Reads data of the unified data type from the system pasteboard. This API returns the result synchronously and cannot be called in the same thread as **setUnifiedData** and **setUnifiedDataSync** when the delayed copy and paste function is used.|
| setAppShareOptions(shareOptions: ShareOption): void | Sets pasteable range of pasteboard data for an application.|
| removeAppShareOptions(): void | Removes the pasteable range configuration set for the application.|

### How to Develop

1. Import the **pasteboard**, **unifiedDataChannel**, and **uniformTypeDescriptor** modules.
   
   <!-- @[pasteboard_timelaps_PasteData1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->    
   
   ``` TypeScript
   import { BusinessError, pasteboard } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { unifiedDataChannel, uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
   const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
   ```


2. Construct a piece of PlainText data and write the function for obtaining the delay data.

   <!-- @[pasteboard_timelaps_PasteData2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->   
   
   ``` TypeScript
   let plainTextData = new unifiedDataChannel.UnifiedData();
   let getDelayPlainText = ((dataType: string) => {
     let plainText = new unifiedDataChannel.PlainText();
     plainText.details = {
       Key: 'delayPlaintext',
       Value: 'delayPlaintext',
     };
     plainText.textContent = 'delayTextContent';
     plainText.abstract = 'delayTextContent';
     plainTextData.addRecord(plainText);
     return plainTextData;
   });
   ```


3. Save a piece of PlainText data to the system pasteboard.

   <!-- @[pasteboard_timelaps_PasteData3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->    
   
   ``` TypeScript
   let setDelayPlainText = () => {
     plainTextData.properties.shareOptions = unifiedDataChannel.ShareOptions.CROSS_APP;
     // For cross-application use, set this parameter to CROSS_APP. For intra-application use, set this parameter to IN_APP.
     plainTextData.properties.getDelayData = getDelayPlainText;
     pasteboard.getSystemPasteboard().setUnifiedData(plainTextData).then(() => {
       hilog.info(0xFF00, '[Sample_pasteboard]', 'Succeeded in set PlainText.');
       // The data is successfully saved, which is a normal case.
     }).catch((error: BusinessError) => {
       hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to set PlainText. Cause: ' + error.message);
       // Error case
     });
   }
   ```


4. Read the text data from the system pasteboard.

   <!-- @[pasteboard_timelaps_PasteData4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->    
   
   ``` TypeScript
   let getPlainTextUnifiedData = (() => {
     pasteboard.getSystemPasteboard().getUnifiedData().then((data) => {
       let outputData = data;
       let records = outputData.getRecords();
       if (records[0].getType() == uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) {
         let record = records[0] as unifiedDataChannel.PlainText;
         hilog.info(0xFF00, '[Sample_pasteboard]', 'GetPlainText success, type:' + records[0].getType());
         // Note: The data copied by users is sensitive information. Do not print the data obtained from the pasteboard in plaintext in logs.
       } else {
         hilog.info(0xFF00, '[Sample_pasteboard]', 'Get Plain Text Data No Success, Type is: ' + records[0].getType());
       }
     }).catch((error: BusinessError) => {
       hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to get PlainTextUnifiedData. Cause: ' + error.message);
       // Error case
     })
   })
   ```

   
5. Set pasteable range of pasteboard data for an application.

   <!-- @[pasteboard_timelaps_PasteData5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->    
   
   ``` TypeScript
   try {
     systemPasteboard.setAppShareOptions(pasteboard.ShareOption.LOCALDEVICE);
     hilog.info(0xFF00, '[Sample_pasteboard]', 'Set app share options success.');
   } catch (err) {
     hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to Set app share options. Cause: ' + err.message);
     // Error case
   }
   ```

   
6. Remove the pasteable range configuration set for the application.

   <!-- @[pasteboard_timelaps_PasteData6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/PasteboardModel.ets) -->    
   
   ``` TypeScript
   try {
     systemPasteboard.removeAppShareOptions();
     hilog.info(0xFF00, '[Sample_pasteboard]', 'Remove app share options success.');
   } catch (err) {
     hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to Remove app share options. Cause: ' + err.message);
     // Error case
   }
   ```
