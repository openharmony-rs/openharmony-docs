# 录屏常见问题

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

## 录屏启动报错AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT

实例数量超出规格限制，当前规格为每种数据格式最多两个实例。建议释放多余实例后再使用新实例。

录屏会话限制策略：

1. 客户端应用数量上限4个，比如会议屏幕共享、会议投屏、后台听歌识曲、系统录屏同时存在。

2. 单应用单模式（存为文件或存为码流）可创建实例上限2个，典型场景：在线上会议共享屏幕时，需要同步录制会议内容。
