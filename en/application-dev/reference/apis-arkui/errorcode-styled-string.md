# Styled String Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=08942777370a0b90b1f82affd44908847b9279aa translatedAt=2026-08-29T09:26:04.479Z pushedAt=2026-08-31T07:07:55.702Z -->

The styled string error codes define the error messages that may occur during operations such as conversion, decoding, and serialization of styled strings, along with the corresponding handling suggestions, helping you quickly locate and resolve styled string related issues.

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 170001 Conversion Error

**Error Message**

Convert Error.

**Description**

This error code is reported when the **fromHtml** API fails to convert the input string into a styled string.

**Possible Causes**

The provided string is empty or does not comply with the HTML format.

**Solution**

1. Check whether the input string is empty. If yes, pass a valid non-empty string.
2. Check whether the string complies with the HTML format. If no, change it to a string that complies with the HTML format and call the API again.

<!--Del-->
## 170002 Styled String Decoding Error

**Error Message**

Styled string decode error.

**Description**

This error code is reported when the **unmarshalling** API fails to deserialize the input bytes into a styled string.

**Possible Causes**

The input bytes do not comply with the format requirements for styled string serialization.

**Solution**

N/A
<!--DelEnd-->

## 180101 Invalid Styled String

**Error Message**

invalid styled string.

**Description**

This error code is reported when the styled string object in **ArkUI_StyledString_Descriptor** is empty in the styled string serialization C API.

**Possible Causes**

The styled string object passed in the parameter is empty.

**Solution**

1. Check whether the styled string object in **ArkUI_StyledString_Descriptor** has been correctly initialized.
2. Ensure that the styled string object is not set to empty when calling the related API.