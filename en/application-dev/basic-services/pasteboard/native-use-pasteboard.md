# Using the Pasteboard to Copy and Paste (C/C++)
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## When to Use

The pasteboard allows you to copy and paste data of the plain text, hypertext, and URI.

## Basic Concepts

- [**OH_PasteboardObserver**](../../reference/apis-basic-services-kit/capi-pasteboard-oh-pasteboardobserver.md): pasteboard observer object, which is used to listen for data changes on the pasteboard.
- [**OH_Pasteboard**](../../reference/apis-basic-services-kit/capi-pasteboard-oh-pasteboard.md): pasteboard object, which is used to query and write data.
- [**OH_UdmfData**](../../reference/apis-arkdata/capi-udmf-oh-udmfdata.md): unified data object.

## Constraints

- The pasteboard content, including system service metadata and application settings, has a maximum size of 128 MB by default. For PCs/2-in-1 devices, the maximum size can be changed through system settings, with a valid range from 128 MB to 2 GB.
- To ensure the accuracy of the pasteboard data, only one copy can be performed at a time.
- Currently, supported data types include **OH_UdsPlainText** (plain text), **OH_UdsHtml** (hypertext markup language), **OH_UdsFileUri** (file URI). **OH_UdsPixelMap** (pixel map), **OH_UdsHyperlink** (hyperlink), **OH_UdsAppItem** (application icon), and custom type. The data types supported by ArkTS APIs are different from those supported by NDK APIs. You need to match the data types with the corresponding APIs during usage. For details, see [Using the Pasteboard to Copy and Paste](../pasteboard/use-pasteboard-to-copy-and-paste.md).
- When you copy and paste data of a custom type, the specified type name cannot be the same as an existing one.
- Since API version 12, [permission control](get-pastedata-permission-guidelines.md) is added to the pasteboard reading API to enhance user privacy protection.
- The [setUnifiedData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#setunifieddata12) and [getUnifiedData](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getunifieddata12) APIs added in API version 12 are independent of the [OH_Pasteboard_SetData](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_setdata) and [OH_Pasteboard_GetData](../../reference/apis-basic-services-kit/capi-oh-pasteboard-h.md#oh_pasteboard_getdata) APIs mentioned in this topic. Use the corresponding APIs when writing and reading data.

## Available APIs

For details about more APIs and their usage, see [Pasteboard](../../reference/apis-basic-services-kit/capi-pasteboard.md).

| API                                                    | Description                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| OH_PasteboardObserver* OH_PasteboardObserver_Create()        | Creates a pasteboard observer object.                     |
| OH_PasteboardObserver_Destroy(OH_PasteboardObserver* observer) | Destroys the pasteboard observer object.                         |
| int OH_PasteboardObserver_SetData(OH_PasteboardObserver* observer, void* context, const Pasteboard_Notify callback, const Pasteboard_Finalize finalize) | Sets the callback used to return data changes to the pasteboard observer object. |
| OH_Pasteboard* OH_Pasteboard_Create()                        | Creates a pasteboard instance.                                   |
| void OH_Pasteboard_Destroy(OH_Pasteboard* pasteboard)        | Destroys the pasteboard instance.                                       |
| int OH_Pasteboard_Subscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer) | Subscribes to the pasteboard observer.                                 |
| int OH_Pasteboard_Unsubscribe(OH_Pasteboard* pasteboard, int type, const OH_PasteboardObserver* observer) | Unsubscribes from the pasteboard observer.                           |
| bool OH_Pasteboard_IsRemoteData(OH_Pasteboard* pasteboard)   | Checks whether the pasteboard data comes from remote devices.                   |
| int OH_Pasteboard_GetDataSource(OH_Pasteboard* pasteboard, char* source, unsigned int len) | Obtains the pasteboard data source.                             |
| bool OH_Pasteboard_HasType(OH_Pasteboard* pasteboard, const char* type) | Checks whether the pasteboard contains data of the specified type.                     |
| bool OH_Pasteboard_HasData(OH_Pasteboard* pasteboard)        | Checks whether the pasteboard contains data.                               |
| OH_UdmfData* OH_Pasteboard_GetData(OH_Pasteboard* pasteboard, int* status) | Obtains data from the pasteboard.                                   |
| int OH_Pasteboard_SetData(OH_Pasteboard* pasteboard, OH_UdmfData* data) | Writes data to the pasteboard.                                   |
| int OH_Pasteboard_ClearData(OH_Pasteboard* pasteboard)       | Clears data from the pasteboard.                                   |
| void (\*Pasteboard_Notify)(void\* context, Pasteboard_NotifyType type) | Notifies data changes in the pasteboard.                             |
| void (\*Pasteboard_Finalize)(void\* context)                 | Releases context resources when the pasteboard observer object is destroyed.|

## How to Develop

1. Add dynamic link libraries.

   ```CMake
   # Add the following libraries to **CMakeLists.txt**.
   libudmf.so
   libpasteboard.so
   ```

