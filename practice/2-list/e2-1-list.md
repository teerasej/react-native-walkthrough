
# เตรียมพร้อม Project

## 1. ติดตั้ง Package dependencies

จากไฟล์ **e2.zip** ให้แตกไฟล์ และเปิดโปรเจคขึ้่นมาใน Visual Studio Code

จากนั้นให้รันคำสั่งใน terminal ดังนี้

```powershell
npm i
```

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