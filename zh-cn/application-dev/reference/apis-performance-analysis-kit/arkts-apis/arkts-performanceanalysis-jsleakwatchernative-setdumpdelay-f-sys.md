# setDumpDelay（系统接口）

## 导入模块

```TypeScript
```

## setDumpDelay

```TypeScript
function setDumpDelay(delay: number): void
```

设置GC后执行dump之前的延迟时间，单位为毫秒。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function setDumpDelay(delay: int): void--><!--Device-jsLeakWatcherNative-function setDumpDelay(delay: int): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delay | number | 是 | 转储延迟。<br>单位为：毫秒。取值限定为整数。 |
