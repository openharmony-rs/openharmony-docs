# PrintPageRange

定义打印范围的接口。

**起始版本：** 11

<!--Device-print-interface PrintPageRange--><!--Device-print-interface PrintPageRange-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## endPage

```TypeScript
endPage?: number
```

表示结束页。默认值为待打印文件的最大页数。

**类型：** number

**起始版本：** 11

<!--Device-PrintPageRange-endPage?: int--><!--Device-PrintPageRange-endPage?: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pages

```TypeScript
pages?: Array<number>
```

表示待打印的页面范围的集合。默认值为空。

**类型：** Array&lt;number&gt;

**起始版本：** 11

<!--Device-PrintPageRange-pages?: Array<int>--><!--Device-PrintPageRange-pages?: Array<int>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## startPage

```TypeScript
startPage?: number
```

表示起始页。默认值为1。

**类型：** number

**起始版本：** 11

<!--Device-PrintPageRange-startPage?: int--><!--Device-PrintPageRange-startPage?: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

