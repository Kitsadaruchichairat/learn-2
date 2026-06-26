># DevOps คือ?

> DevOps (Development + Operations) คือแนวคิดและวิธีการทำงานที่รวมการทำงานของทีม Developer (Dev) กับ ทีมดูแลระบบ (Operations / Ops) ให้ร่วมกันพัฒนา ทดสอบ Deploy และดูแล Software ได้รวดเร็วและมีประสิทธิภาพมากขึ้น


### ปัญหาก่อนมี DevOps

> รูปแบบเก่า
```
Developer

เขียน Code

↓

ส่งให้ Ops

↓

Ops Deploy

↓

เกิดปัญหา

```
>ปัญหา

>- Deploy ช้า
>- Dev กับ Server ไม่เหมือนกัน
>- แก้ปัญหายาก
>- ทำงาน Manual เยอะ

>### DevOps ทำอะไร?

>ทำให้ Software Lifecycle เป็นระบบอัตโนมัติ
```
Code
 |
 ↓
Git
 |
 ↓
Build
 |
 ↓
Test
 |
 ↓
Deploy
 |
 ↓
Monitor
```

>### สิ่งสำคัญใน DevOps

>#### 1. CI/CD (Continuous Integration / Continuous Delivery)

>#### CI คือการตรวจสอบ Code อัตโนมัติ

>เช่น 

```
 Developer Push Code
↓

ระบบทำ

ตรวจ Code
Run Test
Build

```

>#### CD

>คือการนำ Code ขึ้น Production อัตโนมัติ

>ตัวอย่าง

```
Test ผ่าน

↓

Deploy Server

↓

ผู้ใช้ใช้งาน
```

>#### 2.Automation

>ลดงานที่ต้องทำด้วยมือ

>ก่อน
```
SSH เข้า Server

Upload File

Restart App
```

>หลัง
```
git push

↓

ระบบ Deploy อัตโนมัติ
```

>#### 3 Infrastructure as Code (IaC)

>คือการเขียน Infrastructure เป็น Code

>เช่น แทนที่จะสร้าง Server เอง 

```YAML
server:
  cpu: 2
  ram: 4GB
```

>แล้วระบบสร้างให้ 

>เครื่องมือ
>- Terraform
>- Ansible

>#### 4 Container

>ทำให้ Application ทำงานเหมือนกันทุกที่

> เช่น Docker

```
Application

+

Library

+

Environment
```
>เป็น Container เดียว

>#### 5 Monitoring

> คือการติดตามสถานะและประสิทธิภาพของระบบ

>#### เช่น
>- CPU
>- RAM
>- Error
>- Response Time

>- Prometheus
>- Grafana

> ### เครื่องมือ DevOps ที่เจอบ่อย

| งาน              | เครื่องมือ              |
| ---------------- | ----------------------- |
| เก็บ Code        | Git, GitHub             |
| CI/CD            | GitHub Actions, Jenkins |
| Container        | Docker                  |
| จัดการ Container | Kubernetes              |
| Cloud            | AWS, Azure, GCP         |
| Monitoring       | Grafana, Prometheus     |

>สรุปสั้น ๆคือ

```
Dev = สร้าง Software
Ops = ดูแล Software
DevOps = ทำให้ทั้งสองฝั่งทำงานเป็นระบบเดียวกัน
```

># Unit Test คืออะไร?

>Unit Test คือการทดสอบโปรแกรมในส่วนที่เล็กที่สุด (Unit) เช่น Function, Method หรือ Component เพื่อเช็กว่าการทำงานแต่ละส่วนถูกต้องตามที่ออกแบบไว้

>### ทำไมต้องมี Unit Test?

>ใช้เพื่อ
>- ลด Bug
>- ตรวจสอบว่า Code ยังทำงานหลังแก้ไข
>- ป้องกัน Bug เดิมกลับมา (Regression)
>- ทำให้ Refactor Code ได้มั่นใจขึ้น

>### Unit Test ทดสอบอะไร?

>เช่นมี Function 
```JavaScript
function add(a,b){
 return a+b;
}
```

>Unit Test
```Java Script
test(
"should add numbers",
()=>{

expect(
 add(2,3)
)
.toBe(5)

})
```

> จะเช็คว่า 2 + 3 = 5 หรือไหม


>### หลักการ AAA ของ Unit Test
>นิยมใช้รูปแบบ

>1. Arrange เตรียมข้อมูล

``` JavaScript 
const user = {
 name:"Kit"
}
```

>2. Act  เรียก Function ที่ต้องการทดสอบ

```JavaScript 
const result =
getUserName(user)
```

