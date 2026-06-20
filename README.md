# FitTrack — Zintegrowana Platforma Fitness

## Informacje o projekcie
FitTrack to kompleksowa platforma fitness realizowana jako projekt inżynierski. Celem systemu jest redukcja fragmentacji narzędzi cyfrowych wykorzystywanych przez entuzjastów treningu siłowego poprzez połączenie w jednym interfejsie modułów treningowych, dietetycznych oraz systemu współpracy na linii trener–podopieczny. Projekt dąży do zastąpienia przeciętnie trzech odrębnych aplikacji jednym spójnym rozwiązaniem.


## Architektura i Stack Technologiczny
System został zaprojektowany w architekturze zorientowanej na usługi (SOA) z centralną warstwą backendową oraz podejściem Polyglot Persistence, w którym bazy danych są dobierane pod kątem specyficznych wymagań poszczególnych modułów.
- Backend: Java, Spring Boot, Spring Security OAuth2 Client
- Autentykacja: JWT (JSON Web Token) + httpOnly cookie + Google OAuth 2.0
- Konteneryzacja i Infrastruktura: Docker, Docker Compose, VPS
- CI/CD: GitHub Actions
- Komunikacja: REST API (format wymiany danych: JSON)

## Moduły Systemu
# Uwierzytelnianie i Autoryzacja
- Rejestracja oraz logowanie za pomocą adresu e-mail i hasła (z walidacją złożoności).
- Logowanie jednokrotnym kliknięciem przez Google OAuth 2.0 z automatyczną rejestracją nowego konta.
- Zarządzanie sesjami przez JWT i bezpieczne pliki cookie (httpOnly) z automatycznym wylogowaniem po 30 minutach nieaktywności.
- Zarządzanie rolami użytkowników (Użytkownik, Trener) oraz profilami antropometrycznymi.
- Obsługa trwałego usuwania konta zgodnie z art. 17 RODO.

## Moduł Treningu Siłowego
- Katalog ćwiczeń z zaawansowanym filtrowaniem (partia mięśniowa, sprzęt, rodzaj) i opcją definiowania własnych pozycji.
- Rejestracja sesji treningowych (ćwiczenia, serie, obciążenie, powtórzenia, skala RPE 1–10).
- Obsługa zaawansowanych technik kulturystycznych: superserie oraz dropsety.
- Automatyczne wyliczanie tonażu treningowego oraz estymacja jednego powtórzenia maksymalnego (1RM).
- Tworzenie i edycja szablonów treningowych.

## Moduł Diety i Żywienia
- Integracja z bazą Open Food Facts - wyszukiwanie produktów po nazwie oraz kodzie kreskowym.
- Logowanie posiłków w podziale na kategorie oraz śledzenie dziennego spożycia wody.
- Automatyczne obliczanie wskaźników BMR oraz TDEE na podstawie parametrów profilu.
- Monitorowanie dziennego i tygodniowego bilansu kalorycznego oraz makroskładników (białko, tłuszcze, węglowodany) względem celów.

## Moduł Współpracy Trener–Podopieczny
- System zaproszeń i powiązań kont za pomocą unikalnych kodów lub e-maili.
- Wgląd trenera w historyczne dane treningowe, żywieniowe oraz wskaźniki adherencji podopiecznego.
- Możliwość zdalnego przypisywania planów i celów przez trenera (wytyczne trenera posiadają najwyższy priorytet).
- Wbudowany, wewnętrzny komunikator tekstowy oraz system powiadomień systemowych.

## Moduł Gamifikacji
- System punktów doświadczenia (XP) oraz poziomów użytkownika promujący regularną aktywność.
- Odznaki za osiągnięcia (np. pierwsza sesja, rekordy 1RM, ciągłość dietetyczna).
- Wewnętrzne rankingi aktywności dla podopiecznych przypisanych do konkretnego trenera.
