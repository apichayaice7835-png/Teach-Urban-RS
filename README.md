# Teach Urban RS
## Google Earth Engine with Python for Urban Remote Sensing (Thailand)

หลักสูตรภาคปฏิบัติสำหรับนิสิตระดับปริญญาตรีที่ต้องการเริ่มใช้ **Google Earth Engine (GEE) ผ่าน Python API** เพื่อศึกษาพื้นที่เมืองด้วยข้อมูลภูมิสารสนเทศและ Remote Sensing โดยใช้ **กรุงเทพมหานคร** เป็นตัวอย่างสาธิตหลัก และใช้ **เชียงใหม่** เป็นพื้นที่สำหรับแบบฝึกหัดและการประยุกต์

> กลุ่มเป้าหมายหลัก: นิสิตชั้นปีที่ 3 ด้าน Urban Studies, Geography, Geoinformatics, Environmental Science หรือสาขาที่เกี่ยวข้อง  
> พื้นฐานที่คาดหวัง: เคยใช้ GIS/Remote Sensing เบื้องต้น และรู้ Python เพียงเล็กน้อยก็สามารถเรียนได้

---

## Repository

ชื่อ GitHub repository ที่แนะนำ:

```text
Teach-Urban-RS
```

เมื่อสร้าง repository แล้ว ให้แทนคำว่า `YOUR_GITHUB_USERNAME` ใน README และ Notebook ทั้งหมดด้วย GitHub username ของผู้สอน

ตัวอย่าง URL:

```text
https://github.com/YOUR_GITHUB_USERNAME/Teach-Urban-RS
```

---

# 1. ก่อนเริ่มเรียน: ต้องเตรียมอะไรบ้าง?

Earth Engine ทำงานบน Google Cloud ดังนั้นก่อนใช้ Python API ผู้เรียนต้องมี **Google Cloud Project** ที่เปิดใช้ Earth Engine API และลงทะเบียน Earth Engine เรียบร้อยแล้ว

คู่มือทางการ:

- Earth Engine access: https://developers.google.com/earth-engine/guides/access
- Authentication and initialization: https://developers.google.com/earth-engine/guides/auth
- Python + Colab: https://developers.google.com/earth-engine/guides/python_install-colab
- Noncommercial tiers: https://developers.google.com/earth-engine/guides/noncommercial_tiers

## 1.1 สร้าง Google Cloud Project

1. ลงชื่อเข้าใช้ Google Account
2. เปิด Google Cloud Console: https://console.cloud.google.com/
3. สร้าง Project ใหม่
4. ตั้ง **Project name** เช่น:

```text
Teach Urban RS
```

5. จด **Project ID** ไว้ เพราะ Python ใช้ Project ID ไม่ใช่ Project name

ตัวอย่าง:

```text
Project name: Teach Urban RS
Project ID: teach-urban-rs-123456
```

> Project ID ต้องไม่ซ้ำกับผู้อื่น และเมื่อสร้างแล้วไม่สามารถเปลี่ยนได้

## 1.2 ลงทะเบียน Project เพื่อใช้ Earth Engine

เปิดหน้า:

https://code.earthengine.google.com/register

หรือทำตาม Earth Engine Access Guide

สำหรับการเรียนการสอนในมหาวิทยาลัยโดยทั่วไป:

1. เลือก Existing Google Cloud Project
2. เลือก Project ที่สร้างไว้
3. เลือก **Noncommercial use**
4. ยืนยันการใช้งานด้าน **Education / Academic / Research** ตามแบบฟอร์ม
5. เลือก **Community Tier** สำหรับการเรียนระดับปริญญาตรี
6. ทำแบบสอบถาม/verification ให้เสร็จ
7. ตรวจสอบหน้า Earth Engine Configuration ว่า Project registered แล้ว

> Earth Engine Community Tier เป็น tier ที่ออกแบบมาสำหรับ undergraduate students และงานคำนวณทั่วไป การจัดสรร quota อาจมีการปรับปรุงตามนโยบายของ Google จึงควรตรวจสอบหน้า Noncommercial tiers ก่อนเริ่มภาคการศึกษา

## 1.3 Project name ไม่เท่ากับ Project ID

