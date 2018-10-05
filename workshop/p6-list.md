
# List 

`<List>` ของ Nativebase เป็นหนึ่งใน UI ที่นิยมใช้กัน ส่วนสำคัญพื้นฐานได้แก่

1. `dataArray` สำหรับกำหนดค่า Array ที่จะใช้ในการวนลูปแสดงผลเป็น `ListItem`
2. `renderRow` สำหรับกำหนด function ที่จะรับค่า item ใน `dataArray` มาใช้ในการวนลูป

```javascript
<List
    dataArray={this.items}
    renderRow={item => {
        return (
        <ListItem>
        <Text>{item}</Text>
        </ListItem>
    )}}
    />
```

## ตัวอย่าง

```javascript
import React from "react";
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
  ListItem
} from "native-base";

export default class App extends React.Component {
  items = [
    "Simon Mignolet",
    "Nathaniel Clyne",
    "Dejan Lovren",
    "Mama Sakho",
    "Emre Can"
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
      Ionicons: require("@expo/vector-icons/fonts/Ionicons.ttf")
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
          <List
            dataArray={this.items}
            renderRow={item => {
                return (
              <ListItem>
                <Text>{item}</Text>
              </ListItem>
            )}}
          />
        </Content>
      </Container>
    );
  }
}

```

## List Detail

List Item ของ Nativebase มาพร้อมกับ Template เริ่มต้นที่ปรับแต่งได้ เช่นการแสดงรูปภาพ 

```javascript
import React from "react";
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

export default class App extends React.Component {
  items = [
    { name: 'valmira', tel: '(884)-630-1206', imageURL: 'https://randomuser.me/api/portraits/men/73.jpg'},
    { name: 'lucille', tel: '0901-875-7972', imageURL: 'https://randomuser.me/api/portraits/men/43.jpg'},
    { name: 'inaya', tel: '(099)-724-0617', imageURL: 'https://randomuser.me/api/portraits/men/66.jpg'},
    { name: 'mustafa', tel: '(063)-186-6153', imageURL: 'https://randomuser.me/api/portraits/men/59.jpg'},
    { name: 'liam', tel: '140-536-9678', imageURL: 'https://randomuser.me/api/portraits/men/33.jpg'},
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
      Ionicons: require("@expo/vector-icons/fonts/Ionicons.ttf")
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
          <List
            dataArray={this.items}
            renderRow={item => (
              <ListItem thumbnail>
              <Left>
                <Thumbnail square source={{ uri:item.imageURL}} />
              </Left>
              <Body>
                <Text>{item.name}</Text>
                <Text note>{item.phone}</Text>
              </Body>
              <Right>
                <Button transparent>
                  <Text>View</Text>
                </Button>
              </Right>
            </ListItem>
            )}
          />
        </Content>
      </Container>
    );
  }
}

```