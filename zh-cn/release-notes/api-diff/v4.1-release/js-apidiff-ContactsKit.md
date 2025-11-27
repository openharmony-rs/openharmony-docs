| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace contact<br>差异内容：declare namespace contact|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function addContact(contact: Contact, callback: AsyncCallback\<number>): void;<br>差异内容：function addContact(contact: Contact, callback: AsyncCallback\<number>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function addContact(context: Context, contact: Contact, callback: AsyncCallback\<number>): void;<br>差异内容：function addContact(context: Context, contact: Contact, callback: AsyncCallback\<number>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function addContact(contact: Contact): Promise\<number>;<br>差异内容：function addContact(contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function addContact(context: Context, contact: Contact): Promise\<number>;<br>差异内容：function addContact(context: Context, contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function selectContact(callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function selectContact(callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function selectContact(): Promise\<Array\<Contact>>;<br>差异内容：function selectContact(): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function selectContacts(callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function selectContacts(callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function selectContacts(): Promise\<Array\<Contact>>;<br>差异内容：function selectContacts(): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function selectContacts(options: ContactSelectionOptions): Promise\<Array\<Contact>>;<br>差异内容：function selectContacts(options: ContactSelectionOptions): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function deleteContact(key: string, callback: AsyncCallback\<void>): void;<br>差异内容：function deleteContact(key: string, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function deleteContact(context: Context, key: string, callback: AsyncCallback\<void>): void;<br>差异内容：function deleteContact(context: Context, key: string, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function deleteContact(key: string): Promise\<void>;<br>差异内容：function deleteContact(key: string): Promise\<void>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function deleteContact(context: Context, key: string): Promise\<void>;<br>差异内容：function deleteContact(context: Context, key: string): Promise\<void>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(key: string, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(key: string, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(context: Context, key: string, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(context: Context, key: string, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(context: Context, key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(context: Context, key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(context: Context, key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(context: Context, key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;<br>差异内容：function queryContact(key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContact(context: Context, key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;<br>差异内容：function queryContact(context: Context, key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(context: Context, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(context: Context, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(context: Context, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContacts(context: Context, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>差异内容：function queryContacts(holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContacts(context: Context, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>差异内容：function queryContacts(context: Context, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(email: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(email: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(context: Context, email: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(context: Context, email: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(context: Context, email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(context: Context, email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(context: Context, email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(context: Context, email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(context: Context, email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByEmail(context: Context, email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>差异内容：function queryContactsByEmail(email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByEmail(context: Context, email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>差异内容：function queryContactsByEmail(context: Context, email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>差异内容：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>差异内容：function queryContactsByPhoneNumber(phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>差异内容：function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryGroups(callback: AsyncCallback\<Array\<Group>>): void;<br>差异内容：function queryGroups(callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryGroups(context: Context, callback: AsyncCallback\<Array\<Group>>): void;<br>差异内容：function queryGroups(context: Context, callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryGroups(holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;<br>差异内容：function queryGroups(holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryGroups(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;<br>差异内容：function queryGroups(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryGroups(holder?: Holder): Promise\<Array\<Group>>;<br>差异内容：function queryGroups(holder?: Holder): Promise\<Array\<Group>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryGroups(context: Context, holder?: Holder): Promise\<Array\<Group>>;<br>差异内容：function queryGroups(context: Context, holder?: Holder): Promise\<Array\<Group>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryHolders(callback: AsyncCallback\<Array\<Holder>>): void;<br>差异内容：function queryHolders(callback: AsyncCallback\<Array\<Holder>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryHolders(context: Context, callback: AsyncCallback\<Array\<Holder>>): void;<br>差异内容：function queryHolders(context: Context, callback: AsyncCallback\<Array\<Holder>>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryHolders(): Promise\<Array\<Holder>>;<br>差异内容：function queryHolders(): Promise\<Array\<Holder>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryHolders(context: Context): Promise\<Array\<Holder>>;<br>差异内容：function queryHolders(context: Context): Promise\<Array\<Holder>>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryKey(id: number, callback: AsyncCallback\<string>): void;<br>差异内容：function queryKey(id: number, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryKey(context: Context, id: number, callback: AsyncCallback\<string>): void;<br>差异内容：function queryKey(context: Context, id: number, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryKey(id: number, holder: Holder, callback: AsyncCallback\<string>): void;<br>差异内容：function queryKey(id: number, holder: Holder, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryKey(context: Context, id: number, holder: Holder, callback: AsyncCallback\<string>): void;<br>差异内容：function queryKey(context: Context, id: number, holder: Holder, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryKey(id: number, holder?: Holder): Promise\<string>;<br>差异内容：function queryKey(id: number, holder?: Holder): Promise\<string>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryKey(context: Context, id: number, holder?: Holder): Promise\<string>;<br>差异内容：function queryKey(context: Context, id: number, holder?: Holder): Promise\<string>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryMyCard(callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryMyCard(callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryMyCard(context: Context, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryMyCard(context: Context, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryMyCard(attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryMyCard(attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryMyCard(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>差异内容：function queryMyCard(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryMyCard(attrs?: ContactAttributes): Promise\<Contact>;<br>差异内容：function queryMyCard(attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function queryMyCard(context: Context, attrs?: ContactAttributes): Promise\<Contact>;<br>差异内容：function queryMyCard(context: Context, attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function updateContact(contact: Contact, callback: AsyncCallback\<void>): void;<br>差异内容：function updateContact(contact: Contact, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function updateContact(context: Context, contact: Contact, callback: AsyncCallback\<void>): void;<br>差异内容：function updateContact(context: Context, contact: Contact, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;<br>差异内容：function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;<br>差异内容：function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function updateContact(contact: Contact, attrs?: ContactAttributes): Promise\<void>;<br>差异内容：function updateContact(contact: Contact, attrs?: ContactAttributes): Promise\<void>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise\<void>;<br>差异内容：function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise\<void>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isLocalContact(id: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isLocalContact(id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isLocalContact(context: Context, id: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isLocalContact(context: Context, id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isLocalContact(id: number): Promise\<boolean>;<br>差异内容：function isLocalContact(id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isLocalContact(context: Context, id: number): Promise\<boolean>;<br>差异内容：function isLocalContact(context: Context, id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isMyCard(id: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isMyCard(id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isMyCard(context: Context, id: number, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isMyCard(context: Context, id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isMyCard(id: number): Promise\<boolean>;<br>差异内容：function isMyCard(id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function isMyCard(context: Context, id: number): Promise\<boolean>;<br>差异内容：function isMyCard(context: Context, id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：interface ContactSelectionOptions<br>差异内容：interface ContactSelectionOptions|api/@ohos.contact.d.ts|
|新增API|NA|类名：ContactSelectionOptions；<br>API声明：isMultiSelect?: boolean;<br>差异内容：isMultiSelect?: boolean;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Contact<br>差异内容：class Contact|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：static readonly INVALID_CONTACT_ID: -1;<br>差异内容：static readonly INVALID_CONTACT_ID: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：readonly id?: number;<br>差异内容：readonly id?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：readonly key?: string;<br>差异内容：readonly key?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：contactAttributes?: ContactAttributes;<br>差异内容：contactAttributes?: ContactAttributes;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：emails?: Email[];<br>差异内容：emails?: Email[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：events?: Event[];<br>差异内容：events?: Event[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：groups?: Group[];<br>差异内容：groups?: Group[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：imAddresses?: ImAddress[];<br>差异内容：imAddresses?: ImAddress[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：phoneNumbers?: PhoneNumber[];<br>差异内容：phoneNumbers?: PhoneNumber[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：portrait?: Portrait;<br>差异内容：portrait?: Portrait;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：postalAddresses?: PostalAddress[];<br>差异内容：postalAddresses?: PostalAddress[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：relations?: Relation[];<br>差异内容：relations?: Relation[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：sipAddresses?: SipAddress[];<br>差异内容：sipAddresses?: SipAddress[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：websites?: Website[];<br>差异内容：websites?: Website[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：name?: Name;<br>差异内容：name?: Name;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：nickName?: NickName;<br>差异内容：nickName?: NickName;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：note?: Note;<br>差异内容：note?: Note;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Contact；<br>API声明：organization?: Organization;<br>差异内容：organization?: Organization;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class ContactAttributes<br>差异内容：class ContactAttributes|api/@ohos.contact.d.ts|
|新增API|NA|类名：ContactAttributes；<br>API声明：attributes: Attribute[];<br>差异内容：attributes: Attribute[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：enum Attribute<br>差异内容：enum Attribute|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_CONTACT_EVENT<br>差异内容：ATTR_CONTACT_EVENT|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_EMAIL<br>差异内容：ATTR_EMAIL|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_GROUP_MEMBERSHIP<br>差异内容：ATTR_GROUP_MEMBERSHIP|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_IM<br>差异内容：ATTR_IM|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_NAME<br>差异内容：ATTR_NAME|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_NICKNAME<br>差异内容：ATTR_NICKNAME|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_NOTE<br>差异内容：ATTR_NOTE|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_ORGANIZATION<br>差异内容：ATTR_ORGANIZATION|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_PHONE<br>差异内容：ATTR_PHONE|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_PORTRAIT<br>差异内容：ATTR_PORTRAIT|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_POSTAL_ADDRESS<br>差异内容：ATTR_POSTAL_ADDRESS|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_RELATION<br>差异内容：ATTR_RELATION|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_SIP_ADDRESS<br>差异内容：ATTR_SIP_ADDRESS|api/@ohos.contact.d.ts|
|新增API|NA|类名：Attribute；<br>API声明：ATTR_WEBSITE<br>差异内容：ATTR_WEBSITE|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Email<br>差异内容：class Email|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：static readonly CUSTOM_LABEL: 0;<br>差异内容：static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：static readonly EMAIL_HOME: 1;<br>差异内容：static readonly EMAIL_HOME: 1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：static readonly EMAIL_WORK: 2;<br>差异内容：static readonly EMAIL_WORK: 2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：static readonly EMAIL_OTHER: 3;<br>差异内容：static readonly EMAIL_OTHER: 3;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：static readonly INVALID_LABEL_ID: -1;<br>差异内容：static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：email: string;<br>差异内容：email: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：labelName?: string;<br>差异内容：labelName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：displayName?: string;<br>差异内容：displayName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Email；<br>API声明：labelId?: number;<br>差异内容：labelId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Event<br>差异内容：class Event|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：static readonly CUSTOM_LABEL: 0;<br>差异内容：static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：static readonly EVENT_ANNIVERSARY: 1;<br>差异内容：static readonly EVENT_ANNIVERSARY: 1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：static readonly EVENT_OTHER: 2;<br>差异内容：static readonly EVENT_OTHER: 2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：static readonly EVENT_BIRTHDAY: 3;<br>差异内容：static readonly EVENT_BIRTHDAY: 3;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：static readonly INVALID_LABEL_ID: -1;<br>差异内容：static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：eventDate: string;<br>差异内容：eventDate: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：labelName?: string;<br>差异内容：labelName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Event；<br>API声明：labelId?: number;<br>差异内容：labelId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Group<br>差异内容：class Group|api/@ohos.contact.d.ts|
|新增API|NA|类名：Group；<br>API声明：groupId?: number;<br>差异内容：groupId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Group；<br>API声明：title: string;<br>差异内容：title: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Holder<br>差异内容：class Holder|api/@ohos.contact.d.ts|
|新增API|NA|类名：Holder；<br>API声明：readonly bundleName: string;<br>差异内容：readonly bundleName: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Holder；<br>API声明：readonly displayName?: string;<br>差异内容：readonly displayName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Holder；<br>API声明：holderId?: number;<br>差异内容：holderId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class ImAddress<br>差异内容：class ImAddress|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly CUSTOM_LABEL: -1;<br>差异内容：static readonly CUSTOM_LABEL: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly IM_AIM: 0;<br>差异内容：static readonly IM_AIM: 0;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly IM_MSN: 1;<br>差异内容：static readonly IM_MSN: 1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly IM_YAHOO: 2;<br>差异内容：static readonly IM_YAHOO: 2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly IM_SKYPE: 3;<br>差异内容：static readonly IM_SKYPE: 3;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly IM_QQ: 4;<br>差异内容：static readonly IM_QQ: 4;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly IM_ICQ: 6;<br>差异内容：static readonly IM_ICQ: 6;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly IM_JABBER: 7;<br>差异内容：static readonly IM_JABBER: 7;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：static readonly INVALID_LABEL_ID: -2;<br>差异内容：static readonly INVALID_LABEL_ID: -2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：imAddress: string;<br>差异内容：imAddress: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：labelName?: string;<br>差异内容：labelName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ImAddress；<br>API声明：labelId?: number;<br>差异内容：labelId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Name<br>差异内容：class Name|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：familyName?: string;<br>差异内容：familyName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：familyNamePhonetic?: string;<br>差异内容：familyNamePhonetic?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：fullName: string;<br>差异内容：fullName: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：givenName?: string;<br>差异内容：givenName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：givenNamePhonetic?: string;<br>差异内容：givenNamePhonetic?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：middleName?: string;<br>差异内容：middleName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：middleNamePhonetic?: string;<br>差异内容：middleNamePhonetic?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：namePrefix?: string;<br>差异内容：namePrefix?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Name；<br>API声明：nameSuffix?: string;<br>差异内容：nameSuffix?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class NickName<br>差异内容：class NickName|api/@ohos.contact.d.ts|
|新增API|NA|类名：NickName；<br>API声明：nickName: string;<br>差异内容：nickName: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Note<br>差异内容：class Note|api/@ohos.contact.d.ts|
|新增API|NA|类名：Note；<br>API声明：noteContent: string;<br>差异内容：noteContent: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Organization<br>差异内容：class Organization|api/@ohos.contact.d.ts|
|新增API|NA|类名：Organization；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Organization；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class PhoneNumber<br>差异内容：class PhoneNumber|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly CUSTOM_LABEL: 0;<br>差异内容：static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_HOME: 1;<br>差异内容：static readonly NUM_HOME: 1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_MOBILE: 2;<br>差异内容：static readonly NUM_MOBILE: 2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_WORK: 3;<br>差异内容：static readonly NUM_WORK: 3;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_FAX_WORK: 4;<br>差异内容：static readonly NUM_FAX_WORK: 4;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_FAX_HOME: 5;<br>差异内容：static readonly NUM_FAX_HOME: 5;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_PAGER: 6;<br>差异内容：static readonly NUM_PAGER: 6;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_OTHER: 7;<br>差异内容：static readonly NUM_OTHER: 7;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_CALLBACK: 8;<br>差异内容：static readonly NUM_CALLBACK: 8;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_CAR: 9;<br>差异内容：static readonly NUM_CAR: 9;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_COMPANY_MAIN: 10;<br>差异内容：static readonly NUM_COMPANY_MAIN: 10;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_ISDN: 11;<br>差异内容：static readonly NUM_ISDN: 11;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_MAIN: 12;<br>差异内容：static readonly NUM_MAIN: 12;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_OTHER_FAX: 13;<br>差异内容：static readonly NUM_OTHER_FAX: 13;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_RADIO: 14;<br>差异内容：static readonly NUM_RADIO: 14;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_TELEX: 15;<br>差异内容：static readonly NUM_TELEX: 15;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_TTY_TDD: 16;<br>差异内容：static readonly NUM_TTY_TDD: 16;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_WORK_MOBILE: 17;<br>差异内容：static readonly NUM_WORK_MOBILE: 17;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_WORK_PAGER: 18;<br>差异内容：static readonly NUM_WORK_PAGER: 18;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_ASSISTANT: 19;<br>差异内容：static readonly NUM_ASSISTANT: 19;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly NUM_MMS: 20;<br>差异内容：static readonly NUM_MMS: 20;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：static readonly INVALID_LABEL_ID: -1;<br>差异内容：static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：labelName?: string;<br>差异内容：labelName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：phoneNumber: string;<br>差异内容：phoneNumber: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PhoneNumber；<br>API声明：labelId?: number;<br>差异内容：labelId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Portrait<br>差异内容：class Portrait|api/@ohos.contact.d.ts|
|新增API|NA|类名：Portrait；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class PostalAddress<br>差异内容：class PostalAddress|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：static readonly CUSTOM_LABEL: 0;<br>差异内容：static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：static readonly ADDR_HOME: 1;<br>差异内容：static readonly ADDR_HOME: 1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：static readonly ADDR_WORK: 2;<br>差异内容：static readonly ADDR_WORK: 2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：static readonly ADDR_OTHER: 3;<br>差异内容：static readonly ADDR_OTHER: 3;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：static readonly INVALID_LABEL_ID: -1;<br>差异内容：static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：city?: string;<br>差异内容：city?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：country?: string;<br>差异内容：country?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：labelName?: string;<br>差异内容：labelName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：neighborhood?: string;<br>差异内容：neighborhood?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：pobox?: string;<br>差异内容：pobox?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：postalAddress: string;<br>差异内容：postalAddress: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：postcode?: string;<br>差异内容：postcode?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：region?: string;<br>差异内容：region?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：street?: string;<br>差异内容：street?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：PostalAddress；<br>API声明：labelId?: number;<br>差异内容：labelId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Relation<br>差异内容：class Relation|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly CUSTOM_LABEL: 0;<br>差异内容：static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_ASSISTANT: 1;<br>差异内容：static readonly RELATION_ASSISTANT: 1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_BROTHER: 2;<br>差异内容：static readonly RELATION_BROTHER: 2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_CHILD: 3;<br>差异内容：static readonly RELATION_CHILD: 3;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_DOMESTIC_PARTNER: 4;<br>差异内容：static readonly RELATION_DOMESTIC_PARTNER: 4;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_FATHER: 5;<br>差异内容：static readonly RELATION_FATHER: 5;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_FRIEND: 6;<br>差异内容：static readonly RELATION_FRIEND: 6;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_MANAGER: 7;<br>差异内容：static readonly RELATION_MANAGER: 7;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_MOTHER: 8;<br>差异内容：static readonly RELATION_MOTHER: 8;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_PARENT: 9;<br>差异内容：static readonly RELATION_PARENT: 9;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_PARTNER: 10;<br>差异内容：static readonly RELATION_PARTNER: 10;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_REFERRED_BY: 11;<br>差异内容：static readonly RELATION_REFERRED_BY: 11;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_RELATIVE: 12;<br>差异内容：static readonly RELATION_RELATIVE: 12;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_SISTER: 13;<br>差异内容：static readonly RELATION_SISTER: 13;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly RELATION_SPOUSE: 14;<br>差异内容：static readonly RELATION_SPOUSE: 14;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：static readonly INVALID_LABEL_ID: -1;<br>差异内容：static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：labelName?: string;<br>差异内容：labelName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：relationName: string;<br>差异内容：relationName: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：Relation；<br>API声明：labelId?: number;<br>差异内容：labelId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class SipAddress<br>差异内容：class SipAddress|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：static readonly CUSTOM_LABEL: 0;<br>差异内容：static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：static readonly SIP_HOME: 1;<br>差异内容：static readonly SIP_HOME: 1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：static readonly SIP_WORK: 2;<br>差异内容：static readonly SIP_WORK: 2;|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：static readonly SIP_OTHER: 3;<br>差异内容：static readonly SIP_OTHER: 3;|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：static readonly INVALID_LABEL_ID: -1;<br>差异内容：static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：labelName?: string;<br>差异内容：labelName?: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：sipAddress: string;<br>差异内容：sipAddress: string;|api/@ohos.contact.d.ts|
|新增API|NA|类名：SipAddress；<br>API声明：labelId?: number;<br>差异内容：labelId?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：class Website<br>差异内容：class Website|api/@ohos.contact.d.ts|
|新增API|NA|类名：Website；<br>API声明：website: string;<br>差异内容：website: string;|api/@ohos.contact.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.contact.d.ts<br>差异内容：ContactsKit|api/@ohos.contact.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.ContactsKit.d.ts<br>差异内容：ContactsKit|kits/@kit.ContactsKit.d.ts|