สิ่งที่แสดงใน Google Cloud:

```text
Teach Urban RS
```

คือ **Project name**

แต่ใน Python ต้องใช้:

```python
ee.Initialize(project="YOUR_GOOGLE_CLOUD_PROJECT_ID")
```

ตัวอย่าง:

```python
ee.Initialize(project="teach-urban-rs-123456")
```

---

# 2. Authentication และ Authorization

สำหรับ Earth Engine Python API มี 2 ขั้นตอนหลัก

```text
Authenticate
    ↓
ยืนยันว่าเราเป็นใคร
    ↓
Initialize
    ↓
ระบุ Cloud Project ที่จะใช้ประมวลผล
```

โค้ดพื้นฐาน:

```python
import ee

ee.Authenticate()
ee.Initialize(project="YOUR_GOOGLE_CLOUD_PROJECT_ID")
```

เมื่อรัน `ee.Authenticate()` ใน Colab ให้:

1. เลือก Google Account ที่ลงทะเบียน Earth Engine
2. อนุญาตสิทธิ์ตามหน้าจอ
3. กลับมาที่ Notebook
4. รัน `ee.Initialize(...)`

> เมื่อ Colab runtime ถูก restart, disconnect หรือถูก recycle อาจต้องรันขั้นตอน setup / authentication ใหม่

---

# 3. การใช้ Google Colab

Google Colab เป็น Jupyter Notebook บน Cloud เหมาะสำหรับรายวิชานี้เพราะไม่ต้องติดตั้ง Python environment บนเครื่องนิสิต

เปิด Colab:

https://colab.research.google.com/

ลำดับการใช้งาน:

```text
Open Notebook
    ↓
Runtime connects
    ↓
Import libraries
    ↓
Authenticate Earth Engine
    ↓
Initialize Project
    ↓
Run cells from top to bottom
```

## Notebook สำหรับทดสอบระบบก่อนเรียน

| Notebook | Open in Colab |
|---|---|
| `000_Earth_Engine_Colab_Setup.ipynb` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/000_Earth_Engine_Colab_Setup.ipynb) |

Notebook 000 ใช้สำหรับ:
- Import Earth Engine Python API
- Authenticate
- Initialize ด้วย Cloud Project
- ทดสอบ Earth Engine API
- ทดลองแสดงข้อมูลบนแผนที่
- ตรวจสอบว่า environment พร้อมก่อนเข้าสู่บทเรียนจริง

**นิสิตทุกคนควรรัน Notebook 000 ให้ผ่านก่อน**

---

# 4. Libraries ที่ใช้ในรายวิชา

| Library | หน้าที่ |
|---|---|
| `earthengine-api (ee)` | เข้าถึงและประมวลผลข้อมูลบน Google Earth Engine |
| `geemap` | แสดง Earth Engine data บน interactive map ใน Colab/Jupyter |
| `pandas` | จัดการข้อมูลตารางและ time series |
| `numpy` | การคำนวณเชิงตัวเลข |
| `matplotlib` | สร้างกราฟเชิงวิชาการ |
| `scipy` | สถิติ เช่น Pearson correlation |
| `scikit-learn` | Simple linear regression และ model เบื้องต้น |
| `folium` | Web map แบบ Leaflet; ใช้เป็น optional extension |

เอกสาร:

- Earth Engine Python API: https://developers.google.com/earth-engine/guides/python_install
- geemap: https://geemap.org/
- geemap in Colab: https://geemap.org/notebooks/00_geemap_colab/
- pandas: https://pandas.pydata.org/docs/
- Matplotlib: https://matplotlib.org/stable/
- SciPy: https://docs.scipy.org/doc/scipy/
- scikit-learn: https://scikit-learn.org/stable/
- Folium: https://python-visualization.github.io/folium/

---

# 5. Remote Sensing Primer: แนวคิดที่ควรรู้ก่อนเขียนโค้ด

## 5.1 Raster และ Vector

**Vector**
- Point
- Line
- Polygon

ตัวอย่างในรายวิชา:
- Bangkok point
- Bangkok boundary
- Random sample points

**Raster**
- Satellite image
- NDVI
- Land Surface Temperature
- Built probability

ใน Earth Engine:

| GIS concept | Earth Engine object |
|---|---|
| Raster 1 ภาพ | `ee.Image` |
| Raster หลายภาพ/หลายเวลา | `ee.ImageCollection` |
| Vector 1 วัตถุ | `ee.Feature` |
| Vector หลายวัตถุ | `ee.FeatureCollection` |
| Geometry | `ee.Geometry` |

---

## 5.2 Pixel และ Resolution

Remote Sensing ต้องเข้าใจ resolution อย่างน้อย 3 แบบ

### Spatial resolution
ขนาดพื้นที่บนพื้นโลกที่ pixel หนึ่งแทน

ตัวอย่าง:
- Sentinel-2: 10, 20 และ 60 m
- Landsat 8: 30 m สำหรับผลิตภัณฑ์ที่ใช้ในรายวิชา
- MODIS: 1 km สำหรับ MOD13A3 และ MOD11A2

### Spectral resolution
จำนวนและตำแหน่งของ wavelength bands

### Temporal resolution
ความถี่ที่ sensor กลับมาสังเกตพื้นที่เดิม

การเลือกข้อมูลจึงเป็น trade-off:

```text
รายละเอียดเชิงพื้นที่สูง
        ↕
ความต่อเนื่องเชิงเวลาสูง
```

Sentinel-2 เหมาะกับ spatial urban pattern ส่วน MODIS เหมาะกับ long/regular time series

---

# 6. Dataset หลักที่ใช้

## 6.1 FAO GAUL 2025 Level 1

Earth Engine ID:

```python
FAO/GAUL/2025/level1
```

ใช้สำหรับ:
- ขอบเขตประเทศไทย
- กรุงเทพมหานคร
- จังหวัดเชียงใหม่

field ที่ใช้:

```text
GAUL0_NAME = Country
GAUL1_NAME = First-level administrative unit
```

ใน Desktop GIS เราอาจใช้ Shapefile แต่ใน Earth Engine ข้อมูล vector ถูกใช้งานผ่าน `FeatureCollection`

Data Catalog:

https://developers.google.com/earth-engine/datasets/catalog/FAO_GAUL_2025_level1

---

## 6.2 Sentinel-2 Level-2A Surface Reflectance Harmonized

Earth Engine ID:

```python
COPERNICUS/S2_SR_HARMONIZED
```

Sentinel-2 MSI Level-2A ใน Earth Engine collection นี้มี **12 spectral bands** สำหรับ Surface Reflectance (ไม่มี B10 ใน L2A SR collection)

| Band | ช่วงคลื่น/หน้าที่ | Pixel size |
|---|---|---:|
| B1 | Aerosol | 60 m |
| B2 | Blue | 10 m |
| B3 | Green | 10 m |
| B4 | Red | 10 m |
| B5 | Red Edge 1 | 20 m |
| B6 | Red Edge 2 | 20 m |
| B7 | Red Edge 3 | 20 m |
| B8 | NIR | 10 m |
| B8A | Narrow NIR / Red Edge 4 | 20 m |
| B9 | Water vapor | 60 m |
| B11 | SWIR 1 | 20 m |
| B12 | SWIR 2 | 20 m |

Surface Reflectance ใช้ scale factor:

$$
\rho = DN \times 0.0001
$$

### True Color

```text
R = B4
G = B3
B = B2
```

### False Color สำหรับ vegetation

```text
R = B8
G = B4
B = B3
```

Data Catalog:

https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED

---

# 7. ดัชนีพืชพรรณ: NDVI

Normalized Difference Vegetation Index:

$$
NDVI = \frac{NIR - Red}{NIR + Red}
$$

สำหรับ Sentinel-2:

$$
NDVI = \frac{B8-B4}{B8+B4}
$$

แนวคิด:
- vegetation ดูดกลืน Red
- vegetation สะท้อน NIR สูง
- vegetation ที่เขียว/หนาแน่นจึงมักมี NDVI สูงขึ้น

> NDVI เป็น spectral index ไม่ใช่ Land Use class และไม่ควรใช้ threshold เดียวแบบตายตัวกับทุกพื้นที่/ฤดูกาล

---

# 8. Dynamic World

Earth Engine ID:

```python
GOOGLE/DYNAMICWORLD/V1
```

