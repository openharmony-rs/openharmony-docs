# OnChangeType

```TypeScript
export type OnChangeType<T> = (propertyName: string, newValue: T) => void
```

注册AppStorage/ LocalStorage中所引用属性变化事件的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnChangeType<T> = (propertyName: string, newValue: T) => void--><!--Device-unnamed-export type OnChangeType<T> = (propertyName: string, newValue: T) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | property name |
| newValue | T | 是 | the new value of state variable |

