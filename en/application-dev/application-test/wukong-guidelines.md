# wukong User Guide
<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @qkfg-->
<!--Designer: @qkfg-->
<!--Tester: @caixincen-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d62a05cd3afbfcc6267bfda8bea80438a42a8ef4 translatedAt=2026-09-17T09:26:56.716Z pushedAt=2026-09-21T11:20:39.265Z -->

## Introduction

wukong is a built-in command line tool that implements application stability test capabilities such as random event injection, component injection, exception capture, report generation, and data traversal of abilities. This tool allows you to conduct stability tests on the system or applications by simulating user behavior. wukong provides three types of testing: random testing, special testing, and focus testing.

In random testing, test inputs are generated randomly. Available features include shell startup, whole application startup, multiple injection modes, random seeds setting, run log printing, and report generation.

Special testing mainly tests the controls of specified applications. Available features include shell startup, sequential traversal and screenshot, sleep/wakeup testing, record and playback, run log printing, and report generation.

In focus testing, specific components are injected. Available features include shell startup, device application startup, multiple injection modes, random seed setting, focus component type setting, component injection times setting, run log printing, and report generation.

## Principles

The following figure shows the wukong component architecture and the responsibilities of sub-modules.

![Alternate text](figures/wukongRandomTestFlow.png)

- Command line parsing: obtains and parses parameters using commands.
- Operating environment management: initializes the overall operating environment of wukong using commands.
- System API management: checks and obtains the specified mgr, and registers the callback function of Faultlogger for the controller and DFX.
- Random event generation: generates a sequence of random numbers using a specified seed through a random function, and creates events based on this sequence.
- Event injection: injects events of supported types to the system. This feature depends on the window, multimodal, and security subsystems.
- Exception capture and processing and report generation: obtains exception information with the DFX subsystem during application running, record log, and generate reports.

## Constraints

1. The wukong tool is built in the system since API version 9.

2. Before running any command, configure the <!--RP1-->[hdc environment](../dfx/hdc.md)<!--RP1End--> and enter the shell mode.
   <!--Del-->
3. In API versions earlier than 9, you need to build the tool and push it to the target device. The procedure is as follows:

   ```bash
   # Build code
   ./build.sh --product-name rk3568 --build-target wukong

   # Push code
   hdc shell mount -o rw,remount /
   hdc file send wukong /
   hdc shell chmod a+x /wukong
   hdc shell mv /wukong /bin/
   ```
   <!--DelEnd-->
## Functions and Commands

| Command          | Description                                          |
| -------------- | ---------------------------------------------- |
| -v/--version | Obtains version information.                            |
| help    | Obtains help information.                            |
| appinfo | Queries the bundle name and the name of the corresponding mainAbility of the app that can be started.|
| special | Runs special testing.                                  |
| exec    | Runs random testing.                                  |
| focus   | Runs focus testing.                                  |

### Running Commands

- Open the shell.

  ```bash
  #If you are testing one device, run **hdc shell**.
  C:\Users>hdc shell
  $
  #If you are testing multiple devices, obtain the SNs first by running **hdc list targets**. Then, enter the shell.
  C:\Users>hdc list targets
  15xxx424axxxx345209d94xxxx8fxx900
  C:\Users>hdc -t 15xxx424axxxx345209d94xxxx8fxx900 shell
  $
  ```

- Obtain the bundle name and ability name of the application.

  ```bash
  $ wukong appinfo
  BundleName:  com.ohos.adminprovisioning
  AbilityName:  com.ohos.adminprovisioning.MainAbility
  BundleName:  com.ohos.callui
  AbilityName:  com.ohos.callui.MainAbility
  ```
