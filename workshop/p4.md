
# Action Buttton

- [การตรวจจับการ Touch โดย React Native](https://facebook.github.io/react-native/docs/handling-touches)
- [Button ของ NativeBase](http://docs.nativebase.io/Components.html#button-def-headref)

```javascript
import { Button } from 'native-base';

render(){
    return (
        <Container >
            <Header>
            <Body>
                <Title>My App</Title>
            </Body>
            </Header>
            <Content>
            <Button block>
                <Text>Hello</Text>
            </Button>
            </Content>
        </Container>
    );
}
```

## Event

เราสามารถเขียน function แบบ inline ก็ได้

```javascript
render(){
    return (
        <Container >
            <Header>
            <Body>
                <Title>My App</Title>
            </Body>
            </Header>
            <Content>
            <Button block onPress={() {
                // do something
            }}>
                <Text>Hello</Text>
            </Button>
            </Content>
        </Container>
    );
}
```

หรือจะใช้ method ของ class ก็ได้

```javascript

doSomething() {
    // do something
}

render(){
    return (
        <Container >
            <Header>
            <Body>
                <Title>My App</Title>
            </Body>
            </Header>
            <Content>
            <Button block onPress={this.doSomething}>
                <Text>Hello</Text>
            </Button>
            </Content>
        </Container>
    );
}
```

ในบาง component ที่รับค่ามา เช่น `<Input>` ตัว event จะรับค่ามาใช้งานได้ และเราสามารถส่งต่อให้ method ได้เช่นกัน

```javascript

updateUsernameValue(text){
    this.setState({
        username: text
    });
}

<Input onChangeText={(text) => this.updateUsernameValue(text)}>

```
