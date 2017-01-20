# Embedded System Development Course for EEI

เนื้อหาต่างๆที่เตรียมสำหรับการอบรมการพัฒนาซอฟต์แวร์ฝังตัวจัดที่วิทยาลัยเทคนิคฉะเชิงเทราในระหว่างวันที่ 26-29 ธันวาคม 2559 สนับสนุนโดยสถาบันไฟฟ้าและอิเล็กทรอนิกส์ (EEI) ด้วยความร่วมมือกับสมาคมสมองกลฝังตัวไทย (TESA)  กิจกรรมนี้เป็นส่วนหนึ่งของการพัฒนาบุคลากรในอุตสาหกรรมไฟฟ้าและอิเล็กทรอนิกส์ ภายใต้นโยบายเขตพัฒนาเศรษฐกิจพิเศษในรูปแบบคลัสเตอร์เครื่องใช้ไฟฟ้า อิเล็กทรอนิกส์ และอุปกรณ์โทรคมนาคม   เอกสารการอบรมเป็นแบบออนไลน์ที่

https://prezi.com/qea261kvukw3/embedded-system-development/

## ภาพรวมของการอบรม

### การสร้างซอฟต์แวร์สาหรับระบบสมองกลฝังตัว
โครงสร้างและลักษณะเด่นของระบบซอฟต์แวร์ฝังตัว การพัฒนาข้ามแพลตฟอร์ม ชุดเครื่องมือพัฒนาซอฟต์แวร์ฝังตัว การเขียนโปรแกรมแบบโมดูล การสร้างและปรับแต่งไฟล์อิมเมจ ปัญหาและข้อความรายงานในการสร้างไฟล์อิมเมจ การโปรแกรมลงบอร์ด การทดสอบและดีบั๊กซอฟต์แวร์ฝังตัว เครื่องมือและเทคนิคในการทดสอบและดีบั๊กซอฟต์แวร์ฝังตัว

### บอร์ด Nucleo F401RE
การอบรมเลือกใช้บอร์ด ST Nucleo-F401RE โดยได้รับการสนับสนุนบอร์ดจาก ST Microelectronics (ประเทศไทย)   บอร์ดพัฒนานี้ใช้ไมโครคอนโทรเลอร์ STM32F401RE สถาปัตยกรรม ARM Cortex-M4 ทำงานที่ 84 MHz หน่วยความจำแฟลช 512 kB และหน่วยความจำ RAM 96 kB  ตัวบอร์ดพัฒนาจะมีหัวต่อ 2 ชุดแบ่งเป็นหัวต่อตามรูปแบบ Arduino Uno และหัวต่อแบบ Morpho ที่เปิดให้เข้าถึงขาต่างๆของตัว MCU  การพัฒนาจะใช้ส่วนเชื่อมต่อ ST-LinkV2 บนบอร์ดที่รองรับทั้งการโปรแกรม/ดีบั๊กแบบ SWD รวมทั้งมีเฟิร์มแวร์ที่รองรับการโปรแกรมผ่าน USB Mass Storage และการสื่อสารแบบ USB Serial 

การอ้างชื่อขาสัญญาณบนบอร์ดจะใช้ได้ 3 ระบบคือ 

* ระบบชื่อเฉพาะสำหรับแพลตฟอร์ม mbed เช่น LED1 USER_BUTTON
* ระบบ Arduino ได้แก่ ขา D0 ถึง D13 สำหรับขาสัญญาณดิจิตอล และ A0 ถึง A5 สำหรับขาอินพุตแอนะล็อก
* ระบบ MCU ที่อ้างอิงพอร์ต A ถึง C และขา 0-15   

ตัวอย่างเช่น การสั่งปิด/เปิด LED จะอ้างเป็น **LED1**, **D13** หรือ **PA5** และการอ่านสถานะปุ่มกดจะอ้างเป็น **USER_BUTTON** หรือ **PA_5** ได้  

