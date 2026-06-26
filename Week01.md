
# Markdown คืออะไร? ![Logo9](https://miro.medium.com/0*9BC7CoIEGH5Bi351.png)
    Markdown เป็น Lighweight Markup Language ที่ใช้จัดFormatของPlain Text บน Document และแปลงเป็นHTML โดนที่Markdown มีนามสกลุไฟล์เป็น.md 

# การใช้Markdown

# 1.Headings 
    มี 6 แบบโดยเพิ่มจํานวน # ตามเลเวล Heading ที่ต้องการ ได้แก่
    1. # Heading 1
    2. ## Heading 2
    3. ### Heading 3
    4. #### Heading 4
    5. ##### Heading 5
    6. ###### Heading 6

# 2. Paragraphs (New Line)
    ถ้าเราต้องการเว้นบรรทัดให้ข้อความ เราจะต้องเคาะenterเว้นลง
    มาเป็นบรรทัดเปล่า 1 บรรทัด หรือกดspacebar2ครี้ง

# 3. Horizontal Line
    ใช้ --- เพื่อแบ่งเลเวล headerเพื่อทําเป็นเส้นคั่น ถ้าเหนือเส้นมีข้อความก็ต้องเว้นลรรทัดก่อนถึงจะมีเส้นนคั่นแสดง

***ตัวอย่าง***

---    

# 4. Text Styles 
    จะทำตัวเอียงและตัวหนา โดยใช้ _ หรือ * ครอบข้อความที่เราต้องการให้เอียง 
    และใช้ __ หรือ ** ครอบข้อความที่เราต้องการให้หนาแลถถ้าอยากได้ตัวหนาและเอียงพร้อมกันก็ใช้ ***หรือ ___ และถ้าอยากขีดค่าข้อความก็ใช้ ~~ ครอบข้อความ ช่น
_ตัวเอียง_  
__ตัวหนา__  
*ตัวเอียง*  
**ตัวหนา**  
***ตัวหนาและเอียง***  
___ตัวหนาและเอียง___  
~~ขีดค่าข้อความนี้น้า~~

# 5. Links
    ใช้ [ ] แสดงข้อความที่เราต้องการ คู่กับกับใส่ลิงก์ในวงเล็บ ( ) เพื่อทำการลิงก์
    เช่่น
    
