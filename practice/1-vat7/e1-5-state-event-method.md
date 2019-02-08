# 5. ใช้งาน State, Event และ method

เราจะเริ่มมีการเรียกใช้ method ชื่อ `this.setState({})` และ property ชื่อ `this.state`

```js
this.setState({});
this.state;
```
โดย `this.state` และเป็น object พิเศษที่เราจะเก็บ และเรียกใช้ค่าตัวแปรระหว่าง component ต่างๆ ใน class นี้

## 1. เรียกใช้งาน setState กับ `onChangeText` event ของ `<Input/>`

`<Input>` มี event ชื่อ `onChangeText` ซึ่งเราสามารถกำหนด function ให้กับมันได้ 

```html
<Input placeholder="Money" 
    keyboardType="numeric" 
    onChangeText={text => this.setState({money: text})}
/>
```

ในที่นี้ function รับตัวแปรเข้ามาชืื่อ `text` และเรากำหนดให้กับค่า `{ money: }`

## 2. สร้าง method ที่จะทำงานเมื่อปุ่มถูกกด

จากนั้นเราจะเขียน method ขึ้นมาชื่อ `calculate` เพื่อใช้คำนวนราคาที่บวก Vat 7 แล้ว ตอนกดปุ่ม 

```js
calculate = () => {

    let money = parseInt(this.state.money);
    let finalResult = money * 107/100;

    if(isNaN(finalResult)){
      finalResult = 0;
    }

    console.log(finalResult);

}
```

## 3. นำ method ไปใช้กับ `onPress` event ของ `<Button/>`

ทีนี้ให้ลองเรียกใช้ method `calculate()` ผ่าน event `onPress` ของปุ่มดู

```html
<Button block onPress={this.calculate}>
    <Text>Calculate</Text>
</Button>
```

## 4. สร้าง property ของ state สำหรับแสดงค่าตัวแปร

เราจะเพิ่ม **proprety** ชื่อ `result` ให้กับ `this.state` ใน constructor

เพื่อใช้ใน component ของเรา

```js
constructor(props){
    super(props);

    this.state = {
      result: 0,
      loading: true
    };
  }
```

## 5. นำ this.state.result มาแสดงใน Component 


เราจะนำค่า `this.state.result` มาแสดงใน Template 

```js
<View style={styles.resultBox}>
    <Text style={styles.resultText}>        
        {this.state.result}
    </Text>
</View>
```

## 6. กำหนดผลลัพธ์ให้กับ this.state.result

โดยในที่นี้เรากำหนดค่าให้กับ property `result` ใหม่

```js
calculate = () => {

    let money = parseInt(this.state.money);
    let finalResult = money * 107/100;

    if(isNaN(finalResult)){
        finalResult = 0;
    }

    this.setState({
        result: finalResult
    });
}
```



