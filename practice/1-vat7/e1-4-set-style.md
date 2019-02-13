# 4. กำหนด Style ให้กับ Component

ลงมาในส่วนของ StyleSheet ให้เขียนกำหนดชื่อ propreties และคุณสมบัติตามด้านล่าง

```js
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
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

นำ `styles` มากำหนดให้กับ Component ต่างๆ 

```js
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
              <Input placeholder="Money" keyboardType="numeric"/>
            </Item>
          </Form>
          <Button block>
            <Text>Calculate</Text>
          </Button>
          <View style={styles.resultBox}>
            <Text style={styles.resultText}>0</Text>
          </View>
        </Content>
      </Container>
    );
  }
```