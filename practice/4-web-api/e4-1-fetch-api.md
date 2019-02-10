
# ติดต่อกับ Web API และดึงข้อมูลมาใช้งาน


## Web API ตัวอย่าง

เราจะใช้ Web API แบบ public เพื่อแสดงข้อมูลในแอพพลิเคชั่นของเรา

- [https://randomuser.me/](https://randomuser.me/)

## 1. เราจะเขียนคำสั่งเรียกใช้ `fetch()`

เปิดไฟล์ `pages/home.page.js`

เราจะเพิ่มคำสั่ง `componentDidMount()` ซึ่งเป็น life cycle method ตัวหนึ่งที่จะถูกเรียกใข้งาน หลังจากที่ตัว component อยู่ในระบบเรียบร้อยแล้ว 

```js
async componentDidMount() {

    let response = await fetch("https://randomuser.me/api/?results=20");
    let json = await response.json();

    console.log('JSON here',json.results);

}
```
ทดสอบการทำงาน จะเห็นว่ามีข้อมูลแสดงขึ้นมาใน log เป็น JSON 

### อ้างอิง

- React native life cycle method: [`componentDidMount()`](https://reactjs.org/docs/react-component.html#componentdidmount)


## 2. ปรับให้ List ใช้ข้อมูล array จาก State แทน

เนื่องจากข้อมูลที่ List ใช้จะมีการเปลี่ยนแปลงอยู่ตลอดเวลาที่มีการติดต่อกับ Web API 
เราจึงเลือกให้ List ดึงข้อมูลจาก State แทน

เริ่มจากกำหนดให้ State มี properties ชื่อ `items` แทน 

```js
    constructor(props) {
        super(props);

        this.state = {
            items: [],
            loading: true
        };
    }
```

จากนั้น ในขั้นตอนที่เราได้ข้อมูลมาจาก Web API เราก็จะกำหนดค่าผ่าน `setState()`

```js
async componentDidMount() {

    let response = await fetch("https://randomuser.me/api/?results=20");
    let json = await response.json();

    console.log('JSON here',json.results);

    this.setState({
        items: json.results
    });

}
```

และแน่นอน เนื่องจาก object ของ user ที่เอามาวนลูปแสดงใน List เปลี่ยนโครงสร้าง เราก็ต้องมาปรับใช้งานใหม่

```js
return (

    <List
        dataArray={this.state.items}
        renderRow={item => {

            console.log('item', item);

            return (
                <ListItem thumbnail onPress={() => this.itemSelected(item)}>
                    <Left>
                        <Thumbnail square source={{ uri: item.picture.large }} />
                    </Left>
                    <Body>
                        <Text>{item.name.first} {item.name.last}</Text>
                        <Text note>{item.phone}</Text>
                    </Body>
                </ListItem>
            )s
        }}
    />

);
```

### 3. อัพเดตการดึงข้อมูลในหน้า Detail 

และด้วยข้อมูลที่ส่งมายังหน้า detail มีโครงสร้างปรับใหม่ เราจึงต้องเรียกข้อมูลแบบใหม่กัน 

```js
static navigationOptions = ({ navigation }) => {
    return {
      title: navigation.getParam('name').first + ' ' + navigation.getParam('name').last,
    };
};
```

ส่วนของ method render ก็ต้องปรับเช่นกัน

```js
render() {
    let data = this.props.navigation.state.params;
    console.log(data);

    return (
      <View style={styles.container}>
        <Image
          style={{ width: 200, height: 200 }}
          source={{
            uri:
              data.picture.large
          }}
        />
        <Button block style={styles.button} onPress={this.makeCall}>
          <Text>
            Call {data.phone}
          </Text>
        </Button>
      </View>
    )
  }
```

ทดสอบแอพพลิเคชั่น เราจะเห็นว่ามีข้อมูลจาก Web API แสดงขึ้นมาแทนแล้ว