Dynamic World เป็น Land Use/Land Cover product ความละเอียด 10 m ที่ให้ probability สำหรับ 9 classes:

1. water
2. trees
3. grass
4. flooded vegetation
5. crops
6. shrub and scrub
7. built
8. bare
9. snow and ice

รายวิชาใช้ `built` probability เป็นหลัก

$$
0 \le P(\mathrm{built}) \le 1
$$

ในแบบฝึกหัดอาจทดลอง threshold:

$$
P(\mathrm{built}) \ge 0.5
$$

> 0.5 เป็น **operational threshold เพื่อการสอน** ไม่ใช่ threshold สากลสำหรับทุกเมือง

Data Catalog:

https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1

---

# 9. Landsat 8 Level-2 และ Land Surface Temperature

Earth Engine ID:

```python
LANDSAT/LC08/C02/T1_L2
```

ใช้สำหรับศึกษาความร้อนพื้นผิวเมือง

## Surface Reflectance scaling

$$
\rho = DN \times 0.0000275 - 0.2
$$

## Surface Temperature

สำหรับ `ST_B10`:

$$
T_K = DN \times 0.00341802 + 149.0
$$

แปลง Kelvin เป็น Celsius:

$$
T_{^\circ C}=T_K-273.15
$$

ข้อสำคัญ:

$$
LST \ne T_{air}
$$

Land Surface Temperature คืออุณหภูมิพื้นผิวเชิงรังสี ไม่ใช่อุณหภูมิอากาศมาตรฐานที่วัดใกล้ระดับ 2 m

แนวคิด surface energy balance แบบง่าย:

$$
R_n = H + LE + G
$$

vegetation มีบทบาทผ่าน evapotranspiration และ latent heat flux ขณะที่ impervious surface มีคุณสมบัติด้านการกักเก็บ/ถ่ายเทความร้อนต่างออกไป

Data Catalog:

https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2

---

# 10. MODIS สำหรับ Time Series

## 10.1 MOD13A3 Monthly Vegetation Indices

Earth Engine ID:

```python
MODIS/061/MOD13A3
```

ลักษณะสำคัญ:
- Temporal resolution: Monthly
- Spatial resolution: 1 km
- มี NDVI และ EVI
- NDVI scale factor = 0.0001

$$
NDVI_{physical} = DN \times 0.0001
$$

ใช้สำหรับศึกษารูปแบบ vegetation ตามฤดูกาลและระหว่างปี

Data Catalog:

https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD13A3

## 10.2 MOD11A2 Land Surface Temperature

Earth Engine ID:

```python
MODIS/061/MOD11A2
```

ลักษณะสำคัญ:
- 8-day composite
- Spatial resolution: 1 km
- มี Daytime และ Nighttime LST
- `LST_Day_1km` scale factor = 0.02 K

$$
T_K = DN \times 0.02
$$

$$
T_{^\circ C}=T_K-273.15
$$

Data Catalog:

https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD11A2

---

# 11. Statistical concepts ที่ใช้ตอนท้าย

## Pearson correlation

ใช้ตรวจสอบทิศทางและความแรงของ linear association ระหว่างตัวแปร เช่น NDVI กับ LST

$$
r =
\frac{\sum (x_i-\bar{x})(y_i-\bar{y})}
{\sqrt{\sum (x_i-\bar{x})^2\sum(y_i-\bar{y})^2}}
$$

$$
-1 \le r \le 1
$$

## Simple Linear Regression

$$
LST_i = \beta_0 + \beta_1 NDVI_i + \epsilon_i
$$

- $\beta_0$ = intercept
- $\beta_1$ = slope
- $R^2$ = สัดส่วนความแปรปรวนที่ linear model อธิบายได้

> Correlation และ Regression แสดง **association** ไม่ได้พิสูจน์ **causation**

Spatial data ยังมีประเด็นสำคัญ เช่น spatial autocorrelation, scale และ confounding variables

---

# 12. ลำดับการเรียน

## 000 — Setup และทดสอบ Earth Engine API

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/000_Earth_Engine_Colab_Setup.ipynb)

**ทำก่อน Notebook อื่นทั้งหมด**

