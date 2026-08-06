# clearInterval

## clearInterval

```TypeScript
function clearInterval(timerId?: int | null): void
```

取消指定的定时器。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-function clearInterval(timerId?: int | null): void--><!--Device-unnamed-function clearInterval(timerId?: int | null): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timerId | int \| null | 否 | 由setInterval返回的定时器ID，如果不传、传入null或undefined，则不执行任何操作。 |

