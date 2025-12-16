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
> - 容器类对象跨线程传递时，只能传递数据，自定义方法会丢失。如果需要自定义方法，则需要使用[@Sendable装饰器](arkts-sendable.md#sendable装饰器)标识为Sendable function后，自定义方法可以跨线程传递。

## 使用示例

<!-- @[example_container_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/CommunicationObjects/entry/src/main/ets/managers/ContainerObject.ets) -->

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
    console.info('value:', value);
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
          // 1. 创建Test实例objA
          let treeSet: TreeSet<number> = new TreeSet<number>(sendableCompareFunc);

          treeSet.add(1);
          treeSet.add(5);
          treeSet.add(3);
          treeSet.add(2);
          // 2. 创建任务task，将treeSet传递给该任务，通过序列化传递给子线程
          let task = new taskpool.Task(treeSetTestFunc, treeSet);
          // 3. 执行任务
          taskpool.execute(task).then(() => {
            console.info('taskpool: execute task success!');
          }).catch((e: BusinessError) => {
            console.error(`taskpool: execute task: Code: ${e.code}, message: ${e.message}`);
          })
          this.message = 'success';
        })
    }
    .height('100%')
    .width('100%')
  }
}
```