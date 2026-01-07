# 🚀 OPLEX - Szybki Start

## ⚡ Pierwsze Uruchomienie

### KROK 1: Otwórz `index.html`
```
oplex/index.html
```

### KROK 2: Automatyczna Inicjalizacja
Przy pierwszym otwarciu system automatycznie utworzy:
- ✅ Konto super-admin: **admin / sierra10**

### KROK 3: Zaloguj się
```
Login:  admin
Hasło:  sierra10
```

✅ **GOTOWE!** Masz pełny dostęp jako Super-Admin!

---

## 🔐 System Logowania - NOWE ZASADY

### ❌ CO NIE DZIAŁA:
```
Login: "wojtek" → ❌ BŁĄD (użytkownik nie istnieje)
Login: "jan123" → ❌ BŁĄD (użytkownik nie istnieje)
Login: dowolny  → ❌ BŁĄD (tylko zdefiniowani pracownicy)
```

### ✅ CO DZIAŁA:
```
Login: "admin"  → ✅ Prompt hasła → Zalogowany jako Super-Admin
```

---

## 👥 Dodawanie Pracowników

### Zaloguj się jako admin:
1. Login: `admin` → Hasło: `sierra10`
2. Kliknij kafelek **🔐 Zarządzanie**
3. Zakładka **👥 Profile Pracowników**
4. Przycisk **➕ Dodaj Pracownika**

### Przykładowy Pracownik:
```
Imię i Nazwisko: Jan Kowalski
Login (username): jan.kowalski
Hasło: (opcjonalne) jankow123
Rola: 👤 Pracownik lub 🔑 Zarządca
Stanowisko: Sprzedawca
Procent z obrotu: 1%
✅ Aktywny
```

### Po dodaniu:
Pracownik może się zalogować:
```
Login: jan.kowalski
Hasło: jankow123 (jeśli ustawione)
```

---

## 🎭 Poziomy Dostępu

### POZIOM 0: Pracownik (employee)
```
Login: jan.kowalski
Hasło: (jeśli ustawione)

Dostęp:
✅ Obrót
✅ Zwroty
✅ Reklamacje
✅ Urlopy
✅ Kalkulacje
❌ Zarządzanie (zablokowane)
```

### POZIOM 1: Zarządca (manager)
```
Login: anna.nowak
Hasło: (jeśli ustawione)

Dostęp podstawowy:
✅ Obrót, Zwroty, Reklamacje, Urlopy, Kalkulacje

Dostęp admin (po kliknięciu Zarządzanie):
1. Kliknij kafelek 🔐 Zarządzanie
2. Prompt hasła pracownika (weryfikacja)
3. Prompt hasła super-admin (sierra10)
4. ✅ Token admin 60 min
5. Dostęp: Profile, Wypłaty, Koszty, Audyt, Ustawienia
```

### POZIOM 2: Super-Admin
```
Login: admin
Hasło: sierra10

Auto-login jako admin:
✅ Token aktywny od razu
✅ Wszystkie kafelki odblokowane
✅ Pełny dostęp permanentny
```

---

## 🧪 Testowanie Systemu

### TEST 1: Zły login
```
1. Wpisz: "nieistniejacy"
2. Kliknij Zaloguj
3. ✅ Powinna pojawić się wiadomość: "Nieprawidłowy login!"
```

### TEST 2: Admin login
```
1. Wpisz: "admin"
2. Kliknij Zaloguj
3. Prompt hasła: "sierra10"
4. ✅ Zalogowany jako "Super Administrator"
5. ✅ Badge w topbar: "🔐 Admin • 60:00"
6. ✅ Wszystkie kafelki odblokowane
```

### TEST 3: Dodaj pracownika
```
1. Zaloguj jako admin
2. Kliknij 🔐 Zarządzanie
3. Zakładka 👥 Profile Pracowników
4. ➕ Dodaj Pracownika
5. Wypełnij dane testowe
6. 💾 Zapisz
7. ✅ Pracownik dodany
```

### TEST 4: Zaloguj jako pracownik
```
1. Wyloguj (przycisk w topbar)
2. Wpisz login nowego pracownika
3. Jeśli ma hasło → prompt
4. ✅ Zalogowany jako pracownik
5. ✅ Kafelek Zarządzanie zablokowany (dla zwykłego pracownika)
```

### TEST 5: Zarządca - dostęp admin
```
1. Dodaj pracownika z rangą "🔑 Zarządca"
2. Zaloguj jako ten pracownik
3. Kliknij 🔐 Zarządzanie
4. Prompt hasła pracownika → weryfikacja
5. Prompt hasła super-admin → sierra10
6. ✅ Token admin aktywny
7. ✅ Dostęp do panelu zarządzania
```

---

## ⚠️ Ważne Informacje

### Konto Awaryjne
```
Login: admin
Hasło: sierra10

- Nie może być usunięte
- Ukryte w liście pracowników
- Nie uczestniczy w wypłatach
- Permanentny dostęp admin
```

### Bezpieczeństwo
```
✅ Hasła przechowywane jako Base64
✅ Token sesji 60 minut (przedłużalny)
✅ Auto-logout po wygaśnięciu
✅ Weryfikacja przy każdej akcji admin
✅ Tylko zdefiniowani pracownicy mogą się logować
```

### localStorage Keys
```
oplex_user              # Aktualnie zalogowany
oplex_employees         # Baza pracowników
oplex_admin_session     # Token sesji admin
oplex_admin_password    # Hasło super-admin (Base64)
```

---

## 🆘 Rozwiązywanie Problemów

### Problem: "System pracowników niedostępny"
**Rozwiązanie:**
```javascript
// W konsoli przeglądarki (F12):
localStorage.clear();
location.reload();
// System utworzy konto admin automatycznie
```

### Problem: Zapomniałem hasła super-admin
**Rozwiązanie:**
```javascript
// W konsoli przeglądarki (F12):
localStorage.setItem('oplex_admin_password', btoa('sierra10'));
// Przywrócono domyślne hasło: sierra10
```

### Problem: Chcę zresetować cały system
**Rozwiązanie:**
```javascript
// W konsoli przeglądarki (F12):
localStorage.clear();
location.reload();
// System zresetowany do ustawień fabrycznych
```

---

## 📊 Status Modułów

### ✅ Gotowe do użycia:
```
✅ System logowania (profile pracowników)
✅ Autoryzacja 3-poziomowa (employee/manager/super-admin)
✅ Dashboard z kafelkami
✅ Panel Super-Admin (Profile Pracowników)
✅ Token sesji admin (60 min)
```

### 🚧 W przygotowaniu:
```
🚧 Wypłaty (struktura gotowa)
🚧 Koszty (struktura gotowa)
🚧 Urlopy (struktura gotowa)
🚧 Kalkulacje (struktura gotowa)
🚧 Audyt (logi gotowe)
```

### ✅ Działające moduły:
```
✅ Obrót v3.0.7 (pełna funkcjonalność)
✅ Zwroty (pełna funkcjonalność)
✅ Reklamacje (pełna funkcjonalność)
```

---

## 🎯 Pierwsze Kroki Po Zalogowaniu

1. **Dodaj pracowników** (Panel Zarządzanie → Profile)
2. **Ustaw limity urlopowe** (w przyszłości)
3. **Konfiguruj koszty** (w przyszłości)
4. **Sprawdź logi** (Panel Zarządzanie → Audyt)
5. **Zmień hasło super-admin** (Panel Zarządzanie → Timer sesji → 🔑 Zmień hasło)

---

**Powodzenia! 🚀**
