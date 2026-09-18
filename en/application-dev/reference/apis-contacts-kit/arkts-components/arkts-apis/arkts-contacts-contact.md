# @ohos.contact

The **contact** module provides contact management functions, such as adding, deleting, and updating contacts.

**Since:** 7

**System capability:** SystemCapability.Applications.ContactsData

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addContact](arkts-contacts-contact-addcontact-f.md) | Adds a contact. This API uses an asynchronous callback to return the result. |
| [addContact](arkts-contacts-contact-addcontact-f.md) | Adds a contact. This API uses an asynchronous callback to return the result. |
| [addContact](arkts-contacts-contact-addcontact-f.md) | Adds a contact. This API uses a promise to return the result. |
| [addContact](arkts-contacts-contact-addcontact-f.md) | Adds a contact. This API uses a promise to return the result. |
| [addContacts](arkts-contacts-contact-addcontacts-f.md) | Adds contacts in batches. This API uses a promise to return the result. |
| [addContactViaUI](arkts-contacts-contact-addcontactviaui-f.md) | Calls the API for adding a contact to open the UI. This API uses a promise to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md) | Deletes a contact. This API uses an asynchronous callback to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md) | Deletes a contact. This API uses an asynchronous callback to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md) | Deletes a contact. This API uses a promise to return the result. |
| [deleteContact](arkts-contacts-contact-deletecontact-f.md) | Deletes a contact. This API uses a promise to return the result. |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md) | Checks whether there are call records that meet the specified conditions. By default, call records within the last 6 hours are queried. This API applies only to carrier calls. This API uses a promise to return the result. |
| [hasMatchedCallLog](arkts-contacts-contact-hasmatchedcalllog-f.md) | Checks whether there are call records that meet the specified conditions. This API applies only to carrier calls. This API uses a promise to return the result. |
| [importContactsViaUI](arkts-contacts-contact-importcontactsviaui-f.md) | Imports multiple contacts through UI interaction. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md) | Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md) | Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md) | Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result. |
| [isLocalContact](arkts-contacts-contact-islocalcontact-f.md) | Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md) | Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md) | Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md) | Checks whether a contact is included in my card. This API uses a promise to return the result. |
| [isMyCard](arkts-contacts-contact-ismycard-f.md) | Checks whether a contact is included in my card. This API uses a promise to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key and holder. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key and holder. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key, holder, and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key, holder, and attributes. This API uses an asynchronous callback to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key, holder, and attributes. This API uses a promise to return the result. |
| [queryContact](arkts-contacts-contact-querycontact-f.md) | Queries a contact based on the specified key, holder, and attributes. This API uses a promise to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified holder and attributes. This API uses a promise to return the result. |
| [queryContacts](arkts-contacts-contact-querycontacts-f.md) | Queries all contacts based on the specified holder and attributes. This API uses a promise to return the result. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByEmail](arkts-contacts-contact-querycontactsbyemail-f.md) | Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsByPhoneNumber](arkts-contacts-contact-querycontactsbyphonenumber-f.md) | Queries a contact based on the specified phone number, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](arkts-contacts-contact-querycontact-f.md) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task. |
| [queryContactsCount](arkts-contacts-contact-querycontactscount-f.md) | Queries the number of all contacts. This API uses a promise to return the result. |
| [queryContactSyncInfo](arkts-contacts-contact-querycontactsyncinfo-f.md) | Queries information about ongoing contact synchronization for the calling application. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md) | Queries all groups of a contact. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md) | Queries all groups of a contact. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md) | Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md) | Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md) | Queries all groups of a contact based on the specified holder. This API uses a promise to return the result. |
| [queryGroups](arkts-contacts-contact-querygroups-f.md) | Queries all groups of a contact based on the specified holder. This API uses a promise to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md) | Queries all applications that have created contacts. This API uses an asynchronous callback to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md) | Queries all applications that have created contacts. This API uses an asynchronous callback to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md) | Queries all applications that have created contacts. This API uses a promise to return the result. |
| [queryHolders](arkts-contacts-contact-queryholders-f.md) | Queries all applications that have created contacts. This API uses a promise to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md) | Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md) | Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md) | Queries the key of a contact based on the specified contact ID and holder. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md) | Queries the key of a contact based on the specified contact ID and holder. This API uses an asynchronous callback to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md) | Queries the key of a contact based on the specified contact ID and holder. This API uses a promise to return the result. |
| [queryKey](arkts-contacts-contact-querykey-f.md) | Queries the key of a contact based on the specified contact ID and holder. This API uses a promise to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md) | Queries my card. This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md) | Queries my card. This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md) | Queries my card. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md) | Queries my card. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md) | Queries my card. (The contact attribute list can be imported.) This API uses a promise to return the result. |
| [queryMyCard](arkts-contacts-contact-querymycard-f.md) | Queries my card. (The contact attribute list can be imported.) This API uses a promise to return the result. |
| [saveToExistingContactViaUI](arkts-contacts-contact-savetoexistingcontactviaui-f.md) | Saves the information to an existing contact through UI interaction.. This API uses a promise to return the result. |
| [selectContact](arkts-contacts-contact-selectcontact-f.md) | Selects a contact. This API uses an asynchronous callback to return the result. |
| [selectContact](arkts-contacts-contact-selectcontact-f.md) | Selects a contact. This API uses a promise to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md) | Selects a contact. This API uses an asynchronous callback to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md) | Selects a contact. This API uses a promise to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md) | Selects a contact. (Filter criteria can be transferred during contact selection.) This API uses an asynchronous callback to return the result. |
| [selectContacts](arkts-contacts-contact-selectcontacts-f.md) | Selects a contact. (Filter criteria can be transferred during contact selection.) This API uses a promise to return the result. |
| [syncContacts](arkts-contacts-contact-synccontacts-f.md) | Synchronizes multiple contacts to the contacts database in batches. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md) | Updates a contact. This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md) | Updates a contact. This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md) | Updates a contact. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md) | Updates a contact. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md) | Updates a contact. (The contact attribute list can be imported.) This API uses a promise to return the result. |
| [updateContact](arkts-contacts-contact-updatecontact-f.md) | Updates a contact. (The contact attribute list can be imported.) This API uses a promise to return the result. |

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
