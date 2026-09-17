# Authenticator

Defines an authenticator.

**Since:** 8

**System capability:** SystemCapability.Account.AppAccount

## Modules to Import

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## addAccountImplicitly

```TypeScript
addAccountImplicitly(
      authType: string,
      callerBundleName: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

Adds an application account implicitly based on the specified authentication type and options. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [createAccountImplicitly](#createaccountimplicitly)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createAccountImplicitly](#createaccountimplicitly)(options: CreateAccountImplicitlyOptions, callback: AuthCallback)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| callerBundleName | string | Yes | Bundle name of the authentication requester. |
| options | { [key: string]: any } | Yes | Options for the authentication. |
| callback | [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | Yes | Authenticator callback used to return the result. |

## auth

```TypeScript
auth(name: string, authType: string, options: Record<string, Object>, callback: AuthCallback): void
```

Authenticates an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| options | Record&lt;string, Object&gt; | Yes | Options for the authentication. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

## authenticate

```TypeScript
authenticate(
      name: string,
      authType: string,
      callerBundleName: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

Authenticates an application account to obtain the OAuth token. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [auth](#auth)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [auth](#auth)(name: string, authType: string, options: Record&lt;string, Object&gt;, callback: AuthCallback)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| callerBundleName | string | Yes | Bundle name of the authentication requester. |
| options | { [key: string]: any } | Yes | Options for the authentication. |
| callback | [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | Yes | Authenticator callback used to return the result. |

## checkAccountLabels

```TypeScript
checkAccountLabels(name: string, labels: Array<string>, callback: AuthCallback): void
```

Checks the account labels. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| labels | Array&lt;string&gt; | Yes | Labels to check. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Examples**

```TypeScript
This API must be used together with the getRemoteObject API. For details, see the example of the [getRemoteObject](#getremoteobject) API.
```

## checkAccountRemovable

```TypeScript
checkAccountRemovable(name: string, callback: AuthCallback): void
```

Checks whether an application account can be deleted. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Examples**

```TypeScript
This API must be used together with the getRemoteObject API. For details, see the example of the [getRemoteObject](#getremoteobject) API.
```

## createAccountImplicitly

```TypeScript
createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void
```

Creates an application account implicitly based on the specified account owner. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CreateAccountImplicitlyOptions](arkts-basicservices-appaccount-createaccountimplicitlyoptions-i.md) | Yes | Options for implicitly creating the account. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

## getRemoteObject

```TypeScript
getRemoteObject(): rpc.RemoteObject
```

Obtains the remote object of an authenticator. This API cannot be overloaded.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Return value:**

| Type | Description |
| --- | --- |
| [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) | Remote object of the authenticator, which is used for inter-process communication. |

**Examples**

```TypeScript
This API must be used together with the getRemoteObject API. For details, see the example of the [getRemoteObject](#getremoteobject) API.
```

## setProperties

```TypeScript
setProperties(options: SetPropertiesOptions, callback: AuthCallback): void
```

Sets the authenticator properties. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SetPropertiesOptions](arkts-basicservices-appaccount-setpropertiesoptions-i.md) | Yes | Authenticator properties to set. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Examples**

```TypeScript
This API must be used together with the getRemoteObject API. For details, see the example of the [getRemoteObject](#getremoteobject) API.
```

## verifyCredential

```TypeScript
verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void
```

Verifies the credential of an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| options | [VerifyCredentialOptions](arkts-basicservices-appaccount-verifycredentialoptions-i.md) | Yes | Options for credential verification. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Examples**

```TypeScript
This API must be used together with the getRemoteObject API. For details, see the example of the [getRemoteObject](#getremoteobject) API.
```
