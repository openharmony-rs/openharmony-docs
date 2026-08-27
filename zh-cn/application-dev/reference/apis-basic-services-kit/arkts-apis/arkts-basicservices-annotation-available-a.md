# Available

```TypeScript
export @interface Available
```

提供API注解能力，用于标记API支持的最低可用版本。 此注解可以标注在类、接口、函数、变量、类型、模块、枚举上。 在源码定义处添加注解后，编译工具会在使用处检查潜在的兼容性问题。 当minApiVersion大于build-profile.json5中指定的compatibleSdkVersion字段，会生成兼容性警告。

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

minApiVersion用于标识最低可用版本，由两部分组成：系统类型+版本号。仅当系统类型为OpenHarmony时可省略系统类型。例如：'OpenHarmony 20'，'20'。 当minApiVersion大于build-profile.json5中指定的compatibleSdkVersion字段时，会生成兼容性警告。传入无效格式时，编译器会报错提示格式不正确。

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Base

**示例**

```TypeScript
import { Available, deviceInfo } from '@kit.BasicServicesKit';

@Available({minApiVersion: 'OpenHarmony 22'}) // 标记函数最低可用版本
function myFunc() {}

@Available({minApiVersion: '22'}) // 标记类最低可用版本，系统类型默认值为 OpenHarmony
class MyClass {}

// 不建议写法：如果工程根目录下build-profile.json5文件设置的compatibleSdkVersion值小于 22，直接调用myFunc方法且没有做版本判断处理，编译器会在myFunc方法调用处抛出告警，提示该方法可能在低版本设备上运行失败
myFunc();

// 建议写法1：使用deviceInfo.sdkApiVersion获取系统软件API版本进行判断，可以避免低版本设备运行异常，消除编译告警
if (deviceInfo.sdkApiVersion >= 22) {
  myFunc();
} else {
  // 根据业务逻辑选择低版本可用方法
}

// 建议写法2：在myFunc调用处的父级函数（或类）上，标记@Available起始版本信息，当新标记的版本号不低于 myFunc的最低可用版本, 消除编译告警
@Available({minApiVersion: 'OpenHarmony 22'})
function myNewFunc() {
  myFunc();
}
```
