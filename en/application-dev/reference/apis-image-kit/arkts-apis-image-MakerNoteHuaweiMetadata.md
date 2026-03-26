# Class (MakerNoteHuaweiMetadata)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

MakerNoteHuaweiMetadata implements Metadata

Photo metadata from Huawei cameras.

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

| Name                                   | Type          | Read-Only| Optional| Description                                                        |
| --------------------------------------- | -------------- | ---- | ---- | ------------------------------------------------------------ |
| isXmageSupported          | boolean  | No  | Yes  | Whether XMAGE is supported. **true** indicates yes; **false** indicates no.                         |
| xmageWatermarkMode        | number         | No  | Yes  | XMAGE watermark mode. For details, see [Constants](arkts-apis-image-c.md).|
| xmageLeft                 | number         | No  | Yes  | Horizontal coordinate of the left boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px.|
| xmageTop                  | number         | No  | Yes  | Vertical coordinate of the top boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px.|
| xmageRight                | number         | No  | Yes  | Horizontal coordinate of the right boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px.|
| xmageBottom               | number         | No  | Yes  | Vertical coordinate of the bottom boundary of the effective content area (excluding the watermark coverage area) on the original image, relative to the top-left origin of the image. The unit is px.|
| xmageColorMode            | [XmageColorMode](arkts-apis-image-e.md#xmagecolormode23) | No  | Yes  | XMAGE color mode.                                             |
| isCloudEnhanced           | boolean        | No  | Yes  | Whether the image has been cloud-enhanced. **true** indicates yes; **false** indicates no.                    |
| cloudLabel                | string         | No  | Yes  | Cloud enhancement label.                                                |
| isWindSnapshot            | boolean        | No  | Yes  | Whether the wind snapshot mode is used. **true** indicates yes; **false** indicates no.<br>This mode is a specialized photography mode designed for capturing fast-moving subjects or scenes prone to blurring, such as in windy conditions or when photographing moving objects.|
| sceneVersion              | number         | No  | Yes  | Version number of the scene recognition algorithm.                                                  |
| sceneFoodConfidence       | number         | No  | Yes  | Capture scene: food confidence.                                      |
| sceneStageConfidence      | number         | No  | Yes  | Capture scene: stage performance confidence.                                  |
| sceneBlueSkyConfidence    | number         | No  | Yes  | Capture scene: blue sky confidence.                                      |
| sceneGreenPlantConfidence | number         | No  | Yes  | Capture scene: green plant confidence.                                  |
| sceneBeachConfidence      | number         | No  | Yes  | Capture scene: beach confidence.                                      |
| sceneSnowConfidence       | number         | No  | Yes  | Capture scene: snow confidence.                                      |
| sceneSunsetConfidence     | number         | No  | Yes  | Capture scene: sunset confidence.                                      |
| sceneFlowersConfidence    | number         | No  | Yes  | Capture scene: flower confidence.                                      |
| sceneNightConfidence      | number         | No  | Yes  | Capture scene: night scene confidence.                                      |
| sceneTextConfidence       | number         | No  | Yes  | Capture scene: text confidence.                                      |
| faceCount                 | number         | No  | Yes  | Number of faces.                                                    |
| faceConfidences           | number[]       | No  | Yes  | Confidences of a specified number of faces.                                   |
| faceSmileScores           | number[]       | No  | Yes  | Smile scores of a specified number of faces.                                    |
| captureMode               | number         | No  | Yes  | Capture mode.                                                  |
| burstNumber               | number         | No  | Yes  | Number of burst shots.                                                  |
| isFrontCamera             | boolean        | No  | Yes  | Whether to use the front camera. **true** indicates yes; **false** indicates no.                    |
| rollAngle                 | number         | No  | Yes  | Horizontal pan angle.                                                |
| pitchAngle                | number         | No  | Yes  | Pitch angle.                                                  |
| physicalAperture          | number         | No  | Yes  | Physical aperture, in fNumber.                                                  |
| focusMode                 | [FocusMode](arkts-apis-image-e.md#focusmode23) | No  | Yes  | Lens focus control policy, which determines how the camera adjusts the focal length.               |

## createInstance

static createInstance(): MakerNoteHuaweiMetadata

Returns an empty [MakerNoteHuaweiMetadata](arkts-apis-image-MakerNoteHuaweiMetadata.md) instance.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Returns**:

| Type                                                        | **Description**                                 |
| ------------------------------------------------------------ | ------------------------------------- |
| [MakerNoteHuaweiMetadata](arkts-apis-image-MakerNoteHuaweiMetadata.md) | Empty **MakerNoteHuaweiMetadata** instance.|

**Example**:

```ts
async function makerNoteHuaweiCreateInstance(context: Context) {
  let makerNoteHuaweiMetadata = image.MakerNoteHuaweiMetadata.createInstance();
  if (makerNoteHuaweiMetadata != undefined) {
    console.info("createInstance success");
  }
}
```

## getProperties

getProperties(key: Array\<string>): Promise\<Record\<string, string \| null>>

Obtains image property values. This API returns the result asynchronously through a promise.

For details about the properties, see [PropertyKey](arkts-apis-image-e.md#propertykey7).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**:

| Name| Type          | Mandatory| Description                    |
| ------ | -------------- | ---- | ------------------------ |
| key    | Array\<string> | Yes  | Property names.|

**Returns**:

| Type                                    | **Description**                                                        |
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
  const filePath: string = context.cacheDir + '/exif.jpg';  // An image containing Exif metadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiGetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    await metaData.makerNoteHuaweiMetadata.getProperties(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]).then((data) => {
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

For details about the properties, see [PropertyKey](arkts-apis-image-e.md#propertykey7).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**:

| Name | Type                          | Mandatory| Description                    |
| ------- | ------------------------------ | ---- | ------------------------ |
| records | Record\<string, string \| null> | Yes  | Array containing key-value pairs representing properties and their corresponding values of the **MakerNoteHuaweiMetadata** object to be modified.|

**Returns**:

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value.|

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
  const filePath: string = context.cacheDir + '/exif.jpg';  // An image containing Exif metadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiSetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    let setkey: Record<string, string | null> = {
      "HwMnoteIsXmageSupported": "1",
      "HwMnoteXmageMode": "9"
    };
    await metaData.makerNoteHuaweiMetadata.setProperties(setkey).then(async () => {
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

getAllProperties(): Promise\<Record\<string, string \| null>>

Obtains all properties and their values from the image metadata. This API returns the result asynchronously through a promise.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Returns**:

| Type                                    | Description                                       |
| ---------------------------------------- | ------------------------------------------- |
| Promise\<Record\<string, string \| null>> | Promise used to return all key-value pairs defined in the metadata.|

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // An image containing Exif metadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiGetAllProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    await metaData.makerNoteHuaweiMetadata.getAllProperties().then((data) => {
      const count = Object.keys(data).length;
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

clone(): Promise\<MakerNoteHuaweiMetadata>

Clones [MakerNoteHuaweiMetadata](arkts-apis-image-MakerNoteHuaweiMetadata.md) metadata. This API returns the result asynchronously through a promise.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Returns**:

| Type                                                        | Description                                                    |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| Promise\<[MakerNoteHuaweiMetadata](arkts-apis-image-MakerNoteHuaweiMetadata.md)> | Promise used to return the **MakerNoteHuaweiMetadata** metadata instance if metadata is successfully obtained.|

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // An image containing Exif metadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiClone(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    let new_metadata = await metaData.makerNoteHuaweiMetadata.clone();
    new_metadata.getProperties(["HwMnoteIsXmageSupported"]).then((data1) => {
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

**Returns**:

| Type                 | Description                                 |
| --------------------- | ------------------------------------- |
| Promise\<ArrayBuffer> | Promise used to return the binary data of the metadata.|

**Example**:

```ts
import { fileIo as fs } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // An image containing Exif metadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiGetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    let blob = await metaData.makerNoteHuaweiMetadata.getBlob();
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

**Parameters**:

| Name| Type       | Mandatory| Description                |
| ------ | ----------- | ---- | -------------------- |
| blob   | ArrayBuffer | Yes  | Binary data used to replace the metadata.|

**Returns**:

| Type          | **Description**         |
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
  const filePath: string = context.cacheDir + '/exif.jpg';  // An image containing Exif metadata is required.
  const file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiSetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    let blob = await metaData.makerNoteHuaweiMetadata.getBlob();
    if (blob != undefined) {
      console.info("get blob success");
      metaData.makerNoteHuaweiMetadata.setBlob(blob);
    }
    let new_blob = metaData.makerNoteHuaweiMetadata.getBlob();
    if (new_blob != undefined) {
      console.info("new_blob is not undefined");
    }
  }
}
```
<!--no_check-->