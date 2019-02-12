
# สร้างโครงหน้าของ Page

ทำการ import component มาจาก `nativebase`

```javascript
// ของที่ React ให้มา
import React from 'react';
// อย่าลืมลบ Text ออก เพราะจะไปซ้ำกับของ Nativebase
import { StyleSheet, View } from 'react-native';

import {
  Container,
  Header,
  Title,
  Content,
  Body,
  Icon,
  Text,
} from "native-base";

```

จากนั้นประกาศ component ในส่วน method `render()`

```javascript
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
          <Text>Hello</Text>
        </Content>
      </Container>
    );
  }
```

## Style

Style ใน Component จะอยู่ในรูปแบบของ JavaScript Object เราสามารถกำหนดให้กับ `style` attribute ของ Component ได้โดยตรง

### อ้างอิง

- [React Native's style](https://facebook.github.io/react-native/docs/style)
- [Layout](https://facebook.github.io/react-native/docs/flexbox)

```javascript
return (
      <Container>
        <Header>
          <Body>
            <Title>My App</Title>
          </Body>
        </Header>
        <Content style={styles.content}>
          <Text>Hello</Text>
        </Content>
      </Container>
    );


const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  content: {
    padding: 20
  }
});
```