# 🚀 Guia de Deploy Mobile com Expo + EAS

Um guia simples, direto e prático para publicar aplicativos **Expo** nas lojas oficiais:

- 🤖 **Android** no Google Play
- 🍎 **iOS** na App Store

Este repositório reúne os passos essenciais para sair do app rodando localmente com `expo start` e chegar até uma versão pronta para teste, revisão ou publicação.

---

## ✨ O que você encontra aqui

📦 Preparação do projeto Expo  
🔐 Configuração de credenciais no EAS  
🏗️ Geração de builds nativos  
🧪 Envio para testes internos, TestFlight ou tracks do Google Play  
🛒 Publicação nas lojas oficiais  
✅ Observações importantes para evitar erros comuns

---

## 📚 Guias disponíveis

| Plataforma | Guia | Resultado esperado |
| --- | --- | --- |
| 🤖 Android | [android-deploy.md](./android-deploy.md) | Gerar `.aab` ou `.apk` e publicar no Google Play |
| 🍎 iOS | [beta-deploy.ios.md](./beta-deploy.ios.md) | Gerar `.ipa` e enviar para App Store Connect/TestFlight |

---

## 🧭 Fluxo geral de publicação

Antes de publicar em qualquer loja, o caminho normalmente passa por estas etapas:

1. ✅ Ter o app Expo funcionando localmente com `expo start`
2. ⚙️ Ajustar `app.json` ou `app.config.js`
3. 🔑 Configurar conta de desenvolvedor da loja
4. 🛠️ Instalar e configurar o EAS CLI
5. 🏗️ Gerar o build nativo com `eas build`
6. 📤 Enviar o build para a loja com EAS Submit ou upload manual
7. 🧾 Preencher metadados, screenshots, privacidade e classificação
8. 🚀 Liberar para teste ou produção

---

## 🤖 Android em resumo

Para publicar no Google Play, você vai precisar de:

- Conta Google
- Conta no Google Play Console
- Pacote Android configurado em `expo.android.package`
- `versionCode` e `versionName`
- Build gerado pelo EAS, preferencialmente em `.aab`

Comando principal:

```bash
eas build --platform android --profile production
```

Depois disso, o build pode ser enviado para uma track de teste ou produção no Google Play Console.

➡️ Veja o passo a passo completo em [android-deploy.md](./android-deploy.md).

---

## 🍎 iOS em resumo

Para publicar na App Store ou testar via TestFlight, você vai precisar de:

- Apple ID com autenticação de dois fatores
- Conta no Apple Developer Program
- App configurado no App Store Connect
- Bundle Identifier configurado em `expo.ios.bundleIdentifier`
- Build `.ipa` gerado pelo EAS

Comando principal:

```bash
eas build --platform ios --profile production
```

Depois disso, o build pode ser enviado para o App Store Connect usando EAS Submit ou Transporter.

➡️ Veja o passo a passo completo em [beta-deploy.ios.md](./beta-deploy.ios.md).

---

## 🛠️ Comandos úteis

```bash
# Instalar EAS CLI
npm install -g eas-cli

# Fazer login no Expo
eas login

# Configurar EAS no projeto
eas build:configure

# Revisar credenciais
eas credentials

# Build Android
eas build --platform android --profile production

# Build iOS
eas build --platform ios --profile production

# Enviar build para a loja
eas submit
```

---

## ⚠️ Observações importantes

- O **Expo Go** é ótimo para desenvolvimento, mas não substitui o build nativo para publicação.
- Para Android, o formato recomendado para Google Play é `.aab`.
- Para iOS, a publicação passa pelo App Store Connect e pode ser testada primeiro via TestFlight.
- As lojas exigem informações de privacidade, classificação etária, screenshots e políticas do app.
- O EAS pode gerenciar credenciais automaticamente, o que facilita bastante o processo.

---

## 🎯 Para quem é este repositório?

Para devs que já têm um app Expo pronto ou quase pronto e querem transformar aquele clássico “funciona na minha máquina” em:

- 🧪 um build testável
- 📲 um app instalável
- 🛒 uma publicação real na loja

---

## 💡 Próximo passo

Escolha sua plataforma e siga o guia completo:

- [Publicar no Android](./android-deploy.md)
- [Publicar no iOS](./beta-deploy.ios.md)

Boa publicação! 🚀
