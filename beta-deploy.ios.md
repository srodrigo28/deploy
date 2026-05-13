## Sequência completa de deploy iOS usando Expo / EAS

### 1. Criar a conta Apple
1. Vá para `https://appleid.apple.com/` e crie um Apple ID.
2. Ative a autenticação de dois fatores (2FA), que é obrigatória para desenvolvimento iOS.

### 2. Registrar-se no Apple Developer
1. Acesse `https://developer.apple.com/`.
2. Entre com o Apple ID.
3. Inscreva-se no Apple Developer Program.
4. Pague a anuidade (US$ 99/ano) e complete os dados pessoais ou da empresa.

### 3. Configurar App Store Connect
1. Acesse `https://appstoreconnect.apple.com/`.
2. Aceite os termos, contratos e políticas se solicitado.
3. Complete o cadastro de informações de contato, banco e impostos, caso vá publicar o app.

### 4. Preparar o projeto Expo
1. Verifique que seu app Expo já roda localmente com `expo start`.
2. Confirme o arquivo de configuração (`app.json` ou `app.config.js`):
   - `expo.name`
   - `expo.slug`
   - `expo.ios.bundleIdentifier` (por exemplo: `com.seunome.app`)
   - `expo.ios.buildNumber`
3. Se ainda não tiver instalado, adicione o EAS CLI:
   - `npm install -g eas-cli`
   - ou `yarn global add eas-cli`

### 5. Fazer login no Expo
1. No terminal do projeto:
   - `eas login`
2. Se não tiver conta Expo, crie ou faça login com:
   - `expo register`
   - `expo login`

### 6. Configurar EAS Build no projeto
1. No diretório do projeto, execute:
   - `eas build:configure`
2. Escolha a plataforma `iOS` quando solicitado.
3. Confirme o perfil de build desejado (`production`, `preview` ou `development`).

### 7. Configurar credenciais Apple no EAS
1. O EAS pode gerenciar credenciais automaticamente durante o build.
2. Se precisar revisar, use:
   - `eas credentials`
3. Permita que o EAS gere ou importe:
   - certificado de distribuição
   - provisioning profile
   - App Store Connect API key (opcional)

### 8. Fazer o build iOS com EAS
1. Execute:
   - `eas build --platform ios --profile production`
2. Aguarde a compilação nos servidores Expo.
3. Ao finalizar, o EAS retornará um link para baixar o `.ipa`.

### 9. Criar o app no App Store Connect
1. Em App Store Connect, vá em “Meus Apps” > “+” > “Novo App”.
2. Preencha:
   - Nome do app
   - Bundle ID igual ao `expo.ios.bundleIdentifier`
   - Plataforma iOS
   - Idioma padrão
3. Salve o app.

### 10. Enviar o build para a Apple
Opção 1: usar EAS Submit
1. Execute:
   - `eas submit --platform ios`
2. Siga o fluxo para enviar o `.ipa` ao App Store Connect.

Opção 2: usar Transporter (macOS)
1. Baixe o `.ipa` gerado pelo EAS.
2. Abra o app Transporter no Mac.
3. Envie o arquivo para App Store Connect.

### 11. Configurar metadados e screenshots
1. Em App Store Connect, abra o app.
2. Preencha:
   - descrição
   - texto promocional
   - keywords
   - suporte e privacidade
   - screenshots para iPhone
3. Complete as informações de classificação etária e privacidade.

### 12. Liberar para TestFlight ou revisão
1. Se desejar testar primeiro, adicione o build ao TestFlight interno ou externo.
2. Para publicar, envie o app para revisão: “Submit for Review”.

### 13. Aguardar aprovação
1. A Apple fará a análise do app.
2. Quando aprovado, você poderá publicar na App Store.
3. Se houver rejeição, corrija os problemas e reenvie.

---

## Observações importantes
- O Expo Go é usado para testes durante o desenvolvimento, mas para publicação você precisa de um build nativo `.ipa` gerado pelo EAS.
- Seu fluxo principal, com o app já pronto, é:
  1. configurar Apple ID + Developer
  2. preparar `app.json`
  3. executar `eas build`
  4. enviar para App Store Connect
  5. publicar ou usar TestFlight.
