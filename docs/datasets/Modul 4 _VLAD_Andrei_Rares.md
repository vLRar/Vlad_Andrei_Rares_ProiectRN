# 📘 README – Etapa 4: Arhitectura Completă a Aplicației SIA bazată pe Rețele Neuronale

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Vlad Andrei Rares 
[**Link Repository GitHub**](https://github.com/vLRar/Vlad_Andrei_Rares_ProiectRN)
**Data:** [04/12/25]  
---

## Scopul Etapei 4
Această etapă corespunde punctului **5. Dezvoltarea arhitecturii aplicației software bazată pe RN** din lista de 9 etape - slide 2 **RN Specificatii proiect.pdf**.

**Trebuie să livrați un SCHELET COMPLET și FUNCȚIONAL al întregului Sistem cu Inteligență Artificială (SIA). In acest stadiu modelul RN este doar definit și compilat (fără antrenare serioasă).**

### IMPORTANT - Ce înseamnă "schelet funcțional":

 **CE TREBUIE SĂ FUNCȚIONEZE:**
- Toate modulele pornesc fără erori
- Pipeline-ul complet rulează end-to-end (de la date → până la output UI)
- Modelul RN este definit și compilat (arhitectura există)
- Web Service/UI primește input și returnează output

 **CE NU E NECESAR ÎN ETAPA 4:**
- Model RN antrenat cu performanță bună
- Hiperparametri optimizați
- Acuratețe mare pe test set
- Web Service/UI cu funcționalități avansate

**Scopul anti-plagiat:** Nu puteți copia un notebook + model pre-antrenat de pe internet, pentru că modelul vostru este NEANTRENAT în această etapă. Demonstrați că înțelegeți arhitectura și că ați construit sistemul de la zero.

---

##  Livrabile Obligatorii

### 1. Tabelul Nevoie Reală → Soluție SIA → Modul Software (max ½ pagină)
Completați in acest readme tabelul următor cu **minimum 2-3 rânduri** care leagă nevoia identificată în Etapa 1-2 cu modulele software pe care le construiți (metrici măsurabile obligatoriu):

| **Nevoie reală concretă** | **Cum o rezolvă SIA-ul vostru** | **Modul software responsabil** |
|---------------------------|--------------------------------|--------------------------------|
Predicția Producției: Operatorii de rețea electrică trebuie să știe instantaneu câți Wați va produce un parc fotovoltaic pentru a echilibra rețeaua națională.-Sistemul utilizează o Rețea Neuronală antrenată (Inference) care calculează instantaneu puterea estimată (Output) pe baza parametrilor meteo introduși de operator. Modul software responsabil - Predictie.vi
Interactivitate și Vizualizare: Nevoia de a simula scenarii "What-If" (ex: Ce se întâmplă dacă vine o furtună brusc?) fără riscuri fizice. - O interfață grafică  care permite modificarea manuală a parametrilor meteo și vizualizarea instantanee a răspunsului rețelei.	- Modul 3: Predictie.vi 
Lipsa Datelor Istorice: Accesul la date reale de la parcuri fotovoltaice este dificil și costisitor pentru cercetare.	-Dezvoltarea unui simulator numeric propriu care integrează ecuații fizice și zgomot aleator pentru a crea seturi de date infinite.	Modul 1: Generate_Training_Data.vi 

### 2. Contribuția Voastră Originală la Setul de Date – MINIM 40% din Totalul Observațiilor Finale

**Regula generală:** Din totalul de **N observații finale** în `data/processed/`, **minimum 40%** trebuie să fie **contribuția voastră originală**.

#### Cum se calculează 40%:

**Exemplu 1 - Dataset DOAR public în Etapa 3:**

Etapa 3: Ați folosit 10,000 samples dintr-o sursa externa (ex: Kaggle)
Etapa 4: Trebuie să generați/achiziționați date astfel încât:
  
Opțiune A: Adăugați 6,666 samples noi → Total 16,666 (6,666/16,666 = 40%)

#### Tipuri de contribuții acceptate (exemple din inginerie):

Alegeți UNA sau MAI MULTE dintre variantele de mai jos și **demonstrați clar în repository**:

| **Tip contribuție** | **Exemple concrete din inginerie** | **Dovada minimă cerută** |
|---------------------|-------------------------------------|--------------------------|
| **Date sintetice prin metode avansate** | • Simulări efectuate prin aplicatia Generate_Training_Data.vi

#### Declarație obligatorie în README:

Scrieți clar în acest README (Secțiunea 2):

### Contribuția originală la setul de date: 100%

**Total observații finale:** [N] (după Etapa 3 + Etapa 4)
**Observații originale:** [M] ([X]%)

**Tipul contribuției:**
[ ] Date generate prin simulare fizică  
[ ] Date achiziționate cu senzori proprii  
[x] Etichetare/adnotare manuală  
[x] Date sintetice prin metode avansate  

**Descriere detaliată:**
Generarea setului de date a fost realizată integral în mediul LabVIEW prin intermediul modulului original Generate_Training_Data.vi. Am utilizat o metodă de simulare numerică bazată pe modelul matematic al celulei fotovoltaice, care corelează iradianța solară, temperatura ambientală și randamentul tehnologic pentru a calcula puterea electrică debitată.

Modul 2: Neural Network (Definirea Arhitecturii)
În această etapă, modelul de rețea neuronală a fost definit și configurat în interiorul VI-ului de antrenare, utilizând toolkit-ul Super Simple Neural Network din LabVIEW.
    Configurație:
Input Layer: 6 neuroni (corespunzători variabilelor meteo normalizate).
Hidden Layer: Un singur strat ascuns cu 3 neuroni. Această alegere minimizează complexitatea și previne divergența erorii.
Output Layer: 1 neuron (puterea generată în Wați).

Modul 3: Interfața Utilizator (UI / Dashboard)

Modulul de predicție (Predictie.vi) servește drept consolă de control pentru utilizatorul final.
Input: Controale de tip Knob sau Slider pentru setarea manuală a condițiilor de mediu.
Logică: VI-ul încarcă modelul salvat (training.nn), aplică transformările de scalare (ex. Ora/52.07) și rulează motorul de inferență.
Output: Afișaj numeric și grafic (Gauge) care indică producția de energie în timp real.

**Locația codului:** `src/data_acquisition/Generate_Training_Data.vi
**Locația datelor:** `data/processed/date_meteo.csv

**Dovezi:**
- Grafic comparativ: `docs/generated_vs_real.png`
- Setup experimental: `docs/acquisition_setup.jpg` (dacă aplicabil)
- Tabel statistici: `docs/data_statistics.csv`
```

#### Exemple pentru "contribuție originală":
-Simulări fizice realiste cu ecuații și parametri justificați  
-Date reale achiziționate cu senzori proprii (setup documentat)  
-Augmentări avansate cu justificare fizică (ex: simulare perspective camera industrială)  


#### Atenție - Ce NU este considerat "contribuție originală":

- Augmentări simple (rotații, flips, crop) pe date publice  
- Aplicare filtre standard (Gaussian blur, contrast) pe imagini publice  
- Normalizare/standardizare (aceasta e preprocesare, nu generare)  
- Subset dintr-un dataset public (ex: selectat 40% din ImageNet)


---

### 3. Diagrama State Machine a Întregului Sistem (OBLIGATORIE)

**Cerințe:**
- **Minimum 4-6 stări clare** cu tranziții între ele
- **Formate acceptate:** PNG/SVG, pptx, draw.io 
- **Locație:** `docs/state_machine.*` (orice extensie)
- **Legendă obligatorie:** 1-2 paragrafe în acest README: "De ce ați ales acest State Machine pentru nevoia voastră?"

**Stări tipice pentru un SIA:**
```
IDLE → ACQUIRE_DATA → PREPROCESS → INFERENCE → DISPLAY/ACT → LOG → [ERROR] → STOP
                ↑______________________________________________|
```

**Exemple concrete per domeniu de inginerie:**

#### A. Monitorizare continuă proces industrial (vibrații motor, temperaturi, presiuni):
```
IDLE → START_ACQUISITION → COLLECT_SENSOR_DATA → BUFFER_CHECK → 
PREPROCESS (filtrare, FFT) → RN_INFERENCE → THRESHOLD_CHECK → 
  ├─ [Normal] → LOG_RESULT → UPDATE_DASHBOARD → COLLECT_SENSOR_DATA (loop)
  └─ [Anomalie] → TRIGGER_ALERT → NOTIFY_OPERATOR → LOG_INCIDENT → 
                  COLLECT_SENSOR_DATA (loop)
       ↓ [User stop / Emergency]
     SAFE_SHUTDOWN → STOP
```

#### B. Clasificare imagini defecte producție (suduri, suprafețe, piese):
```
IDLE → WAIT_TRIGGER (senzor trecere piesă) → CAPTURE_IMAGE → 
VALIDATE_IMAGE (blur check, brightness) → 
  ├─ [Valid] → PREPROCESS (resize, normalize) → RN_INFERENCE → 
              CLASSIFY_DEFECT → 
                ├─ [OK] → LOG_OK → CONVEYOR_PASS → IDLE
                └─ [DEFECT] → LOG_DEFECT → TRIGGER_REJECTION → IDLE
  └─ [Invalid] → ERROR_IMAGE_QUALITY → RETRY_CAPTURE (max 3×) → IDLE
       ↓ [Shift end]
     GENERATE_REPORT → STOP
```

#### C. Predicție traiectorii robot mobil (AGV, AMR în depozit):
```
IDLE → LOAD_MAP → RECEIVE_TARGET → PLAN_PATH → 
VALIDATE_PATH (obstacle check) →
  ├─ [Clear] → EXECUTE_SEGMENT → ACQUIRE_SENSORS (LIDAR, IMU) → 
              RN_PREDICT_NEXT_STATE → UPDATE_TRAJECTORY → 
                ├─ [Target reached] → STOP_AT_TARGET → LOG_MISSION → IDLE
                └─ [In progress] → EXECUTE_SEGMENT (loop)
  └─ [Obstacle detected] → REPLAN_PATH → VALIDATE_PATH
       ↓ [Emergency stop / Battery low]
     SAFE_STOP → LOG_STATUS → STOP
```

#### D. Predicție consum energetic (turbine eoliene, procese batch):
```
IDLE → LOAD_HISTORICAL_DATA → ACQUIRE_CURRENT_CONDITIONS 
(vânt, temperatură, demand) → PREPROCESS_FEATURES → 
RN_FORECAST (24h ahead) → VALIDATE_FORECAST (sanity checks) →
  ├─ [Valid] → DISPLAY_FORECAST → UPDATE_CONTROL_STRATEGY → 
              LOG_PREDICTION → WAIT_INTERVAL (1h) → 
              ACQUIRE_CURRENT_CONDITIONS (loop)
  └─ [Invalid] → ERROR_FORECAST → USE_FALLBACK_MODEL → LOG_ERROR → 
                ACQUIRE_CURRENT_CONDITIONS (loop)
       ↓ [User request report]
     GENERATE_DAILY_REPORT → STOP
```

stateDiagram-v2
    [*] --> INIT
    
    state "1. INIT (Initializare)" as INIT
    state "2. DATA_GENERATION (Generator)" as GEN
    state "3. TRAINING (Antrenare RN)" as TRAIN
    state "4. PREDICTION (Interfață UI)" as PREDICT
    state "5. ERROR_HANDLING" as ERR

    INIT --> GEN : Start Proiect / Run Generator
    GEN --> TRAIN : Fișier CSV generat cu succes
    GEN --> ERR : Eroare scriere fișier
    
    TRAIN --> PREDICT : Model .nn salvat
    TRAIN --> ERR : Eroare convergență (Infinit)
    
    PREDICT --> TRAIN : Retestare cu alți parametri
    PREDICT --> [*] : Închidere aplicație
    
    ERR --> INIT : Resetare parametri

    

**Notă pentru proiecte simple:**
Chiar dacă aplicația voastră este o clasificare simplă (user upload → classify → display), trebuie să modelați fluxul ca un State Machine. Acest exercițiu vă învață să gândiți modular și să anticipați toate stările posibile (inclusiv erori).

**Legendă obligatorie (scrieți în README):**
INIT - Faza de inițializare în care sistemul verifică prezența toolkit-ului de Neural Network și integritatea folderelor de date (/data/raw, /data/processed).
DATA_GENERATION - Starea în care sunt rulate ecuațiile fizice pentru simularea producției solare si acoperirea norilor. Se generează cele 5.000 de eșantioane originale și se salvează în format CSV.
TRAINING - Motorul de calcul al rețelei. Datele sunt normalizate (ex. Ora/52), iar algoritmul Backpropagation ajustează ponderile arhitecturii MLP (6-3-1). Finalizează prin exportul fișierului training.nn.
PREDICTION - Modelul antrenat este încărcat în memorie, iar sistemul răspunde instantaneu la modificările butoanelor.
ERROR_HANDLING : Gestionarea excepțiilor, precum lipsa fișierului de date sau divergența erorii în timpul antrenării (eroare "Infinit").
### Justificarea State Machine-ului ales:

Am ales această structură deoarece separă clar procesarea de date de interfața cu utilizatorul. Astfel, dacă vrei să reantrenezi rețeaua cu alte date, nu trebuie să modifici interfața de predicție, ci doar să treci din nou prin starea de Training.
Stările principale sunt:

Starea IDLE: Sistemul este pornit, dar așteaptă interacțiunea utilizatorului.
Starea GENERARE (Modul 1): Activată la pornirea generatorului de date. Creează setul de date CSV original cu 5.000 de eșantioane.
Starea ANTRENARE (Modul 2): Sistemul citește datele, execută algoritmul Backpropagation și salvează "creierul" rețelei în fișierul .nn.
Starea PREDICȚIE (Modul 3): Starea de operare continuă. Preia valorile de la butoane, le trece prin rețeaua antrenată și afișează rezultatul.

Tranzițiile critice sunt:
- [STARE_A] → [STARE_B]: [când se întâmplă - ex: "când buffer-ul atinge 1024 samples"]
- [STARE_X] → [ERROR]: [condiții - ex: "când senzorul nu răspunde > 100ms"]

Starea ERROR este esențială pentru că [Fisierele pot sa nu fie selectate corect, datele de antrenare sa fie corupte ].


### 4. Scheletul Complet al celor 3 Module Cerute la Curs (slide 7)

Toate cele 3 module trebuie să **pornească și să ruleze fără erori** la predare. Nu trebuie să fie perfecte, dar trebuie să demonstreze că înțelegeți arhitectura.

| **Modul** | **Python (exemple tehnologii)** | **LabVIEW** | **Cerință minimă funcțională (la predare)** |
|-----------|----------------------------------|-------------|----------------------------------------------|
| **1. Data Logging / Acquisition** | `src/data_acquisition/` | LLB cu VI-uri de generare/achiziție | **MUST:** Produce CSV cu datele voastre (inclusiv cele 40% originale). Cod rulează fără erori și generează minimum 100 samples demonstrative. |
| **2. Neural Network Module** | `src/neural_network/model.py` sau folder dedicat | LLB cu VI-uri RN | **MUST:** Modelul RN definit, compilat, poate fi încărcat. **NOT required:** Model antrenat cu performanță bună (poate avea weights random/inițializați). |
| **3. Web Service / UI** | Streamlit, Gradio, FastAPI, Flask, Dash | WebVI sau Web Publishing Tool | **MUST:** Primește input de la user și afișează un output. **NOT required:** UI frumos, funcționalități avansate. |

#### Detalii per modul:

#### **Modul 1: Data Logging / Acquisition**

**Funcționalități obligatorii:**
- [x] Cod rulează fără erori: src/data/Generate_Training_Data.vi
- [x] Generează CSV în format compatibil cu preprocesarea din Etapa 3
- [x] Include minimum 40% date originale în dataset-ul final
- [x] Documentație în cod: ce date generează, cu ce parametri

#### **Modul 2: Neural Network Module**

**Funcționalități obligatorii:**
- [x] Arhitectură RN definită și compilată fără erori
- [x] Model poate fi salvat și reîncărcat
- [x] Include justificare pentru arhitectura aleasă (în docstring sau README)
- [x] **NU trebuie antrenat** cu performanță bună (weights pot fi random)


#### **Modul 3: Web Service / UI**

**Funcționalități MINIME obligatorii:**
- [x] Propunere Interfață ce primește input de la user (formular, file upload, sau API endpoint)
- [x] Includeți un screenshot demonstrativ în `docs/screenshots/`

**Ce NU e necesar în Etapa 4:**
- UI frumos/profesionist cu grafică avansată
- Funcționalități multiple (istorice, comparații, statistici)
- Predicții corecte (modelul e neantrenat, e normal să fie incorect)
- Deployment în cloud sau server de producție

**Scop:** Prima demonstrație că pipeline-ul end-to-end funcționează: input user → preprocess → model → output.


## Structura Repository-ului la Finalul Etapei 4 (OBLIGATORIE)

**Verificare consistență cu Etapa 3:**

```
proiect-rn-[nume-prenume]/
├── data/
│   ├── raw/
│   ├── processed/
│   ├── generated/  # Date originale
│   ├── train/
│   ├── validation/
│   └── test/
├── src/
│   ├── data_acquisition/
│   ├── preprocessing/  # Din Etapa 3
│   ├── neural_network/
│   └── app/  # UI schelet
├── docs/
│   ├── state_machine.*           #(state_machine.png sau state_machine.pptx sau state_machine.drawio)
│   └── [alte dovezi]
├── models/  # Untrained model
├── config/
├── README.md
├── README_Etapa3.md              # (deja existent)
├── README_Etapa4_Arhitectura_SIA.md              # ← acest fișier completat (în rădăcină)
└── requirements.txt  # Sau .lvproj
```

**Diferențe față de Etapa 3:**
- Adăugat `data/generated/` pentru contribuția dvs originală
- Adăugat `src/data_acquisition/` - MODUL 1
- Adăugat `src/neural_network/` - MODUL 2
- Adăugat `src/app/` - MODUL 3
- Adăugat `models/` pentru model neantrenat
- Adăugat `docs/state_machine.png` - OBLIGATORIU
- Adăugat `docs/screenshots/` pentru demonstrație UI

---

## Checklist Final – Bifați Totul Înainte de Predare

### Documentație și Structură
- [x] Tabelul Nevoie → Soluție → Modul complet (minimum 2 rânduri cu exemple concrete completate in README_Etapa4_Arhitectura_SIA.md)
- [x] Declarație contribuție 40% date originale completată în README_Etapa4_Arhitectura_SIA.md
- [x] Cod generare/achiziție date funcțional și documentat
- [x] Dovezi contribuție originală: grafice + log + statistici în `docs/`
- [x] Diagrama State Machine creată și salvată în `docs/state_machine.*`
- [x] Legendă State Machine scrisă în README_Etapa4_Arhitectura_SIA.md (minimum 1-2 paragrafe cu justificare)
- [x] Repository structurat conform modelului de mai sus (verificat consistență cu Etapa 3)

### Modul 1: Data Logging / Acquisition
- [x] Cod rulează fără erori (`python src/data_acquisition/...` sau echivalent LabVIEW)
- [x] Produce minimum 40% date originale din dataset-ul final
- [x] CSV generat în format compatibil cu preprocesarea din Etapa 3
- [x] Documentație în `src/data_acquisition/README.md` cu:
  - [x] Metodă de generare/achiziție explicată
  - [x] Parametri folosiți (frecvență, durată, zgomot, etc.)
  - [x] Justificare relevanță date pentru problema voastră
- [x] Fișiere în `data/generated/` conform structurii

### Modul 2: Neural Network
- [x] Arhitectură RN definită și documentată în cod (docstring detaliat) - versiunea inițială 
- [x] README în `src/neural_network/` cu detalii arhitectură curentă

### Modul 3: Web Service / UI
- [x] Propunere Interfață ce pornește fără erori (comanda de lansare testată)
- [x] Screenshot demonstrativ în `docs/screenshots/ui_demo.png`
- [x] README în `src/app/` cu instrucțiuni lansare (comenzi exacte)

---

**Predarea se face prin commit pe GitHub cu mesajul:**  
`"Etapa 4 completă - Arhitectură SIA funcțională"`

**Tag obligatoriu:**  
`git tag -a v0.4-architecture -m "Etapa 4 - Skeleton complet SIA"`


