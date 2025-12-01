# Зээлийн эрсдэл, алдагдлын хандлага

## Төслийн танилцуулга

Энэхүү төсөл нь зээлийн эрсдэл, алдагдлын хандлагыг статистик аргаар судалж, ойрын жилүүдийн прогноз гаргах зорилготой. UCI Machine Learning Repository-аас "German Credit" dataset ашиглана.

**Гол зорилго:**
- Зээлийн эрсдэл, алдагдлын хандлагыг статистик аргаар судлах
- Ойрын жилүүдийн (2024-2026) прогноз гаргах
- Статистик шинжилгээний практик дадал чадвар эзэмшүүлэх

## Төслийн бүтэц

```
Credit Risk Analysis/
├── Report.qmd          # Гол тайлбарын файл (Quarto)
├── references.bib      # Эшлэлийн жагсаалт
├── ieee.csl           # IEEE citation style
├── _config.yml        # Jupyter Book тохиргоо
├── _toc.yml           # Агуулгын жагсаалт
├── raw_data.csv       # Өгөгдөл (CSV формат)
├── raw_data.Rds       # Өгөгдөл (R формат, автоматаар үүснэ)
├── requirements.txt   # Python багцууд (сонголттой)
└── _files/            # График, зураг хадгалах folder
    ├── fig-risk-per-year.pdf
    └── fig-prediction.pdf
```

## Шаардлага

### Програм хангамж

