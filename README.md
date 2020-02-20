# tencent_rtc_plugin

腾讯云实时音视频插件

## 功能清单
[x]房间相关接口函数  
[x]视频相关接口函数  
[x]音频相关接口函数  
[x]摄像头相关函数  
[ ]直播相关接口函数  
[ ]美颜滤镜相关接口  
[ ]自定义采集和渲染  
[ ]自定义消息发送  
[ ]背景混音相关接口  
[ ]音效相关接口  
[ ]网络测试  
[ ]混流转码并发布到 CDN  
[ ]Log相关接口  
[ ]播放背景音乐的回调接口  
[ ]视图边距  
[x]回调事件  
[ ]枚举类型同步(大改动)  
[ ]数据对象同步(大改动)  
[ ]README.md 编写    

## Getting Started

该插件基于腾讯音视频通话进行集成。    
引用腾讯官方文档原文：``在 defaultConfig 中，指定 App 使用的 CPU 架构(目前 TRTC SDK 支持 armeabi ， armeabi-v7a 和 arm64-v8a) 。``  
如果出现闪退问题，请检查是否是系统架构导致

## 集成

### Flutter
```
  tencent_rtc_plugin:
    git:
      url: https://github.com/JiangJuHong/FlutterTencentRtcPlugin.git
      ref: master
```
暂不支持通过版本号引入

### Android
无需额外配置，已内部打入混淆规则

### IOS
配置权限信息，在Info.plist中增加
```
<key>NSMicrophoneUsageDescription</key>
<string>App需要您的同意,才能访问麦克风</string>
<key>NSCameraUsageDescription</key>
<string>App需要您的同意,才能访问摄像头</string>
```

## 功能清单
|  接口   | 说明  | 参数  | Android | IOS |
|  ----  | ----  | ----  | ----  | ----  |
| enterRoom  | 进入房间 | - | √ | 
| exitRoom  | 退出房间 | - | √ | 
| switchRole  | 切换角色 | - | √ | 
| setDefaultStreamRecvMode  | 设置音视频数据接收模式（需要在进房前设置才能生效）。 | - | √ | 
| muteRemoteAudio  | 静音 / 取消静音 | - | √ | 
| muteAllRemoteAudio  | 静音 / 取消静音 所有用户 | - | √ | 
| setRemoteViewFillMode  | 设置远程显示填充模式 | - | √ | 
| setLocalViewFillMode  | 设置本地显示填充模式 | - | √ | 
| startLocalAudio  | 开启本地音频采集 | - | √ | 
| stopLocalAudio  | 关闭本地音频采集 | - | √ | 
| stopAllRemoteView  | 停止显示所有远端视频画面。 | - | √ | 
| muteRemoteVideoStream  | 暂停接收指定的远端视频流。 | - | √ | 
| muteAllRemoteVideoStreams  | 停止接收所有远端视频流。 | - | √ | 
| setVideoEncoderParam  | 设置视频编码相关。 | - | √ | 
| setNetworkQosParam  | 设置网络流控相关参数。 | - | √ | 
| setLocalViewRotation  | 设置本地图像的顺时针旋转角度。 | - | √ | 
| setRemoteViewRotation  | 设置远端图像的顺时针旋转角度。 | - | √ | 
| setVideoEncoderRotation  | 设置视频编码输出的（也就是远端用户观看到的，以及服务器录制下来的）画面方向。 | - | √ | 
| setLocalViewMirror  | 设置本地摄像头预览画面的镜像模式。 | - | √ | 
| setVideoEncoderMirror  | 设置编码器输出的画面镜像模式。 | - | √ | 
| setGSensorMode  | 设置重力感应的适应模式。 | - | √ | 
| enableEncSmallVideoStream  | 开启大小画面双路编码模式。 | - | √ | 
| setRemoteVideoStreamType  | 选定观看指定 uid 的大画面或小画面。 | - | √ | 
| setPriorRemoteVideoStreamType  | 设定观看方优先选择的视频质量。 | - | √ | 
| muteLocalAudio  | 静音本地的音频。 | - | √ | 
| setAudioRoute  | 设置音频路由。 | - | √ | 
| enableAudioVolumeEvaluation  | 启用音量大小提示。 | - | √ | 
| startAudioRecording  | 开始录音。 | - | √ | 
| stopAudioRecording  | 停止录音。 | - | √ | 
| setSystemVolumeType  | 设置通话时使用的系统音量类型。 | - | √ | 
| enableAudioEarMonitoring  | 开启耳返。 | - | √ | 
| switchCamera  | 切换摄像头。 | - | √ | 
| isCameraZoomSupported  | 查询当前摄像头是否支持缩放。 | - | √ | 
| setZoom  | 设置摄像头缩放因子（焦距）。 | - | √ | 
| isCameraTorchSupported  | 查询是否支持开关闪光灯（手电筒模式）。 | - | √ | 
| enableTorch  | 开启闪光灯 | - | √ | 
| isCameraFocusPositionInPreviewSupported  | 查询是否支持设置焦点 | - | √ | 
| setFocusPosition  | 设置摄像头焦点 | - | √ | 
| isCameraAutoFocusFaceModeSupported  | 查询是否支持自动识别人脸位置 | - | √ | 

## 使用
大部分方法直接基于腾讯云原始API，根据 TencentRtcPlugin 对象即可使用；部分视频相关内容，TencentRtcVideoView 需要配合 TencentRtcVideoViewControlle调用方法;  
例如进入房间只需要调用``TencentRtcPlugin.enterRoom()``即可，腾讯API文档地址:[linke https://cloud.tencent.com/document/product/647/32264](https://cloud.tencent.com/document/product/647/32264)  
<img src="https://raw.githubusercontent.com/JiangJuHong/access-images/master/FlutterTencentRtcPlugin/1.png" height="300em" style="max-width:100%;display: inline-block;"/>
<img src="https://raw.githubusercontent.com/JiangJuHong/access-images/master/FlutterTencentRtcPlugin/2.png" height="300em" style="max-width:100%;display: inline-block;"/>
