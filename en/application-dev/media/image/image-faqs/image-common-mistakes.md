# Common Crash and Error Issues in Image Kit
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @ww_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T07:03:30.965Z pushedAt=2026-06-03T10:07:13.122Z -->

This document presents typical incorrect usage cases of Image Kit APIs, helping developers avoid common development issues and improve application stability and performance.

## Crash Caused by PixelMap Being Released or Modified During Encoding

**Typical Crash Stack Example:**

``` text
Fault thread info:
Tid:5005, Name:OS_FFRT_3_0
#00 pc 000000000006d1f0 /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtWStream::write(void const*, unsigned long)+24)(300e33eb41735f2d3c8fe2259a671217)
#01 pc 0000000001828c94 /system/lib64/libskia_canvaskit.z.so(sk_empty_output_buffer(jpeg_compress_struct*)+48)(484139254f1cae74fd86fe798dbea128)
#02 pc 00000000010d1bb4 /system/lib64/libskia_canvaskit.z.so(encode_mcu_huff+692)(484139254f1cae74fd86fe798dbea128)
#03 pc 00000000010c8a88 /system/lib64/libskia_canvaskit.z.so(compress_output+384)(484139254f1cae74fd86fe798dbea128)
#04 pc 0000000000f8c4b0 /system/lib64/libskia_canvaskit.z.so(jpeg_finish_compress+220)(484139254f1cae74fd86fe798dbea128)
#05 pc 0000000000f8bf08 /system/lib64/libskia_canvaskit.z.so(SkJpegEncoderImpl::onEncodeRows(int)+384)(484139254f1cae74fd86fe798dbea128)
#06 pc 0000000000fd25ac /system/lib64/libskia_canvaskit.z.so(SkEncoder::encodeRows(int)+68)(484139254f1cae74fd86fe798dbea128)
#07 pc 0000000000fd2514 /system/lib64/libskia_canvaskit.z.so(SkJpegEncoder::Encode(SkWStream*, SkPixmap const&, SkJpegEncoder::Options const&)+64)(484139254f1cae74fd86fe798dbea128)
#08 pc 00000000000545dc /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtEncoder::SkEncodeImage(SkWStream*, SkBitmap const&, SkEncodedImageFormat, int)+188)(300e33eb41735f2d3c8fe2259a671217)
#09 pc 00000000000547a4 /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtEncoder::DoEncode(SkWStream*, SkBitmap const&, SkEncodedImageFormat const&)+204)(300e33eb41735f2d3c8fe2259a671217)
#10 pc 0000000000055464 /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtEncoder::EncodeImageByBitmap(SkBitmap&, bool, SkWStream&)+284)(300e33eb41735f2d3c8fe2259a671217)
#11 pc 0000000000055ad8 /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtEncoder::EncodeImageByPixelMap(OHOS::Media::PixelMap*, bool, SkWStream&)+1356)(300e33eb41735f2d3c8fe2259a671217)
#12 pc 0000000000053350 /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtEncoder::EncodeSdrImage(OHOS::ImagePlugin::ExtWStream&)+984)(300e33eb41735f2d3c8fe2259a671217)
#13 pc 0000000000052684 /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtEncoder::PixelmapEncode(OHOS::ImagePlugin::ExtWStream&)+184)(300e33eb41735f2d3c8fe2259a671217)
#14 pc 0000000000053a7c /system/lib64/platformsdk/libextplugin.z.so(OHOS::ImagePlugin::ExtEncoder::FinalizeEncode()+952)(300e33eb41735f2d3c8fe2259a671217)
#15 pc 00000000000b7d00 /system/lib64/platformsdk/libimage_native.z.so(std::__h::__function::__func<OHOS::Media::ImagePacker::FinalizePacking()::$_3, std::__h::allocator<OHOS::Media::ImagePacker::FinalizePacking()::$_3>, unsigned int (OHOS::ImagePlugin::AbsImageEncoder*)>::operator()(OHOS::ImagePlugin::AbsImageEncoder*&&)+28)(abee48eb37a365d523ba3560f087b63a)
#16 pc 00000000000b58b4 /system/lib64/platformsdk/libimage_native.z.so(OHOS::Media::ImagePacker::DoEncodingFunc(std::__h::function<unsigned int (OHOS::ImagePlugin::AbsImageEncoder*)>, bool)+272)(abee48eb37a365d523ba3560f087b63a)
#17 pc 00000000000b6de4 /system/lib64/platformsdk/libimage_native.z.so(OHOS::Media::ImagePacker::FinalizePacking(long&)+80)(abee48eb37a365d523ba3560f087b63a)
#18 pc 000000000009a5b8 /system/lib64/platformsdk/libimage_napi.z.so(OHOS::Media::PackToFileExec(napi_env__*, void*)+912)(1d95fd2a148829930aeec8cbeaf92976)
#19 pc 000000000006258c /system/lib64/platformsdk/libace_napi.z.so(NativeAsyncWork::AsyncWorkCallback(uv_work_s*)+264)(f5de54fc91f8cc9643b4846b808f9d4c)
#20 pc 0000000000013bd4 /system/lib64/platformsdk/libuv.so(uv__queue_work+48)(7dfe11681838c768af19f3408663affb)
 ...
 
```
**Crash Cause:**
`await` is not used to wait for the asynchronous operation to complete during encoding, causing resource objects to be released or modified prematurely before the asynchronous operation finishes.

