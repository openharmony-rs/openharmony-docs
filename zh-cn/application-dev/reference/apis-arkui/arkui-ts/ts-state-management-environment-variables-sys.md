# 内置环境变量说明（系统接口）

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

持久化存储后端接口，提供基于键值对（key-value）的数据持久化能力，包括数据的读取、写入、清除和删除，支持自定义存储文件路径和跨线程安全访问。PersistentStorage通过该接口实现AppStorage数据的本地持久化，适用于需要对应用数据进行灵活本地持久化存储的场景。

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
| needCrossThread | boolean | 否   | 是否需要跨线程访问存储。取值为true时，实例支持跨线程读写，框架以线程安全方式处理存储访问；取值为false时，仅在创建线程（通常为主线程）内访问。<br>默认值：false。 |
| file            | string  | 否   | 指定存储文件名。默认使用应用文件目录下的persistent_storage作为存储文件。 |

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

将指定key对应的数据持久化存储到磁盘。若Storage实例创建时needCrossThread为false，本方法仅可在创建线程（通常为主线程）内调用。

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
