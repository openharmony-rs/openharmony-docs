# 使用 IDL 实现 ModularObjectExtensionAbility 的 IPC 通信

## 1. 使用场景

通过 IDL 工具可自动生成 ModularObjectExtensionAbility 所需的 Proxy/Stub 代码及类型库文件，屏蔽 IPC通信底层细节（如参数序列化/反序列化、消息码分发等），使开发者专注于接口设计与业务逻辑，大幅简化ModularObjectExtensionAbility的开发流程。

## 2. 名词解释

| 术语 | 说明 |
| --- | --- |
| **Taihe** | 面向 OpenHarmony 生态的跨语言接口定义与代码生成工具，用于从 `.taihe` 文件生成跨语言、跨模块的接口胶水层代码 |
| **IDL** | 接口定义语言，用于声明接口、结构体、枚举、函数参数和返回值类型，以及注解和调用约束 |
| **Proxy** | 客户端代理对象，负责序列化请求、发送 IPC 消息、解析返回值 |
| **Stub** | 服务端桩对象，负责反序列化请求、调用真实实现、写回响应数据 |

## 3. 前置条件

### 3.1 软件依赖

- **Python**：3.11.4 及以上

### 3.2 工程依赖

- OpenHarmony SDK（API 26+）

### 3.3 命令行使用

Taihe 提供了核心编译器工具 `taihec`，用于解析 Taihe IDL 文件并编译为目标语言代码。<br>
安装对应的 wheel 包后，开发者可直接指定 `modobj-ipc` 后端生成 ModularObjectExtensionAbility客户端和服务端IPC通信所需的 Proxy、Stub 和类型库文件。

```bash
taihec [taihe_files ...] [options ...]
```

- `taihe_files`：可以是一个或多个 Taihe IDL 文件，主接口文件和公共类型文件需一并列出。
- `options`：用于指定代码生成的各种选项。

**常用选项**

| 参数 | 简写 | 说明 |
| --- | --- | --- |
| `--output <path>` | `-O <path>` | 指定生成的目标文件存放目录 |
| `--generate <backend>` | `-G <backend>` | 指定代码生成后端，ModularObjectExtensionAbilityIPC通信场景下使用 `modobj-ipc` |
| `--codegen <namespace>:<config>[=<value>]` | `-C <namespace>:<config>[=<value>]` | 指定后端配置，例如 `modobj:ipc-common=common.ohidl` 用于引入公共类型文件 |

**执行代码生成示例**

主接口文件引用了其他文件中的类型，使用 -C 参数来引用公共数据类型
```bash
taihec
-G modobj-ipc
-O example/generated/IBasicTypes_ohidl_c
-C modobj:ipc-common=example/ExampleServiceIpcTypes.ohidl
example/IBasicTypes.ohidl
```
所有类型都定义在主接口文件中，无需引用其他文件
```bash
taihec
-G modobj-ipc
-O example/generated
example/Easy.ohidl
```

## 4. 开发规范

### 4.1 Taihe IDL 语言规范

**文件组织**

- **主接口文件**：定义服务核心接口，使用 `@main_service` 标记
- **公共类型文件**：定义结构体、枚举，通过 from ... use ... 复用

**参数与返回值约定**

- 方法参数统一视为输入参数
- 输出结果统一通过返回值表达
- 需要返回多个字段时，用 `struct` 作为返回值封装

### 4.2 基础示例

主接口文件 `Easy.ohidl`：

<!-- @[easy](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampleone/example/Easy.ohidl) -->
```rust
@!namespace("OHOS", "IPC")

@main_service(version = "1.0.0")
interface ICalculator {
    Add(a: i32, b: i32): i32;
}
```

### 4.3 生成代码解析

| 文件名 | 说明 |
| --- | --- |
| `icalculator.h` | 纯虚接口定义头文件 |
| `calculator_proxy.h` | 客户端代理类声明 |
| `calculator_proxy.cpp` | 代理实现，负责参数序列化、发送 IPC 请求、解析返回值 |
| `calculator_stub.h` | 服务端 Stub 类声明 |
| `calculator_stub.cpp` | Stub 实现，负责反序列化请求、调用业务实现、写回响应 |
| `calculator.typelib.json` | 接口元数据描述文件 |