- View the help information.

  ```bash
  C:\Users>hdc shell
  $ wukong help        #wukong help menu.
  usage: wukong <command> [<arguments>]
  These are common wukong command list:
    help                       wukong help information
    -v/--version               wukong version
    exec                       run random test
    special                    run special test
    focus                      run focus test
    appinfo                    show all app information
  $ wukong exec -help   #Help menu for wukong random testing.
  usage: wukong exec [<arguments>]
  These are wukong exec arguments list:
    -h, --help                 random test help
    -a, --appswitch            appswitch event percent
    -b, --bundle               the bundle name of allowlist
    -p, --prohibit             the bundle name of blocklist
    -d, --page                 block page list
    -t, --touch                touch event percent
    -c, --count                test count
    -i, --interval             interval
    -s, --seed                 random seed
    -m, --mouse                mouse event percent
    -k, --keyboard             keyboard event percent
    -H, --hardkey              hardkey event percent
    -S, --swap                 swap event percent
    -T, --time                 test time
    -C, --component            component event percent
    -r, --rotate               rotate event percent
    -e, --allow ability        the ability name of allowlist
    -E, --block ability        the ability name of blocklist
    -Y, --blockCompId          the id list of block component
    -y, --blockCompType        the type list of block component
    -I, --screenshot           get screenshot(only in random input)
    -B, --checkBWScreen        black and white screen detection
    -U, --Uri                  set Uri pages
    -x, --Uri-type             set Uri-type
    -K, --knuckle              set percent of knuckle event
    -f, --finger               set the number of fingers and proportions for tests such as swipe and knuckle gesture
    -P, --pinch                set percent of pinch-to-zoom event
    -D, --direction            set the swipe directions and proportions
    -o, --pause                pause swiping for 1 second
    -w, --crown                set percent of watch crown rotation event
    -g, --gestures             set percent of watch gesture recognition events
    -l, --idle                 set percent of watch idle event
    -j, --keypress             set percent of watch physical button press event
    -F, --float                set percent of float and split event
    -W, --browser              set percent of browser operation event
  $ wukong special -help    #Help menu for wukong special testing.
  usage: wukong special [<arguments>]
  These are wukong special arguments list:
    -h, --help                 special test help
    -t, --touch[x,y]           touch event
    -c, --count                total count of test
    -i, --interval             interval
    -S, --swap[option]         swap event
                                option is -s| -e| -b
                                -s, --start: the start point of swap
                                -e, --end: the end point of swap
                                -b, --bilateral: swap go and back
    -k, --spec_insomnia        power on/off event
    -T, --time                 total time of test
    -C, --component            component event
    -p, --screenshot           get screenshot(only in component input)
    -r, --record               record user operation
    -R, --replay               replay user operation
    -u, --uitest               uitest dumpLayout
  ```

## Random Testing

### Commands

| Command           | Description                                | Mandatory| Remarks                                    |
| --------------- | ------------------------------------ | ---- | ---------------------------------------- |
| -h,--help       | Obtains the help information about the test.              | No  |  -                        |
| -c,--count      | Sets the execution count, which conflicts with the total test time -T. Use one of the two.   | No   | Unit count, default value: 10.                       |
| -i,--interval   | Sets the execution interval.                         | No   | Unit: ms, default value: 1500 ms.                       |
| -s,--seed       | Sets the random seed.                        | No  | If the same random seed is set, the same random event sequence is generated.|
| -b,--bundle[bundlename, ......, bundlename]    | Sets allowed bundles for the test. This command conflicts with the **-p** command.| No  | By default, all bundles on the device are allowed. Use commas (,) to separate bundle names.                |
| -p,--prohibit[bundlename, ......, bundlename]  | Sets blocked bundles for the test. This command conflicts with the **-b** command.| No  | By default, no bundle is blocked. Use commas (,) to separate bundle names.                      |
| -d,--page[page, ......, page]                  | Sets blocked pages for the test.| No | By default, the **pages/system** pages are blocked. Use commas (,) to separate page names.|
| -a,--appswitch  | Sets the random application launch test ratio.             | No   | Value range: 0 to 1, default value: 10%.                                  |
| -t,--touch      | Sets the random screen touch test ratio.            | No   | Value range: 0 to 1, default value: 10%.                                  |
| -S,--swap       | Sets the random screen swipe test ratio.             | No   | Value range: 0 to 1, default value: 3%.                                   |
| -m,--mouse      | Sets the random screen mouse test ratio.            | No   | Value range: 0 to 1, default value: 1%.                                   |
| -k,--keyboard   | Sets the random screen keyboard operation test ratio.         | No   | Value range: 0 to 1, default value: 2%.                                   |
| -H,--hardkey    | Sets the random physical key test ratio.              | No   | Value range: 0 to 1, default value: 2%.                                   |
| -r,--rotate     | Sets the random screen rotation test ratio.               | No   | Value range: 0 to 1, default value: 2%.                                   |
| -C, --component | Sets the random control test ratio.                 | No   | Value range: 0 to 1, default value: 70%.                                  |
| -I, --screenshot | Takes a screenshot for the component test.                | No  | - |
| -T,--time       | Sets the total test time, which conflicts with the execution count -c. Use one of the two. | No   | Unit: minutes, default value: 10 minutes.         |
| -e, --allow ability   |  Sets the ability that allows testing.| No| - |
| -E, --block ability   |  Sets the ability that blocks testing.| No| - |
| -Y, --blockCompId     |  Sets the blocked **CompId**.| No| - |
| -y, --blockCompType   |  Sets the blocked **CompType**.| No| - |
| -B, --checkBWScreen   |  Enables black and white screen check.| No| - |
| -U, --Uri        | Sets the URI of the page to be launched by the application. | No | - |
| -x, --UriType    | Sets the URIType (Uniform Resource Identifier type) of the page to be launched by the application. | No | - |
| -K, --knuckle    | Sets the knuckle tap test ratio.       | No | Value range: 0 to 1, default value: 0.|
| -f, --finger     | Sets the number of fingers and ratio involved in the swipe and knuckle tap tests. | No | Supports configuring 1 to 4 fingers. Format: -f <finger count 1,ratio>,<finger count 2,ratio>,<finger count 3,ratio>,<finger count 4,ratio>, for example: -f 1,0.25,2,0.25,3,0.25,4,0.25.|
| -P, --pinch      | Sets the two-finger pinch test ratio.     | No | Value range: 0 to 1, default value: 0.|
| -D, --direction  | Sets the swipe direction and ratio.     | No | Supports configuring four directions: up (u), down (d), left (l), and right (r). Format: -D <direction 1,ratio>,<direction 2,ratio>,<direction 3,ratio>,<direction 4,ratio>, for example: u,0.25,r,0.25,d,0.25,l,0.25.|
| -o, --pause      | Enables pausing during the swipe.    | No | Pausing is not supported if this parameter is omitted. |
| -w, --crown      | Sets the crown operation test ratio.     | No | Supported only on Wearable devices. Value range: 0 to 1, default value: 0.|
| -g, --gestures   | Sets the gesture (such as swipe up, swipe down, swipe left, and swipe right) operation test ratio. | No | Supported only on Wearable devices. Value range: 0 to 1, default value: 0.|
| -l, --idle       | Sets the operation test ratio in the standby state. | No | Supported only on Wearable devices. Value range: 0 to 1, default value: 0.|
| -j, --keypress   | Sets the key (power key and smart window key) operation test ratio. | No | Supported only on Wearable devices. Value range: 0 to 1, default value: 0.|
| -F, --float      | Sets the test ratio for the application split-screen mode and floating window mode. | No | Value range: 0 to 1, default value: 0.|
| -W, --browser    | Sets the browser operation test ratio.     | No | Value range: 0 to 1, default value: 0.|

