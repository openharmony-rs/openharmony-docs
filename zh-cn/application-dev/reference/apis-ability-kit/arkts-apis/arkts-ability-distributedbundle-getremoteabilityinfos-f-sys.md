# getRemoteAbilityInfos（系统接口）

## 导入模块

```TypeScript
import { distributedBundle } from '@kit.AbilityKit';
```

## getRemoteAbilityInfos

```TypeScript
function getRemoteAbilityInfos(elementNames: Array<ElementName>,
    callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

根据给定的ElementName获取有关远程设备AbilityInfos信息，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundle-function getRemoteAbilityInfos(elementNames: Array<ElementName>,    callback: AsyncCallback<Array<RemoteAbilityInfo>>): void--><!--Device-distributedBundle-function getRemoteAbilityInfos(elementNames: Array<ElementName>,    callback: AsyncCallback<Array<RemoteAbilityInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName信息，最大数组长度为10。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | 是 | 程序启动作为入参的回调函数，返回远程基本能力信息。 |


## getRemoteAbilityInfos

```TypeScript
function getRemoteAbilityInfos(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>
```

根据给定的ElementName获取有关远程设备AbilityInfos信息，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-distributedBundle-function getRemoteAbilityInfos(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>--><!--Device-distributedBundle-function getRemoteAbilityInfos(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName信息，最大数组长度为10。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | Promise形式返回远程基本能力信息。 |

