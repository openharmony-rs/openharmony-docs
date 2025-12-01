# Unsubscribing from Common Events in C

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

## When to Use

After completing service requirements, subscribers need to unsubscribe from common events.

## Available APIs

For details about the APIs, see [oh_commonevent.h](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md).

| API                              | Description                                                            |
| ------------------------------------ | ---------------------------------------------------------------- |
|[CommonEvent_ErrCode OH_CommonEvent_UnSubscribe(const CommonEvent_Subscriber* subscriber)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_unsubscribe)|Unsubscribes from a common event.|

## How to Develop

1. Include header files.

   <!-- @[event_unsubscriber_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_unsubscribe.h) -->
   
   ``` C
   #include <cstdint>
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


3. Unsubscribe from a common event.

   After a subscriber subscribes to a common event and meets service requirements, the subscriber can use [OH_CommonEvent_UnSubscribe](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_unsubscribe) to unsubscribe from the event.

   <!-- @[event_unsubscriber](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_unsubscribe.cpp) -->
   
   ``` C++
   void Unsubscribe(CommonEvent_Subscriber *subscriber)
   {
       // Unsubscribe from a common event by passing a subscriber.
       int32_t ret = OH_CommonEvent_UnSubscribe(subscriber);
       OH_LOG_Print(LOG_APP, LOG_INFO, 1, "CES_TEST", "OH_CommonEvent_UnSubscribe ret <%{public}d>.", ret);
   }
   ```
