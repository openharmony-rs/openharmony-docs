# IPC与RPC通信术语
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

## D

### DeathRecipient；死亡通知

提供的远端Stub对象状态订阅机制。Proxy侧注册回调后，当远端Stub对象所在进程退出或RPC通信依赖的软总线连接断开时，自动触发回调通知，用于Proxy侧清理本地代理对象及相关资源。

## I

### Inter Process Communication (IPC)；进程间通信

基于Binder驱动实现的设备内跨进程通信机制。采用客户端-服务端模型，Client进程获取Server的Proxy代理后发起请求，Server端Stub处理请求并应答结果。典型使用场景为后台服务，提供单设备跨进程接口与调用数据传递能力。

## R

### Remote Procedure Call (RPC)；远程过程调用

基于软总线实现的跨设备进程间通信机制，采用与IPC相同的客户端-服务端模型和Proxy-Stub对应关系。典型使用场景为多端协同，提供跨设备远端接口调用与数据传递能力。与IPC的关键区别在于通信范围跨设备而非设备内，底层驱动为软总线而非Binder。

## S

### Stub

IPC/RPC通信模型中包括服务端侧对象（Stub）和客户端对象（Proxy），Stub接收并处理Proxy发起的请求并应答结果。Stub定义具体的请求处理逻辑，Proxy实现对应的请求发起方法。