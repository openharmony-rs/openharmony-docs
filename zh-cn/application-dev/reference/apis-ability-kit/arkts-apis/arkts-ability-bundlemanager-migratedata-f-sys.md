# migrateData（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## migrateData

```TypeScript
function migrateData(sourcePaths: Array<string>, destinationPath: string): Promise<void>
```

拷贝文件，将文件从源路径拷贝到目标路径。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MIGRATE_DATA

<!--Device-bundleManager-function migrateData(sourcePaths: Array<string>, destinationPath: string): Promise<void>--><!--Device-bundleManager-function migrateData(sourcePaths: Array<string>, destinationPath: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourcePaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 需要迁移的源路径数组，支持传入如/example1/test.txt的单文件路径，或/example2/test的目录路径。 |
| destinationPath | string | 是 | 目标路径，仅支持传入一个目录路径，例如：/example2/test。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700080](../errorcode-bundle.md#17700080-源路径中存在无效路径) | The source paths are invalid. |
| [17700081](../errorcode-bundle.md#17700081-目标路径为无效路径) | The destination path is invalid. |
| [17700082](../errorcode-bundle.md#17700082-用户身份认证失败) | User authentication failed. |
| [17700083](../errorcode-bundle.md#17700083-用户身份认证超时) | Waiting for user authentication timeout. |
| [17700084](../errorcode-bundle.md#17700084-源路径中存在未开启权限路径) | There are inaccessible path in the source paths. |
| [17700085](../errorcode-bundle.md#17700085-目标路径未开启写权限) | The destination path cannot be accessed. |
| [17700086](../errorcode-bundle.md#17700086-发生系统错误) | System error occurred during copy execution. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  // 开发者需将source1、source2、dest内容更新为实际文件路径或目录路径。
  let source1: string = "/data/app/el2/100/base/com.example.myapplication/";
  let source2: string = "/data/app/el2/101/base/com.example.myapplication/log.txt";
  let dest: string = "/data/local/tmp";
  let sourcePaths: Array<string> = [source1, source2];

  bundleManager.migrateData(sourcePaths, dest)
    .then(() => {
      hilog.info(0x0000, 'testTag', 'migrateData succeed');
    })
    .catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'migrateData err: %{public}s', JSON.stringify(err));
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', 'migrateData call err: %{public}s', JSON.stringify(err));
}

```

