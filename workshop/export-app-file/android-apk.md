
# Export Android (APK file)

## 1. กำหนดรายละเอียดในไฟล์ app.json ให้เรียบร้อย

ระบบ Expo จะใช้ข้อมูลในไฟล์ `app.json` ในการ build โปรเจค 

```js
{
   "expo": {
    "name": "Your App Name",
    "icon": "./path/to/your/app-icon.png",
    "version": "1.0.0",
    "slug": "nextflow-app-name",
    "sdkVersion": "XX.0.0",
    "ios": {
      "bundleIdentifier": "th.in.nextflow.yourappname"
    },
    "android": {
      "package": "th.in.nextflow.yourappname"
    }
   }
 }
```

ในส่วนของ iOS `bundleIdentifier` และ Android `package` เป็นชื่อ ID ของแอพ สามารถตั้งเองได้ โดยใช้แนวทางเหมือนตั้งชื่อ domain name แต่เขียนย้อนกลับ เช่น

**nextflow.in.th** เขียนเป็น **th.in.nextflow.myapp**


### 2. รันคำสั่งผ่าน Terminal

1. จาก terminal รันคำสั่ง `expo build:android`
2. จะมีการตรวจเช็คข้อมูล ถ้ามีข้อผิดพลาด ให้แก้ตามรายการที่ขึ้น error ใน log
3. **ถ้ามีการถาม Expo Account** ให้กรอก username และ password ให้เรียบร้อย (ถ้าไม่มีก็เลือกสร้างใหม่ได้)
4. **ถ้ามีการถาม Apple ID** ให้กรอกชื่อ และรหัสผ่าน ที่ลงทะเบียนกับทาง Apple ไว้ (เสีย $99/ปี นั่นแหละ)
5. ถ้าถามว่า

```
? How would you like to upload your credentials? (Use arrow keys)
```

ให้เลือกตอบ

```
❯ Expo handles all credentials, you can still provide overrides 
```

6. ระบบจะดำเนินการ build กับ Expo service และสามารถเช็คสถานะได้จากลิ้งค์ที่แสดงใน terminal 

```
[16:10:56] You can monitor the build at
 https://expo.io/builds/c7188116-6a1f-46ef-853e-512c82dc986e
```

7. ดาวน์โหลดไฟล์มาใช้งานจากล้ิงค์ เมื่อการ build สิ้นสุด