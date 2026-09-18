# PauseDownloadOptions (System API)

Defines the pausing download options, which are used to control the pause behavior. The object contains the **isAllowAutoResume** field. The value **true** indicates that automatically resuming download is allowed, and the value **false** indicates that download needs to be manually resumed.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## isAllowAutoResume

```TypeScript
isAllowAutoResume: boolean
```

Whether to allow automatic resuming of download. This parameter is set only when there is an ongoing download task.

The value **true** indicates that automatically resuming download is allowed and the system may automatically resume the download. The value **false** indicates that automatically resuming download is not allowed and you need to manually call **resumeDownload** to resume the download.

You are advised to set this parameter to **true** when the network is unstable, improving the download success rate. You are advised to set this parameter to **false** when the download time needs to be precisely controlled or resuming download needs to be prevented in specific network environments. In this case, you can call **resumeDownload** to control when to resume the download.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
