
# Location

> [Expo - Location](https://docs.expo.io/versions/latest/sdk/location/)

## 1. เตรียมพร้อมโปรเจค

1. [ดาวน์โหลดโปรเจคมาจากที่นี่](https://github.com/teerasej/react-native-workshop-location-gps/tree/start)
2. แตก zip file 
3. รันคำสั่ง `npm i` จากในโฟลเดอร์์โปรเจค

## 2. import component

เปิดไฟล์ `App.js`

เขียนคำสั่ง import **Location** และ **Permissions**

```js
import { Location, Permissions } from 'expo';
```

## 3. เขียน check permission

เขียนใช้ **Permissions** component ในการขอใช้ระบบระบุตำแหน่ง 

```js
async getPosition() {
    let { status } = await Permissions.askAsync(Permissions.LOCATION);

    if (status !== 'granted') {
      this.setState({
        errorMessage: 'Permission to access location was denied',
      });
    }
}
```

## 4. ขอตำแหน่ง Location

```js
 async getPosition() {
    let { status } = await Permissions.askAsync(Permissions.LOCATION);

    if (status !== 'granted') {
      this.setState({
        errorMessage: 'Permission to access location was denied',
      });
    }

    let location = await Location.getCurrentPositionAsync({});
    console.log(location);
    this.setState({ location });

}
```

## 5. กำหนดการแสดงผลที่แตกต่างกัน ตามข้อมูลที่อยู่ใน this.state.location


```js
render() {
    if (this.state.loading) {
      return <Expo.AppLoading />;
    }

    let report;

    if (this.state.location) {
      report = (
        <View>
          <Text>Latitude: {this.state.location.coords.latitude}</Text>
          <Text>longitude: {this.state.location.coords.longitude}</Text>
          <Text>error: {this.state.errorMessage}</Text>
        </View>
      )
    } else {
      report = (
        <View>
          <Text>กดปุ่มเพื่อดึงข้อมูล</Text>
        </View>
      )
    }

    return (

      <Container>
        <Header>
          <Body>
            <Title>Nextflow GPS</Title>
          </Body>
        </Header>

        <Content style={styles.content}>

          <Button block onPress={() => { this.getPosition() }}>
            <Text>
              Get GPS
            </Text>
          </Button>
          {report}
        </Content>

      </Container>

    );
  }
```


## 6. บันทึกไฟล์ และทดสอบ

## เฉลย

เฉลยสามารถ[ดาวน์โหลด zip file ได้จากที่นี่](https://github.com/teerasej/react-native-workshop-location-gps/tree/master) และรันคำสั่ง `npm i` ให้เรียบร้อยก่อนใช้งานโปรเจค