> **NOTE**
>
> - The test ratio of the preceding parameters indicates the operations in the current test. The sum of the test ratios of all parameters must be less than or equal to 1.
>
> - The -K, -f, -P, -D, -o, -w, -g, -l, -j, -F, and -W parameters are supported since API version 23.

### Samples

- Set 100 event injections.

  ```bash
  $ wukong exec -s 10 -i 1000 -a 0.28 -t 0.72 -c 100
  ```

  The parameters in the command are described as follows.
  | Command          | Value     |Description       |
  | -------------- | -------------- | -------------- |
  | wukong exec | -           | Works as the main command.               |
  | -s     | 10           | Sets the random seed. The seed value is **10**. |
  | -i  | 1000           | Sets the application startup interval to **1000** ms.|
  | -a  | 0.28          | Sets the proportion of the random application startup test to **28%**.   |
  | -t  | 0.72           | Sets the proportion of the random touch test to **72%**.   |
  | -c  | 100           | Sets the number of execution times to **100**.        |

- Specify a page to perform a pressure test.

  ```bash
  > Explicit launch
  > hdc_std shell
  $ wukong exec -b bundlename -e abilityname -U uri

  > Implicit start
  > hdc_std shell
  $ wukong exec -b bundlename -U uri -x uriType
  ```

- Set the ability that allows and blocks testing.
  ```bash
  $ wukong exec -b com.ohos.settings -e com.ohos.settings.MainAbility -E com.ohos.settings.AppInfoAbility
  ```
  >  **NOTE**
  >
  > If **-e** and **-E** are set, you must set **-b** to specify an application.

## Special Testing

### Commands

