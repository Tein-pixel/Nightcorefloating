# 📱 NightcoreFloating APK Build Guide

## Cara Build APK Otomatis Menggunakan GitHub Actions

Repo ini sudah dikonfigurasi dengan **GitHub Actions** untuk build APK secara otomatis setiap kali ada `push` ke branch `main`.

### ✅ Cara Menggunakan:

#### **Opsi 1: Trigger Manual (Recommended untuk testing)**
1. Buka repo: https://github.com/Tein-pixel/Nightcorefloating
2. Klik tab **Actions**
3. Pilih workflow **"Build APK"** di sebelah kiri
4. Klik tombol **"Run workflow"** (kuning)
5. Tunggu hingga build selesai (biasanya 5-10 menit)

#### **Opsi 2: Trigger Otomatis**
- Setiap kali kamu push ke branch `main`, workflow akan **otomatis berjalan**
- Build APK akan dibuat secara otomatis

### 📥 Download APK:

Setelah build selesai:
1. Di halaman Actions, klik workflow run yang sudah selesai
2. Scroll ke bawah, cari **"Artifacts"** section
3. Download **"NightcoreFloating-APK"**
4. Extract file `.zip` untuk mendapatkan `app-debug.apk`

### 🎯 Install ke HP:

#### Cara 1: Direct Install via File Manager
1. Copy file `app-debug.apk` ke HP (via kabel USB atau transfer lain)
2. Buka file manager di HP
3. Cari dan tap file APK
4. Tap "Install"
5. Selesai!

#### Cara 2: Via ADB (Advanced)
```bash
adb install project/NightcoreFloating/app/build/outputs/apk/debug/app-debug.apk
```

### 📝 Format Project ZIP:

ZIP harus berisi struktur:
```
NightcoreFloating/
├── app/
│   ├── src/main/
│   │   ├── java/
│   │   ├── res/
│   │   └── AndroidManifest.xml
│   └── build.gradle
├── settings.gradle
├── build.gradle
└── gradlew (optional tapi recommended)
```

### 🔧 Troubleshooting:

#### ❌ Error: "NightcoreFloating.zip not found"
- Pastikan file `NightcoreFloating.zip` ada di root directory repo

#### ❌ Error: "Gradle sync failed"
- Update `build.gradle` dengan:
```gradle
android {
    compileSdkVersion 33
    targetSdkVersion 33
}
```

#### ❌ Error: "gradlew permission denied"
- Workflow sudah handle ini, tapi pastikan `gradlew` file executable

### 🚀 Next Steps:

1. **Update file ZIP** dengan project terbaru
2. **Push ke main branch** atau trigger manual workflow
3. **Download APK** dari Artifacts
4. **Install di HP** dan test!

### 📌 Tips:

- Gunakan **"Run workflow"** untuk testing
- Cek workflow logs jika ada error:
  - Klik workflow run → scroll ke job yang failed → lihat error details
- File APK di-store selama 30 hari, bisa didownload kapan saja dari Artifacts

---

**Butuh bantuan?** Cek logs di Actions tab untuk error details lebih lengkap!
