# 🎯 PASSO 2.3: Criar Azure Static Web Apps (CAPTURA 5)

## Objetivo
Criar um Azure Static Web App para hospedar o frontend estático (HTML, CSS, JavaScript) do e-commerce. O Static Web Apps é ideal para sites estáticos e oferece hospedagem gratuita com CDN global.

## 📋 Pré-requisitos
- ✅ Resource Group criado (`rg-ecommerce-iot-prod`)
- ✅ Subscription Azure ativa
- ⚠️ **Opcional**: Conta GitHub (para deployment automático)
  - Se não tiver GitHub, pode fazer deployment manual depois

---

## Instruções Detalhadas:

### 1. Acessar Static Web Apps

1. **No Portal Azure**:
   - Use a barra de pesquisa no topo
   - Digite "Static Web Apps" e clique no resultado
   - Ou vá em "Create a resource" > "Web" > "Static Web App"

2. **Iniciar Criação**:
   - Clique no botão "+ Create" (Criar)
   - Você verá um formulário com várias abas

---

### 2. Aba "Basics" (Básico)

#### 2.1. Informações do Projeto
- **Subscription**: Selecione sua subscription
- **Resource group**: Selecione `rg-ecommerce-iot-prod` (o que criamos anteriormente)
- **Name**: Digite `swa-ecommerce-[seu-nome]`
  - Exemplo: `swa-ecommerce-gabriel`
  - ⚠️ O nome deve ser único globalmente (use seu nome ou iniciais)
  - ⚠️ Apenas letras minúsculas, números e hífens são permitidos
  - Este será o URL: `https://swa-ecommerce-[seu-nome].azurestaticapps.net`

#### 2.2. Plan Type (Tipo de Plano)
- **Plan type**: Selecione **"Free"** ⭐ (GRATUITO - Recomendado para testes)
  - ✅ 100 GB de bandwidth por mês
  - ✅ Storage ilimitado
  - ✅ Custom domains (domínios personalizados)
  - ✅ SSL automático
  - ✅ CDN global
  - ⚠️ Limitação: Apenas para sites estáticos (HTML, CSS, JS)

#### 2.3. Region (Região)
- **Region**: ⚠️ **IMPORTANTE**: Use a MESMA região do Resource Group
  - Se o Resource Group está em "East US", selecione "East US"
  - Se está em "Central US", selecione "Central US"
  - Se está em outra região, use a mesma
  - **NÃO use "West US 2"** se já teve problemas antes

⚠️ **PROBLEMA COMUM**: Se você receber erro "RequestDisallowedByAzure" em TODAS as regiões, veja a seção "🚨 Solução: Erro de Região Bloqueada" abaixo.

#### 2.4. Deployment Details (Detalhes de Deployment)

**Você tem 3 opções:**

---

##### **Opção A: GitHub (Recomendado - Deployment Automático)** ⭐

Se você tem ou quer criar uma conta GitHub:

1. **Source**: Selecione **"GitHub"**
2. **Sign in with GitHub**: Clique em "Sign in with GitHub"
   - Você será redirecionado para autorizar o Azure
   - Faça login no GitHub se necessário
   - Autorize o Azure a acessar seus repositórios
3. **Organization**: Selecione sua organização GitHub (geralmente seu username)
4. **Repository**: 
   - Se já tem um repositório com o código, selecione-o
   - Ou selecione "Create new repository" para criar um novo
5. **Branch**: Selecione **"main"** ou **"master"** (depende do seu repositório)
6. **Build Presets**: Selecione **"Custom"**
   - **App location**: `/` (raiz do projeto)
   - **Api location**: Deixe vazio (não temos API no frontend)
   - **Output location**: `/` (raiz do projeto)

**Vantagens:**
- ✅ Deployment automático a cada push no GitHub
- ✅ Preview environments para pull requests
- ✅ Histórico de deployments

---

##### **Opção B: Azure DevOps (Alternativa)**

Se você usa Azure DevOps:

1. **Source**: Selecione **"Azure DevOps"**
2. **Organization**: Selecione sua organização Azure DevOps
3. **Project**: Selecione seu projeto
4. **Repository**: Selecione o repositório
5. **Branch**: Selecione a branch (ex: "main")
6. **Build Presets**: Selecione **"Custom"**
   - **App location**: `/`
   - **Api location**: Deixe vazio
   - **Output location**: `/`

---

##### **Opção C: Other (Manual - Sem GitHub)** ⚠️

