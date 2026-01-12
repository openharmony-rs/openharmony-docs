# Configuring the Application Shared Directory
<!--Kit: Core File Kit-->
<!--Subsystem: Security-->
<!--Owner: @renzehua-->
<!--Designer: @renzehua; @huangjieliang; @zhanganxiang-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

From API version 23, shared directory configuration is supported. In the [application file sharing](share-app-file.md) scenario, you can configure the shared directory scope to prevent sensitive data disclosure.

## How to Develop

1. Add the **shareFiles** tag to the **module** tag in the application module-level configuration file [src/main/module.json5](../quick-start/module-configuration-file.md) to restrict permissions for sandbox shared directories. If no shared directory is configured, the application is allowed to share files in its own sandbox by default.

   **shareFiles tag**

   ``` JSON5
   {
     "module": {
       // ...
       "shareFiles": "$profile:share_files", // Resource configuration, which points to the configuration file share_files.json defined in the profile.
       // ...
     }
   }
   ```

2. Define the configuration file **share_files.json** under **resources/base/profile** in the development view to specify the permission information for all shared paths of the current module.

   The file name **share_files** can be changed to any valid file name, but must be the same as the file name configured in the **shareFiles** tag.

   **Description of the share_files tag**

   | Property| Description| Data Type| Mandatory|
   | -------- | -------- | -------- | -------- |
   | scopes | Sharing scope. For details, see the description of the **scopes** tag.| Object array| No|

   **Description of the scopes tag**

   | Property| Description| Data Type| Mandatory|
   | -------- | -------- | -------- | -------- |
   | path | Shared path, which defaults to [/el2](share-app-file.md#shareable-application-directories). Its value must be unique. The options are as follows:<br>- `/base/files`<br>- `/base/preferences`<br>- `/base/haps` | string | Mandatory when **scopes** exists.|
   | permission | Shared path permission. The options are as follows:<br>- `r`: read-only.<br>- `r+w`: read and write.| string | Mandatory when **scopes** exists.|

   Example of **share_files.json**:

   ``` json
   {
     "share_files": {
       "scopes": [
         {
           "path": "/base/files",
           "permission": "r+w"
         }
       ]
     }
   }
   ```
