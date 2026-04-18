
# 🔒 SECURITY AUDIT APP - HỆ THỐNG BẢO MẬT ANDROID TOÀN DIỆN

## 📌 TỔNG QUAN

**Security Audit App** là ứng dụng Android chuyên dụng để đánh giá, giám sát và nâng cao bảo mật toàn diện. Ứng dụng cung cấp **15 chức năng chính**, đánh giá theo **17 tiêu chí bảo mật** và **280 tiêu chí chi tiết**, hỗ trợ **4 loại tài khoản** với phân quyền rõ ràng, tích hợp **wrapper kết nối PHP backend**.

| Thông số | Giá trị |
|----------|---------|
| Ngôn ngữ | Kotlin 2.0.0 |
| Min SDK | 24 (Android 7.0) |
| Target SDK | 34 (Android 14) |
| Architecture | MVVM + Clean Architecture |
| Dependency Injection | Dagger Hilt |
| Database | Room + SQLCipher |
| Backend | PHP (via ApiWrapper) |

---

## 📱 15 CHỨC NĂNG CHÍNH (SIDEBAR)

| # | Chức năng | Mô tả |
|---|-----------|-------|
| 1 | 📊 Dashboard | Hiển thị trạng thái bảo mật tổng thể, điểm 280 tiêu chí |
| 2 | 🔑 Quản lý phiên đăng nhập | Xem và thu hồi session active |
| 3 | 📱 Quản lý thiết bị tin cậy | Đăng ký / hủy thiết bị đã xác thực |
| 4 | 🛡️ MFA & xác thực 2 lớp | TOTP, SMS, Email, WebAuthn |
| 5 | 📜 Lịch sử hoạt động | Log chi tiết theo 280 tiêu chí |
| 6 | 📄 Báo cáo bảo mật | Tự động xuất PDF/JSON định kỳ |
| 7 | 🔐 Mã hóa tệp & thư mục | AES-256-GCM + ChaCha20 + Secure Container |
| 8 | 🦠 Kiểm tra mã độc ứng dụng | Scan APK, permissions |
| 9 | 🔑 Quản lý mật khẩu & khóa | Lưu trữ trong Keystore/StrongBox |
| 10 | 🌐 Giám sát kết nối mạng | Cảnh báo MITM, root, proxy |
| 11 | ⚙️ Chính sách bảo mật động | Cập nhật từ server (PHP) |
| 12 | 💾 Sao lưu & khôi phục an toàn | End-to-end encrypted backup |
| 13 | 🚨 Hỗ trợ khẩn cấp | Xóa dữ liệu từ xa, khóa app |
| 14 | 🔍 Web Security Scanner | Quét XSS, SQLi, Header, API (gọi PHP) |
| 15 | 🔢 Password Strength Meter | Đo độ mạnh, kiểm tra rò rỉ (gọi PHP) |

---

## 🛡️ 17 TIÊU CHÍ BẢO MẬT

| Nhóm | Tiêu chí |
|------|----------|
| **Xác thực** | 1. Mật khẩu mạnh (entropy, length) / 2. MFA bắt buộc / 3. Xác thực sinh trắc học / 4. Khóa bảo mật phần cứng StrongBox / 5. Timeout tự động đăng xuất |
| **Mạng & Web** | 6. Phát hiện XSS / 7. Phát hiện SQL Injection / 8. Kiểm tra Security Headers / 9. Chống MITM, SSL pinning |
| **Dữ liệu** | 10. Mã hóa local AES-256 / 11. Mã hóa TLS 1.3 khi truyền / 12. Không lưu mật khẩu plaintext |
| **Ứng dụng** | 13. Chống root/jailbreak / 14. Chống debug & repackaging / 15. Phân quyền tối thiểu |
| **Quản lý** | 16. Ghi log đầy đủ & không sửa được / 17. Cập nhật chính sách OTA từ PHP |

---

## 📊 280 TIÊU CHÍ ĐÁNH GIÁ CHI TIẾT

Chia thành **14 nhóm**, mỗi nhóm 20 tiêu chí, chấm điểm 0-5 → tổng tối đa 1400 điểm:

