# 发布公共事件（C/C++）

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

## 场景介绍

当需要发布某个公共事件时，可以通过[OH_CommonEvent_Publish](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publish)和[OH_CommonEvent_PublishWithInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publishwithinfo)方法发布事件。发布的公共事件可以携带数据，供订阅者解析并进行下一步处理。

## 接口说明

详细的API说明请参考[CommonEvent API参考](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md)。

| 接口名                               | 描述                                                             |
| ------------------------------------ | ---------------------------------------------------------------- |
|[struct CommonEvent_PublishInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-commonevent-publishinfo.md)|发布公共事件时使用的公共事件属性对象。|
|[CommonEvent_ErrCode OH_CommonEvent_Publish(const char* event)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publish)|发布公共事件。|
|[CommonEvent_ErrCode OH_CommonEvent_PublishWithInfo(const char* event, const CommonEvent_PublishInfo* info)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publishwithinfo)| 发布带有指定属性的公共事件。 |
|[CommonEvent_PublishInfo* OH_CommonEvent_CreatePublishInfo(bool ordered)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createpublishinfo)|创建公共事件属性对象。|
|[void OH_CommonEvent_DestroyPublishInfo(CommonEvent_PublishInfo* info)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroypublishinfo)|销毁公共事件属性对象。|
|[CommonEvent_Parameters* OH_CommonEvent_CreateParameters()](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createparameters)|创建公共事件附加信息对象。|
|[void OH_CommonEvent_DestroyParameters(CommonEvent_Parameters* param)](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroyparameters)|销毁公共事件附加信息对象。|

## 开发步骤

1. 引用头文件。

   <!-- @[event_publisher_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.h) -->

2. 在CMake脚本中添加动态链接库。

   ```txt
   target_link_libraries(entry PUBLIC
       libace_napi.z.so
       libhilog_ndk.z.so
       libohcommonevent.so
   )
   ```

3. （可选）创建公共事件属性对象。

   发布携带数据的公共事件时，需要通过[OH_CommonEvent_CreatePublishInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_createpublishinfo)创建公共事件属性对象，并通过以下接口设置公共事件属性。

   <!-- @[event_publisher_create_set](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->

4. 发布公共事件。

   - 通过[OH_CommonEvent_Publish](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publish)发布不携带信息的公共事件。

     > **说明：**
     >
     > 不携带信息的公共事件，只能发布为无序公共事件。

     <!-- @[event_publisher_publish](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->

   - 通过[OH_CommonEvent_PublishWithInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_publishwithinfo)发布携带信息的公共事件。

     <!-- @[event_publisher_publish_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->
    

5. 销毁公共事件对象。

   如果后续无需使用已创建的公共事件对象来发布公共事件，需要先通过[OH_CommonEvent_DestroyParameters](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroyparameters)销毁`CommonEvent_Parameters`对象，然后再通过[OH_CommonEvent_DestroyPublishInfo](../../reference/apis-basic-services-kit/capi-oh-commonevent-h.md#oh_commonevent_destroypublishinfo)销毁公共事件对象。
   
   <!-- @[event_publisher_destroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/NativeCommonEvent/entry/src/main/cpp/common_event_publish.cpp) -->
