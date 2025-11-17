# GeoProg — โครงการ GIS + CS + DS

โปรเจ็กต์นี้บูรณาการความรู้ด้าน Geographic Information Systems (GIS), Computer Science (CS) และ Data Science (DS) เพื่อสำรวจ วิเคราะห์ และแสดงผลข้อมูลเชิงพื้นที่ ตั้งแต่การจัดการข้อมูลเวกเตอร์/ราสเตอร์ ไปจนถึงการทำแผนที่เชิงโต้ตอบ (interactive) ด้วย Python และเครื่องมือโอเพนซอร์ส

## เป้าหมาย
- สร้างเวิร์กโฟลว์วิเคราะห์ข้อมูลเชิงพื้นที่ที่ทำซ้ำได้และอ่านง่าย
- เชื่อมโลกของ GIS เข้ากับแนวปฏิบัติทางซอฟต์แวร์ (CS) และการวิเคราะห์ข้อมูล (DS)
- สร้างแผนที่เชิงโต้ตอบสำหรับการสื่อสารผลลัพธ์อย่างมีประสิทธิภาพ

## สิ่งที่ทำได้
- อ่าน/เขียนและประมวลผลข้อมูลราสเตอร์ (GeoTIFF) ด้วย `rasterio`, `xarray`, `rioxarray`
- วิเคราะห์ข้อมูลเวกเตอร์ (Shapefile/GeoJSON) และการผสานข้อมูลตารางด้วย `geopandas`
- สร้างแผนที่โต้ตอบด้วย `leafmap`
- ทำสถิติ/การแปลงข้อมูลด้วย `pandas` และ `numpy`

## เทคโนโลยีหลัก
- Python 3.11 (แนะนำ)
- ไลบรารี: `geopandas`, `rasterio`, `xarray`, `rioxarray`, `leafmap`, `pandas`, `numpy`
- เครื่องมือทำงาน: Jupyter Notebook / VS Code

## เริ่มต้นใช้งาน (Windows + conda-forge แนะนำ)
เพื่อหลีกเลี่ยงปัญหา DLL ของ GDAL ควรติดตั้งแพ็กเกจ GIS ผ่านช่องทาง `conda-forge` แบบสอดคล้องกันทั้งชุด

```powershell
# สร้างและเปิดใช้งานสภาพแวดล้อมใหม่
conda create -n geopro -c conda-forge python=3.11 gdal geopandas rasterio xarray rioxarray leafmap pandas numpy
conda activate geopro

# เปิดโฟลเดอร์โปรเจ็กต์ใน VS Code (ถ้าไม่ได้เปิดอยู่)
code C:\Users\thammarat\Documents\GeoProg
```

หลังติดตั้งเสร็จ หากใช้ Jupyter/Notebook ให้สั่ง Restart Kernel เมื่อเปลี่ยนสภาพแวดล้อม

## รันโน้ตบุ๊กตัวอย่าง
ไฟล์ตัวอย่างอยู่ที่ `test.ipynb`
1) เปิดไฟล์ `test.ipynb`
2) รันเซลแรกเพื่อตรวจว่าไลบรารีโหลดสำเร็จ (จะพิมพ์ “All libraries imported successfully!”)
3) รันเซลแผนที่เพื่อดูแผนที่โต้ตอบด้วย `leafmap`

โค้ดตัวอย่างสั้น ๆ ที่ใช้ในโน้ตบุ๊ก:

```python
import leafmap
m = leafmap.Map(center=[40, -100], zoom=4, height="600px")
m.add_basemap("OpenTopoMap")
m.add_basemap("USGS.Imagery")
m  # แสดงแผนที่โต้ตอบ
```

## โครงสร้างโฟลเดอร์ (แนะนำ)
- `notebooks/` – เก็บสมุดงานทดลองและสาธิต (ปัจจุบันใช้ `test.ipynb` ที่รากโปรเจ็กต์)
- `data/` – ข้อมูลตัวอย่าง (เพิ่มตามการใช้งานจริง; ไม่ควรใส่ไฟล์ใหญ่ใน git)
- `src/` – โค้ดแบบโมดูลสำหรับใช้ซ้ำในงานวิเคราะห์
- `docs/` – เอกสาร/บทความประกอบ

## เคล็ดลับสภาพแวดล้อม
- ใช้ `conda-forge` ให้สอดคล้องกันทั้งชุดเมื่อมีแพ็กเกจที่พึ่งพา GDAL (`rasterio`, `fiona`, ฯลฯ)
- หากพบปัญหา `rasterio` นำเข้าไม่ได้ ให้ลอง:
  ```powershell
  conda install -c conda-forge gdal rasterio fiona --force-reinstall
  ```
- เปลี่ยนสภาพแวดล้อมแล้วควร Restart Kernel ของ Jupyter เสมอ

## การมีส่วนร่วม
ยินดีรับข้อเสนอแนะ ปรับปรุงโค้ด และไอเดียการใช้งานใหม่ ๆ ผ่าน PR/Issue

## ใบอนุญาต
ระบุภายหลัง (TBD)
