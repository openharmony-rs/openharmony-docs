# setPowerConfig（系统接口）

## setPowerConfig

```TypeScript
function setPowerConfig(sceneName: string, value: string): void
```

根据场景名称设置电源配置值。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.POWER_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneName | string | 是 | 表示电源配置的场景名称。sceneName参数必须是字符串类型且最大长度128字节； |
| value | string | 是 | 表示电源配置值。value参数必须是字符串类型且最大长度128字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../../errorcode-universal.md#4900101-Failed) | Failed to connect to the service. |
| [4900400](../../errorcode-universal.md#4900400-Invalid) | Invalid parameter. Possible causes:<br/>1. The sceneName or value parameter is an empty string;<br/>2. The length of sceneName parameter exceeds 128 bytes;<br/>3. The length of value parameter exceeds 128 bytes. |
| [4900601](../../errorcode-universal.md#4900601-Failed) | Failed to write the power configuration value. |

**示例：**

```TypeScript
try {
    power.setPowerConfig('scene_name_test', 'value_test');
    console.info('set power config success');
} catch(err) {
    console.error('set power config failed, err: ' + err);
}

```

