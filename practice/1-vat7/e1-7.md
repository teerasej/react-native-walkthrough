# เสร็จสมบูรณ์

```js
import React from 'react';
import { StyleSheet, View } from 'react-native';
import {
  Card,
  CardItem,
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
      result: 0,
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



  calculate = (text) => {

    let money = parseInt(text);
    let finalResult = money * 107/100;

    if(isNaN(finalResult)){
      finalResult = 0;
    }

    this.setState({
      result: finalResult
    });
  }


  render() {

    if (this.state.loading) {
      return <Expo.AppLoading />;
    }

    return (
      <Container>
        <Header>
          <Body>
            <Title>Vat 7</Title>
          </Body>
        </Header>
        <Content>
          <Form style={styles.formBox}>
            <Item>
              <Input placeholder="Money" keyboardType="numeric" onChangeText={text => this.calculate(text)}/>
            </Item>
          </Form>
          {/* <Button block onPress={this.calculate}>
            <Text>Calculate</Text>
          </Button> */}
          <View style={styles.resultBox}>
            <Text style={styles.resultText}>{this.state.result}</Text>
          </View>
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
  formBox: {
    padd
  },
  content: {
    
  },
  resultBox: {
    height: 300,
    backgroundColor: 'yellow',
    justifyContent: 'center',
    alignItems: 'center',
  },
  resultText: {
    fontSize: 60
  }
});

```