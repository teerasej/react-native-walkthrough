
# 5. ทดสองใช้งาน Event และ Method ของ Input


## 1. สร้าง Method ใหม่

จากนั้นเราจะเขียน method ขึ้นมาชื่อ `calculateLive` เพื่อใช้คำนวนราคาที่บวก Vat 7 แล้ว ผ่านการเขียนข้อความลง `<Input>`

```js
calculateLive = (text) => {

    let money = parseInt(text);
    let finalResult = money * 107/100;

    if(isNaN(finalResult)){
      finalResult = 0;
    }

    this.setState({
        result: finalResult
    });

}
```

## 2. ซ่อนปุ่ม

```html
{/* <Button block onPress={this.calculate}>
<Text>Calculate</Text>
</Button> */}
```

## 3. เรียกใช้งาน `onChangeText` event ของ `<Input>`

```html
<Form style={styles.formBox}>
    <Item>
        <Input placeholder="Money" keyboardType="numeric" onChangeText={text => this.calculate(text)}/>
    </Item> 
</Form>
```
