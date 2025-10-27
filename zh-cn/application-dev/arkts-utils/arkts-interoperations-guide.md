# ArkTS1.2与ArkTS1.1互操作规格指导

ArkTS互操作规格指导说明了ArkTS1.2对象与ArkTS1.1对象在多线程环境下互操作的传输语义，以及Taskpool与EAWorker在互操作场景下的使用规则。本规则旨在兼顾兼容性、易用性与性能，确保开发者在混合版本ArkTS代码中，编写多线程程序时行为可预测且高效。

## ArkTS1.1与ArkTS1.2对象互操作跨线程传输规格

ArkTS1.1与ArkTS1.2对象互操作跨线程传输包括默认传递语义与拷贝传递语义两部分。默认传递语义描述的是在不调用额外API时，跨线程传递对象的行为。拷贝传递语义描述的是在显式深拷贝对象时，允许用户主动创建对象副本，以安全地跨线程使用。

### 默认跨线程传递语义（在ArkTS1.2中互操作ArkTS1.1对象）

由于ArkTS1.1为线程隔离环境，对象跨线程传递需要使用普通对象跨线程拷贝传递或Sendable对象跨线程引用传递。

当ArkTS1.2互操作ArkTS1.1对象时，默认为懒加载模式，第一次使用完ArkTS1.1对象后，再进行默认跨线程传递时，由于创建对象的上下文不同，将会触发运行时异常（RTE）。

    ```ts
    //file1.ets ArkTS1.1
    export const num: number = 1;

    //file2.ets ArkTS1.2
    'use static'
    import { num } from "/file1";

    console.info(num); //第一次使用时懒加载num
    taskpool.execute(() => {
        console.info(num); //RTE:在 ArkTS1.2懒加载后ArkTS1.1对象，不允许直接跨线程调用
    });
    ```

在ArkTS1.2中通过默认传递语义互操作ArkTS1.1对象时，包含以下两种情况：

- 当ArkTS1.2对象中直接包含ArkTS1.1普通对象时，将会触发运行时异常（RTE）。

    ```ts
    // file1.ets ArkTS1.1
    class A {
        n: number = 1;
    }

    // file2.ets ArkTS1.2
    'use static'

    import { A } from "/file1";
    class B {
        a: A;
    }

    function printArgs(b: B): number {
        ++b.a.n; // RTE：在跨线程上下文中，ArkTS1.2对象包含ArkTS1.1普通对象时，不被允许以引用方式共享
        return b.a.n;
    }

    let arg = new B();
    let task = new taskpool.Task(printArgs, arg); 
    taskpool.execute(task, taskpool.Priority.MEDIUM).then((num: number) => {
        console.info(num);
    });
    console.info(arg.n);
    ```
    
    该互操作场景将在运行时触发异常（RTE），以防止不安全的跨运行时对象共享。

