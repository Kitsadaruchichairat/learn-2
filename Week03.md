># เก็บ password ยังไงให้ปลอดภัย

>### หลักการสําคัญคือ
>- ห้ามเก็บ password เป็นตัวอักษรปกติที่สามารถอ่านได้ (Plaintext)
>- ต้องเก็บเป็นค่า HASH ที่ไม่สามารถอ่านได้และกลับไปเป็นแบบเดิมไม่ได้่

>#### สิ่งที่ห้ามทํา
> #### 1. เก็บ password เป็นตัวอักษรปกติ (Plaintext)

> ตัวอย่าง
>#### Database

| id | username | password |
| --- | --- | --- |
| 1 | Kit | 123456 |

ถ้าDatabase หลุดออกไปสามารถเห็นได้ทันที
```
username: Kit
password: 123456
```
> #### 2. เข้ารหัส Password ด้วย Encryption ธรรมดา 
> ตัวอย่าง

```
password123

↓

AES Encryption

↓

8F9A7BC92....
```

>#### สาเหตุที่ไม่ปลอดภัยเพราะว่า สามารถถอดรหัสกลับมาเป็น password เดิมได้ ถ้า Key หลุด

```

Encrypted Text
        |
        |
     Secret Key
        |
        ↓
Original Password

```

> #### วิธีที่ปลอดภัยคือการเก็บ password เป็นค่า Hash

>#### กระบวนการ ของpassword เป็นค่า Hash คือ
```
password
|
|
Hash Algorithm
|
|
Hash Value
|
|
Database
```

>  ตัวอย่าง

> User สมัคร
```
123456
```

> System ทําการ Hash
```
bcrypt()

↓

$2b$12$A8s92jdksl.....
```
> Database เก็บ
```
$2b$12$A8s92jdksl.....
```
> #### bcrypt คือ เครื่องมือที่เอา Password ของผู้ใช้มาแปลงเป็นค่า Hash ที่ไม่สามารถย้อนกลับเป็น Password เดิมได้

> #### 3. Hash 

> คุณสมบัติของ Hash มี
  1. ONE-WAY: ไม่สามารถย้อนกลับไปเป็นข้อมูลเดิมได้
  2. ข้อมูลที่เหมือนกันจะได้ Hash ที่เหมือนกันเสมอ

> #### 4. Salt คืออะไร?
> Salt คือ ค่าที่สุ่มเพิ่มเข้าไปใน Password ก่อนที่จะHash เพื่อเพิ่มความปลอดภัย
> เข่น 
```
Password123456 + 9e6i5X
```
> เป็น 
```
password123X92A8Z
```

> ตัวอย่าง
```
User 1:

password123

salt=A8D9

hash=xrsr
```
```
User 2:

password123

salt=92KA

hash=ystst
```
> (ถ้า password เหมือนกัน แต่ salt ไม่เหมือนกัน hash จะไม่เหมือนกัน)


> #### 5. ค่า Cost Factor คืออะไร?
> bcrypt มีค่า Cost Factor ที่บอกว่าต้องใช้เวลานานแค่ไหนในการสร้าง Hash ยิ่งค่า Cost Factor สูงยิ่งปลอดภัยแต่ก็ต้องใช้เวลามากขึ้นในการสร้าง Hash
```
bcrypt(password, 12)
```
>เลข 12 คือ จํานวนรอบที่คํานวณ  
>ที่นิยมปัจจุบันคือ 10-12

> #### 6. Argon2 คืออะไร?
> ปัจจุบันระบบใหม่หลายแห่งนิยม


>Argon2id

>ข้อดี
>- ป้องกันGPU Attack ได้ดี
>- ใช้ Memory สูง ทําให้ใช้ทรัพยากรในการคำนวณมากขึ้น ทำให้การเดา Password จำนวนมากทำได้ช้าลง
>- ปลอดภัยมากกว่า bcrypt ในบางกรณี

