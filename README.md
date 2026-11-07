# BI Sys Android

Natywna aplikacja Android dla systemu **BI Sys** działającego pod adresem `https://cloud.przemysl.eu`.

## Bieżąca wersja

- `versionName`: **1.0.6**
- `versionCode`: **7**
- `applicationId`: `pl.przemysl.bisys`
- `minSdk`: 26
- `targetSdk`: 35
- backend mobilny: BI Sys **1.5.5.2** lub nowszy

Od wersji **1.0.6** repozytorium `rafikpor-prog/BI-SYS` jest głównym źródłem kodu aplikacji. Kolejne aktualizacje powinny być przygotowywane na podstawie aktualnej gałęzi `main` tego repozytorium.

## Zakres aplikacji

- logowanie do systemu i 30-dniowa sesja API,
- MFA,
- rejestracja wejścia do serwerowni,
- ewidencja wejść: lista, podgląd i edycja,
- rejestracja incydentu,
- rejestr incydentów: lista, podgląd i edycja,
- natywne formularze generowane z aktualnego schematu serwera,
- polskie biznesowe etykiety pól w formularzach i podglądach,
- kolejka offline i automatyczna synchronizacja po odzyskaniu sieci,
- szyfrowanie lokalnych danych kolejki i schematów przy użyciu Android Keystore,
- konto zalogowanego użytkownika,
- funkcje administratora: zarządzanie użytkownikami i aktualizacja systemu,
- natywne komunikaty powodzenia i błędów operacji,
- centrum powiadomień z dzwonkiem, licznikiem i historią 20 ostatnich powiadomień,
- ekran „O aplikacji” z rozwijanymi opisami funkcji,
- historia aktualizacji aplikacji.

Aplikacja nie używa WebView jako interfejsu użytkownika i nie przenosi generatorów eksportu, rozbudowanych filtrów ani pozostałych modułów systemu.

## Backend

Aplikacja korzysta z natywnego API `/api/mobile/v1` udostępnianego przez BI Sys. Aktualnie przyjętą bazą backendu jest **1.5.5.2** lub wersja nowsza zachowująca zgodność tego API.

## Podpis produkcyjny

Od wersji **1.0.6** wszystkie produkcyjne APK muszą być podpisywane tym samym kluczem `BI-Sys-release.jks`.

**Prywatny klucz i hasła nie są przechowywane w GitHubie.** Repozytorium zawiera wyłącznie `signing.properties.example` oraz odcisk publicznego certyfikatu w `SIGNATURE-FINGERPRINT.txt`.

Nie wolno generować nowego keystore dla kolejnych wydań. Szczegóły znajdują się w `BUILD-RELEASE.md`.

## Historia najważniejszych zmian

### 1.0.6
- ustanowiono stałą linię podpisu produkcyjnego dla wszystkich kolejnych aktualizacji,
- zachowano centrum powiadomień i licznik nieprzeczytanych,
- zachowano zielone potwierdzenia i czerwone alerty operacji,
- rozbudowano historię aktualizacji i automatyczne prezentowanie wersji.

### 1.0.5
- dodano zielone komunikaty powodzenia i czerwone alerty błędów,
- dodano centrum ostatnich 20 powiadomień pod ikoną dzwonka,
- rozbudowano ekran „O aplikacji”,
- dodano historię aktualizacji.

### 1.0.4
- zastąpiono techniczne nazwy pól czytelnymi polskimi etykietami,
- połączono etykiety podglądu z dynamicznym schematem formularzy.

## Zasada dalszego rozwoju

Każda kolejna wersja powinna:

1. zaczynać się od aktualnej gałęzi `main`,
2. zwiększać `versionCode`,
3. aktualizować `versionName` i `ReleaseNotes.java`,
4. przejść kompilację i test podpisu,
5. być podpisana stałym kluczem produkcyjnym linii 1.0.6+,
6. nie zawierać w repozytorium plików `.jks`, `.keystore`, `signing.properties` ani prywatnych paczek wydawniczych.
