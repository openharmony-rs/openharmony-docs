# IME Tool
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6036c6e8fc50c26cc4c13106c23fcc7ac6fe9cc1 translatedAt=2026-11-03T08:26:27.517Z pushedAt=2026-11-03T08:26:27.517Z nl=1 -->

The IME tool lets you manage system input method applications in developer mode, including enabling, disabling, and switching input methods.

> **NOTE**
>
> The IME tool is supported since API version 20.
> When [Assessment Management](../reference/apis-assessment-kit/js-apis-customization-assessment.md) is enabled, the IME tool cannot switch to another input method using the switch command.

**Environment requirements**<br/>

Before using this tool, obtain the hdc tool and run **hdc shell**.


**How to Use**<br>

hdc shell ime [option] [parameter]

**Commands**
| Option| Parameter      | Description                                                        |
| ---- | ---------- | ------------------------------------------------------------ |
| -u | userId | Specifies the target user ID. The default is the ID of the foreground user on the main screen. This option can be used with other options to manage input methods in a multi-user environment. |
| -e | bundle [-b /-f] | Enables an input method in the specified mode. If neither **-b** nor **-f** is set, the basic access mode (**-b**) is used by default. **-f** indicates the full experience mode.<br>**Note**: This command cannot change the enabled state of the system's preset default input method. |
| -d | bundle | Disables a specified input method.<br>**Note**: The preset default input method cannot be disabled.|
| -s   | bundle     | Switches to a specified input method.<br>**Note**: You are not allowed to switch to another input method when the screen is locked or the password is being entered.|
| -g   | NA         | Obtains the current input method.|
| -l   | NA         | Lists all input methods.|
| -h   | NA         | Displays the help information.|

## Managing Input Methods Using IME Tool

1. Enabling an input method. You can enable a third-party input method in basic access mode or full experience mode.

   ```shell
    # Input: Use an hdc command to enable an input method.
    # Processing: Check if it is an hdc shell command, and call the corresponding system API for managing input methods.
    # Output: The effect is equivalent to a direct API call.
    # Basic access mode
    hdc shell ime -e com.xxx.yyy 
    # Full experience mode
    hdc shell ime -e com.xxx.yyy -f
   ```

2. Disabling an input method. You can disable a third-party input method.

   ```shell
    # Input: Use an hdc command to disable an input method.
    # Processing: Check if it is an hdc shell command, and call the corresponding API for disabling.
    # Output: The effect is equivalent to a direct API call.
    hdc shell ime -d com.xxx.yyy
   ```

3. Switching to a specified input method.

   ```shell
    # Input: Use an hdc command to switch the input method.
    # Processing: Check if it is an hdc shell command, and call the corresponding API for switching.
    # Output: The effect is equivalent to a direct API call.
    hdc shell ime -s com.xxx.yyy
   ```

4. Obtaining the current input method.

   ```shell
    # Input: Use an hdc command to obtain the current input method.
    # Processing: Check if it is an hdc shell command, and call the corresponding API for obtaining.
    # Output: The effect is equivalent to a direct API call.
    hdc shell ime -g
   ```

5. Listing all input methods. The enabling status of the preset default input method is not displayed.

   ```shell
    # Input: Use an hdc command to list all input methods.
    # Processing: Check if it is an hdc shell command, and call the corresponding API for listing.
    # Output: The effect is equivalent to a direct API call.
    hdc shell ime -l
   ```

6. Displaying the help information.

   ```shell
    # Input: Use an hdc command to display the help information.
    # Output: Display the help information.
    hdc shell ime -h
   ```

## Managing Input Methods in a Multi-User Environment

Starting from API version 26.0.0, you can use the **-u** option to specify a target user ID and manage input methods for different users in a multi-user environment.

### Multi-User Command Examples

1. Obtaining the current input method for a specified user.

   ```shell
    # Input: Obtain the current input method for user 100.
    # Processing: Query the current input method for user 100.
    # Output: Display information about the current input method for user 100.
    hdc shell ime -u 100 -g
   ```

2. Switching the input method for a specified user.

   ```shell
    # Input: Switch to the specified input method for user 100.
    # Processing: Switch the input method for user 100.
    # Output: Display the switching result.
    hdc shell ime -u 100 -s com.example.ime
   ```

3. Enabling an input method for a specified user.

   ```shell
    # Input: Enable the specified input method in basic access mode for user 100.
    # Processing: Enable the input method for user 100.
    # Output: Display the result.
    hdc shell ime -u 100 -e com.example.ime

    # Enable full experience mode.
    hdc shell ime -u 100 -e com.example.ime -f
   ```

4. Disabling an input method for a specified user.

   ```shell
    # Input: Disable the specified input method for user 100.
    # Processing: Disable the input method for user 100.
    # Output: Display the result.
    hdc shell ime -u 100 -d com.example.ime
   ```

5. Listing all input methods for a specified user.

   ```shell
    # Input: List all input methods for user 100.
    # Processing: Query all input methods for user 100.
    # Output: Display the list of all input methods for user 100.
    hdc shell ime -u 100 -l
   ```

> **NOTE**
>
> - The **-u** option is optional. If omitted, the command operates on the current user.
> - The user ID must be a non-negative integer.
> - Only applications of user 0 can perform cross-user operations.

<!--no_check-->