2. Include header files.

   <!-- @[pasteboard_native2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   #include <cstdio>
   #include <cstring>
   #include <hilog/log.h>
   #include <database/pasteboard/oh_pasteboard.h>
   #include <database/udmf/udmf.h>
   #include <database/udmf/uds.h>
   ```


3. Define the callback for listening for pasteboard data changes.

    <!-- @[pasteboard_native3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    // Define the callback for notifying data changes in the pasteboard.
    static void PasteboardNotifyImpl2(void* context, Pasteboard_NotifyType type)
    {
        OH_LOG_INFO(LOG_APP, "Pasteboard_NotifyType, type: %d", type);
    }
    // Define the callback for notifying when the pasteboard observer object is destroyed.
    static void PasteboardFinalizeImpl2(void* context)
    {
        OH_LOG_INFO(LOG_APP, "callback: Pasteboard_Finalize");
    }
    ```


4. Subscribe to the pasteboard observer.

   <!-- @[pasteboard_native4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static void PasteboardTestObserver()
   {
       // 1. Create a pasteboard instance.
       OH_Pasteboard* pasteboard = OH_Pasteboard_Create();
       // 2. Create a pasteboard observer instance.
       OH_PasteboardObserver* observer = OH_PasteboardObserver_Create();
       // 3. Set two callbacks to the pasteboard observer instance.
       OH_PasteboardObserver_SetData(observer, (void*)pasteboard, PasteboardNotifyImpl2, PasteboardFinalizeImpl2);
       // 4. Subscribe to local data changes on the pasteboard.
       OH_Pasteboard_Subscribe(pasteboard, NOTIFY_LOCAL_DATA_CHANGE, observer);
   }
   ```


5. Write data to the pasteboard.

   <!-- @[pasteboard_native5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value NAPI_Pasteboard_set(napi_env env, napi_callback_info info)
   {
       napi_value args[1];
       size_t argc = 1;
       napi_status status = napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
       char text[256];
       size_t value0Size;
       status = napi_get_value_string_utf8(env, args[0], text, sizeof(text), &value0Size);
   
       // 1. Create a pasteboard instance.
       OH_Pasteboard* pasteboard = OH_Pasteboard_Create();
       if (pasteboard == nullptr) {
           OH_LOG_INFO(LOG_APP, "Failed to create pasteboard instance.");
       };
       // 2. Create an OH_UdmfRecord object and add text data to it.
       OH_UdsPlainText* udsPlainText = OH_UdsPlainText_Create();
       OH_UdsPlainText_SetContent(udsPlainText, text);
       OH_UdsHtml* udsHtml = OH_UdsHtml_Create();
       OH_UdsHtml_SetContent(udsHtml, "hello world");
       OH_UdmfRecord* record = OH_UdmfRecord_Create();
       OH_UdmfRecord_AddPlainText(record, udsPlainText);
       OH_UdmfRecord_AddHtml(record, udsHtml);
       // 3. Create an OH_UdmfData object and add OH_UdmfRecord to it.
       OH_UdmfData* data = OH_UdmfData_Create();
       OH_UdmfData_AddRecord(data, record);
       // 4. Write data to the pasteboard.
       OH_Pasteboard_SetData(pasteboard, data);
       // 5. Destroy the pointer when the object is no longer required.
       OH_UdsPlainText_Destroy(udsPlainText);
       OH_UdsHtml_Destroy(udsHtml);
       OH_UdmfRecord_Destroy(record);
       OH_UdmfData_Destroy(data);
       OH_Pasteboard_Destroy(pasteboard);
       // ...
   }
   ```


6. Read data from the pasteboard.

   <!-- @[pasteboard_native6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_NDK_sample/entry/src/main/cpp/napi_init.cpp) -->    
   
   ``` C++
   static napi_value NAPI_Pasteboard_get(napi_env env, napi_callback_info info)
   {
       // 1. Create a pasteboard instance.
       OH_Pasteboard* pasteboard = OH_Pasteboard_Create();
       if (pasteboard == nullptr) {
           OH_LOG_INFO(LOG_APP, "Failed to create pasteboard instance.");
       };
       // 2. Check whether the pasteboard contains text data.
       bool hasPlainTextData = OH_Pasteboard_HasType(pasteboard, "text/plain");
       if (hasPlainTextData) {
           // 3. Obtain the unified data OH_UdmfData from the pasteboard.
           int ret = 0;
           OH_UdmfData* udmfData = OH_Pasteboard_GetData(pasteboard, &ret);
           if (udmfData == nullptr) {
               OH_LOG_INFO(LOG_APP, "Failed to get data from pasteboard.");
           };
           // 4. Obtain the first data record from OH_UdmfData.
           OH_UdmfRecord* record = OH_UdmfData_GetRecord(udmfData, 0);
           if (record == nullptr) {
               OH_LOG_INFO(LOG_APP, "Failed to get record from udmfData.");
           };
           // 5. Obtain the text data from the data record.
           OH_UdsPlainText* plainText = OH_UdsPlainText_Create();
           if (plainText == nullptr) {
               OH_LOG_INFO(LOG_APP, "Failed to create plain text object.");
           };
           OH_UdmfRecord_GetPlainText(record, plainText);
           const char* content = OH_UdsPlainText_GetContent(plainText);
           if (content == nullptr) {
               OH_LOG_INFO(LOG_APP, "Failed to get content from plain text.");
           }
           napi_value result;
           napi_create_string_utf8(env, content, strlen(content), &result);
           // 6. Destroy the pointer when the object is no longer required.
           OH_UdsPlainText_Destroy(plainText);
           OH_UdmfRecord_Destroy(record);
           return result;
       } else {
           OH_LOG_INFO(LOG_APP, "No plain text data in pasteboard.");
       }
       OH_Pasteboard_Destroy(pasteboard);
   }
   ```