| Nhóm | Nội dung | Số tiêu chí |
|------|----------|-------------|
| 1 | Độ mạnh mật khẩu (Entropy, pattern, dictionary) | 20 |
| 2 | Quét XSS (Reflected, Stored, DOM-based) | 20 |
| 3 | Quét SQL Injection (Boolean, Time-based, Union) | 20 |
| 4 | File Inclusion & Command Execution | 20 |
| 5 | Security Headers (CSP, HSTS, X-Frame, etc.) | 20 |
| 6 | API Security (XXE, SSRF, IDOR, Path Traversal) | 20 |
| 7 | Mã hóa & lưu trữ an toàn | 20 |
| 8 | Xác thực & MFA | 20 |
| 9 | Bảo mật mạng & MITM | 20 |
| 10 | Chống root/debug/repack | 20 |
| 11 | Quản lý phiên & thiết bị | 20 |
| 12 | Logging & giám sát | 20 |
| 13 | Backup & khôi phục | 20 |
| 14 | Chính sách & tuân thủ | 20 |
| **TỔNG** | | **280** |

---

## 👥 4 LOẠI TÀI KHOẢN BẢO MẬT

| Loại tài khoản | Quyền hạn | Chức năng được phép |
|----------------|-----------|---------------------|
| 👑 **Super Admin** | Toàn quyền | Tất cả 15 chức năng + quản lý user |
| 📊 **Security Auditor** | Chỉ xem báo cáo, log, quét | Dashboard, lịch sử, web scanner, password meter (chỉ xem) |
| ⚙️ **Operator** | Thực thi tác vụ | Quản lý phiên, thiết bị, MFA, mã hóa, backup |
| 👁️ **Viewer** | Chỉ xem, không thay đổi | Xem dashboard, báo cáo (read-only) |

---

## 🔧 KIẾN TRÚC ỨNG DỤNG

```
┌─────────────────────────────────────────────────────────────┐
│                      UI Layer (MVVM)                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐       │
│  │Fragment  │ │ViewModel │ │  Adapter │ │  Widget  │       │
│  └────┬─────┘ └────┬─────┘ └──────────┘ └──────────┘       │
├───────┴────────────┴─────────────────────────────────────────┤
│                      Domain Layer (Use Cases)                │
├─────────────────────────────────────────────────────────────┤
│                      Data Layer                              │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────────┐    │
│  │ Room + SQLCipher│ │ Repository  │ │ ApiWrapper (PHP)│    │
│  └──────────────┘ └──────────────┘ └──────────────────┘    │
├─────────────────────────────────────────────────────────────┤
│                    Security Layer                            │
│  ┌──────────────────────────────────────────────────────┐   │
│  │ Keystore │ StrongBox │ Biometric │ AES │ Shamir │    │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

---

## 📁 CẤU TRÚC THƯ MỤC CODE

```
app/src/main/java/com/security/app/
├── common/                 # Constants, utils, base classes
├── data/                   # Local (Room), remote (API), repository
├── domain/                 # Models, use cases
├── ui/                     # 15 chức năng (dashboard, webscanner, passwordmeter...)
├── network/wrapper/        # ApiWrapper, WebScannerWrapper, PasswordWrapper, SyncWrapper
├── security/               # Crypto, keystore, integrity, validator
├── evaluation/             # 280 tiêu chí (14 groups, checkers, calculator)
├── di/                     # Dagger Hilt modules
├── service/                # Background services, workers
├── broadcast/              # Broadcast receivers
└── widget/                 # Home screen widgets
```

---

## 🌐 KẾT NỐI PHP BACKEND (API WRAPPER)

### Các endpoint PHP cần triển khai

```php
POST /api/v1/webscanner/scan       # Quét lỗ hổng website (XSS, SQLi, Header)
GET  /api/v1/webscanner/result/{id}# Lấy kết quả quét theo ID
GET  /api/v1/webscanner/history    # Lịch sử quét

POST /api/v1/password/check        # Kiểm tra mật khẩu rò rỉ (HIBP)
POST /api/v1/password/evaluate     # Đánh giá độ mạnh mật khẩu (AI)

