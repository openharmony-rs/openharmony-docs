# @ohos.fontManager (字体管理)(系统接口)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

字体管理模块，提供给系统应用安装和卸载三方字体的能力。

>  **说明：**
>  
>  - 本模块首批接口从API version 19开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  - 本模块为系统接口。

## 导入模块

```js
import { fontManager } from '@kit.LocalizationKit';
```

## installFont

installFont(path: string): Promise&lt;number&gt;

安装指定路径下的字体，使用promise异步回调。

**需要权限:** ohos.permission.UPDATE_FONT

**系统能力:** SystemCapability.Global.FontManager

**参数：** 

| 参数名   | 类型     | 必填   | 说明    |
| ----- | ------ | ---- | ----- |
| path | string | 是    | 安装字体文件路径。 |

**返回值：**

| 类型                    | 说明                     |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | 返回安装结果。返回为0表示安装成功，否则安装失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission denied.                 |
| 202 | Non-system application.            |
| 31100101 | Font does not exist.          |
| 31100102 | Font is not supported.        |
| 31100103 | Font file copy failed.        |
| 31100104 | Font file installed.          |
| 31100105 | Exceeded maximum number of installed files.     |
| 31100106 | Other error.     |

**示例：**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async installFont() {
    try {
      let res = await fontManager.installFont('fontPath');
      console.info('installFont suc. res is ' + res);
    } catch (error) {
      console.error('installFont err.' + error.code);
    }
    return;
  }
  ```

## uninstallFont

uninstallFont(fullName: string): Promise&lt;number&gt;

卸载指定名称的字体，使用promise异步回调。

**需要权限:** ohos.permission.UPDATE_FONT

**系统能力:** SystemCapability.Global.FontManager

**参数：** 

| 参数名   | 类型     | 必填   | 说明    |
| ----- | ------ | ---- | ----- |
| fullName | string | 是    | 需要卸载的字体名称，字体名称可通过打开.ttf或.ttc字体文件获取。 |

**返回值：**

| 类型                    | 说明                     |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | 返回卸载结果。返回为0表示卸载成功，否则卸载失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission denied.                |
| 202 | Non-system application.           |
| 31100107 | Font file does not exist.    |
| 31100108 | Font file delete error.      |
| 31100109 | Other error.                 |

**示例：**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async uninstallFont() {
    try {
      let res = await fontManager.uninstallFont('fontName');
      console.info('uninstallFont suc. res is ' + res);
    } catch (error) {
      console.error('uninstallFont err.' + error.code);
    }
    return;
  }
  ```

## dataMigration<sup>23+</sup>

dataMigration(callback: DataMigrationCallback): int

设备升级时使用的数据迁移接口，用于拉起迁移任务。

**需要权限:** ohos.permission.UPDATE_FONT

**系统能力:** SystemCapability.Global.FontManager

**参数：** 

| 参数名   | 类型     | 必填   | 说明    |
| ----- | ------ | ---- | ----- |
| callback | [DataMigrationCallback](#datamigrationcallback23) | 是    | 数据迁移的回调函数。 |

**返回值：**

| 类型                    | 说明                     |
| --------------------- | ---------------------- |
| int | 返回拉起数据迁移任务结果。返回为0表示拉起成功，否则拉起失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission denied.                |
| 202 | Non-system application.           |
| 31100110 | System error.  |
| 31100111 | DataMigrationing.      |

**示例：**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.log('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.log('onProgress callback');
      },
      onResult(result : int) => {
        console.log('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

## DataMigrationCallback<sup>23+</sup>

数据迁移时使用的回调类型。

### onHeartBeat<sup>23+</sup>

onHeartBeat(): void

回调函数，用于返回心跳回调。

**系统能力：** SystemCapability.Global.FontManager

**示例：**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.log('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.log('onProgress callback');
      },
      onResult(result : int) => {
        console.log('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

### onProgress<sup>23+</sup>

onProgress(progress : DataMigrationProgress): void

回调函数，用于返回数据迁移进度。

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名  | 类型   | 必填 | 说明                               |
| ------- | ------ | ---- | ---------------------------------- |
| progress | [DataMigrationProgress](#datamigrationprogress23) | 是   | 数据迁移进度信息。 |

**示例：**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.log('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.log('onProgress callback');
      },
      onResult(result : int) => {
        console.log('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

### onResult<sup>23+</sup>

onResult(result : int): void

回调函数，用于返回数据迁移的结果。

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名  | 类型   | 必填 | 说明                               |
| ------- | ------ | ---- | ---------------------------------- |
| result | int | 是   | 数据迁移结果。<br>0：数据迁移成功。<br>1：无需进行数据迁移。<br>2：获取用户ID失败。<br>3：检查目录失败。<br>4：初始化缓存目录失败。<br>5：打开源文件失败。<br>6：拷贝失败。<br>7：文件重命名失败。<br>8：文件删除失败。|

**示例：**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.log('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.log('onProgress callback');
      },
      onResult(result : int) => {
        console.log('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

## DataMigrationProgress<sup>23+</sup>

描述数据迁移的进度信息。

**系统能力：** SystemCapability.Global.FontManager

| 名称     | 类型 | 只读 | 可选    | 说明  |
| -------- | ---------------|--------|---------|-------------------------------- |
| timeRemaining | int  |是 | 否 | 表示预计剩余时间，单位：秒。    |
| progressPercentage | int |是 | 否 | 表示数据迁移百分比进展，取值：0-100。|