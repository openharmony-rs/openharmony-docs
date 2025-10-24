# Managing Distributed Accounts (for System Applications Only)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

You can use the [distributed account SDK](../../reference/apis-basic-services-kit/js-apis-distributed-account.md) to implement smooth switchover between a distributed account and a system account.

## Before You Start

1. Request the ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS permission. For details, see [Requesting Permissions for system_basic Applications](../../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).

2. Import the **distributedAccount** module.

   ```ts
   import { distributedAccount, BusinessError } from '@kit.BasicServicesKit';
   ```

3. Obtain a **DistributedAccountAbility** instance.

   ```ts
   const distributedAccountAbility = distributedAccount.getDistributedAccountAbility();
   ```

## Logging In to a Distributed Account from the Current System Account

**Procedure**

1. Specify the distributed account to be logged in. Set **event** to **Ohos.account.event.LOGIN**.

   ```ts
   let distributedInfo: distributedAccount.DistributedInfo = {
       name: 'ZhangSan',
       id: '12345',
       event: 'Ohos.account.event.LOGIN',
   };
   ```

2. Use [setOsAccountDistributedInfo](../../reference/apis-basic-services-kit/js-apis-distributed-account.md#setosaccountdistributedinfo9) to log in to the distributed account.

   ```ts
   distributedAccountAbility.setOsAccountDistributedInfo(distributedInfo).then(() => {
       console.info('setOsAccountDistributedInfo successfully');
   }).catch((err: BusinessError) => {
       console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
   });
   ```

3. After the login, use [getOsAccountDistributedInfo](../../reference/apis-basic-services-kit/js-apis-distributed-account.md#getosaccountdistributedinfo9) to obtain information of the distributed account.

   ```ts
   distributedAccountAbility.getOsAccountDistributedInfo().then((data: distributedAccount.DistributedInfo) => {
       console.info('distributed information: ' + JSON.stringify(data));
   }).catch((err: BusinessError) => {
       console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
   });
   ```

## Logging Out of a Distributed Account to the Current System Account

**Procedure**

1. Specify the distributed account to be logged out. Set **event** to **Ohos.account.event.LOGOUT**.

   ```ts
   let distributedInfo: distributedAccount.DistributedInfo = {
       name: 'ZhangSan',
       id: '12345',
       event: 'Ohos.account.event.LOGOUT',
   };
   ```

2. Use [setOsAccountDistributedInfo](../../reference/apis-basic-services-kit/js-apis-distributed-account.md#setosaccountdistributedinfo9) to log out of the specified distributed account.

   ```ts
   distributedAccountAbility.setOsAccountDistributedInfo(distributedInfo).then(() => {
       console.info('setOsAccountDistributedInfo successfully');
   }).catch((err: BusinessError) => {
       console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
   });
   ```

## Logging In to a Distributed Account from a System Account

**Procedure**

1. Specify the system account and the distributed account to be logged in. Set **event** to **Ohos.account.event.LOGIN**.

   ```ts
   let localId: number = 100;
   let distributedInfo: distributedAccount.DistributedInfo = {
       name: 'ZhangSan',
       id: '12345',
       event: 'Ohos.account.event.LOGIN',
   };
   ```

2. Call [setOsAccountDistributedInfoByLocalId](../../reference/apis-basic-services-kit/js-apis-distributed-account-sys.md#setosaccountdistributedinfobylocalid10) to bind the specified distributed account to the current system account.

   ```ts
   distributedAccountAbility.setOsAccountDistributedInfoByLocalId(localId, distributedInfo).then(() => {
       console.info('setOsAccountDistributedInfoByLocalId successfully');
   }).catch((err: BusinessError) => {
       console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
   });
   ```

3. After the login, use [getOsAccountDistributedInfoByLocalId](../../reference/apis-basic-services-kit/js-apis-distributed-account-sys.md#getosaccountdistributedinfobylocalid10) to obtain information of the distributed account.

   ```ts
   distributedAccountAbility.getOsAccountDistributedInfoByLocalId(localId).then((data: distributedAccount.DistributedInfo) => {
       console.info('distributed information: ' + JSON.stringify(data));
   }).catch((err: BusinessError) => {
       console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
   });
   ```

## Logging Out of a Distributed Account to a System Account

**Procedure**

1. Specify the system account and the distributed account to be logged out. Set **event** to **Ohos.account.event.LOGOUT**.

   ```ts
   let localId: number = 100;
   let distributedInfo: distributedAccount.DistributedInfo = {
       name: 'ZhangSan',
       id: '12345',
       event: 'Ohos.account.event.LOGOUT',
   };
   ```

2. Use [setOsAccountDistributedInfoByLocalId](../../reference/apis-basic-services-kit/js-apis-distributed-account-sys.md#setosaccountdistributedinfobylocalid10) to log out of the specified distributed account to the target system account.

   ```ts
   distributedAccountAbility.setOsAccountDistributedInfoByLocalId(localId, distributedInfo).then(() => {
       console.info('setOsAccountDistributedInfoByLocalId successfully');
   }).catch((err: BusinessError) => {
       console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
   });
   ```
