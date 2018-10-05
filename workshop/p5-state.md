
# State 

การใช้ State จะเริ่มจากการกำหนดค่าใน State ก่อน ส่วนใหญ่จะทำใน `constructor()` โดยกำหนดในรูปแบบของ Javascript object

```javascript
constructor(props){
    super(props);

    this.state = {
      result: 0,
      loading: true
    };
}
```

การทำให้ method `render()` ทำงานอีกครั้ง จะเกิดจากการใช้คำสั่ง `this.setState({})` และกำหนดค่าใหม่ลงไปใน property เดิม เช่น

```javascript
this.setState({
    result: 10
})
```
## ตัวอย่าง

```javascript
export default class App extends React.Component {
  constructor(props){
    super(props);

    this.state = {
      result: 0,
      loading: true
    };
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
            <Form>
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

```