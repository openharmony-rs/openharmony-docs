# Account Management Error Codes

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=fe12aa593b775ac05a8cc487da6ab2db32674d15 translatedAt=2026-11-10T04:00:44.019Z pushedAt=2026-11-10T06:04:16.362Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

The following error codes include system account, distributed account, and application account error codes.

## 12300001 System Service Exception

**Error Message**

The system service works abnormally.

**Possible Causes**

This error code indicates a system service exception. Possible causes are as follows:
1. The account management service fails to start properly.
2. The IPC object of account management cannot be obtained.
3. Other services that account management depends on fail to start properly, or their IPC objects cannot be obtained.
4. The service is not initialized.
5. Insufficient storage space.
6. An exception occurs when reading or writing a file.
7. An exception occurs when creating a directory.
8. An exception occurs when creating or deleting a file.
9. An exception occurs when reading from or writing to the database.

**Solution**

Please try again later or restart the device.

## 12300002 Invalid parameter

**Error Message**

Invalid parameter.

**Possible Causes**

This error code indicates that an invalid parameter is passed in. The possible causes are as follows:
1. The username is empty.
2. The length of the system account username is greater than 1024.
3. The length of the distributed account username is greater than 256.
4. The system account ID is less than 0, less than 100, or greater than 1099.
5. The length of the distributed account ID is greater than 512.
6. An unsupported event type is passed in for the distributed account.
7. The domain name is empty.
8. The domain name length exceeds 128.
9. The domain account is empty.
10. The domain account length exceeds 512.
11. The constraint is empty.
12. The constraint length exceeds 128.
13. Invalid authentication and query parameters are passed in.
14. The length of the provided system account avatar encoding string exceeds 4 KB.
15. The length of the provided distributed account avatar encoding string exceeds 2 MB.
16. An image that is not in JPG or PNG format is provided.
17. The application account name length exceeds 512.
18. The authentication type length exceeds 1024.
19. The token length exceeds 1024.
20. The key name length exceeds 1024.
21. The custom data value length exceeds 1024.
22. Invalid token.
23. Invalid context ID.
24. Invalid credential ID.

**Solution**

Set parameters correctly.

## 12300003 Account Does Not Exist

**Error Message**

The account does not exist.

**Possible Causes**

This error code indicates that the account to be operated does not exist. The possible causes are as follows:
1. Querying, activating, or deleting an account that has not been created.
2. Querying, activating, or deleting an account that has been deleted.
3. Setting constraints, username, or avatar for a deleted account.
4. Updating an account that has not been created.
5. Setting or canceling account information access authorization for a nonexistent account.
6. Setting, deleting, or querying the password of a nonexistent account.
7. Setting or deleting a token for a nonexistent account.
8. Set additional information for an account that does not exist.
9. Set/delete credentials for an account that does not exist.
10. Set custom data for an account that does not exist.
11. Enable the distributed synchronization feature for an account that does not exist.

**Solution**

Check whether the account exists.

## 12300004 Account Already Exists

**Error Message**

The account already exists.

**Possible Causes**

This error code indicates that the account already exists. The possible causes are as follows:

An existing account is created.

**Solution**

Cancel the creation, or retry with a different account name.

## 12300005 Unsupported Multi-user

**Error Message**

Multi-user is not supported.

**Possible Causes**

This error code indicates that multi-user is not supported. The possible causes are as follows:

The current device does not support multi-user, so the account cannot be created.

**Solution**

No other account can be created. Cancel the creation.

## 12300006 Unsupported Account Type

**Error Message**

The account type is not supported.

**Possible Causes**

This error code indicates that an unsupported account type is provided. Possible cause: the current device does not support creating an account of the specified type.

**Solution**

Create an account of another type.

## 12300007 The Number of Accounts Has Reached the Upper Limit

**Error Message**

The number of accounts has reached the upper limit.

**Possible Causes**

This error code indicates that the number of accounts has reached the upper limit. Possible cause: 1000 accounts already exist when creating a system account or application account.

**Solution**

Delete other accounts before creating a new one.

## 12300008 Restricted Account

**Error Message**

The specified account is restricted.

**Possible Causes**

This error code indicates that the account being operated is restricted. Possible causes are as follows:
1. Deleting a system-reserved user.
2. Querying the constraint source type of a system-reserved user.
3. Creating an account with an ID from 0 to 100.

**Solution**

