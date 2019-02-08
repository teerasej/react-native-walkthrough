
## 6. ส่งข้อมูล และใช้ข้อมูลในเพจที่เปิดขึ้นมาใหม่ 


### 1. ส่ง object ข้อมูลที่ต้องการ ไปยัง

เปิดไฟล์ `pages/home.page.js`

เราสามารถกำหนดส่งผ่าน object ไปยัง Screen ที่จะถูกเปิดขึ้นมาได้ ผ่าน parameter ตัวที่ 2 ของ `this.props.navigation.navigate()` 

```js
itemSelected(data) {
    console.log('data:', data);
    this.props.navigation.navigate('Detail', data);
}
```

### 2. ดึงเอาข้อมูลมาใช้งานใน Component ที่ถูกโหลดขึ้นมาเป็น page

เปิดไฟล์ `pages/detail.page.js`

เราสามารถดึงค่าที่ส่งมา กลับมาใช้ได้จากคำสั่ง `this.props.navigation.state.params`

```js
render() {

    // or use this.props.navigation.getParams('object property name')
    // Reference: https://reactnavigation.org/docs/en/params.html
    let data = this.props.navigation.state.params;
    console.log(data);

    return <Text>{data.name}</Text>;
  }
```

ทดสอบการทำงานดู จะเห็นว่าชื่อของ User ที่ถูกเลือก จะมาปรากฎในหน้าที่ 2 แล้ว 

### 3. แสดงชื่อใน Header ของ Navigation Bar


จากค่า `navigationOptions` ที่เรากำหนดเป็น object ธรรมดานั้น เราสามารถเปลี่ยนเป็น function ที่คืนค่า object ออกไปได้ด้วย

เช่นในที่นี้ ตัว function  เรารับค่า `navigation` เข้ามา เพื่อเข้าถึง parameter ที่ช่ือ `name` ที่ส่งมาจากหน้าแรก

```js
{ name: 'สมชาย', tel: '(884)-630-1206', imageURL: 'https://randomuser.me/api/portraits/men/73.jpg' }
```

เขียนได้แบบนี้

```js
static navigationOptions = ({ navigation }) => {
  return {
    title: navigation.getParam("name")
  };
};
```

### 4. แสดงภาพจากข้อมูลที่ส่งมาจากหน้าแรก

ด้วยข้อมูลที่เรามี ทำให้เราสามารถดึงข้อมูลของ user ที่ได้มาใช้ในหน้า Detail ได้เหมือนกับในหน้า Home


```js
render() {
    let data = this.props.navigation.state.params;
    console.log(data);

    return (
      <View style={styles.container}>
        <Image
          style={{ width: 100, height: 100 }}
          source={{
            uri:
              data.imageURL
          }}
        />
        <Text>{data.name}</Text>
      </View>
    )
  }
```