> ตัวอย่าง
```
argon2id(
 password,
 salt
)
```
> เหมาะกับ
>- Banking
>- Enterprise
>- Saas (Software-as-a-Service) คือรูปแบบการให้บริการซอฟต์แวร์ผ่านอินเทอร์เน็ต โดยประมวลผลและเก็บข้อมูลไว้บนคลาวด์ Cloud

> #### เพิ่มเติม 
>- ห้าม Log Pasword เพราะ Log อาจถูก ส่งไป Server,Backup หรือ Monitoring


# Encode / Encrypt / Hash คืออะไร มีแบบไหนบ้าง แล้วเหมาะกับใช้ทำอะไร

| ประเภท  | จุดประสงค์          | ย้อนกลับได้ไหม     | ใช้กับ                  |
| ------- | ------------------- | ------------------ | ----------------------- |
| Encode  | เปลี่ยนรูปแบบข้อมูล |  ได้              | ส่งข้อมูล / แปลง Format |
| Encrypt | ปกป้องข้อมูลลับ     |  ได้ (ต้องมี Key) | ความลับ / Security      |
| Hash    | ตรวจสอบข้อมูล       |  ไม่ได้           | Password / Integrity    |

> ### 1. Encode (การเข้ารหัสรูปแบบข้อมูล)
> คือ การเปลี่ยนข้อมูลจากรูปแบบหนึ่งไปอีกรูปแบบหนึ่ง เพื่อให้ระบบอื่นสามารถอ่านหรือส่งต่อได้
ไม่ได้ทำเพื่อความปลอดภัย สามารถ Decode กลับมาเป็นข้อมูลเดิมได้

> #### ทําไมต้อง Encode?  
>เพราะ บางข้อมูลไม่สามารถส่งต่อได้ ต้องแปลงให้อยู่ในรูปText เช่น
> - Binary file
> - รูปภาพ
> - Token
> - URL

>### ตัวอย่าง Encode ยอดนิยม

> #### 1. Base64 นิยมมากใน Web Application ใช้กับ
    
    - JWT (JSON Web Tokens)
    - image 
    - API

> ##### ตัวอย่าง
```Javascript
const text = "Hello";

const encoded =
Buffer
.from(text)
.toString("base64");


console.log(encoded);
```

>ผลลัพธ์ :   SGVsbG8=

>##### Decode
```Javascript
const decoded =
Buffer
.from(
"SGVsbG8=",
"base64"
)
.toString();


console.log(decoded);
```
>ผลลัพธ์ :   Hello

> #### 2. URL Encoding ใช้กับ URL
> เช่น ข้อมูล 
```
hello world
```

กลายเป็น
```
hello%20world
```

ใช้กับ
```
https://example.com/search?q=hello%20world
```


```javascript
encodeURIComponent(
"hello world"
);
```
>ผลลัพธ์ : hello%20world


> #### 3. Unicode Encoding ใช้แทนตัวอักษรหลายภาษา
>เช่น 

```
ต
```

เก็บเป็น
```
Unicode Code Point
```
> ใช้กับ 
> - ภาษาไทย
> - Emoji
> - ภาษาต่างประเทศ

> ไม่เหมาะกับ Password หรือ ข้อมูลลับ เพราะสามารถ Decode กลับมาเป็นข้อมูลเดิมได้


> ### 2. Encryption (การเข้ารหัสเพื่อความปลอดภัย)

> Encryption คือการทำให้ข้อมูลอ่านไม่ได้ เพื่อป้องกันคนที่ไม่มีสิทธิ์เข้าถึง
ต้องมี
> - Algorithm
> - Key (Secret Key)
>##### Flow ของ Encryption
```
ข้อมูลจริง

   +
Encryption Key

        ↓

ข้อมูลที่ถูกเข้ารหัส
```

ถอดกลับ
```
Encrypted Data

+
Key

↓

ข้อมูลจริง
```

>ตัวอย่าง
> ข้อมูล เป็น credit_card = 1234-5678  
> Encrypt: A8F92KX91  
> คนที่ไม่มี Key เห็น: A8F92KX91 จะไม่สามารถอ่านออกเป็นข้อมูลจริงได้

