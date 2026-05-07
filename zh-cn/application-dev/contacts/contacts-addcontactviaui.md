# 使用picker管理联系人

<!--Kit: Contacts Kit-->
<!--Subsystem: Applications-->
<!--Owner: @librahCode-->
<!--Designer: @jiayanhong-hw-->
<!--Tester: @shangzhijie-->
<!--Adviser: @zhang_yixin13-->
## 接口说明

| 接口名                  | 描述                                       |
| --------------------- | ------------------------------------------ |
| selectContacts(options: ContactSelectionOptions, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void | 调用选择联系人接口，打开选择联系人UI界面。使用callback异步回调。 |
| addContactViaUI(context: Context, contact: Contact): Promise&lt;number&gt; | 调用新建联系人接口，打开新建联系人UI界面，新建完成。使用Promise异步回调。 |
| saveToExistingContactViaUI(context: Context, contact: Contact): Promise&lt;number&gt; | 调用保存至已有联系人接口，选择联系人UI界面并完成编辑。使用Promise异步回调。 |

## 使用Picker选择联系人

当用户选择联系人的时候，通过Picker的方式，拉起联系人列表，引导用户完成界面操作，接口本身无需申请权限。

1. 导入相关的联系人模块。

   <!-- @[contacts_indexImport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Contacts/ContactsKit/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   import { contact } from '@kit.ContactsKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 调用联系人接口，拉起联系人列表，用户点击对应的联系人后返回。

   <!-- @[contacts_selectContactsByPicker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Contacts/ContactsKit/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   contact.selectContacts({
     isMultiSelect:false
   }, (err: BusinessError, data) => {
       if (err) {
         console.error('selectContact callback, errCode:' + err.code + ', errMessage:' + err.message);
           return;
       }
       console.info(`selectContact callback: success data->${JSON.stringify(data)}`);
   });

   ```

3. 完成操作，返回想要的data数据。


## 使用picker新建联系人

调用新建联系人接口，打开新建联系人UI界面，用户可在UI界面中填写并新建联系人。

<!-- @[contacts_addContactByPicker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Contacts/ContactsKit/entry/src/main/ets/pages/Index.ets) -->

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';
import { BusinessError } from '@kit.BasicServicesKit';


@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
    
  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          let contactInfo: contact.Contact = {
            name: {
              fullName: 'xxx'
            },
            phoneNumbers: [{
              phoneNumber: '138xxxxxx'
            }]
          };
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let promise = contact.addContactViaUI(context, contactInfo);
          promise.then((data) => {
              console.info(`Succeeded in add Contact via UI.data->${JSON.stringify(data)}`);
            }).catch((err: BusinessError) => {
              console.error(`Failed to add Contact via UI. Code: ${err.code}, message: ${err.message}`);
            });
        })
    }
  }
}
```

## 使用picker更新联系人信息

可以通过拉起picker，将选中的联系人信息更新到现有联系人中。

<!-- @[contacts_updateContactByPicker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Contacts/ContactsKit/entry/src/main/ets/pages/Index.ets) -->

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';
import { BusinessError } from '@kit.BasicServicesKit';


@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
    
  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          let contactInfo: contact.Contact = {
            id: 1,
            name: {
              fullName: 'xxx'
            },
            phoneNumbers: [{
              phoneNumber: '138xxxxxx'
            }]
          }
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let promise = contact.saveToExistingContactViaUI(context, contactInfo);
          promise.then((data) => {
              console.info(`Succeeded in save to existing Contact via UI.data->${JSON.stringify(data)}`);
            }).catch((err: BusinessError) => {
              console.error(`Failed to save to existing Contact via UI. Code: ${err.code}, message: ${err.message}`);
            });
        })
    }
  }
}
``` 