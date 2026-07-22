# isIdleState

## 导入模块

```TypeScript
import { bundleState } from '@kit.BackgroundTasksKit';
```

## isIdleState

```TypeScript
function isIdleState(bundleName: string, callback: AsyncCallback<boolean>): void
```

判断指定bundleName的应用当前是否是空闲状态，三方应用只能查询自身的空闲状态。系统应用支持查询其他应用的空闲状态，查询前需要申请权限ohos.permission.BUNDLE_ACTIVE_INFO。使用Callback异步回调。

**起始版本：** 7

**废弃版本：** 9

<!--Device-bundleState-function isIdleState(bundleName: string, callback: AsyncCallback<boolean>): void--><!--Device-bundleState-function isIdleState(bundleName: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的bundleName。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 指定的callback回调方法。如果指定的bundleName有效，则返回指定bundleName的应用当前是否是空闲状态；否则返回null。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';
// 三方应用使用示例代码时，注意将bundleName更换为自己应用的bundleName
bundleState.isIdleState("com.ohos.camera", (err: BusinessError, res: boolean) => {
  if (err) {
    console.error('BUNDLE_ACTIVE isIdleState callback failed, because: ' + err.code);
  } else {
    console.info('BUNDLE_ACTIVE isIdleState callback succeeded, result: ' + JSON.stringify(res));
  }
});

```


## isIdleState

```TypeScript
function isIdleState(bundleName: string): Promise<boolean>
```

判断指定bundleName的应用当前是否是空闲状态，三方应用只能查询自身的空闲状态。系统应用支持查询其他应用的空闲状态，查询前需要申请权限ohos.permission.BUNDLE_ACTIVE_INFO，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

<!--Device-bundleState-function isIdleState(bundleName: string): Promise<boolean>--><!--Device-bundleState-function isIdleState(bundleName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 指定的Promise回调方法。如果指定的bundleName有效，则返回指定bundleName的应用当前是否是空闲状态；否则返回null。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';
// 三方应用使用示例代码时，注意将bundleName更换为自己应用的bundleName
bundleState.isIdleState("com.ohos.camera").then((res: boolean) => {
  console.info('BUNDLE_ACTIVE isIdleState promise succeeded, result: ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE isIdleState promise failed, because: ' + err.code);
});

```