The specified ID is a system-reserved user and cannot be operated.

## 12300009 Account Already Activated

**Error Message**

The account has been activated.

**Possible Causes**

This error code indicates that the account has been activated. The possible cause is as follows:

An already activated account is activated again.

**Solution**

The current account has been activated. Do not repeat the operation.

## 12300010 Account Service Busy

**Error Message**

The account service is busy.

**Possible Causes**

This error code indicates that the account service is busy. Possible causes are as follows:
1. Duplicate requests are submitted within a short period, such as repeated activation and repeated setup.
2. The number of authentication sessions of the application account exceeds 256, and new authentication requests cannot be processed.

**Solution**

Wait for a while and try again, and reduce the call frequency.

## 12300011 Event Listener Already Registered

**Error Message**

The event listener has been registered.

**Possible Causes**

This error code indicates that the listener has been registered. The possible causes are as follows:

The current application registers a listener that has already been registered with the system, and duplicate registration is not allowed.

**Solution**

Cancel the registration, or register again using a listener that has not been registered.

## 12300012 Event Listener Not Registered

**Error Message**

The event listener has not been registered.

**Possible Causes**

This error code indicates that the listener has not been registered. The possible causes are as follows:

Unregistering a listener that has not been registered.

**Solution**

Use a registered listener to perform the unregistration operation.

## 12300013 Network Exception

**Error Message**

Network exception.

**Possible Causes**

This error code indicates a network exception. Possible causes are as follows:
1. The device is not connected to a network.
2. The network connection is abnormal.
3. The application does not have the network access permission.
4. An unknown network error occurs.

**Solution**

1. Connect to a network.
2. Ensure that the network can be accessed normally.
3. Ensure that the application has the network access permission.
4. Retry the related operation.

## 12300014 Domain Account Not Authenticated

**Error Message**

The domain account is not authenticated.

**Possible Causes**

The domain account is not logged in.

**Solution**

Log in to the domain account first.

## 12300015 Short Name Already Exists

**Error Message**

The short name already exists.

**Possible Causes**

The short name used to create the account already exists.

**Solution**

Use a different short name that does not exist.

## 12300016 The Number of Logged-in Accounts Reaches the Upper Limit

**Error Message**

The number of logged in accounts reaches the upper limit.

**Possible Causes**

The number of logged-in accounts has reached the upper limit, and no new account can be logged in.

**Solution**

Log out an account that is already logged in, and then log in to a new account.

<!--Del-->

## 12300017 Foreground System Account Not Found

**Error Message**

The foreground OS account is not found.

**Possible Causes**

This error code indicates that no system account running in the foreground is found on the specified logical screen (displayId). The possible causes are as follows.
1. No system account is running in the foreground on the specified logical screen (not activated or not switched to the foreground).
2. The specified displayId is invalid or the corresponding logical screen does not exist.
3. The specified localId is invalid or the corresponding system account does not exist.

**Solution**

Check whether the passed displayId/localId is correct and exists. Ensure that an account already exists on the logical screen and is in the foreground, and then try again.

## 12300018 Display not found.

**Error Message**

Display not found.

**Possible Causes**

This error code indicates that the specified logical display ID cannot be recognized or does not exist. The possible causes are as follows.
1. The specified displayId is invalid or the corresponding logical display does not exist.
2. The target logical display is not connected or has been disconnected.

**Solution**

Check whether the displayId is correct and whether the logical display device is connected and available. Then retry with a valid logical display ID.

## 12300019 Cross-display Activation Not Supported

**Error Message**

Cross-display activation not supported.

**Possible Causes**

This error code indicates that the target device or the current system configuration does not support activating an account across different logical displays. Possible causes are as follows:

The current system policy or configuration restricts cross-display activation.

**Solution**

Perform the activation on the same logical display, or sign out of the account on the specified logical display and then activate it again.

<!--Del-->
## 12300020 Device Hardware Abnormal

**Error Message**

Device hardware abnormal.

**Description**

Device hardware abnormal.

**Possible Causes**

The device hardware is abnormal and cannot work properly.

**Solution**

Re-enter the credential information. If the issue persists, send the device for repair.
<!--DelEnd-->

## 12300021 System Account Already Bound to a Domain Account

**Error Message**

The OS account is already bound.

**Description**

The input system account is already bound to a domain account.

**Possible Causes**

The input system account is already bound to a domain account.

**Solution**