ข้อควรระวังเกี่ยวกับการใช้ขาสัญญาณคือ มีบางขาที่จะไม่เชื่อมต่อจึงไม่สามารถใช้งานได้ เช่น ขา PA_2/PA_3 ที่เป็นพอร์ตอนุกรมจะไม่เชื่อมต่อกับขา D0/D1 บนบอร์ด เนื่องจากเชื่อมต่ออยู่กับตัวชิพ ST-LinkV2 จึงไม่สามารถสั่งการขา D0/D1 ยกเว้นจะมีการบัดกรีจุดเชื่อม ทำให้ไม่สามารถใช้กับบอร์ด Shield บางประเภทที่มีการใช้ขา D0/D1 เช่น XBee Shield ได้


## การเตรียมการ

### การติดตั้งและใช้งานบอร์ด Nucleo F401RE
1. ลงทะเบียน
   1. ลงทะเบียนใช้งานที่เว็บ https://developer.mbed.org
   2. เลือก Signup จากนั้นกรอกข้อมูลชี่อและ e-mail แล้วยืนยัน e-mail ที่ส่งไปหา
   3. ล็อกอินเข้าเว็บไซต์ https://developer.mbed.org จากนั้นคลิกเลือกที่ Compiler
2. เลือกแพลตฟอร์ม   
   1. เพิ่มแพลตฟอร์มของ Nucleo F401RE โดยคลิกเลือกที่มุมขวาบนของหน้าต่าง mbed Compiler
   2. เลือก Add Platform จะมีการเปิดแท็บใหม่ไปที่แพลตฟอร์ม 
   3. เลือก STMicroelectronics ทางแถบซ้ายมือ แล้วเลือกที่บอร์ด NUCLEO-F401RE
   4. กดปุ่ม Add to your mbed Compiler
   5. กดปุ่ม Open mbed Compiler เพื่อย้อนกลับไปหน้าต่าง mbed Compiler
3. สร้างและติดตั้งโปรแกรม
   1. เลือกตัวอย่างเป็นโค้ดกระพริบ LED
   2. กดปุ่ม Compile เพื่อทำการคอมไพล์และลิงก์ซอร์สโค้ด จากนั้นตัวโปรแกรมจะถูกดาวน์โหลดมาเป็นไฟล์ที่มีนามสกุล .bin
   3. เสียบสาย USB จากบอร์ด Nucleo-F401RE เข้าคอมพิวเตอร์ จะเห็นเป็นสื่อประเภทเดียวกับแฟลชไดร์ฟ
   4. สำเนาไฟล์ .bin จากเว็บไซต์ mbed ลงในไดร์ฟ
   5. โค้ดกระพริบ LED จะทำงานบนบอร์ด

### การติดตั้งและใช้งานโปรแกรม MDK-ARM
1. ติดตั้งไดรเวอร์ serial port และ debugger
   1. ขยายไฟล์ไดรเวอร์ ST-LinkV2 ชื่อ en.stsw-link009.zip ที่ดาวน์โหลดจากเว็บ STMicroelectronics
   2. จาก Control Panel เลือกหัวข้อ Device Manager
   3. คลิกขวาที่ ST-Link Debug และ Unknown Device แล้วเลือก Update Driver Software เพื่ออัพเดทดีไวซ์ไดรเวอร์ 
   4. คลิกที่ตัวเลือก Browse จากนั้นเลือกไปที่ไดเร็กทอรีที่ขยายไฟล์ en.stsw-link009.zip ไว้
