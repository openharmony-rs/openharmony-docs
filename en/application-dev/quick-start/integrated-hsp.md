# Integrated HSP
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

The integrated HSP is an intermediate build product of the intra-application HSP. It aims to solve the strong coupling between the bundle name and signature of the user.
> **NOTE**
>
> The HSP can be used only by projects with the same bundle name, but the integrated HSP can be used by projects with different bundle names.
>
> When using the integrated HSP, the user needs to re-sign the integrated HSP with the signature file and install the re-signed integrated HSP first.

## Use Scenario

If multiple applications share the same basic capability, such as a logging module, they can share a single logging module to save development costs and enable code and resource sharing. In this case, the in-application HSP can be used to provide the capabilities. Due to the limitations of the in-application HSP, each application needs to adjust its bundle name and re-sign the HSP with its own signature to build a new HSP for the current application. This means that for each additional application, the bundle name adjustment and re-signing operations must be performed, resulting in a cumbersome signature and packaging process.
With the integrated HSP, the bundle name adjustment and re-signing are automatically handled during the DevEco Studio compilation process. You do not need to concern yourself with repeated signing operations and can focus on function development.

## Constraints
- The integrated HSP is only available for the [stage model](application-package-structure-stage.md).
- The integrated HSP is supported since API version 12.
- The integrated HSP must use the standardized OHMUrl format. You need to set the **useNormalizedOHMUrl** field under [strictMode](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile-app#section13181758123312) to **true** in the project-level [build-profile.json5 file](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile-app).

## Development Instructions

### Configuring the Integrated HSP

1. Project configuration: Set **useNormalizedOHMUrl** to **true** in the project-level **build-profile.json5** file.

    <!-- @[integrated_hsp_002](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/IntegratedHsp/build-profile.json5) -->
    
    ``` JSON5
    {
      "app": {
        "signingConfigs": [
        ],
        "products": [
          {
            "name": "default",
            "signingConfig": "default",
            "targetSdkVersion": "5.1.1(19)",
            "compatibleSdkVersion": "5.1.1(19)",
            "runtimeOS": "HarmonyOS",
            "buildOption": {
              "strictMode": {
                // ...
                "useNormalizedOHMUrl": true,
              }
            }
          }
        ],
        // ...
      },
      // ...
    }
    ```

2. Module configuration: Set **integratedHsp** to **true** in the module-level [build-profile.json5 file](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile) to specify the built HSP module as the integrated HSP.

    <!-- @[integrated_hsp_001](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/IntegratedHsp/library/build-profile.json5) -->
    
    ``` JSON5
    // library/build-profile.json5
    {
      "apiType": "stageMode",
      // ...
      "buildOptionSet": [
        {
          // ...
          "arkOptions": {
            "integratedHsp": true,
            // ...
          },
        },
      ],
      // ...
    }
    ```


3. Package the configuration (.tgz package).

    (1) Configure project signature information. For details, see [Configuring a Debug Signature](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-signing).

    (2) Configure the release mode.

    ![](./figures/ide-release-setting.png)

    (3) Select the **library** directory and choose **Build** > **Make Module 'library'**.

### Integrating the HSP

1. Directory creation and file copying: Create a **libs** directory under the **entry** directory and copy the .tgz package to the created directory.

2. Project dependency configuration: Add dependencies to the **oh-package.json5** configuration file of the main module of the user.

    <!-- @[integrated_hsp_003](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/IntegratedHsp/entry/oh-package.json5) -->
    
    ``` JSON5
    "dependencies": {
      "library": "file:./libs/library-default.tgz"
    },
    ```

3. Project configuration: Set **useNormalizedOHMUrl** to **true** in the project-level **build-profile.json5** file.

    <!-- @[integrated_hsp_002](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/IntegratedHsp/build-profile.json5)  -->
    
    ``` JSON5
    {
      "app": {
        "signingConfigs": [
        ],
        "products": [
          {
            "name": "default",
            "signingConfig": "default",
            "targetSdkVersion": "5.1.1(19)",
            "compatibleSdkVersion": "5.1.1(19)",
            "runtimeOS": "HarmonyOS",
            "buildOption": {
              "strictMode": {
                // ...
                "useNormalizedOHMUrl": true,
              }
            }
          }
        ],
        // ...
      },
      // ...
    }
    ```

4. Configure the signature.

    Before installing and running an application, the user must configure the project signature information. For details, see [Configuring a Debug Signature](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-signing).

5. [Install and run](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-run-device).
