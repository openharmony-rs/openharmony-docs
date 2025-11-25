# Using the Delayed Copy and Paste Feature of the Pasteboard
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong2-->
<!--Adviser: @fang-jinxu-->

## When to Use

The [pasteboard service](../../reference/apis-basic-services-kit/js-apis-pasteboard.md) provides the capability of managing the pasteboard of the system to support the copy and paste functions of the system.

When copy is performed repeatedly, redundant data is stored in the pasteboard cache, which increases the memory usage. To optimize the memory and support the paste of specified data types, the pasteboard provides the delayed copy and paste function.

When a user copies data in an application that uses the delayed copy and paste function, the real data is not immediately written into the cache of the pasteboard service, but is obtained from the application when the data needs to be pasted.

## Constraints

- The pasteboard content, including system service metadata and application settings, has a maximum size of 128 MB by default. For PCs/2-in-1 devices, the maximum size can be changed through system settings, with a valid range from 128 MB to 2 GB.

- NDK APIs support only record-based delayed copy and paste.

- ArkTS APIs support only PasteData-level delayed copy and paste.

## Using Record-based Delayed Copy and Paste (Recommended)

This solution allows you to query the data type before pasting. Applications can determine whether to request data from the pasteboard based on the query result.

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

### How to Develop

The following uses plain text and HTML data as an example to describe how to set delayed data copy to the pasteboard service.

For better code readability, the operation result verification of each step is omitted in the following code. In actual development, you need to check whether each call is successful.

1. Include header files.
   
   ```c
   #include <database/pasteboard/oh_pasteboard.h>
   #include <database/udmf/udmf.h>
   #include <database/udmf/uds.h>
   #include <database/udmf/udmf_meta.h>
   ```

2. Define a data providing function for **OH_UdmfRecordProvider** and a callback function for destroying this instance.
   
   ```c
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

3. Prepare the data for delayed copy in the pasteboard. Note that the plain text and HTML data is not written to the pasteboard until the **GetDataCallback** function is triggered when the data consumer obtains **OH_UdsPlainText** or **OH_UdsHtml** from **OH_UdmfRecord**.
   
   ```c
   // 3. Create an OH_UdmfRecord object.
   OH_UdmfRecord* record = OH_UdmfRecord_Create();
   // 4. Create an OH_UdmfRecordProvider object and set two callback functions used to provide and destruct data.
   OH_UdmfRecordProvider* provider = OH_UdmfRecordProvider_Create();
   OH_UdmfRecordProvider_SetData(provider, (void *)record, GetDataCallback, ProviderFinalizeCallback);
   
   // 5. Bind the provider to the record and set the supported data type.
   #define TYPE_COUNT 2
   const char* types[TYPE_COUNT] = {UDMF_META_PLAIN_TEXT, UDMF_META_HTML};
   OH_UdmfRecord_SetProvider(record, types, TYPE_COUNT, provider);
   
   // 6. Create an OH_UdmfData object and add OH_UdmfRecord to it.
   OH_UdmfData* setData = OH_UdmfData_Create();
   if (setData != nullptr) {
       OH_UdmfData_AddRecord(setData, record);
   }
   
   // 7. Create an OH_Pasteboard object and write data to the pasteboard.
   OH_Pasteboard* pasteboard = OH_Pasteboard_Create();
   if (setData != nullptr) {
       OH_Pasteboard_SetData(pasteboard, setData);
   }
   OH_UdmfRecordProvider_Destroy(provider);
   OH_UdmfRecord_Destroy(record);
   OH_UdmfData_Destroy(setData);
   ```

4. Obtain the data for delayed copy from the pasteboard.
   
   ```c
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
       //11. Query the data types in OH_UdmfRecord.
       unsigned typeCount = 0;
       char** recordTypes = OH_UdmfRecord_GetTypes(record, &typeCount);
   
       //12. Traverse data types.
       for (unsigned int typeIndex = 0; typeIndex < typeCount; ++typeIndex) {
           const char* recordType = recordTypes[typeIndex];
           ProcessRecordType(record, recordType);
       }
   }
   // ...
       // 8. Obtain OH_UdmfData from the pasteboard.
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
   
       // 9. Obtain all OH_UdmfRecord records from OH_UdmfData.
       unsigned int recordCount = 0;
       OH_UdmfRecord** getRecords = OH_UdmfData_GetRecords(getData, &recordCount);
       OH_UdsPlainText* udsText = nullptr;
       OH_UdsHtml* udsHtml = nullptr;
   
       // 10. Traverse OH_UdmfRecord records.
       for (unsigned int recordIndex = 0; recordIndex < recordCount; ++recordIndex) {
           OH_UdmfRecord* record = getRecords[recordIndex];
           ProcessRecord(record);
       }
   ```

5. Release the memory after the objects are used.
   
   ```c
   OH_UdsPlainText_Destroy(udsText);
   OH_UdsHtml_Destroy(udsHtml);
   OH_UdmfData_Destroy(getData);
   OH_Pasteboard_Destroy(pasteboard);
   ```


## Using PasteData-Level Delayed Copy and Paste

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
   
   ```ts\
   import { BusinessError, pasteboard } from '@kit.BasicServicesKit';
   import hilog from '@ohos.hilog';
   import { unifiedDataChannel, uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
   ```

2. Construct a piece of PlainText data and write the function for obtaining the delay data.

   ```ts
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

   ```ts
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

   ```ts
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

   ```ts
   try {
     systemPasteboard.setAppShareOptions(pasteboard.ShareOption.LOCALDEVICE);
     hilog.info(0xFF00, '[Sample_pasteboard]', 'Set app share options success.');
   } catch (err) {
     hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to gSet app share options. Cause: ' + err.message);
     // Error case
   }
   ```
   
6. Remove the pasteable range configuration set for the application.

   ```ts
   try {
     systemPasteboard.removeAppShareOptions();
     hilog.info(0xFF00, '[Sample_pasteboard]', 'Remove app share options success.');
   } catch (err) {
     hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to Remove app share options. Cause: ' + err.message);
     // Error case
   }
   ```
