# Processor

可以上报事件的数据处理者对象。用于事件的上报和管理，开发者可自定义数据处理配置，满足不同的数据处理需求。

**起始版本：** 11

<!--Device-hiAppEvent-interface Processor--><!--Device-hiAppEvent-interface Processor-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## appId

```TypeScript
appId?: string
```

应用id，默认为空字符串。传入字符串长度不能超过8KB，超过时会被置为默认值。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-appId?: string--><!--Device-Processor-appId?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## batchReport

```TypeScript
batchReport?: number
```

事件上报阈值，当事件条数达到阈值时上报事件。传入数值必须大于0且小于1000，不在数值范围内会被置为默认值0，不进行上报。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-batchReport?: int--><!--Device-Processor-batchReport?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## configId

```TypeScript
configId?: number
```

数据处理者配置id。传入数值必须大于或等于0，小于0时会被置为默认值0。传入的值大于0时，与数据处理者的名称name共同唯一标识数据处理者。

**原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-configId?: int--><!--Device-Processor-configId?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## configName

```TypeScript
configName?: string
```

数据处理者的配置名称，支持从配置文件中加载对应配置，默认为空。只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。

**原子化服务API：** 从API version 20开始，该参数支持在原子化服务中使用。

**类型：** string

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-configName?: string--><!--Device-Processor-configName?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## customConfigs

```TypeScript
customConfigs?: Record<string, string>
```

自定义扩展参数。传入参数名和参数值不符合规格会默认不配置扩展参数，其规格定义如下：

- 参数名为string类型，首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过32个字符。  
- 参数值为string类型，参数值长度需在1024个字符以内。  
- 参数个数需在32个以内。

元服务API： 从API version 12开始，该参数支持在元服务中使用。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-customConfigs?: Record<string, string>--><!--Device-Processor-customConfigs?: Record<string, string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## debugMode

```TypeScript
debugMode?: boolean
```

是否开启debug模式，默认值为false。配置值为true表示开启debug模式，false表示不开启debug模式。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-debugMode?: boolean--><!--Device-Processor-debugMode?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## eventConfigs

```TypeScript
eventConfigs?: AppEventReportConfig[]
```

数据处理者可以上报的事件描述配置数组。默认为空数组。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** AppEventReportConfig[]

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-eventConfigs?: AppEventReportConfig[]--><!--Device-Processor-eventConfigs?: AppEventReportConfig[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name: string
```

数据处理者的名称。名称只能包含大小写字母、数字、下划线和 $，不能以数字开头，长度非空且不超过256个字符。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-name: string--><!--Device-Processor-name: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## onBackgroundReport

```TypeScript
onBackgroundReport?: boolean
```

当应用程序进入后台时是否上报事件，默认值为false。配置值为true表示上报事件，false表示不上报事件。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-onBackgroundReport?: boolean--><!--Device-Processor-onBackgroundReport?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## onStartReport

```TypeScript
onStartReport?: boolean
```

数据处理者在启动时是否上报事件，默认值为false。配置值为true表示上报事件，false表示不上报事件。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-onStartReport?: boolean--><!--Device-Processor-onStartReport?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## periodReport

```TypeScript
periodReport?: number
```

事件定时上报时间周期，单位为秒。传入数值必须大于或等于0，小于0时会被置为默认值0，不进行定时上报。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-periodReport?: int--><!--Device-Processor-periodReport?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## routeInfo

```TypeScript
routeInfo?: string
```

服务器位置信息，默认为空字符串。传入字符串长度不能超过8KB，超过时会被置为默认值。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-routeInfo?: string--><!--Device-Processor-routeInfo?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## userIds

```TypeScript
userIds?: string[]
```

数据处理者可以上报的用户ID的name数组。name对应[setUserId](arkts-performanceanalysis-hiappevent-setuserid-f.md#setuserid-1)接口的name参数。默认为空数组。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string[]

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-userIds?: string[]--><!--Device-Processor-userIds?: string[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## userProperties

```TypeScript
userProperties?: string[]
```

数据处理者可以上报的用户属性的name数组。name对应[setUserProperty](arkts-performanceanalysis-hiappevent-setuserproperty-f.md#setuserproperty-1)接口的name参数。默认为空数组。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string[]

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Processor-userProperties?: string[]--><!--Device-Processor-userProperties?: string[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

