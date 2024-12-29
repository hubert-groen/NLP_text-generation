# NLP

Dokumentacja wstępna projektu: **Generacja tekstu na podstawie źródła.**

## Cel projektu
Projekt ma na celu stworzenie systemu generacji tekstu na podstawie dostarczonego źródła w formie tekstowej. Planowane jest wykorzystanie różnych architektur sieci neuronowych w celu zbadania ich skuteczności w zadaniu generacji tekstu.

## Obecny stan projektu
Na obecnym etapie stworzono kod umożliwiający:
1. **Ładowanie źródła tekstowego**:
   - Załadowanie pliku `.txt` do pamięci.
   - Przekształcenie znaków na ich reprezentacje numeryczne.

2. **Przetwarzanie danych wejściowych (preprocessing)**:
   - Zdefiniowanie mapowania znaków na indeksy i odwrotnie.
   - Podział danych wejściowych na sekwencje o stałej długości.
   - Przekształcenie sekwencji w pary wejście-cel.
   - Utworzenie zbioru danych w formacie TensorFlow Dataset.

3. **Szkielet architektury modelu**:
   - Implementacja podstawowego modelu opartego na warstwach **GRU** z dodatkowymi warstwami osadzania (embedding), połączoną warstwą wyjściową.
   - Zdefiniowanie funkcji straty oraz konfiguracji procesu trenowania modelu.

4. **Zapisywanie stanu modelu**:
   - Przygotowanie mechanizmu do zapisywania checkpointów modelu w celu późniejszego wczytania wag.

5. **Generacja tekstu**:
   - Implementacja funkcji generującej tekst na podstawie modelu i ciągu początkowego znaków.

## Planowane kroki
W kolejnych etapach projektu przewidziane są:
1. Trening i testowanie modelu na różnych architekturach, takich jak:
   - **LSTM**
   - **RNN**
   - Rozszerzone wersje **GRU** z modyfikacjami parametrów.

2. Porównanie wyników uzyskanych dla każdej architektury, z uwzględnieniem:
   - Jakości generowanego tekstu.
   - Szybkości konwergencji modelu.
   - Złożoności obliczeniowej.

3. Wdrożenie funkcji oceny jakości generacji tekstu na podstawie metryk, takich jak:
   - Entropia krzyżowa dla danych testowych.
   - Subiektywna ocena płynności i sensowności tekstu.
