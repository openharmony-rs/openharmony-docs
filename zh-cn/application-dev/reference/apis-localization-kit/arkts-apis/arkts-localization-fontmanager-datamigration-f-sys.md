# dataMigration（系统接口）

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## dataMigration

```TypeScript
function dataMigration(callback: DataMigrationCallback): number
```

设备升级时使用的数据迁移接口，用于启动迁移任务，通过回调函数实时反馈迁移进度和结果。

**起始版本：** 23

**需要权限：** ohos.permission.UPDATE_FONT

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | 是 | 数据迁移的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 迁移任务启动结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [31100110](../errorcode-font-manager.md#31100110-系统异常导致接口调用失败) | Call failed due to system error. |
| [31100111](../errorcode-font-manager.md#31100111-迁移任务执行中) | Data migration is in progress. |

**示例**

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
