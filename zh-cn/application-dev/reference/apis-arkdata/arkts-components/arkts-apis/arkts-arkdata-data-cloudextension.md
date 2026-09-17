# @ohos.data.cloudExtension(端云共享Extension)

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

## 完整示例

以上示例中的类均采用implements实现，示例代码不能单独编译，需要实现父类中的所有方法才能使用，提供完整示例以作参考。

```ts
 import { Want, ServiceExtensionAbility } from '@kit.AbilityKit';
 import { rpc } from '@kit.IPCKit';
 import { cloudData, cloudExtension } from '@kit.ArkData';
 type Participant = cloudData.sharing.Participant;
 let testLockId: number = 1;
 let testTime: number = 10;
 let testSpace: number = 100;
 let testUserId: number = 1;
 class MyCloudDB implements cloudExtension.CloudDB {
 async generateId(count: number): Promise&lt;cloudExtension.Result&lt;Array&lt;string&gt;>
> {
 console.info(`generate id, count: &#36;{count}`);
 let result = new Array&lt;string&gt;();
 // ...
 // 返回创建Id的结果
 return {
 code: cloudExtension.ErrorCode.SUCCESS,
 description: 'generateId succeeded',
 value: result
 };
 }
 async update(table: string, values: Array&lt;Record<string,
 cloudExtension.CloudType>&gt;, extensions: Array&lt;Record<string, cloudExtension.CloudType>&gt;):
 　　Promise&lt;Array&lt;cloudExtension.Result&lt;Record&lt;string, cloudExtension.CloudType&gt;>>
> {
 console.info(`update, table: &#36;{table}`);
 let updateRes: Array&lt;cloudExtension.Result&lt;Record&lt;string, cloudExtension.CloudType&gt;>
> = [];
 // ...
 // 返回更新数据的结果
 return updateRes;
 }
 async insert(table: string, values: Array&lt;Record<string, cloudExtension.CloudType>&gt;,
 extensions: Array&lt;Record<string, cloudExtension.CloudType>&gt;): Promise&lt;Array&lt;cloudExtension.Result&lt;Record&lt;string, cloudExtension.CloudType&gt;>>
> {
 console.info(`insert, table: &#36;{table}`);
 let insertRes: Array&lt;cloudExtension.Result&lt;Record&lt;string, cloudExtension.CloudType&gt;>
> = [];
 // ...
 // 返回插入数据的结果
 return insertRes;
 }
 async delete(table: string, extensions: Array&lt;Record<string, cloudExtension.CloudType>&gt;):
 　　Promise&lt;Array&lt;cloudExtension.Result&lt;Record&lt;string, cloudExtension.CloudType&gt;>>
> {
 console.info(`delete, table: &#36;{table}`);
 let deleteRes: Array&lt;cloudExtension.Result&lt;Record&lt;string, cloudExtension.CloudType&gt;>
> = [];
 // ...
 // 返回删除数据的结果
 return deleteRes;
 }
 async query(table: string, fields: Array&lt;string&gt;, queryCount: number, queryCursor: string): Promise&lt;cloudExtension.Result&lt;cloudExtension.CloudData&gt;
> {
 console.info(`query, table: &#36;{table}`);
 // ...
 // 返回查询数据的结果
 return {
 code: cloudExtension.ErrorCode.SUCCESS,
 description: 'query succeeded',
 value: {
 nextCursor: "test_nextCursor",
 hasMore: true,
 values: []
 }
 };
 }
 async lock(): Promise&lt;cloudExtension.Result&lt;cloudExtension.LockInfo&gt;
> {
 console.info(`DB lock`);
 // ...
 // 返回锁定数据的结果
 return {
 code: cloudExtension.ErrorCode.SUCCESS,
 description: 'lock succeeded',
 value: {
 interval: testTime,
 lockId: testLockId
 }
 };
 }
 async heartbeat(lockId: number): Promise&lt;cloudExtension.Result&lt;cloudExtension.LockInfo&gt;
> {
 console.info(`heartbeat lock`);
 // ...
 // 返回心跳检测的结果
 return {
 code: cloudExtension.ErrorCode.SUCCESS,
 description: 'heartbeat succeeded',
 value: {
 interval: testTime,
 lockId: testLockId
 }
 };
 }
 async unlock(lockId: number): Promise&lt;cloudExtension.Result&lt;boolean&gt;
