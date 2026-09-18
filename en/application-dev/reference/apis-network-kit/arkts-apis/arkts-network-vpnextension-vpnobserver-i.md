# VpnObserver

Defines a VPN observer object. It is used to listen for VPN-related events. Before calling **VpnObserver** APIs, you need to create a VPN connection object by calling [vpnExtension.createVpnObserver](arkts-network-vpnextension-createvpnobserver-f.md).

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NetManager.Vpn

## Modules to Import

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## offAuthorizationResult

```TypeScript
offAuthorizationResult(callback?: Callback<boolean>): void
```

Unregisters a listener for the user authorization result.

> **NOTE:** 
> 
> If you have called [onAuthorizationResult](#onauthorizationresult) multiple times to register
> listeners and want to unregister the listener, you need to pass the callback passed in the last call or pass no
> parameter.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Vpn

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | No | Listener callback used to return the user authorization result.<br>If this parameter is passed, the specified listener is unregistered. If no parameter is passed, all registered listeners are unregistered. |

**Examples**

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';

let vpnObserver: vpnExtension.VpnObserver = vpnExtension.createVpnObserver();

let callback = (result: boolean) => {
  console.info('Authorization result: ' + result);
};
// Register a listener.
vpnObserver.onAuthorizationResult(callback);

// Unregister a specified listener.
vpnObserver.offAuthorizationResult(callback);

// Unregister all registered listeners.
vpnObserver.offAuthorizationResult();
```

## onAuthorizationResult

```TypeScript
onAuthorizationResult(callback: Callback<boolean>): void
```

Registers a listener for the user authorization result. The authorization result is displayed in a dialog box after [startVpnExtensionAbility](arkts-network-vpnextension-startvpnextensionability-f.md) is called. The notification is sent only when the user taps the dialog box, and only the result of the current VPN is received. If you do not need to listen for the authorization result, call [offAuthorizationResult](#offauthorizationresult) to cancel the registration.

> **NOTE:** 
> 
> If this API is called multiple times, only the last callback takes effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Vpn

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; | Yes | Callback used to return the user authorization result. The value **true** indicates that the user agrees to the authorization, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';

let vpnObserver: vpnExtension.VpnObserver = vpnExtension.createVpnObserver();
vpnObserver.onAuthorizationResult((result: boolean) => {
  if (result) {
    console.info('VPN authorization succeeded');
  } else {
    console.error('VPN authorization failed');
  }
});
```
