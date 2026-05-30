| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace contact<br>Differences: declare namespace contact|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function addContact(contact: Contact, callback: AsyncCallback\<number>): void;<br>Differences: function addContact(contact: Contact, callback: AsyncCallback\<number>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function addContact(context: Context, contact: Contact, callback: AsyncCallback\<number>): void;<br>Differences: function addContact(context: Context, contact: Contact, callback: AsyncCallback\<number>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function addContact(contact: Contact): Promise\<number>;<br>Differences: function addContact(contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function addContact(context: Context, contact: Contact): Promise\<number>;<br>Differences: function addContact(context: Context, contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function selectContact(callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function selectContact(callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function selectContact(): Promise\<Array\<Contact>>;<br>Differences: function selectContact(): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function selectContacts(callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function selectContacts(callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function selectContacts(): Promise\<Array\<Contact>>;<br>Differences: function selectContacts(): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function selectContacts(options: ContactSelectionOptions): Promise\<Array\<Contact>>;<br>Differences: function selectContacts(options: ContactSelectionOptions): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function deleteContact(key: string, callback: AsyncCallback\<void>): void;<br>Differences: function deleteContact(key: string, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function deleteContact(context: Context, key: string, callback: AsyncCallback\<void>): void;<br>Differences: function deleteContact(context: Context, key: string, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function deleteContact(key: string): Promise\<void>;<br>Differences: function deleteContact(key: string): Promise\<void>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function deleteContact(context: Context, key: string): Promise\<void>;<br>Differences: function deleteContact(context: Context, key: string): Promise\<void>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(key: string, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(key: string, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(context: Context, key: string, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(context: Context, key: string, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(context: Context, key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(context: Context, key: string, holder: Holder, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(context: Context, key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(context: Context, key: string, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;<br>Differences: function queryContact(key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContact(context: Context, key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;<br>Differences: function queryContact(context: Context, key: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(context: Context, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(context: Context, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(context: Context, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContacts(context: Context, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>Differences: function queryContacts(holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContacts(context: Context, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>Differences: function queryContacts(context: Context, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(email: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(email: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(context: Context, email: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(context: Context, email: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(context: Context, email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(context: Context, email: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(context: Context, email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(context: Context, email: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(context: Context, email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByEmail(context: Context, email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>Differences: function queryContactsByEmail(email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByEmail(context: Context, email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>Differences: function queryContactsByEmail(context: Context, email: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;<br>Differences: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback\<Array\<Contact>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>Differences: function queryContactsByPhoneNumber(phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;<br>Differences: function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise\<Array\<Contact>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryGroups(callback: AsyncCallback\<Array\<Group>>): void;<br>Differences: function queryGroups(callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryGroups(context: Context, callback: AsyncCallback\<Array\<Group>>): void;<br>Differences: function queryGroups(context: Context, callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryGroups(holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;<br>Differences: function queryGroups(holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryGroups(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;<br>Differences: function queryGroups(context: Context, holder: Holder, callback: AsyncCallback\<Array\<Group>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryGroups(holder?: Holder): Promise\<Array\<Group>>;<br>Differences: function queryGroups(holder?: Holder): Promise\<Array\<Group>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryGroups(context: Context, holder?: Holder): Promise\<Array\<Group>>;<br>Differences: function queryGroups(context: Context, holder?: Holder): Promise\<Array\<Group>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryHolders(callback: AsyncCallback\<Array\<Holder>>): void;<br>Differences: function queryHolders(callback: AsyncCallback\<Array\<Holder>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryHolders(context: Context, callback: AsyncCallback\<Array\<Holder>>): void;<br>Differences: function queryHolders(context: Context, callback: AsyncCallback\<Array\<Holder>>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryHolders(): Promise\<Array\<Holder>>;<br>Differences: function queryHolders(): Promise\<Array\<Holder>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryHolders(context: Context): Promise\<Array\<Holder>>;<br>Differences: function queryHolders(context: Context): Promise\<Array\<Holder>>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryKey(id: number, callback: AsyncCallback\<string>): void;<br>Differences: function queryKey(id: number, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryKey(context: Context, id: number, callback: AsyncCallback\<string>): void;<br>Differences: function queryKey(context: Context, id: number, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryKey(id: number, holder: Holder, callback: AsyncCallback\<string>): void;<br>Differences: function queryKey(id: number, holder: Holder, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryKey(context: Context, id: number, holder: Holder, callback: AsyncCallback\<string>): void;<br>Differences: function queryKey(context: Context, id: number, holder: Holder, callback: AsyncCallback\<string>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryKey(id: number, holder?: Holder): Promise\<string>;<br>Differences: function queryKey(id: number, holder?: Holder): Promise\<string>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryKey(context: Context, id: number, holder?: Holder): Promise\<string>;<br>Differences: function queryKey(context: Context, id: number, holder?: Holder): Promise\<string>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryMyCard(callback: AsyncCallback\<Contact>): void;<br>Differences: function queryMyCard(callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryMyCard(context: Context, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryMyCard(context: Context, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryMyCard(attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryMyCard(attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryMyCard(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;<br>Differences: function queryMyCard(context: Context, attrs: ContactAttributes, callback: AsyncCallback\<Contact>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryMyCard(attrs?: ContactAttributes): Promise\<Contact>;<br>Differences: function queryMyCard(attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function queryMyCard(context: Context, attrs?: ContactAttributes): Promise\<Contact>;<br>Differences: function queryMyCard(context: Context, attrs?: ContactAttributes): Promise\<Contact>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function updateContact(contact: Contact, callback: AsyncCallback\<void>): void;<br>Differences: function updateContact(contact: Contact, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function updateContact(context: Context, contact: Contact, callback: AsyncCallback\<void>): void;<br>Differences: function updateContact(context: Context, contact: Contact, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;<br>Differences: function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;<br>Differences: function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback\<void>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function updateContact(contact: Contact, attrs?: ContactAttributes): Promise\<void>;<br>Differences: function updateContact(contact: Contact, attrs?: ContactAttributes): Promise\<void>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise\<void>;<br>Differences: function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise\<void>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isLocalContact(id: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isLocalContact(id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isLocalContact(context: Context, id: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isLocalContact(context: Context, id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isLocalContact(id: number): Promise\<boolean>;<br>Differences: function isLocalContact(id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isLocalContact(context: Context, id: number): Promise\<boolean>;<br>Differences: function isLocalContact(context: Context, id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isMyCard(id: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isMyCard(id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isMyCard(context: Context, id: number, callback: AsyncCallback\<boolean>): void;<br>Differences: function isMyCard(context: Context, id: number, callback: AsyncCallback\<boolean>): void;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isMyCard(id: number): Promise\<boolean>;<br>Differences: function isMyCard(id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: function isMyCard(context: Context, id: number): Promise\<boolean>;<br>Differences: function isMyCard(context: Context, id: number): Promise\<boolean>;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: interface ContactSelectionOptions<br>Differences: interface ContactSelectionOptions|api/@ohos.contact.d.ts|
|New API|NA|Class name: ContactSelectionOptions;<br>API declaration: isMultiSelect?: boolean;<br>Differences: isMultiSelect?: boolean;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Contact<br>Differences: class Contact|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: static readonly INVALID_CONTACT_ID: -1;<br>Differences: static readonly INVALID_CONTACT_ID: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: readonly id?: number;<br>Differences: readonly id?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: readonly key?: string;<br>Differences: readonly key?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: contactAttributes?: ContactAttributes;<br>Differences: contactAttributes?: ContactAttributes;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: emails?: Email[];<br>Differences: emails?: Email[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: events?: Event[];<br>Differences: events?: Event[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: groups?: Group[];<br>Differences: groups?: Group[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: imAddresses?: ImAddress[];<br>Differences: imAddresses?: ImAddress[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: phoneNumbers?: PhoneNumber[];<br>Differences: phoneNumbers?: PhoneNumber[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: portrait?: Portrait;<br>Differences: portrait?: Portrait;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: postalAddresses?: PostalAddress[];<br>Differences: postalAddresses?: PostalAddress[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: relations?: Relation[];<br>Differences: relations?: Relation[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: sipAddresses?: SipAddress[];<br>Differences: sipAddresses?: SipAddress[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: websites?: Website[];<br>Differences: websites?: Website[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: name?: Name;<br>Differences: name?: Name;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: nickName?: NickName;<br>Differences: nickName?: NickName;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: note?: Note;<br>Differences: note?: Note;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Contact;<br>API declaration: organization?: Organization;<br>Differences: organization?: Organization;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class ContactAttributes<br>Differences: class ContactAttributes|api/@ohos.contact.d.ts|
|New API|NA|Class name: ContactAttributes;<br>API declaration: attributes: Attribute[];<br>Differences: attributes: Attribute[];|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: enum Attribute<br>Differences: enum Attribute|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_CONTACT_EVENT<br>Differences: ATTR_CONTACT_EVENT|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_EMAIL<br>Differences: ATTR_EMAIL|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_GROUP_MEMBERSHIP<br>Differences: ATTR_GROUP_MEMBERSHIP|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_IM<br>Differences: ATTR_IM|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_NAME<br>Differences: ATTR_NAME|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_NICKNAME<br>Differences: ATTR_NICKNAME|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_NOTE<br>Differences: ATTR_NOTE|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_ORGANIZATION<br>Differences: ATTR_ORGANIZATION|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_PHONE<br>Differences: ATTR_PHONE|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_PORTRAIT<br>Differences: ATTR_PORTRAIT|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_POSTAL_ADDRESS<br>Differences: ATTR_POSTAL_ADDRESS|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_RELATION<br>Differences: ATTR_RELATION|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_SIP_ADDRESS<br>Differences: ATTR_SIP_ADDRESS|api/@ohos.contact.d.ts|
|New API|NA|Class name: Attribute;<br>API declaration: ATTR_WEBSITE<br>Differences: ATTR_WEBSITE|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Email<br>Differences: class Email|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: static readonly CUSTOM_LABEL: 0;<br>Differences: static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: static readonly EMAIL_HOME: 1;<br>Differences: static readonly EMAIL_HOME: 1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: static readonly EMAIL_WORK: 2;<br>Differences: static readonly EMAIL_WORK: 2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: static readonly EMAIL_OTHER: 3;<br>Differences: static readonly EMAIL_OTHER: 3;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: static readonly INVALID_LABEL_ID: -1;<br>Differences: static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: email: string;<br>Differences: email: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: labelName?: string;<br>Differences: labelName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: displayName?: string;<br>Differences: displayName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Email;<br>API declaration: labelId?: number;<br>Differences: labelId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Event<br>Differences: class Event|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: static readonly CUSTOM_LABEL: 0;<br>Differences: static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: static readonly EVENT_ANNIVERSARY: 1;<br>Differences: static readonly EVENT_ANNIVERSARY: 1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: static readonly EVENT_OTHER: 2;<br>Differences: static readonly EVENT_OTHER: 2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: static readonly EVENT_BIRTHDAY: 3;<br>Differences: static readonly EVENT_BIRTHDAY: 3;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: static readonly INVALID_LABEL_ID: -1;<br>Differences: static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: eventDate: string;<br>Differences: eventDate: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: labelName?: string;<br>Differences: labelName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Event;<br>API declaration: labelId?: number;<br>Differences: labelId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Group<br>Differences: class Group|api/@ohos.contact.d.ts|
|New API|NA|Class name: Group;<br>API declaration: groupId?: number;<br>Differences: groupId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Group;<br>API declaration: title: string;<br>Differences: title: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Holder<br>Differences: class Holder|api/@ohos.contact.d.ts|
|New API|NA|Class name: Holder;<br>API declaration: readonly bundleName: string;<br>Differences: readonly bundleName: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Holder;<br>API declaration: readonly displayName?: string;<br>Differences: readonly displayName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Holder;<br>API declaration: holderId?: number;<br>Differences: holderId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class ImAddress<br>Differences: class ImAddress|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly CUSTOM_LABEL: -1;<br>Differences: static readonly CUSTOM_LABEL: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly IM_AIM: 0;<br>Differences: static readonly IM_AIM: 0;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly IM_MSN: 1;<br>Differences: static readonly IM_MSN: 1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly IM_YAHOO: 2;<br>Differences: static readonly IM_YAHOO: 2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly IM_SKYPE: 3;<br>Differences: static readonly IM_SKYPE: 3;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly IM_QQ: 4;<br>Differences: static readonly IM_QQ: 4;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly IM_ICQ: 6;<br>Differences: static readonly IM_ICQ: 6;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly IM_JABBER: 7;<br>Differences: static readonly IM_JABBER: 7;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: static readonly INVALID_LABEL_ID: -2;<br>Differences: static readonly INVALID_LABEL_ID: -2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: imAddress: string;<br>Differences: imAddress: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: labelName?: string;<br>Differences: labelName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: ImAddress;<br>API declaration: labelId?: number;<br>Differences: labelId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Name<br>Differences: class Name|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: familyName?: string;<br>Differences: familyName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: familyNamePhonetic?: string;<br>Differences: familyNamePhonetic?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: fullName: string;<br>Differences: fullName: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: givenName?: string;<br>Differences: givenName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: givenNamePhonetic?: string;<br>Differences: givenNamePhonetic?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: middleName?: string;<br>Differences: middleName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: middleNamePhonetic?: string;<br>Differences: middleNamePhonetic?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: namePrefix?: string;<br>Differences: namePrefix?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Name;<br>API declaration: nameSuffix?: string;<br>Differences: nameSuffix?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class NickName<br>Differences: class NickName|api/@ohos.contact.d.ts|
|New API|NA|Class name: NickName;<br>API declaration: nickName: string;<br>Differences: nickName: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Note<br>Differences: class Note|api/@ohos.contact.d.ts|
|New API|NA|Class name: Note;<br>API declaration: noteContent: string;<br>Differences: noteContent: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Organization<br>Differences: class Organization|api/@ohos.contact.d.ts|
|New API|NA|Class name: Organization;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Organization;<br>API declaration: title?: string;<br>Differences: title?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class PhoneNumber<br>Differences: class PhoneNumber|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly CUSTOM_LABEL: 0;<br>Differences: static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_HOME: 1;<br>Differences: static readonly NUM_HOME: 1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_MOBILE: 2;<br>Differences: static readonly NUM_MOBILE: 2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_WORK: 3;<br>Differences: static readonly NUM_WORK: 3;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_FAX_WORK: 4;<br>Differences: static readonly NUM_FAX_WORK: 4;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_FAX_HOME: 5;<br>Differences: static readonly NUM_FAX_HOME: 5;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_PAGER: 6;<br>Differences: static readonly NUM_PAGER: 6;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_OTHER: 7;<br>Differences: static readonly NUM_OTHER: 7;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_CALLBACK: 8;<br>Differences: static readonly NUM_CALLBACK: 8;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_CAR: 9;<br>Differences: static readonly NUM_CAR: 9;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_COMPANY_MAIN: 10;<br>Differences: static readonly NUM_COMPANY_MAIN: 10;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_ISDN: 11;<br>Differences: static readonly NUM_ISDN: 11;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_MAIN: 12;<br>Differences: static readonly NUM_MAIN: 12;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_OTHER_FAX: 13;<br>Differences: static readonly NUM_OTHER_FAX: 13;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_RADIO: 14;<br>Differences: static readonly NUM_RADIO: 14;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_TELEX: 15;<br>Differences: static readonly NUM_TELEX: 15;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_TTY_TDD: 16;<br>Differences: static readonly NUM_TTY_TDD: 16;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_WORK_MOBILE: 17;<br>Differences: static readonly NUM_WORK_MOBILE: 17;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_WORK_PAGER: 18;<br>Differences: static readonly NUM_WORK_PAGER: 18;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_ASSISTANT: 19;<br>Differences: static readonly NUM_ASSISTANT: 19;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly NUM_MMS: 20;<br>Differences: static readonly NUM_MMS: 20;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: static readonly INVALID_LABEL_ID: -1;<br>Differences: static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: labelName?: string;<br>Differences: labelName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: phoneNumber: string;<br>Differences: phoneNumber: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PhoneNumber;<br>API declaration: labelId?: number;<br>Differences: labelId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Portrait<br>Differences: class Portrait|api/@ohos.contact.d.ts|
|New API|NA|Class name: Portrait;<br>API declaration: uri: string;<br>Differences: uri: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class PostalAddress<br>Differences: class PostalAddress|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: static readonly CUSTOM_LABEL: 0;<br>Differences: static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: static readonly ADDR_HOME: 1;<br>Differences: static readonly ADDR_HOME: 1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: static readonly ADDR_WORK: 2;<br>Differences: static readonly ADDR_WORK: 2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: static readonly ADDR_OTHER: 3;<br>Differences: static readonly ADDR_OTHER: 3;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: static readonly INVALID_LABEL_ID: -1;<br>Differences: static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: city?: string;<br>Differences: city?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: country?: string;<br>Differences: country?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: labelName?: string;<br>Differences: labelName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: neighborhood?: string;<br>Differences: neighborhood?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: pobox?: string;<br>Differences: pobox?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: postalAddress: string;<br>Differences: postalAddress: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: postcode?: string;<br>Differences: postcode?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: region?: string;<br>Differences: region?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: street?: string;<br>Differences: street?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: PostalAddress;<br>API declaration: labelId?: number;<br>Differences: labelId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Relation<br>Differences: class Relation|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly CUSTOM_LABEL: 0;<br>Differences: static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_ASSISTANT: 1;<br>Differences: static readonly RELATION_ASSISTANT: 1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_BROTHER: 2;<br>Differences: static readonly RELATION_BROTHER: 2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_CHILD: 3;<br>Differences: static readonly RELATION_CHILD: 3;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_DOMESTIC_PARTNER: 4;<br>Differences: static readonly RELATION_DOMESTIC_PARTNER: 4;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_FATHER: 5;<br>Differences: static readonly RELATION_FATHER: 5;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_FRIEND: 6;<br>Differences: static readonly RELATION_FRIEND: 6;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_MANAGER: 7;<br>Differences: static readonly RELATION_MANAGER: 7;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_MOTHER: 8;<br>Differences: static readonly RELATION_MOTHER: 8;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_PARENT: 9;<br>Differences: static readonly RELATION_PARENT: 9;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_PARTNER: 10;<br>Differences: static readonly RELATION_PARTNER: 10;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_REFERRED_BY: 11;<br>Differences: static readonly RELATION_REFERRED_BY: 11;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_RELATIVE: 12;<br>Differences: static readonly RELATION_RELATIVE: 12;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_SISTER: 13;<br>Differences: static readonly RELATION_SISTER: 13;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly RELATION_SPOUSE: 14;<br>Differences: static readonly RELATION_SPOUSE: 14;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: static readonly INVALID_LABEL_ID: -1;<br>Differences: static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: labelName?: string;<br>Differences: labelName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: relationName: string;<br>Differences: relationName: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: Relation;<br>API declaration: labelId?: number;<br>Differences: labelId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class SipAddress<br>Differences: class SipAddress|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: static readonly CUSTOM_LABEL: 0;<br>Differences: static readonly CUSTOM_LABEL: 0;|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: static readonly SIP_HOME: 1;<br>Differences: static readonly SIP_HOME: 1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: static readonly SIP_WORK: 2;<br>Differences: static readonly SIP_WORK: 2;|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: static readonly SIP_OTHER: 3;<br>Differences: static readonly SIP_OTHER: 3;|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: static readonly INVALID_LABEL_ID: -1;<br>Differences: static readonly INVALID_LABEL_ID: -1;|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: labelName?: string;<br>Differences: labelName?: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: sipAddress: string;<br>Differences: sipAddress: string;|api/@ohos.contact.d.ts|
|New API|NA|Class name: SipAddress;<br>API declaration: labelId?: number;<br>Differences: labelId?: number;|api/@ohos.contact.d.ts|
|New API|NA|Class name: contact;<br>API declaration: class Website<br>Differences: class Website|api/@ohos.contact.d.ts|
|New API|NA|Class name: Website;<br>API declaration: website: string;<br>Differences: website: string;|api/@ohos.contact.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.contact.d.ts<br>Differences: ContactsKit|api/@ohos.contact.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.ContactsKit.d.ts<br>Differences: ContactsKit|kits/@kit.ContactsKit.d.ts|
