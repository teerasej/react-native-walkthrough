
# เริ่มต้น

## ติดตั้งชุดคำสั่งที่จำเป็น 

**Mac**

```
sudo npm install -g create-react-native-app
sudo npm install -g expo-cli
sudo npm install -g exp
sudo npm install -g react-native-cli
```

**Windows**

```
npm install -g create-react-native-app
npm install -g expo-cli
npm install -g exp
npm install -g react-native-cli
```

**ติดตั้ง Expo Application ลงในอุปกรณ์**

https://expo.io/

## สร้างและทดสอบโปรเจค

### 1. สร้างโปรเจค

จากโปรแกรม Terminal, Command Prompt, หรือ Powershell ให้รันคำสั่ง

```
expo init vat7
```

1. เลือก template: **blank**
2. เลือก workflow: **managed**
3. กำหนดชื่อเป็น: **Nextflow Vat7**
4. ถ้ามีการถามเรื่อง yarn ให้ตอบตกลง: **yes**

### 2. ทดสอบรันแอพพลิเคชั่น

* ให้แน่ใจว่า Computer กับอุปกรณ์พกพาอยู่เครือข่ายเดียวกัน

```
cd vat7

// ถ้าลง npm
npm start

// ถ้าลง yarn
yarn start
```

จะเป็นการเปิด Web server ของ Expo ขึ้นมา เราสามารถเลือกใช้เมนูจากทางด้านซ้ายมือได้

1. สำหรับ Android เลือกคำสั่ง **Run Android Device/Simulator** จาก Web console
2. สำหรับ iOS สามารถเลือกคำสั่ง

## กรณีเจอปัญหาระหว่างรันคำสั่งใน Expo Web console


### A. เปิด iOS  Simulator ไม่ขึ้น 
```
Simulator not installed. Please visit https://developer.apple.com/xcode/download/ to download Xcode and the iOS simulator. If you already have the latest version of Xcode installed, you may have to run the command `sudo xcode-select -s /Applications/Xcode.app`.
```

ให้ตรวจสอบให้แน่ใจว่า ใน Xcode มี iOS Simulator อย่างน้อย 1 ตัว [ดูวิธีเช็คและสร้าง Simulator ได้จากที่นี่](https://nextflow.in.th/2019/create-and-manage-ios-simulator-with-xcode-thai/)



ถ้าเช็คแล้วว่ามี ให้ทดลองรันคำสั่งด้านล่าง แล้วลองใหม่อีกครั้ง

```
sudo xcode-select -s /Applications/Xcode.app
```



### B. เกิด error จอแดง ใน Expo App บนมือถือ

```
Module `@expo/vector-icons/AntDesign` does not exist in the Haste module map ...
```

ให้รันทีละคำสั่ง ตามรายการด้านล่าง

```
watchman watch-del-all
rm -rf node_modules && npm i
rm -rf /tmp/metro-bundler-cache-*
npm start --reset-cache
```


### C. แก้ error `Props` ตอนเปิดโปรเจคใน Visual Studio Code

ให้ทำการปิด validate eneable ใน VS Code setting

```
"javascript.validate.enable": false,
```