> #### ประเภทหลัก Encryption มี 2 ประเภท
>##### 1. Symmetric Encryption (การเข้ารหัสแบบสมมาตร)  
> - ใช้ Key เดียวกันทั้งเข้ารหัสและถอดรหัส 

>##### 2. Asymmetric Encryption 

>- ใช้ Key 2 ต้ว ตัวนึงใช้ Encrypt อีกตัวใช้ Decrypt 

```
Public Key

Private Key
```
> หลักการ:

>- Public Key: ใช้เข้ารหัส

>- Private Key: ใช้ถอดรหัส


> #### Encryption ควรใช้เมื่อไหร่?
>- ข้อมูลส่วนตัว
>- ข้อมูลทางการเงิน
>- File สําคัญ
>- API Secret
>- Network Communication

ไม่เหมาะกับ
>-  Password Storage   
>Password ไม่ควร Encrypt ควร Hash

> ### 3.Hashing

> Hash คือการสร้างค่าประจำตัวของข้อมูล   
> ข้อมูลเหมือนเดิม ได้ Hashเดิม แต่การ Hash กลับเป็น ข้อมูลจริง ทำไม่ได้

>##### Flow Hash
```
Password

     |
     |
   Hash

     |
     ↓

A82F92XXXXX
```

>ตัวอย่าง
```
hello123
```

Hash
```
a3f5b8....
```

>#### Algorithm Hash

>##### 1. SHA-256 นิยมมากใน
>> - Blockchain
>> - Digital Signature
>> - ตรวจไฟล์


>##### 2. SHA-3 ใหม่กว่า SHA-2 ใช้กับ
>>- Security System
>>- Cryptographic Application

>##### 3. bcrypt ออกแบบมาเพื่อ Password   
> คุณสมบัติ

>- มี Salt
>- ปรับความยากได้ 

> ใช้กับ
```
Password Storage
```

>##### Argon2 ปัจจุบันนิยมมาก 


> เหมาะกับ

>- ระบบ Login
>- Application ใหม่

> ข้อดี

>- กัน GPU Attack
>- ใช้ Memory สูง

>### Rainbow Table เกี่ยวกับ Hashing ยังไง?

>Rainbow Table คือวิธีโจมตี Hash โดยใช้ ตารางที่เตรียมค่า Password กับ Hash ไว้ล่วงหน้า เพื่อย้อนหาว่า Hash นั้นมาจาก Password อะไร

>เพราะ Hash ปกติย้อนกลับไม่ได้ แต่ Rainbow Table ใช้การ "เดาและเทียบค่า Hash" แทนการถอดรหัส


>ปัญหาของ Hash แบบธรรมดา

```
username: Kit

password_hash:

e10adc3949ba59abbe56e057f20f883e

```

>Server ไม่รู้ Password จริงแล้ว แต่ Hacker อาจลองทำแบบนี้
```
MD5(123456)

↓

e10adc3949ba59abbe56e057f20f883e
```
>ตรงกัน แปลว่า Hash นี้ = 123456


#### Rainbow Table ทำงานยังไง?

>โดยก่อนโจมตี Hacker สร้างตารางไว้ก่อน

| Password | Hash      |
| -------- | --------- |
| 123456   | e10adc... |
| password | 5f4dcc... |
| admin    | 21232f... |
| qwerty   | d8578e... |


>เวลาเจอ Hash เช่น e10adc3949...

>ค้นหาในตาราง เจอ 123456


>#### ทำไม bcrypt / Argon2 กัน Rainbow Table ได้?

>เพราะ
>1. มี Salt อัตโนมัติ
>2.  ช้าใช้เวลาคํานวณนาน (Slow Hash)


>##### Hashing ควรใช้เมื่อไหร่? 
>- Password
>- ตรวจสอบไฟล์
>- Digital Signature
>- Integrity Check

>ไม่เหมาะกับ

>- ต้องการถอดข้อมูลกลับ

>##### ตัวอย่างการใช้จริง

