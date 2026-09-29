# AddressFamily

```TypeScript
export enum AddressFamily
```

Enumerates IP address families of the target domain name.

**Since:** 15

<!--Device-http-export enum AddressFamily--><!--Device-http-export enum AddressFamily-End-->

**System capability:** SystemCapability.Communication.NetStack

## DEFAULT

```TypeScript
DEFAULT = 'CURL_IPRESOLVE_WHATEVER'
```

Automatically selects the IPv4 or IPv6 address of the target domain name.

**Since:** 15

<!--Device-AddressFamily-DEFAULT = 'CURL_IPRESOLVE_WHATEVER'--><!--Device-AddressFamily-DEFAULT = 'CURL_IPRESOLVE_WHATEVER'-End-->

**System capability:** SystemCapability.Communication.NetStack

## ONLY_V4

```TypeScript
ONLY_V4 = 'CURL_IPRESOLVE_V4'
```

Resolves only the IPv4 address of the target domain name and ignores the IPv6 address.

**Since:** 15

<!--Device-AddressFamily-ONLY_V4 = 'CURL_IPRESOLVE_V4'--><!--Device-AddressFamily-ONLY_V4 = 'CURL_IPRESOLVE_V4'-End-->

**System capability:** SystemCapability.Communication.NetStack

## ONLY_V6

```TypeScript
ONLY_V6 = 'CURL_IPRESOLVE_V6'
```

Resolves only the IPv6 address of the target domain name and ignores the IPv4 address.

**Since:** 15

<!--Device-AddressFamily-ONLY_V6 = 'CURL_IPRESOLVE_V6'--><!--Device-AddressFamily-ONLY_V6 = 'CURL_IPRESOLVE_V6'-End-->

**System capability:** SystemCapability.Communication.NetStack