**icalculator.h**
- `GetDescriptor()` 返回接口描述符字符串
- `IpcCode` 枚举为每个方法分配唯一命令码
- 仅声明接口，不包含实现
<!-- @[ICalculator](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampleone/generated/icalculator.h) -->
```cpp
class ICalculator {
public:
    virtual ~ICalculator() = default;
    static const char* GetDescriptor() { return "OHOS.IPC.ICalculator"; }

    enum class IpcCode : uint32_t {
        COMMAND_ADD = 1001,
        COMMAND_GET_TYPE_LIB_INFO = 1,
        COMMAND_GET_VERSION = 2,
        COMMAND_GET_TAIHE_VERSION = 3,
    };

    virtual ErrCode Add(int32_t a, int32_t b, int32_t& result) = 0;
    virtual ErrCode GetTypeLibInfo(int32_t fd) = 0;
    virtual ErrCode GetVersion(std::string& result) = 0;
    virtual ErrCode GetTaiheVersion(std::string& result) = 0;
};
```

**calculator_proxy.h**
- `CalculatorProxy` 继承 `ICalculator`
- 包含远端句柄 `remote_`
- 每个接口方法都对应一个代理实现
<!-- @[CalculatorProxy](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampleone/generated/calculator_proxy.h) -->
```cpp
class CalculatorProxy : public ICalculator {
public:
    explicit CalculatorProxy(OHIPCRemoteProxy* remote) : remote_(remote) {}
    ~CalculatorProxy() override = default;

    ErrCode Add(int32_t a, int32_t b, int32_t& result) override;
private:
    OHIPCRemoteProxy* remote_ = nullptr;
};
```

**calculator_proxy.cpp**
- 创建 `OHIPCParcel` 请求包和响应包
- 写入接口令牌，序列化方法参数
- 调用 `OH_IPCRemoteProxy_SendRequest()` 发起同步 IPC
- 读取 `reply` 中的错误码与返回值
<!-- @[CalculatorProxy](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampleone/generated/calculator_proxy.cpp) -->
```cpp
ErrCode CalculatorProxy::Add(int32_t a, int32_t b, int32_t& result)
{
  std::unique_ptr<OHIPCParcel, ParcelDeleter> parcelData(OH_IPCParcel_Create());
  std::unique_ptr<OHIPCParcel, ParcelDeleter> parcelReply(OH_IPCParcel_Create());
  if (OH_IPCParcel_WriteInterfaceToken(parcelData.get(),
      ICalculator::GetDescriptor()) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_WRITE_ERROR;
  }

  if (OH_IPCParcel_WriteInt32(parcelData.get(), a) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_WRITE_ERROR;
  }

  if (OH_IPCParcel_WriteInt32(parcelData.get(), b) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_WRITE_ERROR;
  }

  int32_t transportErr = OH_IPCRemoteProxy_SendRequest(
      remote_,
      static_cast<uint32_t>(ICalculator::IpcCode::COMMAND_ADD),
      parcelData.get(),
      parcelReply.get(),
      &option);

  int32_t errCode = OH_IPC_SUCCESS;
  if (OH_IPCParcel_ReadInt32(parcelReply.get(), &errCode) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_READ_ERROR;
  }
  if (errCode != OH_IPC_SUCCESS) {
      return errCode;
  }

  int32_t resultValue = 0;
  if (OH_IPCParcel_ReadInt32(parcelReply.get(), &resultValue) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_READ_ERROR;
  }
  result = resultValue;

  return OH_IPC_SUCCESS;
}
```

**calculator_stub.h**
- `CalculatorStub` 继承 `ICalculator`
- `OnRemoteRequest` 作为 IPC 调用入口
- `OnRemoteRequestInner` 根据 `code` 分发到具体 `HandleXXX` 方法
<!-- @[CalculatorStub](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampleone/generated/calculator_stub.h) -->
```cpp
class CalculatorStub : public ICalculator {
public:
    static int32_t OnRemoteRequest(uint32_t code,
      const OHIPCParcel* data,
      OHIPCParcel* reply,
      void* userData);
private:
    int32_t OnRemoteRequestInner(uint32_t code, const OHIPCParcel* data, OHIPCParcel* reply);
    int32_t HandleAdd(const OHIPCParcel* data, OHIPCParcel* reply);
};
```

**calculator_stub.cpp**
  - 先校验接口令牌，确保请求目标正确。
  - `HandleAdd` 从 `data` 中读取参数，调用真实 `Add` 业务实现。
  - 将 `errCode` 和结果写回 `reply`。
