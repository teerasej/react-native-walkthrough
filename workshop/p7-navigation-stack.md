
# Navigation Stack

## ติดตั้ง react-navigation

```
npm install --save react-navigation
```

## แยก Page Component อย่างชัดเจน

เราจะเริ่มต้นจาก 3 ไฟล์

### pages/HomePage.js

กำหนด Component เป็นหน้าแรกที่จะถูกแสดงขึ้นมา เราตั้งชื่อว่า `HomePage`

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

### App.js

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