A system account cannot be bound to a domain account repeatedly. Use another system account for binding.

## 12300022 Domain Account Already Bound

**Error Message**

The domain account is already bound.

**Description**

The entered domain account is already bound to a system account.

**Possible Causes**

The entered domain account is already bound to a system account.

**Solution**

The same domain account cannot be bound to multiple system accounts. Use another domain account or delete the bound account before binding.

## 12300023 The Number of Accounts of the Specified Type Has Reached the Upper Limit

**Error Message**

The number of accounts of the specified type has reached the upper limit.

**Possible Causes**

The number of system accounts of the specified type has reached the upper limit.

**Solution**

Delete the redundant accounts and try again.

<!--DelEnd-->

## 12300101 Incorrect Credential

**Error Message**

The credential is incorrect.

**Possible Causes**

This error code indicates that the credential is incorrect. Possible causes are as follows:
1. The password is entered incorrectly;
2. The biometric feature does not match;
3. The token is invalid;

**Solution**

Enter a correct and valid credential and try again.

<!--Del-->
## 12300090 Cross-device Authentication Not Supported

**Error Message**

Cross-device capability not supported.

**Description**

Cross-device authentication is not supported.

**Possible Causes**

The current version or device does not support cross-device authentication.

**Solution**

Use the local identity authentication method.

## 12300091 Cross-device Communication Failed

**Error Message**

Cross-device communication failed.

**Description**

Cross-device communication failed.

**Possible Causes**

A normal connection could not be established between the devices.

**Solution**

Check whether a trusted link exists between the devices.
<!--DelEnd-->

## 12300102 Credential Does Not Exist

**Error Message**

The credential does not exist.

**Possible Causes**

This error code indicates that the credential does not exist. Possible causes are as follows:
1. Authenticate an unenrolled credential type.
2. Query an unenrolled credential type.
3. Delete an unenrolled credential type.

**Solution**

Check whether the credential type exists.

## 12300103 Credential Inputer Already Exists

**Error Message**

The credential inputer already exists.

**Possible Causes**

This error code indicates that the credential inputer has already been registered. Possible causes:

The PIN inputer has already been registered and cannot be registered again before being unregistered.

**Solution**

The credential inputer already exists. Do not repeat the operation.

## 12300104 Credential Inputer Does Not Exist

**Error Message**

The credential inputer is not found.

**Possible Causes**

This error code indicates that the credential inputer does not exist. The possible causes are as follows:

The credential inputer is not registered during authentication, addition, or modification of credentials.

**Solution**

Register the credential inputer.

## 12300105 Trust Level Not Supported

**Error Message**

The trust level is not supported.

**Possible Causes**

This error code indicates that the trust level is not supported. The possible causes are as follows:

A trust level not supported by the system is passed in.

**Solution**

Enter a valid trust level.

## 12300106 Unsupported Authentication Type

**Error Message**

The authentication type is not supported.

**Possible Causes**

This error code indicates that the authentication type is unsupported. The possible causes are as follows:

An authentication type unsupported by the system is passed in.

**Solution**

Provide an authentication type supported by the system.

## 12300107 The Authentication Type Does Not Exist

**Error Message**

The authentication type does not exist.

**Possible Causes**

This error code indicates that the authentication type does not exist. Possible causes are as follows:

The specified authentication type does not exist when querying or deleting a token.

**Solution**

Use an existing authentication type to query or delete.

## 12300108 The authentication session does not exist.

**Error Message**

The authentication session does not exist.

**Possible Causes**

This error code indicates that the session does not exist. The possible causes are as follows:

Querying the callback of a session that does not exist.

**Solution**

Use the identifier of a successfully opened session to query the session callback.

## 12300109 Authentication, Enrollment, or Update Operation Canceled

**Error Message**

The authentication, enrollment, or update operation is canceled.

**Possible Causes**

This error code indicates that the authentication, enrollment, or update operation is canceled. Possible causes are as follows:

1. During authentication, the user cancels the authentication operation.
2. During credential enrollment, the user cancels the enrollment operation.
3. During credential enrollment, the user cancels the update operation.

**Solution**

Perform the authentication operation again or end it.

## 12300110 Authentication Locked

**Error Message**

The authentication is locked.

**Possible Causes**

This error code indicates that authentication is locked. The possible causes are as follows:

The number of incorrect attempts for the authentication type exceeds the upper limit.

**Solution**