>3. Assert ตรวจผลลัพธ์ว่าใช่หรือไม่

```JavaScript 
expect(result)
.toBe("Kit")
```

>### Unit Test ต่างกับ Test อื่นยังไง?

| Test             | ทดสอบอะไร                      |
| ---------------- | ------------------------------ |
| Unit Test        | Function เล็ก ๆ                |
| Integration Test | หลายระบบทำงานร่วมกัน           |
| E2E Test         | ทดสอบตั้งแต่ User ถึง Database |

> ตัวอย่าง
>#### Unit Test 
> ##### ทําการ ตรวจ Function Login

>#### Integration Test
>##### Integration Test คือการทดสอบการทำงานร่วมกันของหลายส่วนในระบบเพื่อดูว่าแต่ละ Module สามารถเชื่อมต่อและส่งข้อมูลหากันได้ถูกต้องหรือไม่

>#### E2E Test (End-to-End Test)
>#####คือการทดสอบระบบตั้งแต่ต้นจนจบโดยจำลองการใช้งานเหมือนผู้ใช้จริง เป้าหมายคือ ตรวจสอบว่า ระบบทั้งหมดทำงานร่วมกันได้จริงหรือไม่


>### เครื่องมือ Unit Test ที่นิยม

>JavaScript / TypeScript
>- Jest
>- Vitest

>Python
>- pytest

>Java
>- JUnit


>### Unit Test ใน DevOps / CI-CD
>Flow

```
Developer

↓

git push
(ส่ง Code ขึ้น  Repository)

↓

CI Pipeline เริ่มทำงาน

↓

Install Dependency
(ติดตั้ง Library)

↓

Lint / Code Check
(ตรวจ Code)

↓

Run Unit Test
(ทดสอบ Function)

↓

Test ผ่าน ?

↓

Build Application
(สร้างไฟล์สำหรับ Production)

↓

Deploy

↓

Production Server

ถ้า Test ไม่ผ่าน หยุด Deploy
```

> ### Unit Test ที่ดีควรเป็นแบบไหน?
>-  รันเร็ว
>-  ไม่พึ่ง Database จริง
>-  รันกี่ครั้งผลเหมือนเดิม
>-  ทดสอบแค่จุดเดียว

> ### Mock คือ การ ใช้แทนของจริง เช่น 
> ไม่อยากเรียก Database จริง แทนด้วย

```Javascript 
const fakeDatabase = {
 user:"Kit"
}
```
>เพื่อทดสอบ Logic


> # TDD (Test-Driven Development) คืออะไร?

>คือแนวทางการพัฒนา Software ที่ให้ เขียน Test ก่อน แล้วค่อยเขียน Code จริง

>ปกติแล้ว การพัฒนาแบบปกติ จะ เขียนโค้ดเสร็จแล้วค่อย Test

>TDD จะเป็น

```
เขียน Test

↓

เขียน Code

↓

ปรับปรุง Code
```


> หลักการของ TDD มีวงจรสำคัญ 3 ขั้นตอน คือ Red ,Green และ  Refactor


> 1. Red คือ  เขียน Test ก่อน และ Test ต้อง Fail


> 2. Green คือ  เขียน Code ให้น้อยที่สุด เพื่อให้ Test ผ่าน

> 3. Refactor คือ  ปรับปรุง Code โดย Test ต้องยังผ่านอยู่


> วงจร  
```
เขียน Test

↓

Fail

↓

เขียน Code

↓

Pass

↓

Refactor

↓

เขียน Test ใหม่
```
>วนซ้ำไปเรื่อย ๆ

>####  ข้อดีของ TDD
> 1. Bug น้อยลง  เพราะมี Test ตั้งแต่แรก

>2. Refactor ง่าย มี Test คอยตรวจ 

>3.  Design ดีขึ้น  เพราะต้องคิด API และ Function ก่อนเขียนจริง

>4. Documentation ทางอ้อม  เพราะ อ่าน Test ก็รู้ว่า Function ทำอะไร

> #### ข้อเสียของ TDD

>1. ใช้เวลามากขึ้นช่วงแรก เพราะ ต้องเขียน Test ก่อนเสมอ

>2. ไม่เหมาะกับ Prototype เร็ว ๆ เพราะ บางงานต้องการ Proof of Concept ก่อน

>3. ต้องมีวินัย เพราะ หลายทีมเริ่มทำแล้วเลิกกลางทาง

>### TDD vs Unit Test

