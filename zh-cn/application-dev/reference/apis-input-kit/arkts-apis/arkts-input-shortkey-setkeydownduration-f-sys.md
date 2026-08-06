# setKeyDownDuration（系统接口）

## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void
```

设置快捷键拉起Ability的延迟时间，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void--><!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.ShortKey

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessKey | string | 是 | 业务在多模侧注册的唯一标识，与ability\_\_\_ESCAPED\_UNDERSCORE\_\_\_launch\_\_\_ESCAPED\_UNDERSCORE\_\_\_config.json中的businessId对应。调用接口前自行查询。 |
| delay | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 按下快捷键多长时间后拉起Ability，单位：ms，仅支持快捷键按下触发。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当设置快捷键拉起Ability的延迟时间成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |


## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: int): Promise<void>
```

设置快捷键拉起Ability的延迟时间，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int): Promise<void>--><!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.ShortKey

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessKey | string | 是 | 业务在多模侧注册的唯一标识，与ability\_\_\_ESCAPED\_UNDERSCORE\_\_\_launch\_\_\_ESCAPED\_UNDERSCORE\_\_\_config.json中的businessId对应。调用接口前自行查询。 |
| delay | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 按下快捷键多长时间后拉起Ability，单位：ms，仅支持快捷键按下触发。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Returns the result through a promise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

