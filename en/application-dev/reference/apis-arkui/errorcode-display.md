# Display Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 1400001 Invalid Display or Screen
**Error Message**<br>
Invalid display or screen.

**Description**<br>
This error code is reported when an invalid display, including a virtual screen, is operated.

**Possible Causes**<br>
1. The virtual screen has not been created.
2. The virtual screen has been destroyed.

**Solution**<br>
1. Before operating the virtual screen, check whether the virtual screen has been created.
2. Check whether the virtual screen has been destroyed.

<!--Del-->
## 1400002 Unauthorized Operation
**Error Message**<br>
Unauthorized operation.

**Description**<br>
This error code is reported when the API does not have the required permissions to operate an object.

**Possible Causes**<br>
The creator and destroyer of the virtual screen are different.

**Solution**<br>
Check whether unauthorized operations are performed on the object of another process. If yes, delete the operations.
<!--DelEnd-->

## 1400003 Abnormal Display Manager Service
**Error Message**<br>
This display manager service works abnormally.

**Description**<br>
This error code is reported when the display manager service is abnormal.

**Possible Causes**<br>
1. The display manager service is not started normally.
2. The bottom-layer graphics synthesis and rendering are abnormal.

**Solution**<br>
Try again later or restart the device.

## 1400004 Parameter Error
**Error Message**<br>
Parameter error. 

**Description**<br>
This error code is reported when an input parameter is incorrect.

**Possible Causes**<br>
The parameter value is out of range.

**Solution**<br>
Correct the parameters.
