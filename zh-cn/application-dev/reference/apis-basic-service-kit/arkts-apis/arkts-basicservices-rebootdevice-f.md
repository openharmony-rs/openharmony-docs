# rebootDevice

## rebootDevice

```TypeScript
function rebootDevice(reason: string): void
```

重启系统。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [reboot](arkts-basicservices-reboot-f-sys.md#reboot-1)

**需要权限：** ohos.permission.REBOOT

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 重启原因。例如，“updater”表示重启后进入更新模式。如果未指定该参数，系统将在重启后进入正常模式。 |

**示例：**

```TypeScript
power.rebootDevice('reboot_test');

```

