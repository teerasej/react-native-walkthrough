
# ใช้งาน Event ของ ListItem

## 1. สร้าง method สำหรับกรณีที่เกิดการกดเลือก item ใน List

```js
  itemSelected = () => {
    console.log('ok');
  }
```

## 2. เรียกใช้งาน method กับ event `onPress` ใน List Item

```html
 <ListItem thumbnail onPress={this.itemSelected}>
```

ทดสอบกดใช้่งาน จะเห็นว่ามีคำว่า ok แสดงขึ้นมาใน log


## 3. กำหนดให้ส่งข้อมูลของ item กดเลือกเข้ามาใน method

```js
  itemSelected = (data) => {
    console.log('data:', data);
  }
```

และเขียน function ใหม่ใน event `onPress`

```html
 <ListItem thumbnail onPress={() => this.itemSelected(item)}>
```

ทดสอบกดใช้่งาน จะเห็นว่ามีคำว่ามี object ของ List Item ที่กดเลือก แสดงขึ้นมาใน log