Se você **NÃO tem GitHub** ou quer fazer deployment manual depois:

1. **Source**: Selecione **"Other"**
2. **Build Presets**: Selecione **"Custom"**
   - **App location**: `/`
   - **Api location**: Deixe vazio
   - **Output location**: `/`

**Nota**: Com "Other", você precisará fazer deployment manual depois usando:
- Azure CLI
- VS Code Extension
- GitHub Actions (criando manualmente)

**Recomendação**: Se possível, use a **Opção A (GitHub)** para facilitar o deployment.

---

### 3. Aba "Review + create" (Revisar e Criar)

1. **Revisar Configurações**:
   - Clique na aba "Review + create"
   - Revise todas as informações:
     - Nome do Static Web App
     - Resource Group
     - Região
     - Plan Type (Free)
     - Source (GitHub/Other)

2. **Validar**:
   - Aguarde a validação (pode levar alguns segundos)
   - Se houver erros, corrija e tente novamente

3. **Criar**:
   - Clique em "Create" (Criar)
   - Aguarde a criação (pode levar 1-3 minutos)

---

### 4. Aguardar Criação

1. **Notificações**:
   - Você verá notificações no topo direito do portal
   - Aguarde até aparecer "Your deployment is complete"

2. **Ir para o Recurso**:
   - Clique em "Go to resource" quando aparecer
   - Ou vá em "Static Web Apps" > clique no Static Web App criado

3. **Se usou GitHub**:
   - Uma GitHub Action será criada automaticamente
   - O primeiro deployment pode levar alguns minutos
   - Você verá o status na aba "Deployment" do Static Web App

---

## 📸 CAPTURA DE TELA 5 - O QUE CAPTURAR:

### Opção A: Captura Durante a Criação (Recomendado)

**Tela 5A: Formulário de Criação do Static Web App**
- Capture a tela do formulário mostrando:
  - Nome do Static Web App preenchido (`swa-ecommerce-[seu-nome]`)
  - Resource Group selecionado (`rg-ecommerce-iot-prod`)
  - Plan Type selecionado (Free)
  - Região selecionada
  - Source selecionado (GitHub/Other)
  - Build Presets configurado (Custom com App location `/`)
  - Botão "Review + create" ou "Create" visível

### Opção B: Captura Após Criação

**Tela 5B: Static Web App Criado com Sucesso**
- Capture a tela mostrando:
  - A página do Static Web App criado
  - Nome do Static Web App visível no topo (`swa-ecommerce-[seu-nome]`)
  - URL do Static Web App visível (ex: `https://swa-ecommerce-[seu-nome].azurestaticapps.net`)
  - Status "Running" ou "Ready"
  - Resource Group (`rg-ecommerce-iot-prod`)
  - Região
  - Plan Type (Free)
  - Se usou GitHub, mostre a aba "Deployment" com o status do deployment

**Dica para captura:**
- Certifique-se de que o nome completo do Static Web App está visível
- Mostre o URL completo (será usado para acessar o site)
- Mostre o status "Running" ou deployment em andamento
- Se possível, mostre também o Resource Group e região

---

## ⚠️ IMPORTANTE:

### Custo
- **Free Plan**: **GRATUITO** ✅
  - 100 GB de bandwidth por mês
  - Storage ilimitado
  - Custom domains
  - SSL automático
  - CDN global
  - Sem custos adicionais

### Informações para Anotar
- **Static Web App Name**: `swa-ecommerce-[seu-nome]`
- **URL**: `https://swa-ecommerce-[seu-nome].azurestaticapps.net`
- **Resource Group**: `rg-ecommerce-iot-prod`
- **Plan Type**: Free
- **Source**: GitHub/Other (o que você escolheu)

### Limitações do Free Plan
- ✅ Perfeito para sites estáticos (HTML, CSS, JavaScript)
- ✅ Suporta até 100 GB de bandwidth por mês
- ⚠️ Não suporta server-side rendering (SSR)
- ⚠️ Não suporta APIs serverless (use Azure Functions para isso)

---

## 🔧 Próximos Passos Após Criação

### 1. Se Você Usou GitHub (Opção A)

1. **Verificar GitHub Action**:
   - Vá até seu repositório no GitHub
   - Clique na aba "Actions"
   - Você verá um workflow do Azure Static Web Apps
   - Aguarde o primeiro deployment completar

