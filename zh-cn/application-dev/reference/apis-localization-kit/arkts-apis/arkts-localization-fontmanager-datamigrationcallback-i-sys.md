# DataMigrationCallback（系统接口）

数据迁移时使用的回调接口类型，定义了数据迁移过程中的回调方法。开发者需实现该接口的所有方法，以接收迁移过程中的心跳通知、进度更新和最终结果。

**起始版本：** 23

<!--Device-fontManager-interface DataMigrationCallback--><!--Device-fontManager-interface DataMigrationCallback-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## onHeartBeat

```TypeScript
onHeartBeat(): void
```

回调函数，在数据迁移任务执行期间定期调用，用于通知开发者迁移任务仍在正常运行，开发者可据此更新UI提示或执行其他业务逻辑。

**起始版本：** 23

<!--Device-DataMigrationCallback-onHeartBeat(): void--><!--Device-DataMigrationCallback-onHeartBeat(): void-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { fontManager } from '@kit.LocalizationKit';

class DataMigrationCallbackImpl implements fontManager.DataMigrationCallback {
  onHeartBeat(): void {
    console.info('onHeartBeat callback');
  }
  onProgress(progress : fontManager.DataMigrationProgress): void {
    console.info('onProgress callback');
  }
  onResult(result : int): void {
    console.info('onResult callback');
  }
}

async function dataMigration() {
  const callback = new DataMigrationCallbackImpl;
  try {
    let res: int = fontManager.dataMigration(callback);
    console.info('dataMigration suc. res is ' + res);
  } catch (error) {
    console.error('dataMigration err.' + error.code);
  }
}
```

## onProgress

```TypeScript
onProgress(progress : DataMigrationProgress): void
```

回调函数，在数据迁移任务执行过程中定期调用，用于通知开发者当前的迁移进度和预估剩余时间。当需要在UI上展示进度条、剩余时间等信息时使用此回调。

**起始版本：** 23

<!--Device-DataMigrationCallback-onProgress(progress : DataMigrationProgress): void--><!--Device-DataMigrationCallback-onProgress(progress : DataMigrationProgress): void-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | [DataMigrationProgress](arkts-localization-fontmanager-datamigrationprogress-i-sys.md) | 是 | 数据迁移进度信息。 |

**示例**

```TypeScript
import { fontManager } from '@kit.LocalizationKit';

class DataMigrationCallbackImpl implements fontManager.DataMigrationCallback {
  onHeartBeat(): void {
    console.info('onHeartBeat callback');
  }
  onProgress(progress : fontManager.DataMigrationProgress): void {
    console.info('onProgress callback');
  }
  onResult(result : int): void {
    console.info('onResult callback');
  }
}

async function dataMigration() {
  const callback = new DataMigrationCallbackImpl;
  try {
    let res: int = fontManager.dataMigration(callback);
    console.info('dataMigration suc. res is ' + res);
  } catch (error) {
    console.error('dataMigration err.' + error.code);
  }
}
```

## onResult

```TypeScript
onResult(result : int): void
```

回调函数，在数据迁移任务完成（无论成功或失败）后调用，用于通知开发者迁移的最终结果。当需要在迁移完成后执行后续操作（如更新UI、记录日志、通知用户等）时使用此回调。

**起始版本：** 23

<!--Device-DataMigrationCallback-onResult(result : int): void--><!--Device-DataMigrationCallback-onResult(result : int): void-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | int | 是 | 数据迁移结果。 <br>0：数据迁移成功。 <br>1：无需进行数据迁移。 <br>2：获取用户ID失败。 <br>3：检查目录失败。 <br>4：初始化缓存目录失败。 <br>5：打开源文件失败。 <br>6：拷贝失败。 <br>7：文件重命名失败。 <br>8：文件删除失败。 |

**示例**

```TypeScript
import { fontManager } from '@kit.LocalizationKit';

class DataMigrationCallbackImpl implements fontManager.DataMigrationCallback {
  onHeartBeat(): void {
    console.info('onHeartBeat callback');
  }
  onProgress(progress : fontManager.DataMigrationProgress): void {
    console.info('onProgress callback');
  }
  onResult(result : int): void {
    console.info('onResult callback');
  }
}

async function dataMigration() {
  const callback = new DataMigrationCallbackImpl;
  try {
    let res: int = fontManager.dataMigration(callback);
    console.info('dataMigration suc. res is ' + res);
  } catch (error) {
    console.error('dataMigration err.' + error.code);
  }
}
```

