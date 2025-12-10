# 容器类对象
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

容器类对象在跨线程传递时，可通过序列化的形式，确保两个线程的内容一致，从而实现跨线程数据传递。
目前支持序列化的容器类对象包括[TreeSet](../reference/apis-arkts/js-apis-treeset.md)。

> **说明：**
>
> - 从API version 22开始，支持使用TreeSet容器类对象实现跨线程数据传递。
> 
> - 容器类对象跨线程传递时，只能传递数据，类方法会丢失。使用[@Sendable装饰器](arkts-sendable.md#sendable装饰器)标识为Sendable类后，类实例对象跨线程传递后，可携带类方法。

## 使用示例

<!-- @[example_container_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/CommunicationObjects/entry/src/main/ets/managers/ContainerObject.ets) -->