**Solution:**

1. **Lifecycle management of asynchronous operations:** When calling asynchronous APIs of Image Kit (such as [packToData](../../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodata13), [packToFile](../../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofile11), [createPixelMap](../../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#createpixelmap7), etc.), ensure that the passed resource objects (such as PixelMap, ImageSource) are not released or modified before the asynchronous operation completes.

2. **Use await or Promise.then:** It is recommended to use `await` to wait for the asynchronous operation to complete, or release resources in the callback of `Promise.then()` to ensure the correct release timing.

3. **Page lifecycle management:** If asynchronous image operations are used in a page, ensure that all asynchronous operations have been completed or canceled when the page is destroyed, to prevent asynchronous callbacks from accessing destroyed resources after the page is unloaded.

**Incorrect Code Example:**

``` TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function wrongPackingExample(pixelMap: image.PixelMap, fd: number): Promise<void> {
  let imagePacker = image.ImagePacker | null = null;

  try {
    imagePacker = image.createImagePacker();
    let packOpts: image.PackingOption = { format: 'image/jpeg', quality: 95 };
    // Error: Modifying pixelMap during asynchronous encoding.
    pixelMap.crop({x:1, y:1, size: {height:200, width:200}});
    
     // Error: Asynchronous operation does not use await.
    imagePacker.packToFile(pixelMap, fd, packOpts).then(() => {
      console.info('Succeeded in packing the image to file.');
    }).catch((error: BusinessError) => {
      console.error('Pack failed: ' + error);
    });

  } catch (error) {
    console.error('Pack failed: ' + error);
  } finally {    
    // Error: Releasing PixelMap before asynchronous encoding is complete, causing the application to crash.
    pixelMap?.release();
    imagePacker?.release();
  }
}
```

**Correct Code Example:**

``` TypeScript
import { image } from '@kit.ImageKit';

async function correctPackingExample(pixelMap: image.PixelMap, fd: number): Promise<void> {
  let imagePacker = image.ImagePacker | null = null;

  try {
    imagePacker = image.createImagePacker();
    let packOpts: image.PackingOption = { format: 'image/jpeg', quality: 95 };

    // Correct: When cropping PixelMap, you must use await to wait for the operation to complete.
    await pixelMap.crop({x:1, y:1, size: {height:200, width:200}});
    
    // Correct: Use await to wait for the asynchronous operation to complete.
    await imagePacker.packToFile(pixelMap, fd, packOpts);
    console.info('Pack success');

  } catch (error) {
    console.error('Pack failed: ' + error)
  } finally {
    pixelMap?.release();
    imagePacker?.release();
  }
}
```

## Multiple Asynchronous Operations Sharing the Same ImageSource Object

**Typical Crash Stack Example:**

``` text
Fault thread info:
Tid: 41048, Name: OS_FFRT_3_5
#00 pc 00000000000b0864 /system/lib64/platformsdk/libimage_napi.z.so(OHOS::Media::CreatePixelMapInner(OHOS::Media::ImageSourceNapi*, std::__h::shared_ptr<OHOS::Media::ImageSource>, unsigned int, OHOS::Media::DecodeOptions, unsigned int8)+116) (3a63d0a0dc3ac58d9e1a58a77ad194f9)
#01 pc 00000000000b1178 /system/lib64/platformsdk/libimage_napi.z.so(OHOS::Media::CreatePixelMapExecute(napi_env__*, void*) (.1167.cfi)+308) (3a63d0a0dc3ac58d9e1a58a77ad194f9)
#02 pc 000000000005c3c0 /system/lib64/platformsdk/libace_napi.z.so(NativeAsyncWork: :AsyncWorkCallback(uv_work_s*)+304) (68011f831ed16fa3d94d4f22664d2eaf)
#03 pc 0000000000013614 /system/lib64/platformsdk/libuv.so(uv__queue_work+60)(1399a989328aa340c8622e4a1d0ca961)
#04 pc 0000000000091794 /system/lib64/ndk/libffrt.so(ffrt::UVTask::Execute()+764) (7921196b695415b02aa2bódfb05c7deb)
#05
pc 000000000008d13c /system/lib64/ndk/libffrt.so(ffrt::ExecuteTask(ffrt::TaskBase*)+248) (7921196b695415b02aa2b6dfb05c7deb)
#06 pc 000000000002e054 /system/lib64/ndk/libffrt.so(ffrt::CPUWorker::RunTask(ffrt: :TaskBase*, ffrt::CPUWorker*)+84) (7921196b695415b02aa2bódfb05c7deb)
#07 pc 00000000000cóc58 /system/lib64/ndk/libffrt.so(7921196b695415b02aa2b6dfb05c7deb)
#08 pc 00000000001d8c5c /system/lib/ld-musl-aarch64.so.1(start+240)(05aecbbf0bdce12d75badb7b497d0f9f)
 ...
```
**Crash Cause:**
Concurrent operations on the same ImageSource object cause resource race conditions, leading to a crash.

**Solution:**

1. **Avoid concurrent access:** Do not perform multiple asynchronous operations concurrently on the same ImageSource instance. It is recommended to execute them sequentially, ensuring one operation completes before starting the next.

2. **Resource lifecycle:** The lifecycle of ImageSource should cover all asynchronous operations that use it. Release it only after confirming that all asynchronous operations have completed.

3. **Performance considerations:** Although sequential execution may reduce concurrency performance, it avoids race conditions and crashes. If concurrent processing is truly needed, create multiple independent ImageSource instances.


**Incorrect Code Example:**

``` TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function wrongSharedImageSourceExample(filePath: string, decodingOptions: Array<image.DecodingOptions>): Promise<Array<image.PixelMap>> {
  // Create an ImageSource instance.
  const imageSource = image.createImageSource(filePath);
  const pixelMaps: Array<image.PixelMap> = [];

  // Error: Multiple decoding operations are launched concurrently in a for loop, sharing the same ImageSource.
  for (const opts of decodingOptions) {
    imageSource.createPixelMap(opts).then((pixelMap: image.PixelMap) => {
      pixelMaps.push(pixelMap);
      console.info('PixelMap created');
    }).catch((error: BusinessError) => {
      console.error('Create pixelMap failed: ' + error);
    });
  }

  // Error: ImageSource is released immediately, while the asynchronous operation may still be executing.
  imageSource.release();
  return pixelMaps;
}
```

**Correct Code Example:**

``` TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function correctSharedImageSourceExample(filePath: string): Promise<void> {
  // Create an ImageSource instance.
  const imageSource = image.createImageSource(filePath);

  try {
    // Correct: Execute asynchronous operations sequentially to avoid concurrent access.
    const imageInfo = await imageSource.getImageInfo();
    console.info(`Image info: width=${imageInfo.size.width}, height=${imageInfo.size.height}`);

    const pixelMap1 = await imageSource.createPixelMap({ editable: true });
    console.info('First pixelMap created');

    const pixelMap2 = await imageSource.createPixelMap({ editable: false });
    console.info('Second pixelMap created');

    // Release resources after use.
    pixelMap1.release();
    pixelMap2.release();
  } catch (error) {
    console.error('Operation failed: ' + error);
  }

  // Safely release the ImageSource after all operations are complete.
  imageSource.release();
}
```