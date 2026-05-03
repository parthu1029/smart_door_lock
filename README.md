# Smart Door Lock System 🔐

An IoT-based smart door lock system that integrates **fingerprint authentication, OTP verification, and email confirmation** to securely unlock doors. The system combines **ESP32 hardware, a Flask backend, and a React dashboard** to create a multi-layer secure door access system.

---

## Features

- User registration and login
- Fingerprint enrollment and authentication
- OTP generation and verification
- Email confirmation before unlocking the door
- ESP32 hardware integration
- React dashboard for system management
- SQLite database for storing users and fingerprints
- REST API communication between hardware and backend

---

## System Architecture

Fingerprint Sensor  
↓  
ESP32 Controller  
↓  
Flask Backend API  
↓  
OTP Verification  
↓  
Email Confirmation  
↓  
Door Unlock via Relay  

---

## Authentication Flow

1. User registers through the web dashboard.
2. User logs in to manage fingerprints.
3. Fingerprint is scanned using the sensor.
4. ESP32 sends fingerprint ID to Flask backend.
5. Backend verifies fingerprint and generates OTP.
6. User enters OTP using keypad.
7. Backend verifies OTP.
8. Email confirmation link is sent to registered email.
9. User clicks the link.
10. Flask sends unlock command to ESP32.
11. Relay activates and door unlocks.

---

## Project Structure

smart_door_lock  
│  
├── backend  
│   ├── app.py  
│   ├── database.py  
│   ├── config.py  
│   ├── email_service.py  
│   ├── fingerprint_service.py  
│   ├── otp_service.py  
│   ├── hardware_service.py  
│   └── smartlock.db  
│  
├── frontend  
│   ├── public  
│   ├── src  
│   │   ├── pages  
│   │   │   ├── Register.js  
│   │   │   ├── Login.js  
│   │   │   └── Dashboard.js  
│   │   │  
│   │   ├── App.js  
│   │   ├── api.js  
│   │   └── index.js  
│   │  
│   └── package.json  
│  
├── hardware  
│   └── esp32_main.ino  
│  
└── README.md  

---

## Technologies Used

### Frontend
- React.js
- Axios
- React Router

### Backend
- Flask
- Flask-CORS
- Flask-Mail
- SQLite

### Hardware
- ESP32
- Fingerprint Sensor
- 4×4 Keypad
- Relay Module

---

## Installation

### Clone the repository

git clone https://github.com/yourusername/smart_door_lock.git  
cd smart_door_lock  

---

### Backend Setup

cd backend  
pip install -r requirements.txt  
python app.py  

Backend server runs at:

http://127.0.0.1:5000

---

### Frontend Setup

cd frontend  
npm install  
npm start  

Frontend runs at:

http://localhost:3000

---

## Hardware Setup

Upload the ESP32 firmware using **Arduino IDE**.

Required libraries:

WiFi.h  
HTTPClient.h  
Keypad.h  
Adafruit Fingerprint Sensor Library  

Hardware responsibilities:

- Detect fingerprint
- Send fingerprint ID to Flask server
- Receive OTP verification response
- Activate relay to unlock door

---

## API Endpoints

| Endpoint | Method | Description |
|--------|--------|--------|
| /register | POST | Register new user |
| /login | POST | User login |
| /add-fingerprint | POST | Add fingerprint |
| /remove-fingerprint | POST | Remove fingerprint |
| /fingerprint-detected | POST | Verify fingerprint |
| /verify-otp | POST | Verify OTP |
| /unlock/<token> | GET | Unlock door |

---

## Database Tables

### Users

id  
name  
email  
password  

---

### Fingerprints

id  
user_id  
fingerprint_id  

---

### OTPs

id  
user_id  
otp  

---

### Unlock Tokens

id  
user_id  
token  

---

## Security Layers

This project implements **multi-factor authentication**:

Fingerprint Authentication  
+  
OTP Verification  
+  
Email Confirmation  

This provides stronger security compared to traditional locks.

---

## Future Improvements

- Face recognition integration
- Mobile app control
- Access logs dashboard
- Camera capture during fingerprint detection
- Cloud deployment
- Push notifications

---

## Contributors

S Siddardha  
Project Collaborator
G Pardhasaradhi
Project Collaborator
B Sujith
Project Collaborator

---

## License

This project is open-source and available under the MIT License.
