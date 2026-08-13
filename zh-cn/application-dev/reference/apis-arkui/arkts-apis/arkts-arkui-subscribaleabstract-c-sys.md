# SubscribaleAbstract（系统接口）

可订阅抽象类，用于管理所持有的属性集合，提供属性的添加、删除和变更通知能力。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare abstract class SubscribaleAbstract--><!--Device-unnamed-declare abstract class SubscribaleAbstract-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## addOwningProperty

```TypeScript
public addOwningProperty(subscriber: IPropertySubscriber): void
```

添加持有的属性。属性不再使用时，应调用[removeOwningProperty](#removeOwningProperty) 或[removeOwningPropertyById](#removeOwningPropertyById)移除。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SubscribaleAbstract-public addOwningProperty(subscriber: IPropertySubscriber): void--><!--Device-SubscribaleAbstract-public addOwningProperty(subscriber: IPropertySubscriber): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 是 | 要添加的订阅者，该订阅者将接收属性变化通知。 |

## constructor

```TypeScript
constructor()
```

构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SubscribaleAbstract-constructor()--><!--Device-SubscribaleAbstract-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## notifyPropertyHasChanged

```TypeScript
protected notifyPropertyHasChanged(propName: string, newValue: any): void
```

通知属性更改时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SubscribaleAbstract-protected notifyPropertyHasChanged(propName: string, newValue: any): void--><!--Device-SubscribaleAbstract-protected notifyPropertyHasChanged(propName: string, newValue: any): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | 要通知变更的属性名称。 |
| newValue | any | 是 | 更改后的新值。 |

## removeOwningProperty

```TypeScript
public removeOwningProperty(property: IPropertySubscriber): void
```

使用ID删除持有的属性时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SubscribaleAbstract-public removeOwningProperty(property: IPropertySubscriber): void--><!--Device-SubscribaleAbstract-public removeOwningProperty(property: IPropertySubscriber): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 是 | 要删除的订阅者， 需为已通过[addOwningProperty](#addOwningProperty)添加的订阅者。 |

## removeOwningPropertyById

```TypeScript
public removeOwningPropertyById(subscriberId: number): void
```

使用ID删除持有的属性时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SubscribaleAbstract-public removeOwningPropertyById(subscriberId: number): void--><!--Device-SubscribaleAbstract-public removeOwningPropertyById(subscriberId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriberId | number | 是 | 要删除的订阅者ID， 需为已通过[addOwningProperty](#addOwningProperty)添加的订阅者ID， 通过[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md#IPropertySubscriber（系统接口）).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)方法获取。 |

## owningProperties_

```TypeScript
private owningProperties_: Set<number>
```

所持有的属性集合。

**类型：** Set&lt;number&gt;

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SubscribaleAbstract-private owningProperties_: Set<number>--><!--Device-SubscribaleAbstract-private owningProperties_: Set<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

