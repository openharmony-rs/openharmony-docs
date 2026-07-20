# PrintAttributes

定义打印参数的接口。

**起始版本：** 11

<!--Device-print-interface PrintAttributes--><!--Device-print-interface PrintAttributes-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## colorMode

```TypeScript
colorMode?: PrintColorMode
```

表示待打印文件的色彩模式。

**类型：** PrintColorMode

**起始版本：** 11

<!--Device-PrintAttributes-colorMode?: PrintColorMode--><!--Device-PrintAttributes-colorMode?: PrintColorMode-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber?: number
```

表示文件打印份数。默认值为1。

**类型：** number

**起始版本：** 11

<!--Device-PrintAttributes-copyNumber?: int--><!--Device-PrintAttributes-copyNumber?: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## directionMode

```TypeScript
directionMode?: PrintDirectionMode
```

表示待打印文件的方向。

**类型：** PrintDirectionMode

**起始版本：** 11

<!--Device-PrintAttributes-directionMode?: PrintDirectionMode--><!--Device-PrintAttributes-directionMode?: PrintDirectionMode-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode?: PrintDuplexMode
```

表示待打印文件的单双面模式。

**类型：** PrintDuplexMode

**起始版本：** 11

<!--Device-PrintAttributes-duplexMode?: PrintDuplexMode--><!--Device-PrintAttributes-duplexMode?: PrintDuplexMode-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pageRange

```TypeScript
pageRange?: PrintPageRange
```

表示待打印文件的页面范围。

**类型：** PrintPageRange

**起始版本：** 11

<!--Device-PrintAttributes-pageRange?: PrintPageRange--><!--Device-PrintAttributes-pageRange?: PrintPageRange-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize?: PrintPageSize | PrintPageType
```

表示待打印文件的纸张类型。

**类型：** PrintPageSize \| PrintPageType

**起始版本：** 11

<!--Device-PrintAttributes-pageSize?: PrintPageSize | PrintPageType--><!--Device-PrintAttributes-pageSize?: PrintPageSize | PrintPageType-End-->

**系统能力：** SystemCapability.Print.PrintFramework

