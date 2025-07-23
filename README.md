# WiFi Connect App (Flutter)

A Flutter-based app that allows users to scan and connect to nearby WiFi networks.

---

## 🔧 IDE, Packages & Plugins

- **IDE**: Visual Studio Code
- **Flutter SDK**: >=3.13.0
- **Key Packages**:
  - [`wifi_iot`](https://pub.dev/packages/wifi_iot): For scanning and connecting to WiFi.
  - [`permission_handler`](https://pub.dev/packages/permission_handler): To request runtime permissions.
  - [`fluttertoast`](https://pub.dev/packages/fluttertoast): For showing connection feedback.

---

## 📱 Platform Limitations

### Android:
- Tested on Android 10+.
- Requires `ACCESS_FINE_LOCATION` or `NEARBY_WIFI_DEVICES` permissions.
- Must enable **location services** to scan WiFi.

### iOS:
- WiFi scanning is **not supported** due to platform restrictions.
- You can still manually enter SSID and connect using `WiFiForIoTPlugin.connect(...)` but with limited success.
- Add required capabilities in `Info.plist` (e.g., location usage description).

---

## 🔐 Permissions Handling

Used the `permission_handler` package to request and check:
- **Location permission**
- **Nearby WiFi permission (Android 13+)**
- Prompted user if services like location were disabled.

Handled permission fallback gracefully to prevent crashes and notify user.

⭐ Bonus Features
UI feedback for connection success/failure using FlutterToast.

Password input dialog with validation.

Auto-connect to known networks if found.

Modular and clean architecture (UI, service, utils separated).

Clear comments and easy to extend.

🚀 How to Run
Clone the repo.

Run on Android device with location/WiFi enabled.

Tap Scan & Connect to WiFi.

Select a network and enter password.

---

## 🗃️ WiFi Database Logic

- Supported two modes:
  - **Generic Scan & Connect** (connect to any WiFi, user enters password)
  - **Known Networks Matching** (optional): Uses a JSON list with predefined SSID-password pairs.
- JSON format:

```json
[
  {
    "ssid": "MyWiFi",
    "password": "mypassword123"
  }
]