| Command               | Description                  | Mandatory| Remarks               |
| :------------------ | ---------------------- | ---- | :------------------ |
| -h, --help          | Obtains the help information about the special testing.| No  |  -    |
| -k, --spec_insomnia | Performs the sleep/wakeup special testing.      | No  | -                   |
| -c, --count         | Sets the execution count.           | No   | Unit Count, default value is 10.          |
| -i, --interval      | Sets the execution interval.           | No   | Unit ms, default value is 1500ms.  |
| -S, --swap          | Sets a swipe event for the test.              | No  | -                   |
| -s, --start[x,y]    | Sets the coordinates of the start point of the swipe event.  | No  | The values of coordinates are positive.          |
| -e, --end[x,y]      | Sets the coordinates of the end point of the swipe event.  | No  | The values of coordinates are positive.         |
| -b, --bilateral     | Sets a back and forth swipe event.          | No  | By default, the back and forth swipe event is disabled.     |
| -t, --touch[x,y]    | Sets a touch event for the test.              | No  | -                   |
| -T, --time          | Sets the total test time.         | No   | Unit Minutes, default value is 10 minutes. |
| -C, --component     | Sets the sequential traversal test for components.      | No  | You need to set the name of the test application.|
| -r, --record     | Records user operation.      | No  | You need to specify the recording file.|
| -R, --replay    |  Replays user operation.     | No  | You need to specify the playback file.|
| -p, --screenshot    |  Takes a screenshot for the component test.     | No  | - |

### Samples

```bash
$ wukong special -C [bundlename] -p
```

## Focus Testing

### Commands

| Command           | Description                                | Mandatory| Remarks                                    |
| --------------- | ------------------------------------ | ---- | ---------------------------------------- |
| -n,--numberfocus       | Sets the number of injections for each component.              | No  | Unit: times                |
| -f, --focustypes       | Sets the types of component for the focus testing.              | No  | Use commas (,) to separate the types.                        |
| -h,--help       | Obtains the help information about the test.              | No  |  -                       |
| -c,--count      | Sets the execution count. Conflicts with -T, which sets the execution time. Use one of the two.   | No   | Unit count, default value: 10 times.                       |
| -i,--interval   | Sets the execution interval.                         | No   | Unit ms, default value: 1500 ms.                       |
| -s,--seed       | Sets the random seed.                        | No  | If the same random seed is set, the same random event sequence is generated.|
| -b,--bundle[bundlename, ......, bundlename]    | Sets allowed bundles for the test. This command conflicts with the **-p** command.| No  | By default, all bundles on the device are allowed. Use commas (,) to separate bundle names.                |
| -p,--prohibit[bundlename, ......, bundlename]  | Sets blocked bundles for the test. This command conflicts with the **-b** command.| No  | By default, no bundle is blocked. Use commas (,) to separate bundle names.                      |
| -d,--page[page, ......, page]                  | Sets blocked pages for the test.| No | By default, the **pages/system** pages are blocked. Use commas (,) to separate page names.|
| -a,--appswitch  | Sets the random application launch test ratio.             | No   | Default value: 10%.                                  |
| -t,--touch      | Sets the random screen touch test ratio.            | No   | Default value: 10%.                                  |
| -S,--swap       | Sets the random screen swipe test ratio.             | No   | Default value: 3%.                                   |
| -m,--mouse      | Sets the random screen mouse test ratio.            | No   | Default value: 1%.                                   |
| -k,--keyboard   | Sets the random screen keyboard operation test ratio.         | No   | Default value: 2%.                                   |
| -H,--hardkey    | Sets the random physical key test ratio.              | No   | Default value: 2%.                                   |
| -r,--rotate     | Sets the random screen rotation test ratio.               | No   | Default value: 2%.                                   |
| -C, --component | Sets the random control test ratio.                 | No   | Default value: 70%.                                  |
| -I, --screenshot | Takes a screenshot for the component test.                | No  | - |
| -T,--time       | Sets the total test time. Conflicts with -c, which sets the execution count. Use one of the two. | No   | Unit minutes, default value: 10 minutes.         |
| -e, --allow ability   |  Sets the ability that allows testing.| No| - |
| -E, --block ability   |  Sets the ability that blocks testing.| No| - |
| -Y, --blockCompId     |  Sets the blocked **CompId**.| No| - |
| -y, --blockCompType   |  Sets the blocked **CompType**.| No| - |
| -B, --checkBWScreen   |  Enables black and white screen check.| No| - |

### Samples

```bash
$ wukong focus -s 10 -i 1000 -a 0.28 -t 0.72 -c 100
```

The parameters in the command are described as follows.
| Command          | Value     |Description       |
| -------------- | -------------- | -------------- |
| wukong focus | -           | Works as the main command.               |
| -s     | 10           | Sets the random seed. The seed value is **10**. |
| -i  | 1000           | Sets the application startup interval to **1000** ms.|
| -a  | 0.28          | Sets the proportion of the random application startup test to **28%**.   |
| -t  | 0.72           | Sets the proportion of the random touch test to **72%**.   |
| -c  | 100           | Sets the number of execution times to **100**.        |