| หัวข้อ       | Unit Test               | TDD                 |
| ------------ | ----------------------- | ------------------- |
| คืออะไร      | การทดสอบ                | วิธีพัฒนา           |
| เขียนเมื่อไร | ก่อนหรือหลัง Code ก็ได้ | เขียนก่อนเสมอ       |
| เป้าหมาย     | ตรวจสอบความถูกต้อง      | ออกแบบและพัฒนา Code |


>#  Test Double คืออะไร?
>Test Double คือวัตถุ ที่สร้างขึ้นมาแทนของจริงในระหว่างการทดสอบ 

> ใช้วัตถุปลอมแทน Database, API, Email Service หรือระบบภายนอก เพื่อให้ Unit Test ทดสอบเฉพาะ Logic ที่ต้องการ

>### ทำไมต้องใช้ Test Double?
>ถ้า Unit Test ใช้ของจริงทั้งหมด
>- ช้า
>- พึ่งพาระบบภายนอก
>- Test อาจ Fail เพราะ Database 

>### ประเภทของ Test Double แบ่งเป็น 5 ประเภทหลัก

>#### 1. Dummy 
>สร้างมาให้ครบ Parameter แต่ไม่ได้ใช้งานจริง

>#### 2.Stub
>คืนค่าที่กำหนดไว้ล่วงหน้า

>#### 3. Fake
>มี Logic ทำงานจริง แต่เป็นเวอร์ชันง่าย ๆ

>#### 4. Spy

>เก็บข้อมูลว่าถูกเรียกยังไง

>#### 5. Mock

>กำหนดพฤติกรรมและคาดหวังผลลัพธ์


>### Test Double กับ Unit Test

>Unit Test ที่ดีควร 

>- ไม่เรียก Database จริง
>- ไม่เรียก API จริง
>- ไม่ส่ง Email จริง


>#### แต่ควรใช้ Test Double แทน


>### นิยมใช้ร่วมกับ
>- Unit Test
>- TDD
>- Jest
>- Vitest



># OOP (Object-Oriented Programming) คืออะไร?
>คือแนวคิดการเขียนโปรแกรมโดยมองสิ่งต่าง ๆ เป็น Object  ที่มีข้อมูลและ
พฤติกรรม รวมอยู่ด้วยกัน

>เช่น รถยนต์

>ข้อมูล
>- สี
>- ยี่ห้อ
>- ความเร็ว

>พฤติกรรม
>- ขับ
>- เบรก
>- เลี้ยว


>## 4 หลักการสำคัญของ OOP

>### 1. Encapsulation
>การซ่อนรายละเอียดภายใน Object ป้องกันไม่ให้แก้ข้อมูลโดยตรง

>#### ข้อดี
>- ป้องกันข้อมูลเสียหาย
>- ควบคุมการเข้าถึงข้อมูล

>### 2. Inheritance
> การสืบทอดคุณสมบัติจาก Class แม่

>#### ข้อดี
>- ลด Code ซ้ำ
>- นำ Logic เดิมกลับมาใช้ได้

>### 3. Polymorphism
>Object หลายชนิดใช้ Method ชื่อเดียวกันได้

>#### ข้อดี
>- เขียน Code ยืดหยุ่น
>- ขยายระบบง่าย

>### 4. Abstraction
>ซ่อนความซับซ้อน แสดงเฉพาะสิ่งที่จำเป็น

>#### ข้อดี
>- ใช้งานง่าย
>- ลดความซับซ้อน


>## องค์ประกอบสำคัญ ของOOP

>### Class และ Object

>### Class คือ พิมพ์เขียว

```Javascript
class User {

  constructor(name){
    this.name = name;
  }

}
```

>### Object คือสิ่งที่สร้างจาก Class

```Javascript
const user1 =
new User("Kit");

const user2 =
new User("John");
```

>### Constructor เป็น Method พิเศษที่ทำงานตอนสร้าง Object

```Javascript
class User {

  constructor(name){

    this.name = name;

  }

}
```
>### this คือ Object ปัจจุบัน

```Javascript
class User {

  constructor(name){

    this.name = name;

  }

}
```

>### Access Modifier 
>ใช้กำหนดการเข้าถึงข้อมูล

| Modifier  | ความหมาย                  |
| --------- | ------------------------- |
| public    | ใช้ได้ทุกที่              |
| private   | ใช้ได้เฉพาะใน Class       |
| protected | ใช้ใน Class และ Class ลูก |

>ตัวอย่าง

```TypeScript
class User {

  private password;

}
```

>## ข้อดีของ OOP
>- จัดโครงสร้างโปรแกรมง่าย
>- ลด Code ซ้ำ
>- ดูแลระบบง่าย
>- ขยายระบบง่าย
>- เหมาะกับโปรเจกต์ขนาดกลาง-ใหญ่

