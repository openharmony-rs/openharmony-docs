# @ohos.contact

��ģ���ṩ��ϵ�˹�������������������ϵ�ˡ�ɾ����ϵ�ˡ�������ϵ�˵ȡ�

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact-1) | ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact-2) | ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact-3) | ������ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [addContact](arkts-contacts-contact-addcontact-f.md#addContact-4) | ������ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md#addContactViaUI-1) | ͨ��UI����������ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [addContacts](arkts-contacts-contact-addcontacts-f.md#addContacts-1) | ����������ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact-1) | ɾ����ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact-2) | ɾ����ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact-3) | ɾ����ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deleteContact-4) | ɾ����ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasMatchedCallLog-1) | ����Ƿ��з���������ͨ����¼��Ĭ�ϲ�ѯ6Сʱ���ڵ�ͨ����¼���������Ӫ��ͨ����ʹ��Promise�첽�ص���<br/> |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasMatchedCallLog-2) | ����Ƿ��з���������ͨ����¼���������Ӫ��ͨ����ʹ��Promise�첽�ص���<br/> |
| [importContactsViaUI](arkts-contacts-contact-importcontactsviaui-f.md#importContactsViaUI-1) | ͨ��UI����������������ϵ�ˡ�<br/><br/> ÿ�����ɵ���100����ϵ�ˡ�<br/> |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact-1) | �жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��callback�첽�ص���<br/> |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact-2) | �жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��callback�첽�ص���<br/> |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact-3) | �жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��Promise�첽�ص���<br/> |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#isLocalContact-4) | �жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��Promise�첽�ص���<br/> |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard-1) | �ж��Ƿ�Ϊ���ҵ���Ƭ����ʹ��callback�첽�ص���<br/> |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard-2) | �ж��Ƿ�Ϊ���ҵ���Ƭ����ʹ��callback�첽�ص���<br/> |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard-3) | �ж��Ƿ�Ϊ���ҵ���Ƭ����ʹ��Promise�첽�ص���<br/> |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#isMyCard-4) | �ж��Ƿ�Ϊ���ҵ���Ƭ����ʹ��Promise�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-1) | ������ϵ��Ψһ��ʶ��key��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-2) | ����key��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-3) | ����key��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-4) | ����key��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-5) | ����key��ָ������(attrs)��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-6) | ����key��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-7) | ����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8) | ����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-9) | ����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-10) | ����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [queryContactSyncInfo](arkts-contacts-contact-querycontactsyncinfo-f.md#queryContactSyncInfo-1) | ��ѯ����Ӧ�ó������ڽ��е���ϵ��ͬ����Ϣ��<br/><br/>������ص���ϵ��ͬ����ϢΪ�գ�����÷���������ϵ��ͬ������ϵ��ͬ������ɡ�<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-1) | ��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-2) | ��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-3) | ����holder��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-4) | ����holder��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-5) | ����attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-6) | ����attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-7) | ����holder��attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-8) | ����holder��attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-9) | ����holder��attrs��ѯ������ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#queryContacts-10) | ����holder��attrs��ѯ������ϵ�ˡ�ʹ��Promise�첽�ص���<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-1) | ����email��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-2) | ����email��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-3) | ����email��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-4) | ����email��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-5) | ����email��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-6) | ����email��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-7) | ����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-8) | ����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-9) | ����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#queryContactsByEmail-10) | ����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-1) | ���ݵ绰�����ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڽ�������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-2) | ���ݵ绰�����ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڽ�������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-3) | ���ݵ绰�����holder��ѯ��ϵ�ˣ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-4) | ���ݵ绰�����holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-5) | ���ݵ绰�����attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-6) | ���ݵ绰�����attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-7) | ���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-8) | ���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-9) | ���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#queryContactsByPhoneNumber-10) | ���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��<br/>[queryContact](contact.queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;))<br/>�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����<br/> |
| [queryContactsCount](arkts-contacts-contact-querycontactscount-f.md#queryContactsCount-1) | ��ѯ������ϵ�˵�������ʹ��Promise�첽�ص���<br/> |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups-1) | ��ѯ��ϵ�˵�����Ⱥ�顣ʹ��callback�첽�ص���<br/> |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups-2) | ��ѯ��ϵ�˵�����Ⱥ�顣ʹ��callback�첽�ص���<br/> |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups-3) | ����holder��ѯ��ϵ�˵�����Ⱥ�顣ʹ��callback�첽�ص���<br/> |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups-4) | ����holder��ѯ��ϵ�˵�����Ⱥ�顣ʹ��callback�첽�ص���<br/> |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups-5) | ����holder��ѯ��ϵ�˵�����Ⱥ�顣ʹ��Promise�첽�ص���<br/> |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#queryGroups-6) | ����holder��ѯ��ϵ�˵�����Ⱥ�顣ʹ��Promise�첽�ص���<br/> |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders-1) | ��ѯ���д�����ϵ�˵�Ӧ����Ϣ�ࡣʹ��callback�첽�ص���<br/> |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders-2) | ��ѯ���д�����ϵ�˵�Ӧ����Ϣ�ࡣʹ��callback�첽�ص���<br/> |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders-3) | ��ѯ���д�����ϵ�˵�Ӧ����Ϣ�ࡣʹ��Promise�첽�ص���<br/> |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryHolders-4) | ��ѯ���д�����ϵ�˵�Ӧ����Ϣ�ࡣʹ��Promise�첽�ص���<br/> |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey-1) | ������ϵ�˵�id��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���<br/> |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey-2) | ������ϵ�˵�id��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���<br/> |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey-3) | ������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���<br/> |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey-4) | ������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���<br/> |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey-5) | ������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��Promise�첽�ص���<br/> |
| [queryKey](arkts-contacts-contact-querykey-f.md#queryKey-6) | ������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��Promise�첽�ص���<br/> |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard-1) | ��ѯ���ҵ���Ƭ����ʹ��callback�첽�ص���<br/> |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard-2) | ��ѯ���ҵ���Ƭ����ʹ��callback�첽�ص���<br/> |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard-3) | ��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��callback�첽�ص���<br/> |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard-4) | ��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��callback�첽�ص���<br/> |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard-5) | ��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��Promise�첽�ص���<br/> |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#queryMyCard-6) | ��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��Promise�첽�ص���<br/> |
| [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md#saveToExistingContactViaUI-1) | ���ñ�����������ϵ�˽ӿڣ�ѡ����ϵ��UI���沢��ɱ༭��ʹ��Promise�첽�ص���<br/> |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectContact-1) | ����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��callback�첽�ص���<br/> |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectContact-2) | ����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��Promise�첽�ص���<br/> |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-1) | ����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��callback�첽�ص���<br/> |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2) | ����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��Promise�첽�ص���<br/> |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-3) | ����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���棨ѡ����ϵ��ʱ֧�ִ���[ɸѡ����](arkts-contacts-contact-contactselectionoptions-i.md#ContactSelectionOptions)����ʹ��callback�첽�ص���<br/> |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-4) | ����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���棨ѡ����ϵ��ʱ֧�ִ���ɸѡ��������ʹ��Promise�첽�ص���<br/> |
| [syncContacts](arkts-contacts-contact-synccontacts-f.md#syncContacts-1) | ����ͬ�������ϵ������ϵ�����ݿ⡣<br/><br/> ��������ͬ��400����ϵ�ˡ����÷����봦��ǰ̨��<br/> |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact-1) | ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact-2) | ������ϵ�ˡ�ʹ��callback�첽�ص���<br/> |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact-3) | ������ϵ�ˣ�֧�ִ�����ϵ�˵������б���ʹ��callback�첽�ص���<br/> |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact-4) | ������ϵ�ˣ�֧�ִ�����ϵ�˵������б�����ʹ��callback�첽�ص���<br/> |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact-5) | ������ϵ�ˣ�֧�ִ�����ϵ�˵������б���ʹ��Promise�첽�ص���<br/> |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updateContact-6) | ������ϵ�ˣ�֧�ִ�����ϵ�˵������б�����ʹ��Promise�첽�ص���<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [Contact](arkts-contacts-contact-contact-c.md) | ��ϵ�˶����ࡣ<br/> |
| [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | ��ϵ�������б���һ����Ϊ���������ʶϣ����ѯ����ϵ�����ԡ�<br/>������Ϊnullʱ��Ĭ�ϲ�ѯȫ�����ԡ�<br/> |
| [Email](arkts-contacts-contact-email-c.md) | ��ϵ�˵����䡣<br/> |
| [Event](arkts-contacts-contact-event-c.md) | ��ϵ���¼��ࡣ<br/> |
| [Group](arkts-contacts-contact-group-c.md) | ��ϵ�˵�Ⱥ���ࡣ<br/> |
| [Holder](arkts-contacts-contact-holder-c.md) | ������ϵ�˵�Ӧ����Ϣ�ࡣ<br/> |
| [ImAddress](arkts-contacts-contact-imaddress-c.md) | ��ϵ�˵ļ�ʱ��Ϣ��ַ��<br/> |
| [Name](arkts-contacts-contact-name-c.md) | ��ϵ�˵������ࡣ<br/> |
| [NickName](arkts-contacts-contact-nickname-c.md) | ��ϵ�˵��ǳ��ࡣ<br/> |
| [Note](arkts-contacts-contact-note-c.md) | ��ϵ�˵ı�ע�ࡣ<br/> |
| [Organization](arkts-contacts-contact-organization-c.md) | ��ϵ�˵���֯�ࡣ<br/> |
| [PhoneNumber](arkts-contacts-contact-phonenumber-c.md) | ��ϵ�˵绰�����ࡣ<br/> |
| [Portrait](arkts-contacts-contact-portrait-c.md) | ��ϵ�˵�ͷ���ࡣ<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 22��ʼ��֧��ͨ��uri��[PixelMap](@ohos.multimedia.image:image.PixelMap)��ʽ������ϵ��ͷ����Դ(�ݲ�֧��ͨ��<br/>&gt; [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md#addContactViaUI-1)��<br/>&gt; [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md#saveToExistingContactViaUI-1)�ӿ�����)��<br/>&gt; <br/>&gt; uriΪ�ɷ��ʵ���ϵ��ͷ���ļ���ַ��[PixelMap](@ohos.multimedia.image:image.PixelMap)Ϊͨ����ϵ��ͷ����Դ���ɵ�<br/>&gt; [PixelMap](@ohos.multimedia.image:image.PixelMap)����<br/>&gt; <br/>&gt; ��API version 22��ʼ��֧��ͨ��uri��ʽ��ȡ��ϵ��ͷ����Դ���ø�ʽ��֧����<br/>&gt; [fs.open](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-open-f.md#open-1)��ʽ�򿪣��޷�ֱ����Image�������ʾ�����ȡ��ת��Ϊ<br/>&gt; [PixelMap](@ohos.multimedia.image:image.PixelMap)��ʽ��ʾ��<br/> |
| [PostalAddress](arkts-contacts-contact-postaladdress-c.md) | ��ϵ�˵�������ַ�ࡣ<br/> |
| [Relation](arkts-contacts-contact-relation-c.md) | ��ϵ�˵Ĺ�ϵ�ࡣ<br/> |
| [SipAddress](arkts-contacts-contact-sipaddress-c.md) | ��ϵ�˵ĻỰ����Э��(SIP)��ַ�ࡣ<br/> |
| [Website](arkts-contacts-contact-website-c.md) | ��ϵ�˵���վ��Ϣ�ࡣ<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContactSelectionFilter](arkts-contacts-contact-contactselectionfilter-i.md) | ��ϵ�˲�ѯ��������<br/> |
| [ContactSelectionOptions](arkts-contacts-contact-contactselectionoptions-i.md) | ѡ����ϵ��������<br/> |
| [ContactSyncInfo](arkts-contacts-contact-contactsyncinfo-i.md) | ����Ӧ�ó�����ص���ϵ��ͬ������Ϣ��<br/> |
| [ContactSyncProgress](arkts-contacts-contact-contactsyncprogress-i.md) | ��ϵ��ͬ�����ȵ���Ϣ��<br/><br/>����ͬ��ID����ǰ���κ������Ρ�<br/> |
| [DataFilter](arkts-contacts-contact-datafilter-i.md) | ��ϵ�����ݹ����<br/> |
| [FilterClause](arkts-contacts-contact-filterclause-i.md) | ��ϵ�˹������������ɸѡ����֮���ǡ����ߡ��Ĺ�ϵ������������������ͣ��������ֻ�ܰ���3��Ԫ�ء�<br/> |
| [FilterOptions](arkts-contacts-contact-filteroptions-i.md) | ��ϵ�˹��˲�����<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Attribute](arkts-contacts-contact-attribute-e.md) | ö�٣�����Ϊnumber����ϵ�������б���<br/>ͨ��JSON��ʽ�������ݡ�<br/> |
| [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md) | ͬ��ģʽ�����͡�<br/> |
| [DataField](arkts-contacts-contact-datafield-e.md) | ö�٣���ϵ�������ֶΡ�<br/> |
| [FilterCondition](arkts-contacts-contact-filtercondition-e.md) | ö�٣�����������<br/> |
| [FilterType](arkts-contacts-contact-filtertype-e.md) | ö�٣���ϵ�˹������͡�<br/> |

