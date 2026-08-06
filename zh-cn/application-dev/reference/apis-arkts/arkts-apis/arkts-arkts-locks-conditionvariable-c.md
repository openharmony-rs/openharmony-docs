# ConditionVariable

实现异步等待功能的类，支持异步等待通知操作。该类使用@Sendable装饰器装饰。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Sendable

<!--Device-locks-class ConditionVariable--><!--Device-locks-class ConditionVariable-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

默认构造函数。创建一个异步等待通知操作的对象。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-constructor()--><!--Device-ConditionVariable-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## notifyAll

```TypeScript
notifyAll(): void
```

通知所有等待的线程。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-notifyAll(): void--><!--Device-ConditionVariable-notifyAll(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## notifyOne

```TypeScript
notifyOne(): void
```

通知第一个等待的线程。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-notifyOne(): void--><!--Device-ConditionVariable-notifyOne(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## request

```TypeScript
static request(name: string): ConditionVariable
```

使用指定的名称查找或创建（如果未找到）异步等待通知操作的对象。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-static request(name: string): ConditionVariable--><!--Device-ConditionVariable-static request(name: string): ConditionVariable-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 按指定名称查找或创建等待通知操作的对象名称，字符串无特别限制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回查找到或创建后的异步等待通知操作的实例。 |

## wait

```TypeScript
wait(): Promise<void>
```

异步调用进入等待中，将在被唤醒后继续执行。使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-wait(): Promise<void>--><!--Device-ConditionVariable-wait(): Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

## waitFor

```TypeScript
waitFor(timeout: number): Promise<void>
```

异步调用进入等待中，将在被唤醒或者等待时间结束后继续执行。使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConditionVariable-waitFor(timeout: number): Promise<void>--><!--Device-ConditionVariable-waitFor(timeout: number): Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 等待时间，单位为毫秒，正整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

