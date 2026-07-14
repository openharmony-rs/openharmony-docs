# @ohos.configPolicy

配置策略提供按系统预定义的定制配置层级获取对应目录和文件路径的能力。

**起始版本：** 8

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCfgDirList](arkts-basicservices-getcfgdirlist-f-sys.md#getcfgdirlist-1) | 获取配置层级目录列表，按优先级从低到高。使用callback异步回调。 |
| [getCfgDirList](arkts-basicservices-getcfgdirlist-f-sys.md#getcfgdirlist-2) | 获取配置层级目录列表，按优先级从低到高。使用Promise异步回调。 |
| [getCfgDirListSync](arkts-basicservices-getcfgdirlistsync-f-sys.md#getcfgdirlistsync-1) | 获取配置层级目录列表，按优先级从低到高。 |
| [getCfgFiles](arkts-basicservices-getcfgfiles-f-sys.md#getcfgfiles-1) | 获取指定文件名的所有文件列表，按优先级从低到高。使用callback异步回调。例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml。 |
| [getCfgFiles](arkts-basicservices-getcfgfiles-f-sys.md#getcfgfiles-2) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备默认卡opkey为46060，设置的followMode为configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getCfgFiles](arkts-basicservices-getcfgfiles-f-sys.md#getcfgfiles-3) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/${telephony.sim.opkey0}"。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getCfgFiles](arkts-basicservices-getcfgfiles-f-sys.md#getcfgfiles-4) | 获取指定文件名的所有文件列表，按优先级从低到高。使用Promise异步回调。 |
| [getCfgFiles](arkts-basicservices-getcfgfiles-f-sys.md#getcfgfiles-5) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用Promise异步回调。 |
| [getCfgFilesSync](arkts-basicservices-getcfgfilessync-f-sys.md#getcfgfilessync-1) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。 |
| [getOneCfgFile](arkts-basicservices-getonecfgfile-f-sys.md#getonecfgfile-1) | 获取指定文件名优先级最高的配置文件路径。使用callback异步回调。例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml，最终返回优先级最高的是：/sys_pod/etc/config.xml。 |
| [getOneCfgFile](arkts-basicservices-getonecfgfile-f-sys.md#getonecfgfile-2) | 根据提供的跟随模式获取指定文件名优先级最高的配置文件路径。使用callback异步回调。例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备默认卡opkey为46060，设置的followMode为configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：/sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getOneCfgFile](arkts-basicservices-getonecfgfile-f-sys.md#getonecfgfile-3) | 根据跟随模式获取指定文件优先级最高的配置文件路径。使用callback异步回调。例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/${telephony.sim.opkey0}"。最终返回的是：/sys_pod/etc/carrier/46060/etc/config.xml。 |
| [getOneCfgFile](arkts-basicservices-getonecfgfile-f-sys.md#getonecfgfile-4) | 获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。 |
| [getOneCfgFile](arkts-basicservices-getonecfgfile-f-sys.md#getonecfgfile-5) | 根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。 |
| [getOneCfgFileSync](arkts-basicservices-getonecfgfilesync-f-sys.md#getonecfgfilesync-1) | 根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FollowXMode](arkts-basicservices-followxmode-e-sys.md) |  |
<!--DelEnd-->