- **R** (4.0+) - [Суулгах](https://cran.r-project.org/)
- **Quarto** (1.0+) - [Суулгах](https://quarto.org/docs/get-started/)
- **XeLaTeX** (PDF үүсгэхэд) - MiKTeX эсвэл TeX Live

### R багцууд

Дараах R багцууд шаардлагатай:

- `MASS` - Урвасан бином регресс
- `AER` - Dispersion test
- `Cairo` - PDF график үүсгэх
- `knitr` - Тайлан үүсгэх

## Setup (Суулгах)

### Алхам 1: R ба Quarto суулгах

#### Windows дээр:

1. **R суулгах:**
   - [CRAN вэбсайт](https://cran.r-project.org/) руу орох
   - Windows installer татаж авах, суулгах

2. **Quarto суулгах:**
   - [Quarto вэбсайт](https://quarto.org/docs/get-started/) руу орох
   - Windows installer татаж авах, суулгах
   - **Эсвэл** RStudio ашиглах (Quarto дотроо багтсан)

3. **Шалгах:**
   ```powershell
   R --version
   quarto --version
   ```

### Алхам 2: R багцууд суулгах

#### Арга 1: R Console ашиглах (Зөвлөмжлөсөн)

1. **R Console нээх:**
   - Windows: Start → R → R x64 4.x.x
   - Эсвэл RStudio → Console tab

2. **Ажлын directory тохируулах:**
   ```r
   setwd("C:/Users/HP/Documents/prob/Credit Risk Analysis")
   ```

3. **Багцууд суулгах:**
   ```r
   install.packages(c("MASS", "AER", "Cairo", "knitr"))
   ```

4. **Шалгах:**
   ```r
   library(MASS)
   library(AER)
   library(Cairo)
   library(knitr)
   ```

#### Арга 2: RStudio ашиглах

1. RStudio нээх
2. Packages tab → Install → багцуудын нэрийг оруулах
3. Install товч дарах

### Алхам 3: XeLaTeX суулгах (PDF үүсгэхэд)

**Windows:**
- [MiKTeX](https://miktex.org/download) суулгах
- Эсвэл [TeX Live](https://www.tug.org/texlive/) суулгах

**Тэмдэглэл:** Хэрэв XeLaTeX байхгүй бол HTML формат ашиглаж болно.

## Ажиллуулах заавар

### Арга 1: RStudio ашиглах (Хамгийн хялбар)

1. **RStudio нээх**
2. **File** → **Open File...** → `Report.qmd` сонгох
3. Дээд хэсэгт **"Render"** товч дарах (эсвэл `Ctrl+Shift+K`)
4. PDF тайлан автоматаар үүснэ

### Арга 2: Terminal/PowerShell ашиглах

```powershell
# Төслийн folder руу шилжих
cd "C:\Users\HP\Documents\prob\Credit Risk Analysis"

# Тайлан үүсгэх
quarto render Report.qmd
```

### Арга 3: R Console ашиглах

```r
# Ажлын directory тохируулах
setwd("C:/Users/HP/Documents/prob/Credit Risk Analysis")

# Quarto багц ачаалах
library(quarto)

# Тайлан үүсгэх
quarto_render("Report.qmd")
```

## Үр дүн

Амжилттай ажиллуулсны дараа:

- **Report.pdf** - PDF тайлан үүснэ
- **_files/** folder дотор графикууд үүснэ:
  - `fig-risk-per-year.pdf` - Эрсдэл, алдагдлын хандлага
  - `fig-prediction.pdf` - Прогноз
- **raw_data.Rds** - Татаж авсан өгөгдөл (автоматаар үүснэ)

## Өгөгдөл

### Эх сурвалж

- **Dataset:** UCI Machine Learning Repository - German Credit Dataset
- **URL:** https://archive.ics.uci.edu/ml/datasets/statlog+(german+credit+data)
- **Өгөгдлийн хэмжээ:** 1000 зээлдэгч

### Өгөгдлийн тайлбар

- **class:** Зээлийн эрсдэлийн үнэлгээ
  - `1` = good credit (эрсдэлгүй зээл)
  - `2` = bad credit (эрсдэлтэй зээл)
- **credit_amount:** Зээлийн хэмжээ
- **duration:** Зээлийн хугацаа (сар)
- Бусад зээлдэгчийн мэдээлэл

### Өгөгдөл татаж авах

Өгөгдөл автоматаар татагдана (`Report.qmd` ажиллуулахад). Хэрэв татаж чадахгүй бол:

1. Интернэт холболт шалгах
2. `raw_data.Rds` файлыг устгаад дахин оролдох
3. Алдаа гарвал жишээ өгөгдөл автоматаар үүснэ

## Төслийн агуулга

### 1. Өгөгдөл
- UCI Machine Learning Repository-аас German Credit dataset
- Өгөгдлийн бэлтгэл, шинжилгээ

### 2. Зээлийн эрсдэл, алдагдлын үзүүлэлтүүд
- Dataset-ийн үндсэн статистик
- Жил бүрээр эрсдэлийн хандлага
- График дүрслэл

### 3. Зээлийн эрсдэл, алдагдлын хандлага
- Спирмэний рангийн корреляцийн шинжилгээ
- Статистик таамаглал шалгалт

### 4. Зээлийн эрсдэл, алдагдлын загварчлал
- Шугаман регресс (эрсдэлтэй зээлийн хувь)
- Ложистик регресс (эрсдэлтэй зээлийн хувь)
- Урвасан бином регресс (алдагдлын хэмжээ)
- Детерминацийн коэффициент (R²)

### 5. Зээлийн эрсдэл, алдагдлын прогноз
- 2024-2026 оны урьдчилсан байдал
- График дээрх харагдах байдал

## Техникийн мэдээлэл

### Ашигласан арга зүй

1. **Корреляцийн шинжилгээ:**
   - Спирмэний рангийн корреляц (параметрийн бус)
   - `cor.test()` функц

2. **Регрессийн загвар:**
   - Шугаман регресс (`lm()`)
   - Ложистик регресс (`glm()`, `family = binomial`)
   - Урвасан бином регресс (`MASS::glm.nb()`)

3. **Overdispersion шалгалт:**
   - `AER::dispersiontest()`

4. **Детерминацийн коэффициент:**
   - Шугаман регрессийн R²
   - McFadden-ийн псевдо R² (логистик, урвасан бином регресс)

### Өгөгдлийн формат

- **CSV:** `raw_data.csv` - хүснэгт формат
- **RDS:** `raw_data.Rds` - R обьект формат (автоматаар үүснэ)

## Алдаа засах

### Алдаа 1: "quarto: command not found"

**Шийдэл:**
- Quarto суулгах: https://quarto.org/docs/get-started/
- Эсвэл RStudio ашиглах

### Алдаа 2: "Package not found" (R)

**Шийдэл:**
```r
# CRAN mirror сонгох
chooseCRANmirror()

# Дахин суулгах
install.packages(c("MASS", "AER", "Cairo", "knitr"))
```

### Алдаа 3: "Cannot download data"

**Шийдэл:**
- Интернэт холболт шалгах
- Алдаа гарвал жишээ өгөгдөл автоматаар үүснэ

### Алдаа 4: "XeLaTeX not found" (PDF үүсгэхэд)

**Шийдэл:**
- MiKTeX эсвэл TeX Live суулгах
- Windows: https://miktex.org/download
- Эсвэл HTML формат ашиглах

### Алдаа 5: Warning мессежүүд PDF дээр харагдах

**Шийдэл:**
- `Report.qmd` файлд `warning: false` тохиргоо байгаа эсэхийг шалгах
- Глобал тохиргоонд `execute: warning: false` байгаа эсэхийг шалгах

## Хурдан заавар (RStudio)

1. ✅ RStudio нээх
2. ✅ `Report.qmd` файл нээх
3. ✅ `Ctrl+Shift+K` дарах (Render)
4. ✅ Хүлээх (PDF үүсэх хүртэл)
5. ✅ `Report.pdf` файлыг нээх

## Тэмдэглэл

- Эхний удаа ажиллуулахад удаан хугацаа шаардагдаж болно (өгөгдөл татахад)
- Интернэт холболт шаардлагатай (UCI-аас өгөгдөл татахад)
- R багцууд эхний удаа суулгах шаардлагатай
- Dataset нь Германы банкуудын зээлийн эрсдэлийн үнэлгээний өгөгдөл агуулдаг
- Олон улсын стандарт dataset тул машин сургалтын судалгаанд өргөн ашиглагддаг

## Эшлэл

Эшлэлийн жагсаалтыг `references.bib` файлд агуулсан. IEEE формат ашигласан.

## Огноо

2025 оны 11-р сарын 20