[W3School](http://w3schools.com/git/git_install.asp?remote=github)

อีกตัวอย่าง [YouTube] | [Instagram]

[YouTube]: https://www.youtube.com/watch?v=JBAuRoIRAs8&list=RDldSl6agcUAI&index=21   
[Instagram]: https://www.instagram.com/

# 6.Images
    การแทรกรูปภาพของ Markdown จะใช้ Syntax คล้ายกับ Links เลย แต่เพิ่มเครื่องหมายตกใจ ไปข้างหน้า เช่น
![Logo2](https://docs.mikelopster.dev/img/mikelopster.webp)

# 7. Blockquotes
    การทำ Quote แค่ใส่ > หน้าข้อความเราที่ต้องการให้เป็น Quote เท่านั้น เช่น
> ติ๊กต็อกๆ
>
>>สวัสดีครับ
>>>ชื่ออะไรเอ่ย

# 8. Lists Unordered Lists
    ทําได้หลายแบบเลย เช่นใช้
    *,-,+ หรือ Ordered Lists ใช้ตัวเลข 1.2.3 อื่นๆ และ Nested Lists คือการสร้าง List ที่ซ้อนกัน ให้เราเคาะ Space เข้าไป 
- ซอส
- มายอง
+ ก้าสะบะละห้า
* ห้าห้าห้า 
+ มะเขือ
  + เทศ

1. อิ
8. อะ

    7. อุ
    9. น้
4. พ


# 9. Code & Code Block Code
    จะใช้เครื่องหมาย ` ครอบข้อความหรือโค้ดที่เราต้องการ เพื่อให้แสดงผลในรูปแบบของ Code เช่น
```
print("Hello World")
```

```python
print("Hello World") 
````
# 10. Task Lists
    การทำ Task List เราจะใช้ – [x] สำหรับ Checked ที่ Task นั้น ๆ และใช้ – [ ] สำหรับ Task ที่ไม่ได้ถูก Checked เช่น 

- [x] A  
- [ ]

# 11. Tables
    การทำตารางใน Markdown อาจจะต้องใช้จินตนาการนิดหน่อย โดยใช้เราคิดว่า | คือเส้นตารางแนวตั้ง และ — คือเส้นคั่นแนวนอนของหัวตาราง เช่น
#### วิธีหาเห็ดหูหนู

| ลำดับที่ | ช่องทางติดตาม | ลิงก์ของแต่ละช่องทาง |
| ---- | ---- | ---- |

| 1 | YouTube | https://www.youtube.com/ |




# gitคืออะไร ![Logo8](https://www.20i.com/blog/wp-content/uploads/2022/08/git-blog-header.png)
    git คือเครื่องมือที่ช่วยจัดการเวอร์ชั่นของโค้ด และสามารถใช้ทํางานร่วมกับคนอื่นและติดตามการเปลี่ยนแปลงและแก้ไข้ข้อผิดพลาดได้
    
# การดู version ของgit

* คําสั่งในการดูเวอร์ชั่นของgit
```
git -v,git --version
```
# วิธีการติดตั้ง git 
windows: สามารถ Dowload และติดตั้งได้เลย
    macOS: ถ้าใช้ Homebrew ก็ใช้ 
```
    brew install git ในterminalz
```
    Linux: เปิดตัวterminalและใช้คําสั่ง 
```
    sudo apt-get install git
```
# คําสั่งพื้นฐาน 
* git commit:ใช้บันทึกภาพรวมหรือประวัติการเปลี่ยแปลงของโค้ด
    
* git brach (ชื่อที่ต้องการตั้ง): ใช้สร้างbrach ใหม่
* git checkout (ชื่อที่ต้องการเข้า): ใช้ออกไปเข้าbrach ที่ต้องการ

* git merge (ชื่อที่ต้องการ): รวม commit ที่แตกต่างกันของ 2 branch โดยเอามาทั้งหมด  

* git rebase (ชื่อที่ต้องการ): คำสั่งสำหรับย้ายหรือเรียงลำดับ Commit ใหม่ในประวัติการทำงานของ Git โดยการนำ Commit ของเราไปต่อไว้บนสุดของ Branch เป้าหมาย

* git init เปลี่ยนโฟลเดอร์นั้นเป็น git repo หรือก็คือการ สร้างโปรเจ็ค 
* git status บอกว่าไฟล์ไหนเพิ่งถูกเพิ่มมาใหม่  ถูกแก้ไข หรือถูกลบทิ้ง
* git add ตามด้วยชื่อไฟล์นั้น หรือถ้าอยาก add ทุกไฟล์ทีเดียว พิมพ์ git add .
: คือการบอกโปรแกรมว่าเราอยากจะ track และ snap ไฟล์อะไรบ้าง
* git log :Log 
จะแสดงข้อมูล 4 อย่างคือ  
    Commit Hash – unique ID สำหรับ commit นั้นๆ (40 ตัวอักษร)
    Author – ใครเป็นคน commit
    Date – วันที่และเวลา
    Message – ข้อความที่ใส่เข้าไป

* git revert (commit-hash) : คือปุ่ม “safe undo” โดย git จะสร้าง commit ใหม่ที่ undo การเปลี่ยนแปลงทั้งหมดของ commit ก่อนหน้า หรือ specific commit ที่เราเลือก

* git switch [branch name] :ใช้ เพื่อย้ายไปอยู่ branch ใหม่ 
 
 * git pull : ใช้ในการดึงของจาก remote repo ลงมาที่คอมเรา
 * git push : คือการผลักของจากคอมเราขึ้นไปที่ remote repo

# YAML & JSON คือ?![Logo5](https://blog.openreplay.com/images/convert-json-to-yaml/images/hero.png)
    JSON คืออะไร?
    JavaScript Object Notation (JSON) เป็นรูปแบบข้อมูลที่มีน้ำหนักเบา ทำให้เครื่องสามารถวิเคราะห์และสร้างข้อมูลได้ง่าย มีการใช้งานอย่างแพร่หลายในแอปพลิเคชันเว็บที่ต้องการการถ่ายโอนข้อมูลที่รวดเร็ว รองรับชนิดข้อมูลที่หลากหลาย เช่น ตัวเลข สตริง บูลีน หรือออบเจ็กต์

    ข้อดีที่ สำคัญที่สุดอย่างหนึ่งของJSONคือ ภาษาโปรแกรมอย่าง JavaScript และ Python มีการรองรับ JSON ในตัว ซึ่งทำให้การพัฒนาซอฟต์แวร์สำหรับการถ่ายโอนข้อมูลสะดวกอย่างยิ่ง

    YAML คืออะไร?
    YAML เป็นภาษาสำหรับการแปลงข้อมูลเป็นรูปแบบที่อ่านง่ายมาก ที่จริงแล้วมันเป็นส่วนขยายของ JSON ซึ่งหมายความว่าไฟล์ YAML ที่ถูกต้องสามารถมีอ็อบเจ็กต์ JSON ได้ในทางทฤษฎี นอกจากจะรองรับชนิดข้อมูลมาตรฐานของ JSON แล้ว ยังรองรับชนิดข้อมูลที่ซับซ้อนกว่า เช่น วันที่และเวลาอีกด้วย

    เนื่องจากYAML มีข้อดี ที่ชัดเจน ในด้านความอ่านง่าย จึงมักถูกใช้ในการกำหนดค่าไฟล์ในภาษาโปรแกรมต่างๆ กระบวนการปรับใช้ และแพลตฟอร์มคลาวด์

# ไวยากรณ์
    ไวยากรณ์JSON กับ YAMLมีความแตกต่างที่เห็นได้ชัดที่สุดคือรูปแบบการจัดวาง ในขณะที่ YAML ใช้การเว้นวรรคเพื่อจัดโครงสร้างฟิลด์และออบเจ็กต์ แต่ JSON ใช้เพียงวงเล็บปีกกาและเครื่องหมายจุลภาคเท่านั้น

YAML
```YAML
id: 1
name: anonymous
address:
	city: Hanoi
	country: Vietnam 
```
JSON
```JSON
{
	"id": 1,
	"name": "anonymous",
	"address": {
		"city": "Hanoi",
		"country": "Vietnam"
	}
}
```
# ประเภทข้อมูล
    สำหรับชนิดข้อมูล JSON รองรับสตริง อ็อบเจ็กต์ ตัวเลข บูลีน อาร์เรย์ และค่าว่างความแตกต่างหลักระหว่าง YAML และ JSONคือ YAML มีการรองรับวันที่และเวลาเพิ่มเติมในตัว
# ความสามารถในการขยาย
    ในแง่ของความยืดหยุ่น YAML รองรับการอ้างอิงข้อมูลและชื่ออ้างอิง ทำให้คุณสามารถอ้างอิงข้อมูลเดียวกันได้หลายครั้งภายในเอกสารเดียว ในขณะที่ JSON ไม่มีฟังก์ชันรองรับการอ้างอิงหรือชื่ออ้างอิงในตัว ทำให้มีความยืดหยุ่นน้อยกว่าเมื่อคุณต้องการนำโค้ดกลับมาใช้ใหม่

# JSON กับ YAML: ควรใช้แบบไหนดี
    JSON มีประสิทธิภาพดีในการแปลงข้อมูลเป็นรูปแบบที่จัดเก็บได้ และภาษาโปรแกรมบางภาษาก็มีระบบรองรับในตัว ควรเลือกใช้ JSON หากต้องการ
* ทำงานร่วมกับ API บนเว็บ
* จัดเก็บข้อมูลชั่วคราว
* การบันทึกและการวิเคราะห์ข้อมูล
* ผสานรวมกับระบบอื่น

YAML มีคุณสมบัติมากมายและการออกแบบมาเพื่อความอ่านง่าย ควรเลือกใช้ YAML หากคุณต้องการ
* สร้างไฟล์การกำหนดค่า
* ใช้ไปป์ไลน์การปรับใช้ CI/CD
* นำโครงสร้างพื้นฐานมาใช้ในรูปแบบโค้ด
* สร้างการนำเสนอข้อมูลที่มนุษย์สามารถอ่านได้

![Logo2](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSE57YzOT0_LFe1sjx9XPqqorJEb0T2fOk1jw&s)  
# Linux คือ?
    ลินุกซ์ ก็ คือ ระบบปฏิบัติการ (OS : Operating System) อีกระบบหนึ่งที่พัฒนาแบบ Open Source นั่นหมายความว่าผู้ใช้ หรือนักพัฒนาสามารถนำไปใช้ หรือปรับแต่งแก้ไข เพื่อให้ใช้งานกับงานของตัวเองได้โดยไม่มีข้อจำกัด หรือติดลิขสิทธิ์ใดๆ

  *  Kernel เป็นหัวใจสำคัญของ Linux ทำหน้าที่ในการจัดการหน่วยประมวลผล(CPU), หน่วยความจำ(memory) และอุปกร์ต่อพ่วง เช่น จอมอนิเตอร์ แป้นพิมพ์ หรือเม้าส์
* Shell เป็นส่วนต่อประสานกับ Kernel ทำหน้าที่รับ commands จาก users และเรียกใช้ฟังก์ชันต่างๆของ kernel
* Utilities โปรแกรมอรรถประโยชน์ช่วยอำนวยความสะดวกแก่ผู้ใช้ เข่น Editor (vi , nano) , Complier (gcc, g++) เป็นต้น

# Distribution ของ Linux คืออะไร
    Linux มีหลาย version รอบรับผู้ใช้งานทุกประเภท ตั้งแต่ Beginner จนถึง Expert เราเรียก version ต่างๆเหล่านี้ว่า distributions หรือเรียกสั้นๆว่า “distro”
    
* Distro สำหรับ Desktop
    + LINUX MINT 
    * DEBIAN
    - UBUNTU
    + FEDORA
    * OPENSUSE
    - ELEMENTARY OS
* Distro สำหรับ Server
    * Ubuntu Server
    - Red Hat Enterprise Linux
    + CentOS
    - SUSE Enterprise Linux

# Linux Command Line 
*  ls :ใช้เพื่อแสดงรายการไฟล์และไดเรกทอรีในโฟลเดอร์ปัจจุบัน 
* ls -l : แสดงรายละเอียดของไฟล์และโฟลเดอร์
* ls -a : เพื่อแสดงไฟล์ที่ซ่อนอยู่
* pwd : ใช้เพื่อแสดงให้เห็นถึง  ไดเรกทอรี ที่ใช้งานอยู่
* rmdir : ใช้ลบไดเรกทอรีที่ว่างเปล่า
* cp : ใช้คัดลอกไฟล์จากไดเรกทอรีหนึ่งไปยังอีกที่หนึ่ง
* mv : 	ใช้เปลี่ยนชื่อหรือนำไฟล์ไปแทนที่ไฟล์อื่น
* rm : ใช้ลบไฟล์
* uname :ใช้แสดงข้อมูลพื้นฐานของระบบปฏิบัติการ
* locate : ใช้ค้นหาไฟล์ในฐานข้อมูล
* touch : ใช้สร้างไฟล์ว่าง
* ln : ใช้สร้างทางลัดไปยังไฟล์อื่น
* cat : ใช้แสดงเนื้อหาไฟล์ในเทอร์มินัล
* clear : 	ใช้ล้างหน้าจอเทอร์มินัล
* ps : ใช้แสดงกระบวนการที่กำลังทำงาน  
* man : ใช้เข้าถึงคู่มือการใช้คำสั่ง
* grep :ใช้ค้นหาข้อความในผลลัพธ์
* echo : ใช้แสดงข้อความในเทอร์มินัล
* wget : ใช้ดาวน์โหลดไฟล์จากอินเทอร์เน็ต
* whoami : ใช้แสดงชื่อผู้ใช้งานปัจจุบัน
* sort : ใช้เรียงลำดับเนื้อหาไฟล์
* cal : 	ใช้ดูปฏิทินในเทอร์มินัล
*  whereis : 	ใช้แสดงที่ตั้งของคำสั่งที่ป้อน
* df: ช้แสดงรายละเอียดของระบบไฟล์
* wc : ใช้ตรวจสอบจำนวนบรรทัด คำ และอักขระในไฟล์

# Docker คืออะไร
![Logo3](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ-oV3dKd5Y4KDxi4D-pwdGQYdk44HHZgVStQ&s)

    Docker คือ แพลตฟอร์ม Open-Source ที่ช่วยให้นักพัฒนาสามารถปรับใช้และจัดการแอปพลิเคชันได้โดยอัตโนมัติในรูปแบบ Container โดย Container จะมีบริการแต่ละอย่างที่จำเป็นสำหรับการ Run an application, Code, System tools และ Library ด้วยการใช้เทคโนโลยี Containerization ตัว Docker จึงสามารถจัดการ Version Control ในระบบต่าง ๆ ได้อย่าง่ายดายโดยไม่คำนึงถึงโครงสร้างพื้นฐาน

# Docker ใช้ทำอะไร?
1. Increased Portability  
Docker Container ง่ายต่อการเคลื่อนย้าย ช่วยให้แอปพลิเคชันสามารถทํางานได้อย่างมีระสิทธิภาพแม้จะอยู่ในสภาพแวดล้อมที่แตกต่างออกไป
2. Simplified Deployment
นักพัฒนาสามารถ Deploy แอปพลิเคชันได้ง่ายขึ้นด้วย Docker โดยตัว Container จะจัดเตรียมรูปแบบมาตรฐาน เพื่อให้มั่นใจได้ว่านักพัฒนาจะสามารถ Deploy และ Run แอปพลิเคชันได้อย่างง่ายดาย

3. Efficient Resource Utilization
Containers ของ Docker จะใช้ OS, CPU และ RAM ร่วมกันกับ Host OS ซึ่งช่วยลดปัญหาการเกิด Overhead
4. Rapid Development and Testing
ด้วย Docker กระบวนการติดตั้งแอปพลิเคชันจะกลายเป็นเรื่องที่ง่ายเนื่องจากตัว Containers สามารถสร้างขึ้นได้ในเวลาเพียงไม่กี่วินาที

# ระบบนิเวศของ Docker
* Docker Engine : เป็นหัวใจหลักของ Dockerซึ่งเป็นเทคโนโลยีหลักที่รับผิดชอบในการสร้างและจัดการ Containers

* Docker Hub : Docker Hub หรืออีกชื่อ Docker Registry เป็นพื้นที่เก็บข้อมูลในคลาวด์ที่นักพัฒนาจะทำการอัปโหลด Docker Image ของแอปพลิเคชันเอาไว้ โดยที่นักพัฒนาคนอื่น ๆ จะสามารถเข้าถึง Image เหล่านี้เพื่อนำมาพัฒนาหรือต่อยอดแอปพลิเคชันได้เช่นกัน

* Docker Compose : Docker Compose เป็นเครื่องมือที่ทรงประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถกำหนดค่าแอปพลิเคชันที่มีหลาย Containers ได้สะดวกมากขึ้นโดยการกำหนดตั้งค่าไฟล์ YAML สิ่งนี้ช่วยลดความซับซ้อนของกระบวนการจัดการแอปพลิเคชันและช่วยให้ประหยัดเวลามากขึ้น

* Docker Swarm : Docker Swarm เป็นเครื่องมือที่ช่วยให้นักพัฒนาสามารถสร้างและจัดการ Docker จำนวนมากให้อยู่ในสภาพแวดล้อมเดียวกันได้โดยมี Swarm Manager ที่ทำหน้าที่ในการควบคุมเครื่องเซิร์ฟเวอร์อื่น ๆ ที่เข้ามาช่วยในการทำงาน

# การใช้งาน Docker
1. Microservices Architecture   
Docker ได้กลายเป็นหนึ่งในตัวเลือกที่ยอดเยี่ยมสำหรับองค์กรที่ใช้ Microservices Architecture เพราะนอกจากจะช่วยให้นักพัฒนาแบ่งส่วนบริการออกเป็นส่วน ๆ เพื่อแก้ปัญหาความยุ่งยากและความซับซ้อนของระบบขนาดใหญ่แล้วยังช่วยให้นักพัฒนาเข้าใจ พัฒนา และบำรุงรักษาระบบได้ง่ายขึ้นอีกด้วย

2. Continuous Integration and Continuous Deployment (CI/CD)  
การนำ Docker เข้ามาอยู่ในกระบวนการ CI/CD ช่วยเพิ่มความคล่องตัวในการพัฒนาและปรับใช้ให้มีประสิทธิภาพมากขึ้น อีกทั้งยังช่วยให้มั่นใจได้ว่าการเปลี่ยนแปลงโค้ดในแต่ละครั้งจะถูกทดสอบอย่างละเอียดใน Containers ก่อนที่จะถูกนำไปใช้ในการ Deploy Production เพื่อลดความเสี่ยงของการเกิดข้อผิดพลาดและการหยุดทำงาน

3. Hybrid Cloud Deployments  
  ความสามารถในการประยุกต์ไปที่ระบบปฏิบัติการอื่นโดยไม่ยึดติดกับการเป็นระบบปฏิบัติการเดียว ทำให้ Docker เป็นตัวเลือกที่เหมาะสมสำหรับการปรับใช้กับระบบ Hybrid Cloud  ซึ่งนักพัฒนาสามารถสร้างแอปพลิเคชันในสภาพแวดล้อมที่แตกต่างกันและนำไปใช้งานบนเซิร์ฟเวอร์คลาวด์อื่น ๆ ได้อย่างราบรื่นโดยไม่มีปัญหาด้านความเข้ากันได้

# commands Docker
```

docker --version หรือ docker -v

```
- ใช้ตรวจสอบเวอร์ชัน

``` 
docker info
```
- แสดงข้อมูลทั้งระบบเกี่ยวกับ Docker

```
docker pull <image_name>
```
- ดาวน์โหลด image จาก Docker Hub

```
docker images 
หรือ docker image ls
```
- แสดงรายการอิมเมจ Docker ในเครื่อง

```
docker ps 
หรือ docker container ls
```
- แสดงรายการ containers ที่ทำงานอยู่

```
docker ps -a 
หรือ docker container ls -a
```
- แสดงรายการ containers ทั้งหมด รวมถึง containers ที่หยุดทำงานด้วย

```
docker run <options> <image_name>
```
- สร้างและรัน container ใหม่จาก image

```
docker build -t <image_name> <path_to_Dockerfile>
```
- สร้างอิมเมจ Docker จาก Dockerfile

```
docker rmi <image_name>
```
- ลบ Image

```
docker image prune
``` 
- ลบ Image ที่ไม่ได้ใช้ทั้งหมด

```
docker volume create <volume_name>
```
- สร้าง volume ที่มีชื่อ

```
docker run -v <volume_name>: <container_path>
```
- เชื่อม volume เข้ากับ container
```
 docker volume ls
```
- แสดงรายการ volume
```
docker volume rm <volume_name>
```
- ลบ volume

```
docker network create <network_name>
```
- สร้าง network ที่ผู้ใช้กำหนดเอง

```
docker network ls
```
- แสดงรายการ networks

```
docker network connect <network_name> <container_name/id>
```
- เชื่อมต่อ container กับ network
```
docker network disconnect <network_name> <container_name/id>
```
- หยุดเชื่อมต่อ container จาก network


> # เพิ่มเติม

>### Git checkout กับ switch แตกต่างกันยังไง

> git checkout = คำสั่งเก่า ทำหลายอย่าง มีการ เปลี่ยน branch, สร้าง branch,ย้าย commit , restore file 

> git switch = คำสั่งใหม่ ใช้เปลี่ยน branch โดยเฉพาะ

>###  แยกแยะให้ได้ว่าcommand ไหนทํางานบนเครื่องเรา ทําบนoffline และทําบน online ของgit

>#### 1. Command ที่ทำงานบนเครื่องเรา (Local / Offline)


> ##### พวกนี้ ไม่ต้องใช้อินเทอร์เน็ต
>- git status = ดูว่าไฟล์ไหนเปลี่ยน 

>- git log = ดู commit ที่มีในเครื่อง

>- git diff = ดูความต่างของไฟล์

>- git branch = ดู branch ในเครื่อง

>- git switch dev = เปลี่ยน branch ในเครื่อง

>- git switch -c feature/login = สร้าง branch ใหม่ในเครื่อง

>- git add . = ย้ายไฟล์เข้า Staging

>- git commit -m "add login" = บันทึกลง Local Repository


>#### 2. Command ที่ทำงานกับ Remote (Online)

>ต้องต่อ Internet


>- git fetch = คือ เอาข้อมูลมาเก็บในเครื่อง แต่ยังไม่เปลี่ยนไฟล์

>- git pull = ดึงจาก GitHub แล้วรวมเข้า branch เรา

>- git push = ส่ง commit ของเราไป GitHub

>#### 3.  Command ที่ใช้ได้ทั้งสองฝั่ง

>- git clone URL =  ครั้งแรก ต้องใช้ Internet แต่หลังจากโหลดแล้ว ทำงาน offline ได้

>- git remote -v = ดูว่าเชื่อม GitHub ไหน

> ### Git Life Cycle (กระบวนการทำงานของ Git)

```
แก้ไขไฟล์
   |
   v
Working Directory
(ไฟล์ที่กำลังแก้)
   |
   | git add
   v
Staging Area
(เตรียมไฟล์ที่จะบันทึก)
   |
   | git commit
   v
Local Repository
(เก็บประวัติในเครื่อง)
   |
   | git push
   v
Remote Repository
(GitHub / GitLab)
```

>### Git ref log กับlog ต่างกันยังไง

```
git log
= ดูประวัติ "commit"

git reflog
= ดูประวัติ "การขยับของ HEAD / branch ในเครื่อง"
```


> ### Conventional Commit Messages (รูปแบบการเขียน Git commit message ให้เป็นมาตรฐาน)

> รูปแบบ commit 
```
git commit -m "<type>(<scope>): <description>"
```

>ตัวอย่าง
```
git commit -m "feat(login): add login page"
```
>ความหมาย
>-  feat = เพิ่มความสามารถใหม่
>- login = ส่วนที่แก้ (scope)
>- add login page = สิ่งที่ทำ

>Type ที่ใช้บ่อย

| Type       | ใช้เมื่อ                                      | ตัวอย่าง                           |
| ---------- | --------------------------------------------- | ---------------------------------- |
| `feat`     | เพิ่ม feature ใหม่                            | `feat(auth): add login page`       |
| `fix`      | แก้ bug / แก้ปัญหา                            | `fix(api): handle error response`  |
| `docs`     | แก้เอกสาร README / comment                    | `docs: update installation guide`  |
| `style`    | format code, spacing, lint (ไม่เปลี่ยน logic) | `style: format eslint rules`       |
| `refactor` | ปรับโครงสร้าง code/folder ไม่เปลี่ยนผลลัพธ์          | `refactor: move components folder` |
| `test`     | เพิ่ม/แก้ test                                | `test: add login test case`        |
| `chore`    | งานทั่วไป config, gitignore, project setup    | `chore: initial project setup`     |
| `ci`       | CI/CD เช่น GitHub Actions, GitLab CI          | `ci: add deploy pipeline`          |
| `build`    | build system, dependency, Docker, package     | `build: update docker image`       |
| `perf`     | ปรับ performance                              | `perf: optimize api request`       |
| `revert`   | ย้อน commit ก่อนหน้า                          | `revert: revert login change`      |

