# DongPassword 개인정보 처리방침 (Privacy Policy)

**시행일 (Effective Date):** 2026-11-17  
**확장 프로그램 및 애플리케이션 명칭 (Product Name):** DongPassword — Windows 보안 비밀번호 금고  
**개발자 (Publisher):** DongHyuk Kim

---

## [한국어] 개인정보 처리방침

**DongPassword**(브라우저 확장 프로그램 및 Windows 데스크톱 금고 앱)는 사용자의 개인정보와 계정 자격 증명을 **외부 서버로 일체 수집·전송·저장하지 않는 100% 로컬(On-Device) 보안 비밀번호 금고**입니다.

### 1. 수집 및 외부 전송하는 개인정보: 없음 (Zero Cloud / Zero Telemetry)
- DongPassword는 자체 웹 서버, 클라우드 데이터베이스, 외부 분석 도구(Google Analytics 등), 광고 SDK, 원격 로그 수집기를 **전혀 사용하지 않습니다.**
- 사용자가 저장하는 웹사이트 URL, 아이디(Username), 비밀번호(Password), 메모 등 모든 데이터는 인터넷이나 제3자 서버로 절대 전송되지 않습니다.

### 2. 데이터의 로컬 처리 및 암호화 보관 방식
- 브라우저 확장 프로그램은 사용자가 웹사이트에 로그인하거나 자동 입력을 요청할 때만 Chromium 표준 **Native Messaging (`com.dopt.password`)** 표준 입출력 파이프를 통해 **동일 PC 내부에 설치된 `DongPasswordNativeHost.exe` 로컬 프로세스**와만 통신합니다.
- 모든 비밀번호 데이터는 사용자 PC 내부 저장소(`%APPDATA%\DongPassword\`)에만 보관되며, **Windows DPAPI (`ProtectedData`, `CurrentUser` 범위)** 및 **AES-256-GCM** 이중 암호화로 보호됩니다.
- 민감한 작업(비밀번호 열람, 복사, 이력 복원, 삭제, 백업 내보내기) 시에는 Windows OS 계정 비밀번호 인증(`LogonUser` / Windows Security)을 거쳐야만 복호화됩니다.

### 3. 브라우저 확장 프로그램 권한 사용 목적
DongPassword 브라우저 확장 프로그램이 요청하는 권한은 오직 아래의 로컬 기능 수행에만 사용됩니다.
- **`nativeMessaging`**: 내 PC에 설치된 로컬 금고 호스트(`com.dopt.password`)와 안전하게 자격 증명을 주고받기 위해 사용합니다.
- **`activeTab` / `tabs`**: 현재 열려 있는 탭의 도메인 주소(URL)에 일치하는 저장 계정을 조회하여 표시하기 위해 사용합니다. (방문 기록을 수집하거나 외부로 전송하지 않습니다.)
- **`scripting` / `host_permissions` (`http://*/*`, `https://*/*`)**: 다양한 웹사이트의 로그인 폼(ID/비밀번호 입력란)을 감지하여 로그인 시 로컬 금고 저장을 돕고, 재방문 시 사용자의 원클릭 자동 입력 바를 표시하기 위해 사용합니다.
- **`storage`**: 확장 프로그램의 로컬 UI 상태 등 최소한의 브라우저 내부 설정값만 기기 내에 임시 저장합니다.

### 4. 제3자 제공 및 판매 금지
- 수집하거나 보유하는 서버 데이터가 없으므로, 어떠한 사용자 정보도 제3자에게 제공, 공유, 임대 또는 판매하지 않습니다.

### 5. 데이터의 삭제 및 사용자 통제권
- 사용자는 언제든지 DongPassword 데스크톱 앱에서 개별 계정 또는 이력을 즉시 영구 삭제할 수 있으며, 프로그램 제거 또는 로컬 데이터 폴더(`%APPDATA%\DongPassword`) 삭제 시 모든 암호화 데이터가 PC에서 완전히 삭제됩니다.

---

## [English] Privacy Policy

**DongPassword** (Browser Extension & Companion Windows Desktop Vault Application) is a **100% offline, local-only password vault**. We **do NOT collect, transmit, store, share, or sell** any personal data, browsing history, or user credentials to any external server or third party.

### 1. Data Collection & External Transmission: None
- DongPassword operates with **zero cloud servers, zero external APIs, zero analytics/telemetry trackers, and zero advertisements**.
- No URLs, usernames, passwords, form inputs, or personal information ever leave the user's local Windows computer.

### 2. Local Storage & Encryption Architecture
- All communication between the Microsoft Edge / Chromium browser extension and the companion Windows desktop vault occurs strictly inside the user's local machine via Chromium's standard **Native Messaging (`com.dopt.password`)** stdio pipe (`DongPasswordNativeHost.exe`).
- All vault records are stored exclusively on the user's local disk (`%APPDATA%\DongPassword\`) encrypted at rest using **Windows Data Protection API (DPAPI, `CurrentUser` scope)** combined with **AES-256-GCM**.
- Viewing, copying, deleting, or exporting saved passwords requires local Windows OS account authentication.

### 3. Justification of Browser Extension Permissions
Each requested permission is used strictly locally on the user's device:
- **`nativeMessaging`**: Required to communicate over local stdio with the companion Windows Native Messaging Host (`com.dopt.password`) installed on the same PC.
- **`activeTab` & `tabs`**: Used solely to match the current tab's domain/hostname against locally stored credentials so matching accounts can be offered in the popup and autofill bar. Browsing history is never logged or transmitted anywhere.
- **`scripting` & `host_permissions` (`http://*/*`, `https://*/*`)**: Required because login forms exist across arbitrary user-visited websites. Content scripts detect username/password inputs locally on the page to capture user-submitted logins into the local vault and fill credentials upon explicit user click.
- **`storage`**: Used only for lightweight local extension preferences inside the browser.

### 4. Third-Party Sharing
- Because zero user data is collected or transmitted off-device, no data is ever shared with, disclosed to, or sold to any third party.

### 5. User Control & Data Deletion
- Users have complete local ownership of their vault data and may view, export (`.dpbackup` encrypted archive), or permanently delete individual or all credentials at any time directly from the DongPassword desktop app or by removing `%APPDATA%\DongPassword`.
