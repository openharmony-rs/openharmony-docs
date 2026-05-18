# Sendable使用场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->
Sendable对象在不同并发实例间默认采用引用传递，这种方式比序列化更高效，且不会丢失类成员方法。因此，Sendable能够解决两个关键场景的问题：

- 跨并发实例传输大数据（例如达到100KB以上的数据）。

- 跨并发实例传递带方法的class实例对象。

## 跨并发实例传输大数据场景

由于跨并发实例序列化的开销随数据量线性增长，因此当传输数据量较大时（100KB的数据传输耗时约为1ms），跨并发实例的拷贝开销会影响应用性能。使用引用传递方式传输对象可提升性能。

**示例：**
<!-- @[across_concurrent_instance_transfer_large_data ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/SendableObject/SendableScenarios/bigdata/src/main/ets/pages/Index.ets) --> 


<!-- @[across_concurrent_instance_transfer_large_data ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/SendableObject/SendableScenarios/bigdata/src/main/ets/pages/sendable.ets) --> 



## 跨并发实例传递带方法的class实例对象

在序列化传输实例对象时，会丢失方法。因此，若需调用实例方法，应使用引用传递。处理数据时，若需解析数据，可使用[ASON工具](ason-parsing-generation.md)。

**示例：**
<!-- @[across_concurrent_instance_pass_class_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/SendableObject/SendableScenarios/crossconcurrency/src/main/ets/pages/Index.ets) --> 

<!-- @[across_concurrent_instance_pass_class_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/SendableObject/SendableScenarios/crossconcurrency/src/main/ets/pages/sendable.ets) --> 
