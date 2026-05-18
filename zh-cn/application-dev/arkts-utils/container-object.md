# 容器类对象
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

容器类对象在跨线程传递时，可通过序列化的机制，确保跨线程间的数据一致，从而实现跨线程数据传递。

目前支持序列化的容器类对象包括[TreeSet](../reference/apis-arkts/js-apis-treeset.md)，容器类对象中的成员必须是序列化支持的类型，目前序列化支持类型可以参考[线程间通信对象概述](serializable-overview.md)中的相关对象。

> **说明：**
>
> - 从<!--RP1-->OpenHarmony 6.1<!--RP1End-->开始，支持使用TreeSet容器类对象实现跨线程数据传递。
> 
> - 容器类对象跨线程传递时，只能传递数据，自定义方法会丢失。如果需要自定义方法，则需要使用[@Sendable装饰器](arkts-sendable.md#sendable装饰器)标识为Sendable function后，自定义方法可以跨线程传递。

## 使用示例

<!-- @[example_container_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/CommunicationObjects/entry/src/main/ets/managers/ContainerObject.ets) --> 