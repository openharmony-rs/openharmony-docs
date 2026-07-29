# Storage（系统接口）

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

>**说明：**
>
>本模块首批接口从API version 7开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。

## Storage

持久化存储后端接口，提供基于键值对（key-value）的数据持久化能力，包括数据的读取、写入、清除和删除。PersistentStorage通过该接口实现AppStorage数据的本地持久化，适用于需要对应用数据进行灵活本地持久化存储的场景。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(needCrossThread?: boolean, file?: string)

创建Storage实例的构造函数。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名          | 类型    | 必填 | 说明                                   |
| --------------- | ------- | ---- | -------------------------------------- |
| needCrossThread | boolean | 否   | 是否需要跨线程访问存储。预留接口，暂不提供具体功能。 |
| file            | string  | 否   | 指定存储文件名。预留接口，暂不提供具体功能。默认使用应用文件目录下的persistent_storage作为存储文件。 |

### get

get(key: string): string \| undefined

根据指定key从磁盘中读取对应的存储数据。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                    | 必填 | 说明                              |
| -------- | ----------------------- | ---- | -------------------------------- |
| key      | string                  | 是   | 要获取的存储key名称。              |

**返回值：**

| 类型      | 说明                                                      |
| --------- | -------------------------------------------------------- |
| string \| undefined | key对应的值；key不存在时返回undefined。          |

### set

set(key: string, val: any): void

将指定key对应的数据持久化存储到磁盘。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                    | 必填 | 说明                             |
| -------- | ----------------------- | ---- | ------------------------------- |
| key      | string                  | 是   | 要设置的存储key名称。             |
| val      | any                     | 是   | 要存储的数据，支持string、number、boolean等基本类型以及可序列化的对象和数组，数据将被序列化后持久化到存储文件中。                    |

### clear

clear(): void

清除所有存储数据。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### delete

delete(key: string): void

删除指定key对应的存储数据。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                    | 必填 | 说明                             |
| -------- | ----------------------- | ---- | ------------------------------- |
| key      | string                  | 是   | 要删除的存储key名称。             |
