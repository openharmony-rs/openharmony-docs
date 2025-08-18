# Interop规格文档

ArkTS跨线程interop规格定义了ArkTS1.2对象、ArkTS1.1对象（包括Sendable和普通对象）在多线程环境下互操作的传输语义，以及Taskpool与EAWorker在互操作场景下的使用规则。本规则旨在兼顾兼容性、易用性与性能，确保开发者在混合版本ArkTS代码中，编写多线程程序时行为可预测且高效。

> **说明：**
> 
> ArkTS版本：文档所述interop规格适用于ArkTS1.2。
>

## ArkTS1.2对象跨线程传输规格

跨线程传输包括默认传递语义与拷贝传递语义（即clone API语义）两部分。默认传递语义描述的是在不调用额外API时，跨线程传递对象的行为。clone API描述的是显示深拷贝对象的行为时，允许用户主动创建对象副本以安全跨线程使用。

### 默认跨线程传递语义

由于ArkTS1.1为线程隔离环境，对象跨线程传递分为普通对象跨线程拷贝传递和Sendable对象跨线程引用传递。在ArkTS1.2中，默认传递语义包含以下几种情况：

- 1.2对象直接包含1.1普通对象 -> RTE
    
    ```ts
    // ArkTS 1.1
    class A {
        n: number = 1;
    }

    // ArkTS 1.2
    import { A } from "1.1";
    class B {
        a: A;
    }

    function printArgs(b: B): number {
        ++b.a.n; // RTE：在跨线程上下文中，1.2对象包含1.1普通对象不被允许以引用方式共享
        return b.a.n;
    }

    let arg = new B();
    let task = new taskpool.Task(printArgs, arg); // 跨线程传递 A 的实例
    taskpool.execute(task, taskpool.Priority.MEDIUM).then((num: number) => {
        console.info(num);
    });
    console.info(arg.n);
    ```
    
    该场景将在运行时触发异常（RTE），以防止不安全的跨运行时对象共享。

- 1.2对象包含1.1Sendable对象 -> 引用传递（正常共享）
    
    ```ts
    // ArkTS 1.1
    @Sendable
    class B {
        n: number = 1;  
    }

    // ArkTS 1.2
    import { B } from "./1.1";

    class A {
        b: B;
        constructor() {

            this.b = new B();
        }
    }

    function printArgs(a: A): number {
        ++a.b.n;
        return a.b.n;
    }

    let arg = new A();
    let task: taskpool.Task = new taskpool.Task(printArgs, arg); // 跨线程传递A的实例
    try{
        taskpool.execute(task, taskpool.Priority.MEDIUM).then((num: Any) => {
            console.info(num); // 2
        });
    }catch(error){
        let err = error as Error;
        console.error("interop: error message is: ", err.message);
    }

    console.info(arg.b.n); // 2
    ```
    
    此场景中1.1对象使用@Sendable标注，允许跨线程的引用式共享。

- 1.1普通对象（拷贝传递）中包含1.2对象 -> 1.2对象按引用传递
    
    ```ts
    // ArkTS 1.2
    class B {
        n: number = 1;
    }

    // ArkTS 1.1
    import { B } from "1.2";
    class A {
        b: B;
    }

    function printArgs(a: A): number {
        ++a.b.n;
        return a.b.n;
    }

    let arg = new A();
    let task = new taskpool.Task(printArgs, arg);   // 跨线程传递 A 的实例
    taskpool.execute(task, taskpool.Priority.MEDIUM).then((num: number) => {
        console.info(num); // 2
    });
    console.info(arg.b.n); // 2
    ```
    
    此场景中1.2对象部分保持引用语义。

- 1.1@Sendable对象（引用传递）中包含1.2对象 -> RTE
    
    此场景中，ArkTS1.1的@Sendable注解仅能保证1.1自身对象的线程安全性，无法验证1.2对象的线程安全行为。1.2对象在1.1的语义中隐式视为非Sendable对象，即使该对象在1.2中可能是线程安全的，也会在运行时触发异常（RTE）。

### clone API语义

ArkTS1.2支持对象clone，通过clone接口可以返回对象的深拷贝。以下clone行为在所有场景均可以保证无异常：

| 被clone对象类型 | 支持深拷贝的成员 |
| --------------  | --------------- |
|      1.2对象     |   可深拷贝其直接/间接包含的1.1普通对象与1.1Sendable对象。|
|      1.1Sendable对象 |   可深拷贝其直接/间接包含的1.2对象。 |
|      1.1普通对象 |    可深拷贝其直接/间接包含的1.2对象。 |


## ArkTS1.2 Taskpool/EAWorker interop规格

本节规定Taskpool.execute与EAWorker相关接口在互操作场景下的限制与行为。

