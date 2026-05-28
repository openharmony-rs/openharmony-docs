# Geolocation Information Is Missing from Images
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Symptom

After an image is opened in read-only mode, geolocation information in the image cannot be obtained during image parsing.

## Possible Cause

To protect sensitive information in user images, [Media Library Kit](../photoAccessHelper-overview.md) desensitizes images when applications read them by removing sensitive fields from the image EXIF data. As a result, geolocation information may be missing when the image is used.

> **NOTE**
>
> Desensitization applies only to images, not videos.

## Solution

After the application requests the [ohos.permissions.MEDIA_LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location) permission, desensitization is disabled for the application, allowing it to obtain all sensitive information from the image.

**Example**

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { dataSharePredicates } from '@kit.ArkData';
import { common } from '@kit.AbilityKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { image } from '@kit.ImageKit';

@Entry({ routeName : 'Scene1' })
@Component
export struct Scene1 {

  @State latitude: string = '';

  build() {
    NavDestination() {
      Column({ space: 20 }) {

        Button('example')
          .width('80%')
          .height(50)
          .fontSize(16)
          .onClick(async () => {
            let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
            this.latitude = await example(phAccessHelper, context);
          })
      }
      .width('100%')
      .height('100%')
    }
    .title('Get from Media Library')
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context): Promise<string> {
  try {
    // Obtain the image URI.
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = 
      await phAccessHelper.getAssets(fetchOption);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    // Open the image using the image URI.
    let file: fs.File = fs.openSync(photoAsset.uri, fs.OpenMode.READ_ONLY);
    const imageSourceObj = image.createImageSource(file.fd);
    console.info("getImagePropertySync");
    // Obtain the latitude information from the image.
    let latitude = imageSourceObj.getImagePropertySync(image.PropertyKey.GPS_LATITUDE);
    return latitude;
  } catch (err) {
    console.error(`get latitude failed with error: ${err.code}, ${err.message}`);
    return `get latitude failed with error: ${err.code}, ${err.message}`;
  }
}
```

## Appendix

For details about geolocation fields and how to use them, see [PropertyKey](../../../reference/apis-image-kit/arkts-apis-image-e.md#propertykey7) in Image Kit.

| Name |  Description|
| ----- | ---- |
| GPSLatitude | Image latitude.|
| GPSLongitude | Image longitude.|
| GPSTimeStamp | GPS timestamp.|
| GPSDateStamp | GPS date stamp.|
| GPSAltitude | Altitude based on **GPSAltitudeRef**.|
| GPSVersionID | GPS information version.|