เรียน:
- Import `ee`
- Authenticate
- Initialize Cloud Project
- Test API
- ทดลอง map visualization

---

## 001 — GEE Beginner: Bangkok Step-by-Step

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/001_GEE_Beginner_Bangkok_Step_by_Step.ipynb)

Notebook สำหรับผู้เริ่มต้นโดยเฉพาะ

เรียนแบบ:

```text
Map
→ Point
→ GAUL polygon
→ ImageCollection
→ filterBounds
→ filterDate
→ cloud filter
→ single image
→ RGB
→ False Color
→ cloud mask
→ median composite
→ clip
→ NDVI
→ point query
→ random points
→ table
→ GeoTIFF / CSV / Shapefile
```

เหมาะสำหรับผู้ที่มีพื้นฐาน Python น้อยและต้องการเห็นผลบนแผนที่หลังรันแต่ละช่วง

---

## 01 — Urban Boundary and Satellite Imagery

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/01_Urban_Boundary_and_Satellite_Imagery.ipynb)

เรียน:
- Raster / Vector
- GAUL
- Sentinel-2
- Spatial / Temporal resolution
- True Color / False Color
- Administrative boundary vs Physical urban extent

กรณีสาธิต: Bangkok  
แบบฝึกหัด: Chiang Mai

---

## 02 — Urban Vegetation and Built-up

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/02_Urban_Vegetation_and_Builtup.ipynb)

เรียน:
- Land Cover vs Land Use
- NDVI
- Dynamic World
- Built probability
- Pixel area
- Built-up area และ percentage
- Classification uncertainty

กรณีสาธิต: Bangkok  
แบบฝึกหัด: Chiang Mai

---

## 03 — Urban Heat and Land Surface Temperature

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/03_Urban_Heat_and_LST.ipynb)

เรียน:
- LST vs air temperature
- Urban heat
- Landsat 8 Level-2
- QA masking
- Scale factor
- Kelvin → Celsius
- Professional LST map
- Common color scale
- Urban analysis zone

---

## 04 — Urban Environmental Time Series

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/04_Urban_Time_Series.ipynb)

เรียน:
- MODIS NDVI
- MODIS LST
- ImageCollection → regional statistic
- Earth Engine → Pandas
- Monthly time series
- Seasonal climatology
- Trend / seasonality / variability
- Spatial-temporal resolution trade-off

---

## 05 — Urban Environmental Relationships

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Teach-Urban-RS/blob/main/05_Urban_Environmental_Relationships.ipynb)

เรียน:
- Spatial sampling
- Raster stack
- Scatterplot
- Pearson correlation
- Simple linear regression
- $R^2$
- Association vs causation
- Spatial autocorrelation และ confounding

---

# 13. แผนการเรียนที่แนะนำ

สำหรับนิสิตที่มีพื้นฐาน Python น้อย:

```text
ก่อนเรียน
000 Setup                 30–45 min
        ↓
พื้นฐาน GEE
001 Beginner Bangkok      90–120 min
        ↓
Urban Remote Sensing
01 Boundary + Satellite
02 Vegetation + Built-up
03 Urban Heat
04 Time Series
05 Environmental Relationship
```

ถ้าเวลาเรียนมีเพียงประมาณ 5 ชั่วโมง สามารถใช้ 001 เป็น pre-class/self-study และใช้ 01–05 เป็น core workshop

---

# 14. รูปแบบการเรียนในแต่ละ Notebook

ทุก Notebook เน้นลำดับ:

```text
Concept
  ↓
Code
  ↓
Map / Plot
  ↓
Observe
  ↓
Interpret
  ↓
Exercise
  ↓
Solution
```

หลักสำคัญ:

> **อ่านแผนที่ก่อนคำนวณตัวเลข**

และ

> **เข้าใจ geographic/remote-sensing meaning ก่อนเพิ่มความซับซ้อนของ code**

---

# 15. Basemap ใน Colab

ในบาง environment default OpenStreetMap tile อาจถูก block

ชุด Notebook นี้จึงใช้แนวทาง:

```python
Map = geemap.Map()
Map.clear_layers()

Map.add_basemap("Esri.WorldImagery", show=True)
Map.add_basemap("Esri.WorldStreetMap", show=False)
Map.add_basemap("Esri.WorldTopoMap", show=False)
```

