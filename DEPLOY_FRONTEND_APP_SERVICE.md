# 🚀 Deploy do Frontend no App Service (Alternativa ao Static Web Apps)

## Objetivo
Como o Static Web Apps está bloqueado em todas as regiões, vamos fazer deploy do frontend (HTML, CSS, JavaScript) no App Service que já funciona.

## ✅ Pré-requisitos
- ✅ App Service criado (`app-ecommerce-api-[seu-nome]`)
- ✅ Código do frontend local (pasta do projeto)

---

## Método 1: Deploy via Azure CLI (Recomendado) ⭐

### Passo 1: Instalar Azure CLI (se ainda não tiver)

1. **Baixar Azure CLI**:
   - Acesse: https://aka.ms/installazurecliwindows
   - Baixe e instale o instalador
   - Ou use PowerShell:
     ```powershell
     # Via winget (Windows 11)
     winget install -e --id Microsoft.AzureCLI
     ```

2. **Verificar instalação**:
   ```powershell
   az --version
   ```

### Passo 2: Fazer Login no Azure

```powershell
az login
```
- Isso abrirá o navegador para fazer login
- Faça login com sua conta Azure

### Passo 3: Configurar Deployment Local

1. **Navegar até a pasta do projeto**:
   ```powershell
   cd C:\Users\gabri\Card-pio_Online_Completo
   ```

2. **Criar arquivo de configuração** (opcional):
   - Crie um arquivo `.deployment` na raiz do projeto:
   ```
   [config]
   SCM_DO_BUILD_DURING_DEPLOYMENT=true
   ```

### Passo 4: Fazer Deploy

```powershell
# Fazer deploy de todos os arquivos
az webapp deployment source config-zip `
  --resource-group rg-ecommerce-iot-prod `
  --name app-ecommerce-api-[seu-nome] `
  --src deploy.zip
```

**Mas primeiro, você precisa criar um ZIP:**

```powershell
# Criar ZIP do projeto (excluindo node_modules se houver)
Compress-Archive -Path index.html, CSS, JS, img, fonts -DestinationPath deploy.zip -Force
```

**Ou use este comando completo:**

```powershell
# Navegar até a pasta
cd C:\Users\gabri\Card-pio_Online_Completo

# Criar ZIP
Compress-Archive -Path index.html, CSS, JS, img, fonts -DestinationPath deploy.zip -Force

# Fazer deploy
az webapp deployment source config-zip `
  --resource-group rg-ecommerce-iot-prod `
  --name app-ecommerce-api-[seu-nome] `
  --src deploy.zip
```

### Passo 5: Verificar Deploy

1. **Acessar o site**:
   - Vá para: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`
   - Você deve ver seu site funcionando!

2. **Verificar no portal**:
   - No portal Azure, vá até o App Service
   - Vá em "Deployment Center" > "Logs"
   - Veja o status do deployment

---

## Método 2: Deploy via Portal Azure (Mais Simples)

### Passo 1: Preparar ZIP

1. **Criar arquivo ZIP** com os arquivos do frontend:
   - Selecione: `index.html`, pasta `CSS`, pasta `JS`, pasta `img`, pasta `fonts`
   - Clique com botão direito > "Enviar para" > "Pasta compactada (zip)"
   - Renomeie para `deploy.zip`

### Passo 2: Fazer Deploy no Portal

1. **No Portal Azure**:
   - Vá até o App Service (`app-ecommerce-api-[seu-nome]`)
   - No menu lateral, vá em **"Deployment Center"**
   - Ou vá em **"Advanced Tools"** > **"Go"** (Kudu)

2. **Opção A: Via Deployment Center**:
   - Clique em **"Settings"** (Configurações)
   - Em **"Source"**, selecione **"Local Git"** ou **"External Git"**
   - Ou use **"OneDrive"** / **"Dropbox"** se preferir

3. **Opção B: Via Kudu (Mais Direto)**:
   - Vá em **"Advanced Tools"** > **"Go"** (abre Kudu)
   - Clique em **"Debug console"** > **"CMD"**
   - Navegue até `site/wwwroot`
   - Arraste e solte o arquivo ZIP
   - Extraia o ZIP usando:
     ```
     unzip deploy.zip
     ```

### Passo 3: Verificar

- Acesse: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`
- Seu site deve estar funcionando!

