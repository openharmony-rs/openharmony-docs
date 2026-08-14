# getExtensionRunningInfos（系统接口）

## getExtensionRunningInfos

```TypeScript
function getExtensionRunningInfos(upperLimit: int): Promise<Array<ExtensionRunningInfo>>
```

获取关于运行扩展能力的信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-abilityManager-function getExtensionRunningInfos(upperLimit: int): Promise<Array<ExtensionRunningInfo>>--><!--Device-abilityManager-function getExtensionRunningInfos(upperLimit: int): Promise<Array<ExtensionRunningInfo>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upperLimit | int | 是 | 获取消息数量的最大限制，最大为2&lt;sup&gt;31&lt;/sup&gt;-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ExtensionRunningInfo&gt;&gt; | Promise对象，返回接口运行结果及运行扩展能力的信息。开发者可在此进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |


## getExtensionRunningInfos

```TypeScript
function getExtensionRunningInfos(upperLimit: int, callback: AsyncCallback<Array<ExtensionRunningInfo>>): void
```

获取关于运行扩展能力的信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-abilityManager-function getExtensionRunningInfos(upperLimit: int, callback: AsyncCallback<Array<ExtensionRunningInfo>>): void--><!--Device-abilityManager-function getExtensionRunningInfos(upperLimit: int, callback: AsyncCallback<Array<ExtensionRunningInfo>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upperLimit | int | 是 | 获取消息数量的最大限制，最大为2&lt;sup&gt;31&lt;/sup&gt;-1。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;ExtensionRunningInfo&gt;&gt; | 是 | 回调函数。当获取运行扩展能力的信息成功，err为undefined，data为获取到的运行扩展能力信息；否则为 错误对象。可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

