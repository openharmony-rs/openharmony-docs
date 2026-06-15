# WLAN常见问题

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->

## 使用wifiManager.getLinkedInfo()获取SSID时，是否需要访问用户位置信息
使用设备MAC连接时需申请ohos.permission.GET_WIFI_LOCAL_MAC权限；随机MAC不需要。

## App在使用addCandidateConfig连接WiFi时偶现错误码201，需明确错误原因及修复方式以优化用户体验
需要权限： ohos.permission.SET_WIFI_INFO。

## 鸿蒙系统是否有API来切换网络，以解决在特定情况下无法连接外网的问题
将指定的WLAN设备配置添加为候选网络，添加后的网络在没有连接记录的情况下无法触发自动回连，可以通过connectToCandidateConfig或connectToCandidateConfigWithUserAction方法实现候选网络连接，页面确认连接成功后，可实现自动回连。

## 在连接到没有网络的热点时，系统会自动断开连接且未触发Wi-Fi连接状态变化的回调，导致无法正常监听连接状态变化
该网络无互联网访问权限。点击【确定】连接，或【取消】自动切换至更优网络。
