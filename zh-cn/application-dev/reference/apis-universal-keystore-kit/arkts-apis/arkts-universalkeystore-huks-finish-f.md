# finish

## finish

```TypeScript
function finish(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

finish操作密钥接口。使用callback异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [huks.finishSession\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [huks.finishSession](arkts-universalkeystore-huks-finishsession-f.md#finishsession)(handle:

<!--Device-huks-function finish(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>): void--><!--Device-huks-function finish(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Finish操作的uint64类型的handle值。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Finish的参数集合。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;HuksResult&gt; | 是 | 回调函数。当密钥操作finish成功时，err为undefined，data为获取到的HuksResult；否则为错误对象。 |


## finish

```TypeScript
function finish(handle: number, options: HuksOptions): Promise<HuksResult>
```

finish操作密钥接口。使用Promise异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [huks.finishSession\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_9+\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [huks.finishSession](arkts-universalkeystore-huks-finishsession-f.md#finishsession)(

<!--Device-huks-function finish(handle: number, options: HuksOptions): Promise<HuksResult>--><!--Device-huks-function finish(handle: number, options: HuksOptions): Promise<HuksResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Finish操作的uint64类型的handle值。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Finish操作的参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise对象，返回HuksResult。 |

