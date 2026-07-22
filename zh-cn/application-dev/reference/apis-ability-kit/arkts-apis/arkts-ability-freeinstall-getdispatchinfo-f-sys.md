# getDispatchInfo（系统接口）

## 导入模块

```TypeScript
import { freeInstall } from '@kit.AbilityKit';
```

## getDispatchInfo

```TypeScript
function getDispatchInfo(callback: AsyncCallback<DispatchInfo>): void
```

获取有关dispatch版本的信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-freeInstall-function getDispatchInfo(callback: AsyncCallback<DispatchInfo>): void--><!--Device-freeInstall-function getDispatchInfo(callback: AsyncCallback<DispatchInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DispatchInfo&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)。当函数调用成功，err为undefined，data为获取到的[DispatchInfo](arkts-ability-freeinstall-dispatchinfo-t-sys.md)信息。否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |


## getDispatchInfo

```TypeScript
function getDispatchInfo(): Promise<DispatchInfo>
```

获取有关dispatch版本的信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-freeInstall-function getDispatchInfo(): Promise<DispatchInfo>--><!--Device-freeInstall-function getDispatchInfo(): Promise<DispatchInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DispatchInfo&gt; | Promise对象，返回[DispatchInfo](arkts-ability-freeinstall-dispatchinfo-t-sys.md)信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