| ถ้าต้องการ          | ใช้     |
| ------------------- | ------- |
| เปลี่ยนรูปแบบข้อมูล | Encode  |
| ปิดบังข้อมูลลับ     | Encrypt |
| เก็บ Password       | Hash    |
| ตรวจไฟล์            | Hash    |
| ส่งข้อมูลผ่าน API   | Encode  |
| HTTPS               | Encrypt |



# Cryptography Algorithm ของ Symmetric & Asymmetric ยอดนิยมและยังปลอดภัยจนถึงปัจจุบัน

> Cryptography คือเทคนิคการปกป้องข้อมูล โดยทำให้ข้อมูลสามารถ อ่านได้เฉพาะผู้ที่มีสิทธิ์, ป้องกันการแก้ไขข้อมูล, ยืนยันตัวตน

> ##### Algorithm หลักแบ่งเป็น 2 ประเภท
```
- Symmetric Encryption
- Asymmetric Encryption
```

> #### 1. Symmetric Encryption ใช้ Key เดียวกัน สำหรับ:
>> Encrypt (เข้ารหัส)  
>> Decrypt (ถอดรหัส)

>Flow
```
ข้อมูลจริง
    |
    |
 Encrypt
    |
    ↓

ข้อมูลเข้ารหัส

    |
    |
 Decrypt
    |
    ↓

ข้อมูลจริง
```

>##### ข้อดี Symmetric
>- เร็วมาก
>- เหมาะกับข้อมูลขนาดใหญ่
>- ใช้ทรัพยากรน้อย

>##### ข้อเสีย Symmetric

>- ต้องแชร์ Key ระหว่างกัน
>- ถ้า Key หลุด ข้อมูลถูกถอดได้

>##### Algorithm Symmetric ที่นิยม

>##### 1. AES (Advanced Encryption Standard) เป็นมาตรฐานที่นิยมมากที่สุดในปัจจุบัน

>- ปัจจุบันนิยม AES-256

| Algorithm | Key     |
| --------- | ------- |
| AES-128   | 128 bit |
| AES-192   | 192 bit |
| AES-256   | 256 bit |

> นิยมใช้
>-  HTTPS/TLS
>- Database Encryption
>- File Encryption
>- Cloud Storage

> ตัวอย่าง AES
```javascript
const crypto = require("crypto");

const key = crypto.randomBytes(32);
const iv = crypto.randomBytes(16);


const cipher = crypto.createCipheriv(
    "aes-256-cbc",
    key,
    iv
);


let encrypted =
cipher.update(
    "Hello Security",
    "utf8",
    "hex"
);

encrypted += cipher.final("hex");


console.log(encrypted);
```

> ผลลัพธ์ a82fd91xxxxxx

> ##### 2. ChaCha20-Poly1305 เป็น Algorithm รุ่นใหม่ 

> นิยมใน

>-  TLS 1.3
>- Mobile Application
>- Mobile Application

>ข้อดี

>- ปลอดภัย
>- เร็ว
>- ทำงานดีบนอุปกรณ์ที่ไม่มี Hardware AES

> #### 2.Asymmetric Encryption มี 2 Key

```
Public Key
     |
     |
 Encrypt
     |
     ↓

ข้อมูลเข้ารหัส

     |
     |
Private Key
     |
     |
 Decrypt

```

>##### Public Key เปิดเผยได้

> ใช้
>- Encrypt
>- Verify Signaturec

>##### Private Key

> ใช้
>- Decrypt
>- Digital Signature

> ข้อดี
>- ไม่ต้องแชร์ Secret Key
>- เหมาะกับ Internet
>- ใช้สร้างความน่าเชื่อถือ

> ข้อเสีย
>- ช้ากว่า Symmetric

>####  Algorithm ที่นิยม

>1. RSA (Rivest–Shamir–Adleman) เป็น Algorithm ที่ใช้มานาน

>นิยมกับ
>- SSL Certificate
>- Digital Signature
>- Key Exchange

> Key ที่นิยม 
>- RSA-2048
>- RSA-3072
>- RSA-4096

> ตัวอย่าง 

