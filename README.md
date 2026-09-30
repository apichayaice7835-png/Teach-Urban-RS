# Teaching Urban Remote Sensing with Google Earth Engine & Python

<p align="center">
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white" alt="Python"></a>
  <a href="https://jupyter.org/"><img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white" alt="Jupyter"></a>
  <a href="https://colab.research.google.com/"><img src="https://img.shields.io/badge/Google-Colab-F9AB00?logo=googlecolab&logoColor=white" alt="Google Colab"></a>
  <a href="https://earthengine.google.com/"><img src="https://img.shields.io/badge/Google-Earth%20Engine-34A853?logo=googleearth&logoColor=white" alt="Google Earth Engine"></a>
  <a href="https://geemap.org/"><img src="https://img.shields.io/badge/Mapping-geemap-2E8B57" alt="geemap"></a>
</p>

<p align="center">
  <a href="https://pandas.pydata.org/"><img src="https://img.shields.io/badge/Data-Pandas-150458?logo=pandas&logoColor=white" alt="Pandas"></a>
  <a href="https://numpy.org/"><img src="https://img.shields.io/badge/Array-NumPy-013243?logo=numpy&logoColor=white" alt="NumPy"></a>
  <a href="https://matplotlib.org/"><img src="https://img.shields.io/badge/Plot-Matplotlib-11557C" alt="Matplotlib"></a>
  <a href="https://scipy.org/"><img src="https://img.shields.io/badge/Stats-SciPy-8CAAE6?logo=scipy&logoColor=white" alt="SciPy"></a>
  <a href="https://scikit-learn.org/"><img src="https://img.shields.io/badge/Model-scikit--learn-F7931E?logo=scikitlearn&logoColor=white" alt="scikit-learn"></a>
</p>

<p align="center">
  <a href="https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED"><img src="https://img.shields.io/badge/Satellite-Sentinel--2-2F80ED" alt="Sentinel-2"></a>
  <a href="https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2"><img src="https://img.shields.io/badge/Satellite-Landsat%208-4C9A2A" alt="Landsat 8"></a>
  <a href="https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD13A3"><img src="https://img.shields.io/badge/Satellite-MODIS-6A5ACD" alt="MODIS"></a>
  <a href="https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1"><img src="https://img.shields.io/badge/Land%20Cover-Dynamic%20World-00A86B" alt="Dynamic World"></a>
  <a href="https://developers.google.com/earth-engine/datasets/catalog/FAO_GAUL_2025_level1"><img src="https://img.shields.io/badge/GIS-FAO%20GAUL-0072B2" alt="FAO GAUL"></a>
</p>

> **แบบเรียนเชิงปฏิบัติการด้าน Urban Remote Sensing และ Geoinformatics สำหรับวิเคราะห์พื้นที่เมืองของประเทศไทยด้วย Google Earth Engine, Python และ Google Colab**

Repository นี้พัฒนาขึ้นเป็นแบบเรียนแบบ **step-by-step** สำหรับนิสิตระดับปริญญาตรี โดยเฉพาะชั้นปีที่ 3 ในสาขา **Urban Studies, Geography, Geoinformatics, Environmental Science** และสาขาที่เกี่ยวข้อง ผู้เรียนไม่จำเป็นต้องมีพื้นฐาน Python ขั้นสูง แต่ควรมีความเข้าใจ GIS/Remote Sensing เบื้องต้น

กรณีศึกษาหลักใช้ **กรุงเทพมหานคร** สำหรับการสาธิต และใช้ **เชียงใหม่** สำหรับแบบฝึกหัดและการประยุกต์ เพื่อให้ผู้เรียนได้ฝึกถ่ายโอนแนวคิดจากพื้นที่หนึ่งไปสู่อีกพื้นที่หนึ่ง

---

## Course philosophy

แนวคิดหลักของแบบเรียนคือ

```text
Earth Observation
      ↓
Spectral Measurement
      ↓
Geographic Representation
      ↓
Image Processing
      ↓
Urban Indicator
      ↓
Spatial / Temporal Analysis
      ↓
Statistical Relationship
      ↓
Scientific Interpretation
```

นักศึกษาจะไม่ได้เรียนเพียง “วิธีเขียนโค้ด GEE” แต่จะเรียนรู้ว่า **ข้อมูลดาวเทียมวัดอะไร มี resolution เท่าใด ผ่าน processing ใด และผลลัพธ์ที่เห็นบนแผนที่/กราฟสามารถตีความทางวิทยาศาสตร์ได้มากน้อยเพียงใด**

