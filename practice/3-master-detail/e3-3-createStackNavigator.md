
## 3. สร้าง Navigator หลัก



### 1. สร้างตัวแปร App เพื่อเก็บ Navigator

เปิดไฟล์ `App.js`

เราจะเขียน import `React` และสร้างตัวแปร `App` ขึ้นมา

```js
import React from "react";

const App;

export default App;
```

สังเกตว่าในบรรทัดสุดท้ายเรามีคำสั่ง `export default App;` 

### 2. import `createStackNavigator`

```js
import React from "react";
import { createStackNavigator } from 'react-navigation';

const App = createStackNavigator({
});

export default App;
```
`createStackNavigator` เป็นระบบที่จะดูแล Page ต่างๆ (Component ที่เราเขียนแยกไปไว้ในไฟล์นั่นแหละ)

### 3. import Class HomePage และกำหนดใน StackNavigator

```js
import React from "react";
import { createStackNavigator } from 'react-navigation';
import HomePage from "./pages/home.page";


const App = createStackNavigator({
  Home: { screen: HomePage },
});


export default App;
```

ทดสอบแอพ จะเห็นว่าหน้า home แสดงขึ้นมาเหมือนเดิม แต่มีแถบสีขาวอยู่ด้านบน

### 4. นำส่วน header ของเดิมออก เพื่อให้ใช้ Navigation แทน

1. เปิดไฟล์ `pages/home.page.js` 
2. สร้าง property ชื่อ `navigationOptions` และกำหนดค่า `title`

```js
export default class HomePage extends React.Component {

    static navigationOptions = {
        title: 'Nextflow Contact',
    };
```

บันทึกไฟล์ จะเห็นว่ามีข้อความแสดงขึ้นมาในส่วนพื้นที่สีขาวด้านบนของหน้า home นี่คือ header ของ Navigation

### 5. ลบส่วนของหน้าแอพออก เหลือแต่ส่วนของ UI ในหน้านั้น

ทำการลบ Component ที่ไม่จำเป็นออกจากการ render หน้า Home Page เช่น `<Container>`, `<Header>`, `<Content>`

```js
render() {
        if (this.state.loading) {
          return <Expo.AppLoading />;
        }
    
        return (
          
          
              <List
                dataArray={this.items}
                renderRow={item => (
                  <ListItem thumbnail onPress={this.itemSelected}>
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
                    
        );
      }
```