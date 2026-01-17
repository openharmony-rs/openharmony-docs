# ArkUI瀑布流渲染场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

此处提供使用任务池[TaskPool](../reference/apis-arkts/js-apis-taskpool.md)提升[WaterFlow瀑布流](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md)渲染性能的开发指导。UI线程查询数据库数据，并将数据渲染到瀑布流组件，数据过大时会导致UI线程长时间等待，影响用户体验。因此，我们可以将数据查询操作放到子线程中，并通过TaskPool的接口返回数据给UI线程。

本示例说明以下场景：
- 模拟子线程[读取数据库数据](batch-database-operations-guide.md)并返回给UI线程。
- UI线程感知到数据更新，将子线程返回的数据渲染到瀑布流组件。

1. 定义一个接口，用于子线程查询数据库并将数据返回给UI线程。

    <!-- @[query_database_return_main_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/Mock.ets) -->    
    
    ``` TypeScript
    import { taskpool } from '@kit.ArkTS';
    import { fillImg } from './WaterfallRendering';
    
    @Concurrent
    function query() {
      console.info('TaskPoolTest-this is query');
      let result = new Array<string>(33);
      for (let i = 0; i < 33; i++) {
        result[i] = 'Image' + i;
      }
      taskpool.Task.sendData(result);
    }
    
    export function getImgFromDB() {
      //此处模拟查询数据库，并返回数据
      let task = new taskpool.Task(query);
      task.onReceiveData(fillImg);
      taskpool.execute(task);
    }
    ```

2. 封装一个瀑布流组件数据源，用于瀑布流组件加载数据。
   <!-- @[encapsulate_waterfall_data_source](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/WaterFlowDataSource.ets) -->
   
   ``` TypeScript
   // 实现IDataSource接口的对象，用于瀑布流组件加载数据
   export class WaterFlowDataSource implements IDataSource {
     private dataArray: number[] = [];
     private listeners: DataChangeListener[] = [];
   
     constructor() {
       for (let i = 0; i < 100; i++) {
         this.dataArray.push(i);
       }
     }
   
     // 获取索引对应的数据
     public getData(index: number): number {
       return this.dataArray[index];
     }
   
     // 通知控制器数据重新加载
     notifyDataReload(): void {
       this.listeners.forEach(listener => {
         listener.onDataReloaded();
       })
     }
   
     // 通知控制器数据增加
     notifyDataAdd(index: number): void {
       this.listeners.forEach(listener => {
         listener.onDataAdd(index);
       })
     }
   
     // 通知控制器数据变化
     notifyDataChange(index: number): void {
       this.listeners.forEach(listener => {
         listener.onDataChange(index);
       })
     }
   
     // 通知控制器数据删除
     notifyDataDelete(index: number): void {
       this.listeners.forEach(listener => {
         listener.onDataDelete(index);
       })
     }
   
     // 通知控制器数据位置变化
     notifyDataMove(from: number, to: number): void {
       this.listeners.forEach(listener => {
         listener.onDataMove(from, to);
       })
     }
   
     //通知控制器数据批量修改
     notifyDatasetChange(operations: DataOperation[]): void {
       this.listeners.forEach(listener => {
         listener.onDatasetChange(operations);
       })
     }
   
     // 获取数据总数
     public totalCount(): number {
       return this.dataArray.length;
     }
   
     // 注册改变数据的控制器
     registerDataChangeListener(listener: DataChangeListener): void {
       if (this.listeners.indexOf(listener) < 0) {
         this.listeners.push(listener);
       }
     }
   
     // 注销改变数据的控制器
     unregisterDataChangeListener(listener: DataChangeListener): void {
       const pos = this.listeners.indexOf(listener);
       if (pos >= 0) {
         this.listeners.splice(pos, 1);
       }
     }
   
     // 增加数据
     public add1stItem(): void {
       this.dataArray.splice(0, 0, this.dataArray.length);
       this.notifyDataAdd(0);
     }
   
     // 在数据尾部增加一个元素
     public addLastItem(): void {
       this.dataArray.splice(this.dataArray.length, 0, this.dataArray.length);
       this.notifyDataAdd(this.dataArray.length - 1);
     }
   
     // 在指定索引位置增加一个元素
     public addItem(index: number): void {
       this.dataArray.splice(index, 0, this.dataArray.length);
       this.notifyDataAdd(index);
     }
   
     // 删除第一个元素
     public delete1stItem(): void {
       this.dataArray.splice(0, 1);
       this.notifyDataDelete(0);
     }
   
     // 删除第二个元素
     public delete2ndItem(): void {
       this.dataArray.splice(1, 1);
       this.notifyDataDelete(1);
     }
   
     // 删除最后一个元素
     public deleteLastItem(): void {
       this.dataArray.splice(-1, 1);
       this.notifyDataDelete(this.dataArray.length);
     }
   
     // 在指定索引位置删除一个元素
     public deleteItem(index: number): void {
       this.dataArray.splice(index, 1);
       this.notifyDataDelete(index);
     }
   
     // 重新加载数据
     public reload(): void {
       this.dataArray.splice(1, 1);
       this.dataArray.splice(3, 2);
       this.notifyDataReload();
     }
   }
   ```

3. 在应用冷启动阶段，调用`getImgFromDB()`接口，将数据查询操作放到子线程中。在`img`接收到子线程返回的数据后，将数据渲染到瀑布流组件。

   <!-- @[receive_child_thread_data_render_waterfall_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/WaterfallRendering.ets) -->  
