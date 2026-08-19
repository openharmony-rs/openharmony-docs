# TaskResult

对处于等待或执行过程中的任务执行取消操作后，在catch分支里捕获到BusinessError里的补充信息。其他场景下该信息为undefined。 > **说明：** > > 任务被取消后，有如下两种情况： > - 如果当前任务处于等待阶段，则result为undefined，error与BusinessError的message字段一致； > - 如果当前任务正在运行且有异常抛出，则result为undefined，error为抛出的异常信息；没有异常时，result为任务执行完成后的结果，error与BusinessError的message字段一致。

**起始版本：** 20

<!--Device-taskpool-interface TaskResult--><!--Device-taskpool-interface TaskResult-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## error

```TypeScript
error?: Error | Object
```

错误信息。默认和BusinessError的message字段一致。不建议修改此值。

**类型：** Error \| Object

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TaskResult-error?: Error | Object--><!--Device-TaskResult-error?: Error | Object-End-->

**系统能力：** SystemCapability.Utils.Lang

## result

```TypeScript
result?: Object
```

任务执行结果。默认为undefined。不建议修改此值。

**类型：** Object

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TaskResult-result?: Object--><!--Device-TaskResult-result?: Object-End-->

**系统能力：** SystemCapability.Utils.Lang

