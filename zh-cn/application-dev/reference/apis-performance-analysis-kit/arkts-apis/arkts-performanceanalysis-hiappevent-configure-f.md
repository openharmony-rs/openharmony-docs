# configure

## configure

```TypeScript
function configure(config: ConfigOption): void
```

应用事件打点配置方法，支持配置打点开关和目录存储配额大小。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function configure(config: ConfigOption): void--><!--Device-hiAppEvent-function configure(config: ConfigOption): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用事件打点配置项对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |
| [11103001](../errorcode-hiappevent.md#11103001-非法的最大存储配额值) | Invalid max storage quota value. Possibly caused by incorrectly formatted. |

**示例：**

```TypeScript
// 配置打点开关为关闭状态
let config1: hiAppEvent.ConfigOption = {
  disable: true,
};
hiAppEvent.configure(config1);

// 配置文件目录存储配额为100M
let config2: hiAppEvent.ConfigOption = {
  maxStorage: '100MB',
};
hiAppEvent.configure(config2);
```

