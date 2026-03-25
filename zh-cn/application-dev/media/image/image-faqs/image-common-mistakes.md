# Image Kit常见崩溃报错问题
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @ww_Machine_cc-->

本文档展示了Image Kit接口的典型错误用法案例，帮助开发者避免常见的开发陷阱，提高应用的稳定性和性能。

## 编码场景错误用法

### packing过程中PixelMap被释放/修改导致崩溃

**错误代码：**

``` TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function wrongPackingExample(pixelMap: image.PixelMap): Promise<void> {
  let imagePacker = image.ImagePacker | null = null;

  try {
    imagePacker = image.createImagePacker();
    let packOpts: image.PackingOption = { format: 'image/jpeg', quality: 95 };
    // 错误：异步pack执行过程中，对pixelMap进行修改。
    pixelMap.crop({x:1, y:1, size: {height:200, width:200}});
    
    // 错误：异步操作没有使用await。
    imagePacker.packToData(pixelMap, packOpts).then((data: ArrayBuffer) => {
      console.info('Pack success');
    }).catch((error: BusinessError) => {
      console.error('Pack failed: ' + error);
    });

  } catch (error) {
    console.error('Pack failed: ' + error);
  } finally {    
    // 错误：异步pack未完成，直接释放PixelMap，触发应用闪退。
    pixelMap?.release();
    imagePacker.release();
  }
}
```

**正确代码：**

``` TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function correctPackingExample(pixelMap: image.PixelMap): Promise<void> {
  let imagePacker = image.ImagePacker | null = null;

  try {
    imagePacker = image.createImagePacker();
    let packOpts: image.PackingOption = { format: 'image/jpeg', quality: 95 };

    // 正确：对PixelMap做裁剪时，必须await等待操作完成。
    await pixelMap.crop({x:1, y:1, size: {height:200, width:200}});
    
    // 正确：使用await等待异步操作完成。
    const data = await imagePacker.packToData(pixelMap, packOpts);
    console.info('Pack success');

  } catch (error) {
    console.error('Pack failed: ' + error)
  } finally {
    pixelMap?.release();
    imagePacker?.release();
  }
}
```

**典型崩溃堆栈示例：**

```
Fault thread info:
Tid: 7877, Name: 0S_FFRT_3_1
 #00 pc 0000000000f529f4 /system/lib64/libskia_canvaskit.z.so(SkARGB32_Shader_Blitten::blitRect(int, int, int, int)+768)(7155ee7097e240b489727ac2b4155793)
 #01 pc 0000000000ff5cc4 /system/lib64/libskia_canvaskit.z.so (SkBlitter(int, int, int, int, unsigned char)+96) (7155ee7097e240b489727ac2b4155793)
 ...
 #13 pc 00000000000f1b04 /system/lib64/platformsdk/libimage_native.z.so（OHOS::Media::DrawImage（bool, OHOS::Medias::AntiALiasingOption const&, SkCanvas&,sk_sp<SkImage>&(+464) (59bc4a53bbdaaae59d3489a422cac0fc)
 #14 pc 00000000000f2118 /system/lib64/platformsdk/libimage_native.z.so（OHOS::Media::PixelMap::DoTranslation(OHOS::Media:TransInfos&, OHOS::Media::AntiAliasingoption const&, bool）+1492)(59bc4a53bbdaaae59d3489a4226ac0fc)
 #15 pc 00000000000f2ef8 /system/lib64/platformsdk/libimage_native.z.so(OHOS::Media::PixelMap::scale(float, float)+192)(59bc4a53bbdaaae59d3489a422cac0fc)
 #16 pc 00000000000e5d0c /system/lib64/platformsdk/libimage_napi.z.so(OHOS::Media::PixelMapNapi::Scale(napi_env__*. napi_calLback_info__*)::$_19::__invoke(napi_env__*.void*)+68)(2685a6f94f433c89e1a68ae797ef8ba4)
 #17 pc 0000000000060728 /system/lib64/platformsdk/libace_napi.z.so(NativeAsyncWork::AsyncWorkCallback(uv_work_s*)+264)(a540b1c0156867802564e8971775356e)
 #18 pc 00000000003/system/lib64/platformsdk/libuv.so(uv__queue_work+48) (1910e9cc3d1caad339bbad0fb1197758)
 ...
 
```

**注意事项：**

1. **异步操作的生命周期管理：** 在调用Image Kit的异步接口（如[`packToData`](../../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtodata13)、[`packToFile`](../../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#packtofile11)、[`createPixelMap`](../../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#createpixelmap7)等）时，必须确保传入的资源对象（如PixelMap、ImageSource）在异步操作完成之前不被释放或修改。

2. **使用await或Promise.then：** 推荐使用`await`等待异步操作完成，或者在`Promise.then()`的回调中释放资源，确保释放时机正确。

3. **页面生命周期管理：** 如果在页面中使用异步图片操作，需要在页面销毁时确保所有异步操作已经完成或取消，避免页面卸载后异步回调访问已销毁的资源。

## 解码场景错误用法

### 多个异步操作共享同一个ImageSource对象

**错误代码：**

``` TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function wrongSharedImageSourceExample(filePath: string, decodingOptions: Array<image.DecodingOptions>): Promise<Array<image.PixelMap>> {
  // 创建一个ImageSource实例。
  const imageSource = image.createImageSource(filePath);
  const pixelMaps: Array<image.PixelMap> = [];

  // 错误：for循环中并发启动多个解码操作，共享同一个ImageSource。
  for (const opts of decodingOptions) {
    imageSource.createPixelMap(opts).then((pixelMap: image.PixelMap) => {
      pixelMaps.push(pixelMap);
      console.info('PixelMap created');
    }).catch((error: BusinessError) => {
      console.error('Create pixelMap failed: ' + error);
    });
  }

  // 错误：立即释放ImageSource，此时异步操作可能还在执行。
  imageSource.release();
  return pixelMaps;
}
```

**正确代码：**

``` TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function correctSharedImageSourceExample(filePath: string): Promise<void> {
  // 创建一个ImageSource实例。
  const imageSource = image.createImageSource(filePath);

  try {
    // 正确：按顺序执行异步操作，避免并发访问。
    const imageInfo = await imageSource.getImageInfo();
    console.info(`Image info: width=${imageInfo.size.width}, height=${imageInfo.size.height}`);

    const pixelMap1 = await imageSource.createPixelMap({ editable: true });
    console.info('First pixelMap created');

    const pixelMap2 = await imageSource.createPixelMap({ editable: false });
    console.info('Second pixelMap created');

    // 使用完成后释放资源。
    pixelMap1.release();
    pixelMap2.release();
  } catch (error) {
    console.error('Operation failed: ' + error);
  }

  // 所有操作完成后，安全地释放ImageSource。
  imageSource.release();
}
```

**问题堆栈：**

```
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
```

**注意事项：**

1. **避免并发访问：** 不要对同一个ImageSource实例并发执行多个异步操作，推荐按顺序执行，确保一个操作完成后再执行下一个操作。

2. **资源生命周期：** ImageSource的生命周期应该覆盖所有使用它的异步操作，只有在确认所有异步操作都完成后才能释放。

3. **性能考虑：** 虽然顺序执行可能会降低并发性能，但可以避免竞态条件和崩溃问题。如果确实需要并发处理，应该创建多个独立的ImageSource实例。
