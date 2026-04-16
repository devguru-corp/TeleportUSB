# Teleport USB 설치 가이드

DEVGURU **Teleport USB**는 USB 장치를 네트워크를 통해 원격 PC에서 사용할 수 있게 해주는 Virtual USB Network 솔루션입니다.

**동작 원리:** Server PC에 물리적으로 연결된 USB 장치를 네트워크로 공유하면, Client PC에서 해당 USB를 마치 직접 꽂은 것처럼 사용할 수 있습니다.

```
[Server PC] ──USB 장치 연결──▶ 네트워크 공유 ──▶ [Client PC] 에서 원격 사용
```

---

## 목차

- [1. 사전 준비](#1-사전-준비)
  - [1.1 설치 파일 구성](#11-설치-파일-구성)
  - [1.2 시스템 요구사항](#12-시스템-요구사항)
  - [1.3 네트워크 요구사항](#13-네트워크-요구사항)
- [2. Server 설치 (USB 장치를 연결할 PC)](#2-server-설치-usb-장치를-연결할-pc)
  - [2.1 Server 프로그램 설치](#21-server-프로그램-설치)
  - [2.2 USB 장치 공유](#22-usb-장치-공유)
- [3. Client 설치 (USB 장치를 사용할 PC)](#3-client-설치-usb-장치를-사용할-pc)
  - [3.1 Client 프로그램 설치](#31-client-프로그램-설치)
  - [3.2 Server 연결 및 장치 사용](#32-server-연결-및-장치-사용)
- [4. 사용 확인](#4-사용-확인)
- [5. 트러블슈팅](#5-트러블슈팅)
- [6. 참고사항](#6-참고사항)

---

## 1. 사전 준비

### 1.1 설치 파일 구성

이 저장소에는 2개의 설치 파일이 포함되어 있습니다.

| 파일명 | 설치 대상 | 설명 |
|--------|----------|------|
| `TeleportUSB_server_installer_64bit.msi` | **Server PC** | USB 장치가 물리적으로 연결되어 있는 PC에 설치 |
| `TeleportUSB_client_installer_64bit.msi` | **Client PC** | USB 장치를 원격으로 사용할 PC에 설치 |

> **설치 파일 다운로드:** 이 저장소의 [`TeleportUSB_installer_64bit/`](./TeleportUSB_installer_64bit/) 폴더에서 MSI 파일을 다운로드하세요.

### 1.2 시스템 요구사항

Server PC와 Client PC **모두** 아래 사양을 충족해야 합니다.

| 항목 | 최소 사양 |
|------|----------|
| OS | Windows 10 64bit 이상 |
| Processor | Intel i3 Dual Core 이상 |
| RAM | 4GB 이상 |
| 권한 | **관리자 권한** (MSI 설치 시 필요) |

### 1.3 네트워크 요구사항

| 항목 | 조건 |
|------|------|
| 네트워크 | Server PC와 Client PC가 **같은 네트워크(서브넷)**에 있어야 합니다 |
| 방화벽 | Server PC에서 Teleport USB가 사용하는 포트가 열려 있어야 합니다 |
| IP 확인 | Server PC의 IP 주소를 미리 확인해 두세요 (아래 방법 참조) |

#### Server PC의 IP 주소 확인 방법

Server PC에서 명령 프롬프트(`cmd`)를 열고 다음 명령어를 입력합니다:

```cmd
ipconfig
```

출력 결과에서 **IPv4 주소** 항목을 확인합니다. (예: `192.168.100.9`)

```
이더넷 어댑터:
   IPv4 주소 . . . . . . . . : 192.168.100.9    ← 이 값을 메모하세요
   서브넷 마스크 . . . . . . : 255.255.255.0
   기본 게이트웨이 . . . . . : 192.168.100.1
```

---

## 2. Server 설치 (USB 장치를 연결할 PC)

> **이 섹션은 USB 장치가 물리적으로 연결된 PC에서 진행합니다.**

### 2.1 Server 프로그램 설치

**Step 1.** `TeleportUSB_server_installer_64bit.msi` 파일을 **더블 클릭**하여 실행합니다.

- Windows에서 "이 앱이 디바이스를 변경할 수 있도록 허용하시겠어요?" 라는 UAC 팝업이 나타나면 **`예`** 를 클릭합니다.

**Step 2.** 설치 마법사가 나타나면 **`accept the terms in the License Agreement`** 체크박스를 선택한 후, **`Install`** 버튼을 클릭합니다.

![Server 설치 마법사 - 라이선스 동의 후 Install 클릭](images/server-install-wizard.png)

**Step 3.** 설치가 완료되면 **`Finish`** 버튼을 클릭합니다.

**Step 4.** 바탕화면 또는 시작 메뉴에서 **`Teleport USB Server`** 를 실행합니다.

- 트레이 아이콘(화면 우측 하단)에 Teleport USB 아이콘이 나타나면 정상 실행된 것입니다.

### 2.2 USB 장치 공유

**Step 1.** 공유할 USB 장치를 Server PC에 연결합니다.

**Step 2.** Teleport USB Server 프로그램 창에서 연결된 USB 장치 목록이 표시됩니다. 공유할 장치 옆의 **`Share`** 버튼을 클릭합니다.

![Server - 장치 목록에서 Share 버튼 클릭](images/server-share-button.png)

**Step 3.** 공유 성공 확인:
- USB 아이콘에 **녹색 테두리**가 나타남
- `Share` 버튼이 **비활성화**(회색)됨
- 장치 이름이 표시됨 (예: `Integrated Camera`, `USB Mass Storage` 등)

![Server - 공유 완료 상태 (녹색 테두리)](images/server-share-complete.png)

> **공유 해제:** 공유를 중단하려면 장치 옆의 **`x`** 버튼을 클릭합니다.

---

## 3. Client 설치 (USB 장치를 사용할 PC)

> **이 섹션은 USB 장치를 원격으로 사용할 PC에서 진행합니다.**

### 3.1 Client 프로그램 설치

**Step 1.** `TeleportUSB_client_installer_64bit.msi` 파일을 **더블 클릭**하여 실행합니다.

- UAC 팝업이 나타나면 **`예`** 를 클릭합니다.

**Step 2.** 설치 마법사에서 **`accept the terms in the License Agreement`** 체크박스를 선택한 후, **`Install`** 버튼을 클릭합니다.

![Client 설치 마법사 - 라이선스 동의 후 Install 클릭](images/client-install-wizard.png)

**Step 3.** 설치 완료 후 **`Finish`** 를 클릭합니다.

**Step 4.** 바탕화면 또는 시작 메뉴에서 **`Teleport USB Client`** 를 실행합니다.

### 3.2 Server 연결 및 장치 사용

**Step 1.** Client 프로그램 상단의 **`Add Server`** 버튼을 클릭합니다.

**Step 2.** `Add Server` 창이 열리면:
- **`Server IP`** 칸에 [앞서 확인한 Server PC의 IP 주소](#server-pc의-ip-주소-확인-방법)를 입력합니다 (예: `192.168.100.9`)
- `Description` 칸은 선택사항입니다 (메모 용도)
- **`Add`** 버튼을 클릭합니다

![Client - Server IP 입력 후 Add 클릭](images/client-add-server-ip.png)

**Step 3.** Server에서 공유된 USB 장치가 **자동으로 검색**되어 목록에 표시됩니다. 사용할 장치 옆의 **`Connect`** 버튼을 클릭합니다.

![Client - 검색된 장치에서 Connect 클릭](images/client-device-found.png)

**Step 4.** 연결 성공 확인:
- USB 아이콘에 **녹색 테두리**가 나타남
- `Connect` 버튼이 **비활성화**(회색)됨

![Client - 연결 완료 상태 (녹색 테두리)](images/client-connect-complete.png)

> **연결 해제:** 장치 옆의 **`x`** 버튼을 클릭합니다.

---

## 4. 사용 확인

연결이 완료되면 Client PC에서 USB 장치를 **로컬에 직접 연결한 것과 동일하게** 사용할 수 있습니다.

예시: USB 메모리가 공유된 경우, Client PC의 파일 탐색기에 USB 드라이브가 나타나며 **읽기/쓰기/삭제** 등 모든 동작이 가능합니다.

![Client PC에서 공유된 USB 드라이브 사용 화면](images/client-usb-drive-usage.png)

### 정상 동작 체크리스트

| 확인 항목 | 예상 결과 |
|----------|----------|
| Server에서 USB 아이콘에 녹색 테두리 | 장치 공유 정상 |
| Client에서 `Add Server` 후 장치 검색됨 | 네트워크 연결 정상 |
| Client에서 USB 아이콘에 녹색 테두리 | 장치 연결 정상 |
| Client PC 파일 탐색기에 USB 드라이브 표시 | 사용 준비 완료 |

---

## 5. 트러블슈팅

### 장치가 검색되지 않는 경우

| 원인 | 해결 방법 |
|------|----------|
| Server에서 장치를 공유하지 않음 | Server 프로그램에서 `Share` 버튼 클릭 여부 확인 |
| IP 주소 오류 | Server PC에서 `ipconfig`로 IP 재확인 후 다시 입력 |
| 네트워크 분리 | 두 PC가 같은 네트워크/서브넷에 있는지 확인 |
| 방화벽 차단 | Server PC의 Windows 방화벽에서 Teleport USB를 **허용** 처리 |

### 방화벽 허용 방법 (Server PC)

1. Windows 검색에서 **`Windows Defender 방화벽`** 을 검색하여 열기
2. 좌측 메뉴에서 **`앱 또는 기능을 Windows Defender 방화벽을 통해 허용`** 클릭
3. **`설정 변경`** → **`다른 앱 허용`** 클릭
4. Teleport USB Server 실행 파일을 찾아 추가
5. **개인** 및 **공용** 네트워크 모두 체크 후 **`확인`**

### 연결 후 장치가 동작하지 않는 경우

| 원인 | 해결 방법 |
|------|----------|
| 드라이버 미설치 | Client PC에 해당 USB 장치의 드라이버 설치 필요 |
| 장치 사용 충돌 | Server PC에서 해당 USB 장치를 사용 중인 프로그램 종료 |
| 프로그램 미실행 | Server/Client 양쪽 모두 프로그램이 실행 중인지 확인 |

---

## 6. 참고사항

- Server 프로그램과 Client 프로그램의 버전은 동일해야 합니다 (현재 v1.3.0.0)
- 하나의 USB 장치는 **한 번에 하나의 Client**만 연결하여 사용할 수 있습니다
- Server PC가 종료되거나 USB 장치가 분리되면 Client의 연결도 자동으로 끊어집니다
- 프로그램 제거: Windows **`설정`** → **`앱`** → `Teleport USB Server/Client` 검색 → **`제거`**
