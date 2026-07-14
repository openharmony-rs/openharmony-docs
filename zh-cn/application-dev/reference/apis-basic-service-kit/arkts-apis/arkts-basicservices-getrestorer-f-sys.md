# getRestorer（系统接口）

## getRestorer

```TypeScript
function getRestorer(): Restorer
```

获取恢复出厂设置对象。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Restorer | 恢复出厂对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();

```

