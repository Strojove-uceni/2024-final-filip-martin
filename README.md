# 🎧 **Rozpoznávání zvuku - tvorba titulků pro neslyšící**  

## 📋 **Popis cíle**  
Naším cílem je vytvořit nástroj, který analyzuje zvukovou stopu, klasifikuje zvuky a generuje titulky pro neslyšící. 
Jako zdroj dat využíváme veřejný dataset [YouTube AudioSet](https://research.google.com/audioset/unbalanced_train/vehicle.html).  

---

## 🛠️ **Implementace**  

### Získání dat  
Data jsou získána pomocí skriptu `data_collection_final.ipynb` ve složce **data_preparation**.  

### Předzpracování dat  
Pro předzpracování dat je použit skript `data_preprocessing.ipynb`, který provádí následující kroky:  
- **Resamplování** všech zvukových souborů na jednotný *sample_rate*.  
- **Trimování** zvukových záznamů na délku **8 sekund**.  
- **Normalizace** do intervalu **[0, 1]**.  
- **Výpočet Mel spectrogramů** pro reprezentaci zvuku.  
- **Uložení dat** do jednotného **HDF5 souboru** pro efektivní načítání.  

### Trénování modelu  
- Hlavní model je popsán v notebooku `Noise_recognition.ipynb` ve složce **noise_recognition**.  
- Použitý model: **Konvoluční neuronová síť (CNN)** s **dense klasifikační vrstvou**.  

---

## 📈 **Výsledky**  
- ✅ Model dosahuje přesnosti **80 %** při klasifikaci zvukových záznamů.  
- ⚠️ **Hlavní problémy**:  
  - Malá velikost datasetu (~3000 vzorků).  
  - Nekonzistentní kvalita dat a špatné labely.  

---

## 🚀 **Možnosti zlepšení**  
1. **Rozšíření datasetu** o více vzorků.  
2. **Čištění dat** k odstranění chybných labelů a šumových nahrávek.  
3. **Transfer Learning**: Využití předtrénovaných modelů pro rychlejší a přesnější výsledky.  
4. **Augmentace dat**: Přidání variací (např. šum, změny hlasitosti, časové posuny) pro lepší generalizaci modelu.  

---

## 📁 **Struktura projektu**  

```plaintext
root/
│-- data/                     
│   ├── evaluation/           
│   │   └── 4KcakwwF0Bc.flac                # Zvukový soubor použitelný pro evaluaci a zobrazení výsledků
│   ├── weights/                            # Váhy natrénovaných modelů
│   │   └── cnn_2s_128x128_best   
│   └── dataset_metadata/                   # Metadata datasetu - slouží pro stahování dat z youtube
│       └── vehicle_audiset_full.parquet    # Stažená metadata pro kompletní vehicle dataset
│-- data_preparation/                       # Skripty pro sběr a předzpracování dat
│   ├── data_collection_final.ipynb         # Skript pro získávání dat
│   └── data_preprocessing.ipynb            # Skript pro předzpracování dat
│-- noise_recognition/                      # Notebooky a modely pro trénování
│   ├── Noise_recognition.ipynb             # Hlavní notebook pro trénování modelu
│-- visualization/                          # Notebooky pro vizualizaci výsledků
│   └── result_visualization.ipynb          # Skript pro vizualizaci výsledků

```

---
