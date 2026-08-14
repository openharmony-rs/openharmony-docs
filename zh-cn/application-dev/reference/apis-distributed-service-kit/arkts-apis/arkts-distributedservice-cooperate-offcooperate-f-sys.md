# off_cooperate（系统接口）

## off_cooperate

```TypeScript
function off(type: 'cooperate', callback?: Callback<void>): void
```

取消监听键鼠穿越状态。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [off](#off_cooperate)(type: 'cooperateMessage', callback?: Callback&lt;CooperateMessage&gt;)

<!--Device-cooperate-function off(type: 'cooperate', callback?: Callback<void>): void--><!--Device-cooperate-function off(type: 'cooperate', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperate' | 是 | 监听类型，取值为'cooperate'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要取消注册的回调函数，若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. &lt;br&gt;3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
// 取消注册单个回调函数
class Data {
  networkId: string = "networkId";
  msg: cooperate.CooperateMsg = 0;
}

function callbackOff() {
  console.info(`Keyboard mouse crossing event`);
  return false;
}

try {
  cooperate.on('cooperate', (data: Data) => {
    console.info(`Keyboard mouse crossing event: ${JSON.stringify(data)}`);
  });
  cooperate.off('cooperate', callbackOff);
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error)}`);
}
```

```TypeScript
// 取消注册所有回调函数
class Data {
  networkId: string = "networkId";
  msg: cooperate.CooperateMsg = 0;
}

try {
  cooperate.on('cooperate', (data: Data) => {
    console.info(`Keyboard mouse crossing event: ${JSON.stringify(data)}`);
  });
  cooperate.off('cooperate');
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

