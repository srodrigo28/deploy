## Sequência completa de deploy Android usando Expo / EAS

### 1. Configurar a conta Google
1. Crie uma conta Google em `https://accounts.google.com/` se ainda não tiver.
2. Ative a verificação em duas etapas para maior segurança.

### 2. Criar conta no Google Play Console
1. Acesse `https://play.google.com/console`.
2. Faça login com sua conta Google.
3. Cadaste-se no Google Play Console e pague a taxa única de registro (US$ 25).
4. Preencha os dados da conta de desenvolvedor.

### 3. Preparar o projeto Expo
1. Verifique que seu app Expo já roda localmente com `expo start`.
2. Confirme o arquivo de configuração (`app.json` ou `app.config.js`):
   - `expo.name`
   - `expo.slug`
   - `expo.android.package` (por exemplo: `com.seunome.app`)
   - `expo.android.versionCode`
   - `expo.android.versionName`
3. Se ainda não tiver, instale o EAS CLI:
   - `npm install -g eas-cli`
   - ou `yarn global add eas-cli`

### 4. Fazer login no Expo
1. No terminal do projeto:
   - `eas login`
2. Se não tiver conta Expo, crie ou faça login com:
   - `expo register`
   - `expo login`

### 5. Configurar EAS Build no projeto
1. No diretório do projeto, execute:
   - `eas build:configure`
2. Escolha a plataforma `Android` quando solicitado.
3. Confirme o perfil de build desejado (`production`, `preview` ou `development`).

### 6. Configurar credenciais Android no EAS
1. O EAS pode gerenciar chaves automaticamente durante o build.
2. Se quiser revisar ou importar, use:
   - `eas credentials`
3. Permita que o EAS gere ou importe:
   - keystore Android
   - upload key (para Play App Signing)

### 7. Fazer o build Android com EAS
1. Execute:
   - `eas build --platform android --profile production`
2. Aguarde a compilação nos servidores Expo.
3. Ao finalizar, o EAS retornará um link para baixar o `.aab` ou `.apk`.

### 8. Criar o app no Google Play Console
1. No Play Console, clique em “Criar app”.
2. Selecione o nome do app, idioma e tipo de app.
3. Configure os detalhes iniciais como: Loja, política de privacidade e categorias.

### 9. Enviar o build para o Google Play
1. No Play Console, acesse “Release” > “Produção” ou “Teste”.
2. Crie uma nova release.
3. Faça upload do arquivo gerado pelo EAS (`.aab` recomendado).
4. Complete as notas de versão.
5. Salve e revise a release.

### 10. Configurar metadados e gráficos
1. Em “Ficha da loja”, preencha:
   - descrição curta
   - descrição completa
   - screenshots
   - ícone e recursos gráficos
2. Em “Conteúdo do app”, responda ao questionário de classificação e privacidade.
3. Em “Políticas do app”, confirme as informações de conformidade.

### 11. Liberar para teste ou produção
1. Para testar internamente, use a track de teste interno, fechado ou aberto.
2. Para publicar, libere a release na track de produção.

### 12. Aguardar revisão do Google
1. O Google Play analisará o app.
2. Quando aprovado, o app será publicado ou ficará disponível na track de teste.
3. Se houver pendências, corrija e reenvie a release.

---

## Observações importantes
- O Expo Go é para desenvolvimento e testes; para publicar no Google Play você precisa do build nativo (`.aab` ou `.apk`) gerado pelo EAS.
- O fluxo principal para um app já pronto é:
  1. configurar conta Google + Play Console
  2. preparar `app.json`
  3. executar `eas build`
  4. enviar o build ao Google Play
  5. revisar e publicar.
