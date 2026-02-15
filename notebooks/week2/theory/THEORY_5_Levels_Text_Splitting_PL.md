# 📚 Teoria: 5 Poziomów Dzielenia Tekstu

> *„Twoim celem nie jest dzielenie tekstu dla samego dzielenia. Twoim celem jest przygotowanie danych w formacie, który pozwoli na ich wartościowe odzyskanie (RETRIEVAL) później.”*

---

## 🎯 Czym jest Text Splitting?

**Text splitting** (chunking) to dzielenie danych na mniejsze fragmenty — proces niezbędny przed etapem retrieval w systemach RAG.

### Kluczowe pytanie

> **Jak optymalnie przekazać modelowi językowemu dokładnie te dane, których potrzebuje do wykonania zadania?**

---

## 🔍 Czym jest Retrieval?

**Retrieval** to proces gromadzenia odpowiednich informacji dla modelu językowego. To orkiestracja narzędzi i technik, które mają na celu „wywołanie” dokładnie tego, czego model potrzebuje.

### Dlaczego nie przekazujemy „wszystkiego”? (metoda „kitchen sink")

1. **Limity kontekstu** — modele mają górną granicę ilości danych
2. **Stosunek sygnału do szumu** — zbyt duża ilość nieistotnych informacji w kontekście niszczy wydajność. Modele działają lepiej, gdy usunie się z danych zbędny szum

---

## 📊 Dwa podejścia do strategii

| Podejście | Analogia | Skupienie |
|-----------|----------|-----------|
| **Naïwne** | Sortowanie książek na podstawie rozmiaru i miejsca na półce | Fizyczna struktura tekstu (liczba znaków, akapity, składnia kodu) |
| **Semantyczne i agentowe** | Kategoryzowanie książek według gatunków i tematów | Znaczenie (co i dlaczego jest napisane) oraz kontekst |

---

## 🪜 5 Poziomów Dzielenia Tekstu

### Level 1: Dzielenie znakowe (Character Splitting)

- **Opis:** Najprostsza, sztywna metoda — dzielenie co stałą liczbę znaków
- **Wady:** Często przecina słowa lub zdania w połowie — mało użyteczne w produkcji
- **Zastosowanie:** Szybkie prototypowanie, testy

---

### Level 2: Rekurencyjne dzielenie znakowe (Recursive Character Splitting)

- **Opis:** Bierze pod uwagę strukturę tekstu (akapity, nowe linie, znaki interpunkcyjne)
- **Zasada:** Dzieli tekst logicznie, starając się trzymać powiązane fragmenty razem
- **Zalecenie:** ⭐ **Zalecany punkt startowy** dla większości projektów

---

### Level 3: Dzielenie specyficzne dla dokumentu (Document Specific)

- **Opis:** Dostosowanie strategii do formatu pliku
- **Formaty:** Markdown, kod Python/JS, PDF-y z tabelami i obrazami
- **Cel:** Wykorzystanie naturalnych separatorów (nagłówki, definicje klas, sekcje) do grupowania informacji

---

### Level 4: Dzielenie semantyczne (Semantic Splitting)

- **Opis:** Wykorzystuje embeddingi (wektorowe reprezentacje tekstu)
- **Działanie:** Algorytm bada znaczenie zdań. Gdy odległość (różnica znaczeniowa) między zdaniami jest duża → następuje podział (*break point*)
- **Efekt:** Grupowanie tematycznie podobnych treści

---

### Level 5: Dzielenie agentyczne (Agentic Splitting)

- **Opis:** Eksperymentalna metoda — system działający jak agent
- **Proces:** Analizuje tekst zdanie po zdaniu i decyduje: *Czy to zdanie pasuje do obecnego kawałka, czy powinno zacząć nowy?*
- **Charakterystyka:** Powolny i kosztowny, ale **najbardziej zbliżony** do tego, jak tekst podzieliłby człowiek

---

## 🚀 Bonus: Zaawansowane taktyki Retrieval

Strategie wychodzące poza samo cięcie tekstu:

1. **Rozdzielenie indeksowania od generowania**  
   Wyszukujesz na podstawie podsumowania tekstu lub hipotetycznych pytań, ale modelowi przekazujesz pełny, surowy dokument.

2. **Parent Document Retrieval**  
   Wyszukujesz mały, precyzyjny fragment (lepsze dopasowanie), ale modelowi zwracasz ten fragment wraz z **szerszym kontekstem**.

---

## 📋 Podsumowanie

| Level | Nazwa | Złożoność | Rekomendacja |
|:-----:|-------|-----------|--------------|
| 1 | Character | Niska | Prototypy |
| 2 | Recursive Character | Średnia | **Start dla większości** |
| 3 | Document Specific | Średnia–wysoka | Dokumenty specjalistyczne |
| 4 | Semantic | Wysoka | Optymalizacja jakości |
| 5 | Agentic | Bardzo wysoka | Eksperymenty |