- 当ArkTS1.2对象包含带有Sendable标注的ArkTS1.1对象时，可以通过引用传递，正常完成互操作。

    ```ts
    // file1.ets ArkTS1.1
    @Sendable
    class B {
        n: number = 1;  
    }

    // file2.ets ArkTS1.2
    'use static'
    import { B } from "/file1";

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
    
    此场景中ArkTS1.1对象使用@Sendable标注，允许跨线程的引用式共享。

### 默认跨线程传递语义（在ArkTS1.1中互操作ArkTS1.2对象）

在ArkTS1.1中通过默认传递语义互操作ArkTS1.2对象时，包含以下两种情况：

- 当ArkTS1.1普通对象中包含ArkTS1.2对象时，ArkTS1.1对象可以被完整拷贝，但其内部的ArkTS1.2对象不会被拷贝，而是会被多个线程共享引用。

    ```ts
    // file2.ets ArkTS1.2
    'use static'
    class B {
        n: number = 1;
    }

    // file1.ets ArkTS1.1
    import { B } from "/file2";
    class A {
        b: B;
    }

    function printArgs(a: A): number {
        ++a.b.n;
        return a.b.n;
    }

    let arg = new A();
    let task = new taskpool.Task(printArgs, arg);   // 跨线程传递A的实例
    taskpool.execute(task, taskpool.Priority.MEDIUM).then((num: number) => {
        console.info(num); // 2
    });
    console.info(arg.b.n); // 2
    ```
    
    此场景中，ArkTS1.2对象会维持其原有的引用语义，导致该对象在线程间共享而非被复制。

- 当带有Sendable标注的ArkTS1.1对象中包含ArkTS1.2对象时，将会触发运行时异常（RTE）。 
    
    此场景中，ArkTS1.1的@Sendable注解仅能保证ArkTS1.1自身对象的线程安全性，无法验证ArkTS1.2对象的线程安全行为。ArkTS1.2对象在ArkTS1.1的语义中隐式视为非Sendable对象，即使该对象在ArkTS1.2中可能是线程安全的，也会在运行时触发异常（RTE）。

### 拷贝跨线程传递语义

ArkTS1.2支持对象clone，能够创建并返回一个与原对象完全独立的深拷贝。无论原对象处于何种状态，clone创建深拷贝对象的行为在以下场景中都是安全的，不会抛出任何异常：

| 被clone对象类型 | 支持深拷贝的成员 |
| --------------  | --------------- |
|      ArkTS1.2对象     |   可深拷贝其直接/间接包含的ArkTS1.1普通对象与ArkTS1.1Sendable对象。|
|      ArkTS1.1Sendable对象 |   可深拷贝其直接/间接包含的ArkTS1.2对象。 |
|      ArkTS1.1普通对象 |    可深拷贝其直接/间接包含的ArkTS1.2对象。 |


## ArkTS1.2 Taskpool/EAWorker互操作规格

说明Taskpool.execute与EAWorker相关接口在互操作场景下的限制与行为。

总体原则是：执行回调的函数或者处理器必须来自ArkTS1.2，且回调的入参与闭包捕获遵循跨线程传递语义。

### Taskpool互操作规格

Taskpool为应用程序提供多线程环境，降低资源消耗、提高系统性能，无需管理线程生命周期。ArkTS1.2之后需要为Taskpool提供互操作交互规范。Taskpool的互操作行为主要体现在execute接口上，涉及回调任务类型、回调任务入参与闭包捕获规则。

- execute回调任务规格

    execute回调任务只允许使用原生ArkTS1.2方法/函数作为回调函数引用传入，禁止使用ArkTS1.1代理方法作为回调函数引用传入execute。若传入ArkTS1.1方法，运行时会抛出错误。

    正例：

    ```ts
    // flie1.ets ArkTS1.1
    function bar() {}

    // flie2.ets ArkTS1.2
    'use static'
    import { bar } from './1.1';
    function foo() {}

    taskpool.execute(foo); // YES：foo为1.2方法
    ```

    反例：

    ```ts
    // flie1.ets ArkTS1.1
    function bar() {}

    // flie2.ets ArkTS1.2
    'use static'
    import { bar } from './1.1';
    function foo() {}

    taskpool.execute(bar); // NO：bar为1.1方法，禁止作为回调
    ```

- execute回调任务的入参规格

    回调函数的入参不能随意传递，必须遵守跨线程数据传输的安全规则。回调任务的入参规格需要遵循默认跨线程传递语义，即如下规则：
    - 若入参为ArkTS1.2对象，则按引用传递。如果此ArkTS1.2对象中嵌套了非允许的ArkTS1.1普通对象，运行时会因为不能跨线程直接引用触发RTE。
    - 若入参包含ArkTS1.1Sendable对象，允许引用传递。
    - 若入参为ArkTS1.1普通对象，则必须按拷贝语义（序列化/反序列化）传递。如果此普通对象内部包含ArkTS1.2对象，则此部分内容按引用传递。

- execute回调任务闭包规格

    回调闭包中捕获的外部变量在跨线程执行时也被视作“入参”处理，其传输语义同样遵循默认跨线程传递语义。若闭包捕获了不允许跨线程共享的对象（如ArkTS1.2对象直接或者间接包含ArkTS1.1普通对象，或者ArkTS1.1Sendable对象中包含ArkTS1.2对象等不兼容组合），将会在execute时触发RTE。因此应该显示构造要传递的数据，以避免闭包隐式捕获导致的异常。

    正例：

    ```ts
    // flie1.ets ArkTS1.1
    function bar() {}
    class A {}

    // flie2.ets ArkTS1.2
    // 可以ESvalue.load()1.1的对象
    'use static'
    import { bar } from './1.1'
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
    ```
    
    正例：

    ```ts
    // flie1.ets ArkTS1.1
    function bar() {}
    class A {}

    // flie2.ets ArkTS1.2
    // 可以import（lazy）ArkTS1.1的对象
    'use static'
    import { bar } from './1.1'
    function foo(){
        bar()       //YES
    }
    ```

    反例：

    ```ts
    // flie1.ets ArkTS1.1
    function bar() {}
    class A {}

    // flie2.ets ArkTS1.2
    // 不可以使用非import的ArkTS1.1对象
    'use static'
    import { A } from './1.1'
    let a : A = new A
    function foo(){
        a   // NO, RTE
    }
    ```


### EAWorker互操作规格

EAWorker的互操作规格以Message/MessageHandler形式展现，包括以下三点关键规则：

- EAWorker Message的互操作规格

    EAWorker中通过Message发送的消息体，其对象参数与Taskpool execute的回调入参规格相同，具体语义包括ArkTS1.2对象引用传递、ArkTS1.1Sendable对象引用传递和ArkTS1.1普通对象拷贝传递（内部ArkTS1.2对象引用传递），并在不匹配时触发RTE。

    ```ts
    // ArkTS 1.2
    'use static'
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

    EAWorker MessageHandler回调函数必须为ArkTS1.2的方法，ArkTS1.1实现的函数或者方法，其引用或者包装不能作为MessageHandler的回调。

- EAWorker MessageHandler闭包规格

    MessageHandler闭包规格与Taskpool execute一致，回调闭包中捕获的外部变量按默认跨线程传递语义处理，任何不兼容的捕获都会导致发送或者执行阶段触发RTE。
