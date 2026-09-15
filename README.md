<p align="center">
  <img src="Gemini_Generated_Image_qunro2qunro2qunr.jpeg" alt="SolarPredict Logo" width="600"/>
</p>

# SolarPredict ☀️🤖
**Machine Learning Pipeline per la Stima della Produzione Fotovoltaica e Analisi delle Variabili**

## 📖 Descrizione del Progetto
**SolarPredict** è un Proof of Concept (PoC) sviluppato per simulare e ottimizzare la pipeline industriale di un impianto fotovoltaico. Il sistema acquisisce dati grezzi di telemetria dai pannelli solari e dati meteorologici, li consolida attraverso tecniche di Feature Engineering e utilizza algoritmi di Intelligenza Artificiale per stimare i futuri volumi produttivi (Potenza DC). 

Il progetto affronta una sfida ingegneristica reale: prevedere la generazione di energia basandosi esclusivamente su stime meteorologiche (Irraggiamento e Temperatura Ambiente) e variabili temporali, dimostrando robustezza predittiva anche in presenza di fisiologiche incertezze nei dati meteo forniti.

## 🛠️ Stack Tecnologico
* **Linguaggio:** Python 3.x
* **Ambiente:** Jupyter Notebook
* **Data Ingestion & Manipolazione:** `pandas`, `numpy`
* **Machine Learning:** `scikit-learn` (Random Forest, K-Fold Cross Validation)
* **Data Visualization:** `matplotlib`, `seaborn`

## 📊 Dataset
Il progetto utilizza dati industriali reali estratti dal dataset pubblico Kaggle **"Solar Power Generation Data"** (Plant 1).
Per replicare l'ambiente, è necessario scaricare i seguenti file e posizionarli nella root del progetto:
* `Plant_1_Generation_Data.csv` (Dati di produzione degli inverter)
* `Plant_1_Weather_Sensor_Data.csv` (Rilevazioni meteorologiche della stazione)

## ⚙️ Architettura e Workflow
Il sistema è strutturato in una pipeline sequenziale a 6 livelli, facilmente leggibile e scalabile:

1. **Setup & Importazione:** Inizializzazione dell'ambiente e delle dipendenze.
2. **Data Ingestion:** Lettura dei dati storici in CSV con gestione delle eccezioni e conversione automatica del parsing temporale.
3. **Data Preparation & Feature Engineering:** Aggregazione della produzione totale dell'impianto, merge dei dataset basato sull'orario, campionamento orario per la semplificazione computazionale ed estrazione delle feature temporali (Ora e Mese).
4. **Validazione e Addestramento:** 
   * Prevenzione del *Data Leakage*: rimozione della temperatura del modulo per simulare scenari di previsione meteo reali.
   * Introduzione di rumore statistico sui dati per verificare la resilienza dell'algoritmo.
   * Certificazione della stabilità del modello tramite **K-Fold Cross Validation** (5 split).
   * Addestramento del modello **Random Forest Regressor**.
5. **Estrazione Logica & Dashboard (Feature Importance):** Interrogazione delle metriche interne dell'algoritmo per valutare il peso percentuale di ciascuna variabile (Irraggiamento, Ora, Temperatura) e rendering grafico del confronto Reale vs. Stimato.
6. **Simulatore Predittivo Interattivo:** Un'interfaccia a riga di comando che permette all'utente di inserire scenari meteo personalizzati e ottenere una "KPI Card" grafica con la produzione fotovoltaica attesa.

## 🚀 Come avviare il progetto

1. Clonare la repository:
   ```bash
   git clone [https://github.com/tuo-username/SolarPredict.git](https://github.com/tuo-username/SolarPredict.git)
   cd SolarPredict