>## ข้อเสียของ OOP
>- ซับซ้อนกว่าการเขียนแบบธรรมดา
>- มี Boilerplate Code มาก
>- บางงานเล็ก ๆ อาจไม่จำเป็น

># Typescript & Callback

>## TypeScript คืออะไร? 
>TypeScript (TS) คือ JavaScript ที่เพิ่มระบบ Type System เข้ามา

>### ปัญหาของ JavaScript
> JavaScript เป็น Dynamic Type รันได้ แต่บางครั้งทำให้เกิด Bug ตอน Runtime

```JavaScript
let age = 18;

age = "hello";
```

>### TypeScript แก้ปัญหายังไง?
>โดย กำหนดชนิดข้อมูลให้ชัดเจน เพื่อป้องกัน Bug

>## Type หรือ ชนิดของข้อมูล ที่ใช้บ่อย

>### String

```TypeScript
let name: string = "Kit";
```

>### Number

```TypeScript
let age: number = 20;
```

>### Boolean

```TypeScript
let isLogin: boolean = true;
```
>### Array

```TypeScript
let scores: number[] = [10,20,30];
```

>### Function Type
>กำหนดชนิดข้อมูลของ Parameter และ Return

```TypeScript
function add(
  a: number,
  b: number
): number {

  return a + b;

}
```

>### Interface
>ใช้กำหนดโครงสร้าง Object

```TypeScript
interface User {

  id: number;

  name: string;

  email: string;

}
```

>### Type Alias
> คล้าย Interface

 ```TypeScript
type User = {

  id: number;

  name: string;

};
 ```

>### Type Alias กับ Interface ต่างยังไง
 
| หัวข้อ | Interface | Type Alias |
|---------|----------|------------|
| การประกาศชื่อซ้ำ | ทำได้ ( รวมเป็น Object เดียวกัน) | ทำไม่ได้ |
| ความยืดหยุ่น | เหมาะกับ Object เป็นหลัก | ยืดหยุ่นกว่า |
| การสืบทอด | ใช้ `extends` | ใช้ `&` (Intersection Type) |




>### Array Type

```TypeScript
const numbers: number[] = [
  1,
  2,
  3
];
```
>หรือ

```TypeScript
const numbers: Array<number> = [
  1,
  2,
  3
];
```

>### Object Type 

```TypeScript
const user: {
  name: string;
  age: number;
} = {
  name: "Kit",
  age: 20
};
```

>### Generic
>สร้าง Type ที่ยืดหยุ่น

```TypeScript
function identity<T>(
  value: T
): T {

  return value;

}
```
>เวลาใช้งาน

```TypeScript
identity<string>("Hello");

identity<number>(123);
```

>## ข้อดีของ TypeScript
>- ลด Bug
>- Code อ่านง่าย
>- IDE ช่วยแนะนำได้ดี
>- Refactor ง่าย
>- เหมาะกับโปรเจกต์ใหญ่

>## Callback คืออะไร?
>Callback คือ Function ที่ส่งเข้าไปเป็น Argument ของ Function อื่น เพื่อให้ถูกเรียกในภายหลัง

>

```TypeScript
function sayHello() {

  console.log("Hello");

}

function execute(
  callback
){

  callback();

}

execute(sayHello);
```
>จะได้ Hello 

>### ทำไมต้องมี Callback?
>เพราะ JavaScript มีงานที่ใช้เวลา เราไม่อยากให้โปรแกรมหยุดรอ  
> ใช้ในงาน Asynchronous เช่น
>- API
>- Database
>- File System
>- Timer

>### Callback Hell คืออะไร?
>เมื่อ Callback ซ้อนกันหลายชั้น จะเกิดปัญหาคือ อ่านยาก, Debug ยาก, ดูแลยาก

```TypeScript
login(() => {

  getUser(() => {

    getPosts(() => {

      getComments(() => {

      });

    });

  });

});
```

>### Promise แก้ Callback Hell

```TypeScript
login()
  .then(getUser)
  .then(getPosts)
  .then(getComments);
```

>### Promise คืออะไร?
>Promise คือ Object ใน JavaScript ที่ใช้แทน ผลลัพธ์ของงานที่ยังไม่เสร็จ งานที่ใช้เวลา

>### Async/Await แก้อีกขั้น

```TypeScript
async function run(){

  const user =
    await getUser();

  const posts =
    await getPosts();

}
```
>### ความสัมพันธ์
```
Callback

↓

Promise

↓

Async / Await
```
>ทั้งหมดใช้แก้ปัญหาเดียวกัน คือ งานที่ใช้เวลานาน (Asynchronous)