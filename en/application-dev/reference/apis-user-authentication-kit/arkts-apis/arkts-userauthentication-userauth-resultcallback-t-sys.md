# ResultCallback (System API)

```TypeScript
type ResultCallback = (challenge: Uint8Array, result: UserAuthResult) => void
```

Triggered to return the remote authentication result. This callback type is used in remote authentication scenarios. After remote authentication is complete, the system calls this callback function to return the authentication result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| challenge | Uint8Array | Yes | Challenge value. It is a one-time random number used to prevent replay attacks, and is the same as the challenge value passed during authentication initiation. |
| result | [UserAuthResult](arkts-userauthentication-userauth-userauthresult-i.md) | Yes | User authentication result. It contains information such as the authentication result code and authentication token. |
