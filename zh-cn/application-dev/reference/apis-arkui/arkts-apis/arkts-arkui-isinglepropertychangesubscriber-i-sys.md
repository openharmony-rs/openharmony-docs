# ISinglePropertyChangeSubscriber（系统接口）

继承自[IPropertySubscriber]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。用于订阅单个属性值的变化，当被订阅的属性发生变化时接收通知。

**继承/实现关系：** ISinglePropertyChangeSubscriber extends [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md)

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-interface ISinglePropertyChangeSubscriber<T> extends IPropertySubscriber--><!--Device-unnamed-interface ISinglePropertyChangeSubscriber<T> extends IPropertySubscriber-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

变化时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-ISinglePropertyChangeSubscriber-hasChanged(newValue: T): void--><!--Device-ISinglePropertyChangeSubscriber-hasChanged(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 更改后的新值。 |