GET  /api/v1/policy/sync           # Đồng bộ chính sách bảo mật
POST /api/v1/cve/sync              # Đồng bộ database CVE
POST /api/v1/logs/upload           # Upload logs bảo mật
POST /api/v1/evaluation/sync       # Đồng bộ 280 tiêu chí
```

### Mã wrapper chính (ApiWrapper.kt)

```kotlin
class ApiWrapper @Inject constructor(
    private val keystoreHelper: KeystoreHelper,
    private val aesEncryption: AesEncryption
) {
    suspend fun get(endpoint: String): ApiResult<JSONObject>
    suspend fun post(endpoint: String, body: JSONObject): ApiResult<JSONObject>
}
```

### Mã WebScannerWrapper.kt (gọi PHP)

```kotlin
class WebScannerWrapper @Inject constructor(
    private val apiWrapper: ApiWrapper
) {
    suspend fun scanWebsite(url: String): WebScanResult
    suspend fun getScanResult(scanId: String): WebScanResult
    suspend fun getScanHistory(limit: Int): List<WebScanHistory>
}
```

### Mã PasswordWrapper.kt (gọi PHP)

```kotlin
class PasswordWrapper @Inject constructor(
    private val apiWrapper: ApiWrapper
) {
    suspend fun checkPasswordLeaked(password: String): PasswordLeakResult
    suspend fun evaluatePasswordStrength(password: String): PasswordStrengthResult
}
```

---

## 🔐 NÂNG CẤP 7: MÃ HÓA TỆP & THƯ MỤC

| Tính năng cũ | Tính năng nâng cấp |
|--------------|-------------------|
| AES-256 CBC | AES-256 GCM + ChaCha20-Poly1305 (lựa chọn động) |
| Keystore đơn | Keystore + StrongBox + Shamir Secret Sharing |
| Mã hóa từng file | Secure Container (giống VeraCrypt) |
| 5 tiêu chí | 20 tiêu chí (nhóm 7 của 280) |

### Các lớp core nâng cấp 7

```kotlin
// data/local/file/SecureContainer.kt
data class SecureContainer(
    val id: String, val name: String, val path: String,
    val encryptionAlgorithm: EncryptionAlgorithm, val isMounted: Boolean
)

// security/crypto/ShamirSecretSharing.kt
class ShamirSecretSharing {
    fun splitSecret(secret: ByteArray, parts: Int, threshold: Int): List<ByteArray>
    fun combineShares(shares: List<ByteArray>): ByteArray
}
```

---

## 📦 CÀI ĐẶT & CHẠY DỰ ÁN

### Yêu cầu hệ thống
- Android Studio Hedgehog | 2023.1.1 trở lên
- JDK 17
- Gradle 8.0+
- PHP 8.0+ (cho backend)

### Các bước cài đặt

```bash
# 1. Clone repository
git clone https://github.com/your-repo/security-audit-app.git
cd security-audit-app

# 2. Mở project bằng Android Studio

# 3. Cập nhật BASE_URL trong ApiWrapper.kt
BASE_URL = "https://your-php-server.com/api/"

# 4. Build project
./gradlew build

# 5. Chạy ứng dụng
./gradlew installDebug
```

### Cấu hình ProGuard (proguard-rules.pro)

```proguard
# Keep security classes
-keep class com.security.app.security.** { *; }
-keep class com.security.app.evaluation.** { *; }

# Keep native methods
-keepclasseswithmembernames class * {
    native <methods>;
}

# Retrofit + OkHttp
-keepattributes Signature, InnerClasses, EnclosingMethod
-dontwarn okhttp3.**
```

---

## 🧪 TESTING

```bash
# Chạy unit tests
./gradlew test

# Chạy instrumentation tests
./gradlew connectedAndroidTest

# Chạy security tests riêng
./gradlew testSecurityUnitTest
```

---

## 📄 GIẤY PHÉP

MIT License - Xem file [LICENSE](LICENSE)

---

## 📧 LIÊN HỆ

- **Email:** security@auditapp.com
- **Website:** https://security-audit-app.com

---




