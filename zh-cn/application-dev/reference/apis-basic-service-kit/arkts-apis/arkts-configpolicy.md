# @ohos.configPolicy

配置策略提供按系统预定义的定制配置层级获取对应目录和文件路径的能力。

**起始版本：** 8

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getCfgDirList](arkts-basicservices-configpolicy-getcfgdirlist-f-sys.md#getCfgDirList-1) | 获取配置层级目录列表，按优先级从低到高。使用callback异步回调。<br/> |
| <!--DelRow-->[getCfgDirList](arkts-basicservices-configpolicy-getcfgdirlist-f-sys.md#getCfgDirList-2) | 获取配置层级目录列表，按优先级从低到高。使用Promise异步回调。<br/> |
| <!--DelRow-->[getCfgDirListSync](arkts-basicservices-configpolicy-getcfgdirlistsync-f-sys.md#getCfgDirListSync-1) | 获取配置层级目录列表，按优先级从低到高。<br/> |
| <!--DelRow-->[getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles-1) | 获取指定文件名的所有文件列表，按优先级从低到高。使用callback异步回调。<br/>例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml。<br/>最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml。<br/> |
| <!--DelRow-->[getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles-2) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。<br/>例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、<br/>/sys_pod/etc/carrier/46060/etc/config.xml。设备默认卡opkey为46060，设置的followMode为<br/>configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, <br/>/sys_pod/etc/carrier/46060/etc/config.xml。<br/> |
| <!--DelRow-->[getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles-3) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。<br/>例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、<br/>/sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为<br/>configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/${telephony.sim.opkey0}"。<br/>最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。<br/> |
| <!--DelRow-->[getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles-4) | 获取指定文件名的所有文件列表，按优先级从低到高。使用Promise异步回调。<br/> |
| <!--DelRow-->[getCfgFiles](arkts-basicservices-configpolicy-getcfgfiles-f-sys.md#getCfgFiles-5) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用Promise异步回调。<br/> |
| <!--DelRow-->[getCfgFilesSync](arkts-basicservices-configpolicy-getcfgfilessync-f-sys.md#getCfgFilesSync-1) | 根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。<br/> |
| <!--DelRow-->[getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile-1) | 获取指定文件名优先级最高的配置文件路径。使用callback异步回调。<br/>例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml，<br/>最终返回优先级最高的是：/sys_pod/etc/config.xml。<br/> |
| <!--DelRow-->[getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile-2) | 根据提供的跟随模式获取指定文件名优先级最高的配置文件路径。使用callback异步回调。<br/>例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、<br/>/sys_pod/etc/carrier/46060/etc/<br/>config.xml。设备默认卡opkey为46060，设置的followMode为configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：<br/>/sys_pod/etc/carrier/46060/etc/config.xml。<br/> |
| <!--DelRow-->[getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile-3) | 根据跟随模式获取指定文件优先级最高的配置文件路径。使用callback异步回调。<br/>例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、<br/>/sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为<br/>configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/${telephony.sim.opkey0}"。<br/>最终返回的是：/sys_pod/etc/carrier/46060/etc/config.xml。<br/> |
| <!--DelRow-->[getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile-4) | 获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。<br/> |
| <!--DelRow-->[getOneCfgFile](arkts-basicservices-configpolicy-getonecfgfile-f-sys.md#getOneCfgFile-5) | 根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。<br/> |
| <!--DelRow-->[getOneCfgFileSync](arkts-basicservices-configpolicy-getonecfgfilesync-f-sys.md#getOneCfgFileSync-1) | 根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) |  |

