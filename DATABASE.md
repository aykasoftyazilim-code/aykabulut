# AYKASOFT Veritabanı Kurulum Rehberi

## 🔥 Firebase Kurulum (Önerilen)

### 1. Firebase Projesi Oluştur
1. https://console.firebase.google.com adresine git
2. "Proje ekle" tıkla
3. Proje adı: `aykasoft`
4. Google Analytics: Devre dışı bırak (opsiyonel)
5. Projeyi oluştur

### 2. Authentication Aktif Et
1. Firebase console > Authentication > Oturum açma yöntemi
2. "E-posta/Şifre" etkinleştir

### 3. Real-time Database Oluştur
1. Firebase console > Real-time Database
2. "Veritabanı oluştur"
3. Konum: `europe-west1` (Avrupa)
4. Kurallar:

```json
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
```

### 4. Web App Ekleyin
1. Project settings > Genel > Web apps
2. "</>" tıkla
3. App nickname: `aykasoft-web`
4. Register app

### 5. Config'i Güncelle
Aşağıdaki bilgileri alın ve `login.html` dosyasındaki firebaseConfig kısmını güncelleyin:

```javascript
const firebaseConfig = {
  apiKey: "SİZİN_API_KEY",
  authDomain: "aykasoft.firebaseapp.com",
  databaseURL: "https://aykasoft-default-rtdb.firebaseio.com",
  projectId: "aykasoft",
  storageBucket: "aykasoft.appspot.com",
  messagingSenderId: "123456789",
  appId: "SİZİN_APP_ID"
};
```

---

## ⚡ Firebase Kurulum (Terminal)

```bash
# Firebase CLI kurulum
npm install -g firebase-tools

# Giriş yap
firebase login

# Projeyi başlat
firebase init

# Hosting seç, build yok, single page: no
```

---

## 📊 Veritabanı Yapısı

```
aykasoft/
├── users/
│   └── {userId}/
│       ├── email
│       ├── name
│       ├── company
│       └── createdAt
├── products/
│   └── {productId}/
│       ├── barcode
│       ├── name
│       ├── price
│       ├── stock
│       └── category
├── customers/
│   └── {customerId}/
│       ├── name
│       ├── phone
│       ├── address
│       ├── debt
│       └── credit
├── transactions/
│   └── {transactionId}/
│       ├── type
│       ├── amount
│       ├── description
│       ├── userId
│       ├── customerId
│       └── createdAt
└── settings/
    └── {userId}/
        └── companyName
```

---

## 🧪 Test

1. Firebase config'i güncelleyin
2. `login.html`'de localStorage yerine Firebase kullanın
3. Kullanıcı kaydedin
4. Gerçek veritabanında görün!

---

## 💰 Ücretlendirme (Firebase)

| Hizmet |cretsiz Limit|
|-------|-----------|
| Authentication | Aylık 10.000 kullanıcı |
| Database | 100MB depolama, 100GB okuma/yazma |
| Hosting | 1GB depolama, 10GB transfer |

Küçük işletmeler için genellikle **ücretsiz** kalır!