
# Navigation Stack

## ติดตั้ง react-navigation

```
npm install --save react-navigation
```

## แยก Page Component อย่างชัดเจน

เราจะเริ่มต้นจาก 3 ไฟล์

### App.js

ไฟล์กลางที่เราจะใช้กำหนด Routing ของลิ้งค์ต่างๆ กับ Component ที่เราต้องการ

1. เรามีการ import `createStackNavigator` มาใช้งาน 
2. `createStackNavigator` เป็น function ที่เรา object เข้าไป เราจะกำหนดว่า link ไหนจะเรียกใช้ component ไหนขึ้นมาใช้งาน
3. เช่น ชื่อลิ้งค์ **Home** จะกำหนด screen เป็น component ที่ชื่อ **HomePage** (import มาจากไฟล์ `Homepage.js`)

```javascript
...
import { createStackNavigator } from 'react-navigation';
import HomePage from "./pages/HomePage";
import DetailPage from "./pages/DetailPage";

const App = createStackNavigator({
  Home: { screen: HomePage },
  Detail: { screen: DetailPage }
});

```

### pages/HomePage.js

กำหนด Component เป็นหน้าแรกที่จะถูกแสดงขึ้นมา เราตั้งชื่อว่า `HomePage`

1. สังเกต property `navigationOptions` ที่กำหนดเป็น object `{ title: 'My App', }` จะถูกใช้กับส่วนหัวของ page นั้นๆ 
2. สังเกต method ชื่อ `openPageTwo()` ที่เรียกใช้คำสั่ง `this.props.navigation.navigate('Detail');` เป็นคำสั่งที่จะไปเรียกดูรายชื่อที่กำหนดไว้ใน `createStackNavigator()` ในไฟล์ `App.js`

```javascript

...

export default class HomePage extends Component {

    static navigationOptions = {
        title: 'My App',
    };
    
      constructor(props) {
        super(props);
    
        this.state = {
          loading: true
        };
      }
    
      openPageTwo = () => {
        this.props.navigation.navigate('Detail');
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
            <Button block onPress={this.openPageTwo}>
                <Text>เปิดหน้า 2</Text>
            </Button>    
        );
      }
}

const styles = StyleSheet.create({})
```

### pages/DetailPage.js

หน้าที่ 2 ที่เราจะเปิดขึ้นมาในตัวอย่างนี้ สังเกตว่าเรายังมีการกำหนดค่า `navigationOptions` เหมือนกับหน้าแรก เพื่อใช้แสดงเป็นส่วนหัวของ header

```javascript

...

export default class DetailPage extends Component {

    static navigationOptions = {
        title: 'Page 2',
    };
    
      constructor(props) {
        super(props);
      }
    
      render() {
        
        return (
            <Text>Page 2</Text>  
        );
      }
}

const styles = StyleSheet.create({})
```