<!-- @[CalculatorStub](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampleone/generated/calculator_stub.cpp) -->
```cpp
int32_t CalculatorStub::OnRemoteRequestInner(uint32_t code, const OHIPCParcel* data, OHIPCParcel* reply)
{
  if (OH_IPCParcel_ReadInterfaceToken(data, &remoteDescriptor,
      &remoteDescriptorLen, OhipcReadInterfaceTokenAllocator) != OH_IPC_SUCCESS) {
      return OH_IPC_CHECK_PARAM_ERROR;
  }
  switch (static_cast<ICalculator::IpcCode>(code)) {
      case ICalculator::IpcCode::COMMAND_ADD:
          return HandleAdd(data, reply);

        default:
            return OH_IPC_CHECK_PARAM_ERROR;
    }
}

int32_t CalculatorStub::HandleAdd(const OHIPCParcel* data, OHIPCParcel* reply)
{
  int32_t aValue = 0;
  if (OH_IPCParcel_ReadInt32(data, &aValue) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_READ_ERROR;
  }
  int32_t a = aValue;
  
  int32_t result;
  ErrCode errCode = Add(a, b, result);
  if (OH_IPCParcel_WriteInt32(reply, errCode) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_WRITE_ERROR;
  }
  if (errCode != OH_IPC_SUCCESS) {
      return OH_IPC_SUCCESS;
  }

  if (OH_IPCParcel_WriteInt32(reply, result) != OH_IPC_SUCCESS) {
      return OH_IPC_PARCEL_WRITE_ERROR;
  }
  return OH_IPC_SUCCESS;
}
```

**calculator.typelib.json**
  - 保存接口名称、描述符、方法名、IPC code、参数与返回类型。
  - 用于运行时查询方法元数据和动态路由。
```json
{
  "version": "1.0",
  "taihe_version": "1.0.0",
  "enums": [],
  "structs": [],
  "interfaces": [
    {
      "memberId": 1,
      "name": "ICalculator",
      "descriptor": "OHOS.IPC.ICalculator",
      "interface_type": 1,
      "methods": [
        {
          "memberId": 4,
          "name": "Add",
          "code": 1001,
          "oneway": false,
          "return_type": {
            "type": "i32"
          },
          "parameters": [
            {
              "memberId": 2,
              "name": "a",
              "type_info": {
                "type": "i32"
              }
            },
            {
              "memberId": 3,
              "name": "b",
              "type_info": {
                "type": "i32"
              }
            }
          ]
        }
      ]
    }
  ]
}
```

除定义接口外 IDL 会自动生成 `GetTypeLibInfo`、`GetVersion`、`GetTaiheVersion` ：

| 方法              | 默认行为                                                                         |
| :---              | :---                                                                            |
| `GetTypeLibInfo`  | 提供类型库信息，`@callback` 标记的接口不自动生成，仅 `@main_service` 标记的接口生成  |
| `GetVersion`      | 返回 `@main_service` 注解中 version 声明的版本号                                  |
| `GetTaiheVersion` | 返回插件读取到的 Taihe 版本                                                       |

### 4.4 基础数据类型使用规范

**基础类型**：

| Taihe IDL | C++ 类型   | Parcel 写入/读取规则                                         |
| :-------  | :------    | :--------------------------------------------------------   |
| `bool`    | `bool`     | `OH_IPCParcel_WriteInt32`   / `OH_IPCParcel_ReadInt32`      |
| `i8`      | `int8_t`   | `OH_IPCParcel_WriteInt8`    / `OH_IPCParcel_ReadInt8`       |
| `i16`     | `int16_t`  | `OH_IPCParcel_WriteInt16`   / `OH_IPCParcel_ReadInt16`      |
| `i32`     | `int32_t`  | `OH_IPCParcel_WriteInt32`   / `OH_IPCParcel_ReadInt32`      |
| `i64`     | `int64_t`  | `OH_IPCParcel_WriteInt64`   / `OH_IPCParcel_ReadInt64`      |
| `f32`     | `float`    | `OH_IPCParcel_WriteFloat`   / `OH_IPCParcel_ReadFloat`      |
| `f64`     | `double`   | `OH_IPCParcel_WriteDouble`  / `OH_IPCParcel_ReadDouble`     |
| `u8`      | `uint8_t`  | `OH_IPCParcel_WriteUint8_t` / `OH_IPCParcel_ReadUint8_t`    |
| `u16`     | `uint16_t` | `OH_IPCParcel_WriteUint16_t`/ `OH_IPCParcel_ReadUint16_t`   |
| `u32`     | `uint32_t` | `OH_IPCParcel_WriteUint32_t`/ `OH_IPCParcel_ReadUint32_t`   |
| `u64`     | `uint64_t` | `OH_IPCParcel_WriteUint64_t`/ `OH_IPCParcel_ReadUint64_t`   |

