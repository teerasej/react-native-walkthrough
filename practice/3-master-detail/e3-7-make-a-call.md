
## 7. ทำปุ่มโทรออก


### 1. สร้างปุ่ม

เปิดไฟล์ `pages/detail.page.js`

เราสามารถสร้างปุ่มขึ้นมาใน

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
        <Button block style={styles.button}>
          <Text>
            Call {data.tel}
          </Text>
        </Button>
      </View>
    )
}
```

และกำหนดตำแหน่งของปุ่มด้วยการตั้งค่า Styles เหมือนเดิม

```js
const styles = StyleSheet.create({
  container: {
      flex: 1,
      padding: 10,
      backgroundColor: '#fff',
      alignItems: 'center',
      justifyContent: 'center',
  },
  button : {
    marginTop: 10
  }
});
```

### 2. สร้าง method สำหรับการเรียกระบบโทรศัพท์

เราจะเพิ่ม event `onPress` ให้กับปุ่ม

```html
<Button block style={styles.button} onPress={this.makeCall}>
    <Text>
    Call {data.tel}
    </Text>
</Button>
```

และเขียน method เอาไว้ใน class โดยดึงค่าออกมาจาก `this.props.navigation.state.params`

```js
makeCall = () => {
    let data = this.props.navigation.state.params;
    console.log('Calling', data.tel); 
}
```

### 3. ติดตั้ง `react-native-phone-call`

1. หยุด Expo server โดยใช้ปุ่ม Ctrl + C 
2. รันคำสั่ง `npm install --save react-native-phone-call` ใน Terminal
3. รันคำสั่ง `yarn start` เพื่อเริ่ม expo server อีกที

### 4. เรียกใช้ `react-native-phone-call` ในโค้ด

1. เปิดไฟล์ `pages/detail.page.js`
2. เขียนคำสั่ง import

```js
import call from 'react-native-phone-call'
```

3. เขียนคำสั่งโทรใน method `makeCall`

```js
makeCall = () => {
    let data = this.props.navigation.state.params;
    console.log('Calling', data.tel); 

    call({
        number: data.tel
    }).catch()
}
```