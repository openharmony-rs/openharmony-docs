# Order（系统接口）

升级指令。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## DOWNLOAD

```TypeScript
DOWNLOAD = 1
```

下载。适合仅下载升级包场景。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## INSTALL

```TypeScript
INSTALL = 2
```

安装。适合直接安装已下载的升级包场景。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## DOWNLOAD_AND_INSTALL

```TypeScript
DOWNLOAD_AND_INSTALL = 3
```

下载并安装。适合下载并安装场景。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## APPLY

```TypeScript
APPLY = 4
```

生效。仅生效已安装的升级包，设备将重启以应用新版本，适用于已安装完成需重启生效的场景。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## INSTALL_AND_APPLY

```TypeScript
INSTALL_AND_APPLY = 6
```

安装并生效，执行安装后设备将重启以应用新版本。适用于需要快速完成系统更新并立即生效的场景。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。
