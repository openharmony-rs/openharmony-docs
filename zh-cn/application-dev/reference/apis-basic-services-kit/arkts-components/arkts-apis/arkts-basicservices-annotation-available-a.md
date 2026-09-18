# Available

```TypeScript
export @interface Available
```

提供API注解能力，用于标记API支持的最低可用版本。此注解可以标注在类、接口、函数、变量、类型、模块、枚举上。在源码定义处添加注解后，编译工具会在使用处检查潜在的兼容性问题。当minApiVersion大于build-profile.json5中指定的compatibleSdkVersion字段，会生成兼容性警告。

**起始版本：** 22

**系统能力：** SystemCapability.Base

## 导入模块

```TypeScript
import { Available, SuppressWarnings, SuppressWarningsType } from '@kit.BasicServicesKit';
```

## minApiVersion

```TypeScript
minApiVersion: string = ''
```

minApiVersion用于标识最低可用版本，由两部分组成：系统类型+版本号。仅当系统类型为OpenHarmony时可省略系统类型。例如：'OpenHarmony 20'，'20'。当minApiVersion大于build-profile.json5中指定的compatibleSdkVersion字段时，会生成兼容性警告。传入无效格式时，编译器会报错提示格式不正确。

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Base
