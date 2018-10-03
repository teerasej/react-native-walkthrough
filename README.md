
# React Native Walkthrough

### Create project

วิธีสร้างโปรเจค

```
react-native init yourproject
```

## VS Code

ให้ทำการปิด validate eneable ใน VS Code setting

```
"javascript.validate.enable": false,
```

## ถ้ารันครั้งแรกแล้วเจอ Error 

ทดลองรันคำสั่งติดตั้ง node module 2 ตัวนี้

```
npm install --save-dev @babel/core
npm install --save-dev @babel/runtime
```

## Run Native iOS

* ก่อนการรันครั้งแรก ให้เปิดไฟล์ `.xcodeproj` และกำหนด developer account ในส่วน **signing** ก่อน

```
react-native run-ios
```

### การกำหนด version ของ simulator

แสดงรายการ simulator ทั้งหมด

```
xcrun simctl list devices
```

สั่งรันแอพด้วยชื่อ Simulator จากรายการคำสั่งด้านบน

```
react-native run-ios --simulator="iPhone 4s"
```


## Run Native Android

ในที่นี้ให้แน่ใจว่าได้ติดตั้งระบบทุกอย่างตามคู่มือแล้ว 

```
react-native run-android
```