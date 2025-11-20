# 📘 README – Etapa 3: Analiza și Pregătirea Setului de Date pentru Rețele Neuronale

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR 633AB 
**Student:** Vlad-Andrei-Rares
**Data:** 20/11/2025

## Introducere

Acest document descrie activitățile realizate în **Etapa 3**, în care se analizează și se preprocesează setul de date necesar proiectului „Predictia Productiei de energie solara in functie de conditiile meteorologice folosind retele neuronale". Scopul etapei este pregătirea corectă a datelor pentru instruirea modelului RN, respectând bunele practici privind calitatea, consistența și reproductibilitatea datelor.

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


##  2. Descrierea Setului de Date

-Acoperirea norilor - procentul sau nivelul de înnorare

-Viteza vantului - intensitatea vântului, afecteaza temperatura panourilor

-Ora - important pentru poziția soarelui și variația naturală a radiației solare.

-Data - include informații sezoniere

-Gradul de umbrire al panourilor (imagine) - proceseaza o imagine cu panoul solar si determina cata energie poate produce

-Radiatia solara - intensitatea energiei solare disponibile pe suprafața panourilor

-Umiditatea - cantitatea de vapori de apă din aer, care poate afecta transmiterea radiației solare.

-Nivelul de productie al panoului - energia generată de panou la un anumit moment, folosită ca variabilă țintă pentru antrenare.


### 2.1 Sursa datelor

* **Origine: dataset public
* **Modul de achiziție: Fișier extern 
* **Perioada / condițiile colectării:

### 2.2 Caracteristicile dataset-ului

* **Număr total de observații:
* **Număr de caracteristici (features):
* **Tipuri de date: Numerice / Imagini
* **Format fișiere:  TXT /  JPG 

