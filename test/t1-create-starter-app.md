
## Test 1: Create Starter App

### 1. สร้างโปรเจคใหม่ ชื่อ **react-app**

```
expo init react-app
```

### 2. เข้าไปในโฟลเดอร์โปรเจค แล้วรันคำสั่งติดตั้ง dependencies package ชื่อ **native-base** กับ **@expo/vector-icons@8.1.0**

> คำสั่งติดตั้ง `npm install` ต้องสั่งรันจากภายในโฟลเดอร์โปรเจคเท่านั้น

```
cd react-app
npm install --save native-base 
npm install --save @expo/vector-icons@8.1.0
```

### 3. สร้าง template ของหน้าแอพแรก โดยการ copy โค้ดด้านล่างไปวางแทนที่โค้ดเดิมในไฟล์ `App.js`

```js
import React from 'react';
import { StyleSheet, View } from 'react-native';
import {
  Container,
  Header,
  Title,
  Content,
  Footer,
  FooterTab,
  Button,
  Left,
  Right,
  Body,
  Icon,
  Text,
  Form,
  Item,
  Input
} from "native-base";

export default class App extends React.Component {
  constructor(props){
    super(props);

    this.state = {
      loading: true
    };
  }

  async componentWillMount() {
    await Expo.Font.loadAsync({
      Roboto: require("native-base/Fonts/Roboto.ttf"),
      Roboto_medium: require("native-base/Fonts/Roboto_medium.ttf"),
      Ionicons: require("@expo/vector-icons/fonts/Ionicons.ttf"),
    });
    this.setState({ loading: false });
  }
  

  render() {

    if (this.state.loading) {
      return <Expo.AppLoading />;
    }

    return (
      <Container>
        <Header>
          <Body>
            <Title>My App</Title>
          </Body>
        </Header>
        <Content>
          <Text>Hello</Text>
        </Content>
      </Container>
    );
  }
}
```


### 4. ทดสอบรันแอพพลิเคชั่นในอุปกรณ์พกพา

```
expo start
```

