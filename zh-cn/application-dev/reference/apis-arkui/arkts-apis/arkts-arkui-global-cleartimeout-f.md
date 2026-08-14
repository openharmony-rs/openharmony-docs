# clearTimeout

## clearTimeout

```TypeScript
export declare function clearTimeout(timeoutID?: number): void
```

取消通过调用setTimeout()建立的定时器。 定时器对象保存在创建它的线程内，删除定时器时需要在该线程中进行。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare function clearTimeout(timeoutID?: number): void--><!--Device-unnamed-export declare function clearTimeout(timeoutID?: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeoutID | number | 否 | 要取消定时器的ID，需要与调用setTimeout()设置定时器的返回值一致。 如果省略该参数或指定的定时器ID不存在时，不会取消任何定时任务。 |

