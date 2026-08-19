# JsRawHeapTrimLevel

转储堆快照的裁剪级别的枚举。 TRIM_LEVEL_2相比TRIM_LEVEL_1，裁剪时间更长。冻屏的阈值为6秒。使用TRIM_LEVEL_1时，不会达到该阈值；切换至TRIM_LEVEL_2时，裁剪时间可能会超过6秒，触发APP_FREEZE（冻屏事件），导致应用被系统终止，此时回退至TRIM_LEVEL_1级别进行裁剪。 推荐优先使用TRIM_LEVEL_1确保应用稳定，仅在需要更彻底裁剪时尝试TRIM_LEVEL_2。

**起始版本：** 26.1.0

<!--Device-hidebug-enum JsRawHeapTrimLevel--><!--Device-hidebug-enum JsRawHeapTrimLevel-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## TRIM_LEVEL_1

```TypeScript
TRIM_LEVEL_1 = 0
```

LEVEL 1级别裁剪，主要裁剪字符串。

**起始版本：** 26.1.0

<!--Device-JsRawHeapTrimLevel-TRIM_LEVEL_1 = 0--><!--Device-JsRawHeapTrimLevel-TRIM_LEVEL_1 = 0-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## TRIM_LEVEL_2

```TypeScript
TRIM_LEVEL_2 = 1
```

LEVEL 2级别裁剪，在TRIM_LEVEL_1的基础上，精简了对象地址标识的大小，从8个字节减少到4个字节。

**起始版本：** 26.1.0

<!--Device-JsRawHeapTrimLevel-TRIM_LEVEL_2 = 1--><!--Device-JsRawHeapTrimLevel-TRIM_LEVEL_2 = 1-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

