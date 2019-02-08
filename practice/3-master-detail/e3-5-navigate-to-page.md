
## 5. เขียนคำสั่งเปิดไปยังหน้าที่ 2

เมื่อใช้ createNaviation() แล้ว Component ทุกตัวใน Navigation ซึ่งในที่นี้คือ `HomePage` และ `DetailPage` จะได้รับ object ชื่อ `navigation` ส่งผ่านเข้ามาใน `this.props` 

เราสามารถเรียกใช้ค่า `this.props.navigation` ในการควบคุมการเปิดไปมาในแอพพลิเคชั่นของเราได้ 

```js
itemSelected = (data) => {
    console.log('data:', data);
    this.props.navigation.navigate('Detail');
}
```

ให้สังเกตว่า เราใช่ string ที่เป็นชื่อของ screen ในไฟล์ `App.js`

```js
const App = createStackNavigator({
  Home: { screen: HomePage },
  Detail: { screen: DetailPage }
});
```

บันทึกไฟล์ และทดสอบคลิกเลือก item ใน List เพ่ือเปิดไปหน้าที่ 2 