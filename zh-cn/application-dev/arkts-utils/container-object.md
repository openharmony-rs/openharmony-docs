# 容器类对象
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

容器类对象跨线程时通过拷贝（序列化）形式传递，两个线程的对象内容一致，但指向各自线程的隔离内存区间，被分配在各自线程的虚拟机本地堆（LocalHeap）。支持序列化的容器类对象和支持的初始版本可以参考容器类对象支持情况。容器类对象中的成员必须是序列化支持的类型，序列化支持类型可以参考线程间通信对象概述中的相关对象。


> **说明：**
> 
> - 容器类对象跨线程传递时，只能传递数据，自定义方法会丢失。如果需要自定义方法，则需要使用@Sendable装饰器标识为Sendable function后，自定义方法可以跨线程传递。

## 容器类对象支持情况

以下仅针对容器类对象，普通对象（Array、Map、Set等）的支持情况请参考普通对象。

| 容器类名称 | 支持版本 |
| --------- | -------- |
| TreeSet | 搭载<!--RP1-->OpenHarmony 6.1<!--RP1End-->及以上版本的设备支持 |
| ArrayList | 搭载OpenHarmony 7.0.0及以上版本的设备支持 |
| HashMap | 搭载OpenHarmony 7.0.0及以上版本的设备支持 |
| HashSet | 搭载OpenHarmony 7.0.0及以上版本的设备支持 |
| List | 搭载OpenHarmony 7.0.0及以上版本的设备支持 |
| LinkedList | 搭载OpenHarmony 7.0.0及以上版本的设备支持 |
| Deque | 暂不支持 |
| Queue | 暂不支持 |
| Stack | 暂不支持 |
| Vector | 暂不支持 |
| TreeMap | 暂不支持 |
| LightWeightMap | 暂不支持 |
| LightWeightSet | 暂不支持 |
| PlainArray | 暂不支持 |


## 使用示例

<!-- @[example_container_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/CommunicationObjects/entry/src/main/ets/managers/ContainerObject.ets) --> 

``` TypeScript
import { taskpool, TreeSet } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

@Sendable
function sendableCompareFunc(firstValue: number, secondValue: number): boolean {
    return firstValue > secondValue;
}

@Concurrent
function treeSetTestFunc(treeSet: TreeSet<number>) {
  for (let value of treeSet) {
    console.info(`value: ${value}`);
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          // 1. 创建TreeSet实例
          let treeSet: TreeSet<number> = new TreeSet<number>(sendableCompareFunc);
          treeSet.add(1);
          treeSet.add(5);
          treeSet.add(3);
          treeSet.add(2);
          // 2. 创建任务task，将treeSet传递给该任务，通过序列化传递给子线程
          let task = new taskpool.Task(treeSetTestFunc, treeSet);
          // 3. 执行任务
          taskpool.execute(task).then(() => {
            this.message = 'success';
            console.info('taskpool: execute task success!');
          }).catch((e: BusinessError) => {
            this.message = 'failed';
            console.error(`taskpool: execute task: Code: ${e.code}, message: ${e.message}`);
          })
        })
    }
    .height('100%')
    .width('100%')
  }
}
```