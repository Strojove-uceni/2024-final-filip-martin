# Rozpoznávání zvuku pro neslyšící:
##  Popis cíle:

Naším cílem je na základě veřejných dat z youtube vytvořit síť, která je schopná analyzovat zvukovou stopu a klasifikovat
její obsah.
Zdrojem dat je: 'https://research.google.com/audioset/unbalanced_train/vehicle.html'

## Provedení
### Získání dat
Pro získávání dat slouží script data_collection_final ve složce data_preparation

### Předpříprava dat
Pro získávání dat slouží script data_preprocessing ve složce data_preparation
Jednotlivé zvukové soubory jsou:
- Resamplovány na identický sample_rate  
- Trimovány na 8s
- Normalizovány na [0, 1]

Následně z nich je:
- Vypočítán melův histogram
- Všechna data jsou převedena do jednoho h5 souboru

### Učení
Je popsáno v Noise_recognition.ipynb ve složce noise_recognition

Nad daty je vytvořena několika konvoluční síť s dense klasifikační vrstvou
Bylo vyzkoušeno více typů dat a sítí, postup s nejlepšími výsledky je popsán ve výše uvedeném souboru

## Výsledky
Síť je schopná se učit a klasifikovat s cca 70% přesností
Problémy jsou:
- Relativně malý dataset cca 3000 samplů
- Špatná čistota dat

### Možnosti zlepšení
K vylepšení výsledků by mohlo pomoci
- Získat větší dataset
- Očistit stávající dataset o špatné labely
- Využít transfer_learningu a některé z již existujících sítí

--- 
[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/rMTkWhxv)

*Reminder*
*   *Do not miss [deadline](https://su2.utia.cas.cz/labs.html#projects) for uploading your implementation and documentation of your final project.*
*   *Include working demo in Colab, in which you clearly demonstrate your results. Please refer to the Implementation section on the [labs website](https://su2.utia.cas.cz/labs.html#projects).*
*   *Do not upload huge datasets to GitHub repository.*
