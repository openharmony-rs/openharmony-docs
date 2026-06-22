# ArkTS静态类型术语
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

## A
### AOT; 预编译
即Ahead-Of-Time，编译时将字节码转为机器码，可显著提升程序运行性能。

### ANI; ArkTS静态原生接口
ArkTS-Sta Native Interface，即ArkTS静态类型与C++跨语言交互接口，为ArkTS静态类型语言与C++代码提供双向跨语言交互能力。

### ArkTS-Dyn; ArkTS动态类型语言
ArkTS-Dyn使用动态类型模式运行，在保持TypeScript基本风格的基础上，对并发能力进行了局部增强，支持与TypeScript、JavaScript的高效互操作；其对象类型在编译时仅作为静态检查的参考，实际类型的绑定发生在运行时；默认创建的对象仍受限于线程隔离机制，无法直接共享。

### ArkTS-Sta; ArkTS静态类型语言
ArkTS-Sta使用静态类型模式运行，其创建的对象具备天然的并发共享能力，避免了动态类型对象所需的线程隔离机制，适用于多线程共享访问场景；其所有变量和表达式的类型在编译时（静态）就已确定，编译器在生成可执行代码前，会进行严格的类型检查，不允许类型不匹配的赋值或操作。

### AKI; Alpha内核交互框架
即Alpha Kernel Interacting，基于NAPI的ArkTS FFI开发框架，针对OpenHarmony Native开发提供JS与C/C++跨语言访问场景解决方案。

## E
### EAWorker; 独占式ArkTS工作线程
即Exclusive ArkTS Worker，面向ArkTS静态类型设计，支持共享内存并发模型。

### ESValue; ECMAScript值接口
即ECMAScript Value，作为ArkTS-Sta与ArkTS-Dyn互操作的桥接接口，实现两种模式间数据传递。

## I
### IDL; 接口定义语言
即Interface Definition Language，Taihe编程模型通过接口定义语言来标准化描述C++的API接口。

### Interop; 互操作能力
即Interoperability，特指ArkTS-Sta静态类型语言与ArkTS-Dyn动态类型语言之间的双向交互能力。

## N
### NAPI; Node接口
Node-API，即ArkTS-Dyn与C++跨语言交互接口。为ArkTS动态类型语言与C++代码提供稳定、双向的跨语言交互能力。

## O
### .ohidl; Taihe接口定义文件
Taihe IDL文件后缀，需放置在工程指定目录下，Taihe编译器会自动解析该文件并生成对应跨语言接口代码。

## S
### STValue; 静态类型值接口
即Static Type Value，作为ArkTS-Dyn与ArkTS-Sta互操作的桥接接口，完成动态语言到静态语言的数据转换与传递。


## T
### Taihe; 多语言系统接口编程模型
一种跨语言API编程模型，定义了多语言系统接口编程规范，提供简洁易用的API发布与消费机制。

## U
## 'use static'; 静态类型声明标识
必须在文件开头添加，用于标识当前文件启用ArkTS静态类型语言语法与编译检查。

