# Storage（系统接口）

定义存储的基类

**起始版本：** 7

<!--Device-unnamed-declare class Storage--><!--Device-unnamed-declare class Storage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## clear

```TypeScript
clear(): void
```

当数据被清除时调用此方法。

**起始版本：** 7

<!--Device-Storage-clear(): void--><!--Device-Storage-clear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor(needCrossThread?: boolean, file?: string)
```

构造函数参数。

**起始版本：** 7

<!--Device-Storage-constructor(needCrossThread?: boolean, file?: string)--><!--Device-Storage-constructor(needCrossThread?: boolean, file?: string)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| needCrossThread | boolean | 否 |  |
| file | string | 否 |  |

## delete

```TypeScript
delete(key: string): void
```

当数据被删除时调用。

**起始版本：** 7

<!--Device-Storage-delete(key: string): void--><!--Device-Storage-delete(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 |  |

## get

```TypeScript
get(key: string): string | undefined
```

获取数据时调用。

**起始版本：** 7

<!--Device-Storage-get(key: string): string | undefined--><!--Device-Storage-get(key: string): string | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | @syscap SystemCapability.ArkUI.ArkUI.Full@systemapi@FaAndStageModel |

## set

```TypeScript
set(key: string, val: any): void
```

设置时调用。

**起始版本：** 7

<!--Device-Storage-set(key: string, val: any): void--><!--Device-Storage-set(key: string, val: any): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 |  |
| val | any | 是 |  |

