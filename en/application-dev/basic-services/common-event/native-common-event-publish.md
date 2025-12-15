# Publishing Common Events in C

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

## When to Use

You can use the [OH_CommonEvent_Publish](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publish) and [OH_CommonEvent_PublishWithInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publishwithinfo) methods to publish a common event, which can carry data for subscribers to parse and process.

## Available APIs

For details about the APIs, see [oh_commonevent.h](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md).

| API                              | Description                                                            |
| ------------------------------------ | ---------------------------------------------------------------- |
|[struct CommonEvent_PublishInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-commonevent-publishinfo.md)|Defines the property object used for publishing a common event.|
|[CommonEvent_ErrCode OH_CommonEvent_Publish(const char* event)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publish)|Publishes a common event.|
|[CommonEvent_ErrCode OH_CommonEvent_PublishWithInfo(const char* event, const CommonEvent_PublishInfo* info)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publishwithinfo)| Publishes a common event with specified properties.|
|[CommonEvent_PublishInfo* OH_CommonEvent_CreatePublishInfo(bool ordered)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createpublishinfo)|Creates an attribute object of a common event.|
|[void OH_CommonEvent_DestroyPublishInfo(CommonEvent_PublishInfo* info)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroypublishinfo)|Destroys an attribute object of a common event.|
|[CommonEvent_Parameters* OH_CommonEvent_CreateParameters()](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createparameters)|Creates an additional information object of a common event.|
|[void OH_CommonEvent_DestroyParameters(CommonEvent_Parameters* param)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroyparameters)|Destroys an additional information object of a common event.|

## How to Develop

1. Include header files.

   <!-- @[event_publisher_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.h) -->
   
   ``` C
   #include <cstdint>
   #include <cstdio>
   #include <cwchar>
   #include <cstring>
   #include "hilog/log.h"
   #include "BasicServicesKit/oh_commonevent.h"
   
   const long PARAM_LONG_VALUE1 = 2147483646;
   const long PARAM_LONG_VALUE2 = 2147483645;
   const long PARAM_LONG_VALUE3 = 555;
   const double PARAM_DOUBLE_VALUE1 = 11.22;
   const double PARAM_DOUBLE_VALUE2 = 33.44;
   const double PARAM_DOUBLE_VALUE3 = 55.66;
   const int PARAM_INT_VALUE1 = 10;
   const int PARAM_INT_VALUE2 = 123;
   const int PARAM_INT_VALUE3 = 234;
   const int PARAM_INT_VALUE4 = 567;
   ```

2. Add dynamic link libraries to the CMake script.

   ```txt
   target_link_libraries(entry PUBLIC
       libace_napi.z.so
       libhilog_ndk.z.so
       libohcommonevent.so
   )
   ```

