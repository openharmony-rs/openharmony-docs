# PrivacyManagerService

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=f8f1e523aebe959987f2877f5d589fbc2903d846 translatedAt=2026-07-30T03:00:13.207Z pushedAt=2026-07-30T08:25:03.771Z -->

PrivacyManagerService is a command line capability developed based on [hidumper](hidumper.md) for access control. It can display basic access control information and obtain the usage records of sensitive permissions.

## Environment Setup

Set up the environment by referring to [Environment Setup](hidumper.md#environment-setup).

## Obtaining Help Information

To view the help information, run the following command:

```shell
hidumper -s PrivacyManagerService -a '-h'
```

 **Example**

```text

-------------------------------[ability]-------------------------------


----------------------------------PrivacyManagerService----------------------------------
Privacy Dump:
Usage:
       -h: command help
       -t <TOKEN_ID>: according to specific token id dump permission used records
```

## Obtaining Sensitive Permission Usage Records

You can view sensitive permission usage records by app process token ID using the following command.

```shell
hidumper -s PrivacyManagerService -a '-t <tokenId>'
```

You can run the [atm-tool](../tools/atm-tool.md#dump) command to query the token ID required by the command.

 **Example**

```text
hidumper -s PrivacyManagerService -a '-t 536992218'

-------------------------------[ability]-------------------------------


----------------------------------PrivacyManagerService----------------------------------
Privacy Dump:
{
  "permissionRecord": [
    {
      "bundleName": "com.ohos.camera",
      "isRemote": false,
      "permissionName": "ohos.permission.READ_IMAGEVIDEO",
      "lastAccessTime": 1508577149393,
      "lastAccessDuration": 0,
      "accessCount": 2
    }
  ]
}
```