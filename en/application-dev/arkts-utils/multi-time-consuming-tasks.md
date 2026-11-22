---
kits: ["ArkTS / Ark Programming Language"]
description: "Describes how to use TaskPool to execute multiple time-consuming tasks: execute tasks concurrently through TaskGroup and wait for all results, or split a large data list into multiple subtasks for parallel processing and then merge the results. A multi-image loading example demonstrates the complete implementation."
keywords: [multi-task concurrency, TaskGroup, task grouping, large data splitting, result merging, TaskPool, batch image loading]
doctype: guide
status: active
---

# Using TaskPool for Multiple Time-consuming Tasks
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:39:19.560Z pushedAt=2026-11-09T09:08:52.317Z nl=1 -->

When multiple tasks are executed simultaneously, the execution time and the time to return data may vary due to differences in task complexity. If the host thread requires data from all tasks once they are completed, this can be achieved using [TaskGroup](../reference/apis-arkts/js-apis-taskpool.md#taskgroup10).

Additionally, if the volume of data to be processed is large (for example, a list with 10,000 items), processing all the data in a single task can be time-consuming. Instead, you can split the original data into multiple sublists and assign each sublist to an independent task. After all tasks are completed, you can combine the results into a complete dataset. This approach can reduce processing time and enhance user experience.

This example uses image loading of multiple tasks to illustrate the process.

1. Implement the task to be executed in a child thread.

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IconItemSource.ets) -->
   
   ``` TypeScript
   export class IconItemSource {
     image: string | Resource = '';
     text: string | Resource = '';
   
     constructor(image: string | Resource = '', text: string | Resource = '') {
       this.image = image;
       this.text = text;
     }
   }
   ```

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IndependentTask.ets) -->
   
   ``` TypeScript
   import { IconItemSource } from './IconItemSource';
   
   // The method executed in a Task must be annotated with @Concurrent; otherwise, it cannot be called properly.
   @Concurrent
   export function loadPicture(count: number): IconItemSource[] {
     let iconItemSourceList: IconItemSource[] = [];
     // Traverse and add 6*count IconItem data entries.
     for (let index = 0; index < count; index++) {
       const numStart: number = index * 6;
       // Loop through 6 image resources here.
       iconItemSourceList.push(new IconItemSource('$media:startIcon', `item${numStart + 1}`));
       iconItemSourceList.push(new IconItemSource('$media:background', `item${numStart + 2}`));
       iconItemSourceList.push(new IconItemSource('$media:foreground', `item${numStart + 3}`));
       iconItemSourceList.push(new IconItemSource('$media:startIcon', `item${numStart + 4}`));
       iconItemSourceList.push(new IconItemSource('$media:background', `item${numStart + 5}`));
       iconItemSourceList.push(new IconItemSource('$media:foreground', `item${numStart + 6}`));
     }
     return iconItemSourceList;
   }
   ```

2. Add the tasks to a task group and execute them collectively. When all the tasks in the task group finish executing, their results are placed in an array and sent back to the host thread. In this way, the host thread can access the combined results of all tasks at once, rather than receiving results individually as each task completes.

   <!-- @[execute_task_group](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/MultiTask.ets) -->
   
   ``` TypeScript
   import { taskpool } from '@kit.ArkTS';
   import { IconItemSource } from './IconItemSource';
   import { loadPicture } from './IndependentTask';
   
   let iconItemSourceList: IconItemSource[] = [];
   
   let taskGroup: taskpool.TaskGroup = new taskpool.TaskGroup();
   taskGroup.addTask(new taskpool.Task(loadPicture, 30));
   taskGroup.addTask(new taskpool.Task(loadPicture, 20));
   taskGroup.addTask(new taskpool.Task(loadPicture, 10));
   taskpool.execute(taskGroup).then((ret: object) => {
     let retA = ret as IconItemSource[][];
     let tmpLength = (retA).length
     for (let i = 0; i < tmpLength; i++) {
       for (let j = 0; j < retA[i].length; j++) {
         if (retA[i][j]) {
           iconItemSourceList.push(retA[i][j]);
         }
       }
     }
     // The length of iconItemSourceList is 360
     console.info('The length of iconItemSourceList is ' + (iconItemSourceList?.length ?? 0));
   })
   ```
