# VerifyPinHandler

VerifyPinHandler is a class in the Web component that handles PIN code verification requests. It is used to enhance app security in scenarios requiring identity authentication on web pages (such as secure payment, sensitive operation confirmation, etc.). When user PIN authentication is required, this handler is provided to the app through the onVerifyPin event callback, allowing the app to respond to the PIN verification result, effectively preventing unauthorized access and protecting user privacy. For sample code, see [onVerifyPin](arkts-arkweb-web-comp-attribute.md#onverifypin).

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## confirm

```TypeScript
confirm(result: PinVerifyResult): void
```

Notifies the Web component of the PIN authentication result. The app calls this method to return the PIN verification result to the Web component, which then continues the subsequent authentication process based on the result. If the verification is successful, the Web component allows access to protected content; if the verification fails, the Web component denies access and may prompt the user to retry.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [PinVerifyResult](arkts-arkweb-pinverifyresult-e.md) | Yes | PIN authentication result. If successful, the Web component allows subsequent page operations; if failed, page navigation or content loading may be blocked. |

## constructor

```TypeScript
constructor()
```

A constructor used to create a **VerifyPinHandler** instance.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core
