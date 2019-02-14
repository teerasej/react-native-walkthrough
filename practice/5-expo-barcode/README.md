
# Barcode Scanner

> [Expo - Barcode Scanner](https://docs.expo.io/versions/latest/sdk/bar-code-scanner/)

## 1. เตรียมพร้อมโปรเจค

1. [ดาวน์โหลดโปรเจคมาจากที่นี่](https://github.com/teerasej/react-native-workshop-barcode/tree/start)
2. แตก zip file 
3. รันคำสั่ง `npm i` จากในโฟลเดอร์์โปรเจค

## 2. import component

เปิดไฟล์ `pages/scanner.page.js`

เขียนคำสั่ง import **BarCodeScanner** และ **Permissions**

```js
import { BarCodeScanner, Permissions } from 'expo';
```

## 3. ขอ permission 

เขียนใช้ **Permissions** component ในการขอใช้กล้องมือถือ 
และเก็บค่าเอาไว้ใน state ที่ชื่อว่า **hasCameraPermission**

```js
async componentDidMount() {
    const { status } = await Permissions.askAsync(Permissions.CAMERA);

    if()
    this.setState({ hasCameraPermission: status === 'granted' });

  }
```

## 4. แสดงข้อความบนหน้าแอพในกรณีที่ permission ไม่ผ่าน

```js
render() {
    if (this.state.loading) {
      return <Expo.AppLoading />;
    }

    const { hasCameraPermission } = this.state;


    if (hasCameraPermission === null) {
      return <Text>Requesting for camera permission</Text>;
    }
    if (hasCameraPermission === false) {
      return <Text>No access to camera</Text>;
    }
    

    return (
      <View style={{ flex: 1 }}>
        
        <Button block style={styles.button} onPress={()=>{this.cancel()}}>
              <Text>
                  Cancel
              </Text>
        </Button>
      </View>
    );
  }
```

## 5. แสดงพื้นที่แสกนบาร์โค้ด

ใช้ `<BarCodeScanner/>` ในการแสดงพื้นที่แสกนบาร์โค้ด

```js
return (
      <View style={{ flex: 1 }}>
        <BarCodeScanner
          onBarCodeScanned={this.handleBarCodeScanned}
          style={StyleSheet.absoluteFill}
        />
        <Button block style={styles.button} onPress={()=>{this.cancel()}}>
              <Text>
                  Cancel
              </Text>
        </Button>
      </View>
    );
```

และเขียน method `handleBarCodeScanned` เพื่อรับข้อมูลหลังจากแสกนข้อมูลได้แล้ว 

```js
handleBarCodeScanned = ({ type, data }) => {
    console.log(`Bar code with type ${type} and data ${data} has been scanned!`);
    this.props.navigation.goBack();
    this.props.navigation.state.params.onGotBarcode(data);
  }
```

## 6. ส่งข้อมูลกลับไปยังหน้าแรกผ่าน this.props.navigation

```js
handleBarCodeScanned = ({ type, data }) => {
    console.log(`Bar code with type ${type} and data ${data} has been scanned!`);
    
    this.props.navigation.goBack();
    this.props.navigation.state.params.onGotBarcode(data);
  }
```

## 7. รับข้อมูลมาแสดงในหน้าแรกผ่าน this.state

เปิดไฟล์ `pages/home.page.js`

และเขียนนำข้อมูลมาอัพเดตใน method `onGotBarcode`

```js
openScanner = () => {
        this.props.navigation.navigate('Scanner', { onGotBarcode: this.onGotBarcode });
}

onGotBarcode = (barcode) => {
    console.log('Barcode', barcode)
    this.setState({ barcodeData: barcode });
}
```

### อธิบายเพิ่มเติม

เพราะในที่นี้ตอนเปิดไปหน้า Scanner เราส่ง method `onGotBarcode` ไปหน้า Scanner ในชื่อของ `onGotBarcode` 

```js
this.props.navigation.navigate('Scanner', { onGotBarcode: this.onGotBarcode });
```

ดังนั้นในหน้า `scanner.page.js` เราจึงสามารถดึง method มาส่งค่าได้ผ่านคำสั่ง 

```js
handleBarCodeScanned = ({ type, data }) => {
    //...
    this.props.navigation.state.params.onGotBarcode(data);
}
```

## 8. บันทึกไฟล์ และทดสอบ

## เฉลย

เฉลยสามารถ[ดาวน์โหลด zip file ได้จากที่นี่](https://github.com/teerasej/react-native-workshop-barcode) และรันคำสั่ง `npm i` ให้เรียบร้อยก่อนใช้งานโปรเจค

