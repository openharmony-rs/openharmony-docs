# acquireShareData（系统接口）

## acquireShareData

```TypeScript
function acquireShareData(missionId: number, callback: AsyncCallback<Record<string, Object>>): void
```

系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的
[onShare](arkts-ability-uiability-c.md#onshare-1)回调并返回分享数据。使用
callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 目标应用的missionId，最大为2&lt;sup&gt;31&lt;/sup&gt;-1。 |
| callback | AsyncCallback&lt;Record&lt;string, Object&gt;&gt; | 是 | 回调函数。当接口调用成功，err为undefined，data为获取到的分享数据；否则为错误对象。可进行错误处理或其他自定义处理。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |


## acquireShareData

```TypeScript
function acquireShareData(missionId: number): Promise<Record<string, Object>>
```

系统弹框通过该接口发起原子化服务分享，触发目标UIAbility的
[onShare](arkts-ability-uiability-c.md#onshare-1)回调并返回分享数据。使用
Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| missionId | number | 是 | 目标应用的missionId，最大为2&lt;sup&gt;31&lt;/sup&gt;-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, Object&gt;&gt; | Promise used to return the API call result and the shared data. You canperform error handling or other custom processing. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

