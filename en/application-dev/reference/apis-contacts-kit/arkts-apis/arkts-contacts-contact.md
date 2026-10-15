# @ohos.contact

The **contact** module provides contact management functions, such as adding, deleting, and updating contacts.

**Since:** 7

<!--Device-unnamed-declare namespace contact--><!--Device-unnamed-declare namespace contact-End-->

**System capability:** SystemCapability.Applications.ContactsData

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact2) | Adds a contact. This API uses an asynchronous callback to return the result. |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact4) | Adds a contact. This API uses a promise to return the result. |
| [addContacts](arkts-contacts-contact-addcontacts-f.md#addcontacts) | Adds contacts in batches. This API uses a promise to return the result. |
| [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md#addcontactviaui) | Calls the API for adding a contact to open the UI. This API uses a promise to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact2) | Deletes a contact. This API uses an asynchronous callback to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact4) | Deletes a contact. This API uses a promise to return the result. |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasmatchedcalllog1) | Checks whether there are call records that meet the specified conditions. By default, call records within the last 6 hours are queried. This API applies only to carrier calls. This API uses a promise to return the result. |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md#hasmatchedcalllog2) | Checks whether there are call records that meet the specified conditions. This API applies only to carrier calls. This API uses a promise to return the result. |
| [importContactsViaUI](arkts-contacts-contact-importcontactsviaui-f.md#importcontactsviaui) | Imports multiple contacts through UI interaction. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact2) | Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact4) | Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard2) | Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard4) | Checks whether a contact is included in my card. This API uses a promise to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact2) | Queries a contact based on the specified key. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact4) | Queries a contact based on the specified key and holder. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact6) | Queries a contact based on the specified key and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) | Queries a contact based on the specified key, holder, and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact10) | Queries a contact based on the specified key, holder, and attributes. This API uses a promise to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts2) | Queries all contacts. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts4) | Queries all contacts based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts6) | Queries all contacts based on the specified attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts8) | Queries all contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts10) | Queries all contacts based on the specified holder and attributes. This API uses a promise to return the result. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail2) | Queries a contact based on the specified email. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail4) | Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail6) | Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail8) | Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail10) | Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber2) | Queries a contact based on the specified phone number. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber4) | Queries a contact based on the specified phone number and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber6) | Queries a contact based on the specified phone number and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber8) | Queries a contact based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber10) | Queries a contact based on the specified phone number, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsCount](arkts-contacts-contact-querycontactscount-f.md#querycontactscount) | Queries the number of all contacts. This API uses a promise to return the result. |
| [queryContactSyncInfo](arkts-contacts-contact-querycontactsyncinfo-f.md#querycontactsyncinfo) | Queries information about ongoing contact synchronization for the calling application. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups2) | Queries all groups of a contact. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups4) | Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups6) | Queries all groups of a contact based on the specified holder. This API uses a promise to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders2) | Queries all applications that have created contacts. This API uses an asynchronous callback to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders4) | Queries all applications that have created contacts. This API uses a promise to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey2) | Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey4) | Queries the key of a contact based on the specified contact ID and holder. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey6) | Queries the key of a contact based on the specified contact ID and holder. This API uses a promise to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard2) | Queries my card. This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard4) | Queries my card. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard6) | Queries my card. (The contact attribute list can be imported.) This API uses a promise to return the result. |
| [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md#savetoexistingcontactviaui) | Saves the information to an existing contact through UI interaction.. This API uses a promise to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts1) | Selects a contact. This API uses an asynchronous callback to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts2) | Selects a contact. This API uses a promise to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts3) | Selects a contact. (Filter criteria can be transferred during contact selection.) This API uses an asynchronous callback to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts4) | Selects a contact. (Filter criteria can be transferred during contact selection.) This API uses a promise to return the result. |
| [syncContacts](arkts-contacts-contact-synccontacts-f.md#synccontacts) | Synchronizes multiple contacts to the contacts database in batches. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact2) | Updates a contact. This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact4) | Updates a contact. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact6) | Updates a contact. (The contact attribute list can be imported.) This API uses a promise to return the result. |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact1) | Adds a contact. This API uses an asynchronous callback to return the result. |
| [addContact](arkts-contacts-contact-addcontact-f.md#addcontact3) | Adds a contact. This API uses a promise to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact1) | Deletes a contact. This API uses an asynchronous callback to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md#deletecontact3) | Deletes a contact. This API uses a promise to return the result. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact1) | Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md#islocalcontact3) | Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard1) | Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md#ismycard3) | Checks whether a contact is included in my card. This API uses a promise to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact1) | Queries a contact based on the specified key. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact3) | Queries a contact based on the specified key and holder. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact5) | Queries a contact based on the specified key and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact7) | Queries a contact based on the specified key, holder, and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact9) | Queries a contact based on the specified key, holder, and attributes. This API uses a promise to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts1) | Queries all contacts. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts3) | Queries all contacts based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts5) | Queries all contacts based on the specified attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts7) | Queries all contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md#querycontacts9) | Queries all contacts based on the specified holder and attributes. This API uses a promise to return the result. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail1) | Queries a contact based on the specified email. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail3) | Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail5) | Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail7) | Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md#querycontactsbyemail9) | Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber1) | Queries a contact based on the specified phone number. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber3) | Queries a contact based on the specified phone number and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber5) | Queries a contact based on the specified phone number and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber7) | Queries a contact based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md#querycontactsbyphonenumber9) | Queries a contact based on the specified phone number, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md#querycontact8) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups1) | Queries all groups of a contact. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups3) | Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md#querygroups5) | Queries all groups of a contact based on the specified holder. This API uses a promise to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders1) | Queries all applications that have created contacts. This API uses an asynchronous callback to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md#queryholders3) | Queries all applications that have created contacts. This API uses a promise to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey1) | Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey3) | Queries the key of a contact based on the specified contact ID and holder. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md#querykey5) | Queries the key of a contact based on the specified contact ID and holder. This API uses a promise to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard1) | Queries my card. This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard3) | Queries my card. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md#querymycard5) | Queries my card. (The contact attribute list can be imported.) This API uses a promise to return the result. |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectcontact1) | Selects a contact. This API uses an asynchronous callback to return the result. |
| [selectContact](arkts-contacts-contact-selectcontact-f.md#selectcontact2) | Selects a contact. This API uses a promise to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact1) | Updates a contact. This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact3) | Updates a contact. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md#updatecontact5) | Updates a contact. (The contact attribute list can be imported.) This API uses a promise to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [Contact](arkts-contacts-contact-contact-c.md) | Defines a contact. |
| [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | Provides a list of contact attributes, which are generally used as arguments. If **null** is passed, all attributes are queried by default. |
| [Email](arkts-contacts-contact-email-c.md) | Defines a contact's email. |
| [Event](arkts-contacts-contact-event-c.md) | Defines a contact's event. |
| [Group](arkts-contacts-contact-group-c.md) | Defines a contact group. |
| [Holder](arkts-contacts-contact-holder-c.md) | Defines an application that creates the contact. |
| [ImAddress](arkts-contacts-contact-imaddress-c.md) | Enumerates IM addresses. |
| [Name](arkts-contacts-contact-name-c.md) | Defines a contact's name. |
| [NickName](arkts-contacts-contact-nickname-c.md) | Defines a contact's nickname. |
| [Note](arkts-contacts-contact-note-c.md) | Defines a contact's note. |
| [Organization](arkts-contacts-contact-organization-c.md) | Defines a contact's organization. |
| [PhoneNumber](arkts-contacts-contact-phonenumber-c.md) | Defines a contact's phone number. |
| [Portrait](arkts-contacts-contact-portrait-c.md) | Defines a contact's portrait. |
| [PostalAddress](arkts-contacts-contact-postaladdress-c.md) | Defines a contact's postal address. |
| [Relation](arkts-contacts-contact-relation-c.md) | Defines a contact's relationship. |
| [SipAddress](arkts-contacts-contact-sipaddress-c.md) | Defines a contact's SIP address. |
| [Website](arkts-contacts-contact-website-c.md) | Defines a contact's website. |

### Interfaces

| Name | Description |
| --- | --- |
| [ContactSelectionFilter](arkts-contacts-contact-contactselectionfilter-i.md) | Defines the contact selection filter. |
| [ContactSelectionOptions](arkts-contacts-contact-contactselectionoptions-i.md) | Defines the Contact selection options, which specifies whether one contact or multiple contacts can be selected. |
| [ContactSyncInfo](arkts-contacts-contact-contactsyncinfo-i.md) | Information about contact synchronization for the calling application. |
| [ContactSyncProgress](arkts-contacts-contact-contactsyncprogress-i.md) | Information about the contact synchronization progress. |
| [DataFilter](arkts-contacts-contact-datafilter-i.md) | Defines the contact data filter item. |
| [FilterClause](arkts-contacts-contact-filterclause-i.md) | Defines the contact filter criteria. Multiple filter criteria are ORed. If the parameter is an array, the array can contain a maximum of three elements. |
| [FilterOptions](arkts-contacts-contact-filteroptions-i.md) | Defines contact filter options. |

### Enums

| Name | Description |
| --- | --- |
| [Attribute](arkts-contacts-contact-attribute-e.md) | Enumerates contact attributes. The enumerated value is of the number type. Create contact data in JSON format: |
| [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md) | The type of contact synchronization mode. |
| [DataField](arkts-contacts-contact-datafield-e.md) | Enumerates contact data fields. |
| [FilterCondition](arkts-contacts-contact-filtercondition-e.md) | Enumerates filter criteria. |
| [FilterType](arkts-contacts-contact-filtertype-e.md) | Enumerates contact filter types. |