2. **Acessar o Site**:
   - No portal Azure, vá até o Static Web App
   - Clique em "Browse" (Navegar) no topo
   - Ou acesse diretamente: `https://swa-ecommerce-[seu-nome].azurestaticapps.net`
   - Você verá uma página padrão do Azure (se ainda não fez deploy do código)

3. **Fazer Deploy do Código**:
   - Faça push do seu código para o repositório GitHub
   - O deployment será automático via GitHub Actions
   - Aguarde alguns minutos e atualize o site

---

### 2. Se Você Usou "Other" (Opção C - Sem GitHub)

Você precisará fazer deployment manual. Opções:

#### Opção 1: Usar Azure CLI (Recomendado)

1. **Instalar Azure CLI** (se ainda não tiver):
   ```powershell
   # Baixe em: https://aka.ms/installazurecliwindows
   ```

2. **Fazer Login**:
   ```powershell
   az login
   ```

3. **Fazer Deploy**:
   ```powershell
   # Navegue até a pasta do seu projeto
   cd C:\Users\gabri\Card-pio_Online_Completo
   
   # Faça o deploy
   az staticwebapp deploy --name swa-ecommerce-[seu-nome] --resource-group rg-ecommerce-iot-prod --source-location .
   ```

#### Opção 2: Usar VS Code Extension

1. Instale a extensão "Azure Static Web Apps" no VS Code
2. Clique com botão direito na pasta do projeto
3. Selecione "Deploy to Static Web App"
4. Escolha o Static Web App criado

#### Opção 3: Criar GitHub Actions Manualmente

1. Crie um repositório GitHub (se ainda não tiver)
2. Faça push do código
3. No portal Azure, vá até o Static Web App
4. Vá em "Deployment" > "Manage deployment token"
5. Copie o token
6. Configure GitHub Actions manualmente

---

### 3. Configurar CORS (Se Necessário)

Se o frontend precisar chamar a API do App Service:

1. No Static Web App, vá em "Configuration"
2. Adicione uma configuração de CORS se necessário
3. Ou configure no App Service (backend) para aceitar requisições do Static Web App

---

## 🎯 Resumo das Configurações

| Configuração | Valor Recomendado |
|-------------|-------------------|
| **Nome** | `swa-ecommerce-[seu-nome]` |
| **Resource Group** | `rg-ecommerce-iot-prod` |
| **Plan Type** | **Free** (Gratuito) |
| **Region** | Mesma do Resource Group |
| **Source** | **GitHub** ⭐ (Recomendado) ou **Other** |
| **Build Presets** | Custom |
| **App location** | `/` |
| **Output location** | `/` |

---

## ✅ Checklist de Criação

- [ ] Acessei "Static Web Apps" no portal Azure
- [ ] Cliquei em "+ Create"
- [ ] Preenchi Subscription e Resource Group
- [ ] Defini nome único para o Static Web App
- [ ] Selecionei "Free" em Plan Type
- [ ] Selecionei a mesma região do Resource Group
- [ ] Escolhi Source (GitHub ou Other)
- [ ] Configurei Build Presets (Custom)
- [ ] Revisei todas as configurações
- [ ] Cliquei em "Create"
- [ ] Aguardei a criação completar
- [ ] Capturei a tela (Tela 5)
- [ ] Anotei o nome e URL do Static Web App
- [ ] Se usou GitHub, verifiquei o GitHub Action
- [ ] Se usou Other, preparei para fazer deployment manual

---

## 🚨 Solução: Erro de Região Bloqueada para Static Web Apps

### ❌ Erro Recebido
```
RequestDisallowedByAzure
Resource 'swa-ecommerce-quarta' was disallowed by Azure
This policy maintains a set of best available regions...
```

### ⚠️ Situação
Se você tentou **várias regiões** (East US, Central US, North Europe, West Europe, etc.) e **TODAS** foram bloqueadas, isso indica que sua subscription pode ter restrições específicas para Static Web Apps.

### ✅ Soluções (Escolha uma)

---

#### **Solução 1: Usar App Service para Frontend (MAIS RÁPIDO)** ⭐ **RECOMENDADO**

Como você já criou o App Service (passo 2.2), pode usar ele para hospedar o frontend também:

**Vantagens:**
- ✅ Não precisa criar Static Web Apps
- ✅ Usa o recurso que já funciona
- ✅ Mesma região do Resource Group
- ✅ Funciona perfeitamente para sites estáticos

