---
kits: ["Media Kit / 媒体服务"]
description: "汇总AVTranscoder视频转码过程中的常见问题，包括音频编码格式自动变更原因及转码失败后的处理建议，适用于转码功能排障场景。"
keywords: [AVTranscoder, 转码, 常见问题, 音频编码格式, AAC, 转码失败, 错误处理, 格式支持]
doctype: faq
status: active
---
# 转码常见问题
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @yangde_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 应用发送视频进行转码，音频编码格式为什么变化

在转码过程中，若未指定音频编码格式，系统默认将其转换为AAC编码格式。

<!--RP2--><!--RP2End-->

## 调用系统提供的转码能力失败后如何处理

1. 需要确认视频与设置的目标视频格式当前转码系统能力是否支持。

   当前转码能力支持情况：[AVTranscoder支持的格式](media-kit-intro.md#avtranscoder)、[AVCodec支持的格式](../avcodec/avcodec-support-formats.md)<!--RP1--><!--RP1End-->。

2. 应用在收到error事件后，建议发送原视频；应用在收到complete事件后，建议先调用release再对转码后的视频做发送、上云等操作。