总体原则是：执行回调（函数/处理器）必须来自ArkTS1.2，且回调的入参与闭包捕获遵循跨线程传递语义。

### Taskpool interop规格

Taskpool为应用程序提供多线程环境，降低资源消耗、提高系统性能，无需管理线程生命周期。ArkTS1.2之后需要为Taskpool提供interop交互规范。Taskpool的interop行为主要体现在execute接口上，涉及回调任务类型、回调任务入参与闭包捕获规则。

- execute回调任务规格

    execute回调任务只允许使用原生ArkTS1.2方法/函数作为回调函数引用传入，禁止使用ArkTS1.1代理方法作为回调函数引用传入execute。若传入1.1方法，运行时会抛出错误。

    ```ts
    // =============================================
    // ArkTS 1.1
    function bar() {}

    // =============================================
    // ArkTS 1.2
    import { bar } from './1.1';
    function foo() {}

    taskpool.execute(foo); // YES：foo 为 1.2 方法
    taskpool.execute(bar); // NO：bar 为 1.1 方法（代理），禁止作为回调
    ```

- execute回调任务的入参规格

    回调函数的入参不能随意传递，必须遵守跨线程数据传输的安全规则。回调任务的入参规格需要遵循默认跨线程传递语义，即如下规则：
    - 若入参为1.2对象，则按引用传递。如果此1.2对象中嵌套了非允许的1.1普通对象，运行时会因为不能跨线程直接引用触发RTE。
    - 若入参包含1.1Sendable对象，允许引用传递。
    - 若入参为1.1普通对象，则必须按拷贝语义（序列化/反序列化）传递。如果此普通对象内部包含1.2对象，则此部分内容按引用传递。

- execute回调任务闭包规格

    回调闭包中捕获的外部变量在跨线程执行时也被视作“入参”处理，其传输语义同样遵循默认跨线程传递语义。若闭包捕获了不允许跨线程共享的对象（如1.2对象直接或者间接包含1.1普通对象，或者1.1Sendable对象中包含1.2对象等不兼容组合），将会在execute时触发RTE。因此应该显示构造要传递的数据，以避免闭包隐式捕获导致的异常。

    ```ts
    // =============================================
    // ArkTS 1.1
    function bar() {}
    class A {}

    // =============================================
    // ArkTS 1.2
    
    //(1) 可以ESvalue.Load 1.1的对象
    function foo() {
        // 加载模块
        let module: ESValue = ESValue.load("@normalized:N&entry&com.example.interop_test&entry/src/main/ets/pages/1_1&1.0.0")
        let foo: ESValue = module.getProperty('foo')
        let A: ESValue = module.getProperty('A')
        // 实例化
        let aa: ESValue = A.instantiate()
        // 调用函数
        let a: ESValue = foo.invoke(aa)
        // 读属性
        let msg: ESValue = a.getProperty('msg')
        let msgStr: string = msg.toString()  
        let data: ESValue = a.getProperty('data')  
    }
    //(2) 可以import（lazy）1.1的对象
    import { bar } from './1.1'
    function foo(){
        bar()       //YES
    }

    //(3) 不可以使用非import的1.1对象
    import { A } from './1.1'
    let a : A = new A
    function foo(){
        a   // NO, RTE
    }
    ```

### EAWorker interop规格

EAWorker的interop规格与Taskpool高度一致，以Message/MessageHandler形式展现，包括以下三点关键规则：

- EAWorker Message的interop规格

    EAWorker中通过Message发送的消息体，其对象参数与Taskpool execute的回调入参规格相同，具体语义包括1.2对象引用传递、1.1Sendable对象引用传递和1.1普通对象拷贝传递（内部1.2对象引用传递），并在不匹配时触发RTE。

    ```ts
    // ArkTS 1.2
    class SendableObject{
        a : number = 45;
    }

    const workerInstance = new EAWorker("example worker");
    workerInstance.start();

    const workerCB = (msg: concurrency.Message) => {
        let obj: SendableObject = msg.getObject() as SendableObject;
        // 对obj的访问遵循默认跨线程传递语义
        console.info("sendable object is: " + obj.a);
    };

    let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);
    let sendableObj: SendableObject = new SendableObject();
    let msg = new concurrency.Message(1, sendableObj, workerHandler);
    msg.sendToTarget();
    ```

- EAWorker MessageHandler回调规格

    EAWorker MessageHandler回调函数必须为ArkTS1.2的方法，ArkTS1.1代理方法不能作为MessageHandler的回调。

- EAWorker MessageHandler闭包规格

    MessageHandler闭包规格与Taskpool execute一致，回调闭包中捕获的外部变量按默认跨线程传递语义处理，任何不兼容的捕获都会导致发送或者执行阶段触发RTE。
