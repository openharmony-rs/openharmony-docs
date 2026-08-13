# acquireShareData（系统接口）

## acquireShareData

```TypeScript
function acquireShareData(missionId: int, callback: AsyncCallback<Record<string, Object>>): void
```

系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的 [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onShare)回调并返回分享数据。使用 callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-abilityManager-function acquireShareData(missionId: int, callback: AsyncCallback<Record<string, Object>>): void--><!--Device-abilityManager-function acquireShareData(missionId: int, callback: AsyncCallback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 目标应用的missionId，最大为2&lt;sup&gt;31&lt;/sup&gt;-1。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | 回调函数。当接口调用成功，err为undefined，data为获取到的分享数据；否则为错误对象。可进行错误处理或其他自 定义处理。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |


## acquireShareData

```TypeScript
function acquireShareData(missionId: int, callback: AsyncCallback<Record<string, RecordData>>): void
```

系统弹框通过该接口发起原子化服务分享，调用到目标UIAbility的onShare，返回分享数据。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-abilityManager-function acquireShareData(missionId: int, callback: AsyncCallback<Record<string, RecordData>>): void--><!--Device-abilityManager-function acquireShareData(missionId: int, callback: AsyncCallback<Record<string, RecordData>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 目标应用的missionId，最大为231-1。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;&gt; | 是 | 以回调方式返回接口运行结果及分享得到的数据，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system service failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |


## acquireShareData

```TypeScript
function acquireShareData(missionId: int): Promise<Record<string, Object>>
```

系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的 [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onShare)回调并返回分享数据。使用 Promise异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-abilityManager-function acquireShareData(missionId: int): Promise<Record<string, Object>>--><!--Device-abilityManager-function acquireShareData(missionId: int): Promise<Record<string, Object>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 目标应用的missionId，最大为2&lt;sup&gt;31&lt;/sup&gt;-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{ [key: string]: Object | > } The promise returned by the function.<br>**适用版本：** 10+ |
| Promise&lt;Record&lt;string, Object&gt;&gt; | Promise used to return the API call result and the shared data. You can perform error handling or other custom processing.<br>**适用版本：** 11+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |


## acquireShareData

```TypeScript
function acquireShareData(missionId: int): Promise<Record<string, RecordData>>
```

系统弹框通过该接口发起原子化服务分享，调用到目标UIAbility的onShare，返回分享数据。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-abilityManager-function acquireShareData(missionId: int): Promise<Record<string, RecordData>>--><!--Device-abilityManager-function acquireShareData(missionId: int): Promise<Record<string, RecordData>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | int | 是 | 目标应用的missionId，最大为231-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

