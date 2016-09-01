# RxJava-Snipplet
Just my own snipplet about ReactiveX in RxJava


## Create Operators
Observable.just(someList) will give you 1 emission - a List.

Observable.from(someList) will give you N emissions - each item in the list.

* **Just** เป็นการสร้าง Observable ที่จะส่งข้อมูลที่ได้ทันที สำหรับข้อมูล Array โดยจะส่งข้อมูล Array ทั้งหมด
* **From** เป็นการสร้าง Observable ที่จะส่งข้อมูลที่ได้ทันที สำหรับข้อมูล Array โดยจะส่งข้อมูลทีละตัวของ Array
* **From Callable** เป็นการสร้าง Observable ที่ทำงานบน Callable สามารถ Handle Exception ได้
* **Create** เป็นการสร้าง Observable ที่เราจะต้องจัดการ Event ของ Observer เองทั้งหมด ว่าจะให้เกิด onNext, onError, onCompleted เมื่อไรบ้าง
* **Empty** เป็นการสร้าง Observable จะส่ง Event Completed มาทันที โดยไม่มีการส่งข้อมูลใดๆมา
* **Never** เป็นการสร้าง Observable จะไม่ส่งข้อมูลใดๆและไม่ส่ง Event ใดๆมา (ไม่หยุดทำงาน)
* **Error** เป็นการสร้าง Observable จะไม่ส่งข้อมูลใดๆ แต่จะส่ง Exception สำหรับ onError เท่านั้น
* **Timer** เป็นการสร้าง Observable  จะที่คอยเรียก onNext เป็น Interval เรื่อยๆตามที่กำหนดไว้ ซึ่งโคตรเป๊ะ
* **Range** เป็นการสร้าง Observable ที่จะนับตัวเลขตามขอบเขตที่กำหนดให้ เช่นกำหนดเป็น 5, 4 ( 5 คือเลขเริ่มต้น ส่วน 4 คือจำนวครั้งของ Event) ใน onNext ก็จะส่ง Event มาให้ โดยในแต่ละครั้งก็จะส่ง Int มาด้วย เช่น 5, 6, 7 และ 8
* **Repeat** เป็น Create Operator ที่ไม่ได้ถูกสร้างขึ้นด้วยตัวเองเหมือนตัวอื่นๆ แต่ Repeat จะใช้กับ Observable ที่ถูกสร้างขึ้นด้วยวิธีอื่นๆ โดย Repeat จะทำให้ Observable ตัวนั้นๆวนการทำงานเป็นจำนวนครั้งตามที่กำหนดไว้ใน Repeat
* **Start** เป็นการสร้าง Observable ที่จะทำงานทันทีที่ถูกสร้างขึ้น แล้วเก็บค่านั้นไว้ใช้ส่ง onNext ตลอด โดยไม่สนว่าคำสั่งที่กำหนดไว้จะมีการเปลี่ยนแปลงค่าเรียบร้อยแล้ว และคำสั่งนี้เรียกใช้ใน Async ซึ่งไม่มีอยู่ใน RxJava ปกติ ต้องไปลง RxJavaAsyncUtil อีกที
* **Interval** เป็นการสร้าง Observable ที่จะทำงานเป็น Interval ทุกๆระยะเวลาที่กำหนดไว้ และจะทำงานไปเรื่อยๆ โดยจะส่ง Long มาให้เพื่อบอกว่าวนลูปถึงครั้งที่เท่าไรแล้ว
* **Timer** เป็นการสร้าง Observable ที่จะทำงานในระยะเวลาข้างหน้าตามที่กำหนดไว้ โดยจะส่ง Long เข้ามาใน onNext ด้วยเหมือนกับ Interval แต่เนื่องจากมันเป็น Timer ที่ทำงานแค่ครั้งเดียว เพราะงั้นมันก็เกิด onNext แค่ครั้งเดียว แล้วส่ง Long ที่มีค่าเป็น 0 มา
* **Defer** จะคล้าย Create แต่ว่า Observable จะยังไม่ถูกสร้างในทันทีเหมือน Create จนกว่า Observer จะ Subscribe แล้ว Defer ก็จะสร้าง Observable ขึ้นมาให้ใหม่ในตอนนั้นทันที http://goo.gl/arvo35



