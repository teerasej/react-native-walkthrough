

# 3. สร้าง UI ของ Home Page

เขียน UI Component ขึ้นมาในส่วน `return statement`

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
              <Input placeholder="Money" keyboardType="numeric"
              />
            </Item>
          </Form>
          <Button block>
            <Text>Calculate</Text>
          </Button>
          <View>
            <Text>0</Text>
          </View>
        </Content>
      </Container>
    );
  }
```