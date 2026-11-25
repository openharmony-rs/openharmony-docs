# Identifying Sensitive Content
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @Yuan_bys-->
<!--Designer: @zhengdu_628-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=5f1a7feb50fd3026ea051af48897cc5b4ef740f8 translatedAt=2026-11-20T09:40:02.820Z pushedAt=2026-11-23T08:05:13.558Z nl=2 -->

 
## When to Use
 
Data Protection Kit provides applications with the capability to identify whether a file contains sensitive content, allowing applications to determine whether a file is sensitive and then apply further control over it.

## Constraints

1. File formats supported for identifying sensitive content: txt, doc, docx, xls, xlsx, ppt, pptx.
2. A file to be identified can be up to 80 MB.
<!--RP1--><!--RP1End-->
 
## Development Procedure
 
1. Import the module. 
    <!-- @[dlp_include_identifySensitiveContent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    import { identifySensitiveContent } from '@kit.DataProtectionKit';
    ```
 
2. Identify sensitive content in a specified file based on the configured policies.
 
    2.1 Request the permission: `ohos.permission.ENTERPRISE_DATA_IDENTIFY_FILE`.
 
    2.2 Set the physical path of the file to be identified and the policy array used to identify sensitive content.
 
    2.3 Call [identifySensitiveContent.scanFile](../../reference/apis-data-protection-kit/js-apis-identifySensitiveContent.md#identifysensitivecontentscanfile), which identifies sensitive content in the specified file based on the configured policies and returns an array of identification results, including the matched sensitive labels, matched content, and match counts.
 
    <!-- @[dlp_scanSensitiveInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/DataProtectionKit/DLP/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    scanSensitiveInfo() {
      let filepath = this.uri;
      let policies: identifySensitiveContent.Policy[] = [
        { 'sensitiveLabel': '1', 'keywords': [], 'regex': '' }
      ];
      if (canIUse('SystemCapability.Security.DataLossPrevention')) {
        try {
          identifySensitiveContent.scanFile(filepath, policies).then(records => {
            console.info('scanFile finish');
            this.result = 'scanFile finish';
            hilog.info(HILOG_DLP_DOMAIN, HILOG_TAG, 'scanFile finish');
          }).catch((err: Error) => {
            console.error('error message', err.message);
            this.result = 'error message' + err.message;
            hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
          })
        } catch (err) {
          console.error('error message', err.message);
          this.result = 'error message' + err.message;
          hilog.error(HILOG_DLP_DOMAIN, HILOG_TAG, 'error message' + err.message);
        }
      }
    }
    ```
 
 
 
## FAQs
 
### Sensitive Content Scan Failure
**Symptom**: An error is reported when calling `scanFile` to scan sensitive content.
 
**Solution**:
- Confirm whether the file path is correct, for example, whether the path exists and whether the path is a physical path.
- Confirm whether the policy configuration format is correct, for example, whether the regular expression is correct and whether the policy content length exceeds the upper limit.