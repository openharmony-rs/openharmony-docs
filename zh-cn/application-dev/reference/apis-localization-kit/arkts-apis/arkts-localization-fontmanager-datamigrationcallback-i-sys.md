# DataMigrationCallback（系统接口）

数据迁移时使用的回调类型。

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

回调函数，用于返回心跳回调。

**起始版本：** 23

<!--Device-DataMigrationCallback-onHeartBeat(): void--><!--Device-DataMigrationCallback-onHeartBeat(): void-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
import { fontManager } from '@kit.LocalizationKit';

async function dataMigration() {
  const callback: fontManager.DataMigrationCallback = {
    onHeartBeat: () => {
      console.info('onHeartBeat callback');
    },
    onProgress: (progress : fontManager.DataMigrationProgress) => {
      console.info('onProgress callback');
    },
    onResult: (result : number) => {
      console.info('onResult callback');
    }
  }
  try {
    let res = await fontManager.dataMigration(callback);
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

回调函数，用于返回数据迁移进度。

**起始版本：** 23

<!--Device-DataMigrationCallback-onProgress(progress : DataMigrationProgress): void--><!--Device-DataMigrationCallback-onProgress(progress : DataMigrationProgress): void-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | [DataMigrationProgress](arkts-localization-fontmanager-datamigrationprogress-i-sys.md) | 是 | 数据迁移进度信息。 |

**示例：**

```TypeScript
import { fontManager } from '@kit.LocalizationKit';

async function dataMigration() {
  const callback: fontManager.DataMigrationCallback = {
    onHeartBeat: () => {
      console.info('onHeartBeat callback');
    },
    onProgress: (progress : fontManager.DataMigrationProgress) => {
      console.info('onProgress callback');
    },
    onResult: (result : number) => {
      console.info('onResult callback');
    }
  }
  try {
    let res = await fontManager.dataMigration(callback);
    console.info('dataMigration suc. res is ' + res);
  } catch (error) {
    console.error('dataMigration err.' + error.code);
  }
}

```

## onResult

```TypeScript
onResult(result : number): void
```

回调函数，用于返回数据迁移的结果。

**起始版本：** 23

<!--Device-DataMigrationCallback-onResult(result : int): void--><!--Device-DataMigrationCallback-onResult(result : int): void-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | number | 是 | 数据迁移结果。<br>**0**: 数据迁移成功。<br>**1**: 无需进行数据迁移。<br>**2**: 获取用户ID失败。<br>**3**: 检查目录失败。<br>**4**: 初始化缓存目录失败。<br>**5**: 打开源文件失败。<br>**6**: 拷贝失败。<br>**7**: 文件重命名失败。<br>**8**: 文件删除失败。 |

**示例：**

```TypeScript
import { fontManager } from '@kit.LocalizationKit';

async function dataMigration() {
  const callback: fontManager.DataMigrationCallback = {
    onHeartBeat: () => {
      console.info('onHeartBeat callback');
    },
    onProgress: (progress : fontManager.DataMigrationProgress) => {
      console.info('onProgress callback');
    },
    onResult: (result : number) => {
      console.info('onResult callback');
    }
  }
  try {
    let res = await fontManager.dataMigration(callback);
    console.info('dataMigration suc. res is ' + res);
  } catch (error) {
    console.error('dataMigration err.' + error.code);
  }
}

```

