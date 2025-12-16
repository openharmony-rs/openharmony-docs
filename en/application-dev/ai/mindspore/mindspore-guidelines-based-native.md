# Using MindSpore Lite for Image Classification (C/C++)

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--Designer: @zhuguodong8; @jjfeing-->
<!--Tester: @principal87-->
<!--Adviser: @ge-yafang-->

## When to Use

You can use [MindSpore](../../reference/apis-mindspore-lite-kit/capi-mindspore.md) to quickly deploy AI algorithms into your application to perform AI model inference for image classification.

Image classification can be used to recognize objects in images and is widely used in areas such as medical image analysis, auto driving, e-commerce, and facial recognition.

## Basic Concepts

- N-API: a set of native APIs used to build ArkTS components. N-APIs can be used to encapsulate C/C++ libraries into ArkTS modules.

## Development Process

1. Select an image classification model.
2. Use the MindSpore Lite inference model on the device to classify the selected images.

## How to Develop

The following uses inference on an image in the album as an example to describe how to use MindSpore Lite to implement image classification.

### Selecting a Model

This sample application uses [mobilenetv2.ms](https://download.mindspore.cn/model_zoo/official/lite/mobilenetv2_openimage_lite/1.5/mobilenetv2.ms) as the image classification model. The model file is available in the **entry/src/main/resources/rawfile** project directory.

If you have other pre-trained models for image classification, convert the original model into the .ms format by referring to [Using MindSpore Lite for Model Conversion](mindspore-lite-converter-guidelines.md).

### Writing Inference Code

In **entry/src/main/cpp/mslite_napi.cpp**, call [MindSpore](../../reference/apis-mindspore-lite-kit/capi-mindspore.md) to implement on-device inference. The operation process is as follows:

1. Include the corresponding header file.

   <!-- @[napi_image_classification_headers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->
   
   ```c++
   #include <iostream>
   #include <sstream>
   #include <cstdlib>
   #include <hilog/log.h>
   #include <rawfile/raw_file_manager.h>
   #include <mindspore/types.h>
   #include <mindspore/model.h>
   #include <mindspore/context.h>
   #include <mindspore/status.h>
   #include <mindspore/tensor.h>
   #include "napi/native_api.h"
   ```

2. Read the model file.

   <!-- @[napi_image_classification_log](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->

   ```c++
   #define LOGI(...) ((void)OH_LOG_Print(LOG_APP, LOG_INFO, LOG_DOMAIN, "[MSLiteNapi]", __VA_ARGS__))
   #define LOGD(...) ((void)OH_LOG_Print(LOG_APP, LOG_DEBUG, LOG_DOMAIN, "[MSLiteNapi]", __VA_ARGS__))
   #define LOGW(...) ((void)OH_LOG_Print(LOG_APP, LOG_WARN, LOG_DOMAIN, "[MSLiteNapi]", __VA_ARGS__))
   #define LOGE(...) ((void)OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_DOMAIN, "[MSLiteNapi]", __VA_ARGS__))
   ```

   <!-- @[napi_image_classification_ReadModelFile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->

   ```c++
   void *ReadModelFile(NativeResourceManager *nativeResourceManager, const std::string &modelName, size_t *modelSize)
   {
       auto rawFile = OH_ResourceManager_OpenRawFile(nativeResourceManager, modelName.c_str());
       if (rawFile == nullptr) {
           LOGE("MS_LITE_ERR: Open model file failed");
           OH_ResourceManager_CloseRawFile(rawFile);
           return nullptr;
       }
       long fileSize = OH_ResourceManager_GetRawFileSize(rawFile);
       if (fileSize <= 0) {
           LOGE("MS_LITE_ERR: FileSize not correct");
       }
       void *modelBuffer = malloc(fileSize);
       if (modelBuffer == nullptr) {
           LOGE("MS_LITE_ERR: malloc failed");
       }
       int ret = OH_ResourceManager_ReadRawFile(rawFile, modelBuffer, fileSize);
       if (ret == 0) {
           LOGE("MS_LITE_ERR: OH_ResourceManager_ReadRawFile failed");
           OH_ResourceManager_CloseRawFile(rawFile);
           return nullptr;
       }
       OH_ResourceManager_CloseRawFile(rawFile);
       *modelSize = fileSize;
       return modelBuffer;
   }
   ```

3. Create a context, set parameters such as the number of threads and device type, and load the model. The sample model does not support NNRt inference.

   <!-- @[napi_image_classification_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->

   ```c++
   void DestroyModelBuffer(void **buffer)
   {
       if (buffer == nullptr) {
           return;
       }
       free(*buffer);
       *buffer = nullptr;
   }
   
   OH_AI_ContextHandle CreateMSLiteContext(void *modelBuffer)
   {
       // Set executing context for model.
       auto context = OH_AI_ContextCreate();
       if (context == nullptr) {
           DestroyModelBuffer(&modelBuffer);
           LOGE("MS_LITE_ERR: Create MSLite context failed.\n");
           return nullptr;
       }
       // The OH_AI_DeviceInfoCreate(OH_AI_DEVICETYPE_NNRT) option is not supported.
       auto cpu_device_info = OH_AI_DeviceInfoCreate(OH_AI_DEVICETYPE_CPU);
   
       OH_AI_DeviceInfoSetEnableFP16(cpu_device_info, true);
       OH_AI_ContextAddDeviceInfo(context, cpu_device_info);
       
       LOGI("MS_LITE_LOG: Build MSLite context success.\n");
       return context;
   }
   
   OH_AI_ModelHandle CreateMSLiteModel(void *modelBuffer, size_t modelSize, OH_AI_ContextHandle context)
   {
       // Create model
       auto model = OH_AI_ModelCreate();
       if (model == nullptr) {
           DestroyModelBuffer(&modelBuffer);
           LOGE("MS_LITE_ERR: Allocate MSLite Model failed.\n");
           return nullptr;
       }
   
       // Build model object
       auto build_ret = OH_AI_ModelBuild(model, modelBuffer, modelSize, OH_AI_MODELTYPE_MINDIR, context);
       DestroyModelBuffer(&modelBuffer);
       if (build_ret != OH_AI_STATUS_SUCCESS) {
           OH_AI_ModelDestroy(&model);
           LOGE("MS_LITE_ERR: Build MSLite model failed.\n");
           return nullptr;
       }
       LOGI("MS_LITE_LOG: Build MSLite model success.\n");
       return model;
   }
   ```

4. Set the model input data and perform model inference.

   <!-- @[napi_image_classification_print_num](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->

   ```c++
   constexpr int K_NUM_PRINT_OF_OUT_DATA = 20;
   ```

   <!-- @[napi_image_classification_FillInputTensor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->

   ```c++
   // Set the model input data.
   int FillInputTensor(OH_AI_TensorHandle input, std::vector<float> input_data)
   {
       if (OH_AI_TensorGetDataType(input) == OH_AI_DATATYPE_NUMBERTYPE_FLOAT32) {
           float *data = (float *)OH_AI_TensorGetMutableData(input);
           for (size_t i = 0; i < OH_AI_TensorGetElementNum(input); i++) {
               data[i] = input_data[i];
           }
           return OH_AI_STATUS_SUCCESS;
       } else {
           return OH_AI_STATUS_LITE_ERROR;
       }
   }
   ```

   <!-- @[napi_image_classification_RunMSLiteModel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->

   ```c++
   // Execute model inference.
   int RunMSLiteModel(OH_AI_ModelHandle model, std::vector<float> input_data)
   {
       // Set input data for model.
       auto inputs = OH_AI_ModelGetInputs(model);
       auto ret = FillInputTensor(inputs.handle_list[0], input_data);
       if (ret != OH_AI_STATUS_SUCCESS) {
           LOGE("MS_LITE_ERR: RunMSLiteModel set input error.\n");
           return OH_AI_STATUS_LITE_ERROR;
       }
   
       // Get model output.
       auto outputs = OH_AI_ModelGetOutputs(model);
   
       // Predict model.
       auto predict_ret = OH_AI_ModelPredict(model, inputs, &outputs, nullptr, nullptr);
       if (predict_ret != OH_AI_STATUS_SUCCESS) {
           LOGE("MS_LITE_ERR: MSLite Predict error.\n");
           return OH_AI_STATUS_LITE_ERROR;
       }
       LOGI("MS_LITE_LOG: Run MSLite model Predict success.\n");
   
       // Print output tensor data.
       LOGI("MS_LITE_LOG: Get model outputs:\n");
       for (size_t i = 0; i < outputs.handle_num; i++) {
           auto tensor = outputs.handle_list[i];
           LOGI("MS_LITE_LOG: - Tensor %{public}d name is: %{public}s.\n", static_cast<int>(i),
                OH_AI_TensorGetName(tensor));
           LOGI("MS_LITE_LOG: - Tensor %{public}d size is: %{public}d.\n", static_cast<int>(i),
                (int)OH_AI_TensorGetDataSize(tensor));
           LOGI("MS_LITE_LOG: - Tensor data is:\n");
           auto out_data = reinterpret_cast<const float *>(OH_AI_TensorGetData(tensor));
           std::stringstream outStr;
           for (int i = 0; (i < OH_AI_TensorGetElementNum(tensor)) && (i <= K_NUM_PRINT_OF_OUT_DATA); i++) {
               outStr << out_data[i] << " ";
           }
           LOGI("MS_LITE_LOG: %{public}s", outStr.str().c_str());
       }
       return OH_AI_STATUS_SUCCESS;
   }
   ```

5. Implement a complete model inference process.

   <!-- @[napi_image_classification_RunDemo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/mslite_napi.cpp) -->

   ```c++
   static napi_value RunDemo(napi_env env, napi_callback_info info)
   {
       // run demo
       napi_value error_ret;
       napi_create_int32(env, -1, &error_ret);
       // Process the input data.
       size_t argc = 2;
       napi_value argv[2] = {nullptr};
       napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);
       bool isArray = false;
       napi_is_array(env, argv[0], &isArray);
       uint32_t length = 0;
       // Obtain the length of the array.
       napi_get_array_length(env, argv[0], &length);
       LOGI("MS_LITE_LOG: argv array length = %{public}d", length);
       std::vector<float> input_data;
       double param = 0;
       for (int i = 0; i < length; i++) {
           napi_value value;
           napi_get_element(env, argv[0], i, &value);
           napi_get_value_double(env, value, &param);
           input_data.push_back(static_cast<float>(param));
       }
       std::stringstream outstr;
       for (int i = 0; i < K_NUM_PRINT_OF_OUT_DATA; i++) {
           outstr << input_data[i] << " ";
       }
       LOGI("MS_LITE_LOG: input_data = %{public}s", outstr.str().c_str());
       // Read model file
       const std::string modelName = "mobilenetv2.ms";
       LOGI("MS_LITE_LOG: Run model: %{public}s", modelName.c_str());
       size_t modelSize;
       auto resourcesManager = OH_ResourceManager_InitNativeResourceManager(env, argv[1]);
       auto modelBuffer = ReadModelFile(resourcesManager, modelName, &modelSize);
       if (modelBuffer == nullptr) {
           LOGE("MS_LITE_ERR: Read model failed");
           return error_ret;
       }
       LOGI("MS_LITE_LOG: Read model file success");
       
       auto context = CreateMSLiteContext(modelBuffer);
       if (context == nullptr) {
           LOGE("MS_LITE_ERR: MSLiteFwk Build context failed.\n");
           return error_ret;
       }
       auto model = CreateMSLiteModel(modelBuffer, modelSize, context);
       if (model == nullptr) {
           OH_AI_ContextDestroy(&context);
           LOGE("MS_LITE_ERR: MSLiteFwk Build model failed.\n");
           return error_ret;
       }
       int ret = RunMSLiteModel(model, input_data);
       if (ret != OH_AI_STATUS_SUCCESS) {
           OH_AI_ModelDestroy(&model);
           OH_AI_ContextDestroy(&context);
           LOGE("MS_LITE_ERR: RunMSLiteModel failed.\n");
           return error_ret;
       }
       napi_value out_data;
       napi_create_array(env, &out_data);
       auto outputs = OH_AI_ModelGetOutputs(model);
       OH_AI_TensorHandle output_0 = outputs.handle_list[0];
       float *output0Data = reinterpret_cast<float *>(OH_AI_TensorGetMutableData(output_0));
       for (size_t i = 0; i < OH_AI_TensorGetElementNum(output_0); i++) {
           napi_value element;
           napi_create_double(env, static_cast<double>(output0Data[i]), &element);
           napi_set_element(env, out_data, i, element);
       }
       OH_AI_ModelDestroy(&model);
       OH_AI_ContextDestroy(&context);
       LOGI("MS_LITE_LOG: Exit runDemo()");
       return out_data;
   }
   ```

6. Write the **CMake** script to link the MindSpore Lite dynamic library.

   ```cmake
   # the minimum version of CMake.
   cmake_minimum_required(VERSION 3.4.1)
   project(MindSporeLiteCDemo)
   
   set(NATIVERENDER_PATH ${CMAKE_CURRENT_SOURCE_DIR})
   
   if(DEFINED PACKAGE_FIND_FILE)
       include(${PACKAGE_FIND_FILE})
   endif()
   
   include_directories(${NATIVERENDER_PATH}
                       ${NATIVERENDER_PATH}/include)
   
   add_library(entry SHARED mslite_napi.cpp)
   target_link_libraries(entry PUBLIC mindspore_lite_ndk)
   target_link_libraries(entry PUBLIC hilog_ndk.z)
   target_link_libraries(entry PUBLIC rawfile.z)
   target_link_libraries(entry PUBLIC ace_napi.z)
   ```

### Use N-APIs to encapsulate the C++ dynamic library into an ArkTS module.

1. In **entry/src/main/cpp/types/libentry/Index.d.ts**, define the ArkTS API **runDemo ()**. The content is as follows:

   <!-- @[index_image_classification_runDemo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/cpp/types/libentry/index.d.ts) -->
   
   ```typescript
   export const runDemo: (a: number[], b:Object) => Array<number>;
   ```

2. In the **oh-package.json5** file, associate the API with the .so file to form a complete ArkTS module.

   ```json
   {
     "name": "libentry.so",
     "types": "./Index.d.ts",
     "version": "1.0.0",
     "description": "MindSpore Lite inference module"
   }
   ```

### Implementing Image Input and Preprocessing and Performing Inference

1. Call [@ohos.file.picker](../../reference/apis-core-file-kit/js-apis-file-picker.md) to pick up the desired image in the album.
2. Based on the input image size, call [[@ohos.multimedia.image](../../reference/apis-image-kit/arkts-apis-image.md) and [@ohos.file.fs](../../reference/apis-core-file-kit/js-apis-file-fs.md) to perform operations such as cropping the image, obtaining the image buffer, and standardizing the image.
3. In **entry/src/main/ets/pages/Index.ets**, call the encapsulated ArkTS module to process the inference result.

<!-- @[index_image_classification](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo/entry/src/main/ets/pages/Index.ets) -->

```typescript
// Index.ets
import msliteNapi from 'libentry.so';
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { fileIo } from '@kit.CoreFileKit';
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'MindSporeLite';
const PERMISSIONS: Permissions[] = ['ohos.permission.READ_IMAGEVIDEO'];

@Entry
@Component
struct Index {
  @State message: string = 'MindSporeLite C Demo';
  @State modelName: string = 'mobilenetv2.ms';
  @State modelInputHeight: number = 224;
  @State modelInputWidth: number = 224;
  @State uris: Array<string> = [];
  @State max: number = 0;
  @State maxIndex: number = 0;
  @State maxArray: Array<number> = [];
  @State maxIndexArray: Array<number> = [];

  build() {
    Row() {
      Column() {
        Text(this.message)
        Button() {
          Text('photo')
            .fontSize(30)
            .fontWeight(FontWeight.Bold)
        }
        .onClick(() => {
          let resMgr = this.getUIContext()?.getHostContext()?.getApplicationContext().resourceManager;
          if (resMgr === null || resMgr === undefined){
            hilog.error(0xFF00, TAG, '%{public}s', `MS_LITE_ERR: get resMgr failed.`);
            return
          }

          // Obtain images in an album.
          // 1. Create an image picker instance.
          let photoSelectOptions = new photoAccessHelper.PhotoSelectOptions();

          // 2. Set the media file type to IMAGE and set the maximum number of media files that can be selected.
          photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
          photoSelectOptions.maxSelectNumber = 1;

          // 3. Create an album picker instance and call select() to open the album page for file selection. After file selection is done, the result set is returned through photoSelectResult.
          let photoPicker = new photoAccessHelper.PhotoViewPicker();
          photoPicker.select(photoSelectOptions,
            async (err: BusinessError, photoSelectResult: photoAccessHelper.PhotoSelectResult) => {
              if (err) {
                hilog.error(0xFF00, TAG, '%{public}s',
                  `MS_LITE_ERR: PhotoViewPicker.select failed with err: ${JSON.stringify(err)}`);
                return;
              }
              hilog.info(0xFF00, TAG, '%{public}s',
                `MS_LITE_LOG: PhotoViewPicker.select successfully, uri: ${JSON.stringify(photoSelectResult)}`);
              this.uris = photoSelectResult.photoUris;
              hilog.info(0xFF00, TAG, '%{public}s', `MS_LITE_LOG: uri: ${this.uris}`);

              // Preprocess the image data.
              try {
                // 1. Based on the specified URI, call fileIo.openSync to open the file to obtain the FD.
                let file = fileIo.openSync(this.uris[0], fileIo.OpenMode.READ_ONLY);
                hilog.info(0xFF00, TAG, '%{public}s', `MS_LITE_LOG: file fd: ${file.fd}`);

                // 2. Based on the FD, call fileIo.readSync to read the data in the file.
                let inputBuffer = new ArrayBuffer(4096000);
                let readLen = fileIo.readSync(file.fd, inputBuffer);
                hilog.info(0xFF00, TAG, '%{public}s',
                  `MS_LITE_LOG: readSync data to file succeed and inputBuffer size is: ${readLen}`);

                // 3. Perform image preprocessing through PixelMap.
                let imageSource = image.createImageSource(file.fd);
                if (imageSource === undefined) {
                  hilog.error(0xFF00, TAG, '%{public}s', `MS_LITE_ERR: createImageSource failed.`);
                  return
                }
                imageSource.createPixelMap({ editable: true }).then((pixelMap) => {
                  pixelMap.getImageInfo().then((info) => {
                    hilog.info(0xFF00, TAG, '%{public}s',
                      `MS_LITE_LOG: info.width = ${info.size.width}`);
                    hilog.info(0xFF00, TAG, '%{public}s',
                      `MS_LITE_LOG: info.height = ${info.size.height}`);

                    // 4. Crop the image based on the input image size and obtain the image buffer readBuffer.
                    pixelMap.scale(256.0 / info.size.width, 256.0 / info.size.height).then(() => {
                      pixelMap.crop({
                        x: 16,
                        y: 16,
                        size: { height: this.modelInputHeight, width: this.modelInputWidth }
                      }).then(async () => {
                        let info = await pixelMap.getImageInfo();
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: crop info.width = ${info.size.width}`);
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: crop info.height = ${info.size.height}`);
                        // Set the size of readBuffer.
                        let readBuffer = new ArrayBuffer(this.modelInputHeight * this.modelInputWidth * 4);
                        await pixelMap.readPixelsToBuffer(readBuffer);
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: Succeeded in reading image pixel data, buffer: ${readBuffer.byteLength}`);
                        // Convert readBuffer to the float32 format, and standardize the image.
                        const imageArr =
                          new Uint8Array(readBuffer.slice(0, this.modelInputHeight * this.modelInputWidth * 4));
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: imageArr length: ${imageArr.length}`);

                        let means = [0.485, 0.456, 0.406];
                        let stds = [0.229, 0.224, 0.225];
                        let float32View = new Float32Array(this.modelInputHeight * this.modelInputWidth * 3);
                        let index = 0;
                        for (let i = 0; i < imageArr.length; i++) {
                          if ((i + 1) % 4 === 0) {
                            float32View[index] = (imageArr[i - 3] / 255.0 - means[0]) / stds[0]; // B
                            float32View[index+1] = (imageArr[i - 2] / 255.0 - means[1]) / stds[1]; // G
                            float32View[index+2] = (imageArr[i - 1] / 255.0 - means[2]) / stds[2]; // R
                            index += 3;
                          }
                        }
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: float32View length: ${float32View.length}`);
                        let printStr = 'float32View data:';
                        for (let i = 0; i < 20; i++) {
                          printStr += ' ' + float32View[i];
                        }
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: float32View data: ${printStr}`);

                        // Call the C++ runDemo.
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: *** Start MSLite Demo ***`);

                        let output: Array<number> = msliteNapi.runDemo(Array.from(float32View), resMgr);
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_WARN: output length = ${output.length}, value = ${output.slice(0, 20)}`);

                        // Obtain the top 5 maximum numbers of categories.
                        this.max = 0;
                        this.maxIndex = 0;
                        this.maxArray = [];
                        this.maxIndexArray = [];
                        let newArray = output.filter(value => value !== this.max);
                        for (let n = 0; n < 5; n++) {
                          this.max = output[0];
                          this.maxIndex = 0;
                          // Obtain the maximum value.
                          for (let m = 0; m < newArray.length; m++) {
                            if (newArray[m] > this.max) {
                              this.max = newArray[m];
                              this.maxIndex = m;
                            }
                          }
                          this.maxArray.push(Math.round(this.max * 10000));
                          this.maxIndexArray.push(this.maxIndex);
                          // Call the array filter function.
                          newArray = newArray.filter(value => value !== this.max);
                        }
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: max: ${this.maxArray}`);
                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: maxIndex: ${this.maxIndexArray}`);

                        hilog.info(0xFF00, TAG, '%{public}s',
                          `MS_LITE_LOG: *** Finished MSLite Demo ***`);
                      }).catch((error: BusinessError) => {
                        hilog.error(0xFF00, TAG, '%{public}s',
                          `MS_LITE_ERR: getRawFileContent promise error is: ${error}`);
                      })
                    })
                    // 5. Close the file.
                    fileIo.closeSync(file);
                  })
                })
              } catch (err) {
                hilog.error(0xFF00, TAG, '%{public}s',
                  `MS_LITE_ERR: uri: open file fd failed. ${err}`);
              }
            })
        })
      }.width('100%')
    }
    .height('100%')
  }
}
```

### Debugging and Verification

1. On DevEco Studio, connect to the device, click **Run entry**, and build your own HAP. 

   ```shell
   Launching com.samples.mindsporelitecdemo
   $ hdc shell aa force-stop com.samples.mindsporelitecdemo
   $ hdc shell mkdir data/local/tmp/xxx
   $ hdc file send C:\Users\xxx\MindSporeLiteCDemo\entry\build\default\outputs\default\entry-default-signed.hap "data/local/tmp/xxx"
   $ hdc shell bm install -p data/local/tmp/xxx
   $ hdc shell rm -rf data/local/tmp/xxx
   $ hdc shell aa start -a EntryAbility -b com.samples.mindsporelitecdemo
   ```

2. Touch the **photo** button on the device screen, select an image, and touch **OK**. The classification result of the selected image is displayed on the device screen. In the log printing result, filter images by the keyword **MS_LITE**. The following information is displayed:

   ```verilog
   08-05 17:15:52.001   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: PhotoViewPicker.select successfully, photoSelectResult uri: {"photoUris":["file://media/Photo/13/IMG_1501955351_012/plant.jpg"]}
   ...
   08-05 17:15:52.627   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: crop info.width = 224
   08-05 17:15:52.627   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: crop info.height = 224
   08-05 17:15:52.628   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: Succeeded in reading image pixel data, buffer: 200704
   08-05 17:15:52.971   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: float32View data: float32View data: 1.2385478019714355 1.308123230934143 1.4722440242767334 1.2385478019714355 1.308123230934143 1.4722440242767334 1.2385478019714355 1.308123230934143 1.4722440242767334 1.2385478019714355 1.308123230934143 1.4722440242767334 1.2385478019714355 1.308123230934143 1.4722440242767334 1.2385478019714355 1.308123230934143 1.4722440242767334 1.2385478019714355 1.308123230934143
   08-05 17:15:52.971   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: *** Start MSLite Demo ***
   08-05 17:15:53.454   4684-4684    A00000/[MSLiteNapi]            pid-4684              I     MS_LITE_LOG: Build MSLite model success.
   08-05 17:15:53.753   4684-4684    A00000/[MSLiteNapi]            pid-4684              I     MS_LITE_LOG: Run MSLite model Predict success.
   08-05 17:15:53.753   4684-4684    A00000/[MSLiteNapi]            pid-4684              I     MS_LITE_LOG: Get model outputs:
   08-05 17:15:53.753   4684-4684    A00000/[MSLiteNapi]            pid-4684              I     MS_LITE_LOG: - Tensor 0 name is: Default/head-MobileNetV2Head/Sigmoid-op466.
   08-05 17:15:53.753   4684-4684    A00000/[MSLiteNapi]            pid-4684              I     MS_LITE_LOG: - Tensor data is:
   08-05 17:15:53.753   4684-4684    A00000/[MSLiteNapi]            pid-4684              I     MS_LITE_LOG: 3.43385e-06 1.40285e-05 9.11969e-07 4.91007e-05 9.50266e-07 3.94537e-07 0.0434676 3.97196e-05 0.00054832 0.000246202 1.576e-05 3.6494e-06 1.23553e-05 0.196977 5.3028e-05 3.29346e-05 4.90475e-07 1.66109e-06 7.03273e-06 8.83677e-07 3.1365e-06
   08-05 17:15:53.781   4684-4684    A03d00/JSAPP                   pid-4684              W     MS_LITE_WARN: output length =  500 ;value =  0.0000034338463592575863,0.000014028532859811094,9.119685273617506e-7,0.000049100715841632336,9.502661555416125e-7,3.945370394831116e-7,0.04346757382154465,0.00003971960904891603,0.0005483203567564487,0.00024620210751891136,0.000015759984307806008,0.0000036493988773145247,0.00001235533181898063,0.1969769448041916,0.000053027983085485175,0.000032934600312728435,4.904751449430478e-7,0.0000016610861166554969,0.000007032729172351537,8.836767619868624e-7
   08-05 17:15:53.831   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: max:9497,7756,1970,435,46
   08-05 17:15:53.831   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: maxIndex:323,46,13,6,349
   08-05 17:15:53.831   4684-4684    A03d00/JSAPP                   pid-4684              I     MS_LITE_LOG: *** Finished MSLite Demo ***
   ```


### Effects

Touch the **photo** button on the device screen, select an image, and touch **OK**. The top 4 categories of the image are displayed below the image.

![stepc1](figures/stepc1.png)           ![step2](figures/step2.png)

![step3](figures/step3.png)         ![stepc4](figures/stepc4.png) 

## Related Samples

The following sample is provided to help you better understand how to develop image classification applications using MindSpore Lite:

- [MindSpore Lite Application Development Based on Native APIs (C/C++) (API 11)] (https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/MindSporeLiteKit/MindSporeLiteCDemo)
