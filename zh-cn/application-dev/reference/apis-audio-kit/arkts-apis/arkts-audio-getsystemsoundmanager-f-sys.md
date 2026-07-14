# getSystemSoundManager（系统接口）

## getSystemSoundManager

```TypeScript
function getSystemSoundManager(): SystemSoundManager
```

获取系统声音管理器。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SystemSoundManager | 系统声音管理类。 |

**示例：**

```TypeScript
let systemSoundManagerInstance: systemSoundManager.SystemSoundManager = systemSoundManager.getSystemSoundManager();

```

