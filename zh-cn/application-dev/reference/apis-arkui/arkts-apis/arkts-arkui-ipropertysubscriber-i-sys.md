# IPropertySubscriber（系统接口）

属性订阅者接口，定义订阅者需要实现的方法，用于接收属性变化通知和生命周期回调。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## aboutToBeDeleted

```TypeScript
aboutToBeDeleted(owningView?: IPropertySubscriber): void
```

销毁时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owningView | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 否 | 所在自定义组件；不传入则不指定关联的自定义组件。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let link = AppStorage.setAndLink('PropB', 49); // PropA -> 47, PropB -> 49
link.aboutToBeDeleted();
```

## id

```TypeScript
id(): number
```

获取ID时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回订阅者的唯一标识ID。 |