หลักการสำคัญที่ใช้ตลอดหลักสูตร:

- **Administrative boundary ≠ physical urban extent**
- **Land Cover ≠ Land Use**
- **Cloud percentage ≠ pixel-level cloud mask**
- **Median composite ≠ cloud-free image โดยอัตโนมัติ**
- **NDVI ≠ vegetation class**
- **Built probability ≠ certain built-up truth**
- **LST ≠ air temperature**
- **High spatial resolution ≠ high temporal resolution**
- **Correlation ≠ causation**
- **Map display ≠ scientific validation**

---

# Quick Start


> **ชื่อไฟล์ใน repository ปัจจุบัน:** Notebook 000 ใช้ชื่อภาษาไทยจริงคือ  
> `000_ติดตั้ง_ทดสอบ_ee_api_colab_setup_หลัง_Register.ipynb`  
> ส่วน Notebook 001–05 ใช้ชื่ออังกฤษตามตารางด้านล่าง ปุ่ม GitHub/Colab ใน README นี้จึงอ้างอิงชื่อไฟล์จริงบน branch `main` โดยตรง


หากเป็นผู้เรียนใหม่ ให้ทำตามลำดับนี้

```text
1. Fork repository นี้
        ↓
2. สร้าง Google Cloud Project
        ↓
3. Register Project กับ Google Earth Engine
        ↓
4. เปิด Notebook 000 ใน Colab
        ↓
5. Authenticate + Initialize
        ↓
6. ทดสอบ Earth Engine API ให้ผ่าน
        ↓
7. เรียน Notebook 001
        ↓
8. เรียน 01 → 05 ตามลำดับ
```

### Start here

| ขั้น | Notebook | Open |
|---|---|---|
| Setup | `000_ติดตั้ง_ทดสอบ_ee_api_colab_setup_หลัง_Register.ipynb` | <a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/000_%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%95%E0%B8%B1%E0%B9%89%E0%B8%87_%E0%B8%97%E0%B8%94%E0%B8%AA%E0%B8%AD%E0%B8%9A_ee_api_colab_setup_%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%87_Register.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a> |
| Beginner | `001_GEE_Beginner_Bangkok_Step_by_Step.ipynb` | <a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/001_GEE_Beginner_Bangkok_Step_by_Step.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a> |

> ปุ่ม **Open in Colab** ใน README นี้ชี้ไปที่ repository ต้นฉบับ `nattaponm/Teach-Urban-RS` โดยตรง จึงเปิดได้แม้นิสิตกำลังอ่าน README จาก fork ของตนเอง

---

# How students should use the repository

## Option A — ต้องการเรียนและรัน Notebook อย่างเดียว

1. กด **Open in Colab**
2. รัน cell จากบนลงล่าง
3. เปลี่ยน `YOUR_GOOGLE_CLOUD_PROJECT_ID` เป็น Project ID ของตนเอง
4. เมื่อทำงานเสร็จ ใช้ **File → Save a copy in Drive**

## Option B — ต้องการเก็บงานไว้ใน GitHub fork ของตนเอง

1. กด **Fork** repository นี้ไปยัง GitHub account ของนิสิต
2. เปิด Notebook จากปุ่ม Colab ใน README นี้
3. ใน Colab เลือก **File → Save a copy in GitHub**
4. เลือก repository fork ของตนเอง เช่น

```text
student-name/Teach-Urban-RS
```

5. Commit Notebook ที่แก้ไขกลับเข้า fork ของตนเอง

### ทำไมปุ่ม Colab ไม่เปิด fork ของนิสิตโดยอัตโนมัติ?

GitHub Markdown ไม่สามารถตรวจ username ของผู้ที่ fork repository แล้วสร้าง Colab URL แบบ dynamic ให้แต่ละคนได้อย่างน่าเชื่อถือ ดังนั้น README นี้จึงใช้ source ที่แน่นอน:

```text
nattaponm/Teach-Urban-RS
```

เพื่อให้ปุ่ม Colab ใช้งานได้เสถียรทุกคน

---

# First-time Earth Engine setup

Earth Engine ทำงานบน Google Cloud ดังนั้นผู้เรียนต้องมี **Google Cloud Project** ที่ลงทะเบียนใช้งาน Earth Engine แล้ว

เอกสารทางการ:

