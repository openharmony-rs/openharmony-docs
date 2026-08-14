# on_cooperateMouse（系统接口）

## on_cooperateMouse

```TypeScript
function on(type: 'cooperateMouse', networkId: string, callback: Callback<MouseLocation>): void
```

注册监听指定设备鼠标光标位置。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function on(type: 'cooperateMouse', networkId: string, callback: Callback<MouseLocation>): void--><!--Device-cooperate-function on(type: 'cooperateMouse', networkId: string, callback: Callback<MouseLocation>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperateMouse' | 是 | 监听类型，取值为'cooperateMouse' |
| networkId | string | 是 | 目标设备描述符 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MouseLocation](arkts-distributedservice-cooperate-mouselocation-i-sys.md)&gt; | 是 | 回调函数，异步返回指定监听设备鼠标光标位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2.Incorrect parameter types. &lt;br&gt;3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
function callback(data: cooperate.MouseLocation) {
  console.info('displayX:' + data.displayX + 'displayY:' + data.displayY + 'displayWidth:' +
  data.displayWidth + 'displayHeight:' + data.displayHeight);
}

try {
  let networkId: string = 'Default';
  cooperate.on('cooperateMouse', networkId, callback);
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