---

## Método 3: Deploy via VS Code (Mais Visual)

### Passo 1: Instalar Extensão

1. Abra VS Code
2. Instale a extensão: **"Azure App Service"**
3. Faça login no Azure (ícone do Azure na barra lateral)

### Passo 2: Fazer Deploy

1. **Abrir pasta do projeto** no VS Code
2. **Clicar no ícone do Azure** na barra lateral
3. **Expandir "App Service"**
4. **Clicar com botão direito** no App Service (`app-ecommerce-api-[seu-nome]`)
5. **Selecionar "Deploy to Web App"**
6. **Selecionar a pasta** do projeto
7. **Aguardar** o deploy completar

### Passo 3: Verificar

- O VS Code mostrará uma notificação quando o deploy terminar
- Acesse: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`

---

## ⚙️ Configurações Importantes

### 1. Configurar Default Document

O App Service precisa saber qual arquivo servir como página inicial:

1. No App Service, vá em **"Configuration"**
2. Vá na aba **"General settings"**
3. Em **"Default documents"**, certifique-se de que `index.html` está na lista
4. Se não estiver, adicione: `index.html`
5. Clique em **"Save"**

### 2. Configurar CORS (Se Necessário)

Se o frontend precisar chamar APIs externas:

1. No App Service, vá em **"Configuration"**
2. Vá na aba **"CORS"**
3. Adicione os domínios permitidos (ou deixe `*` para desenvolvimento)
4. Clique em **"Save"**

### 3. Verificar Caminhos dos Arquivos

Certifique-se de que os caminhos no `index.html` estão corretos:
- `./css/main.css` (relativo)
- `./js/app.js` (relativo)
- `./img/logo.png` (relativo)

---

## 🎯 Estrutura Final no App Service

Após o deploy, a estrutura no App Service será:

```
site/wwwroot/
  ├── index.html
  ├── CSS/
  │   ├── main.css
  │   ├── bootstrap.min.css
  │   └── ...
  ├── JS/
  │   ├── app.js
  │   ├── dados.js
  │   └── ...
  ├── img/
  │   ├── logo.png
  │   └── ...
  └── fonts/
      └── ...
```

---

## ✅ Checklist de Deploy

- [ ] Escolhi o método de deploy (CLI, Portal, ou VS Code)
- [ ] Criei arquivo ZIP (se necessário)
- [ ] Fiz login no Azure
- [ ] Fiz deploy dos arquivos
- [ ] Configurei Default Document (`index.html`)
- [ ] Acessei o site: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`
- [ ] Verifiquei que o site está funcionando
- [ ] Capturei tela do site funcionando (para PowerPoint)

---

## 🎉 Pronto!

Agora seu frontend está hospedado no App Service e acessível publicamente!

**URL do site**: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`

**Próximo passo**: Continue com o PASSO 3.1 - Criar Azure IoT Hub

---

## 💡 Dicas

### Atualizar o Site
- Sempre que fizer alterações, refaça o deploy usando o mesmo método
- O site será atualizado imediatamente após o deploy

### Ver Logs
- No App Service, vá em "Log stream" para ver logs em tempo real
- Ou vá em "Logs" para baixar logs

### Custom Domain
- No App Service, vá em "Custom domains"
- Você pode adicionar seu próprio domínio
- O SSL será configurado automaticamente

---

## 🚨 Problemas Comuns

### Site não carrega
- Verifique se `index.html` está configurado como Default Document
- Verifique os caminhos dos arquivos (CSS, JS, imagens)
- Verifique os logs no App Service

### Arquivos não aparecem
- Certifique-se de que todos os arquivos foram incluídos no ZIP
- Verifique a estrutura de pastas no Kudu

### Erro 404
- Verifique se o `index.html` está na raiz do `wwwroot`
- Verifique as configurações de Default Document

