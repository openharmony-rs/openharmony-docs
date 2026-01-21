# Subscribing to Common Events in C

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

## When to Use

A subscriber created using [OH_CommonEvent_CreateSubscriber](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createsubscriber) can subscribe to a common event. If a subscribed event is published, the subscriber will receive the event and its parameters. Also, the subscriber object can be used to further process ordered common events.

## Available APIs

For details about the APIs, see [oh_commonevent.h](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md).

| API                              | Description                                                            |
| ------------------------------------ | ---------------------------------------------------------------- |
|[CommonEvent_SubscribeInfo* OH_CommonEvent_CreateSubscribeInfo(const char* events[], int32_t eventsNum)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createsubscribeinfo)|Creates subscriber information.|
|[void OH_CommonEvent_DestroySubscribeInfo(CommonEvent_SubscribeInfo* info)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroysubscribeinfo)|Destroys subscriber information.|
|[CommonEvent_Subscriber* OH_CommonEvent_CreateSubscriber(const CommonEvent_SubscribeInfo* info, CommonEvent_ReceiveCallback callback)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createsubscriber)| Creates a subscriber.|
|[void OH_CommonEvent_DestroySubscriber(CommonEvent_Subscriber* subscriber)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroysubscriber)|Destroys a subscriber.|
|[CommonEvent_ErrCode OH_CommonEvent_Subscribe(const CommonEvent_Subscriber* subscriber)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_subscribe)|Subscribes to an event.|
|[bool OH_CommonEvent_AbortCommonEvent(CommonEvent_Subscriber* subscriber)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_abortcommonevent)|Sets whether to abort an ordered common event.|
|[bool OH_CommonEvent_ClearAbortCommonEvent(CommonEvent_Subscriber* subscriber)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_clearabortcommonevent)|Sets whether to clear the abort state of an ordered common event.|
|[bool OH_CommonEvent_FinishCommonEvent(CommonEvent_Subscriber* subscriber)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_finishcommonevent)|Sets whether to finish processing an ordered common event.|

## How to Develop

1. Include header files.

   <!-- @[event_subscriber_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.h) -->
   
   ``` C
   #include <cstdint>
   #include <cstdio>
   #include <cwchar>
   #include <cstring>
   #include "hilog/log.h"
   #include "BasicServicesKit/oh_commonevent.h"
   ```


2. Add dynamic link libraries to the CMake script.

   ```txt
   target_link_libraries(entry PUBLIC
       libace_napi.z.so
       libhilog_ndk.z.so
       libohcommonevent.so
   )
   ```

