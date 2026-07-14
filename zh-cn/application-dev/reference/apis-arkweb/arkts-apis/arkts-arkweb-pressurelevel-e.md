# PressureLevel

内存压力等级。在应用主动清理Web组件占用的缓存时，Web内核会根据内存压力等级，进行缓存释放。

**起始版本：** 14

**系统能力：** SystemCapability.Web.Webview.Core

## MEMORY_PRESSURE_LEVEL_MODERATE

```TypeScript
MEMORY_PRESSURE_LEVEL_MODERATE = 1
```

中等内存压力等级。这个等级下，Web内核会尝试释放重新分配开销较小且不需要立即使用的缓存。

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## MEMORY_PRESSURE_LEVEL_CRITICAL

```TypeScript
MEMORY_PRESSURE_LEVEL_CRITICAL = 2
```

严重内存压力等级。这个等级下，Web内核会尝试释放所有可能的内存缓存。

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

