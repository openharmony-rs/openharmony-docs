# IPC Kit术语
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

## A

### Ashmem；匿名共享内存

IPC/RPC通信中用于传输超过200KB大数据量的共享内存机制，允许多个进程共享同一块内存区域而无需多次拷贝数据。IPC单次传输数据量上限为200KB，超出时须使用此机制替代常规序列化传输。

## D

### DeathRecipient；死亡通知

IPC/RPC提供的远端Stub对象状态订阅机制。Proxy侧注册回调后，当远端Stub对象所在进程退出或RPC通信依赖的SoftBus连接断开时，自动触发回调通知，用于Proxy侧清理本地代理对象及相关资源。IPC支持匿名Stub的死亡通知订阅，RPC不支持。

## I

### Inter Process Communication (IPC)；进程间通信

基于Binder驱动实现的设备内跨进程通信机制。采用客户端-服务端模型，Client进程获取Server的Proxy代理后发起请求，Server端Stub处理请求并应答结果。典型使用场景为后台服务，提供单设备跨进程接口调用与数据传递能力。获取通信代理对象的能力由Ability Kit提供，IPC Kit不直接提供。

## N

### Native子进程

通过Ability框架创建的C/C++子进程，用于与主进程进行IPC通信。子进程实现Stub对象并通过导出方法返回，主进程通过回调获取Proxy代理对象后即可进行跨进程通信。子进程主函数返回后进程随即退出。

## P

### Proxy；代理

IPC/RPC通信模型中的客户端侧远程对象代理，由元能力连接服务接口返回，用于向远端Stub读写数据和发起请求。每个Proxy与一个Stub一一对应，构成跨进程通信的客户端桥梁。Proxy不可在本设备内二次跨进程传递，也不可把跨设备的Proxy回传到其指向的Stub所在设备。

## R

### Remote Procedure Call (RPC)；远程过程调用

基于SoftBus驱动实现的跨设备进程间通信机制，采用与IPC相同的客户端-服务端模型和Proxy-Stub对应关系。典型使用场景为多端协同，提供跨设备远端接口调用与数据传递能力。与IPC的关键区别在于通信范围跨设备而非设备内，底层驱动为SoftBus而非Binder。

## S

### System Ability Manager (SAMgr)；系统服务管理

OpenHarmony中管理系统服务注册、查询与调度的核心服务。Stub对象需向其注册后方可被跨进程发现和访问，未注册的为匿名Stub，访问范围受限。

### SoftBus；软总线

OpenHarmony分布式通信基础设施，作为RPC通信的底层驱动，提供跨设备间的数据传输和连接管理能力。RPC通信依赖SoftBus连接，当连接断开时将触发Proxy侧已注册的死亡通知回调。

### Stub

IPC/RPC通信模型中的服务端侧对象，接收并处理Proxy发起的请求并应答结果。Stub定义具体的请求处理逻辑，Proxy实现对应的请求发起方法，二者一一对应。向SAMgr注册的Stub可被跨进程和跨设备发现访问，未注册的为匿名Stub，仅限设备内IPC使用且访问范围受限。