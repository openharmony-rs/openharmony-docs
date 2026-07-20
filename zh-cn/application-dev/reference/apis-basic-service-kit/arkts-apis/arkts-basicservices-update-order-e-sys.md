# Order（系统接口）

升级指令。

**起始版本：** 9

<!--Device-update-export enum Order--><!--Device-update-export enum Order-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## DOWNLOAD

```TypeScript
DOWNLOAD = 1
```

下载。适合仅下载升级包场景。

**起始版本：** 9

<!--Device-Order-DOWNLOAD = 1--><!--Device-Order-DOWNLOAD = 1-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## INSTALL

```TypeScript
INSTALL = 2
```

安装。适合直接安装已下载的升级包场景。

**起始版本：** 9

<!--Device-Order-INSTALL = 2--><!--Device-Order-INSTALL = 2-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## DOWNLOAD_AND_INSTALL

```TypeScript
DOWNLOAD_AND_INSTALL = 3
```

下载并安装。适合下载并安装场景。

**起始版本：** 9

<!--Device-Order-DOWNLOAD_AND_INSTALL = 3--><!--Device-Order-DOWNLOAD_AND_INSTALL = 3-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## APPLY

```TypeScript
APPLY = 4
```

生效。仅生效已安装的升级包，设备将重启以应用新版本，适用于已安装完成需重启生效的场景。

**起始版本：** 9

<!--Device-Order-APPLY = 4--><!--Device-Order-APPLY = 4-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## INSTALL_AND_APPLY

```TypeScript
INSTALL_AND_APPLY = 6
```

安装并生效，执行安装后设备将重启以应用新版本。适用于需要快速完成系统更新并立即生效的场景。

**起始版本：** 9

<!--Device-Order-INSTALL_AND_APPLY = 6--><!--Device-Order-INSTALL_AND_APPLY = 6-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

