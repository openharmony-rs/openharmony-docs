# AddressFamily

枚举，解析目标域名时限定的地址类型。

**起始版本：** 15

<!--Device-http-export enum AddressFamily--><!--Device-http-export enum AddressFamily-End-->

**系统能力：** SystemCapability.Communication.NetStack

## DEFAULT

```TypeScript
DEFAULT = 'CURL_IPRESOLVE_WHATEVER'
```

设置此选项后，系统将自行选择目标域名的IPv4地址或IPv6地址。

**起始版本：** 15

<!--Device-AddressFamily-DEFAULT = 'CURL_IPRESOLVE_WHATEVER'--><!--Device-AddressFamily-DEFAULT = 'CURL_IPRESOLVE_WHATEVER'-End-->

**系统能力：** SystemCapability.Communication.NetStack

## ONLY_V4

```TypeScript
ONLY_V4 = 'CURL_IPRESOLVE_V4'
```

设置此选项后，系统仅解析目标域名的IPv4地址，忽略IPv6地址。

**起始版本：** 15

<!--Device-AddressFamily-ONLY_V4 = 'CURL_IPRESOLVE_V4'--><!--Device-AddressFamily-ONLY_V4 = 'CURL_IPRESOLVE_V4'-End-->

**系统能力：** SystemCapability.Communication.NetStack

## ONLY_V6

```TypeScript
ONLY_V6 = 'CURL_IPRESOLVE_V6'
```

设置此选项后，系统仅解析目标域名的IPv6地址，忽略IPv4地址。

**起始版本：** 15

<!--Device-AddressFamily-ONLY_V6 = 'CURL_IPRESOLVE_V6'--><!--Device-AddressFamily-ONLY_V6 = 'CURL_IPRESOLVE_V6'-End-->

**系统能力：** SystemCapability.Communication.NetStack

