#Pili Streaming Cloud React Native SDK

##Introduction

最近项目需求，所以找基于react-native的直播插件，在github上找到了唯一的一个[https://github.com/buhe/react-native-pili](https://github.com/buhe/react-native-pili)，底层基于 [Pili-SDK](https://github.com/pili-engineering)，原作者是七牛的员工，后来据说离职了，所以这个分支也没人维护了，尝试过后，发现很多功能缺失/bug， 且ReactNative的SDK版本很老，于是自己托管了一份，维护。

##Change Log
1. 升级·react-native· SDK版本到`0.45`
2. 解决直播画面推流比例问题
3. 解决直播回放横竖屏问题


##Installation

```bash
npm install git+https://github.com/12d/react-native-pili.git
```

###Javascript

```bash
cd YourPorjectName
npm start
```

###iOS
1. cd node_modules/react-native-pili/ios & pod install
2. Open ios/*.xcworkspace (这里请注意是打开 .xcworkspace!请确认)
3. Just run your project (Cmd+R)
4. 如果是 iOS 10 需要在 info 中额外添加如下权限:
```
    <key>NSCameraUsageDescription</key>    
    <string>cameraDesciption</string>

    <key>NSContactsUsageDescription</key>    
    <string>contactsDesciption</string>

    <key>NSMicrophoneUsageDescription</key>    
    <string>microphoneDesciption</string>
```    
ref: [iOS 10](http://www.jianshu.com/p/c212cde86877)


###Android
1. Open android use Android Studio
2. Just run your project

##TODO
- [x] Android Player
- [x] Android Streaming
- [x] iOS Player
- [x] iOS Streaming
- [ ] 美颜和水印支持

##Usage
###1. 推流
```javascript
<Streaming
    rtmpURL={"rtmp://pili-publish.pilitest.qiniucdn.com/pilitest/demo_test?key=6eeee8a82246636e"}
    style={{
        height:400,
        width:400,
    }}
    zoom={1} //zoom 
    muted={true} //muted
    focus={false} //focus
    profile={{  //video and audio profile
       video:{
         fps:30,
         bps:1000 * 1024,
         maxFrameInterval:48
       },
       audio:{
         rate:44100,
         bitrate:96 * 1024
       },
    started={false} //streaming status
    onReady={()=>{}} //onReady event
    onConnecting={()=>{}} //onConnecting event
    onStreaming={()=>{}} //onStreaming event
    onShutdown={()=>{}} //onShutdown event
    onIOError={()=>{}} //onIOError event
    onDisconnected={()=>{}} //onDisconnected event
    />
```
###2. 直播播放
```javascript
<Player
  source={{
    uri:"rtmp://pili-live-rtmp.pilitest.qiniucdn.com/pilitest/xxx",
    timeout: 10 * 1000, //live streaming timeout (ms) Android only
    live:true, //live streaming ? Android only
    hardCodec:false, //hard codec [recommended false]  Android only
    }}
    started={true} //iOS only
    muted={false} //iOS only
    style={{
      height:200,
      width:200,
    }}
    onLoading={()=>{}} //loading from remote or local
    onPaused={()=>{}} //pause event
    onShutdown={()=>{}} //stopped event
    onError={()=>{}} //error event
    onPlaying={()=>{}} //play event
    />
```
##Release Note
##2.1.1
- [x] Android Player
- [x] Android Streaming
- [x] iOS Player
- [x] iOS Streaming 
