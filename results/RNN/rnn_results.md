### RNN
RNN to rodzaj sieci neuronowych zaprojektowanych specjalnie do pracy z danymi sekwencyjnymi. Ich kluczową cechą jest zdolność do wykorzystywania wewnętrznej pamięci w celu przetwarzania sekwencji, co sprawia, że są skuteczne w zadaniach takich jak modelowanie języka, predykcja szeregów czasowych czy generowanie tekstu.

#### Charakterystyka RNN:
- Przetwarzanie sekwencyjne: RNN przetwarza dane element po elemencie, zachowując "stan ukryty", który przechowuje informacje o wcześniejszych krokach sekwencji.
- Współdzielenie parametrów: W przeciwieństwie do sieci feedforward, RNN używa tych samych parametrów na każdym kroku czasowym, co ułatwia generalizację dla różnych długości sekwencji.
- Wyzwania:
    - Problem zanikającego gradientu: RNN mają trudności z nauką długoterminowych zależności, ponieważ gradienty maleją podczas propagacji wstecznej.
    - Ograniczona zdolność do złożonych reprezentacji: Standardowe RNN nie radzą sobie dobrze z długimi zależnościami w sekwencjach, co prowadzi do ograniczonej wydajności w bardziej złożonych zadaniach.

#### Wnioski:
1. Wyniki uczenia modelu RNN
- Model oparty na architekturze RNN z dwoma warstwami SimpleRNN osiągnął średnią stratę (loss) wynoszącą 1.4786 oraz perplexity równą 2.7868.
- W miarę postępu treningu dokładność modelu znacznie wzrosła, osiągając stabilny poziom po około 150 epokach, co wskazuje na skuteczną konwergencję.
- Funkcja strat (loss) spadła wykładniczo w pierwszych 50 epokach, a następnie stabilizowała się, co oznacza, że model skutecznie nauczył się reprezentacji danych.
2. Analiza jakości generowanego tekstu
- Generowany tekst charakteryzuje się poprawną strukturą składniową, ale ograniczoną spójnością semantyczną. Model często wprowadza losowe słowa, które nie mają logicznego związku z treścią wejściową.
- Wygenerowane frazy są zgodne z danymi treningowymi (pochodzącymi z książki "Władca Pierścieni"), ale wprowadzają powtarzalność i brak długoterminowego związku między zdaniami.
3. Wady zastosowanej architektury
- Ograniczenia RNN: Model nie radzi sobie dobrze z długoterminowymi zależnościami, co jest typowe dla architektury RNN. Złożone struktury narracyjne wymagają mechanizmów lepiej zapamiętujących dłuższe zależności.
- Problem ze spójnością: Generowany tekst często traci kontekst po kilku zdaniach, co wynika z ograniczonej pamięci modelu.
4. Porównanie do GRU/LSTM
- TODO