```javascript
const crypto = require("crypto");


const keys =
crypto.generateKeyPairSync(
    "rsa",
    {
        modulusLength:2048
    }
);


const message =
"Secret Data";


const encrypted =
crypto.publicEncrypt(
    keys.publicKey,
    Buffer.from(message)
);


const decrypted =
crypto.privateDecrypt(
    keys.privateKey,
    encrypted
);


console.log(
    decrypted.toString()
);
```

> ผล Secret Data


> 2. ECC (Elliptic Curve Cryptography) เป็น Algorithm รุ่นใหม่กว่า RSA

> ข้อดี
>- Key เล็กกว่า
>- เร็วกว่า
>- ใช้ทรัพยากรน้อย

> นิยมใช้
>- HTTPS
>- Blockchain
>- Mobile

> ตัวอย่าง
```
ECDSA
ECDH
```

> ##### เปรียบเทียบ Symmetric vs Asymmetric

| หัวข้อ             | Symmetric              | Asymmetric                   |
| ------------------ | ---------------------- | ---------------------------- |
| Key                | 1 Key (ใช้ร่วมกัน)     | 2 Key (Public + Private)     |
| ความเร็ว           | เร็วมาก                | ช้ากว่า                      |
| ใช้กับ             | เข้ารหัสข้อมูลจำนวนมาก | แลกเปลี่ยน Key / ยืนยันตัวตน |
| Algorithm ตัวอย่าง | AES, ChaCha20-Poly1305 | RSA, ECC                     |
| ใช้ใน HTTPS        | เข้ารหัสข้อมูลจริง     | สร้างความปลอดภัยและแลก Key   |


> # JWT
> JWT (JSON Web Token) คือมาตรฐานการสร้าง Token สำหรับยืนยันตัวตน และส่งข้อมูลระหว่าง Client กับ Server ในรูปแบบ JSON

> นิยมใช้ใน
>- Web Application
>- Mobile Application
>- REST API
>- Microservices  

> โดย JWT ช่วยให้ Server รู้ว่า Request นี้มาจาก User คนไหน และ User มีสิทธิ์อะไร

>#### โครงสร้าง JWT 3 ส่วน 
```
Header.Payload.Signature
```
 >1. ##### Header บอกว่า Token ใช้ Algorithm อะไร
 
 >ตัวอย่าง

 ```JSON
{
  "alg": "HS256",
  "typ": "JWT"
}
 ```
 >2. ##### Payload  เก็บข้อมูล
 
 >ตัวอย่าง

 ```JSON
{
  "id": 123,
  "username": "Kit",
  "role": "admin",
  "exp": 1719999999
}
 ```

 >3.  Signature ส่วนตรวจสอบความถูกต้อง

 > สร้างจาก ผ่าน Algorithm

```
Header

+

Payload

+

Secret Key
```

>#### JWT Algorithm

>##### 1. HMAC (เป็น Symmetric) ใช้ Secret Key เดียว

```
HS256
HS384
HS512
```

>Flow

```
Sign
 ↓

Verify

Secret Key
```

>นิยมกับ
>- API
>- Web APP

>##### 2. RSA (เป็น Asymmetric) ใช้ Public Key กับ Private Key"

>เช่น RS256

> Flow

```
Sign

↓

Public Key

Verify
```
> นิยมกับ 
>- Enterprise
>- Microservices

>##### 3. ECC

>เช่น ES256

>ใช้กับ
>- Modern System
>- Cloud
 
>#### JWT เก็บที่ไหน?

> ##### Browser

> นิยมกับ HttpOnly Cookie

> ข้อดี
>- JavaScript อ่านไม่ได้
>- ลดความเสี่ยง XSS

>##### HttpOnly Cookie คือ? คือ Cookie ที่ถูกตั้งค่าให้ JavaScript ฝั่ง Browser ไม่สามารถเข้าถึงได้ เพื่อเพิ่มความปลอดภัยในการเก็บข้อมูลสำคัญ

> ##### LocalStorage

> เช่น

```Javascript
localStorage.setItem(
"token",
jwt
)
```

> ข้อเสีย 
>- เสี่ยง XSS