3. Create subscriber information.

   Use [OH_CommonEvent_CreateSubscribeInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createsubscribeinfo) to create subscriber information.

   <!-- @[event_subscriber_create_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
   
   ``` C++
   CommonEvent_SubscribeInfo *CreateSubscribeInfo(const char *events[], int32_t eventsNum, const char *permission,
                                                  const char *bundleName)
   {
       int32_t ret = -1;
       // Create subscriber information.
       CommonEvent_SubscribeInfo *info = OH_CommonEvent_CreateSubscribeInfo(events, eventsNum);
   
       // Set the publisher permission.
       ret = OH_CommonEvent_SetPublisherPermission(info, permission);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetPublisherPermission ret <%{public}d>.", ret);
   
       // Set the publisher bundle name.
       ret = OH_CommonEvent_SetPublisherBundleName(info, bundleName);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_SetPublisherBundleName ret <%{public}d>.", ret);
       return info;
   }
   
   // Destroy the subscriber information.
   void DestroySubscribeInfo(CommonEvent_SubscribeInfo *info)
   {
       OH_CommonEvent_DestroySubscribeInfo(info);
       info = nullptr;
   }
   ```


4. Create a subscriber.

   When creating a subscriber, pass in [CommonEvent_ReceiveCallback](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#commonevent_receivecallback). When the event is published, the subscriber receives [CommonEvent_RcvData](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#structs).

   <!-- @[event_subscriber_on_receive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
   
   ``` C++
   // Common event callback.
   void OnReceive(const CommonEvent_RcvData *data)
   {
       // Obtain the name of a common event.
       const char *event = OH_CommonEvent_GetEventFromRcvData(data);
   
       // Obtain the result code of a common event.
       int code = OH_CommonEvent_GetCodeFromRcvData(data);
   
       // Obtain the custom result data of a common event.
       const char *retData = OH_CommonEvent_GetDataStrFromRcvData(data);
   
       // Obtain the bundle name of a common event.
       const char *bundle = OH_CommonEvent_GetBundleNameFromRcvData(data);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST",
                    "event: %{public}s, code: %{public}d, data: %{public}s, bundle: %{public}s", event, code, retData,
                    bundle);
   }
   ```


   Use [CommonEvent_Parameters](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#variables) to pass in a key to obtain the additional information.

   <!-- @[event_subscriber_get_parameters](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
   
   ``` C++
   void GetParameters(const CommonEvent_RcvData *data)
   {
       // Obtain the additional information of a common event.
       bool exists = false;
       const CommonEvent_Parameters *parameters = OH_CommonEvent_GetParametersFromRcvData(data);
   
       // Check whether the additional information of a common event contains a KV pair.
       exists = OH_CommonEvent_HasKeyInParameters(parameters, "intKey");
       // Obtain the int data from the additional information of a common event.
       int intValue = OH_CommonEvent_GetIntFromParameters(parameters, "intKey", 10);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "exists = %{public}d, intValue = %{public}d", exists, intValue);
   
       // Note: In addition to int, the following data types of additional information of a common event can be obtained by calling the corresponding HarmonyOS APIs:
       // - Basic types: Boolean (OH_CommonEvent_GetBoolFromParameters), long (OH_CommonEvent_GetLongFromParameters),
       // double (OH_CommonEvent_GetDoubleFromParameters), and char (OH_CommonEvent_GetCharFromParameters)
       // -
       // Array types: int array (OH_CommonEvent_GetIntArrayFromParameters), long array (OH_CommonEvent_GetLongArrayFromParameters),
       // double array (OH_CommonEvent_GetDoubleArrayFromParameters), char array (OH_CommonEvent_GetCharArrayFromParameters),
       // and Boolean array (OH_CommonEvent_GetBoolArrayFromParameters)
       // Check whether the key exists using OH_CommonEvent_HasKeyInParameters for all types to avoid operation failures.
   }
   ```


   Create a subscriber through [OH_CommonEvent_CreateSubscriber](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createsubscriber), and pass in [CommonEvent_SubscribeInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#structs) and the **OnReceive** callback function defined in step 4.

   <!-- @[event_subscriber_create_and_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
   
   ``` C++
   // Create a subscriber.
   CommonEvent_Subscriber *CreateSubscriber(CommonEvent_SubscribeInfo *info)
   {
       return OH_CommonEvent_CreateSubscriber(info, OnReceive);
   }
   
   // Destroy a subscriber.
   void DestroySubscriber(CommonEvent_Subscriber *Subscriber)
   {
       OH_CommonEvent_DestroySubscriber(Subscriber);
       Subscriber = nullptr;
   }
   ```


5. Subscribe to an event.

   Use [OH_CommonEvent_Subscribe](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_subscribe) to subscribe to an event.

   <!-- @[event_subscriber_subscriber](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
   
   ``` C++
   void Subscribe(CommonEvent_Subscriber *subscriber)
   {
       // Subscribe to an event by passing a subscriber.
       int32_t ret = OH_CommonEvent_Subscribe(subscriber);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_Subscribe ret <%{public}d>.", ret);
   }
   ```


6. (Optional) Further process the subscribed event if this event is an ordered common event.

   Based on the priority set by the subscriber, the common event is preferentially sent to the subscriber with a higher priority. After the subscriber successfully receives the event, the public event is sent to the subscriber with a lower priority. Subscribers with the same priority receive common events in a random order.

   > **NOTE**
   >
   > After receiving a common event, the subscriber can further process the ordered common event through the following API.

   - Abort an ordered common event.

     Use [OH_CommonEvent_AbortCommonEvent](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_abortcommonevent) and [OH_CommonEvent_FinishCommonEvent](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_finishcommonevent) together to abort an ordered common event so that this event is not published to the next subscriber.

     <!-- @[event_subscriber_abort_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
     
     ``` C++
     void AbortCommonEvent(CommonEvent_Subscriber *subscriber)
     {
         // Check whether the event is an ordered common event.
         if (!OH_CommonEvent_IsOrderedCommonEvent(subscriber)) {
             OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "Not ordered common event.");
             return;
         }
         // Abort an ordered common event.
         if (OH_CommonEvent_AbortCommonEvent(subscriber)) {
             if (OH_CommonEvent_FinishCommonEvent(subscriber)) {
                 // Obtain the result of the abort state of an ordered common event.
                 OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "Abort common event success, Get abort <%{public}d>.",
                              OH_CommonEvent_GetAbortCommonEvent(subscriber));
             }
         } else {
             OH_LOG_Print(LOG_APP, LOG_ERROR, 1, "CES_TEST", "Abort common event failed.");
         }
     }
     ```


   - Clear the abort state of an ordered common event.

     Use [OH_CommonEvent_ClearAbortCommonEvent](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_clearabortcommonevent) and [OH_CommonEvent_FinishCommonEvent](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_finishcommonevent) together to clear the abort state of an ordered common event so that this event can be published to the next subscriber.

     <!-- @[event_subscriber_clear](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
     
     ``` C++
     void ClearAbortCommonEvent(CommonEvent_Subscriber *subscriber)
     {
         // Check whether the event is an ordered common event.
         if (!OH_CommonEvent_IsOrderedCommonEvent(subscriber)) {
             OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "Not ordered common event.");
             return;
         }
         // Abort an ordered common event.
         if (!OH_CommonEvent_AbortCommonEvent(subscriber)) {
             OH_LOG_Print(LOG_APP, LOG_ERROR, 1, "CES_TEST", "Abort common event failed.");
             return;
         }
         // Clear the abort state of an ordered event.
         if (OH_CommonEvent_ClearAbortCommonEvent(subscriber)) {
             if (OH_CommonEvent_FinishCommonEvent(subscriber)) {
                 // Obtain the result of the abort state of an ordered common event.
                 OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "Clear abort common event success, Get abort <%{public}d>.",
                              OH_CommonEvent_GetAbortCommonEvent(subscriber));
             }
         } else {
             OH_LOG_Print(LOG_APP, LOG_ERROR, 1, "CES_TEST", "Clear abort common event failed.");
         }
     }
     ```
    

   - Modify the content of an ordered common event.

     Use [OH_CommonEvent_SetCodeToSubscriber](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_setcodetosubscriber) and [OH_CommonEvent_SetDataToSubscriber](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_setdatatosubscriber) to set the code and data of an ordered common event.

     <!-- @[event_subscriber_set_get](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_subscribe.cpp) -->
     
     ``` C++
     void SetToSubscriber(CommonEvent_Subscriber *subscriber, const int32_t code, const char *data)
     {
         // Set the result code for an ordered common event.
         if (!OH_CommonEvent_SetCodeToSubscriber(subscriber, code)) {
             OH_LOG_Print(LOG_APP, LOG_ERROR, 1, "CES_TEST", "OH_CommonEvent_SetCodeToSubscriber failed.");
             return;
         }
         // Set the result data for an ordered common event.
         size_t dataLength = strlen(data);
         if (!OH_CommonEvent_SetDataToSubscriber(subscriber, data, dataLength)) {
             OH_LOG_Print(LOG_APP, LOG_ERROR, 1, "CES_TEST", "OH_CommonEvent_SetDataToSubscriber failed.");
             return;
         }
     }
     
     void GetFromSubscriber(CommonEvent_Subscriber *subscriber)
     {
         // Obtain the result data and code of an ordered common event.
         const char *data = OH_CommonEvent_GetDataFromSubscriber(subscriber);
         int32_t code = OH_CommonEvent_GetCodeFromSubscriber(subscriber);
         OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "Subscriber data <%{public}s>, code <%{public}d>.", data, code);
     }
     ```