- [Earth Engine access](https://developers.google.com/earth-engine/guides/access)
- [Authentication and initialization](https://developers.google.com/earth-engine/guides/auth)
- [Python in Colab](https://developers.google.com/earth-engine/guides/python_install-colab)
- [Noncommercial tiers](https://developers.google.com/earth-engine/guides/noncommercial_tiers)

## 1. สร้าง Google Cloud Project

เปิด:

https://console.cloud.google.com/

ตัวอย่าง:

```text
Project name : Teach Urban RS
Project ID   : teach-urban-rs-123456
```

> Python ใช้ **Project ID** ไม่ใช่ Project name

## 2. Register Project กับ Earth Engine

เปิด:

https://code.earthengine.google.com/register

สำหรับงานเรียน/การศึกษา:

1. เลือก Existing Google Cloud Project
2. เลือก Project ที่สร้างไว้
3. เลือก Noncommercial use
4. เลือก Education / Academic / Research ตามแบบฟอร์ม
5. ใช้ Community Tier สำหรับการเรียนทั่วไป
6. ทำ registration / verification ให้เสร็จ

## 3. Authenticate และ Initialize

ใน Colab:

```python
import ee

PROJECT = "YOUR_GOOGLE_CLOUD_PROJECT_ID"

ee.Authenticate()
ee.Initialize(project=PROJECT)
```

แนวคิดคือ

```text
Authenticate
   ↓
ยืนยันว่าเราเป็นใคร

Initialize
   ↓
ระบุ Cloud Project ที่จะใช้ประมวลผล
```

เมื่อ Colab runtime ถูก restart หรือ disconnect อาจต้อง initialize ใหม่

---

# Main scientific libraries

| Library | Role in this course | Documentation |
|---|---|---|
| **Earth Engine Python API (`ee`)** | เรียกและประมวลผลข้อมูล geospatial บน Google Earth Engine | https://developers.google.com/earth-engine/guides/python_install |
| **geemap** | Interactive mapping, Earth Engine visualization, export utilities | https://geemap.org/ |
| **Pandas** | Table, sampling results, time series | https://pandas.pydata.org/docs/ |
| **NumPy** | Numerical array operations | https://numpy.org/doc/ |
| **Matplotlib** | Scientific plots and publication-style graphics | https://matplotlib.org/stable/ |
| **SciPy** | Scientific statistics เช่น Pearson correlation | https://docs.scipy.org/doc/scipy/ |
| **scikit-learn** | Simple linear regression | https://scikit-learn.org/stable/ |
| **Folium** | Optional Leaflet-based web mapping | https://python-visualization.github.io/folium/ |

---

# Remote Sensing foundations

## Raster และ Vector

### Vector

```text
Point
Line
Polygon
```

ตัวอย่างในรายวิชา:

- Bangkok point
- Bangkok administrative boundary
- Random sample points

### Raster

```text
Satellite image
NDVI
Land Surface Temperature
Built probability
```

Earth Engine objects:

| GIS concept | Earth Engine |
|---|---|
| Raster 1 ภาพ | `ee.Image` |
| Raster หลายภาพ/หลายเวลา | `ee.ImageCollection` |
| Vector 1 feature | `ee.Feature` |
| Vector หลาย feature | `ee.FeatureCollection` |
| Geometry | `ee.Geometry` |

---

## Resolution

### Spatial resolution

ขนาดพื้นที่บนพื้นโลกที่ pixel หนึ่งแทน

```text
Sentinel-2   10 / 20 / 60 m
Landsat 8    ~30 m สำหรับผลิตภัณฑ์หลักในรายวิชา
MODIS        1 km สำหรับ MOD13A3 / MOD11A2
```

### Spectral resolution

จำนวนและตำแหน่ง wavelength bands ที่ sensor ตรวจวัด

### Temporal resolution

ความถี่ในการสังเกตพื้นที่เดิม

หลักสำคัญ:

```text
High spatial detail
        ↕ trade-off
High temporal consistency
```

Sentinel-2 จึงเหมาะกับรายละเอียดเชิงพื้นที่ของเมือง ขณะที่ MODIS เหมาะกับ time-series analysis

---

# Data used in the course

## 1. FAO GAUL 2025 Level 1

Earth Engine ID:

```python
FAO/GAUL/2025/level1
```

ใช้สำหรับ:

- Thailand
- Bangkok
- Chiang Mai

fields หลัก:

```text
GAUL0_NAME = country
GAUL1_NAME = first-level administrative unit
```

[Data Catalog](https://developers.google.com/earth-engine/datasets/catalog/FAO_GAUL_2025_level1)

---

## 2. Sentinel-2 Level-2A Surface Reflectance Harmonized

Earth Engine ID:

```python
COPERNICUS/S2_SR_HARMONIZED
```

Surface Reflectance collection นี้มี 12 spectral bands หลัก

| Band | Spectral region | Pixel |
|---|---|---:|
| B1 | Aerosol | 60 m |
| B2 | Blue | 10 m |
| B3 | Green | 10 m |
| B4 | Red | 10 m |
| B5 | Red Edge 1 | 20 m |
| B6 | Red Edge 2 | 20 m |
| B7 | Red Edge 3 | 20 m |
| B8 | NIR | 10 m |
| B8A | Narrow NIR | 20 m |
| B9 | Water vapor | 60 m |
| B11 | SWIR 1 | 20 m |
| B12 | SWIR 2 | 20 m |

Surface Reflectance:

$$
\rho = DN \times 0.0001
$$

### True Color

```text
R = B4
G = B3
B = B2
```

### False Color vegetation

```text
R = B8
G = B4
B = B3
```

[Data Catalog](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)

---

## 3. NDVI

Normalized Difference Vegetation Index:

$$
NDVI = \frac{NIR-Red}{NIR+Red}
$$

สำหรับ Sentinel-2:

$$
NDVI = \frac{B8-B4}{B8+B4}
$$

vegetation ที่เขียวมักดูดกลืน Red และสะท้อน NIR สูง จึงมักมี NDVI สูงขึ้น

> NDVI เป็น spectral index ไม่ใช่ vegetation class หรือ land-use class โดยตรง

---

## 4. Dynamic World

Earth Engine ID:

```python
GOOGLE/DYNAMICWORLD/V1
```

10-m land-cover probabilities สำหรับ 9 classes:

```text
water
trees
grass
flooded_vegetation
crops
shrub_and_scrub
built
bare
snow_and_ice
```

รายวิชาใช้ `built` probability เป็นหลัก:

$$
0 \le P(\mathrm{built}) \le 1
$$

และทดลอง operational threshold:

$$
P(\mathrm{built}) \ge 0.5
$$

> ค่า 0.5 ใช้เพื่อการเรียน ไม่ใช่ universal threshold

[Data Catalog](https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1)

---

## 5. Landsat 8 Collection 2 Level-2

Earth Engine ID:

```python
LANDSAT/LC08/C02/T1_L2
```

ใช้ศึกษาความร้อนพื้นผิวเมือง

Surface Reflectance:

$$
\rho = DN \times 0.0000275 - 0.2
$$

Surface Temperature จาก `ST_B10`:

$$
T_K = DN \times 0.00341802 + 149.0
$$

$$
T_{^\circ C}=T_K-273.15
$$

ข้อสำคัญ:

$$
LST \ne T_{air}
$$

Land Surface Temperature เป็น radiometric surface temperature ไม่ใช่ air temperature ที่วัดใกล้ระดับ 2 m

Surface energy balance แบบง่าย:

$$
R_n = H + LE + G
$$

[Data Catalog](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2)

---

## 6. MODIS

### MOD13A3 Monthly Vegetation Indices

```python
MODIS/061/MOD13A3
```

```text
Temporal resolution : Monthly
Spatial resolution  : 1 km
Variables           : NDVI, EVI
NDVI scale factor   : 0.0001
```

$$
NDVI_{physical}=DN\times0.0001
$$

[Data Catalog](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD13A3)

### MOD11A2 Land Surface Temperature

```python
MODIS/061/MOD11A2
```

```text
Temporal support    : 8-day composite
Spatial resolution  : 1 km
Variables           : Daytime / Nighttime LST
LST scale factor    : 0.02 K
```

$$
T_K=DN\times0.02
$$

$$
T_{^\circ C}=T_K-273.15
$$

[Data Catalog](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD11A2)

---

# Course workflow

```text
000  Earth Engine / Colab Setup
 │
001  Beginner GEE — Bangkok Step-by-Step
 │
01   Urban Boundary + Satellite Imagery
 │
02   Vegetation + Built-up
 │
03   Urban Heat + LST
 │
04   Urban Time Series
 │
05   Environmental Relationships
```

---

# Notebooks

<table>
<thead>
<tr>
<th>No.</th>
<th>Notebook</th>
<th>Purpose</th>
<th>Main data / concepts</th>
<th>Learning outcomes</th>
<th>Open</th>
</tr>
</thead>
<tbody>

<tr>
<td><b>000</b></td>
<td><b>Earth Engine & Colab Setup</b><br><sub>000_ติดตั้ง_ทดสอบ_ee_api_colab_setup_หลัง_Register.ipynb</sub></td>
<td>เตรียม Google Colab, authenticate, initialize Cloud Project และตรวจว่า Earth Engine API พร้อมใช้งาน</td>
<td>Earth Engine access, authentication, Cloud Project, Colab runtime</td>
<td>เชื่อม Python API กับ Earth Engine และทดสอบ API ได้</td>
<td>
<a href="https://github.com/nattaponm/Teach-Urban-RS/blob/main/000_%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%95%E0%B8%B1%E0%B9%89%E0%B8%87_%E0%B8%97%E0%B8%94%E0%B8%AA%E0%B8%AD%E0%B8%9A_ee_api_colab_setup_%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%87_Register.ipynb">GitHub</a><br>
<a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/000_%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%95%E0%B8%B1%E0%B9%89%E0%B8%87_%E0%B8%97%E0%B8%94%E0%B8%AA%E0%B8%AD%E0%B8%9A_ee_api_colab_setup_%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%87_Register.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</td>
</tr>

<tr>
<td><b>001</b></td>
<td><b>GEE Beginner — Bangkok Step-by-Step</b><br><sub>001_GEE_Beginner_Bangkok_Step_by_Step.ipynb</sub></td>
<td>เรียน GEE แบบหนึ่ง cell ต่อหนึ่งแนวคิด ตั้งแต่ Map ไปจนถึง Export</td>
<td>GAUL, Sentinel-2, filterBounds, filterDate, cloud filtering, RGB, False Color, NDVI, sampling, export</td>
<td>เข้าใจ GEE workflow สำหรับผู้เริ่มต้นและสามารถรันทีละขั้นได้</td>
<td>
<a href="https://github.com/nattaponm/Teach-Urban-RS/blob/main/001_GEE_Beginner_Bangkok_Step_by_Step.ipynb">GitHub</a><br>
<a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/001_GEE_Beginner_Bangkok_Step_by_Step.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</td>
</tr>

<tr>
<td><b>01</b></td>
<td><b>Urban Boundary & Satellite Imagery</b><br><sub>01_Urban_Boundary_and_Satellite_Imagery.ipynb</sub></td>
<td>เข้าใจ raster/vector และอ่านโครงสร้างพื้นที่เมืองจาก Sentinel-2</td>
<td>GAUL, Sentinel-2, True Color, False Color, spatial/temporal resolution</td>
<td>เลือก boundary, filter imagery และตีความ urban spatial pattern ได้</td>
<td>
<a href="https://github.com/nattaponm/Teach-Urban-RS/blob/main/01_Urban_Boundary_and_Satellite_Imagery.ipynb">GitHub</a><br>
<a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/01_Urban_Boundary_and_Satellite_Imagery.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</td>
</tr>

<tr>
<td><b>02</b></td>
<td><b>Urban Vegetation & Built-up</b><br><sub>02_Urban_Vegetation_and_Builtup.ipynb</sub></td>
<td>วิเคราะห์ vegetation และ built-up structure</td>
<td>NDVI, Dynamic World, built probability, pixel area</td>
<td>สร้าง NDVI/built maps และคำนวณ built-up area ได้</td>
<td>
<a href="https://github.com/nattaponm/Teach-Urban-RS/blob/main/02_Urban_Vegetation_and_Builtup.ipynb">GitHub</a><br>
<a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/02_Urban_Vegetation_and_Builtup.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</td>
</tr>

<tr>
<td><b>03</b></td>
<td><b>Urban Heat & Land Surface Temperature</b><br><sub>03_Urban_Heat_and_LST.ipynb</sub></td>
<td>ศึกษาความแตกต่างของอุณหภูมิพื้นผิวเมือง</td>
<td>Landsat 8 Level-2, QA masking, scale factor, LST, urban analysis zone</td>
<td>สร้างและตีความ LST map อย่างถูกต้องได้</td>
<td>
<a href="https://github.com/nattaponm/Teach-Urban-RS/blob/main/03_Urban_Heat_and_LST.ipynb">GitHub</a><br>
<a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/03_Urban_Heat_and_LST.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</td>
</tr>

<tr>
<td><b>04</b></td>
<td><b>Urban Environmental Time Series</b><br><sub>04_Urban_Time_Series.ipynb</sub></td>
<td>วิเคราะห์การเปลี่ยนแปลง NDVI และ LST ตามเวลา</td>
<td>MOD13A3, MOD11A2, Pandas, monthly time series, seasonal climatology</td>
<td>เปลี่ยน ImageCollection เป็น regional time series และตีความ seasonality ได้</td>
<td>
<a href="https://github.com/nattaponm/Teach-Urban-RS/blob/main/04_Urban_Time_Series.ipynb">GitHub</a><br>
<a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/04_Urban_Time_Series.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</td>
</tr>

<tr>
<td><b>05</b></td>
<td><b>Urban Environmental Relationships</b><br><sub>05_Urban_Environmental_Relationships.ipynb</sub></td>
<td>เชื่อม spatial pattern กับสถิติอย่างง่าย</td>
<td>Spatial sampling, scatterplot, Pearson correlation, simple linear regression</td>
<td>วัด NDVI–LST association และอภิปรายข้อจำกัดของ spatial model ได้</td>
<td>
<a href="https://github.com/nattaponm/Teach-Urban-RS/blob/main/05_Urban_Environmental_Relationships.ipynb">GitHub</a><br>
<a href="https://colab.research.google.com/github/nattaponm/Teach-Urban-RS/blob/main/05_Urban_Environmental_Relationships.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
</td>
</tr>

</tbody>
</table>

> หากเปลี่ยนชื่อ Notebook ใน repository ต้องแก้ path ของปุ่ม GitHub และ Colab ให้ตรงกับชื่อไฟล์จริงบน branch `main`

---

# Statistical concepts

## Pearson correlation

$$
r=
\frac{\sum (x_i-\bar{x})(y_i-\bar{y})}
{\sqrt{\sum (x_i-\bar{x})^2\sum(y_i-\bar{y})^2}}
$$

$$
-1 \le r \le 1
$$

## Simple linear regression

$$
LST_i=\beta_0+\beta_1NDVI_i+\epsilon_i
$$

- $\beta_0$ = intercept
- $\beta_1$ = slope
- $R^2$ = proportion of variance explained by the fitted linear relationship

> Statistical association does not establish causation.

---

# Recommended way to study

สำหรับผู้ที่มีพื้นฐาน Python น้อย:

```text
ก่อนเรียน
000 Setup                  30–45 min
      ↓
พื้นฐาน GEE
001 Beginner Bangkok       90–120 min
      ↓
Urban Remote Sensing
01 Boundary + Satellite
02 Vegetation + Built-up
03 Urban Heat
04 Time Series
05 Environmental Relationship
```

สำหรับ workshop 5 ชั่วโมง สามารถกำหนด `001` เป็น pre-class / self-study แล้วใช้ `01–05` เป็น core workshop

---

# Basemap in Google Colab

ในบาง environment default OpenStreetMap tiles อาจถูก block

Notebook ในรายวิชาจึงใช้แนวทาง:

```python
Map = geemap.Map()
Map.clear_layers()

Map.add_basemap("Esri.WorldImagery", show=True)
Map.add_basemap("Esri.WorldStreetMap", show=False)
Map.add_basemap("Esri.WorldTopoMap", show=False)
```

Basemap ใช้เพื่อการอ้างอิงและการตีความ ไม่ใช่ input หลักของการคำนวณ

---

# Scientific interpretation rules

| สิ่งที่เห็น/คำนวณ | สิ่งที่ควรตีความ |
|---|---|
| Administrative boundary | พื้นที่การปกครอง ไม่ใช่ physical city โดยอัตโนมัติ |
| NDVI สูง | spectral response ที่สอดคล้องกับ vegetation greenness มากขึ้น ไม่ใช่ land-use class |
| Dynamic World built probability | model probability ไม่ใช่ ground truth |
| LST สูง | พื้นผิวมี radiometric temperature สูง ไม่ใช่อุณหภูมิอากาศโดยตรง |
| Correlation สูง | linear association สูง ไม่ใช่หลักฐาน causation |
| High-resolution imagery | รายละเอียดเชิงพื้นที่ดีขึ้น แต่ไม่ได้หมายถึง temporal coverage ที่ดีขึ้น |

---


## Canonical notebook filenames in this repository

```text
000_ติดตั้ง_ทดสอบ_ee_api_colab_setup_หลัง_Register.ipynb
001_GEE_Beginner_Bangkok_Step_by_Step.ipynb
01_Urban_Boundary_and_Satellite_Imagery.ipynb
02_Urban_Vegetation_and_Builtup.ipynb
03_Urban_Heat_and_LST.ipynb
04_Urban_Time_Series.ipynb
05_Urban_Environmental_Relationships.ipynb
```

> หากเปลี่ยนชื่อไฟล์ใดใน GitHub ต้องแก้ทั้ง GitHub link และ Colab link ใน README ให้ตรงกันทุกตัวอักษร


# Repository structure

```text
Teach-Urban-RS/
│
├── README.md
├── 000_ติดตั้ง_ทดสอบ_ee_api_colab_setup_หลัง_Register.ipynb
├── 001_GEE_Beginner_Bangkok_Step_by_Step.ipynb
├── 01_Urban_Boundary_and_Satellite_Imagery.ipynb
├── 02_Urban_Vegetation_and_Builtup.ipynb
├── 03_Urban_Heat_and_LST.ipynb
├── 04_Urban_Time_Series.ipynb
└── 05_Urban_Environmental_Relationships.ipynb
```

---

# Troubleshooting

### Colab badge opens “Notebook not found”

ตรวจ 3 จุด:

```text
owner      = nattaponm
repository = Teach-Urban-RS
branch     = main
```

และชื่อไฟล์ใน URL ต้องตรงกับ GitHub **ทุกตัวอักษร**

รูปแบบที่ถูกต้อง:

```text
https://colab.research.google.com/github/
nattaponm/Teach-Urban-RS/blob/main/NOTEBOOK.ipynb
```

### Earth Engine initialized ไม่ผ่าน

ตรวจว่า:

1. Project ลงทะเบียน Earth Engine แล้ว
2. ใช้ **Project ID** ไม่ใช่ Project name
3. Google Account ที่ Authenticate มีสิทธิ์ใน Project
4. Notebook รัน `ee.Authenticate()` / `ee.Initialize()` แล้ว

### Map แสดง OpenStreetMap 403

ใช้ `Map.clear_layers()` แล้วเพิ่ม Esri basemap ตามตัวอย่างด้านบน

---

# References

### Google Earth Engine
- [Earth Engine access](https://developers.google.com/earth-engine/guides/access)
- [Authentication](https://developers.google.com/earth-engine/guides/auth)
- [Python API](https://developers.google.com/earth-engine/guides/python_install)
- [Colab](https://developers.google.com/earth-engine/guides/python_install-colab)
- [Data Catalog](https://developers.google.com/earth-engine/datasets/catalog/)
- [Noncommercial tiers](https://developers.google.com/earth-engine/guides/noncommercial_tiers)

### Scientific Python
- [geemap](https://geemap.org/)
- [Pandas](https://pandas.pydata.org/docs/)
- [NumPy](https://numpy.org/doc/)
- [Matplotlib](https://matplotlib.org/stable/)
- [SciPy](https://docs.scipy.org/doc/scipy/)
- [scikit-learn](https://scikit-learn.org/stable/)
- [Folium](https://python-visualization.github.io/folium/)

### Main datasets
- [FAO GAUL 2025 Level 1](https://developers.google.com/earth-engine/datasets/catalog/FAO_GAUL_2025_level1)
- [Sentinel-2 SR Harmonized](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)
- [Dynamic World](https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1)
- [Landsat 8 Level-2](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2)
- [MOD13A3](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD13A3)
- [MOD11A2](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD11A2)

---

## Teaching philosophy

เป้าหมายของ Repository นี้ไม่ใช่ให้นิสิตจำ syntax จำนวนมาก แต่ให้เชื่อมโยงได้ว่า

```text
Urban Question
      ↓
Geographic Concept
      ↓
Remote Sensing Observation
      ↓
Earth Engine Processing
      ↓
Map / Time Series / Model
      ↓
Scientific Interpretation
```

เมื่อเรียนจบ ผู้เรียนควรสามารถตอบได้ว่า **กำลังใช้ข้อมูลอะไร ที่ spatial/temporal resolution เท่าใด ผ่าน processing ใด และผลลัพธ์สามารถใช้ตอบคำถามด้านเมืองได้ในขอบเขตใด**
