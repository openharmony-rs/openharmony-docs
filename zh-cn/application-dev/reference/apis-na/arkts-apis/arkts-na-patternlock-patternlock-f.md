# PatternLock

## PatternLock

```TypeScript
@ComponentBuilder
export declare function PatternLock(
    controller?: PatternLockController
): PatternLockAttribute
```

创建图案密码锁组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function PatternLock(    controller?: PatternLockController): PatternLockAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function PatternLock(    controller?: PatternLockController): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [PatternLockController](arkts-na-patternlock-patternlockcontroller-c.md) | 否 | 设置PatternLock组件控制器，可用于重置组件状态和设置图案密码的正确或错误状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PatternLockAttribute | The attribute of the PatternLock. |


## PatternLock

```TypeScript
@Builder
export declare function PatternLock(
    style: CustomBuilderT<PatternLockAttribute>,
): PatternLockAttribute
```

定义PatternLock组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function PatternLock(    style: CustomBuilderT<PatternLockAttribute>,): PatternLockAttribute--><!--Device-unnamed-@Builderexport declare function PatternLock(    style: CustomBuilderT<PatternLockAttribute>,): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;PatternLockAttribute&gt; | 是 | PatternLock属性实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PatternLockAttribute |  |

