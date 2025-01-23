# Dokumentacja Techniczna

## 1. **Silnik Gry**

- **Silnik:** Unity
- **Wersja:** _do ustalenia_
- **Język programowania:** C#
- **Narzędzia wspomagające:**
  - Blender
  - Photoshop
  - Tilemap (Unity)

---

## 2. **Architektura Projektu**

### 2.1. **Moduły aplikacji** (Unity):

- **Logika gry** (Game Logic)
  - Moduł odpowiedzialny za główne mechaniki gry, takie jak walka, generowanie poziomów i zarządzanie stanem gry.
- **Interfejs użytkownika** (UI)
  - Warstwa prezentacji, zajmująca się wyświetlaniem informacji dla gracza (HUD, menu, powiadomienia).
- **Moduł audio**
  - System obsługujący efekty dźwiękowe, muzykę w tle i dynamiczne reakcje audio na wydarzenia w grze.
- **System zarządzania danymi**
  - Odpowiada za zapis i odczyt danych (np. stan gry, statystyki gracza) z użyciem plików JSON.
- **AI i pathfinding**
  - Moduł zarządzający zachowaniem przeciwników i ich ruchem w przestrzeni gry z wykorzystaniem algorytmów pathfindingu.

### 2.2. **Warstwy aplikacji**:

- **Presentation Layer**:
  - Wszystko, co jest widoczne dla gracza: grafika, interfejs, animacje.
- **Logic Layer**:
  - Kluczowe mechaniki gry, takie jak obliczanie obrażeń, generowanie mapy, zarządzanie AI.
- **Data Layer**:
  - Przechowywanie i odczyt danych z JSON (np. stanu gry, konfiguracji poziomów).

### 2.3. **Struktura katalogów**:

- **Assets**:
  - Sprites: Grafiki postaci, przeciwników, elementów otoczenia.
  - Animations: Pliki animacji.
  - Prefabs: Prefabrykaty obiektów (np. gotowe przeciwniki, pokoje).
  - Scripts: Skrypty dla logiki gry, UI, AI itp.
  - Audio: Dźwięki i muzyka.
  - Scenes: Pliki poziomów gry.
- **Resources**:
  - Pliki JSON do konfiguracji gry.
- **Plugins**:
  - Zewnętrzne biblioteki lub narzędzia używane w projekcie.

### 2.4. **Komunikacja między komponentami**:

- **Event System (Unity Events)**:
  - Wydarzenia, które będą emitowane między komponentami (np. gracz otrzymał obrażenia, przeciwnik został pokonany).
- **Observer Pattern**:
  - Do powiadamiania UI o zmianach w statystykach gracza (np. zmiana HP).
- **Scriptable Objects**:
  - Przechowywanie danych, takich jak statystyki broni, przeciwników czy konfiguracje poziomów.

---

## 3. **Kluczowe Systemy**

- **Sterowanie postacią:**
  - Mechanika ruchu, ataków i umiejętności
  - Obsługa inputów gracza (klawiatura)
- **Zarządzanie kamerą**:
  - Perspektywa z góry
  - Dynamiczne podążanie kamery za graczem LUB Stały widok kamery w aktualnym pomieszczeniu
- **System kolizji i interakcji**:
  - Wykorzystanie mechaniki Rigidbody2D i detekcji kolizji (Collider2D)
  - Detekcja przeciwników i interakcji za pomocą OverlapCircle2D

---

## 4. **AI i ich zachowanie**

- **Pathfinding**:
  - Algorytm A\* lub Unity NavMesh (z modyfikacjami dla 2D)
  - Obsługa przeszkód i dynamiczne śledzenie gracza
- **Mechaniki NPC**:
  - Reakcje na gracza:
    - Ataki melee i ranged
    - Specjalne zachowania, np. przeszkadzanie w poruszaniu, uniki

---

## 5. **Integracje zewnętrzne**

### 5.1. **Firebase**

_jeśli tak to po co_

- **Zastosowania**:
  _do uzupelnienia_

### 5.2. **Obsługa plików JSON**:

Frameworki do serializacji i deserializacji danych JSON:

- **Newtonsoft.Json (Json.NET)**:
  - Rozbudowany framework umożliwiający zaawansowane operacje na plikach JSON, takie jak walidacja, obsługa skomplikowanych struktur danych czy transformacje danych.
  - Sprawdza się w przypadku projektów wymagających dynamicznego przetwarzania dużych zbiorów danych.
- **System.Text.Json**:

  - Lżejsze i szybsze rozwiązanie wbudowane w .NET Core, odpowiednie do prostych operacji na plikach JSON.
  - Może być stosowane w miejscach, gdzie wymagania dotyczące przetwarzania danych są ograniczone.

- **Zastosowania**:
  - **Przechowywanie danych gracza**:
    - Zapisywanie postępu gracza (np. poziom ukończenia, ekwipunek, zdobyte osiągnięcia).
    - Statystyki gracza, takie jak liczba zabitych przeciwników, zdrowie czy zdobyte punkty doświadczenia.
    - Personalizacja konfiguracji gry (np. ustawienia sterowania, preferencje graficzne).
  - **Konfiguracja poziomów**:
    - Rozmieszczenie przeciwników na mapie.
    - Parametry pokojów (np. typ pomieszczenia: boss room, treasure room).
    - Informacje o generowanych przeszkodach, dekoracjach i skarbach.

---

## 6. Optymalizacja:

- **Zarządzanie pamięcią**:

  - Wstępne ładowanie najważniejszych zasobów na początku poziomu
  - Dynamiczne usuwanie obiektów spoza pola widzenia

- **Optymalizacja zasobów**:

  - Kompresja assetów graficznych i dźwiękowych
  - Minimalizacja liczby draw calls

- **Zarządzanie FPS**:

  - Monitoring wydajności przy pomocy Unity Profiler 7.

- **Testy i debugowanie**:
  - Narzędzia do debugowania:
    - Unity Profiler (do analizy CPU, GPU, pamięci)
    - Debug.Log (monitorowanie działania poszczególnych modułów)
  - **Plan testów**:
    - Testy funkcjonalności (sprawdzanie działania AI, walki)
    - Testy wydajności (generowanie map, liczba przeciwników)
    - Testy balansu (poziom trudności, kombinacje przeciwników)
