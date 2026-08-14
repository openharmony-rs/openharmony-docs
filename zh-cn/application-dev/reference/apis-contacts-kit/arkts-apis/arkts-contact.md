# @ohos.contact

本模块提供联系人管理能力，包括添加联系人、删除联系人、更新联系人等。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare namespace contact--><!--Device-unnamed-declare namespace contact-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact) | 添加联系人。使用callback异步回调。 |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact) | 添加联系人。使用callback异步回调。 |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact) | 添加联系人。使用Promise异步回调。 |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact) | 添加联系人。使用Promise异步回调。 |
| [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md#addContactViaUI) | 调用新建联系人接口，打开新建联系人UI界面。使用Promise异步回调。 |
| [addContacts](arkts-contacts-contact-addcontacts-f.md#addContacts) | 批量添加联系人。使用Promise异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact) | 删除联系人。使用callback异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact) | 删除联系人。使用callback异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact) | 删除联系人。使用Promise异步回调。 |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact) | 删除联系人。使用Promise异步回调。 |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasMatchedCallLog) | 检查是否有符合条件的通话记录，默认查询6小时以内的通话记录，仅针对运营商通话。使用Promise异步回调。 |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasMatchedCallLog) | 检查是否有符合条件的通话记录，仅针对运营商通话。使用Promise异步回调。 |
| [importContactsViaUI](arkts-contacts-contact-importcontactsviaui-f.md#importContactsViaUI) | 通过UI交互批量导入多个联系人。 每次最多可导入100个联系人。不支持导入联系人的头像。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact) | 判断当前联系人id是否在电话簿中。使用callback异步回调。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact) | 判断当前联系人id是否在电话簿中。使用callback异步回调。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact) | 判断当前联系人id是否在电话簿中。使用Promise异步回调。 |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact) | 判断当前联系人id是否在电话簿中。使用Promise异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard) | 判断是否为“我的名片”。使用callback异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard) | 判断是否为“我的名片”。使用callback异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard) | 判断是否为“我的名片”。使用Promise异步回调。 |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard) | 判断是否为“我的名片”。使用Promise异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据联系人唯一标识符key查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key和holder查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key和holder查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key和指定属性(attrs)查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key和attrs查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key、holder和attrs查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key、holder和attrs查询联系人。使用callback异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key、holder和attrs查询联系人。使用Promise异步回调。 |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) | 根据key、holder和attrs查询联系人。使用Promise异步回调。 |
| [queryContactSyncInfo](arkts-contacts-contact-querycontactsyncinfo-f.md#queryContactSyncInfo) | 查询调用应用程序正在进行的联系人同步信息。 如果返回的联系人同步信息为空，则调用方不进行联系人同步或联系人同步已完成。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据holder查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据holder查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据holder和attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据holder和attrs查询所有联系人。使用callback异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据holder和attrs查询所有联系人。使用Promise异步回调。 |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts) | 根据holder和attrs查询所有联系人。使用Promise异步回调。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email和holder查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email和holder查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail) | 根据email、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、Emails属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码查询联系人。使用callback异步回调。该接口仅返回联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码查询联系人。使用callback异步回调。该接口仅返回联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码和holder查询联系人，使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码和holder查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码、holder和attrs查询联系人。使用callback异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber) | 根据电话号码、holder和attrs查询联系人。使用Promise异步回调。该接口返回的列表仅包含联系人信息中的id、key、phoneNumbers属性。如果要查询联系人的所有信息，建议使用 [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact) 接口，根据该接口返回的属性key查询。应用在后台调用此接口获取联系人信息必须要申请对应的长时任务。 |
| [queryContactsCount](arkts-contacts-contact-querycontactscount-f.md#queryContactsCount) | 查询所有联系人的数量。使用Promise异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups) | 查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups) | 查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups) | 根据holder查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups) | 根据holder查询联系人的所有群组。使用callback异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups) | 根据holder查询联系人的所有群组。使用Promise异步回调。 |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups) | 根据holder查询联系人的所有群组。使用Promise异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders) | 查询所有创建联系人的应用信息类。使用callback异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders) | 查询所有创建联系人的应用信息类。使用callback异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders) | 查询所有创建联系人的应用信息类。使用Promise异步回调。 |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders) | 查询所有创建联系人的应用信息类。使用Promise异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey) | 根据联系人的id查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey) | 根据联系人的id查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey) | 根据联系人的id和holder查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey) | 根据联系人的id和holder查询联系人的唯一查询键key。使用callback异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey) | 根据联系人的id和holder查询联系人的唯一查询键key。使用Promise异步回调。 |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey) | 根据联系人的id和holder查询联系人的唯一查询键key。使用Promise异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard) | 查询“我的名片”。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard) | 查询“我的名片”。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard) | 查询“我的名片”（支持传入联系人的属性列表）。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard) | 查询“我的名片”（支持传入联系人的属性列表）。使用callback异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard) | 查询“我的名片”（支持传入联系人的属性列表）。使用Promise异步回调。 |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard) | 查询"我的名片"（支持传入联系人的属性列表）。使用Promise异步回调。 |
| [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md#saveToExistingContactViaUI) | 调用保存至已有联系人接口，选择联系人UI界面并完成编辑。使用Promise异步回调。 |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectContact) | 调用选择联系人接口，打开选择联系人UI界面。使用callback异步回调。 |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectContact) | 调用选择联系人接口，打开选择联系人UI界面。使用Promise异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts) | 调用选择联系人接口，打开选择联系人UI界面。使用callback异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts) | 调用选择联系人接口，打开选择联系人UI界面。使用Promise异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts) | 调用选择联系人接口，打开选择联系人UI界面（选择联系人时支持传入[筛选条件](arkts-contacts-contact-contactselectionoptions-i.md#ContactSelectionOptions)）。使用callback异步回调。 |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts) | 调用选择联系人接口，打开选择联系人UI界面（选择联系人时支持传入筛选条件）。使用Promise异步回调。 |
| [syncContacts](arkts-contacts-contact-synccontacts-f.md#syncContacts) | 批量同步多个联系人至联系人数据库。 每次最多可批量同步400个联系人。调用方必须处于前台。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact) | 更新联系人。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact) | 更新联系人。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact) | 更新联系人，支持传入联系人的属性列表。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact) | 更新联系人（支持传入联系人的属性列表）。使用callback异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact) | 更新联系人，支持传入联系人的属性列表。使用Promise异步回调。 |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact) | 更新联系人（支持传入联系人的属性列表）。使用Promise异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Contact](arkts-contacts-contact-contact-c.md) | 联系人对象类。 |
| [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | 联系人属性列表，一般作为入参用来标识希望查询的联系人属性。 当传入为null时，默认查询全部属性。 |
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
| [ContactSyncProgress](arkts-contacts-contact-contactsyncprogress-i.md) | 联系人同步进度的信息。 包含同步ID、当前批次和总批次。 |
| [DataFilter](arkts-contacts-contact-datafilter-i.md) | 联系人数据过滤项。 |
| [FilterClause](arkts-contacts-contact-filterclause-i.md) | 联系人过滤条件。多个筛选条件之间是“或者”的关系，如果参数是数组类型，数组最多只能包含3个元素。 |
| [FilterOptions](arkts-contacts-contact-filteroptions-i.md) | 联系人过滤参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Attribute](arkts-contacts-contact-attribute-e.md) | 枚举，类型为number。联系人属性列表。 通过JSON格式创建数据。 |
| [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md) | 同步模式的类型。 |
| [DataField](arkts-contacts-contact-datafield-e.md) | 枚举，联系人数据字段。 |
| [FilterCondition](arkts-contacts-contact-filtercondition-e.md) | 枚举，过滤条件。 |
| [FilterType](arkts-contacts-contact-filtertype-e.md) | 枚举，联系人过滤类型。 |

