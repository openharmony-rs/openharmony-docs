# 联系人管理（受限开放）

<!--Kit: Contacts Kit-->
<!--Subsystem: Applications-->
<!--Owner: @librahCode-->
<!--Designer: @jiayanhong-hw-->
<!--Tester: @shangzhijie-->
<!--Adviser: @zhang_yixin13-->

若需要在应用内实现管理联系人的功能，可以使用permissions接口获取应用对联系人的编辑权限。

1. 声明接口调用所需要的权限。
   <!--RP2-->
   - 删除联系人，调用deleteContact接口，需要配置ohos.permission.WRITE_CONTACTS权限，权限级别为system_basic。
   - 更新联系人，调用updateContact接口，需要配置ohos.permission.WRITE_CONTACTS权限，权限级别为system_basic。
   - 查询联系人，调用queryContact接口，需要配置ohos.permission.READ_CONTACTS权限，权限级别为system_basic。

     在申请权限前，请保证符合[权限使用的基本原则](../security/AccessToken/app-permission-mgmt-overview.md#权限使用的基本原则)。然后参考[申请应用权限](../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)声明对应权限。
   <!--RP2End-->

2. 设置一个需要的Permissions数组变量。

3. 执行对应联系人的权限操作。

   <!-- @[contacts_addContactByPermissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Contacts/ContactsKit/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   // 示例代码
   import { common, abilityAccessCtrl, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
   import { contact } from '@kit.ContactsKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   @Entry
   @Component
   struct Contact {
     addContactByPermissions() {
       // 在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
       let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
       const permissions: Array<Permissions> = ['ohos.permission.WRITE_CONTACTS'];
       const contactInfo: contact.Contact = {
         name: { fullName: '王小明' },
         phoneNumbers: [{ phoneNumber: '139xxxxxxxx' }]
       };
       abilityAccessCtrl.createAtManager().requestPermissionsFromUser(context, permissions).
         then((result: PermissionRequestResult) => {
          if (result.authResults[0] !== 0) { // 0 表示请求权限成功，其他任何非零值表示请求失败
            console.error('request contact permissions failed');
            return;
          }
          contact.addContact(context, contactInfo).then((data) => {
            console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
          }).catch((err: BusinessError) => {
            console.error(`Failed to add Contact. Code: ${err.code}, message: ${err.message}`);
          });
        }).catch((err: BusinessError) => {
            console.error(`Failed to createAtManager. Code: ${err.code}, message: ${err.message}`);
        });
     }

     build() {
       Row() {
         Column() {
           Button('添加联系人')
             .onClick(() => {
               this.addContactByPermissions();
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```