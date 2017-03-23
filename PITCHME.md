#HSLIDE

## Przewidywanie ataków padaczki
Konkurs na Kaggle: [https://www.kaggle.com/c/melbourne-university-seizure-prediction](https://www.kaggle.com/c/melbourne-university-seizure-prediction)

#HSLIDE

* ~6000 obserwacji w zbiorze treningowym.
* Każda obserwacja to 16-kanałowy 10-minutowy sygnał EEG.
* Każdy kanał to 240k wartości.
* 3 pacjentów
* Obserwacje podzielone na dwie grupy: przedatakowe i nie-przedatakowe.

#HSLIDE

## EEG

<img src="eeg.png" height="500">

#HSLIDE

## Widmo sygnału
* Szereg <img src="fourier.gif">
* Szybka transformata Fouriera
* Moduł ze współczynników -> widmo
* Liczenie FFT dla każdego otoczenia punktu -> spektrogram

#HSLIDE

### Spektrogram 1/3
<img src="patient1_1_0.png" height="240">

<img src="patient1_1_1.png" height="240">

#HSLIDE

### Spektrogram 2/3
<img src="patient1_2_0.png" height="240">

<img src="patient1_2_1.png" height="240">

#HSLIDE

## Spektrogram 3/3

Niestety, nie możemy wykorzystać całego potencjału spektrogramu, gdyż:

* Widmo, to wektor o rozmwiarze 120k
* Więc spektrogram to macierz 240k * 120k ~ 26GB

#HSLIDE

## Features

* Statystyki sygnału: min, max, średnia, wariancja, wsp. skośności, kurtoza 
* Macierz korelacji sygnałów i jej wektory własne
* Macierz korelacji widma (współczynników FFT) i jej wektory własne
* Power-in-Band Spectral Entropy
* Higuchi fractal dimension
* Petrosian fractal dimension
* Odsetek zer (błędów) w danych

#HSLIDE

## Wsp. skośności (ang. skewness)
<img src="skewness.gif">

![skewness2](skewness2.png)

#HSLIDE

## Kurtoza

![kurtosis](kurtosis.png)

#HSLIDE

## Power-in-Band Spectral Entropy

Niech <img src=entropy1.png> będzie widmem sygnału.

![entropy2](entropy2.png)

![entropy3](entropy3.png)

![entropy4](entropy4.png)

#HSLIDE

## Higuchi fractal dimension

![higuchi](higuchi.png)

![higuchi2](higuchi2.png)

Wymiarem Higuchi'ego jest nachylenie prostej (tangens), która najlepiej przybliża (ze względu na błąd średnio kwadratowy) kolejne wartości funkcji: 

![higuchi3](higuchi3.png)

#HSLIDE

## Petrosian fractal dimension

![hfd](hfd.png)

Gdzie n długość wektora, dla którego jest liczony wymiar.

A ![hfd2](hfd2.png) to liczba zmian znaku pochodnej.

#HSLIDE

## Klasyfikatory

* SVM
* Logistic Regression
* XGBoost

#HSLIDE

## Logistic Regression

![lr](lr_cost.png)
![lr2](lr_grad.png)

#HSLIDE

## Support Vector Machine

![svm](svm.png)
![svm2](svn2.png)

#HSLIDE

## XGBoost

#HSLIDE

## Główne problemy nr 1

Cross-validacja - dane testowe zostały wygenerowane kilkanaście miesięcy po danych treningowych, więc istotnie różniły się, dlatego żadne metody cross-validacji nie były miarodajne.

Brak dobrej cross-validacji narażał nas na overfitting. Jednym z wyjść z tej sytuacji był ensambling.

#HSLIDE

## Główne problemy nr 2

Dziury w danych. Metody radzenia sobie:
* wypełnianie ich szumem Gaussowskim
* wypełnianie ich funkcją liniową
* model auto-regresji
* model ARMA (auto-regression moving average)

#HSLIDE

## Auto-regresja 

![ar](ar.png)

#HSLIDE

## Moving average

![ma](ma.png)

#HSLIDE

## ARMA

![arma](arma.png)

#HSLIDE

#Dziękuję za uwagę :)
