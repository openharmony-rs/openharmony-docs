# enableCompatibleObservedV2ForStatic

## enableCompatibleObservedV2ForStatic

```TypeScript
export declare function enableCompatibleObservedV2ForStatic<T>(value: T): T
```

在ArkTS-Sta中引用ArkTS-Dyn中使用@ObservedV2和@Trace修饰的类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function enableCompatibleObservedV2ForStatic<T>(value: T): T--><!--Device-unnamed-export declare function enableCompatibleObservedV2ForStatic<T>(value: T): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 在ArkTS-Dyn中@ObservedV2修饰的class。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