> #### JWT Security

> 1. กำหนด Expiration
> ไม่ควร  ไว้นาน เป็นวัน เดือน หรือ ปี 

>ควร 15 นาที - 1 ชั่วโมง 


### Authentication และ Authorization

> สองแนวคิดนี้ใช้ร่วมกับ JWT ในระบบ Login

#### Authentication (การยืนยันตัวตน)

>คือการตรวจสอบว่า "คุณคือใคร"  
>ระบบจะตรวจสอบข้อมูล เช่น:
> - Username / Password
> - Token
> - JWT

ตัวอย่าง:

```
User Login
username: Kit
password: 123456


Server ตรวจสอบแล้วพบว่า นี่คือ User Kit


= Authentication สำเร็จ

```

#### Authorization (การอนุญาตสิทธิ์)

>คือการตรวจสอบว่า "คุณทำอะไรได้บ้าง"  
>หลังจากรู้แล้วว่าเป็นใคร ระบบจะตรวจสอบสิทธิ์



> ##### ตัวอย่าง JWT
```JSON
{
 "user":"Kit",
 "role":"admin"
}
```

> #### สั้นๆคือ

```
Login = Authentication
Permission = Authorization
```

># RESTful Design คืออะไร?

>RESTful Design (Representational State Transfer) คือแนวทางการออกแบบ API ให้เป็นมาตรฐาน โดยใช้หลักการของ HTTP เพื่อให้ Client ติดต่อกับ Server ได้อย่างเป็นระบบ

>นิยมกับ
>- Web Application
>- Mobile Application
>- Microservices
>- Backend API

> #### แนวคิดหลัก 
>###### API ไม่ควรออกแบบตาม "คำสั่ง" แต่ควรออกแบบตาม "ทรัพยากร "

> ### Resource Design

> REST ใช้ Noun ไม่ใช้ Verb

> ตัวอย่างผิด
```
GET /getUsers
POST /createUser
DELETE /deleteUser
```
> ตัวอย่างถูก
```
GET /users

POST /users

DELETE /users/1
```


>#### หลักการของ REST 
> REST มีหลักการสําคัญ 6 ข้อ

>#### 1. Client - Server แยกหน้าที่กัน

>Frontend รับผิดชอบ
>- UI
>- User Interaction
>- แสดงผล

>Backend รับผิดชอบ
>- Business Logic
>- Database
>- Authentication

>ข้อดี
>- แก้ไขง่าย
>- Deploy แยกกันได้
>- Scale ง่าย

>#### 2. Stateless

>Server ไม่จําสถานะของ Client ทุก Request ต้องมีข้อมูลครบ

>ตัวอย่าง

 ```
 Request

GET /profile

Header:

Authorization:
Bearer JWT_TOKEN
```

>ทุกครั้งส่ง Token ไป Server ไม่ต้องจำ

>ข้อดี
>- รองรับผู้ใช้จำนวนมาก
>- Load Balance ง่าย



>#### 3. Cacheable

> Response สามารถ Cache ได้

>Cache  คือ การเก็บข้อมูลที่ถูกเรียกใช้บ่อย ๆ ไว้ชั่วคราว เพื่อให้การเข้าถึงครั้งต่อไป เร็วขึ้น และลดภาระของ Server

> เช่น

>Request    
```
GET /products
```

>Response
```
Cache-Control:
max-age=3600
```
>Browser หรือ CDN เก็บไว้

> ข้อดี
>- เร็วขึ้น
>- ลด Server Load

>#### 4. Uniform Interface การออกแบบ API ต้องเป็นมาตรฐานเดียวกัน

>ไม่ควร

```
GET /getUserData
GET /fetchProducts
POST /createNewUser
```

>ควร

```
GET /users

GET /products

POST /users
```
> ใช้ Resource เป็นคำนาม


>#### 5. Layered System Client ไม่จำเป็นต้องรู้ว่า Server ทำงานกี่ชั้น

> Layered System คือการออกแบบระบบให้แบ่งเป็นหลายชั้น (Layer) โดยแต่ละชั้นจะรู้จักเฉพาะชั้นที่อยู่ติดกัน

