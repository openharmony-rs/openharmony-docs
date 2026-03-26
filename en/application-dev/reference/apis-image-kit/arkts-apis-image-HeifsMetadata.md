# Class (HeifsMetadata)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

HeifsMetadata implements Metadata

HEIF image sequence metadata.

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { image } from '@kit.ImageKit';
```

## Properties

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                        | Type  | Read-Only| Optional| Description                                      |
| ---------------------------- | ------ | ---- | ---- | ------------------------------------------ |
| heifsDelayTime | number | Yes  | Yes  | Playback duration of each frame in an HEIF image sequence, in milliseconds.|

## createInstance

static createInstance(): HeifsMetadata

Creates an empty [HeifsMetadata](arkts-apis-image-HeifsMetadata.md) instance.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                                              | Description                       |
| -------------------------------------------------- | --------------------------- |
| [HeifsMetadata](arkts-apis-image-HeifsMetadata.md) | Empty **HeifsMetadata** instance.|

**Example**:

```ts
async function heifsMetadataCreateInstance(context: Context) {
  let heifsMetadata = image.HeifsMetadata.createInstance();
  if (heifsMetadata != undefined) {
    console.info("createInstance success");
  }
}
```

## getProperties

getProperties(key: Array\<string>): Promise\<Record\<string, string \| null>>

Obtains the property values of image metadata. This API returns the result asynchronously through a promise.

For details about the properties, see [HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type          | Mandatory| Description                    |
| ------ | -------------- | ---- | ------------------------ |
| key    | Array\<string> | Yes  | Names of the properties to query.|

**Return value**

| Type                                    | Description                                                        |
| ---------------------------------------- | ------------------------------------------------------------ |
| Promise\<Record\<string, string \| null>> | Promise used to return the property values. If the operation fails, an error code is returned.|

**Error codes**:

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 7600202  | Unsupported metadata. Possible causes: unsupported metadata type. |

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // An image containing HeifsMetadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataGetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    await metaData.heifsMetadata.getProperties(["HeifsDelayTime"]).then((data) => {
      console.info('Get properties ',JSON.stringify(data));
    }).catch((error: BusinessError) => {
      console.error(`Get properties failed error.code is ${error.code}, error.message is ${error.message}`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

## setProperties

setProperties(records: Record\<string, string \| null>): Promise\<void>

Sets the values of specified properties in image metadata in batches. This API returns the result asynchronously through a promise.

For details about the properties, see [HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                          | Mandatory| Description                    |
| ------- | ------------------------------ | ---- | ------------------------ |
| records | Record<string, string \| null> | Yes| Set of key-value pairs representing the **HeifsMetadata** properties and corresponding values.|

**Return value**

| Type          | Description                                 |
| -------------- | ------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**:

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 7600202  | Unsupported metadata. Possible causes: Unsupported metadata type. |

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // An image containing HeifsMetadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataSetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    let setkey: Record<string, string | null> = {
      "HeifsDelayTime": "200",
    };
    await metaData.heifsMetadata.setProperties(setkey).then(async () => {
      console.info('Set properties success.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to set metadata Properties. code is ${error.code}, message is ${error.message}`);
    })
  } else {
    console.error('metadata is null. ');
  }
}
```

## getAllProperties

getAllProperties(): Promise\<Record<string, string \| null>>

Obtains all properties and their values from the image metadata. This API returns the result asynchronously through a promise.

For details about the properties, see [HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                                    | Description                                       |
| ---------------------------------------- | ------------------------------------------- |
| Promise\<Record\<string, string \| null>> | Promise used to return the values of all properties.|

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // An image containing HeifsMetadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataGetAllProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    await metaData.heifsMetadata.getAllProperties().then((data) => {
      const count = Object.keys(data).length;
      console.info('Metadata have ', count, ' properties');
      console.info(`Get metadata all properties: ${data}`);
    }).catch((error: BusinessError) => {
      console.error(`Get metadata all properties failed error.code is ${error.code}, error.message is ${error.message}`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

## clone

clone(): Promise\<HeifsMetadata>

Clones the HEIFS metadata. This API returns the result asynchronously through a promise.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                                                      | Description                                 |
| ---------------------------------------------------------- | ------------------------------------- |
| Promise\<[HeifsMetadata](arkts-apis-image-HeifsMetadata.md)> | Promise used to return the HEIFS metadata instance.|

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // An image containing HeifsMetadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataClone(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    let new_metadata = await metaData.heifsMetadata.clone();
    new_metadata.getProperties(["HeifsDelayTime"]).then((data1) => {
      console.info(`Clone new_metadata and get Properties: ${data1}`);
    }).catch((err: BusinessError) => {
      console.error(`Clone new_metadata failed, error : ${err}`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```


## getBlob<sup>23+</sup>

getBlob(): Promise\<ArrayBuffer>

Obtains the metadata in binary format. This API returns the result asynchronously through a promise.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise\<ArrayBuffer> | Promise used to return the binary data of the metadata.|

**Example**:

```ts
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // An image containing HeifsMetadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataGetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    let blob = await metaData.heifsMetadata.getBlob();
    if (blob != undefined) {
      console.info("get blob success");
    }
  }
}
```

## setBlob<sup>23+</sup>

setBlob(blob: ArrayBuffer): Promise\<void>

Replaces the current metadata with binary data. This API returns the result asynchronously through a promise.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type       | Mandatory| Description                |
| ------ | ----------- | ---- | -------------------- |
| blob   | ArrayBuffer | Yes  | Binary data used to replace the metadata.|

**Return value**

| Type          | Description         |
| -------------- | ------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**:

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 7600206  | Invalid parameter. Possible causes: The blob is empty or has a length of 0. |

**Example**:

```ts
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // An image containing HeifsMetadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataSetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    let blob = await metaData.heifsMetadata.getBlob();
    if (blob != undefined) {
      console.info("get blob success");
      metaData.heifsMetadata.setBlob(blob);
    }
    let new_blob = metaData.heifsMetadata.getBlob();
    if (new_blob != undefined) {
      console.info("new_blob is not undefined");
    }
  }
}
```
<!--no_check-->