## 2. แยกโค้ดหน้า home page ออกจากไฟล์ App.js

1. สร้างโฟลเดอร์์ `pages` ขึ้นมาในโปรเจค
2. สร้างไฟล์ `pages/home.page.js` 
3. ย้ายโค้ดทั้งหมดในไฟล์ `App.js` ไปไว้ในไฟล์ `pages/home.page.js`
4. เปลี่ยนชื่อ class จาก

```js
export default class App extends React.Component {
```

เป็น 

```js
export default class HomePage extends React.Component {
```

### โค้ดในไฟล์ home.page.js

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

export default class HomePage extends React.Component {

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