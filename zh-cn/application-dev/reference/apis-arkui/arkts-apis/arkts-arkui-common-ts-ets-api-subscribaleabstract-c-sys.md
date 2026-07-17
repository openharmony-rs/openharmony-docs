# SubscribaleAbstract（系统接口）

定义Subscribale基类。

**起始版本：** 7

<!--Device-unnamed-declare abstract class SubscribaleAbstract--><!--Device-unnamed-declare abstract class SubscribaleAbstract-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## addOwningProperty

```TypeScript
public addOwningProperty(subscriber: IPropertySubscriber): void
```

添加持有的属性。

**起始版本：** 7

<!--Device-SubscribaleAbstract-public addOwningProperty(subscriber: IPropertySubscriber): void--><!--Device-SubscribaleAbstract-public addOwningProperty(subscriber: IPropertySubscriber): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [IPropertySubscriber](arkts-arkui-common-ts-ets-api-ipropertysubscriber-i-sys.md) | 是 | 订阅者。 |

## constructor

```TypeScript
constructor()
```

构造函数。

**起始版本：** 7

<!--Device-SubscribaleAbstract-constructor()--><!--Device-SubscribaleAbstract-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## notifyPropertyHasChanged

```TypeScript
protected notifyPropertyHasChanged(propName: string, newValue: any): void
```

当通知属性更改时调用。

**起始版本：** 7

<!--Device-SubscribaleAbstract-protected notifyPropertyHasChanged(propName: string, newValue: any): void--><!--Device-SubscribaleAbstract-protected notifyPropertyHasChanged(propName: string, newValue: any): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | 属性名称。 |
| newValue | any | 是 | 更改的新值。 |

## removeOwningProperty

```TypeScript
public removeOwningProperty(property: IPropertySubscriber): void
```

删除已拥有的属性时调用。

**起始版本：** 7

<!--Device-SubscribaleAbstract-public removeOwningProperty(property: IPropertySubscriber): void--><!--Device-SubscribaleAbstract-public removeOwningProperty(property: IPropertySubscriber): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [IPropertySubscriber](arkts-arkui-common-ts-ets-api-ipropertysubscriber-i-sys.md) | 是 | 要删除的属性。 |

## removeOwningPropertyById

```TypeScript
public removeOwningPropertyById(subscriberId: number): void
```

使用id删除已拥有的属性时调用。

**起始版本：** 7

<!--Device-SubscribaleAbstract-public removeOwningPropertyById(subscriberId: number): void--><!--Device-SubscribaleAbstract-public removeOwningPropertyById(subscriberId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriberId | number | 是 | 要删除的属性id。 |

## owningProperties_

```TypeScript
private owningProperties_: Set<number>
```

返回所持有的属性。

**类型：** Set<number>

**起始版本：** 7

<!--Device-SubscribaleAbstract-private owningProperties_: Set<number>--><!--Device-SubscribaleAbstract-private owningProperties_: Set<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

