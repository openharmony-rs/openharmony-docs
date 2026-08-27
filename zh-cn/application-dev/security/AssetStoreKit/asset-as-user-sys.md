# 操作指定用户空间下的关键资产(仅对系统应用开放)(ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

对于提供了系统级管理功能的单实例应用，一般场景下，所有用户共用一个实例，该实例负责实现不同用户的数据隔离。

1. 当同时有多个用户处于活跃状态时，单实例应用需要准确告知待操作关键资产所属的用户空间，才能够在该用户空间下存储、访问、销毁关键资产。
2. 单实例应用存储“首次解锁后可访问”和“解锁状态时可访问”的关键资产时，必须指定其所属的用户空间。

为了支持上述场景中单实例应用的关键资产数据隔离和访问控制，ASSET提供了一套可以指定用户空间进行关键资产操作的接口（仅面向系统应用）。

## 约束与限制

使用接口需要申请权限：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。

申请流程请参考：申请应用权限。

## 接口介绍

可通过API文档查看相关接口：

| 接口名称 | 说明 | 基础功能接口（不指定用户空间）<br>开发示例 |
| -------- | -------- | ----------|
| addAsUser              |   在指定用户空间中新增一条关键资产。使用Promise异步回调。           |  add             |
| removeAsUser              |   从指定用户空间中删除符合条件的一条或多条关键资产。使用Promise异步回调。           |  remove             |
| updateAsUser              |   在指定用户空间中更新符合条件的一条关键资产。使用Promise异步回调。           |  update             |
| preQueryAsUser              |   在指定用户空间中查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用queryAsUser和postQueryAsUser接口。使用Promise异步回调。           |  preQuery             |
| queryAsUser              |   在指定用户空间中查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用preQueryAsUser接口，在本函数后调用postQueryAsUser接口。使用Promise异步回调。           |  若查询需要用户认证的关键资产：query<br>若查询不需要用户认证的关键资产：query            |
| postQueryAsUser              |   在指定用户空间中查询的后置处理，用于需要用户认证的关键资产（与preQueryAsUser函数成对出现）。使用Promise异步回调。           |  postQuery            |