> Client จะไม่รู้ว่าเบื้องหลัง API มีอะไรบ้าง

> Client สนใจแค่
```
ส่ง Request
รับ Response
ไม่ได้สนใจว่า Server ทำงานยังไงข้างใน
```

>#### 6. Code on Demand (ไม่จําเป็น)

>Server สามารถส่ง Code ให้ Client ทำงานได้
>เช่น
>JavaScript
>แต่ปัจจุบันไม่ค่อยใช้

>#### HTTP Method ที่ใช้กับ REST

| Operation | HTTP      |
| --------- | --------- |
| สร้างข้อมูลใหม่    | POST      |
| ใช้ดึงข้อมูล      | GET       |
| แก้ไขข้อมูลทั้งหมด    | PUT|
| แก้บางส่วน    | PATCH |
| ลบข้อมูล    | DELETE    |


 
>### URL Design


>#### Collection รายการทั้งหมด
```
GET /users
```

>#### Specific Resource ข้อมูลตัวเดียว
```
GET /users/10
```

>#### Nested Resource 

> เช่น User มี  Order

```
GET /users/10/orders
```

>### Authentication ใน REST API
>นิยม JWT

># เปรียบเทียบการเขียน code แบบ Synchronous กับ Asynchronous

>### Synchronous (Sync) คืออะไร?

>คือ การทำงานแบบ ทีละขั้นตอนตามลำดับ คำสั่งถัดไปจะทำงานได้ก็ต่อเมื่อคำสั่งก่อนหน้าทำเสร็จแล้ว

>##### Flow
```
งาน A
 |
 | รอให้เสร็จ
 ↓
งาน B
 |
 | รอให้เสร็จ
 ↓
งาน C
```

>##### ข้อดี
>- เขียนง่าย
>- อ่าน Code ง่าย
>- Debug ง่าย
>- เหมาะกับงานที่ต้องทำตามลำดับ

> เช่น
>- คำนวณข้อมูล
>- ตรวจสอบข้อมูล
>- งานเล็ก ๆ

>##### ข้อเสีย 
>- Block การทำงาน ทำให้ช้า
>- รองรับ Request เยอะยาก

>### Asynchronous (Async) คืออะไร?

>คือการทำงานโดยไม่ต้องรอ เมื่อเจองานใช้เวลานาน ระบบสามารถทำงานอื่นต่อได้

>##### Flow
```
เริ่มงาน A

    |
    |
    ↓

รอ A ทำงาน

    |
    |
ทำงาน B ต่อ


A เสร็จ → กลับมาแจ้ง
```

> #### งานที่เหมาะ

| งาน            | ใช้           |
| -------------- | ------------- |
| คำนวณ CPU หนัก | Sync / Thread |
| อ่านไฟล์       | Async         |
| Database Query | Async         |
| API Request    | Async         |
| Upload File    | Async         |
| Network        | Async         |


> #### Async ไม่เท่ากับ Multi Thread

>Async
```
ไม่รอ จัดการงานที่ใช้เวลานาน
```

>Thread
```
สร้างหน่วยทำงานหลายตัว ทำงานพร้อมกัน 
```


># Thread คืออะไร?
>Thread (เธรด) คือ หน่วยการทำงานย่อยภายใน Process ที่ใช้ในการทำงานของโปรแกรม

```
Process = โปรแกรมที่กำลังทำงาน
Thread = งานย่อยที่อยู่ข้างในโปรแกรมนั้น
```

>เช่น 

```
Chrome.exe
(Process)

    |
    |
    +-- Thread 1
    |   แสดงหน้าเว็บ
    |
    +-- Thread 2
    |   โหลดรูป
    |
    +-- Thread 3
        เล่นวิดีโอ
```


>### Single Thread คืออะไร?
>คือการที่ มี Thread เดียวทำงาน 

>เช่น

```
Thread เดียว


งาน A

↓

งาน B

↓

งาน C

```
>จะทำทีละอย่าง

