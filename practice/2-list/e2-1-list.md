
# เตรียมพร้อม Project

## 1. ติดตั้ง Package dependencies

สร้างโปรเจคใหม่ และทำตาม[ขั้นตอน 1-3 จาก lab นี้](https://teerasej.github.io/react-native-walkthrough/practice/1-vat7/) เพื่อเตรียมโปรเจค

## 2. สร้าง Properties ไว้เก็บ Array 

```js
export default class App extends React.Component {

  items = [
    "Nextflow.in.th",
    "React Native",
    "Flutter",
    "Ionic",
    "MEAN Stack"
  ];

```

## 3. เขียน Import `<List>` และ `<ListItem>` 

```js
import {
  ...,
  List,
  ListItem,
  
} from "native-base";
```

## 4. แสดง List และ ListItem ขึ้นมาในหน้า page


โดยเราสามารถกำหนดค่า `dataArray` เป็นตัวแปร Array ที่เราใช้เตรียมไว้ได้

```html
     
    <Content>
        <Text>...</Text>
        <List
            dataArray={this.items}
            renderRow={(item) => {
              return (
                  <ListItem>
                      <Text>{item}</Text>
                  </ListItem>
              );
            }}
        />
    </Content>
</Container>
```

- และจะสังเกตว่า `renderRow` ของ `<List>` นั้นรับค่าเป็น function 
- โดยตัว function จะรับค่ามาจาก List ซึ่งค่าแรกก็คือ item ที่อยู่ใน `dataArray` นั่นเอง
- ตัว function ต้อง return Component ออกไปให้ List ใช้ในการแสดง UI ปกติแล้วก็คือ `<ListItem>`
- อ้างอิงได้จาก [http://facebook.github.io/react-native/docs/listview.html#renderrow](http://facebook.github.io/react-native/docs/listview.html#renderrow)

## 5. ปรับให้ function ใน renderRow เรียบง่ายขึ้น

```html
    <List
        dataArray={this.items}
        renderRow={item => (
            <ListItem>
                <Text>{item}</Text>
            </ListItem>
        )}
    />
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
} from "native-base";

export default class App extends React.Component {

  items = [
    "Nextflow Training",
    "React Native",
    "Flutter",
    "Ionic",
    "MEAN Stack"
  ];

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
            <Title>Nextflow Contact</Title>
          </Body>
        </Header>
        <Content>
          <List
            dataArray={this.items}
            renderRow={item => (
              <ListItem>
                <Text>{item}</Text>
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