## Viewing the Test Result

### Test Result Output Path

After the test commands are executed, the test result is automatically generated. You can obtain the test result in the following directory:

- For DevEco Studio versions earlier than September 22, 2022: **/data/local/wukong/report/xxxxxxxx_xxxxxx/**
- For DevEco Studio versions later than September 22, 2022: **/data/local/tmp/wukong/report/xxxxxxxx_xxxxxx/**

### Test Report Directories

| Type                                | Description              |
| ------------------------------------ | ------------------ |
| exception/                           | Stores exception files generated during the test.|
| screenshot/                          | Stores the screenshots of the test traversal. |
| wukong_report.csv                    | Stores the test report summary.      |
| wukong.log                | Indicates the test operation history.      |

### Viewing Operation Logs

You can run the hdc command to obtain logs to the local host and view the operation history.

```bash
# The path of the wukong.log file is as follows:
/data/local/tmp/wukong/report/xxxxxxxx_xxxxxx/wukong.log

# To view the directory of the wukong test report, run the following command:
$ cd /data/local/tmp/wukong/report/20170805_170053
$ ls
data.js  exception  wukong.log  wukong_report.csv

# Open the shell and run hdc file recv to obtain wukong logs.
C:\Users\xxx>hdc file recv /data/local/tmp/wukong/report/20170805_170053/wukong.log C:\Users\xxx\Desktop\log
[I][2024-01-03 20:08:02] HdcFile::TransferSummary success
FileTransfer finish, Size:76492, File count = 1, time:16ms rate:4780.75kB/s
```

### Test Report Parsing

Contains basic information, event injection statistics, Ability statistics, and exception statistics.

1. Basic Information (Base Info)

    | Field                     | Description              |
    | ------------------------ | ------------------|
    | task status              | Task status. **success** indicates success, and **fail** indicates failure.|
    | task time                | Task execution time. Unit: seconds.|
    | seed                     | Random seed.|
    | task count               | Total number of event injections.|

2. Input Message Statistics

    | Type                            | Description                               |
    | -------------------------------| ---------------------------------- |
    | type                           | Type of event or control injection. For the range of event injection types, see [Random Test Command Parameters](#random-testing). The range of control injection types includes ArkTS components under ArkUI (ArkUI framework) and ArkTS components under ArkWeb (ArkWeb).|
    | execTimes                      | Number of event or control injection executions.|
    | proportion                     | Proportion of the current event operation in the total number of event injection executions.|
    | inputedTimes                   | Number of traversed control types.|
    | expectInputTimes               | Total number of application control types.|
    | coverage                       | Control traversal coverage.|

3. Ability Statistics

    | Field                     | Description               |
    | -----------------       | ------------------ |
    | bundleName              | Bundle name of the application.|
    | inputedAbilityCount     | Number of traversed Abilities.|
    | abilitiesCount          | Total number of Abilities in the application.|
    | coverage                | Ability traversal coverage.|

4. Exception Message Statistics

    > **NOTE**
    >
    > Fault log path: /data/log/faultlog/faultlogger/

    | Field             | Description        |
    | ----------------- | ------------------ |
    | type              | Fault type. The fault types include CPP_CRASH, JS_CRASH, SYS_FREEZE, APP_FREEZE, and so on. |
    | times             | Number of faults. |
    | proportion        | Proportion of the current fault in the total number of faults. |


## FAQs
### What should I do if "failed to connect to AAMS" is displayed?
 **Symptom**

The error message "failed to connect to AAMS" is displayed.

 **Possible Cause**

AAMS is occupied by Hypium or the UIViewer of DevEco Testing. AAMS can be connected to only one program at a time.

 **Solution**

Stop the process that occupies AAMS or restart the device.
### What should I do if "Errorcode:(4005)" is displayed?
 **Symptom**

The error message "Errorcode:(4005)" is displayed.

 **Possible Cause**

The size of the screen display area changes. As a result, the page information fails to be obtained.

 **Solution**

This error does not affect the test process and does not need to be handled.
### What should I do if "Errorcode:(4007)" is displayed?
 **Symptom**

The error message "Errorcode:(4007)" is displayed.

 **Possible Cause**

The size of the screen display area changes. As a result, the page information fails to be obtained.

 **Solution**

This error does not affect the test process and does not need to be handled.