>### Multi Thread คืออะไร?
>คือการที่ มีหลาย Thread ที่ทำงานพร้อมกัน

>เช่น
```
Thread 1

งาน A


Thread 2

งาน B


Thread 3

งาน C
```
> สามารถทำหลายงานพร้อมกันได้


> ### ปัญหาของ Multi Thread

> 1. Race Condition
> คือหลาย Thread แก้ข้อมูลเดียวกัน

> 2.  Deadlock
> Thread รอกันเอง ไม่มีใครทำต่อ

>###  Thread Safety
>คือการเขียน Code ที่หลาย Thread ใช้ร่วมกันได้

>เช่นใช้
>- Lock
>- Mutex
>- Semaphore



# เพิ่มเติม 

## Nonce คืออะไร
>Nonce ย่อมาจาก Number used once คือ ค่าที่ถูกสร้างขึ้นมาเพื่อใช้เพียงครั้งเดียว (One-Time Value) แล้วไม่ควรนำกลับมาใช้ซ้ำ

> ### จุดประสงค์หลักคือ
>- ป้องกันการโจมตีแบบ Replay Attack
>- เพิ่มความปลอดภัยในการเข้ารหัส (Encryption)
>- ยืนยันว่าคำขอนี้เป็นคำขอใหม่จริง

> ### ทำไมต้องมี Nonce?
>สมมติ Login ด้วย 
``` 
Username: Kit

Password: 123456
```
>หาก Hacker ดักข้อมูลได้ อาจส่งข้อมูลเดิมซ้ำ Server อาจคิดว่าเป็นผู้ใช้จริง เรียกว่า

>Replay Attack คือการนำข้อมูลที่เคยส่งมาแล้ว ส่งซ้ำอีกครั้ง

>### Nonce ช่วยอย่างไร?
>Server จะสร้าง Nonce แล้ว ส่งให้ Client และ Client ส่งกลับพร้อมข้อมูล สุดท้าย Server ตรวจสอบ Nonce ถูกต้องไหม เคยใช้แล้วหรือยัง ถ้าเคยใช้แล้ว Reject ทันที

>### คุณสมบัติของ Nonce
>- สุ่ม 
>- ใช้ครั้งเดียว 
>- คาดเดาได้ยาก
>- หมดอายุเร็ว

>### Nonce ใช้ที่ไหนบ้าง?

>#### 1.Cryptography
>เช่น
>- AES-GCM
>- ChaCha20-Poly1305

>Nonce จะถูกใช้ร่วมกับ Key แม้จะเป็นข้อมูลเดิม แต่ถ้า Nonce ต่างกัน Ciphertext จะต่างกัน

>#### 2. JWT 
>JWT ปกติไม่มี Nonce แต่ระบบ Authentication บางระบบ จะมี Nonce เช่น
>- OAuth 2.0
>- OpenID Connect (OIDC)

>#### 3. CSP (Content Security Policy)

>เวลาเว็บโหลด Script Server อาจสร้าง Nonce Browser จะรันเฉพาะ Script ที่มี Nonce ตรงกัน ช่วยป้องกัน XSS (Cross-Site Scripting)

>#### 4.  Blockchain 
>Nonce คือค่าที่ Miner เปลี่ยนไปเรื่อย ๆ จนได้ Hash ที่ตรงตามเงื่อนไข ถ้าไม่ตรง เปลี่ยน Nonce ใหม่ แล้ว Hash ใหม่

>#### Nonce ต่างจาก Salt อย่างไร?

| หัวข้อ       | Nonce                                     | Salt                  |
| ------------ | ----------------------------------------- | --------------------- |
| ใช้กับ       | Encryption / Authentication               | Password Hash         |
| จุดประสงค์   | ป้องกัน Replay และทำให้ Ciphertext ไม่ซ้ำ | ป้องกัน Rainbow Table |
| ใช้ซ้ำได้ไหม | ไม่ควรใช้ซ้ำ                              | เก็บคู่กับ Hash ได้   |
| สุ่มหรือไม่  | สุ่ม                                      | สุ่ม                  |
