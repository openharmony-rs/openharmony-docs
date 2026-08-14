# PromisifiedFunc

```TypeScript
type PromisifiedFunc =  (...args: FixedArray<Any>) => Promise<Any>
```

The type of promisify return function

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-type PromisifiedFunc =  (...args: FixedArray<Any>) => Promise<Any>--><!--Device-util-type PromisifiedFunc =  (...args: FixedArray<Any>) => Promise<Any>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | FixedArray&lt;Any&gt; | 是 | arguments to be passed |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Any&gt; | a promise value |

