# Зээлийн эрсдэлийг статистик загварчлалаар үнэлэх

## Төслийн товч

UCI-ийн German Credit dataset дээр borrower-level мэдээлэл ашиглан зээлдэгчийн чанарыг (good/bad) логистик регрессээр үнэлж, accuracy/precision/recall, AUC үзүүлэлтүүдээр гүйцэтгэлийг шалгав. Результат нь Quarto тайлан (`Report.qmd`) болон PDF (`Report.pdf`) хэлбэрээр бий болно, ROC график `_files/fig-roc.pdf` дотор хадгалагдана.

**Гол зорилго:**
- Зээлдэгчийн bad credit магадлал тооцох
- ML/статистикийн логистик регресс загвараар ажиллуулж, үнэлгээ хийх
- Дахин давтагдах тайлангаар үр дүнг тайлагнах

## Төслийн бүтэц

```
Credit-Risk-Analysis/
├── Report.qmd          # Гол тайлан (Quarto)
├── references.bib      # Эшлэлүүд
├── ieee.csl            # Эшлэлийн формат (IEEE)
├── raw_data.csv        # Өгөгдөл (CSV, автоматаар үүснэ)
├── raw_data.Rds        # Өгөгдөл (RDS, автоматаар үүснэ)
├── requirements.txt    # Сонголттой Python багцууд
└── _files/             # Гарсан графикууд
    ├── fig-roc.pdf
    └── fig-pr-glmnet.pdf
```

## Ашиглах технологи

- R 4.x
- Quarto 1.x
- LaTeX (pdflatex; MiKTeX эсвэл TeX Live)
- R багц: `Cairo`, `knitr`, `glmnet`

## Ажиллуулах заавар

1. R-д шаардлагатай багцуудыг суулгана:
   ```r
   install.packages(c("Cairo", "knitr", "glmnet"))
   ```
2. Төслийн хавтас руу орно, дараа нь:
   ```bash
   quarto render Report.qmd
   ```
   (YAML-д `pdf-engine: pdflatex` заасан.)

Гаралт: `Report.pdf`, `_files/fig-roc.pdf`, `_files/fig-pr-glmnet.pdf`, мөн `raw_data.Rds`/`raw_data.csv` автоматаар үүснэ.

## Агуулга (Report.qmd)

1. Өгөгдөл ба эх сурвалж (`@uci_german_credit`, `@uci_ml_repo`)
2. Өгөгдөл бэлтгэх (factor хөрвүүлэлт, target_bad)
3. Судалгааны дизайн (train/test 70/30, үнэлгээний үзүүлэлтүүд)
4. Логистик регресс (`glm(binomial)`) ба коэффициентын хүснэгт
5. Пеналти логистик (`glmnet`, CV AUC, test AUC, PR муруй)
6. Үнэлгээ: confusion matrix, accuracy/precision/recall, ROC/AUC
7. Дүгнэлт
8. Ажиллуулах заавар, Багийн гишүүдийн үүрэг (тайланд)

## Зохицуулалт ба ёс зүй

- Нийтийн German Credit өгөгдөл; хувийн мэдээлэл агуулаагүй.
- Эшлэлүүдийг `references.bib`-д оруулж, тайланд ашигласан газарт нь заасан.
- Код бүхэлдээ тайлан дотор харагдана; дахин давтагдах байдлыг `set.seed(42)` хангана.
