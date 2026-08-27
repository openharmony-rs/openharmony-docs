# 向用户申请单次授权

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

基于授权最小化原则，防止应用获取和滥用用户数据。针对部分应用敏感权限，在弹窗向用户申请授权时，新增“允许本次使用”的授权选项。

开发者在开发应用时，无需额外配置，仍然调用requestPermissionsFromUser()向用户申请授权。系统会根据该能力支持的权限，弹出对应的弹窗。

授权弹窗如下图所示：

<!--RP1-->
![alt text](figures/allow_this_time.png)

设置选项如下图所示：

![alt text](figures/setting_allow_this.png)

路径：设置 > 隐私 > 权限管理 > 应用 > 目标应用 > 位置信息
<!--RP1End-->

## 支持范围

当前仅支持以下权限，当应用向用户申请这些权限时，弹窗将显示“允许本次使用”的选项；在设置中修改这些权限时，系统将显示“每次询问”的选项。

- 剪贴板："ohos.permission.READ_PASTEBOARD"
- 模糊位置："ohos.permission.APPROXIMATELY_LOCATION"
- 位置："ohos.permission.LOCATION"
- 后台位置："ohos.permission.LOCATION_IN_BACKGROUND"
- 麦克风："ohos.permission.MICROPHONE"
- 相机："ohos.permission.CAMERA"

## 使用限制

- 当用户点击“允许本次使用”按钮后，应用将获得临时权限。

  在应用处于以下状态时，应用的临时权限会持续保留：

    - 应用处于前台活跃状态。
    - 应用展开卡片，且卡片处于当前屏幕可见。
    - 应用使用定位导航类后台长时任务，可保留位置/模糊位置/后台位置权限。

    除上述状态外，系统将启动 10 秒倒计时，计时结束后，系统将自动取消临时授权。临时授权被取消后，若需再次获取该权限，必须重新向用户弹窗申请授权。

    <!--RP2-->
    如下图样例所示，相机应用处于卡片可见状态：

    ![alt text](figures/form_visible.png)
    <!--RP2End-->
- 当用户在位置的权限设置中选择“每次询问”时，应用将获得模糊位置和位置临时权限。取消临时授权的操作与此相同。