The number of incorrect authentication attempts exceeds the upper limit. Retry after freezingTime.

## 12300111 Authentication Timeout

**Error Message**

The authentication time out.

**Possible Causes**

This error code indicates an authentication timeout. The possible causes are as follows:
1. For a system account, authentication or enrollment takes more than three minutes.
2. The authentication service fails to respond in time due to network issues, resulting in a timeout.

**Solution**

1. The authentication or enrollment timed out. Try again.
2. Ensure that the network environment is normal, and then try again.

## 12300112 Authentication Service Busy

**Error Message**

The authentication service is busy.

**Possible Causes**

This error code indicates that the authentication service is busy. Possible causes are as follows:

1. During system account authentication, the total number of authentication operations exceeds 5.
2. During application account authentication, the authenticator service of the third-party application is busy (determined based on the actual situation).

**Solution**

The authentication service is currently busy. Try again later.

## 12300113 Authentication Service Does Not Exist

**Error Message**

The account authentication service does not exist.

**Possible Causes**

This error code indicates that the authentication service does not exist. The possible causes are as follows:

For application accounts:
1. When requesting authentication, the application to which the account belongs does not support the authenticator service.
2. When implicitly adding an account, the application to which the account belongs does not support the authenticator service.
3. When verifying the credential of a specified account, the application to which the account belongs does not support the authenticator service.
4. When setting the authenticator properties of an application, the specified application does not support the authenticator service.
5. When checking the account label, the specified application does not support the authenticator service.

**Solution**

Cancel the operation, or perform authentication with an application that supports the authentication service.

## 12300114 Authentication Service Exception

**Error Message**

The account authentication service works abnormally.

**Possible Causes**

This error code indicates that the account authentication service works abnormally. Possible causes are as follows:
1. An unknown error occurs in the identity authentication service.
2. The application authenticator does not comply with the specifications.

**Solution**

1. Retry or restart the system.
2. Develop the application authenticator in compliance with the specifications.

## 12300115 The Number of User Authentication Passwords Reaches the Upper Limit

**Error Message**

The number of credentials reaches the upper limit.

**Possible Causes**

1. An unknown error occurs in the identity authentication service.
2. The user already has a password of the corresponding type and cannot add another password.

**Solution**

1. Retry or restart the system.
2. Change the password or delete the existing password.

## 12300116 Credential Complexity Verification Failed

**Error Message**

Credential complexity verification failed.

**Possible Causes**

The credential set is too simple.

**Solution**

Enter a credential containing the specified characters as required.

## 12300117 PIN Expired

**Error Message**

PIN is expired.

**Possible Causes**

The PIN for user authentication is expired.

**Solution**

Reset the PIN.

<!--Del-->
## 12300119 Multi-factor Authentication Failed

**Error Message**

Multi-factor authentication failed.

**Description**

Multi-factor authentication failed.

**Possible Causes**

Some authentication factors failed verification.

**Solution**

Perform verification again and ensure that each authentication factor passes verification.

## 12300120 Credentials No Longer Valid

**Error Message**

The credentials are no longer valid.

**Possible Causes**

In the companion device authentication scenario, the companion device is no longer valid.

**Solution**

In the companion device authentication scenario, delete the companion device and then rebind it.

## 12300201 Domain Plugin Has Been Registered

**Error Message**

The domain plugin has been registered.

**Description**

The domain plugin has been registered.

**Possible Causes**

The domain plugin has been registered.

**Solution**

Unregister the domain plugin and then register it again.
<!--DelEnd-->

## 12300211 Server Unreachable

**Error Message**

Server unreachable.

**Description**

The local device cannot establish a network connection with the target server.

**Possible Causes**

This error code indicates that the server is unreachable. The possible causes are as follows:
1. The network of the local device is abnormal.
2. The target server does not provide services properly.

**Solution**

1. Ensure that the local device is properly connected to the network.
2. Ensure that the target server provides services properly.

## 12300212 Server Configuration Information Not Found

**Error Message**

Server config not found.

**Description**

The server configuration information is not found.

**Possible Causes**

The server configuration information was not added successfully or has been deleted.

**Solution**

Ensure that the server configuration information exists.

## 12300213 Server Configuration Information Already Exists

**Error Message**

Server config already exists.

**Description**

The server configuration information already exists.

**Possible Causes**

The server configuration information has been added successfully.

**Solution**

The target server configuration information has been added successfully. Do not repeat the operation.

