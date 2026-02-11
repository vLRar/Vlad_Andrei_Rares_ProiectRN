## 1. Identificare Proiect

| Câmp | Valoare |
|------|---------|
| **Student** | VLAD Andrei Rares |
| **Grupa / Specializare** | [633AB / Informatică Industrială] |
| **Disciplina** | Rețele Neuronale |
| **Instituție** | POLITEHNICA București – FIIR |
| **Link Repository GitHub** | [URL complet - ex: https://github.com/vLRar/Vlad_Andrei_Rares_ProiectRN] |
| **Acces Repository** | [Public] |
| **Stack Tehnologic** | [LabVIEW] |
| **Domeniul Industrial de Interes (DII)** | [Robotica] |
| **Tip Rețea Neuronală** | [MLP] |

### Rezultate Cheie (Versiunea Finală vs Etapa 6)

| Metric | Țintă Minimă | Rezultat Etapa 6 | Rezultat Final | Îmbunătățire | Status |
|--------|--------------|------------------|----------------|--------------|--------|
| Accuracy (Test Set) | ≥70% | [90%] | [89%] | [+8.4%] | [✓] |
| F1-Score (Macro) | ≥0.65 | [X.XX] | [X.XX] | [+X.XX] | [✓/✗] |
| Latență Inferență | [target student] | [50 ms] | [5 ms] | [66%] | [✓] |
| Contribuție Date Originale | ≥40% | [100%] | [100%] | - | [✓] |
| Nr. Experimente Optimizare | ≥4 | [4] | [4] | - | [✓] |

### Declarație de Originalitate & Politica de Utilizare AI

**Acest proiect reflectă munca, gândirea și deciziile mele proprii.**

Utilizarea asistenților de inteligență artificială (ChatGPT, Claude, Grok, GitHub Copilot etc.) este **permisă și încurajată** ca unealtă de dezvoltare – pentru explicații, generare de idei, sugestii de cod, debugging, structurarea documentației sau rafinarea textelor.

**Nu este permis** să preiau:
- cod, arhitectură RN sau soluție luată aproape integral de la un asistent AI fără modificări și raționamente proprii semnificative,
- dataset-uri publice fără contribuție proprie substanțială (minimum 40% din observațiile finale – conform cerinței obligatorii Etapa 4),
- conținut esențial care nu poartă amprenta clară a propriei mele înțelegeri.

**Confirmare explicită (bifez doar ce este adevărat):**

| Nr. | Cerință                                                                 | Confirmare |
|-----|-------------------------------------------------------------------------|------------|
| 1   | Modelul RN a fost antrenat **de la zero** (weights inițializate random, **NU** model pre-antrenat descărcat) | [x] DA     |
| 2   | Minimum **40% din date sunt contribuție originală** (generate/achiziționate/etichetate de mine) | [x] DA     |
| 3   | Codul este propriu sau sursele externe sunt **citate explicit** în Bibliografie | [x] DA     |
| 4   | Arhitectura, codul și interpretarea rezultatelor reprezintă **muncă proprie** (AI folosit doar ca tool, nu ca sursă integrală de cod/dataset) | [x] DA     |
| 5   | Pot explica și justifica **fiecare decizie importantă** cu argumente proprii | [x] DA     |

**Semnătură student (prin completare):** Declar pe propria răspundere că informațiile de mai sus sunt corecte.

---

## 2. Descrierea Nevoii și Soluția SIA

### 2.1 Nevoia Reală / Studiul de Caz

*[Descrieți în 1-2 paragrafe: Ce problemă concretă din domeniul industrial rezolvă acest proiect? Care este contextul și situația actuală? De ce este importantă rezolvarea acestei probleme?]*

[Completați aici]

Proiectul vizează dezvoltarea unui Sistem cu Inteligență Artificială (SIA) capabil să prezică producția de energie electrică a unui parc fotovoltaic pe baza condițiilor meteorologice (temperatură, iradianță, vânt). Soluția este implementată integral în LabVIEW, utilizând o arhitectură de rețea neuronală de tip MLP (Multi-Layer Perceptron).

Elemente distinctive:

    Pipeline Complet: De la generarea sintetică a datelor (bazată pe modele fizice), la preprocesare, antrenare și inferență în timp real.

    Optimizare: Prin ajustarea hiperparametrilor în Etapa 6, s-a obținut un model compact (3 neuroni) care elimină overfitting-ul și răspunde instantaneu la variațiile climatice.

    Aplicabilitate: Sistemul poate fi utilizat de operatorii de rețea pentru echilibrarea consumului sau pentru detecția defecțiunilor în panouri (prin compararea producției reale cu cea estimată de AI).

### 2.2 Beneficii Măsurabile Urmărite

*[Listați 3-5 beneficii concrete cu metrici țintă]*

1 Optimizarea Echilibrării Rețelei (Grid Balancing):
Metrică: Eroare Medie Pătratică (MSE) redusă la 0.0024 (pe date normalizate).
Beneficiu: Operatorii de rețea pot estima cu o precizie de 96.5% (R2) câtă energie va intra în sistem, reducând necesitatea pornirii centralelor pe gaz pentru compensare.

2 Viteză de Reacție în Timp Real:
Metrică: Latență de inferență < 5 ms per eșantion.
Beneficiu: Sistemul permite ajustarea instantaneă a invertoarelor solare la trecerea norilor, mult mai rapid decât modelele matematice complexe care necesită timp mare de calcul.

3 Eficiență Hardware (Resource Efficiency):
Metrică: Model compact cu doar 3 neuroni ascunși.
Beneficiu: Rețeaua poate rula pe controllere industriale low-cost (PLC, NI myRIO) fără a necesita servere GPU scumpe, reducând costul de implementare al soluției.

4 Robustete la Date Zgomotoase:
Metrică: Stabilitate la variații stocastice (Gaussian Noise).
Beneficiu: Modelul filtrează erorile mici ale senzorilor (zgomot de citire), oferind o curbă de predicție lină și utilizabilă.

### 2.3 Tabel: Nevoie → Soluție SIA → Modul Software

| **Nevoie reală concretă** | **Cum o rezolvă SIA-ul** | **Modul software responsabil** | **Metric măsurabil** |
|---------------------------|--------------------------|--------------------------------|----------------------|
Predicția Producției: Operatorii de rețea electrică trebuie să știe instantaneu câți Wați va produce un parc fotovoltaic pentru a echilibra rețeaua națională.-Sistemul utilizează o Rețea Neuronală antrenată (Inference) care calculează instantaneu puterea estimată (Output) pe baza parametrilor meteo introduși de operator. Modul software responsabil - Predictie.vi
Interactivitate și Vizualizare: Nevoia de a simula scenarii "What-If" (ex: Ce se întâmplă dacă vine o furtună brusc?) fără riscuri fizice. - O interfață grafică  care permite modificarea manuală a parametrilor meteo și vizualizarea instantanee a răspunsului rețelei.	- Modul 3: Predictie.vi 
Lipsa Datelor Istorice: Accesul la date reale de la parcuri fotovoltaice este dificil și costisitor pentru cercetare.	-Dezvoltarea unui simulator numeric propriu care integrează ecuații fizice și zgomot aleator pentru a crea seturi de date infinite.	Modul 1: Generate_Training_Data.vi 

---

## 3. Dataset și Contribuție Originală

### 3.1 Sursa și Caracteristicile Datelor

| Caracteristică | Valoare |
|----------------|---------|
| **Origine date** | Simulare 
| **Sursa concretă** | Dataset : data/processed/date_meteo.csv
| **Număr total observații finale (N)** | [5000] |
| **Număr features** | [ex: 7] |
| **Tipuri de date** | [Numerice /Imagini] |
| **Format fișiere** | [CSV / JPEG / JSON / etc.] |
| **Perioada colectării/generării** | [Noiembrie 2025 - Ianuarie 2026] |

### 3.2 Contribuția Originală (minim 40% OBLIGATORIU)

| Câmp | Valoare |
|------|---------|
| **Total observații finale (N)** | [5000] |
| **Observații originale (M)** | [5000] |
| **Procent contribuție originală** | [100%] |
| **Tip contribuție** | [ Date sintetice] |
| **Locație cod generare** | src/data_acquisition/Generate_Training_Data.vi |
| **Locație date originale** | `data/generated/date_meteo.csv |

**Descriere metodă generare/achiziție:**

Generarea setului de date a fost realizată integral în mediul LabVIEW prin intermediul modulului original Generate_Training_Data.vi, utilizând o metodă de simulare numerică bazată pe fizica semiconductorilor. Simularea a produs un set de 5.000 de eșantioane, variind parametrii cheie precum iradianța solară (0-1000 W/m²), temperatura ambientală (20-45°C) și viteza vântului (0-20 m/s). Un aspect esențial a fost introducerea zgomotului stocastic (Gaussian Noise) peste variabilele de mediu pentru a simula imprecizia senzorilor reali.

[Completați aici]

### 3.3 Preprocesare și Split Date

| Set | Procent | Număr Observații |
|-----|---------|------------------|
| Train | 70% | [3500] |
| Validation | 15% | [750] |
| Test | 15% | [750] |

**Preprocesări aplicate:**
Normalizare Min-Max [0, 1]: Toate variabilele de intrare (Iradianță, Temperatură, Vânt) au fost scalate liniar în intervalul unitar. Aceasta este o cerință critică pentru rețelele neuronale cu funcție de activare Tanh sau Sigmoid.
Scalare Temporală (Time Encoding): Variabila "Oră" a fost normalizată prin împărțirea la durata totală a ciclului (Ora / 24), transformând timpul într-o valoare continuă între 0 și 1.
Randomizare (Shuffling): Datele au fost amestecate aleator înainte de split-uire pentru a elimina corelația temporală (evitând situația în care modelul învață doar "Ziua" și este testat pe "Noapte").
Limitare Fizică (Clamping): Valorile de ieșire negative (apărute statistic la limita răsăritului) sunt forțate la 0, deoarece producția de energie nu poate fi negativă.

**Referințe fișiere:** data/generated/data_meteo.csv
---

## 4. Arhitectura SIA și State Machine

### 4.1 Cele 3 Module Software

| Modul | Tehnologie | Funcționalitate Principală | Locație în Repo |
|-------|------------|---------------------------|-----------------|
Achiziție & Generare Date	LabVIEW (G-Code)	Simulează fizica panoului fotovoltaic și generează profilul de nori cu zgomot stocastic (Gaussian) pentru a crea setul de date sintetic.	src/Generate_Training_Data.vi -src/Calcul_Nori.vi
Rețea Neuronală (Training)	LabVIEW ML Toolkit	Implementează algoritmul Backpropagation pentru antrenarea rețelei MLP (6-3-1), incluzând logica de normalizare a datelor și Early Stopping.	src/Antrenare_Retea.vi
Interfață Utilizator (Inference)	LabVIEW GUI (Front Panel)	Dashboard interactiv care încarcă modelul antrenat și afișează puterea estimată în timp real pe baza input-urilor de la utilizator.	src/Predictie.vi
### 4.2 State Machine

**Locație diagramă:** `docs/datasets/state_machine.drawio` 

**Stări principale și descriere:**

| Stare | Descriere | Condiție Intrare | Condiție Ieșire |
|-------|-----------|------------------|-----------------|
GENERATE_DATA -Rulare simulator fizic și zgomot stocastic -"Apăsare ""Generează""" -Fișier CSV salvat
TRAIN_MODEL- Execuție algoritm - Introducere Dataset, RUN -Model .nn salvat
INFERENCE Calcul putere estimată - Modificare Slider (Input) - Valoare afișată (Predictie)
ERROR_HANDLE -"Gestionare excepții (ex: NaN, fișier lipsă)." -Eroare detectată -Resetare sistem

**Justificare alegere arhitectură State Machine:**

*[1 paragraf: De ce această structură pentru problema voastră specifică?]*

[Completați aici]

Am ales o arhitectură de tip Event-Driven State Machine (Mașină de Stări comandată de evenimente) deoarece permite separarea clară a proceselor consumatoare de timp (Antrenarea durează minute) de interfața cu utilizatorul care trebuie să răspundă instantaneu. În LabVIEW, acest design previne blocarea panoului frontal ("freezing") în timpul calculelor complexe, asigurând o experiență fluidă.

### 4.3 Actualizări State Machine în Etapa 6 (dacă este cazul)

| Componentă Modificată | Valoare Etapa 5 | Valoare Etapa 6 | Justificare Modificare |
|----------------------|-----------------|-----------------|------------------------|
| [ex: Threshold alertă] | [0.5] | [0.35] | [Minimizare False Negatives] |
| [ex: Stare nouă adăugată] | N/A | `CONFIDENCE_CHECK` | [Filtrare predicții incerte] |
| [Completați dacă e cazul] | | | |

---

## 5. Modelul RN – Antrenare și Optimizare

### 5.1 Arhitectura Rețelei Neuronale

```
[Arhitectură MLP - Feed Forward]
Input Layer (6 noduri): [Iradianță, Temp, Vânt, Oră_Norm, Nori, Unghi]
    ↓
Hidden Layer 1 (3 noduri):
    → Funcție Activare: Tanh (Tangenta Hiperbolică)
    → Inițializare Ponderi: Xavier
    ↓
Output Layer (1 nod):
    → Funcție Activare: Lineară (Identity)
    → Rezultat: Putere [Wați]
```

**Justificare alegere arhitectură:**

*[1-2 propoziții: De ce această arhitectură? Ce alternative ați considerat și de ce le-ați respins?]*

[Completați aici]

Am optat pentru o arhitectură minimalistă cu un singur strat ascuns de 3 neuroni, respingând variantele "Deep" (cu 2-3 straturi). Motivul este natura fizică a problemei: relația dintre iradianță și putere este dominant liniară, cu mici corecții neliniare (temperatură). O rețea complexă ar fi memorat zgomotul (Overfitting), în timp ce arhitectura 6-3-1 a demonstrat cea mai bună capacitate de generalizare.

### 5.2 Hiperparametri Finali (Model Optimizat - Etapa 6)

| Hiperparametru | Valoare Finală | Justificare Alegere |
|----------------|----------------|---------------------|
Arhitectura (Hidden Layers) - 1 strat cu 3 neuroni - S-a testat inițial cu 10 neuroni, dar rețeaua intra în Overfitting (memora zgomotul). Arhitectura 6-3-1 s-a dovedit cea mai robustă pentru cele 50.000 de eșantioane.
Learning Rate (Rata de învățare) -	0.01 -	O valoare mai mare (0.1) cauza oscilații puternice ale erorii (grafic instabil). Valoarea 0.01 a asigurat o convergență lentă dar sigură.
Momentum -	0.9 -	Adăugat pentru a accelera ieșirea din minimele locale plate și a stabiliza direcția gradientului.
Număr de Epoci	20000 - 50000	Antrenarea s-a oprit automat când eroarea pe setul de validare nu a mai scăzut timp de 100 de epoci (Early Stopping).

### 5.3 Experimente de Optimizare (minim 4 experimente)

| Exp# | Modificare față de Baseline | Accuracy | F1-Score | Timp Antrenare | Observații |
|------|----------------------------|----------|----------|----------------|------------|
| **Baseline** | Configurația din Etapa 5 | [X.XX%] | [X.XX] | [X min] | Referință |
| Exp 1 | [LR 0.01 → 0.001] | [0.0045] | [0.089] | [45 s] | [Stabil. Antrenarea converge, dar eroarea rămâne relativ mare (Underfit).] |
| Exp 2 | [10 Neuroni - 3 Neuroni] | [0.0024] | [0.965] | [20s] | [Optim. Rețeaua mică generalizează cel mai bine legile fizice.] |
| Exp 3 | [Arhitectura [5,5]] | [0.0042] | [0.94] | [80s] | [Complexitate Inutilă. Timp de calcul 4x mai mare fără câștig de precizie.] |
| Exp 4 | [Activare] | [0.0038] | [0.91] | [25] | [Convergenta Lenta] |
| **FINAL** | [Arhitectura 6-3-1(Exp 2)] | **[0.0024%]** | **[0.965]** | [20s] | **Modelul folosit în producție** |

**Justificare alegere model final:**

Am selectat configurația din Experimentul 2 (3 Neuroni, LR=0.01) deoarece a oferit cel mai bun scor R2 (0.965) și cel mai scurt timp de antrenare.

[Completați aici]

**Referințe fișiere:** `results/optimization_experiments.csv`, `models/optimized_model.h5`

---

## 6. Performanță Finală și Analiză Erori

### 6.1 Metrici pe Test Set (Model Optimizat)

| Metric | Valoare | Target Minim | Status |
|--------|---------|--------------|--------|
| **Accuracy** | [X.XX%] | ≥70% | [✓/✗] |
| **F1-Score (Macro)** | [X.XX] | ≥0.65 | [✓/✗] |
| **Precision (Macro)** | [X.XX] | - | - |
| **Recall (Macro)** | [X.XX] | - | - |

**Îmbunătățire față de Baseline (Etapa 5):**

| Metric | Etapa 5 (Baseline) | Etapa 6 (Optimizat) | Îmbunătățire |
|--------|-------------------|---------------------|--------------|
| Accuracy | [X.XX%] | [X.XX%] | [+X.XX%] |
| F1-Score | [X.XX] | [X.XX] | [+X.XX] |

**Referință fișier:** `results/final_metrics.json`

### 6.2 Confusion Matrix

**Locație:** `docs/confusion_matrix_optimized.png`

**Interpretare:**

| Aspect | Observație |
|--------|------------|
Zona cu cea mai bună performanță	Noapte / Iradianță 0. Rețeaua prezice perfect 0 W, eliminând zgomotul.
Zona cu cea mai slabă performanță	Cer variabil (Nori rapizi). Aici apare un "lag" (întârziere) de ~15 minute în predicție.
Liniaritate	Punctele se aliniază strâns pe diagonala XY, confirmând învățarea legii P∝G.

### 6.3 Analiza Top 5 Erori

| # | Input (descriere scurtă) | Predicție RN | Clasă Reală | Cauză Probabilă | Implicație Industrială |
|---|--------------------------|--------------|-------------|-----------------|------------------------|
1	Răsărit (Ora 6:00)	-2.5 W	15 W	Modelul extrapolează liniar panta nopții.	Neglijabilă (producția e oricum mică).
2	Nor Dens (Ora 13:00)	110 W	40 W	Inerția rețelei la schimbări bruște (Lag).	Critic. Operatorul supraestimează energia disponibilă.
3	Caniculă (45°C)	142 W	130 W	Subestimarea efectului termic negativ.	Risc minor de supraîncălzire a invertoarelor.
4	Vânt Maxim (20m/s)	130 W	135 W	Zgomotul vântului tratat ca eroare.	Neglijabilă (eroare conservatoare).
5	Apus (Ora 20:30)	18 W	5 W	Rețeaua "nu stinge" producția instantaneu.	Pierdere de eficiență la prognoza de seară.

### 6.4 Validare în Context Industrial

**Ce înseamnă rezultatele pentru aplicația reală:**

*[1 paragraf: Traduceți metricile în impact real în domeniul vostru industrial]*

[ex: Din 100 de piese cu defecte reale, modelul detectează corect 78 (Recall=78%). 22 de piese defecte ajung la client - cost estimat: 22 × 50 RON = 1100 RON/lot. În același timp, din 100 piese bune, 8 sunt clasificate greșit ca defecte (FP=8%) - cost reinspecție: 8 × 5 RON = 40 RON/lot.]

Sistemul este suficient de precis pentru a fi utilizat în echilibrarea secundară a rețelei.
Impact Economic: Erorile medii de doar 3.8 W la un panou de 150 W înseamnă o abatere de ~2.5%. Aceasta se încadrează în marja de eroare acceptată de operatorii de distribuție (care tolerează până la 5%).
Siguranță: Faptul că modelul nu dă erori majore (outlieri giganți) îl face sigur pentru automatizare.
**Pragul de acceptabilitate pentru domeniu:** Eroare <5% 
**Status:** Atins
**Plan de îmbunătățire (dacă neatins):** [ex: Augmentare date pentru clasa subreprezentată, ajustare threshold]

---

## 7. Aplicația Software Finală

### 7.1 Modificări Implementate în Etapa 6

| Componentă | Stare Etapa 5 | Modificare Etapa 6 | Justificare |
|------------|---------------|-------------------|-------------|
Input UI	Knob Simplu	Slider cu digital display	Control mai fin al parametrilor de intrare.
Logic UI	Afișare directă	Clampare la Zero	Eliminarea valorilor negative (-2 W) care nu au sens fizic.
Model RN	10_neuroni.nn	training.nn (3 neuroni)	Optimizare viteză și precizie (evitare Overfit).

### 7.2 Screenshot UI cu Model Optimizat

**Locație:** `docs/screenshots/inference_optimized.png`

*[Descriere scurtă: Ce se vede în screenshot? Ce demonstrează?]*

[Completați aici]

### 7.3 Demonstrație Funcțională End-to-End

**Locație dovadă:** `docs/demo/` *(GIF / Video / Secvență screenshots)*

**Fluxul demonstrat:**

| Pas | Acțiune | Rezultat Vizibil |
|-----|---------|------------------|
| 1 | Input | [ex: Upload imagine nouă (NU din train/test)] |
| 2 | Procesare | [ex: Bară de progres + preprocesare vizibilă] |
| 3 | Inferență | [ex: Predicție afișată: "Clasa: Defect, Confidence: 87%"] |
| 4 | Decizie | [ex: Alertă roșie + sunet pentru operator] |

**Latență măsurată end-to-end:** [X] ms  
**Data și ora demonstrației:** [DD.MM.YYYY, HH:MM]

---

## 8. Structura Repository-ului Final

```
proiect-rn-[nume-prenume]/
│
├── README.md                               # ← ACEST FIȘIER (Overview Final Proiect - Pe moodle la Evaluare Finala RN > Upload Livrabil 1 - Proiect RN (Aplicatie Sofware) - trebuie incarcat cu numele: NUME_Prenume_Grupa_README_Proiect_RN.md)
│
├── docs/
│   ├── etapa3_analiza_date.md              # Documentație Etapa 3
│   ├── etapa4_arhitectura_SIA.md           # Documentație Etapa 4
│   ├── etapa5_antrenare_model.md           # Documentație Etapa 5
│   ├── etapa6_optimizare_concluzii.md      # Documentație Etapa 6
│   │
│   ├── state_machine.png                   # Diagrama State Machine inițială
│   ├── state_machine_v2.png                # (opțional) Versiune actualizată Etapa 6
│   ├── confusion_matrix_optimized.png      # Confusion matrix model final
│   │
│   ├── screenshots/
│   │   ├── ui_demo.png                     # Screenshot UI schelet (Etapa 4)
│   │   ├── inference_real.png              # Inferență model antrenat (Etapa 5)
│   │   └── inference_optimized.png         # Inferență model optimizat (Etapa 6)
│   │
│   ├── demo/                               # Demonstrație funcțională end-to-end
│   │   └── demo_end_to_end.gif             # (sau .mp4 / secvență screenshots)
│   │
│   ├── results/                            # Vizualizări finale
│   │   ├── loss_curve.png                  # Grafic loss/val_loss (Etapa 5)
│   │   ├── metrics_evolution.png           # Evoluție metrici (Etapa 6)
│   │   └── learning_curves_final.png       # Curbe învățare finale
│   │
│   └── optimization/                       # Grafice comparative optimizare
│       ├── accuracy_comparison.png         # Comparație accuracy experimente
│       └── f1_comparison.png               # Comparație F1 experimente
│
├── data/
│   ├── README.md                           # Descriere detaliată dataset
│   ├── raw/                                # Date brute originale
│   ├── processed/                          # Date curățate și transformate
│   ├── generated/                          # Date originale (contribuția ≥40%)
│   ├── train/                              # Set antrenare (70%)
│   ├── validation/                         # Set validare (15%)
│   └── test/                               # Set testare (15%)
│
├── src/
│   ├── data_acquisition/                   # MODUL 1: Generare/Achiziție date
│   │   ├── README.md                       # Documentație modul
│   │   ├── generate.py                     # Script generare date originale
│   │   └── [alte scripturi achiziție]
│   │
│   ├── preprocessing/                      # Preprocesare date (Etapa 3+)
│   │   ├── data_cleaner.py                 # Curățare date
│   │   ├── feature_engineering.py          # Extragere/transformare features
│   │   ├── data_splitter.py                # Împărțire train/val/test
│   │   └── combine_datasets.py             # Combinare date originale + externe
│   │
│   ├── neural_network/                     # MODUL 2: Model RN
│   │   ├── README.md                       # Documentație arhitectură RN
│   │   ├── model.py                        # Definire arhitectură (Etapa 4)
│   │   ├── train.py                        # Script antrenare (Etapa 5)
│   │   ├── evaluate.py                     # Script evaluare metrici (Etapa 5)
│   │   ├── optimize.py                     # Script experimente optimizare (Etapa 6)
│   │   └── visualize.py                    # Generare grafice și vizualizări
│   │
│   └── app/                                # MODUL 3: UI/Web Service
│       ├── README.md                       # Instrucțiuni lansare aplicație
│       └── main.py                         # Aplicație principală
│
├── models/
│   ├── untrained_model.h5                  # Model schelet neantrenat (Etapa 4)
│   ├── trained_model.h5                    # Model antrenat baseline (Etapa 5)
│   ├── optimized_model.h5                  # Model FINAL optimizat (Etapa 6) ← FOLOSIT
│   └── final_model.onnx                    # (opțional) Export ONNX pentru deployment
│
├── results/
│   ├── training_history.csv                # Istoric antrenare - toate epocile (Etapa 5)
│   ├── test_metrics.json                   # Metrici baseline test set (Etapa 5)
│   ├── optimization_experiments.csv        # Toate experimentele optimizare (Etapa 6)
│   ├── final_metrics.json                  # Metrici finale model optimizat (Etapa 6)
│   └── error_analysis.json                 # Analiza detaliată erori (Etapa 6)
│
├── config/
│   ├── preprocessing_params.pkl            # Parametri preprocesare salvați (Etapa 3)
│   └── optimized_config.yaml               # Configurație finală model (Etapa 6)
│
├── requirements.txt                        # Dependențe Python (actualizat la fiecare etapă)
└── .gitignore                              # Fișiere excluse din versionare
```

### Legendă Progresie pe Etape

| Folder / Fișier | Etapa 3 | Etapa 4 | Etapa 5 | Etapa 6 |
|-----------------|:-------:|:-------:|:-------:|:-------:|
| `data/raw/`, `processed/`, `train/`, `val/`, `test/` | ✓ Creat | - | Actualizat* | - |
| `data/generated/` | - | ✓ Creat | - | - |
| `src/preprocessing/` | ✓ Creat | - | Actualizat* | - |
| `src/data_acquisition/` | - | ✓ Creat | - | - |
| `src/neural_network/model.py` | - | ✓ Creat | - | - |
| `src/neural_network/train.py`, `evaluate.py` | - | - | ✓ Creat | - |
| `src/neural_network/optimize.py`, `visualize.py` | - | - | - | ✓ Creat |
| `src/app/` | - | ✓ Creat | Actualizat | Actualizat |
| `models/untrained_model.*` | - | ✓ Creat | - | - |
| `models/trained_model.*` | - | - | ✓ Creat | - |
| `models/optimized_model.*` | - | - | - | ✓ Creat |
| `docs/state_machine.*` | - | ✓ Creat | - | (v2 opțional) |
| `docs/etapa3_analiza_date.md` | ✓ Creat | - | - | - |
| `docs/etapa4_arhitectura_SIA.md` | - | ✓ Creat | - | - |
| `docs/etapa5_antrenare_model.md` | - | - | ✓ Creat | - |
| `docs/etapa6_optimizare_concluzii.md` | - | - | - | ✓ Creat |
| `docs/confusion_matrix_optimized.png` | - | - | - | ✓ Creat |
| `docs/screenshots/` | - | ✓ Creat | Actualizat | Actualizat |
| `results/training_history.csv` | - | - | ✓ Creat | - |
| `results/optimization_experiments.csv` | - | - | - | ✓ Creat |
| `results/final_metrics.json` | - | - | - | ✓ Creat |
| **README.md** (acest fișier) | Draft | Actualizat | Actualizat | **FINAL** |

*\* Actualizat dacă s-au adăugat date noi în Etapa 4*

### Convenție Tag-uri Git

| Tag | Etapa | Commit Message Recomandat |
|-----|-------|---------------------------|
| `v0.3-data-ready` | Etapa 3 | "Etapa 3 completă - Dataset analizat și preprocesat" |
| `v0.4-architecture` | Etapa 4 | "Etapa 4 completă - Arhitectură SIA funcțională" |
| `v0.5-model-trained` | Etapa 5 | "Etapa 5 completă - Accuracy=X.XX, F1=X.XX" |
| `v0.6-optimized-final` | Etapa 6 | "Etapa 6 completă - Accuracy=X.XX, F1=X.XX (optimizat)" |

---

## 9. Instrucțiuni de Instalare și Rulare

### 9.1 Cerințe Preliminare

```
Python >= 3.8 (recomandat 3.10+)
pip >= 21.0
[sau LabVIEW >= 2020 pentru proiecte LabVIEW]
```

### 9.2 Instalare

```bash
# 1. Clonare repository
git clone [URL_REPOSITORY]
cd proiect-rn-[nume-prenume]

# 2. Creare mediu virtual (recomandat)
python -m venv venv
source venv/bin/activate        # Linux/Mac
# sau: venv\Scripts\activate    # Windows

# 3. Instalare dependențe
pip install -r requirements.txt
```

### 9.3 Rulare Pipeline Complet

```bash
# Pasul 1: Preprocesare date (dacă rulați de la zero)
python src/preprocessing/data_cleaner.py
python src/preprocessing/data_splitter.py --stratify --random_state 42

# Pasul 2: Antrenare model (pentru reproducere rezultate)
python src/neural_network/train.py --config config/optimized_config.yaml

# Pasul 3: Evaluare model pe test set
python src/neural_network/evaluate.py --model models/optimized_model.h5

# Pasul 4: Lansare aplicație UI
streamlit run src/app/main.py
# sau: python src/app/main.py (pentru Flask/FastAPI)
# sau: [instrucțiuni LabVIEW dacă aplicabil]
```

### 9.4 Verificare Rapidă 

```bash
# Verificare că modelul se încarcă corect
python -c "from src.neural_network.model import load_model; m = load_model('models/optimized_model.h5'); print('✓ Model încărcat cu succes')"

# Verificare inferență pe un exemplu
python src/neural_network/evaluate.py --model models/optimized_model.h5 --quick-test
```

### 9.5 Structură Comenzi LabVIEW (dacă aplicabil)

```
[Completați dacă proiectul folosește LabVIEW]
1. Deschideți [nume_proiect].lvproj
2. Rulați Main.vi
3. ...
```

---

## 10. Concluzii și Discuții

### 10.1 Evaluare Performanță vs Obiective Inițiale

| Obiectiv Definit (Secțiunea 2) | Target | Realizat | Status |
|--------------------------------|--------|----------|--------|
| [Obiectiv 1 din 2.2] | [target] | [realizat] | [✓/✗] |
| [Obiectiv 2 din 2.2] | [target] | [realizat] | [✓/✗] |
| Accuracy pe test set | ≥70% | [X.XX%] | [✓/✗] |
| F1-Score pe test set | ≥0.65 | [X.XX] | [✓/✗] |
| [Metric specific domeniului] | [target] | [realizat] | [✓/✗] |

### 10.2 Ce NU Funcționează – Limitări Cunoscute

*[Fiți onești - evaluatorul apreciază identificarea clară a limitărilor]*

1. **Limitare 1:** [ex: Modelul eșuează pe imagini cu iluminare <50 lux - accuracy scade la 45%]
2. **Limitare 2:** [ex: Latența depășește 100ms pentru batch size >32 - neadecvat pentru real-time]
3. **Limitare 3:** [ex: Clasa "defect_minor" are recall doar 52% - date insuficiente]
4. **Funcționalități planificate dar neimplementate:** [ex: Export ONNX, integrare API extern]

### 10.3 Lecții Învățate (Top 5)

1. **[Lecție 1]:** [ex: Importanța EDA înainte de antrenare - am descoperit 8% valori lipsă care afectau convergența]
2. **[Lecție 2]:** [ex: Early stopping a prevenit overfitting sever - fără el, val_loss creștea după epoca 20]
3. **[Lecție 3]:** [ex: Augmentările specifice domeniului (zgomot gaussian calibrat) au adus +5% accuracy vs augmentări generice]
4. **[Lecție 4]:** [ex: Threshold-ul default 0.5 nu e optim pentru clase dezechilibrate - ajustarea la 0.35 a redus FN cu 40%]
5. **[Lecție 5]:** [ex: Documentarea incrementală (la fiecare etapă) a economisit timp major la integrare finală]

### 10.4 Retrospectivă

**Ce ați schimba dacă ați reîncepe proiectul?**

*[1-2 paragrafe: Decizii pe care le-ați lua diferit, cu justificare bazată pe experiența acumulată]*

[Completați aici]

### 10.5 Direcții de Dezvoltare Ulterioară

| Termen | Îmbunătățire Propusă | Beneficiu Estimat |
|--------|---------------------|-------------------|
| **Short-term** (1-2 săptămâni) | [ex: Augmentare date pentru clasa subreprezentată] | [ex: +10% recall pe clasa "defect_minor"] |
| **Medium-term** (1-2 luni) | [ex: Implementare model ensemble] | [ex: +3-5% accuracy general] |
| **Long-term** | [ex: Deployment pe edge device (Raspberry Pi)] | [ex: Latență <20ms, cost hardware redus] |

---

## 11. Bibliografie

*[Minimum 3 surse cu DOI/link funcțional - format: Autor, Titlu, Anul, Link]*

1. [Autor], [Titlu articol/carte], [Anul]. DOI: [link] sau URL: [link]
2. [Autor], [Titlu articol/carte], [Anul]. DOI: [link] sau URL: [link]
3. [Autor], [Titlu articol/carte], [Anul]. DOI: [link] sau URL: [link]
4. [Surse suplimentare dacă este cazul]

**Exemple format:**
- Abaza, B., 2025. AI-Driven Dynamic Covariance for ROS 2 Mobile Robot Localization. Sensors, 25, 3026. https://doi.org/10.3390/s25103026
- Keras Documentation, 2024. Getting Started Guide. https://keras.io/getting_started/

---

## 12. Checklist Final (Auto-verificare înainte de predare)

### Cerințe Tehnice Obligatorii

- [ ] **Accuracy ≥70%** pe test set (verificat în `results/final_metrics.json`)
- [ ] **F1-Score ≥0.65** pe test set
- [ ] **Contribuție ≥40% date originale** (verificabil în `data/generated/`)
- [ ] **Model antrenat de la zero** (NU pre-trained fine-tuning)
- [ ] **Minimum 4 experimente** de optimizare documentate (tabel în Secțiunea 5.3)
- [ ] **Confusion matrix** generată și interpretată (Secțiunea 6.2)
- [ ] **State Machine** definit cu minimum 4-6 stări (Secțiunea 4.2)
- [ ] **Cele 3 module funcționale:** Data Logging, RN, UI (Secțiunea 4.1)
- [ ] **Demonstrație end-to-end** disponibilă în `docs/demo/`

### Repository și Documentație

- [ ] **README.md** complet (toate secțiunile completate cu date reale)
- [ ] **4 README-uri etape** prezente în `docs/` (etapa3, etapa4, etapa5, etapa6)
- [ ] **Screenshots** prezente în `docs/screenshots/`
- [ ] **Structura repository** conformă cu Secțiunea 8
- [ ] **requirements.txt** actualizat și funcțional
- [ ] **Cod comentat** (minim 15% linii comentarii relevante)
- [ ] **Toate path-urile relative** (nu absolute: `/Users/...` sau `C:\...`)

### Acces și Versionare

- [ ] **Repository accesibil** cadrelor didactice RN (public sau privat cu acces)
- [ ] **Tag `v0.6-optimized-final`** creat și pushed
- [ ] **Commit-uri incrementale** vizibile în `git log` (nu 1 commit gigantic)
- [ ] **Fișiere mari** (>100MB) excluse sau în `.gitignore`

### Verificare Anti-Plagiat

- [ ] Model antrenat **de la zero** (weights inițializate random, nu descărcate)
- [ ] **Minimum 40% date originale** (nu doar subset din dataset public)
- [ ] Cod propriu sau clar atribuit (surse citate în Bibliografie)

---

## Note Finale

**Versiune document:** FINAL pentru examen  
**Ultima actualizare:** [DD.MM.YYYY]  
**Tag Git:** `v0.6-optimized-final`

---

*Acest README servește ca documentație principală pentru Livrabilul 1 (Aplicație RN). Pentru Livrabilul 2 (Prezentare PowerPoint), consultați structura din RN_Specificatii_proiect.pdf.*
