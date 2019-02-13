
# ใช้งาน Event ของ ListItem

## 1. สร้าง method สำหรับกรณีที่เกิดการกดเลือก item ใน List

```js
  itemSelected = () => {
    console.log('ok');
  }
```

## 2. เรียกใช้งาน method กับ event `onPress` ใน List Item

```html
 <ListItem thumbnail onPress={this.itemSelected}>
```

ทดสอบกดใช้่งาน จะเห็นว่ามีคำว่า ok แสดงขึ้นมาใน log


## 3. กำหนดให้ส่งข้อมูลของ item กดเลือกเข้ามาใน method

```js
  itemSelected = (data) => {
    console.log('data:', data);
  }
```

และเขียน function ใหม่ใน event `onPress`

```html
 <ListItem thumbnail onPress={() => this.itemSelected(item)}>
```

ทดสอบกดใช้่งาน จะเห็นว่ามีคำว่ามี object ของ List Item ที่กดเลือก แสดงขึ้นมาใน log

## 4. เสร็จเรียบร้อย

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
  Input,
  List,
  ListItem,
  Thumbnail,
} from "native-base";

export default class App extends React.Component {

  items = [
    { name: 'สมชาย', tel: '(884)-630-1206', imageURL: 'https://randomuser.me/api/portraits/men/73.jpg' },
    { name: 'สุชาติ', tel: '0901-875-7972', imageURL: 'https://randomuser.me/api/portraits/men/43.jpg' },
    { name: 'สมหมาย', tel: '(099)-724-0617', imageURL: 'https://randomuser.me/api/portraits/men/66.jpg' },
    { name: 'สมศักดิ์', tel: '(063)-186-6153', imageURL: 'https://randomuser.me/api/portraits/men/59.jpg' },
    { name: 'สุขใจ', tel: '140-536-9678', imageURL: 'https://randomuser.me/api/portraits/men/33.jpg' },
  ];

  constructor(props) {
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

  itemSelected = (data) => {
    console.log('data:', data);
  }


  render() {

    if (this.state.loading) {
      return <Expo.AppLoading />;
    }

    return (
      <Container>
        <Header>
          <Body>
            <Title>Nextflow Contact</Title>
          </Body>
        </Header>
        <Content>
          <List
            dataArray={this.items}
            renderRow={item => (
              <ListItem thumbnail onPress={() => this.itemSelected(item)}>
                <Left>
                  <Thumbnail square source={{ uri: item.imageURL }} />
                </Left>
                <Body>
                  <Text>{item.name}</Text>
                  <Text note>{item.tel}</Text>
                </Body>
              </ListItem>
            )}
          />
        </Content>
      </Container>
    );
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
