
## 4. สร้าง Detail Page 

### 1. สร้างไฟล์หน้า Detail และกำหนดให้อยู่ใน Navigator

1. สร้างไฟล์ `pages\detail.page.js`
2. ทำการเขียนโค้ดสร้างหน้า Detail Page 

```js
import React, { Component } from "react";
import { StyleSheet, View } from "react-native";
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
  Input,
  List,
  ListItem,
  Thumbnail
} from "native-base";

export default class DetailPage extends React.Component {
  static navigationOptions = {
    title: "Detail"
  };

  constructor(props) {
    super(props);
  }

  render() {
    return <Text>Hello</Text>;
  }
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: '#fff',
        alignItems: 'center',
        justifyContent: 'center',
    },
});
```

### 2. กำหนด Detail Page ให้อยู่ใน Navigator

1. เปิดไฟล์ `App.js`
2. เพิ่ม class `DetailPage` เข้าไปใน Navigator แบบเดียวกับ `HomePage`

```js
import HomePage from "./pages/HomePage";
import DetailPage from "./pages/DetailPage";

const App = createStackNavigator({
  Home: { screen: HomePage },
  Detail: { screen: DetailPage }
});
```