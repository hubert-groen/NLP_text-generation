# Wstęp do przetwarzania języka naturalnego (2024Z)

## PROJEKT: Generacja tekstu na podstawie zadanego źródła

**Zespół:**

*   Paweł Sarnacki
*   Marek Rospond
*   Hubert Groen



## Cel projektu
Celem niniejszego projektu było zaimplementowanie modelu do generacji tekstu, bazującego na sieciach rekurencyjnych (RNN) z użyciem biblioteki TensorFlow. Projekt pozwala na:

- Przetworzenie i wstępne przekształcenie danych tekstowych.

- Zbudowanie i trenowanie modelu opartego na różnych wariantach warstw rekurencyjnych (GRU, LSTM, RNN).

- Generowanie nowych fragmentów tekstu na podstawie wytrenowanego modelu.

- Ocenę jakości modelu przy użyciu miary cross-entropy i perplexity.

## Etapy implementacji
1. **Przygotowanie danych**:
   - Zdefiniowano źródło tekstu - pliku `.txt`.
   - Utworzeno mapowania znaków na indeksy (char2index) oraz indeksów na znaki (index2char).
   - Przekształcono tekst na ciąg liczb odpowiadających indeksom znaków.

2. **Podział danych na sekwencje**:
   - Ustalono długość sekwencji na 100 znaków.
   - Utworzono dataset TensorFlow z sekwencjami o stałej długości (101 znaków, w tym jeden znak docelowy).
   - Podzielono sekwencje na pary wejście-cel, gdzie:
      - input_text zawiera 100 pierwszych znaków.
      - target_text zawiera kolejne 100 znaków (przesunięcie o 1).

3. **Przygotowanie danych do treningu**:
   - Dataset został przetasowany i podzielony na batch'e o wielkości 512 z buforowaniem 10 000 próbek.
   - Określono parametry modelu:
      - Rozmiar słownika (vocab_size): liczba unikalnych znaków.
      - Wymiar osadzania (embedding_dim): 300.
      - Liczba jednostek w warstwach rekurencyjnych (rnn_units): 1024 dla dwóch warstw.

4. **Implementacja modelu**:
   -   Zdefiniowano funkcję build_model, pozwalającą na budowanie modeli z różnymi typami warstw rekurencyjnych:
         - GRU
         - LSTM
         - RNN

   - Model składa się z:
      - Warstwy osadzania (Embedding).
      - Domyślnie dwóch warstw rekurencyjnych, z możliwością modyfikacji w celach eksperymentalnych.
      - Warstwy gęstej (Dense) przewidującej rozkład prawdopodobieństwa dla kolejnego znaku.

5. **Trenowanie modelu**:
   - Zdefiniowano funkcję straty, używającą sparse_categorical_crossentropy z opcją from_logits=True.
   - Skonfigurowano model z optymalizatorem Adam.
   - Utworzono callback do zapisywania wag modelu po każdej epoce w folderze ./checkpoints_GRU.
   - Przeprowadzono trening modelu przez 20 epok.

6. **Generacja tekstu**:
   - Załadowano wagi wytrenowanego modelu.
   - Zdefiniowano funkcję generate_text, generującą tekst o długości 1000 znaków na podstawie podanego ciągu startowego.
   - Funkcja wykorzystuje rozkład prawdopodobieństwa, aby wprowadzić element losowości do generacji.

7. **Ocena modelu**:
   - Zaimplementowano funkcję calculate_cross_entropy_loss, obliczającą średnią cross-entropię dla testowych sekwencji.
   - Obliczono wartość perplexity, będącą miarą jakości generowanego tekstu (im mniejsza, tym lepsza).
