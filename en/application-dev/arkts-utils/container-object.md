# Container Object
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=7eddfb93bafdeebc2ae5da10b33a5e5b58bf4c6b translatedAt=2026-11-04T09:15:28.307Z pushedAt=2026-11-04T09:36:08.848Z nl=1 -->

Container class objects are passed across threads by copy (serialization). The object contents in the two threads are identical, but they point to isolated memory regions of their respective threads and are allocated in the virtual machine local heap (LocalHeap) of each thread. For the container class objects that support serialization and the initial versions that support them, see [Container Class Object Support Status](#container-class-object-support-status). The members of a container class object must be of serialization-supported types. For the serialization-supported types, see the related objects in [Inter-Thread Communication Object Overview](serializable-overview.md).


> **NOTE**
> 
> - When a container class object is passed across threads, only data can be passed, and custom methods are lost. If custom methods are required, use the [@Sendable decorator](arkts-sendable.md#sendable-decorator) to mark them as Sendable functions, after which the custom methods can be passed across threads.

## Container Class Object Support Status

The following applies only to container class objects. For the support status of ordinary objects (Array, Map, Set, etc.), see [Ordinary Objects](normal-object.md).

| Container Class Name | Supported Version |
| --------- | -------- |
| [TreeSet](../reference/apis-arkts/js-apis-treeset.md) | Supported on devices running <!--RP1-->OpenHarmony 6.1<!--RP1End--> or later |
| [ArrayList](../reference/apis-arkts/js-apis-arraylist.md) | Not supported yet |
| [List](../reference/apis-arkts/js-apis-list.md) | Not supported yet |
| [LinkedList](../reference/apis-arkts/js-apis-linkedlist.md) | Not supported yet |
| [Deque](../reference/apis-arkts/js-apis-deque.md) | Not supported yet |
| [Queue](../reference/apis-arkts/js-apis-queue.md) | Not supported yet |
| [Stack](../reference/apis-arkts/js-apis-stack.md) | Not supported yet |
| [Vector](../reference/apis-arkts/js-apis-vector.md) | Not supported yet |
| [HashMap](../reference/apis-arkts/js-apis-hashmap.md) | Not supported yet |
| [HashSet](../reference/apis-arkts/js-apis-hashset.md) | Not supported yet |
| [TreeMap](../reference/apis-arkts/js-apis-treemap.md) | Not supported yet |
| [LightWeightMap](../reference/apis-arkts/js-apis-lightweightmap.md) | Not supported yet |
| [LightWeightSet](../reference/apis-arkts/js-apis-lightweightset.md) | Not supported yet |
| [PlainArray](../reference/apis-arkts/js-apis-plainarray.md) | Not supported yet |


## Example

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
          // 1. Create a TreeSet instance.
          let treeSet: TreeSet<number> = new TreeSet<number>(sendableCompareFunc);
          treeSet.add(1);
          treeSet.add(5);
          treeSet.add(3);
          treeSet.add(2);
          // 2. Create a task and transfer treeSet to the task. The task is transferred to the child thread through serialization.
          let task = new taskpool.Task(treeSetTestFunc, treeSet);
          // 3. Execute the task.
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