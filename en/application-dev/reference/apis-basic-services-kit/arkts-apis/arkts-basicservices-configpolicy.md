# @ohos.configPolicy(Configuration Policy)

The **configPolicy** module provides APIs for obtaining the corresponding directory and file path based on the predefined custom configuration level.

**Since:** 8

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getCfgDirList](arkts-basicservices-configpolicy-getcfgdirlist-f-sys.md) | Obtains a list of configuration level directories, in ascending order of priority. This API uses an asynchronous callback to return the result. |
| [getCfgDirList](arkts-basicservices-configpolicy-getcfgdirlist-f-sys.md) | Obtains a list of configuration level directories, in ascending order of priority. This API uses a promise to return the result. |
| [getCfgDirListSync](arkts-basicservices-configpolicy-getcfgdirlistsync-f-sys.md) | Obtains a list of configuration level directories, in ascending order of priority. |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md) | Obtains a list of all files with the specified names, in ascending order of priority. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml** and **\/sys_pod/etc/config.xml** in ascending order of priority, **\/system/etc/config.xml, /sys_pod/etc/config.xml** is returned. |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md) | Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml**, **\/sys_pod/etc/config.xml**, and **\/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the default opkey of the device is **46060**, and **followMode** is set to **configPolicy.FollowXMode.SIM_DEFAULT**, the return value is **\/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml**. |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md) | Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml**, **\/sys_pod/etc/config.xml**, and **\/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the opkey of the device card 1 is **46060**, **followMode** is set to **configPolicy.FollowXMode.USER_DEFINED**, and the custom follow rule is **"etc/carrier/&#36;{telephony.sim.opkey0}"**, the return value is **\/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml**. |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md) | Obtains a list of all files with the specified names, in ascending order of priority. This API uses a promise to return the result. |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md) | Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority. This API uses a promise to return the result. |
| [getCfgFilesSync](arkts-basicservices-configpolicy-getcfgfilessync-f-sys.md) | Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority. |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md) | Obtains the path of the configuration file with the highest priority. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml** and **\/sys_pod/etc/config.xml** in ascending order of priority, **\/sys_pod/etc/config.xml** is returned. |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md) | Obtains the path of the configuration file with the highest priority. This API uses a promise to return the result. |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md) | Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml**, **\/sys_pod/etc/config.xml**, and **\/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the default opkey of the device is **46060**, and **followMode** is set to **configPolicy.FollowXMode.SIM_DEFAULT**, the final return value is **\/sys_pod/etc/carrier/46060/etc/config.xml**. |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md) | Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml**, **\/sys_pod/etc/config.xml**, and **\/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the opkey of the device card 1 is **46060**, **followMode** is set to **configPolicy.FollowXMode.USER_DEFINED**, and the custom follow rule is **"etc/carrier/&#36;{telephony.sim.opkey0}"**, the final return value is **\/sys_pod/etc/carrier/46060/etc/config.xml**. |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md) | Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses a promise to return the result. |
| [getOneCfgFileSync](arkts-basicservices-configpolicy-getonecfgfilesync-f-sys.md) | Obtains the path of the configuration file with the highest priority based on the provided follow mode. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | Define followXMode. |
<!--DelEnd-->
