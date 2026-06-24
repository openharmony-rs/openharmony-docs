# isActive

## isActive

```TypeScript
function isActive(): boolean
```

检测当前设备是否处于活动状态。

- 有屏的设备亮屏时为活动状态，熄屏时为非活动状态。
- 无屏的设备非休眠时为活动状态，休眠时为非活动状态。

**起始版本：** 9

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 活动状态返回true，非活动状态返回false。 |

**示例：**

```TypeScript
let isActive = power.isActive();
console.info('power is active: ' + isActive);

```

