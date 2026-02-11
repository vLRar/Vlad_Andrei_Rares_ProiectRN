# 📘 README – Etapa 3: Analiza și Pregătirea Setului de Date pentru Rețele Neuronale

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Vlad Andrei Rares 
[**Link Repository GitHub**](https://github.com/vLRar/Vlad_Andrei_Rares_ProiectRN)
**Data:** [20.11.2025]  

---

## Introducere

Acest document descrie activitățile realizate în **Etapa 3**, în care se analizează și se preprocesează setul de date necesar proiectului „Rețele Neuronale". Scopul etapei este pregătirea corectă a datelor pentru instruirea modelului RN, respectând bunele practici privind calitatea, consistența și reproductibilitatea datelor.

---

##  1. Structura Repository-ului Github (versiunea Etapei 3)

```
project-name/
├── README.md
├── docs/
│   └── datasets/          # descriere seturi de date, surse, diagrame
├── data/
│   ├── raw/               # date brute
│   ├── processed/         # date curățate și transformate
│   ├── train/             # set de instruire
│   ├── validation/        # set de validare
│   └── test/              # set de testare
├── src/
│   ├── preprocessing/     # funcții pentru preprocesare
│   ├── data_acquisition/  # generare / achiziție date (dacă există)
│   └── neural_network/    # implementarea RN (în etapa următoare)
├── config/                # fișiere de configurare
└── requirements.txt       # dependențe Python (dacă aplicabil)
```

---

##  2. Descrierea Setului de Date

### 2.1 Sursa datelor

Metoda de achiziție: Simulare software (Generate_Training_Data.vi).
Volumul datelor: 5.000 de eșantioane (rânduri).
Format: Fișier .csv (Comma Separated Values).

### 2.2 Caracteristicile dataset-ului

Dimensiune (Instances): 5.000 de înregistrări (rânduri).
Număr de atribute (Features): 7 variabile totale, împărțite astfel:
   6 Variabile Independente (Intrări): Temperatură, Vânt, Radiație, Oră, Eficiență, Nori.
   1 Variabilă Dependentă (Țintă/Target): Producția de Energie (Output).
* **Tipuri de date:** ☐ Numerice
* **Format fișiere:** ☐ CSV / ☐ JPG

### 2.3 Descrierea fiecărei caracteristici

| **Caracteristică** | **Tip** | **Unitate** | **Descriere** | **Domeniu valori**  (Normalizat)|
|-------------------|---------|-------------|---------------|--------------------|
Temperatura - Numeric - °C - Temperatura ambientala - 0.40-089
Vant - Numeric - m/s - Viteza vantului - 0.00-0.50
Radiatie - Numeric - W/m² - Energia Solara - 0.00 - 0.98
Ora - Numeric - Momentul zilei - 0.00 - 1.00
Eficienta - Numeric - Randamentul tehnologic al panoului - 0.15(fix)
Nori - Numeric - % - Gradul de acoperire al cerului - 0.00-1.00
Productie - Numeric - W - Energia electrica generata - 0.00 - 146.4

**Fișier recomandat:**  `data/processed/date_meteo.csv

---

##  3. Analiza Exploratorie a Datelor (EDA) – Sintetic

### 3.1 Statistici descriptive aplicate

Distribuția Radiației: Variază între 0 și ~1000 W/m².

Distribuția Orelor: Inițial, variabila Ora a fost cumulativă (0 - 52 ore), necesitând normalizare specifică.

### 3.2 Analiza calității datelor

Valori Lipsă (Missing Values): 0%.
Nu există duplicate accidentale. Deși există multe rânduri cu Output = 0 (noaptea),


### 3.3 Probleme identificate

Aproximativ 87% dintre inregistrari au productia egala cu 0 sau aproape de 0 adica orele de noapte
Descriere: Datele brute erau ordonate cronologic (Noapte → Zi → Noapte).



##  4. Preprocesarea Datelor

### 4.1 Curățarea datelor

Datele fiind generate sintetic, nu au existat valori lipsă (NaN) sau duplicate eronate.
S-a verificat consistența fizică (ex: să nu existe radiație negativă).

### 4.2 Transformarea caracteristicilor

Rețelele neuronale funcționează optim cu date în intervalul [0,1]. Am aplicat Normalizarea Min-Max manuală sau automată pentru fiecare coloană critică:
Temperatura: Împărțită la 50 (Max estimat).
Radiația: Împărțită la 1000.
Ora: Împărțită la 24
Vânt: Împărțit la 20.

### 4.3 Structurarea seturilor de date

Setul de date procesat (5.000 de mostre) a fost structurat pentru a fi utilizat în modulul de antrenare LabVIEW (Antrenare_Retea.vi):
Set de Instruire (Training Set): 80% (4.000 mostre). 
Set de Validare (Validation Set): 20% (1.000 mostre). 

**Principii respectate:**
* Stratificare pentru clasificare
* Fără scurgere de informație (data leakage)
* Statistici calculate DOAR pe train și aplicate pe celelalte seturi

### 4.4 Salvarea rezultatelor preprocesării

* Date preprocesate în `data/processed/`
* Seturi train/val/test în foldere dedicate
* Parametrii de preprocesare în `config/preprocessing_config.*` (opțional)

---

##  5. Fișiere Generate în Această Etapă

* data/raw/cloud samples – poze folosite la testare
* data/processed/date_meteo.csv – date curățate & transformate
* data/train/training.nn - fisierul incarcat de modulul Predictie.vi pentru a genera estimari
* data/train/training_model.nn - iesirea bruta a algoritimului de antrenare

---

##  6. Stare Etapă (de completat de student)

- [x] Structură repository configurată
- [x] Dataset analizat (EDA realizată)
- [x] Date preprocesate
- [x] Seturi train/val/test generate
- [x] Documentație actualizată în README + `data/README.md`

---
