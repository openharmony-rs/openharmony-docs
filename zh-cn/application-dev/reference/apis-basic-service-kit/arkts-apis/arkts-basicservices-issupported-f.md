# isSupported

## isSupported

```TypeScript
function isSupported(type: RunningLockType): boolean
```

查询系统是否支持该类型的锁。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | RunningLockType | 是 | 需要查询的锁的类型；该参数必须是一个枚举类。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示支持，返回false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types;2. Parameter verification failed. |

**示例：**

```TypeScript
try {
    let isSupported = runningLock.isSupported(runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL);
    console.info('BACKGROUND type supported: ' + isSupported);
} catch(err) {
    console.error('check supported failed, err: ' + err);
}

```

