# setGcDelay（系统接口）

## 导入模块

```TypeScript
```

## setGcDelay

```TypeScript
function setGcDelay(delay: number): void
```

设置每轮GC之间的时间间隔，单位为毫秒。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function setGcDelay(delay: int): void--><!--Device-jsLeakWatcherNative-function setGcDelay(delay: int): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delay | number | 是 | GC时间间隔。<br>单位为：毫秒。取值限定为整数。 |
