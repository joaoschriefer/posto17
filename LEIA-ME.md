# Posto 17 — projeto para gerar APK Android

O jogo está em `www/index.html`, com os recursos principais embutidos, e é empacotado com Capacitor. O workflow do GitHub Actions gera um APK de teste (`app-debug.apk`) automaticamente.

## Gerar o APK sem instalar ferramentas no computador

1. Entre em https://github.com e crie um repositório vazio.
2. Extraia este ZIP e envie **o conteúdo da pasta** `posto17-apk` para o repositório (incluindo a pasta `.github`).
3. Abra a aba **Actions** no repositório e permita a execução de workflows, se o GitHub solicitar.
4. Selecione **Build APK** e clique em **Run workflow** — ou faça um commit/push para iniciar automaticamente.
5. Quando terminar, abra a execução e baixe o artefato **posto17-apk** na seção **Artifacts**. Ele contém `app-debug.apk`.
6. Transfira o APK para o Android e abra-o para instalar. Talvez seja necessário autorizar a instalação dessa fonte nas configurações do celular.

## Gerar localmente

Requisitos: Node.js 20, Java 17 e Android SDK configurado.

```bash
npm install
npx cap add android
```

Depois, configure a orientação/tela cheia conforme necessário e execute:

```bash
npx cap sync android
cd android
./gradlew assembleDebug
```

O APK será criado em `android/app/build/outputs/apk/debug/app-debug.apk`.

## Observações

- Identificador Android: `com.posto17.game`
- Nome exibido: `Posto 17`
- A versão `debug` é apropriada para testes e instalação manual; para publicação na Play Store, será necessário preparar uma versão de lançamento assinada.
