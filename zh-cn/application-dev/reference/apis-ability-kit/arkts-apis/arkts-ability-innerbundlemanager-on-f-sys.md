# on（系统接口）

## 导入模块

```TypeScript
import { BundleStatusCallback } from '@kit.AbilityKit';
```

<a id="on"></a>
## on('BundleStatusChange')

```TypeScript
function on(type: 'BundleStatusChange',
    bundleStatusCallback: BundleStatusCallback, callback: AsyncCallback<string>): void
```

注册Callback。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [on](@ohos.bundle.bundleMonitor:bundleMonitor.on(type: BundleChangedEvent, callback: Callback<BundleChangedInfo>))  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-innerBundleManager-function on(type: 'BundleStatusChange',
    bundleStatusCallback: BundleStatusCallback, callback: AsyncCallback<string>): void--><!--Device-innerBundleManager-function on(type: 'BundleStatusChange',
    bundleStatusCallback: BundleStatusCallback, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | 是 | 指示应执行命令，只支持BundleStatusChange。 |
| bundleStatusCallback | [BundleStatusCallback](arkts-ability-bundlestatuscallback-t-sys.md) | 是 | 指示要注册的回调。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 程序启动作为入参的回调函数，返回正确结果或错误信息。 |


<a id="on-1"></a>
## on('BundleStatusChange')

```TypeScript
function on(type: 'BundleStatusChange', bundleStatusCallback: BundleStatusCallback): Promise<string>
```

注册Callback。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [on](@ohos.bundle.bundleMonitor:bundleMonitor.on(type: BundleChangedEvent, callback: Callback<BundleChangedInfo>))  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-innerBundleManager-function on(type: 'BundleStatusChange', bundleStatusCallback: BundleStatusCallback): Promise<string>--><!--Device-innerBundleManager-function on(type: 'BundleStatusChange', bundleStatusCallback: BundleStatusCallback): Promise<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | 是 | 指示应执行命令，只支持BundleStatusChange。 |
| bundleStatusCallback | [BundleStatusCallback](arkts-ability-bundlestatuscallback-t-sys.md) | 是 | 指示要注册的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise形式返回正确结果或错误信息。 |

