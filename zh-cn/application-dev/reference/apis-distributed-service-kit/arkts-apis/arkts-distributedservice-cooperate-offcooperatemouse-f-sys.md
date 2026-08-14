# off_cooperateMouse（系统接口）

## off_cooperateMouse

```TypeScript
function off(type: 'cooperateMouse', networkId: string, callback?: Callback<MouseLocation>): void
```

取消监听指定设备鼠标光标位置。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function off(type: 'cooperateMouse', networkId: string, callback?: Callback<MouseLocation>): void--><!--Device-cooperate-function off(type: 'cooperateMouse', networkId: string, callback?: Callback<MouseLocation>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperateMouse' | 是 | 监听类型，取值为'cooperateMouse'。 |
| networkId | string | 是 | 目标设备描述符 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MouseLocation](arkts-distributedservice-cooperate-mouselocation-i-sys.md)&gt; | 否 | 需要取消注册的回调函数，若无此参数， 则取消当前应用注册的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. &lt;br&gt;3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
// 取消注册单个回调函数
function callbackOn(data: cooperate.MouseLocation) {
  console.info('Register mouse location listener');
  return false;
}

function callbackOff(data: cooperate.MouseLocation) {
  console.info('Unregister mouse location listener');
  return false;
}

try {
  let networkId: string = 'Default';
  cooperate.on('cooperateMouse', networkId, callbackOn);
  cooperate.off('cooperateMouse', networkId, callbackOff);
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

```TypeScript
// 取消注册所有回调函数
function callbackOn(data: cooperate.MouseLocation) {
  console.info('Register mouse location listener');
}

try {
  let networkId: string = 'Default';
  cooperate.on('cooperateMouse', networkId, callbackOn);
  cooperate.off('cooperateMouse', networkId);
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

