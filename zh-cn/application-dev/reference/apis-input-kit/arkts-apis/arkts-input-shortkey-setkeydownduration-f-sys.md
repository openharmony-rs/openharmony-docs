# setKeyDownDuration（系统接口）

## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void
```

设置快捷键拉起Ability的延迟时间，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void--><!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.ShortKey

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessKey | string | 是 | 业务在多模侧注册的唯一标识，与ability_launch_config.json中的businessId对应。调用接口前自行查询。 |
| delay | int | 是 | 按下快捷键多长时间后拉起Ability，单位：ms，仅支持快捷键按下触发。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置快捷键拉起Ability的延迟时间成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |


## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: int): Promise<void>
```

设置快捷键拉起Ability的延迟时间，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int): Promise<void>--><!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.ShortKey

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessKey | string | 是 | 业务在多模侧注册的唯一标识，与ability_launch_config.json中的businessId对应。调用接口前自行查询。 |
| delay | int | 是 | 按下快捷键多长时间后拉起Ability，单位：ms，仅支持快捷键按下触发。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Returns the result through a promise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |

