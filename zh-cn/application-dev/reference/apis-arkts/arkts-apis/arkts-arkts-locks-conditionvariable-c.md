# ConditionVariable

用于线程同步的对象。

**起始版本：** 18

**装饰器类型：** @Sendable

<!--Device-locks-class ConditionVariable--><!--Device-locks-class ConditionVariable-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

默认构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-constructor()--><!--Device-ConditionVariable-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

<a id="notifyall"></a>
## notifyAll

```TypeScript
notifyAll(): void
```

通知所有等待的Promise。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-notifyAll(): void--><!--Device-ConditionVariable-notifyAll(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

<a id="notifyone"></a>
## notifyOne

```TypeScript
notifyOne(): void
```

通知一个等待的Promise。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-notifyOne(): void--><!--Device-ConditionVariable-notifyOne(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

<a id="request"></a>
## request

```TypeScript
static request(name: string): ConditionVariable
```

使用指定的名称查找或创建ConditionVariable实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-static request(name: string): ConditionVariable--><!--Device-ConditionVariable-static request(name: string): ConditionVariable-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要查找或创建的ConditionVariable的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ConditionVariable](arkts-arkts-locks-conditionvariable-c.md) | 返回ConditionVariable实例。 |

<a id="wait"></a>
## wait

```TypeScript
wait(): Promise<void>
```

等待ConditionVariable被通知。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-wait(): Promise<void>--><!--Device-ConditionVariable-wait(): Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 一旦ConditionVariable被通知，Promise将被解决。 |

<a id="waitfor"></a>
## waitFor

```TypeScript
waitFor(timeout: number): Promise<void>
```

等待ConditionVariable被通知，或直到达到指定的时间限制。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-waitFor(timeout: number): Promise<void>--><!--Device-ConditionVariable-waitFor(timeout: number): Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 最长等待时间。该值应为整数。<br>单位：ms。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 一旦ConditionVariable被通知或达到指定时间限制，Promise将被解决。 |

