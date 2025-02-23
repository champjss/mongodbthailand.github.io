---
title: How to load data from MongoDB to Airbyte
description: เรียนรู้วิธีใช้ Airbyte เพื่อซิงค์ข้อมูล MongoDB ของคุณไปยัง MongoDB ในเวลาไม่กี่นาที
---

## Airbyte คืออะไร?

Airbyte คือแพลตฟอร์มซอฟต์แวร์โอเพนซอร์ส (open-source software)เป็นเครื่องมือที่ช่วยในการข้อมูลระหว่างระบบต่างๆได้เพียงไม่กี่คลิก ไม่ต้องเขียนโค้ดเอง

เราจะอธิบายขั้นตอนที่เราซิงข้อมูลจาก MongoDB ไปยัง MongoDB ปลายทางโดยใช้ Airbyte ซึ่งเป็นเครื่องมือที่ช่วยในกระบวนการนี้

## Prerequisites

1. บัญชี MongoDB (1) เพื่อโอนข้อมูลยัง (2)
2. บัญชี MongoDB (2)
3. บัญชี Airbyte Cloud

## ขั้นตอนที่ 1: Set up MongoDB as a source connector

1. ต้องเริ่มด้วยการเปิดใช้งาน MongoDB และทำให้มันสามารถเข้าถึงได้จากอินเทอร์เน็ต นอกจากนี้คุณจำเป็นต้องมีข้อมูลประจำการเข้าถึงเพื่อเข้าถึงฐานข้อมูล
2. ในแดชบอร์ด Airbyte คลิกที่ "Sources" แล้วคลิกที่ "New Source"
3. เลือก "MongoDB" จากรายการแหล่งข้อมูลที่มีให้
4. ในส่วน "Connection Configuration" ใส่ข้อมูลต่อไปนี้:
-   Host: ชื่อโฮสต์หรือที่อยู่ IP ของตัวอินสแตนซ์ MongoDB ของคุณ
-   Port: หมายเลขพอร์ตที่ตัวอินสแตนซ์ MongoDB ของคุณทำงานอยู่
-   Username: ชื่อผู้ใช้ที่คุณใช้เพื่อเข้าถึงตัวอินสแตนซ์ MongoDB ของคุณ
    Password: รหัสผ่านที่คุณใช้เพื่อเข้าถึงตัวอินสแตนซ์ MongoDB ของคุณ
-   Authentication Database: ชื่อของฐานข้อมูลที่ใช้เก็บข้อมูลการตรวจสอบของคุณ
5. คลิกที่ "Test Connection" เพื่อตรวจสอบว่า Airbyte สามารถเชื่อมต่อกับตัวอินสแตนซ์ MongoDB ของได้หรือไม่
6. หากการเชื่อมต่อสำเร็จ คลิกที่ "Save" เพื่อบันทึกการกำหนดค่าแหล่งข้อมูล MongoDB
7. ตอนนี้สามารถสร้างตัวเชื่อมต่อไปแล้วเลือกแหล่งข้อมูล MongoDB ของคุณเป็นข้อมูลนำเข้า จากนั้นคุณสามารถกำหนดท่อต่อข้อมูลเพื่อแปลงและโหลดข้อมูลของคุณเข้าสู่ปลายทางที่คุณต้องการ

## ขั้นตอนที่ 2: Set up MongoDB as a destination connector

ตัวเช่นเดียวกับขั้นตอนที่ 1

## ขั้นตอนที่ 3: Set up a connection to sync your MongoDB data to MongoDB

หลังจากที่คุณเชื่อมต่อ MongoDB เป็นแหล่งข้อมูลต้นทางและ MongoDB เป็นปลายทางใน Airbyte แล้ว คุณสามารถตั้งค่าท่อนำข้อมูลระหว่างทั้งสองด้วยขั้นตอนต่อไปนี้:

1. Create a new connection: บนแดชบอร์ด Airbyte ให้ไปที่แท็บ 'Connections' และคลิกที่ปุ่ม '+ New Connection'.
2. Choose your source: เลือก MongoDB (1)
3. Select your destination: เลือก MongoDB (2)
4. กำหนดการซิงค์: กำหนดความถี่ของการซิงค์ข้อมูลขึ้นอยู่กับความต้องการของคุณ Airbyte รองรับการตั้งค่าการซิงค์ข้อมูลทั้งแบบด้วยมือและแบบตั้งเวลาอัตโนมัติสำหรับการรีเฟรชข้อมูล
5. เลือกข้อมูลที่จะทำการซิงค์: เลือก specific MongoDB objects MongoDB (1) ที่คุณต้องการนำเข้าข้อมูลจากไปยัง MongoDB (2)คุณสามารถทำการซิงค์ทั้งข้อมูลทั้งหมดหรือเลือกตารางและฟิลด์ที่เฉพาะเจาะจงได้
6. Select the sync mode for your streams
7. Test your connection: คลิกที่ปุ่ม 'Test Connection' เพื่อตรวจสอบว่าการตั้งค่าของคุณทำงานได้หรือไม่ หากการทดสอบการเชื่อมต่อเป็นที่สำเร็จ บันทึกการกำหนดค่าของคุณ
8. Start the sync: หากการทดสอบเชื่อมต่อผ่าน คลิกที่ 'Set Up Connection' Airbyte จะเริ่มย้ายข้อมูลจาก MongoDB (1) ไปยัง MongoDB (2) ตามการตั้งค่าของคุณ

อ้างอิง: [เอกสารจาก Airbyte](https://airbyte.com/how-to-sync/mongodb-to-mongodb-destination)
