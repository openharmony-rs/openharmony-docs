# @ohos.contact

本模块提供联系人管理能力，包括添加联系人、删除联系人、更新联系人等。

**起始版本：** 7

<!--Device-unnamed-declare namespace contact--><!--Device-unnamed-declare namespace contact-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact-1) | 添加联系人。使用callback异步回调。 |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact-2) | 添加联系人。使用callback异步回调。 |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact-3) | 添加联系人。使用Promise异步回调。 |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact-4) | 添加联系人。使用Promise异步回调。 |
| [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md#addcontactviaui-1) | 通过UI交互创建联系人。使用Promise异步回调。 |
| [addContacts](arkts-contacts-contact-addcontacts-f.md#addcontacts-1) | 批量添加联系人。使用Promise异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact-1) | 删除联系人。使用callback异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact-2) | 删除联系人。使用callback异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact-3) | 删除联系人。使用Promise异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact-4) | 删除联系人。使用Promise异步回调。 |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasmatchedcalllog-1) | 检查是否有符合条件的通话记录，默认查询6小时以内的通话记录，仅针对运营商通话。使用Promise异步回调。 |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasmatchedcalllog-2) | 检查是否有符合条件的通话记录，仅针对运营商通话。使用Promise异步回调。 |
| [importContactsViaUI](arkts-contacts-contact-importcontactsviaui-f.md#importcontactsviaui-1) | 通过UI交互批量导入多个联系人。每次最多可导入100个联系人。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact-1) | 判断当前联系人id是否在电话簿中。使用callback异步回调。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact-2) | 判断当前联系人id是否在电话簿中。使用callback异步回调。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact-3) | 判断当前联系人id是否在电话簿中。使用Promise异步回调。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact-4) | 判断当前联系人id是否在电话簿中。使用Promise异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard-1) | 判断是否为“我的名片”。使用callback异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard-2) | 判断是否为“我的名片”。使用callback异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard-3) | 判断是否为“我的名片”。使用Promise异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard-4) | 判断是否为“我的名片”。使用Promise异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-1) | 根据联系人唯一标识符key查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-2) | 根据key查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-3) | 根据key和holder查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-4) | 根据key和holder查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-5) | 根据key和指定属性(attrs)查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-6) | 根据key和attrs查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-7) | 根据key、holder和attrs查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8) | 根据key、holder和attrs查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-9) | 根据key、holder和attrs查询联系人。使用Promise异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-10) | 根据key、holder和attrs查询联系人。使用Promise异步回调。 |
| [queryContactSyncInfo](arkts-contacts-contact-querycontactsyncinfo-f.md#querycontactsyncinfo-1) | 查询调用应用程序正在进行的联系人同步信息。如果返回的联系人同步信息为空，则调用方不进行联系人同步或联系人同步已完成。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-1) | 查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-2) | 查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-3) | 根据holder查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-4) | 根据holder查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-5) | 根据attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-6) | 根据attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-7) | 根据holder和attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-8) | 根据holder和attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-9) | 根据holder和attrs查询所有联系人。使用Promise异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts-10) | 根据holder和attrs查询所有联系人。使用Promise异步回调。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-1) | 根据email查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-2) | 根据email查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-3) | 根据email和holder查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-4) | 根据email和holder查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-5) | 根据email和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-6) | 根据email和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-7) | 根据email、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-8) | 根据email、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-9) | 根据email、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail-10) | 根据email、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-1) | 根据电话号码查询联系人。使用callback异步回调。该接口仅返回联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-2) | 根据电话号码查询联系人。使用callback异步回调。该接口仅返回联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-3) | 根据电话号码和holder查询联系人，使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-4) | 根据电话号码和holder查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-5) | 根据电话号码和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-6) | 根据电话号码和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-7) | 根据电话号码、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-8) | 根据电话号码、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-9) | 根据电话号码、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber-10) | 根据电话号码、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用[queryContact](arkts-contacts-contact-querycontact-f.md#querycontact-8)接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsCount](arkts-contacts-contact-querycontactscount-f.md#querycontactscount-1) | 查询所有联系人的数量。使用Promise异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups-1) | 查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups-2) | 查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups-3) | 根据holder查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups-4) | 根据holder查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups-5) | 根据holder查询联系人的所有群组。使用Promise异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups-6) | 根据holder查询联系人的所有群组。使用Promise异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders-1) | 查询所有创建联系人的应用信息类。使用callback异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders-2) | 查询所有创建联系人的应用信息类。使用callback异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders-3) | 查询所有创建联系人的应用信息类。使用Promise异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders-4) | 查询所有创建联系人的应用信息类。使用Promise异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey-1) | 根据联系人的id查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey-2) | 根据联系人的id查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey-3) | 根据联系人的id和holder查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey-4) | 根据联系人的id和holder查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey-5) | 根据联系人的id和holder查询联系人的唯一查询键key。使用Promise异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey-6) | 根据联系人的id和holder查询联系人的唯一查询键key。使用Promise异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard-1) | 查询“我的名片”。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard-2) | 查询“我的名片”。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard-3) | 查询“我的名片”（支持传入联系人的属性列表）。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard-4) | 查询“我的名片”（支持传入联系人的属性列表）。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard-5) | 查询“我的名片”（支持传入联系人的属性列表）。使用Promise异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard-6) | 查询“我的名片”（支持传入联系人的属性列表）。使用Promise异步回调。 |
| [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md#savetoexistingcontactviaui-1) | 调用保存至已有联系人接口，选择联系人UI界面并完成编辑。使用Promise异步回调。 |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectcontact-1) | 调用选择联系人接口，打开选择联系人UI界面。使用callback异步回调。 |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectcontact-2) | 调用选择联系人接口，打开选择联系人UI界面。使用Promise异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-1) | 调用选择联系人接口，打开选择联系人UI界面。使用callback异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2) | 调用选择联系人接口，打开选择联系人UI界面。使用Promise异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-3) | 调用选择联系人接口，打开选择联系人UI界面（选择联系人时支持传入[筛选条件](arkts-contacts-contact-contactselectionoptions-i.md)）。使用callback异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-4) | 调用选择联系人接口，打开选择联系人UI界面（选择联系人时支持传入筛选条件）。使用Promise异步回调。 |
| [syncContacts](arkts-contacts-contact-synccontacts-f.md#synccontacts-1) | 批量同步多个联系人至联系人数据库。最多可批量同步400个联系人。调用方必须处于前台。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact-1) | 更新联系人。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact-2) | 更新联系人。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact-3) | 更新联系人，支持传入联系人的属性列表。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact-4) | 更新联系人（支持传入联系人的属性列表）。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact-5) | 更新联系人，支持传入联系人的属性列表。使用Promise异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact-6) | 更新联系人（支持传入联系人的属性列表）。使用Promise异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Contact](arkts-contacts-contact-contact-c.md) | 联系人对象类。 |
| [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | 联系人属性列表，一般作为入参用来标识希望查询的联系人属性。当传入为null时，默认查询全部属性。 |
| [Email](arkts-contacts-contact-email-c.md) | 联系人的邮箱。 |
| [Event](arkts-contacts-contact-event-c.md) | 联系人事件类。 |
| [Group](arkts-contacts-contact-group-c.md) | 联系人的群组类。 |
| [Holder](arkts-contacts-contact-holder-c.md) | 创建联系人的应用信息类。 |
| [ImAddress](arkts-contacts-contact-imaddress-c.md) | 联系人的即时消息地址。 |
| [Name](arkts-contacts-contact-name-c.md) | 联系人的名字类。 |
| [NickName](arkts-contacts-contact-nickname-c.md) | 联系人的昵称类。 |
| [Note](arkts-contacts-contact-note-c.md) | 联系人的备注类。 |
| [Organization](arkts-contacts-contact-organization-c.md) | 联系人的组织类。 |
| [PhoneNumber](arkts-contacts-contact-phonenumber-c.md) | 联系人电话号码类。 |
| [Portrait](arkts-contacts-contact-portrait-c.md) | 联系人的头像类。 |
| [PostalAddress](arkts-contacts-contact-postaladdress-c.md) | 联系人的邮政地址类。 |
| [Relation](arkts-contacts-contact-relation-c.md) | 联系人的关系类。 |
| [SipAddress](arkts-contacts-contact-sipaddress-c.md) | 联系人的会话发起协议(SIP)地址类。 |
| [Website](arkts-contacts-contact-website-c.md) | 联系人的网站信息类。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContactSelectionFilter](arkts-contacts-contact-contactselectionfilter-i.md) | 联系人查询过滤器。 |
| [ContactSelectionOptions](arkts-contacts-contact-contactselectionoptions-i.md) | 选择联系人条件。 |
| [ContactSyncInfo](arkts-contacts-contact-contactsyncinfo-i.md) | 调用应用程序相关的联系人同步的信息。 |
| [ContactSyncProgress](arkts-contacts-contact-contactsyncprogress-i.md) | 联系人同步进度的信息。包含同步ID、当前批次和总批次。 |
| [DataFilter](arkts-contacts-contact-datafilter-i.md) | 联系人数据过滤项。 |
| [FilterClause](arkts-contacts-contact-filterclause-i.md) | 联系人过滤条件。多个筛选条件之间是“或者”的关系，如果参数是数组类型，数组最多只能包含3个元素。 |
| [FilterOptions](arkts-contacts-contact-filteroptions-i.md) | 联系人过滤参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Attribute](arkts-contacts-contact-attribute-e.md) | 枚举，类型为number。联系人属性列表。通过JSON格式创建数据。 |
| [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md) | 同步模式的类型。 |
| [DataField](arkts-contacts-contact-datafield-e.md) | 枚举，联系人数据字段。 |
| [FilterCondition](arkts-contacts-contact-filtercondition-e.md) | 枚举，过滤条件。 |
| [FilterType](arkts-contacts-contact-filtertype-e.md) | 枚举，联系人过滤类型。 |