3. (Optional) Create an attribute object of a common event.

   When publishing a common event that carries data, you need to create a property object of the common event using [OH_CommonEvent_CreatePublishInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createpublishinfo) and set the properties using the following APIs:

   <!-- @[event_publisher_create_set](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->
   
   ``` C++
   // Create and add additional information of common event attributes.
   CommonEvent_Parameters *CreateParameters()
   {
       int32_t ret = -1;
       // Create the additional information of a common event.
       CommonEvent_Parameters *param = OH_CommonEvent_CreateParameters();
   
       // Set the additional information and key of the int type.
       ret = OH_CommonEvent_SetIntToParameters(param, "intKey", PARAM_INT_VALUE1);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetIntToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the int array type.
       int intArray[] = {PARAM_INT_VALUE2, PARAM_INT_VALUE3, PARAM_INT_VALUE4};
       size_t arraySize = sizeof(intArray) / sizeof(intArray[0]);
       ret = OH_CommonEvent_SetIntArrayToParameters(param, "intArrayKey", intArray, arraySize);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetIntArrayToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the long type.
       ret = OH_CommonEvent_SetLongToParameters(param, "longKey", PARAM_LONG_VALUE1);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetLongToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the long array type.
       long longArray[] = {PARAM_LONG_VALUE1, PARAM_LONG_VALUE3, PARAM_LONG_VALUE2};
       ret = OH_CommonEvent_SetLongArrayToParameters(param, "longArrayKey", longArray, arraySize);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetLongArrayToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the double type.
       ret = OH_CommonEvent_SetDoubleToParameters(param, "doubleKey", PARAM_DOUBLE_VALUE1);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetDoubleToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the double array type.
       double doubleArray[] = {PARAM_DOUBLE_VALUE1, PARAM_DOUBLE_VALUE2, PARAM_DOUBLE_VALUE3};
       ret = OH_CommonEvent_SetDoubleArrayToParameters(param, "doubleArrayKey", doubleArray, arraySize);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetDoubleArrayToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the Boolean type.
       ret = OH_CommonEvent_SetBoolToParameters(param, "boolKey", true);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetBoolToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the Boolean array type.
       bool boolArray[] = {true, false, true};
       ret = OH_CommonEvent_SetBoolArrayToParameters(param, "boolArrayKey", boolArray, arraySize);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetBoolArrayToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the char type.
       ret = OH_CommonEvent_SetCharToParameters(param, "charKey", 'A');
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetCharToParameters ret <%{public}d>.", ret);
   
       // Set the additional information and key of the char array type.
       const char *value = "Char Array";
       size_t valueLength = strlen(value);
       ret = OH_CommonEvent_SetCharArrayToParameters(param, "charArrayKey", value, valueLength);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetCharArrayToParameters ret <%{public}d>.", ret);
       return param;
   }
   
   // Set common event attributes.
   void SetPublishInfo(const char *bundleName, const char *permissions[], int32_t num, const int32_t code,
                       const char *data)
   {
       int32_t ret = -1;
       // Create publishInfo. Setting the value to true indicates an ordered common event; false indicates an unordered common event.
       CommonEvent_PublishInfo *info = OH_CommonEvent_CreatePublishInfo(true);
   
       // Set the bundle name of a common event.
       ret = OH_CommonEvent_SetPublishInfoBundleName(info, bundleName);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetPublishInfoBundleName ret <%{public}d>.", ret);
   
       // Set the common event permission. The parameters consist of the permission array and the number of permissions.
       ret = OH_CommonEvent_SetPublishInfoPermissions(info, permissions, num);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetPublishInfoPermissions ret <%{public}d>.", ret);
   
       // Set the result code of a common event.
       ret = OH_CommonEvent_SetPublishInfoCode(info, code);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetPublishInfoCode ret <%{public}d>.", ret);
   
       // Set the result data of a common event.
       size_t dataLength = strlen(data);
       ret = OH_CommonEvent_SetPublishInfoData(info, data, dataLength);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetPublishInfoData ret <%{public}d>.", ret);
   
       // Set the additional information of a common event.
       CommonEvent_Parameters *param = CreateParameters();
       ret = OH_CommonEvent_SetPublishInfoParameters(info, param);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetPublishInfoParameters ret <%{public}d>.", ret);
   }
   ```

4. Publish a common event.

   - Use [OH_CommonEvent_Publish](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publish) to publish common events that do not carry information.

     > **NOTE**
     >
     > Common events that do not carry information can be published only as unordered common events.

     <!-- @[event_publisher_publish](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->
     
     ``` C++
     void Publish(const char *event)
     {
         int32_t ret = OH_CommonEvent_Publish(event);
         OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_Publish ret <%{public}d>.", ret);
     }
     ```

   - Use [OH_CommonEvent_PublishWithInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publishwithinfo) to publish common events that carry information.

     <!-- @[event_publisher_publish_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->
     
     ``` C++
     void PublishWithInfo(const char *event, CommonEvent_PublishInfo *info)
     {
         // Create a common event with the attribute object.
         int32_t ret = OH_CommonEvent_PublishWithInfo(event, info);
         OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_PublishWithInfo ret <%{public}d>.", ret);
     }
     ```
    

5. Destroy a common event object.

   If the created common event object is no longer used to publish a common event, destroy the **CommonEvent_Parameters** object by using [OH_CommonEvent_DestroyParameters](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroyparameters), and then destroy the common event object by using [OH_CommonEvent_DestroyPublishInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroypublishinfo).
   
   <!-- @[event_publisher_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->
   
   ``` C++
   void DestroyPublishInfo(CommonEvent_Parameters *param, CommonEvent_PublishInfo *info)
   {
       // First, destroy Parameters.
       OH_CommonEvent_DestroyParameters(param);
       param = nullptr;
       // Second, destroy PublishInfo.
       OH_CommonEvent_DestroyPublishInfo(info);
       info = nullptr;
   }
   ```