2. ติดตั้งโปรแกรม MDK-ARM
   1. ติดตั้งโปรแกรม MDK-ARM จากไฟล์ mdk5xx.exe
   2. เมื่อติดตั้งโปรแกรมเสร็จจะมีการเปิดหน้าต่างของ Pack Installer
   3. เลือกเมนู File > Import เพื่อติดตั้งไฟล์ [Keil.STM32F4xx_DFP.2.11.0.pack](http://www.keil.com/boards2/stmicroelectronics/stm32f4_discovery/) และ
[Keil.STM32NUCLEO_BSP.1.6.0.pack] (http://www.keil.com/boards2/stmicroelectronics/nucleo_f401re/)
   4. เมื่อติดตั้งเสร็จ คลิกที่แท็บ Boards จะเห็นว่า icon ของบอร์ด Nucleo-F401RE เป็นสีเขียว
   5. ปิดโปรแกรม Keil
3. นำเข้าโปรแกรมตัวอย่างจากเว็บไซต์ mbed
   1. จากหน้าต่าง mbed Compiler คลิกขวาเลือกที่ชื่อโปรแกรม จากนั้นเลือก Export Program
   2. เลือก Toolchain เป็น Keil uVision5 และคลิกที่ Export All Files
   3. ขยายไฟล์ zip ที่ดาวน์โหลด
4. สร้างไฟล์อิมเมจ
   1 เรียกใช้โปรแกรม Keil โดยเลือกแบบ Run as administrator
   2. เลือกเมนู Project -> Open Project แล้วเปิดไฟล์นามสกุล .uvprojx ในไดเร็กทอรีที่ขยาย
   3. คลิกขวาที่ชื่อ project จากนั้นเลือกเมนูย่อย Options … 
   4. เลือกที่แท็บ Debug เพื่อตรวจสอบตัวเลือกว่าใช้ ST-Link Debugger จากนั้นกดปุ่ม Settings เพื่อยืนยันว่าดีบั๊กเกอร์ทำงานได้ถูกต้อง
   5. กดปุ่ม Build หรือปุ่มลัด F7 เพื่อคอมไพล์และลิงก์เป็นไฟล์อิมเมจ 
5. ติดตั้งและทดสอบการทำงาน
   1. เลือกเมนู Debug -> Start/Stop Debug Session เพื่อติดตั้งและเข้าสู่โหมด Debug 
   2. กดปุ่ม Run เพื่อสั่งให้บอร์ดทำงาน
   3. โค้ดกระพริบ LED จะทำงานบนบอร์ด

### การใช้งานดีบั๊กเกอร์
1. เริ่มด้วยการคลิกที่แถบสีเทาตรงซ้ายมือของหน้าต่างส่วนโค้ดที่น่าจะมีปัญหาเพื่อตั้ง breakpoint
2. กดปุ่ม Run ซึ่งโค้ดจะมาหยุดที่ตำแหน่งที่ตั้ง breakpoint (มีลูกศรสีเหลืองแสดงตำแหน่งปัจจุบันของโค้ด)
3. คลิกขวาที่ชื่อตัวแปรเพื่อเพิ่มเข้า watch
4. เลือกปุ่ม Step Over หรือกดปุ่ม F10 เพื่อทำงานทีละบรรทัด
5. เมื่อยืนยันการทำงานว่าถูกต้องแล้ว ให้ย้อนกลับไปทำงานขั้นที่ 1 ในส่วนโค้ดถัดไปที่น่าจะเป็นปัญหา

   
## ตัวอย่าง
โค้ดตัวอย่างจะเริ่มจากการสร้างโปรแกรมใหม่ใน mbed Compiler โดยใช้ template คิอ **Blinky LED test for the ST Nucleo boards** จากนั้นสำเนาส่วนโค้ดจากไฟล์ main.cpp ลงไปทับโค้ดเดิม   ในกรณีที่มีไฟล์อื่นๆให้เลือก New File ด้วยการคลิกขวาที่ชื่อโปรแกรมแล้วสำเนาส่วนโค้ด

### nucleo_registers
โค้ดตัวอย่างที่สาธิตวิธีการจัดการ digital I/O ผ่านทางรีจิสเตอร์ RCC และ GPIOA/GPIOC

### nucleo_pwm
โค้ดตัวอย่างที่สาธิตการทำงานของ PWM โดยขับ LED ให้มีความสว่างเพิ่มขึ้นจนถึงสูงสุดแล้วลดกลับมาดับ   การเรียนรู้ยังสามารถปรับค่า period และ duty cycle เพื่อให้สังเกตุการกระพริบได้เมื่อ period เพิ่มจาก 10 เป็น 100 และ 500 มิลลิวินาที

### nucleo_reply
โค้ดตัวอย่างที่สาธิตการทำงานของพอร์ตอนุกรมที่เรียกใช้ผ่านไลบรารี stdio

1. ติดตั้งโปรแกรมลงบอร์ด 
2. เปิดใช้งานซอฟต์แวร์ประเภท terminal เช่น YAT บนคอมพิวเตอร์ จากนั้นเชื่อมต่อกับพอร์ตอนุกรมของบอร์ด Nucleo 
3. พิมพ์ข้อความโดยกดเลือกให้มี CR ('\r') และ LF ('\n') 

ส่วน LED ของบอร์ดจะติดค้างในขณะรอข้อความที่พิมพ์จาก PC ซึ่งจะตอบกลับเป็นข้อความ "hello" และดับ LED เป็นเวลา 1 วินาทีก่อนมาพร้อมรับข้อความใหม่

### nucleo_analog
โค้ดตัวอย่างที่สาธิตการอ่านค่าแรงดันด้วย ADC จากขาสัญญาณ A0 รวมทั้งการรับคำสั่งจาก Serial เพื่อมาควบคุมความสว่างของ LED   

1. ติดตั้งโปรแกรมลงบอร์ด 
2. เปิดใช้งานซอฟต์แวร์ประเภท terminal เช่น YAT บนคอมพิวเตอร์ จากนั้นเชื่อมต่อกับพอร์ตอนุกรมของบอร์ด Nucleo 
3. พิมพ์ตัวอักษร '0' '1' '2' หรือ '3' เพื่อสั่งการ   

ส่วนโค้ดตัวอย่างจะแสดงถึงการประกาศตัวแปร **pc** ด้วยประเภท Serial เพื่อให้สามารถเรียกใช้เมธอด pc.readable() ตรวจสอบว่ามีตัวอักษรในบัฟเฟอร์หรือไม่  แนวทางการตรวจสอบก่อนอ่านนี้ทำให้สามารถหลีกเลี่ยงปัญหาจากฟังก์ชัน **getchar()** ของไลบรารี stdio ที่เป็นแบบ blocking call ทำให้ส่วนโค้ดหยุดทำงานหากยังไม่มีการพิมพ์คำสั่ง

### nucleo_2boards
โค้ดตัวอย่างที่สาธิตการสื่อสารระหว่างบอร์ดด้วยพอร์ตอนุกรม โดยเปิดใช้งานพอร์ตอนุกรม 2 พอร์ตพร้อมกัน   พอร์ตอนุกรมที่ต่อกับ PC คือ USART2 (ขา PA2/PA3) ซึ่งไม่สามารถเข้าถึงได้ผ่านขาสัญญาณ และพอร์ต USART1 (ขา PA9/PA10 ตรงกับขา D8/D2)  

1. ต่อสายระหว่าง GND ของทั้ง 2 บอร์ดและต่อสลับขา D8 และ D2 ระหว่างบอร์ด (twisted) 
2. เปิดใช้งานซอฟต์แวร์ประเภท terminal เช่น YAT บนคอมพิวเตอร์ จากนั้นเชื่อมต่อกับพอร์ตอนุกรมของบอร์ด Nucleo 
3. ต่อสายจากขา A0 ไปขา 3V3 (ไฟเลี้ยง) หรือ GND ซึ่งจะสังเกตุได้ว่า LED ของอีกบอร์ดจะติดหรือดับตามการเลือกต่อ

ส่วนโค้ดตัวอย่างจะแสดงถึงรูปแบบการสื่อสารแบบง่ายระหว่างบอร์ดโดยใช้พอร์ตอนุกรม

### nucleo_oscilloscope
โค้ดตัวอย่างที่สาธิตการใช้ออสซิลโลสโคปเพื่อตรวจสอบการทำงานของบอร์ด เพื่อสร้างความเข้าใจเกี่ยวกับการตรวจวัดสัญญาณดิจิตอลรวมทั้งรูปแบบ/เวลาของสัญญาณพอร์ตอนุกรมเทียบกับพัลส์

1. ต่อออสซิลโลสโคปเพื่อวัดขา D13 (CH1) และ D8 (CH2)
2. ตั้งการทำงานของ Trigger เป็นโหมด NORMAL ตรวจจับขอบขาขึ้นของ CH1 และระดับที่ประมาณ 1 โวลต์
3. ติดตั้งโปรแกรมลงบอร์ด
4. ปรับ Timebase จนเห็นสัญญาณของ LED (พัลส์กว้าง 0.2 วินาที) และ USART Tx (3 ตัวอักษร)

หากมี logic analyzer ให้ตรวจวัดสัญญาณของขา D8 จากนั้นเลือกใช้การถอดรหัส UART เพื่อให้เข้าใจถึงความสัมพันธ์ระหว่าง ASCII กับขบวนพัลส์

### nucleo_crossing_start
โค้ดต้นแบบสำหรับใช้เรียนรู้การสร้างระบบสัญญาณไฟข้ามถนน โดยแบ่งเป็น 3 โมดูลได้แก่ **main** ที่เป็นลอจิกหลัก **lamp** สำหรับปิดเปิดไฟสัญญาณ และ **events** สำหรับเหตุการณ์ในระบบซอฟต์แวร์

* โหมดการทำงานแบ่งเป็น IDLE (รอการกดปุ่ม) PREPARE (ไฟกระพริบ/ไฟเหลือง) CROSS_OK (ไฟแดงฝั่งถนน) CROSS_STOP (ไฟกระพริบเตือน) และ LAMP_ERROR (ไฟขาด)
* ใช้ USER_BUTTON เป็นปุ่มกดสำหรับคนเดินถนน 
* ต่อขา D3-D7 กับ LED เพื่อแทนไฟสัญญาณ หรือพิมพ์ข้อความทางพอร์ตอนุกรม
* ต่อขา A0 กับ 3V3 (ทำงานปกติ) หรือ GND (หลอดไฟขาด)

### nucleo_crossing_finish
โค้ดตัวอย่างที่เฉลย nucleo_crossing_start โดยไฟล์ lamp.cpp จะเป็นกรณีใช้การต่อ LED ส่วน lamp_fake.cpp ใช้การพิมพ์ข้อความแทน

### nucleo_crossing_tester
โค้่ดต้นแบบสำหรับใช้เรียนรู้การสร้างระบบทดสอบกล่องควบคุมไฟข้ามถนน โดยแบ่งเป็น 2 โมดูลได้แก่ **main** ที่คุมลำดับในวงรอบการทดสอบ (IDLE > SETUP > EXECUTE > TEARDOWN) และ **tester** สำหรับรายการทดสอบต่างๆ   แนวทางในการเขียนโค้ดของ tester.cpp จะเน้นการตรวจสอบสถานะผิดพลาดโดยคืนค่า 0 หากไม่มีความผิดพลาด ซึ่งเมื่อรวมทุกการทดสอบหากเป็น 0 จะหมายถึงผ่าน   ระบบทดสอบจะพิมพ์ข้อความของสถานะการทดสอบผ่านทางพอร์ตอนุกรม

1. ติดตั้งโปรแกรม nucleo_crossing_tester ลงบอร์ดที่เป็นระบบทดสอบ
2. แก้ไขไฟล์ events.cpp ใน nucleo_crossing_finish โดยเปลี่ยน **USER_BUTTON** เป็น **D2** จากนั้นติดตั้งลงบอร์ดที่เป็นกล่องควบคุม
3. เชื่อมต่อขา D2 ถึง D7 ระหว่าง 2 บอร์ด และขา D8 จากบอร์ดระบบทดสอบไปขา A0 ของบอร์ดกล่องควบคุม
4. เปิดใช้งานซอฟต์แวร์ประเภท terminal เช่น YAT บนคอมพิวเตอร์ จากนั้นเชื่อมต่อกับพอร์ตอนุกรมของบอร์ด Nucleo 
5. กดปุ่มรีเซ็ตของบอร์ดระบบทดสอบ แล้วกดปุ่มรีเซ็ตของกล่องควบคุม
6. กดปุ่ม USER_BUTTON ของบอร์ดระบบทดสอบเพื่อเริ่มต้นการทดสอบ
7. ดูการรายงานสถานะจากหน้าจอโปรแกรม terminal

โค้ดตัวอย่างจะมีการทดสอบสำหรับ 2 โหมดคือ IDLE และการกดปุ่ม จึงจะรายงานสถานะเป็น NG เสมอ ให้ศึกษาและเขียนโค้ดใน tester.cpp เพิ่มเติมสำหรับการทดสอบส่วนที่เหลือ

## เอกสารอ้างอิง
1. STM32F401xD STM32F401xE datasheet
2. RM0368 Reference manual STM32F401xB/C and STM32F401xD/E advanced ARM-based 32-bit MCUs