ผู้เรียนสามารถใช้ Layer Control เพื่อเปลี่ยนพื้นหลัง

Basemap ใช้เพื่อการอ้างอิงและการตีความ ไม่ใช่ข้อมูลหลักที่นำมาคำนวณ

---

# 16. ข้อควรระวังทางวิชาการ

1. Administrative boundary ไม่เท่ากับ physical urban extent
2. Land Cover ไม่เท่ากับ Land Use
3. Cloud percentage ระดับ scene ไม่เท่ากับ pixel-level cloud mask
4. Median composite ไม่ได้แปลว่า cloud-free 100%
5. NDVI ไม่ใช่ vegetation class โดยตรง
6. Dynamic World probability มี uncertainty
7. LST ไม่ใช่ air temperature
8. Spatial resolution และ temporal resolution มี trade-off
9. Study-area definition มีผลต่อ summary statistics
10. Correlation/regression ไม่พิสูจน์ causation
11. Pixel-based samples อาจมี spatial autocorrelation

---

# 17. โครงสร้าง Repository

```text
Teach-Urban-RS/
│
├── README.md
├── 000_Earth_Engine_Colab_Setup.ipynb
├── 001_GEE_Beginner_Bangkok_Step_by_Step.ipynb
├── 01_Urban_Boundary_and_Satellite_Imagery.ipynb
├── 02_Urban_Vegetation_and_Builtup.ipynb
├── 03_Urban_Heat_and_LST.ipynb
├── 04_Urban_Time_Series.ipynb
├── 05_Urban_Environmental_Relationships.ipynb
└── requirements.txt
```

---

# 18. ก่อน Upload ขึ้น GitHub

ค้นหาและแทน:

```text
YOUR_GITHUB_USERNAME
```

ด้วย GitHub username ของผู้สอน

และ **อย่า hard-code Project ID ของผู้สอนใน public repository**

ให้นิสิตแก้:

```python
PROJECT = "YOUR_GOOGLE_CLOUD_PROJECT_ID"
```

เป็น Project ID ของตนเอง

---

# 19. References และเอกสารหลัก

### Google Earth Engine
- Access: https://developers.google.com/earth-engine/guides/access
- Authentication: https://developers.google.com/earth-engine/guides/auth
- Python API: https://developers.google.com/earth-engine/guides/python_install
- Colab: https://developers.google.com/earth-engine/guides/python_install-colab
- Data Catalog: https://developers.google.com/earth-engine/datasets/catalog/
- Noncommercial tiers: https://developers.google.com/earth-engine/guides/noncommercial_tiers

### Mapping
- geemap: https://geemap.org/
- geemap Colab tutorial: https://geemap.org/notebooks/00_geemap_colab/
- Folium: https://python-visualization.github.io/folium/

### Data analysis
- pandas: https://pandas.pydata.org/docs/
- NumPy: https://numpy.org/doc/
- Matplotlib: https://matplotlib.org/stable/
- SciPy: https://docs.scipy.org/doc/scipy/
- scikit-learn: https://scikit-learn.org/stable/

### Earth Engine datasets
- GAUL 2025 Level 1: https://developers.google.com/earth-engine/datasets/catalog/FAO_GAUL_2025_level1
- Sentinel-2 SR Harmonized: https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED
- Dynamic World: https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1
- Landsat 8 Level-2: https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2
- MOD13A3: https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD13A3
- MOD11A2: https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD11A2

---

## Teaching philosophy

เป้าหมายของ Repository นี้ไม่ใช่ให้นิสิตจำคำสั่ง Python จำนวนมาก แต่ให้สามารถเชื่อม:

```text
Urban Question
      ↓
Geographic Concept
      ↓
Remote Sensing Data
      ↓
Earth Engine Processing
      ↓
Map / Time Series / Model
      ↓
Scientific Interpretation
```

เมื่อจบชุดบทเรียน ผู้เรียนควรสามารถอธิบายได้ว่า **กำลังใช้ข้อมูลอะไร ที่ resolution เท่าใด ผ่าน processing ใด และผลที่เห็นบนแผนที่/กราฟสามารถตีความได้มากน้อยเพียงใด**
