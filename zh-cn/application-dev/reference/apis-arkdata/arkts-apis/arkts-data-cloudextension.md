# @ohos.data.cloudExtension

端云共享Extension，提供第三方厂商适配共享云服务的能力。通过实现端云共享Extension提供的接口，将端侧的数据共享到服务端，实现端云共享的发起、取消或退出，更改共享数据的操作权限、查询共享参与者、根据共享邀请码查询共享参与者、确认或更改共享邀请，并支持返回共享云服务的相关结果。其中，端云共享资源标识是指：对于应用发起共享的每一条数据记录，该条数据在进行端云同步时会生成唯一的共享资源标识（字符串类型的值），此标识作为该条数据记录共享时的识别标识。端云共享参与者是指：共享发起者根据好友列表选中的参与当前数据共享的所有人员。端云共享邀请码是指：共享发起后，在共享的服务端会生成当前共享操作的邀请码，并将该邀请码附加到当前共享邀请中，通过推送消息推送到被邀请者的设备端，被邀请者可以通过该邀请码进行邀请的确认。同步云是指：端云同步的服务端，即同应用同账号跨设备的同步。共享云是指：端云共享的服务端，即同应用跨账号跨设备的共享。

**起始版本：** 11

<!--Device-unnamed-declare namespace cloudExtension--><!--Device-unnamed-declare namespace cloudExtension-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createAssetLoaderStub](arkts-arkdata-cloudextension-createassetloaderstub-f-sys.md#createassetloaderstub) | 根据AssetLoader类的实例创建对应的RemoteObject对象，系统内部通过该对象调用AssetLoader的实现接口，使用Promise异步回调。 |
| [createCloudDBStub](arkts-arkdata-cloudextension-createclouddbstub-f-sys.md#createclouddbstub) | 根据CloudDB类的实例创建对应的RemoteObject对象，系统内部通过该对象调用CloudDB的实现接口，使用Promise异步回调。 |
| [createCloudServiceStub](arkts-arkdata-cloudextension-createcloudservicestub-f-sys.md#createcloudservicestub) | 根据CloudService类的实例创建对应的RemoteObject对象，系统内部通过该对象调用CloudService的实现接口。使用Promise异步回调。 |
| [createShareServiceStub](arkts-arkdata-cloudextension-createshareservicestub-f-sys.md#createshareservicestub) | 根据ShareCenter类的实例创建对应的RemoteObject对象，系统内部通过该对象调用ShareCenter的实现接口，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppBriefInfo](arkts-arkdata-cloudextension-appbriefinfo-i-sys.md) | 简要应用信息。 |
| [AppSchema](arkts-arkdata-cloudextension-appschema-i-sys.md) | 应用数据库模式。 |
| [AssetLoader](arkts-arkdata-cloudextension-assetloader-i-sys.md) | 提供资产上传下载接口的类。 |
| [CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md) | 云资产的信息。 |
| [CloudDB](arkts-arkdata-cloudextension-clouddb-i-sys.md) | 提供云数据库操作接口的类。 |
| [CloudData](arkts-arkdata-cloudextension-clouddata-i-sys.md) | 云数据。 |
| [CloudInfo](arkts-arkdata-cloudextension-cloudinfo-i-sys.md) | 云信息。 |
| [CloudService](arkts-arkdata-cloudextension-cloudservice-i-sys.md) | 提供对接同步云服务的类。开发者需要继承此类并实现类的接口，系统内部通过该类的接口连接并使用同步云服务。 |
| [Database](arkts-arkdata-cloudextension-database-i-sys.md) | 数据库结构信息。 |
| [ExtensionValue](arkts-arkdata-cloudextension-extensionvalue-i-sys.md) | 当前数据记录的扩展信息。 |
| [Field](arkts-arkdata-cloudextension-field-i-sys.md) | 数据库中的字段结构。 |
| [LockInfo](arkts-arkdata-cloudextension-lockinfo-i-sys.md) | 云数据库锁信息。 |
| [Result](arkts-arkdata-cloudextension-result-i-sys.md) | 端云共享结果的返回值。 |
| [ServiceInfo](arkts-arkdata-cloudextension-serviceinfo-i-sys.md) | 云服务信息 |
| [ShareCenter](arkts-arkdata-cloudextension-sharecenter-i-sys.md) | 提供对接共享云服务的类。开发者需要继承此类并实现类的接口，系统内部通过该类的接口连接并使用共享云服务，实现端云共享的发起、取消或退出等能力。 |
| [SubscribeId](arkts-arkdata-cloudextension-subscribeid-i-sys.md) | 订阅ID。 |
| [SubscribeInfo](arkts-arkdata-cloudextension-subscribeinfo-i-sys.md) | 订阅信息 |
| [Table](arkts-arkdata-cloudextension-table-i-sys.md) | 表结构信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ErrorCode](arkts-arkdata-cloudextension-errorcode-e-sys.md) | 表示端云同步过程的状态。请使用枚举名而非枚举值。 |
| [FieldType](arkts-arkdata-cloudextension-fieldtype-e-sys.md) | 描述数据库表中字段类型的枚举。请使用枚举名而非枚举值。 |
| [Flag](arkts-arkdata-cloudextension-flag-e-sys.md) | 描述数据库上执行操作的枚举。请使用枚举名而非枚举值。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CloudAssets](arkts-arkdata-cloudextension-cloudassets-t-sys.md) | 表示CloudAsset类型的数组。 |
| [CloudType](arkts-arkdata-cloudextension-cloudtype-t-sys.md) | 表示云数据字段可使用的类型。各接口参数的实际类型视其功能而定。 |
<!--DelEnd-->

