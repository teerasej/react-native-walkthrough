
# ติดตั้ง Nativebase

```
npm install --save native-base 
npm install --save @expo/vector-icons@8.1.0
```

หลังจากติดตั้งแล้ว ทดลองสั่ง 

```
expo start
```

หากไม่ทำงาน และแจ้งว่าต้องรันคำสั่ง `npm install` ก็ให้รันคำสั่งตามที่แจ้งให้เรียบร้อย แล้วค่อยเรียกคำสั่ง `expo start` อีกครั้ง

ถ้าไม่ได้จริงๆ ให้ทดลองคำสั่ง `npm start`

## ดู UI ได้ที่นี่ 

- [NativeBase docs](https://docs.nativebase.io/Components.html#Components)
- [React Native UI](https://facebook.github.io/react-native/docs/getting-started)


## แก้ไข Missing font ใน Android

หากเจอปัญหา Missing font ใน Android ให้ใช้ code ต่อไปนี้ในการเริ่มต้น component

```javascript
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

## รันคำสั่ง

```
npm i --save @expo/vector-icons@8.1.0
```

## แก้ไข Overlap Status Bar ใน Android

เปิดไฟล์ `app.json` และเพิ่ม setting ด้านล่างลงไปในส่วน `expo: { ... }`

```json
"androidStatusBar": {
      "barStyle": "light-content",
      "backgroundColor": "#C2185B"
    }
```

อย่าลืมสั่งให้ App Expo โหลดค่าใหม่เข้าไป
