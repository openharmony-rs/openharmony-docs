# PpdInfo

定义打印机所使用驱动的PPD文件信息的接口。

**起始版本：** 24

<!--Device-print-interface PpdInfo--><!--Device-print-interface PpdInfo-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## manufacturer

```TypeScript
manufacturer: string
```

表示当前PPD文件内的打印机厂商名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PpdInfo-manufacturer: string--><!--Device-PpdInfo-manufacturer: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## nickName

```TypeScript
nickName: string
```

表示当前PPD文件内的打印机别名。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PpdInfo-nickName: string--><!--Device-PpdInfo-nickName: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## ppdName

```TypeScript
ppdName: string
```

表示当前PPD文件的名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PpdInfo-ppdName: string--><!--Device-PpdInfo-ppdName: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