## 12300214 Server Configuration Information Has Been Bound to an Account

**Error Message**

Server config has been associated with an account.

**Description**

The server configuration information has been bound to an account.

**Possible Causes**

The server configuration information has been bound to an account, so the server configuration information cannot be operated.

**Solution**

Replace the server configuration information or delete the bound account before performing the operation.

## 12300215 The Quantity of Server Configuration Information Has Reached the Upper Limit

**Error Message**

The number of server config reaches the upper limit.

**Description**

The number of server config reaches the upper limit.

**Possible Causes**

The quantity of server configuration information on the current device has reached the preset upper limit, and no new server configuration information can be added.

**Solution**

Delete the redundant server configuration information and then add it again.

## 12300401 System Account Sub-identity Profile Does Not Exist

**Error Message**

OS account sub-profile not found.

**Possible Causes**

No valid system account sub-identity profile identifier is specified.

**Solution**

Specify a valid sub-identity profile.

## 12300402 The Number of Sub-identity Profiles Under the System Account Has Reached the Upper Limit

**Error Message**

The number of sub-profiles under the OS account has reached limit.

**Possible Causes**

Too many sub-identity profiles have been created under the target system account.

**Solution**

Delete the existing sub-identity profiles and retry, or stop creating new sub-identity profiles.

## 12300403 Restricted System Account Sub-identity Profile

**Error Message**

Restricted OS account sub-profile.

**Possible Causes**

1. The target sub-identity profile cannot be deleted;
2. The target sub-identity profile cannot be switched;

**Solution**

Stop operations on the target sub-identity profile.

## 12300404 The Foreground Sub-identity Profile of the System Account Cannot Be Deleted

**Error Message**

The foreground sub-profile of the OS account cannot be deleted.

**Possible Causes**

The sub-identity profile of the system account to be deleted is currently in the foreground.

**Solution**

Stop deleting the sub-identity profile of the system account.

## 12300405 The foreground sub-identity of a logged-in distributed account cannot be directly switched to the background.

**Error Message**

The foreground sub-profile with a logged-in distributed account cannot be directly switched to the background.

**Possible Causes**

The distributed account associated with the foreground sub-identity profile is still in the logged-in state.

**Solution**

Log out the distributed account associated with the foreground sub-identity profile, and then trigger the switch operation.

## 12300406 The Distributed Account Information Has Been Bound to a Sub-identity Profile of the Target System Account

**Error Message**

The distributed account information has already been bound to a sub-profile of the target OS account.

**Possible Causes**

The distributed account information has already been bound to a sub-identity profile of the target system account.

**Solution**

Stop the binding operation, or unbind the account under the target system account before performing the binding operation again.

## 12400001 Application Does Not Exist

**Error Message**

The application does not exist.

**Possible Causes**

This error code indicates that the application does not exist. The possible causes are as follows:
1. The target application does not exist when setting access permissions.
2. The target application does not exist when setting open authorization.

**Solution**

Cancel the setting, or retry with the bundle name of an installed application.

## 12400002 Custom Data Does Not Exist

**Error Message**

The custom data does not exist.

**Possible Causes**

This error code indicates that the custom data does not exist. The possible cause is as follows: when querying the custom data of an account, the entered key name does not exist.

**Solution**

Query using the key name of existing custom data.

## 12400003 Quantity of Custom Data Reached the Upper Limit

**Error Message**

The number of custom data records reaches the upper limit.

**Possible Causes**

This error code indicates that the quantity of custom data has reached the upper limit. The possible cause is as follows: when setting custom data, the quantity of custom data of the target account has reached 512.

**Solution**

Cancel the setting operation, or delete the existing custom data.

## 12400004 The Number of Tokens Reached the Upper Limit

**Error Message**

The number of tokens reaches the upper limit.

**Possible Causes**

This error code indicates that the number of tokens has reached the upper limit. Possible cause: when adding a token, the number of tokens of the target account has reached 1024.

**Solution**

Cancel the add operation, or delete existing tokens before adding again.

## 12400005 Authorization List Reaches the Upper Limit

**Error Message**

The size of the authorization list reaches the upper limit.

**Possible Causes**

This error code indicates that the authorization list has reached the upper limit. Possible cause: when setting access/open authorization, the size of the authorization list exceeds 1024.

**Solution**

Cancel the setup operation, or revoke the existing access/open authorization before setting it again.