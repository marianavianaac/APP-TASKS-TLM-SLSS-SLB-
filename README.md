# APP-TASKS-TLM-SLSS-SLB-
Flutter &amp; Firebase-powered Task Tracker for SLB TLM Workshop (Web, Desktop &amp; Mobile)
Este é o repositório do **TLM Tasks App**, construido em **Flutter** + **Firebase** para desktop (Windows), web e mobile (Android/iOS).

## 📋 Sumário

- [Pré-requisitos](#-pré-requisitos)  
- [Setup do Ambiente](#-setup-do-ambiente)  
- [Clonar o Repositório](#-clonar-o-repositório)  
- [Configurar o Firebase](#-configurar-o-firebase)  
- [Rodando o App](#-rodando-o-app)  
  - [Android](#android)  
  - [iOS](#ios)  
  - [Web](#web)  
  - [Windows (desktop)](#windows-desktop)  
- [Estrutura do Projeto](#-estrutura-do-projeto)  
- [Scripts Úteis](#-scripts-úteis)  
- [`.gitignore`](#gitignore)  
- [Contatos / Dúvidas](#-contatos--dúvidas)  

---

## 🔑 Pré-requisitos

Antes de tudo, instale:

- **Git** (para clonar e versionar)  
- **VS Code**  
  - Extensões recomendadas: **Flutter**, **Dart**, **Firebase**  
- **Flutter SDK** (recomendo a **versão estável** mais recente)  
- **Android SDK / Android Studio** (para Android)  
- **Xcode** (somente em macOS, para iOS)  
- **Visual Studio Build Tools** com workload **Desktop development with C++** (para Windows)  
- **Firebase CLI** (opcional, mas facilita deploy e config)

Links de download:

- VS Code: https://code.visualstudio.com/  
- Flutter: https://flutter.dev/docs/get-started/install  
- Android Studio: https://developer.android.com/studio  
- Xcode: https://developer.apple.com/xcode/  
- Visual Studio Build Tools: https://visualstudio.microsoft.com/pt-br/downloads/  
- Firebase CLI: https://firebase.google.com/docs/cli  

---

## ⚙️ Setup do Ambiente

1. **Flutter**  
   - Extraia e adicione `flutter/bin` ao seu PATH.  
   - Rode:  
     ```bash
     flutter doctor
     ```
     e siga as indicações para instalar dependências faltantes.

2. **VS Code**  
   - Abra a pasta do projeto.  
   - Instale as extensões Flutter e Dart.

3. **Configurar Android**  
   - No Android Studio → SDK Manager → Instale Android SDK 33+ e ferramentas de build.  
   - Configure a variável `ANDROID_HOME` (ou `ANDROID_SDK_ROOT`) apontando para a pasta SDK.

4. **Configurar iOS** (macOS)  
   - Rode `sudo gem install cocoapods`  
   - Dentro de `ios/`, rode:
     ```bash
     pod install
     ```

5. **Configurar Windows**  
   - Garanta que o workload “Desktop development with C++” do Visual Studio esteja instalado, incluindo CMake.  
   - Flutter já gera o `windows/` com CMakeLists automaticamente.

---

## 📥 Clonar o Repositório

```bash
git clone https://github.com/SEU_USUARIO/NOME_DO_REPO.git
cd NOME_DO_REPO
flutter pub get
```

---

## 🔐 Configurar o Firebase

1. No console do Firebase, crie (ou use) o projeto **tlm-tasks-app**.  
2. Adicione apps nas plataformas que precisar (Android, iOS, Web).  
3. Baixe **google-services.json** e coloque em `android/app/`.  
4. Baixe **GoogleService-Info.plist** e coloque em `ios/Runner/`.  
5. Para Web, dentro da pasta raiz rode:
   ```bash
   flutterfire configure --project tlm-tasks-app
   ```
   Isso gera `lib/firebase_options.dart`.  
6. Commit desses arquivos **não** deve ser versionado se contiver chaves privadas — use variáveis de ambiente ou mantenha-os seguros.

---

## ▶️ Rodando o App

### Android

```bash
flutter run -d android
# ou para gerar APK:
flutter build apk --release
```

### iOS (macOS)

```bash
flutter run -d ios
# ou gerar IPA:
flutter build ipa
```

### Web

1. Gere a build:
   ```bash
   flutter build web --release
   ```
2. Teste localmente:
   ```bash
   flutter run -d web-server --release --web-port 8080
   # abra http://localhost:8080
   ```

3. Deploy no Firebase Hosting (após build):
   ```bash
   firebase deploy --only hosting
   ```
   > Certifique-se de que `firebase.json` aponte para `"public": "build/web"`.

### Windows (desktop)

```bash
flutter run -d windows
# ou gerar executável:
flutter build windows --release
```

---

## 📂 Estrutura do Projeto

```
├─ android/          # Configs Android / Gradle
├─ ios/              # Configs Xcode / CocoaPods
├─ linux/            # (se suportado)
├─ macos/            # (se suportado)
├─ windows/          # Build CMake p/ desktop
├─ web/              # Build web estático
├─ lib/
│  ├─ main.dart      # Entry point
│  ├─ firebase_options.dart
│  ├─ screens/       # suas telas Dart
│  └─ widgets/       # componentes reutilizáveis
├─ assets/           # ícones, fontes, imagens
├─ pubspec.yaml      # dependências e assets
├─ firebase.json     # config do Firebase Hosting
└─ README.md         # este guia
```

---

## 🚀 Scripts Úteis

- **Formatar código**  
  ```bash
  flutter format .
  ```

- **Analise estática**  
  ```bash
  flutter analyze
  ```

- **Testes (se houver)**  
  ```bash
  flutter test
  ```

---

## `.gitignore`

```gitignore
# Flutter / Dart
.dart_tool/
.packages
.pub-cache/
build/
.idea/
.vscode/
*.iml

# Android
android/.gradle/
android/app/*.keystore

# iOS
ios/Pods/
ios/Runner/GeneratedPluginRegistrant.*

# macOS
macos/Flutter/ephemeral/

# Web
build/web/

# Firebase (caso queira manter config fora do repo)
android/app/google-services.json
ios/Runner/GoogleService-Info.plist
lib/firebase_options.dart
```

---

## 🤝 Contatos / Dúvidas

Se algo não funcionar, fale comigo:

- **Email:** mariana.correia@cte.ufal.br 
 

