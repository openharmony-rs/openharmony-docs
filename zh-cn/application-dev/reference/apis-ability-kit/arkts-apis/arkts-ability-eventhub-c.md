# EventHub

EventHub是系统提供的基于发布-订阅模式实现的事件通信机制。通过事件名，实现了发送方和订阅方之间的解耦，支持不同业务模块间的高效数据传递和状态同步。主要用于[UIAbility组件与UI的数据通信](../../../application-models/uiability-data-sync-with-ui.md)。不同的Context对象拥有不同的EventHub对象，不同EventHub对象之间无法直接通信。事件的订阅、取消订阅、触发都作用在某一个具体的EventHub对象上。由于Worker、Taskpool通过Actor模型实现[多线程并发](../../../arkts-utils/multi-thread-concurrency-overview.md#多线程并发模型)，不同虚拟机实例之间拥有独占的内存，因此EventHub对象不能用于线程间的数据通信。

**起始版本：** 9

<!--Device-unnamed-declare class EventHub--><!--Device-unnamed-declare class EventHub-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## emit

```TypeScript
emit(event: string, ...args: Object[]): void
```

触发指定事件。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventHub-emit(event: string, ...args: Object[]): void--><!--Device-EventHub-emit(event: string, ...args: Object[]): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 事件名称。 |
| args | Object[] | 是 | 可变参数，事件触发时，传递给回调函数的参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

## off

```TypeScript
off(event: string, callback?: Function): void
```

取消订阅指定事件。

- 传入callback：取消指定的callback对指定事件的订阅，当该事件触发后，将不会回调该callback。  
- 不传callback：取消所有callback对指定事件的订阅。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventHub-off(event: string, callback?: Function): void--><!--Device-EventHub-off(event: string, callback?: Function): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 事件名称。 |
| callback | Function | 否 | 事件回调。如果不传callback，则取消订阅该事件下所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

## on

```TypeScript
on(event: string, callback: Function): void
```

订阅指定事件。
> **说明：**  
>  
> callback被emit触发时，调用方是EventHub对象，如果要修改callback中this的指向，可以使用箭头函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventHub-on(event: string, callback: Function): void--><!--Device-EventHub-on(event: string, callback: Function): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 事件名称。 |
| callback | Function | 是 | 事件回调，事件触发后调用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