### 4.5 注解与使用

**核心注解**：

| 注解                             | 作用范围   |说明                                    | 示例                               |                   
| :---                             | :---       | :---                                  | :---                               |                     
| `@main_service(version="x.y.z")` | 接口     | 声明主服务接口，有且只有一个，生成的Stub用于在[OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc](../reference/apis-ability-kit/capi-modular-object-extension-ability-h.md#OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc())中返回   | @main_service(version="1.0.0")    |
| `@callback`                      | 方法       | 回调接口在客户端执行，不跟随服务端的线程模型 | @callback interface ICallback {}  |
| `@oneway`                        | 方法       | 异步单向IPC调用，仅支持void类型返回值       | @oneway Notify(...): void;        |
| `@!namespace("A","B")`           | 命名空间   | 设置生成的代码所在命名空间，以及IPC接口描述符字符串前缀 | @!namespace("OHOS","NativeApp")   |
| `@size(N)`                       | 类型       | 定长数组的大小，该注解仅供Array使用      | @size(4) Array<i32>;              |

### 4.6 复杂数据类型使用规范

**复杂类型**：

| Taihe IDL           | C++ 类型                     | Parcel 写入/读取规则                                                         |
| :---                | :---                         | :---                                                                        |
| `String`            | `std::string`                | 转为 `const char*` 后 `OH_IPCParcel_WriteString` / `OH_IPCParcel_ReadString` |
| `enum`              | `enum`                       | 按 `int32_t` 序列化                                                          |
| `Vector<T>`         | `std::vector<T>`             | 先写 size，再逐项序列化                                                       |
| `@size(N) Array<T>` | `std::array<T, N>`           | 先写 size，再逐项序列化                                                       |
| `Set<T>`            | `std::set<T>`                | 先写 size，再逐项序列化                                                       |
| `Map<K,V>`          | `std::map<K, V>`             | 先写 size，再顺序写入 key/value                                               |
| `struct`            | `struct&`                    | 调用生成的 `Marshalling/Unmarshalling`                                        |
| `interface`         | `interface&`                 | 写入 `OHIPCRemoteStub` 或 `OHIPCRemoteProxy`，读取 `OHIPCRemoteProxy`         |


### 4.7 约束与限制

- `Map<K, V>` 的键类型仅支持基础类型、`String`、`enum`
- 多个版本间定义方法不能改变顺序
- 同一次 `modobj-ipc` 生成中，只要有 `interface`、 `struct`、 `enum` 名称重复，就会报错并停止生成
- 不同命名空间下同名也会拦截

## 5. 开发步骤

### 5.1 编写 IDL 文件

首先用户需在自定义路径下创建主接口文件与公共类型文件

**场景一：基础方法调用与数据传输**

公共类型文件 `ExampleServiceIpcTypes.ohidl`：

<!-- @[ExampleServiceIpcTypes](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampletwo/example/ExampleServiceIpcTypes.ohidl) -->
```rust
@!namespace("OHOS", "IPC")

enum Color : i64{
    RED = 0,
    GREEN = 1,
    BLUE = 2
}

struct Point {
    x: i32;
    y: i32;
}
```

主接口文件 `IBasicTypes.ohidl`：

<!-- @[IBasicTypes](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/exampletwo/example/IBasicTypes.ohidl) -->
```rust
@!namespace("OHOS", "IPC")
from ExampleServiceIpcTypes use Point, Color;

@main_service(version = "1.0.0")
interface BasicTypes {

    Type_bool(a: bool): bool;
    Type_i8(a: i8): i8;
    Type_i16(a: i16): i16;
    Type_i32(a: i32): i32;
    Type_i64(a: i64): i64;
    Type_u8(a: u8): u8;
    Type_u16(a: u16): u16;
    Type_u32(a: u32): u32;
    Type_u64(a: u64): u64;
    Type_f32(a: f32): f32;
    Type_f64(a: f64): f64;
    Type_String(a: String): String;
    Type_void(): void;
    Type_enum(a:Color): Color;
    Type_struct(a: Point): Point;
    Type_Array1(values: @size(4) Array<i32>): @size(4) Array<i32>;
    Type_Vector(a: Vector<i32>): Vector<i32>;
    Type_Set(a: Set<i32>): Set<i32>;
    Type_Map(a: Map<String, i32>): Map<String, i32>;
}
```

**场景二：客户端注册回调**

 <!-- @[callback](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/examplethree/example/ITestInterface.ohidl) -->
```rust
struct OnProgressResult {
    summary: String;
}

@callback
interface ITestEventCallback {
    OnConnected(clientId: i32, welcome: String): void;
    OnProgress(taskId: i32): OnProgressResult;

    @oneway
    OnDisconnected(reason: String): void;
}

interface ITestCallbackService {
    RegisterCallback(callback: ITestEventCallback): i32;
}
```

**场景三：服务端返回接口**

<!-- @[service](https://gitcode.com/openharmony/applications_app_samples/blob/cac36e5b441e109a6a6964382fe7d8fe2a4b03f0/code/DocsSample/Ability/ModularObjectExtensionAbilityIDL/examplethree/example/ITestInterface.ohidl) -->
```rust
interface TestType_interface {
    GetId(): i64;
}
interface IService {
    GetPoint(): Point;
    OpenSession(): TestType_interface;
}
```

### 5.2  生成命令

命令一：主接口文件引用了其他文件中的类型，则应使用 -C 参数来引用公共数据类型
```bash
./taihec 
-G modobj-ipc
-O ./example/generated/IBasicTypes_ohidl_c
-C modobj:ipc-common=./example/ExampleServiceIpcTypes.ohidl 
./example/IBasicTypes.ohidl
```
命令二：所有类型都定义在主接口文件中，无需引用其他文件
```bash
./taihec 
-G modobj-ipc 
-O ./example/generated
./example/Easy.ohidl
```

### 5.3 stub 和 proxy 源码的使用

[使用规范](参考文件)

### 5.4 通过 taihe 命令生成并使用类型库文件

**类型库文件概述**

在生成接口代码时，会同步输出一个 `*.typelib.json` 文件。该文件描述接口的结构化元信息，包括：

- 接口列表、方法名、IPC code
- 参数列表、返回值类型
- 枚举、结构体、接口等类型信息

``` json
{
  "version": "1.0",
  "taihe_version": "1.0.0",
  "enums": [
    {
      "memberId": 1,
      "name": "Color",
      "values": [
        {
          "memberId": 2,
          "name": "RED",
          "value": 0
        },
      ]
    }
  ],
  "structs": [
    {
      "memberId": 5,
      "name": "Point",
      "fields": [
        {
          "memberId": 6,
          "name": "x",
          "type_info": {
            "type": "i32"
          }
        },
      ]
    }
  ],
  "interfaces": [
    {
      "memberId": 8,
      "name": "BasicTypes",
      "descriptor": "OHOS.IPC.BasicTypes",
      "interface_type": 1,
      "methods": [
        {
          "memberId": 10,
          "name": "Type_bool",
          "code": 1001,
          "oneway": false,
          "return_type": {
            "type": "bool"
          }
        },
        {
          "memberId": 39,
          "name": "Type_Array1",
          "code": 1016,
          "oneway": false,
          "return_type": {
            "type": "array",
            "size": 4,
            "value_type": {
              "type": "i32"
            }
          },
          "parameters": [
            {
              "memberId": 38,
              "name": "values",
              "type_info": {
                "type": "array",
                "size": 4,
                "value_type": {
                  "type": "i32"
                }
              }
            }
          ]
        }
      ]
    }
  ]
}
```

**生成方式**

类型库文件由代码生成后端自动生成，不需要单独开启。执行 `taihec -G modobj-ipc` 命令后，会在输出目录自动生成 `*.typelib.json` 文件。

[**使用方式**](使用动态接口实现运行时查询类型信息、动态调用接口)

类型库文件通常用于运行时动态调用、方法枚举和类型信息查询：

- 利用 `typelib.json` 读取方法元数据
- 依据参数列表和类型信息构建动态调用逻辑
- 结合运行时服务发现机制实现晚绑定调用