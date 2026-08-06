# offDensityUpdate

## offDensityUpdate

```TypeScript
export function offDensityUpdate(context: UIContext, callback?: Callback<DensityInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offDensityUpdate(context: UIContext, callback?: Callback<DensityInfo>): void--><!--Device-uiObserver-export function offDensityUpdate(context: UIContext, callback?: Callback<DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The context scope of the observer. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DensityInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

