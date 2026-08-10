# Toolbox Assistência Pro

![Platform](https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Build Status](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)
![Package](https://img.shields.io/badge/Package-com.heavy.assistenciatoolbox-informational?style=for-the-badge)

> Ferramentas de bancada para manutenção de celular: Remoção de Vírus, Desbloqueio FRP, Hard Reset, Teste de Display Touch, Bateria, IMEI e O.S.

---

## 📌 Visão Geral e Recursos Configurados

Este repositório contém o código-fonte completo do **Toolbox Assistência Pro**, configurado e exportado via **Heavy Studio Pro IDE**. O projeto foi estruturado seguindo as melhores práticas de arquitetura Android/iOS, prontos para compilação automatizada via **GitHub Actions** e distribuição para testadores no **Firebase Console**.

### 🎨 Componentes da Interface de Usuário (Configurados na IDE)
- **Botão Interativo**: "🛡️ Remover Vírus & Malware" *(Ação: `virus_scan`)*
- **Botão Interativo**: "🔓 Desbloqueio FRP & Conta Google" *(Ação: `frp_bypass`)*
- **Botão Interativo**: "⚡ Hard Reset & Fastboot Unlock" *(Ação: `hard_reset`)*
- **Botão Interativo**: "🖥️ Teste de Tela & Touchscreen" *(Ação: `touch_test`)*
- **Botão Interativo**: "🔋 Diagnóstico de Bateria & Carga" *(Ação: `battery_test`)*
- **Botão Interativo**: "🔊 Teste de Alto-Falante & Microfone" *(Ação: `audio_test`)*
- **Botão Interativo**: "📱 Leitor de IMEI & Especificações" *(Ação: `imei_reader`)*
- **Botão Interativo**: "📋 Gerar Ordem de Serviço (O.S.)" *(Ação: `os_generator`)*
- **Botão Interativo**: "🧮 Calculadora de Orçamento de Reparo" *(Ação: `cost_calc`)*
- **Botão Interativo**: "💻 Gerador de Scripts ADB / Fastboot" *(Ação: `adb_scripts`)*

### 🧠 Recursos de Inteligência Artificial & API
- **Modelo Gemini AI**: Integração com `gemini-3.6-flash`
- **Pesquisa em Tempo Real**: ✅ Habilitada (Google Search Grounding)
- **Thinking Budget**: Automático
- **Instruções do Sistema**: Personalizadas na IDE

### 🔐 Segurança, Keystore & Release Signing
- **Assinatura Manual**: Suporte a Keystore customizada no Gradle

### 🔥 Integração & Entrega Contínua (CI/CD)
- **Distribuição**: Artefatos AAB/APK disponíveis via GitHub Artifacts
- **Ícone do App**: Ícone vetorial gerado com a etiqueta "FIX".

---

## 📁 Estrutura de Diretórios do Projeto

```
├── .github/
│   └── workflows/
│       └── android.yml            # Pipeline de Build, Testes e Deploy no GitHub Actions
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/heavy/assistenciatoolbox/
│   │       │   └── MainActivity.kt # Código Principal da Aplicação
│   │       ├── res/
│   │       │   ├── layout/         # Telas XML (activity_main.xml, item_message.xml)
│   │       │   ├── values/         # Temas, Cores e Dimensões
│   │       │   └── drawable/       # Ícones e Backgrounds Vetoriais
│   │       └── AndroidManifest.xml # Manifesto Auditado de Segurança
│   └── build.gradle                # Dependências do Módulo App
├── build.gradle                    # Configurações do Projeto
├── settings.gradle                 # Repositórios e Módulos
└── README.md                       # Documentação do Repositório
```

---

## 🚀 Como Compilar e Executar Localmente

### Pré-requisitos
- **Android Studio Jellyfish / Koala** ou versão mais recente
- **JDK 17** (Java Development Kit) instalado e configurado
- **Gradle 8.x+**

### Passo a Passo
1. **Clonar o Repositório**:
   ```bash
   git clone https://github.com/aloisioars1/toolbox-assist-ncia-pro.git
   cd toolbox-assist-ncia-pro
   ```

2. **Abrir no Android Studio**:
   - Abra o Android Studio, selecione **Open** e escolha a pasta raiz do projeto.
   - Aguarde a sincronização inicial do Gradle.

3. **Executar a Compilação de Teste (Debug APK)**:
   ```bash
   ./gradlew assembleDebug
   ```
   O APK de teste será gerado em: `app/build/outputs/apk/debug/app-debug.apk`

4. **Gerar o App Bundle assinado (Release AAB)**:
   ```bash
   ./gradlew bundleRelease
   ```
   O pacote AAB será gerado em: `app/build/outputs/bundle/release/app-release.aab`

---

## 🔑 Configuração de Segredos no GitHub Actions (Secrets)

Para habilitar a compilação de Release e o envio automático para o Firebase App Distribution no GitHub Actions, adicione as seguintes variáveis na guia **Settings > Secrets and variables > Actions** do seu repositório:

| Nome do Secret | Descrição |
| :--- | :--- |
| `KEYSTORE_BASE64` | Chave de assinatura JKS codificada em Base64 |
| `KEYSTORE_PASSWORD` | Senha mestre do arquivo de Keystore |
| `KEYSTORE_ALIAS` | Nome do Alias da chave de release |
| `KEYSTORE_KEY_PASSWORD` | Senha específica da chave do Alias |
| `FIREBASE_APP_ID` | ID do aplicativo cadastrado no Firebase Console |
| `FIREBASE_TOKEN` | Token CI gerado via `firebase login:ci` |

---

## 🛡️ Auditoria de Segurança do AndroidManifest.xml
O manifesto deste aplicativo passa por verificações de conformidade com as diretrizes de privacidade e segurança da **Google Play Store**:
- ❌ Permissões sensíveis não justificadas (SMS, Call Log) são bloqueadas ou sinalizadas.
- 🔒 Tráfego não criptografado (`usesCleartextTraffic`) é desabilitado por padrão.
- 🛡️ Proteção de backup de dados (`allowBackup="false"`) configurada para prevenir extração de dados.

---

## 📄 Licença e Créditos
Este projeto foi gerado com **Heavy Studio Pro IDE** & **Google Gemini AI**.
Distribuído sob a licença **MIT**. Veja `LICENSE` para mais detalhes.
