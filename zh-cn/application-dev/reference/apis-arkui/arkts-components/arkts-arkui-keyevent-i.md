# KeyEvent

按键事件信息。

**起始版本：** 7

<!--Device-unnamed-declare interface KeyEvent--><!--Device-unnamed-declare interface KeyEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?(keys: Array<string>): boolean
```

获取功能键按压状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-getModifierKeyState?(keys: Array<string>): boolean--><!--Device-KeyEvent-getModifierKeyState?(keys: Array<string>): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 是 | 功能键列表。支持功能键 'Ctrl'\| 'Alt' \| 'Shift'。<br/>**说明：**<br/>此接口不支持在手写笔场景下使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 功能键是否被按下。true表示被按下，false表示未被按下。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |

## deviceId

```TypeScript
deviceId: number
```

触发当前按键的输入设备ID。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-deviceId: number--><!--Device-KeyEvent-deviceId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## intentionCode

```TypeScript
intentionCode: IntentionCode
```

按键对应的意图。

默认值：IntentionCode.INTENTION_UNKNOWN。

**类型：** IntentionCode

**默认值：** IntentionCode.INTENTION_UNKNOWN

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-intentionCode: IntentionCode--><!--Device-KeyEvent-intentionCode: IntentionCode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCapsLockOn

```TypeScript
isCapsLockOn?: boolean
```

CapsLock是否锁定（true: 锁定；false: 解锁）。

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-isCapsLockOn?: boolean--><!--Device-KeyEvent-isCapsLockOn?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isNumLockOn

```TypeScript
isNumLockOn?: boolean
```

NumLock是否锁定（true: 锁定；false: 解锁）。

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-isNumLockOn?: boolean--><!--Device-KeyEvent-isNumLockOn?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isScrollLockOn

```TypeScript
isScrollLockOn?: boolean
```

ScrollLock是否锁定（true: 锁定；false: 解锁）。

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-isScrollLockOn?: boolean--><!--Device-KeyEvent-isScrollLockOn?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyCode

```TypeScript
keyCode: number
```

按键的键值。按键设备提供的键值请参考[KeyCode](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keycode-keycode-e.md)。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-keyCode: number--><!--Device-KeyEvent-keyCode: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keySource

```TypeScript
keySource: KeySource
```

触发当前按键的输入设备类型。

**类型：** KeySource

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-keySource: KeySource--><!--Device-KeyEvent-keySource: KeySource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyText

```TypeScript
keyText: string
```

按键的名称。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-keyText: string--><!--Device-KeyEvent-keyText: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## metaKey

```TypeScript
metaKey: number
```

按键发生时元键（即键盘左下角紧挨Ctrl键或Fn标记了窗口logo的按键）的状态，1表示按压态，0表示未按压态。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-metaKey: number--><!--Device-KeyEvent-metaKey: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: () => void
```

阻塞[事件冒泡](../../../ui/arkts-interaction-basic-principles.md#事件冒泡)传递。

**类型：** () =&gt; void

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-stopPropagation: () => void--><!--Device-KeyEvent-stopPropagation: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

事件时间戳。触发事件时距离系统启动的时间间隔，单位：ns。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-timestamp: number--><!--Device-KeyEvent-timestamp: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: KeyType
```

按键的类型。

**类型：** KeyType

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-type: KeyType--><!--Device-KeyEvent-type: KeyType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unicode

```TypeScript
unicode?: number
```

按键的Unicode码值。支持范围为非空格的基本拉丁字符：0x0021-0x007E，不支持字符为0。组合键场景下，返回当前keyEvent对应按键的Unicode码值。

**类型：** number

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-KeyEvent-unicode?: number--><!--Device-KeyEvent-unicode?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

