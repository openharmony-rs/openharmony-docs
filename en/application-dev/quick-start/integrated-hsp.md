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
Multiple applications in a group can use the same dynamic shared package. To reduce development costs and share code and resources, multiple applications can share one infrastructure HSP (integrated HSP).

## Constraints
- The integrated HSP is only available for the [stage model](application-package-structure-stage.md).
- Only integrated HSP of API version 12 or later is supported. You should set the **useNormalizedOHMUrl** field to **true** in the project-level [build-profile.json5](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile-app) file.

## Development Instructions
1. Project configuration for creators: Set the **useNormalizedOHMUrl** field to **true** in the project-level **build-profile.json5** file to configure the integrated HSP.

    ```json
    // created_party_project/build-profile.json5
    {
      "app": {
        "products": [
          {
            "name": "default",
            "signingConfig": "default",
            "compatibleSdkVersion": "5.0.0(12)",
            "runtimeOS": "HarmonyOS",
            "buildOption": {
              "strictMode": {
                "useNormalizedOHMUrl": true
              }
            }
            // ...
          }
        ]
        // ...
      }
    }
    ```
2. Module configuration for creators: Set the **integratedHsp** field to **true** in the module-level [build-profile.json5](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile) file to specify an HSP module to be built as the integrated HSP module.

    ```json
    // created_party_project/library/build-profile.json5
    {
      "apiType": "stageMode",
      "buildOption": {
        "arkOptions": {
          "integratedHsp": true
        }
      }
    }
    ```

3. Packaging configuration for creators (.tgz package)

    (1) Configure project signature information. For details, see [Configuring a Debug Signature](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-signing).

    (2) Configure the release mode.

    ![](./figures/ide-release-setting.png)

    (3) Select the **library** directory and choose **Build** > **Make Module 'library'**.

4. Directory creation and file copying for users: Create a **libs** directory in the **entry** directory and copy the .tgz file to the created directory.

5. Project dependency configuration for users: Add dependencies to the **oh-package.json5** configuration file in the main module.

    ```json
    // user_project/entry/oh-package.json5
      "dependencies": {
        "hsp": "./libs/library-default.tgz"
      }
    ```

6. Project configuration for users: Set **useNormalizedOHMUrl** to **true** in the project-level **build-profile.json5** file.
    ```json
    // user_project/build-profile.json5
    {
      "app": {
        "products": [
          {
            "name": "default",
            "signingConfig": "default",
            "compatibleSdkVersion": "5.0.0(12)",
            "runtimeOS": "HarmonyOS",
            "buildOption": {
              "strictMode": {
                "useNormalizedOHMUrl": true
              }
            }
          }
        ]
      }
    }
    ```
    > **NOTE**
    > Before installing and running an application, the user must configure the project signature information. For details, see [Configuring a Debug Signature](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-signing).