**Como fazer:**
1. No App Service criado, vá em "Deployment Center"
2. Faça deploy do seu código HTML/CSS/JS
3. O frontend ficará acessível em: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`

**Para captura de tela:**
- Capture o App Service com o frontend deployado
- Isso demonstra que o frontend está na Azure
- Funciona para o projeto acadêmico

---

#### **Solução 2: Pular Static Web Apps (OPCIONAL)**

Se o foco do projeto é backend/IoT, você pode:

1. **Pular este passo completamente**
2. **Manter o frontend local** para testes
3. **Focar nos outros passos** (IoT Hub, Functions, etc.)
4. **Documentar no PowerPoint** que o frontend pode ser migrado depois

**Justificativa para o projeto:**
- "Frontend mantido localmente para desenvolvimento"
- "Foco na arquitetura backend e IoT"
- "Static Web Apps será implementado após resolução de restrições de região"

---

#### **Solução 3: Tentar Criar Sem Especificar Região**

Algumas vezes, deixar o Azure escolher a região pode funcionar:

1. No formulário de criação, **deixe o campo "Region" vazio** (se possível)
2. Ou tente selecionar a **primeira região da lista** (geralmente a mais disponível)
3. O Azure pode escolher automaticamente uma região permitida

---

#### **Solução 4: Contatar Suporte Azure**

Se nenhuma das soluções acima funcionar:

1. No portal Azure, vá em "Help + support"
2. Clique em "+ New support request"
3. Explique que precisa criar Static Web Apps mas todas as regiões estão bloqueadas
4. Mencione que é para projeto acadêmico
5. Solicite acesso a regiões específicas

---

### 🎯 Recomendação Final

**Para seu projeto acadêmico, recomendo a Solução 1:**
- Use o App Service que já funciona
- Deploy do frontend no App Service
- Capture a tela do App Service com frontend
- Documente que o frontend está hospedado na Azure

**Isso resolve o problema e permite continuar com os próximos passos!**

---

## ✅ Após capturar a tela, confirme aqui para continuarmos com o próximo passo!

**Próximo passo será:** PASSO 3.1 - Criar Azure IoT Hub

---

## 📝 Nota sobre Alternativas

Se você não conseguir criar o Static Web Apps devido a restrições de região:

### Alternativa: Usar App Service para Frontend

O App Service que você criou no passo 2.2 pode hospedar tanto o backend (API) quanto o frontend (HTML/CSS/JS):

1. **Estrutura de pastas no App Service:**
   ```
   /api          → Backend API (Node.js/Express)
   /public       → Frontend (HTML, CSS, JS)
   ```

2. **Ou criar dois App Services:**
   - `app-ecommerce-api-[seu-nome]` → Backend
   - `app-ecommerce-web-[seu-nome]` → Frontend

3. **Ou usar o mesmo App Service:**
   - Frontend em `/` (raiz)
   - API em `/api`

**Isso funciona perfeitamente e resolve o problema de região!**

---

## 💡 Dicas Adicionais

### Verificar Status do Deployment
- No portal Azure, vá em "Static Web Apps" > seu app
- Clique na aba "Deployment"
- Veja o status dos deployments
- Se houver erro, clique no deployment para ver detalhes

### Custom Domain (Opcional)
- No Static Web App, vá em "Custom domains"
- Você pode adicionar seu próprio domínio (ex: `www.seudominio.com`)
- O SSL será configurado automaticamente

### Configurar Variáveis de Ambiente
- No Static Web App, vá em "Configuration"
- Adicione variáveis de ambiente se necessário
- Útil para configurar URLs da API, por exemplo

### Monitoramento
- O Static Web Apps já inclui monitoramento básico
- Você pode ver métricas em "Overview"
- Para monitoramento avançado, integre com Application Insights

---

## 🔗 Arquitetura Final

Após criar o Static Web App, você terá:

```
Frontend (Static Web Apps)
  ↓
  https://swa-ecommerce-[seu-nome].azurestaticapps.net
  ↓ (chama API)
Backend (App Service)
  ↓
  https://app-ecommerce-api-[seu-nome].azurewebsites.net
  ↓ (consulta)
Database (SQL Database)
  ↓
  sqldb-ecommerce-prod
```

**Nota**: O frontend (Static Web Apps) chamará a API do backend (App Service), que por sua vez consultará o SQL Database.

---

**Próximo passo após resolver**: Continue com o PASSO 3.1 do guia principal (Criar Azure IoT Hub)

