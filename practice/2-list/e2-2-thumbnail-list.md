
# Thumbnail List

> สามารถใช้โปรเจค **e2-2.zip** ได้

## 1. Import `<Thumbnail>` component

```js
import {
  ...,
  List,
  ListItem,
  Thumbnail,
} from "native-base";
```

## 2. ปรับปรุงข้อมูล

เราจะทำการเขียนข้อมูลจำลอง 

```js
items = [
    { name: 'สมชาย', tel: '(884)-630-1206', imageURL: 'https://randomuser.me/api/portraits/men/73.jpg' },
    { name: 'สุชาติ', tel: '0901-875-7972', imageURL: 'https://randomuser.me/api/portraits/men/43.jpg' },
    { name: 'สมหมาย', tel: '(099)-724-0617', imageURL: 'https://randomuser.me/api/portraits/men/66.jpg' },
    { name: 'สมศักดิ์', tel: '(063)-186-6153', imageURL: 'https://randomuser.me/api/portraits/men/59.jpg' },
    { name: 'สุขใจ', tel: '140-536-9678', imageURL: 'https://randomuser.me/api/portraits/men/33.jpg' },
  ];
```

หลังจากจุดนี้ ถ้าทำการโหลดแอพใหม่จะเห็น error แจ้ง เพราะเนื่องจากไม่สามารถดึงข้อมูล object มาใช้โดยตรงได้ 

## 3. กำหนด property ของ object ในการแสดง Component

```js
dataArray={this.items}
renderRow={item => (
    <ListItem>
        <Text>{item.name}</Text>
    </ListItem>
)}
```

## 4. กำหนดใช้ Thumbnail ใน ListItem ใหม่

```js
            renderRow={item => (
              <ListItem>
                <Text>{item.name}</Text>
              <ListItem thumbnail>
                <Left>
                  <Thumbnail source={{ uri: item.imageURL }} />
                </Left>
                <Body>
                  <Text>{item.name}</Text>
                  <Text note>{item.tel}</Text>
                </Body>
              </ListItem>
```

## 5. ทดสอบใช้งาน `square` property เพื่อเปลี่ยนรูปทรงของ Thumbnail

```js
<Thumbnail square source={{ uri: item.imageURL }} />
```

## 6. เสร็จเรียบร้อย

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
              <ListItem thumbnail>
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