[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/w8H8oomW)
**<ins>Note</ins>: Students must update this `README.md` file to be an installation manual or a README file for their own CS403 projects.**

**รหัสโครงงาน:** 67-1_11_pps-r1

**ชื่อโครงงาน (ไทย):** การค้นหาและการจัดกลุ่มบทคัดย่อทางวิชาการ ด้วยการประมวลผลภาษาธรรมชาติ 

**Project Title (Eng):** RETRIEVAL AND CLUSTERING OF ACADEMIC ABSTRACTS USING 
NATURAL LANGUAGE PROCESSING TECHNIQUES 

**อาจารย์ที่ปรึกษาโครงงาน:** ผศ.ดร. ปกป้อง ส่องเมือง  

**ผู้จัดทำโครงงาน:**
1. นางสาวพิมพิกา เดชประภัสสร  6309681218  pimpika.dej@dome.tu.ac.th
   
Manual / Instructions for your projects starts here !
## รายละเอียดโปรเจกต์
โครงงานนี้นำเสนอแนวทางการพัฒนาและปรับปรุงระบบการค้นหาและจัดกลุ่มบทคัดย่อทางวิชาการ ด้วยการใช้เทคนิคการประมวลผลภาษาธรรมชาติ (NLP)
โปรเจกต์นี้ประกอบด้วย 2 ส่วนหลัก:
1. **Semantic Search**: ค้นหาบทคัดย่อที่เกี่ยวข้องจากคำค้น (keyword) โดยใช้เทคนิค embedding และวัดความคล้ายด้วย cosine similarity
2. **Clustering**: นำเวกเตอร์ของบทคัดย่อมาทำการจัดกลุ่ม (Clustering) ด้วย K-Means และประเมินคุณภาพกลุ่มด้วย Silhouette Score

## โครงสร้างไฟล์ของโครงงาน

**รายละเอียด**
1. `Retrieval and Clustering of Academic abstracts using Natural Language  Processing Techniques .ipynb` ขั้นตอนการเตรียมข้อมูล, สร้าง embedding, และทำการทดลอง semantic search,  การทำ clustering ด้วย K-Means และประเมินผลด้วย Silhouette Score 
2. `research_abstracts.csv` ชุดข้อมูลบทคัดย่อทางวิชาการที่ใช้ทดลอง (10,000 รายการแรก)
3. `KeywordsTest.txt` รายการคำค้น 100 คำ ที่ได้จากบทคัดย่อ (คำศัพท์ทั่วไป)

## Library ที่ใช้
**สำหรับการจัดการข้อมูล**
1. import numpy as np ใช้สำหรับการคำนวณเชิงตัวเลข
2. import pandas as pd ใช้จัดการข้อมูล เช่น ไฟล์ CSV, DataFrame
3. import re ใช้สำหรับจัดการ Regular Expressions เช่น การลบตัวอักษรที่ไม่ต้องการ
4. import string ใช้เข้าถึงตัวอักษร เช่น ตัวพิมพ์เล็ก/ใหญ่ หรือลบเครื่องหมายวรรคตอน
5. from google.colab import drive	ใช้เชื่อมต่อกับ Google Drive เพื่ออ่าน/บันทึกไฟล์ใน Colab
   
**สำหรับการแสดงผล**
1. import matplotlib.pyplot as plt	ใช้สร้างกราฟ เพื่อแสดงผลการวิเคราะห์
   
**สำหรับการประมวลผลข้อความ(NLP)**
1. import nltk	เป็นไลบรารี NLP สำหรับการประมวลผลภาษาธรรมชาติพื้นฐาน
2. from nltk.corpus import stopwords	ใช้โหลด "stop words"
3. import spacy	เป็นไลบรารี NLP แบบโมเดิร์น ใช้สำหรับ lemmatization, tokenization
4. from spacy.lang.en.stop_words import STOP_WORDS	เป็น stop words ที่มีอยู่ใน spaCy ไลบรารี
5. import en_core_sci_lg	โมเดล spaCy สำหรับข้อความวิทยาศาสตร์ (จาก SciSpaCy)
   
**สำหรับการทำ embedding**
1. from gensim.models import Word2Vec	ใช้สร้างเวกเตอร์คำแบบ Word2Vec จากข้อความ
2. from gensim.models.doc2vec import Doc2Vec, TaggedDocument	ใช้สร้างเวกเตอร์ทั้งเอกสารด้วย Doc2Vec
3. from sentence_transformers import SentenceTransformer	โหลดโมเดล BERT สำหรับฝังเวกเตอร์ระดับประโยค(SBERT)
**สำหรับการทำ clustering และการวัดผล**
1. from sklearn.cluster import KMeans	ใช้จัดกลุ่มข้อมูล (Clustering) ด้วยวิธี K-Means
2. from sklearn.decomposition import PCA	ใช้ลดมิติของเวกเตอร์เพื่อทำ visualization หรือ clustering
3. from sklearn.metrics import silhouette_score	ใช้วัดคุณภาพของการจัดกลุ่ม

## วิธีใช้งานเบื้องต้น

1. เปิดไฟล์ `Retrieval and Clustering of Academic  abstracts using Natural Language  Processing Techniques .ipynb` ใน Google Colab
2. อัปโหลดไฟล์ `research_abstracts.csv` เข้าสู่ runtime
3. รันโค้ดทั้งหมดตามลำดับ
4. เปรียบเทียบผลลัพธ์การค้นหาแต่ละ embedding ด้วยค่า precision
5. หลังจากเลือก embedding ที่ดีที่สุด ให้รัน `clustering.ipynb` เพื่อลองจัดกลุ่มบทคัดย่อ และดูผลลัพธ์

## ข้อเสนอแนะ

ระบบนี้เป็นต้นแบบ (backend prototype) ที่สามารถนำไปต่อยอดเป็นระบบค้นหาบทคัดย่อเชิงความหมาย เพื่อช่วยให้ผู้ใช้ทั่วไปสามารถเข้าถึงข้อมูลทางวิชาการได้ง่ายขึ้น โดยไม่จำเป็นต้องใช้คำศัพท์เฉพาะ
