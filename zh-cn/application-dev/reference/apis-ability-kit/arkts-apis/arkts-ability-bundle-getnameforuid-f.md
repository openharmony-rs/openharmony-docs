# getNameForUid

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getNameForUid

```TypeScript
function getNameForUid(uid: number, callback: AsyncCallback<string>): void
```

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getBundleNameByUid

<!--Device-bundle-function getNameForUid(uid: number, callback: AsyncCallback<string>): void--><!--Device-bundle-function getNameForUid(uid: number, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | @param { AsyncCallback&lt;string&gt; } callback |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string> | 是 |  |


## getNameForUid

```TypeScript
function getNameForUid(uid: number): Promise<string>
```

通过uid获取对应的Bundle名称，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

<!--Device-bundle-function getNameForUid(uid: number): Promise<string>--><!--Device-bundle-function getNameForUid(uid: number): Promise<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 要查询的uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Returns the bundle name. |

