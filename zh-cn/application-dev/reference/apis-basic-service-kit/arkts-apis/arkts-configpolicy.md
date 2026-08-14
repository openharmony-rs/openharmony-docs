# @ohos.configPolicy

配置策略提供按系统预定义的定制配置层级获取对应目录和文件路径的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace configPolicy--><!--Device-unnamed-declare namespace configPolicy-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCfgDirList](arkts-basicservices-configpolicy-getcfgdirlist-f-sys.md#getCfgDirList) | 获取配置层级目录列表，按优先级从低到高。使用callback异步回调。 |
| [getCfgDirList](arkts-basicservices-configpolicy-getcfgdirlist-f-sys.md#getCfgDirList（系统接口）) | 获取配置层级目录列表，按优先级从低到高。使用Promise异步回调。 |
| [getCfgDirListSync](arkts-basicservices-configpolicy-getcfgdirlistsync-f-sys.md#getCfgDirListSync) | 获取配置层级目录列表，按优先级从低到高。 |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles) | 获取指定文件名的所有文件列表，按优先级从低到高。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml。 最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml。 |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles（系统接口）) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、 /sys_pod/etc/carrier/46060/etc/config.xml。设备默认卡opkey为46060，设置的followMode为 configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles（系统接口）) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、 /sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为 configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/\\${telephony.sim.opkey0}"。 最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles（系统接口）) | 获取指定文件名的所有文件列表，按优先级从低到高。使用Promise异步回调。 |
| [getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles（系统接口）) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用Promise异步回调。 |
| [getCfgFilesSync](arkts-basicservices-configpolicy-getcfgfilessync-f-sys.md#getCfgFilesSync) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。 |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile) | 获取指定文件名优先级最高的配置文件路径。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml， 最终返回优先级最高的是：/sys_pod/etc/config.xml。 |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile（系统接口）) | 根据提供的跟随模式获取指定文件名优先级最高的配置文件路径。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、 /sys_pod/etc/carrier/46060/etc/ config.xml。设备默认卡opkey为46060，设置的followMode为configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是： /sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile（系统接口）) | 根据跟随模式获取指定文件优先级最高的配置文件路径。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、 /sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为 configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/\\${telephony.sim.opkey0}"。 最终返回的是：/sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile（系统接口）) | 获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。 |
| [getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile（系统接口）) | 根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。 |
| [getOneCfgFileSync](arkts-basicservices-configpolicy-getonecfgfilesync-f-sys.md#getOneCfgFileSync) | 根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) |  |
<!--DelEnd-->