> {
 console.info(`unlock`);
 // ...
 // 返回解锁数据的结果
 return {
 code: cloudExtension.ErrorCode.SUCCESS,
 description: 'unlock succeeded',
 value: false
 };
 }
 }
 class MyAssetLoader implements cloudExtension.AssetLoader {
 async download(table: string, gid: string, prefix: string,
 assets: Array&lt;cloudExtension.CloudAsset&gt;): Promise&lt;Array&lt;cloudExtension.Result&lt;cloudExtension.CloudAsset&gt;>
> {
 console.info(`download asset loader, table: &#36;{table}, gid: &#36;{gid}, prefix: &#36;{prefix}`);
 let downloadRes = Array&lt;cloudExtension.Result<cloudExtension.CloudAsset>&gt;();
 // ...
 return downloadRes;
 }
 async upload(table: string, gid: string, assets: Array&lt;cloudExtension.CloudAsset&gt;): Promise&lt;Array&lt;cloudExtension.Result&lt;cloudExtension.CloudAsset&gt;>
> {
 console.info(`upload asset loader, table: &#36;{table}, gid: &#36;{gid}`);
 let uploadRes = Array&lt;cloudExtension.Result<cloudExtension.CloudAsset>&gt;();
 // ...
 return uploadRes;
 }
 }
 class MyShareCenter implements cloudExtension.ShareCenter {
 constructor() {
 }
 async share(userId: number, bundleName: string, sharingResource: string, participants: Array&lt;Participant&gt;):
 Promise&lt;cloudExtension.Result&lt;Array&lt;cloudExtension.Result&lt;Participant&gt;>>
> {
 console.info(`share, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得共享的返回值
 // ...
 // 返回服务端发起共享的返回结果
 let result: Array&lt;cloudExtension.Result&lt;Participant&gt;
> = [];
 participants.forEach(() =
> {
 result.push({
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'share succeeded'
 });
 });
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'share succeeded',
 value: result
 };
 }
 async unshare(userId: number, bundleName: string, sharingResource: string, participants: Array&lt;Participant&gt;):
 Promise&lt;cloudExtension.Result&lt;Array&lt;cloudExtension.Result&lt;Participant&gt;>>
> {
 console.info(`unshare, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得取消共享的返回值
 // ...
 // 返回服务端取消共享的返回结果
 let result: Array&lt;cloudExtension.Result&lt;Participant&gt;
> = [];
 participants.forEach(() =
> {
 result.push({
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'unshare succeeded'
 });
 });
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'unshare succeeded',
 value: result
 };
 }
 async exit(userId: number, bundleName: string, sharingResource: string):
 Promise&lt;cloudExtension.Result&lt;void&gt;
> {
 console.info(`exit share, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得退出共享的返回值
 // ...
 // 返回服务端退出共享的返回结果
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'exit share succeeded'
 };
 }
 async changePrivilege(userId: number, bundleName: string, sharingResource: string, participants: Array&lt;Participant&gt;):
 Promise&lt;cloudExtension.Result&lt;Array&lt;cloudExtension.Result&lt;Participant&gt;>>
> {
 console.info(`change privilege, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得更改权限的返回值
 // ...
 // 返回服务端更改权限的返回结果
 let result: Array&lt;cloudExtension.Result&lt;Participant&gt;
> = [];
 participants.forEach(() =
> {
 result.push({
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'change privilege succeeded'
 });
 });
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'change privilege succeeded',
 value: result
 };
 }
 async queryParticipants(userId: number, bundleName: string, sharingResource: string):
 Promise&lt;cloudExtension.Result&lt;Array&lt;Participant&gt;>
> {
 console.info(`query participants, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得查询参与者的返回值
 // ...
 // 返回服务端查询参与者的返回结果
 let participants = new Array&lt;cloudData.sharing.Participant&gt;();
 participants.push({
 identity: '000000000',
 role: cloudData.sharing.Role.ROLE_INVITEE,
 state: cloudData.sharing.State.STATE_ACCEPTED,
 privilege: {
 writable: false,
 readable: true,
 creatable: false,
 deletable: false,
 shareable: false
 },
 attachInfo: ''
 });
 participants.push({
 identity: '111111111',
 role: cloudData.sharing.Role.ROLE_INVITEE,
 state: cloudData.sharing.State.STATE_ACCEPTED,
 privilege: {
 writable: false,
 readable: true,
 creatable: false,
 deletable: false,
 shareable: false
 },
 attachInfo: ''
 });
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'query participants succeeded',
 value: participants
 };
 }
 async queryParticipantsByInvitation(userId: number, bundleName: string, invitationCode: string):
 Promise&lt;cloudExtension.Result&lt;Array&lt;Participant&gt;>
> {
 console.info(`query participants by invitation, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得查询参与者的返回值
 // ...
 // 返回服务端查询参与者的返回结果
 let participants = new Array&lt;cloudData.sharing.Participant&gt;();
 participants.push({
 identity: '000000000',
 role: cloudData.sharing.Role.ROLE_INVITEE,
 state: cloudData.sharing.State.STATE_ACCEPTED,
 privilege: {
 writable: false,
 readable: true,
 creatable: false,
 deletable: false,
 shareable: false
 },
 attachInfo: ''
 });
 participants.push({
 identity: '111111111',
 role: cloudData.sharing.Role.ROLE_INVITEE,
 state: cloudData.sharing.State.STATE_ACCEPTED,
 privilege: {
 writable: false,
 readable: true,
 creatable: false,
 deletable: false,
 shareable: false
 },
 attachInfo: ''
 });
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'query participants by invitation succeeded',
 value: participants
 };
 }
 async confirmInvitation(userId: number, bundleName: string, invitationCode: string, state: cloudData.sharing.State):
 Promise&lt;cloudExtension.Result&lt;string&gt;
> {
 console.info(`confirm invitation, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得确认共享邀请的返回值
 // ...
 // 返回服务端确认共享邀请的返回结果
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'confirm invitation succeeded',
 value: 'sharing_resource_test'
 };
 }
 async changeConfirmation(userId: number, bundleName: string, sharingResource: string, state: cloudData.sharing.State):
 Promise&lt;cloudExtension.Result&lt;void&gt;
> {
 console.info(`change confirm, bundle: &#36;{bundleName}`);
 // 对接云共享服务端，并获得更改共享邀请的返回值
 // ...
 // 返回服务端更改共享邀请的返回结果
 return {
 code: cloudData.sharing.SharingCode.SUCCESS,
 description: 'change confirm succeeded'
 };
 }
 }
 class MyCloudService implements cloudExtension.CloudService {
 constructor() {
 }
 async getServiceInfo(): Promise&lt;cloudExtension.ServiceInfo&gt; {
 console.info(`get service info`);
 // ...
 return {
 enableCloud: true,
 id: "test_id",
 totalSpace: testSpace,
 remainingSpace: testSpace,
 user: testUserId,
 };
 }
 async getAppBriefInfo(): Promise&lt;Record&lt;string, cloudExtension.AppBriefInfo&gt;
> {
 console.info(`get app brief info`);
 // ...
 return {
 "test_bundle":
 {
 appId: "test_appID",
 bundleName: "test_bundlename",
 cloudSwitch: true,
 instanceId: 0,
 }
 };
 }
 async getAppSchema(bundleName: string): Promise&lt;cloudExtension.Result&lt;cloudExtension.AppSchema&gt;
> {
 console.info(`get app schema, bundleName:&#36;{bundleName}`);
 // ...
 return {
 code: cloudExtension.ErrorCode.SUCCESS,
 description: "get app schema success",
 value: {
 bundleName: "test_bundleName",
 version: 1,
 databases: []
 }
 };
 }
 async subscribe(subInfo: Record&lt;string, Array<cloudExtension.Database>&gt;,
 expirationTime: number): Promise&lt;cloudExtension.Result&lt;cloudExtension.SubscribeInfo&gt;
> {
 console.info(`subscribe expirationTime: &#36;{expirationTime}`);
 // ...
 return {
 code: cloudExtension.ErrorCode.SUCCESS,
 description: "subscribe success",
 value: {
 expirationTime: testTime,
 subscribe: {}
 }
 };
 }
 async unsubscribe(unsubscribeInfo: Record&lt;string, Array<string>&gt;): Promise&lt;number&gt; {
 console.info(`unsubscribe`);
 // ...
 return cloudExtension.ErrorCode.SUCCESS;
 }
 async connectDB(bundleName: string, database: cloudExtension.Database): Promise&lt;rpc.RemoteObject&gt; {
 console.info(`connect DB, bundleName: &#36;{bundleName}`);
 return cloudExtension.createCloudDBStub(new MyCloudDB());
 }
 async connectAssetLoader(bundleName: string, database: cloudExtension.Database): Promise&lt;rpc.RemoteObject&gt; {
 return cloudExtension.createAssetLoaderStub(new MyAssetLoader());
 }
 async connectShareCenter(userId: number, bundleName: string): Promise&lt;rpc.RemoteObject&gt; {
 console.info(`connect share center, bundle: &#36;{bundleName}`);
 // ...
 return cloudExtension.createShareServiceStub(new MyShareCenter());
 }
 }
 export default class MyServiceExtension extends ServiceExtensionAbility {
 onCreate(want: Want) {
 console.info(`onCreate: &#36;{want}`);
 }
 onRequest(want: Want, startId: number) {
 console.info(`onRequest: &#36;{want} &#36;{startId}`);
 }
 onConnect(want: Want): rpc.RemoteObject | Promise&lt;rpc.RemoteObject&gt; {
 console.info(`onConnect: &#36;{want}`);
 return cloudExtension.createCloudServiceStub(new MyCloudService());
 }
 onDisconnect(want: Want) {
 console.info(`onDisconnect: &#36;{want}`);
 }
 onDestroy() {
 console.info('onDestroy');
 }
 }
 ```

<!--no_check-->

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createAssetLoaderStub](arkts-arkdata-cloudextension-createassetloaderstub-f-sys.md) | 根据[AssetLoader](arkts-arkdata-cloudextension-assetloader-i-sys.md)类的实例创建对应的[RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)对象，系统内部通过该对象调用[AssetLoader](arkts-arkdata-cloudextension-assetloader-i-sys.md)的实现接口，使用Promise异步回调。 |
| [createCloudDBStub](arkts-arkdata-cloudextension-createclouddbstub-f-sys.md) | 根据[CloudDB](arkts-arkdata-cloudextension-clouddb-i-sys.md)类的实例创建对应的[RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)对象，系统内部通过该对象调用[CloudDB](arkts-arkdata-cloudextension-clouddb-i-sys.md)的实现接口，使用Promise异步回调。 |
| [createCloudServiceStub](arkts-arkdata-cloudextension-createcloudservicestub-f-sys.md) | 根据[CloudService](arkts-arkdata-cloudextension-cloudservice-i-sys.md)类的实例创建对应的[RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)对象，系统内部通过该对象调用[CloudService](arkts-arkdata-cloudextension-cloudservice-i-sys.md)的实现接口。使用Promise异步回调。 |
| [createShareServiceStub](arkts-arkdata-cloudextension-createshareservicestub-f-sys.md) | 根据[ShareCenter](arkts-arkdata-cloudextension-sharecenter-i-sys.md)类的实例创建对应的[RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)对象，系统内部通过该对象调用[ShareCenter](arkts-arkdata-cloudextension-sharecenter-i-sys.md)的实现接口，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppBriefInfo](arkts-arkdata-cloudextension-appbriefinfo-i-sys.md) | 简要应用信息。 |
| [AppSchema](arkts-arkdata-cloudextension-appschema-i-sys.md) | 应用数据库模式。 |
| [AssetLoader](arkts-arkdata-cloudextension-assetloader-i-sys.md) | 提供资产上传下载接口的类。 |
| [CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md) | 云资产的信息。 |
| [CloudData](arkts-arkdata-cloudextension-clouddata-i-sys.md) | 云数据。 |
| [CloudDB](arkts-arkdata-cloudextension-clouddb-i-sys.md) | 提供云数据库操作接口的类。 |
| [CloudInfo](arkts-arkdata-cloudextension-cloudinfo-i-sys.md) | 云信息。 |
| [CloudService](arkts-arkdata-cloudextension-cloudservice-i-sys.md) | 提供对接同步云服务的类。开发者需要继承此类并实现类的接口，系统内部通过该类的接口连接并使用同步云服务。 |
| [Database](arkts-arkdata-cloudextension-database-i-sys.md) | 数据库结构信息。 |
| [ExtensionValue](arkts-arkdata-cloudextension-extensionvalue-i-sys.md) | 当前数据记录的扩展信息。 |
| [Field](arkts-arkdata-cloudextension-field-i-sys.md) | 数据库中的字段结构。 |
| [LockInfo](arkts-arkdata-cloudextension-lockinfo-i-sys.md) | 云数据库锁信息。 |
| [Result](arkts-arkdata-cloudextension-result-i-sys.md) | 端云共享结果的返回值。 |
| [ServiceInfo](arkts-arkdata-cloudextension-serviceinfo-i-sys.md) | 云服务信息。 |
| [ShareCenter](arkts-arkdata-cloudextension-sharecenter-i-sys.md) | 提供对接共享云服务的类。开发者需要继承此类并实现类的接口，系统内部通过该类的接口连接并使用共享云服务，实现端云共享的发起、取消或退出等能力。 |
| [SubscribeId](arkts-arkdata-cloudextension-subscribeid-i-sys.md) | 订阅ID。 |
| [SubscribeInfo](arkts-arkdata-cloudextension-subscribeinfo-i-sys.md) | 订阅信息。 |
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
| [CloudAssets](arkts-arkdata-cloudextension-cloudassets-t-sys.md) | 表示[CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md)类型的数组 |
| [CloudType](arkts-arkdata-cloudextension-cloudtype-t-sys.md) | 表示云数据字段可使用的类型。各接口参数的实际类型视其功能而定。 |
<!--DelEnd-->
