# 🎯 PASSO 3.1: Criar Azure IoT Hub (CAPTURA 6)

## Objetivo
Criar um Azure IoT Hub para conectar e gerenciar dispositivos IoT (sensores de estoque) do e-commerce. O IoT Hub permite receber dados de sensores em tempo real e processá-los.

## 📋 Pré-requisitos
- ✅ Resource Group criado (`rg-ecommerce-iot-prod`)
- ✅ Subscription Azure ativa
- ✅ SQL Database criado (para armazenar dados dos sensores depois)

---

## Instruções Detalhadas:

### 1. Acessar IoT Hub

1. **No Portal Azure**:
   - Use a barra de pesquisa no topo
   - Digite "IoT Hub" e clique no resultado
   - Ou vá em "Create a resource" > "Internet of Things" > "IoT Hub"

2. **Iniciar Criação**:
   - Clique no botão "+ Create" (Criar)
   - Você verá um formulário com várias abas

---

### 2. Aba "Basics" (Básico)

#### 2.1. Informações do Projeto
- **Subscription**: Selecione sua subscription
- **Resource group**: Selecione `rg-ecommerce-iot-prod` (o que criamos anteriormente)
- **Region**: ⚠️ **IMPORTANTE**: Use a MESMA região do Resource Group
  - Se o Resource Group está em "East US", selecione "East US"
  - Se está em "Central US", selecione "Central US"
  - Se está em outra região, use a mesma
  - **NÃO use "West US 2"** se já teve problemas antes
- **IoT Hub name**: Digite `iothub-ecommerce-[seu-nome]`
  - Exemplo: `iothub-ecommerce-gabriel`
  - ⚠️ O nome deve ser único globalmente (use seu nome ou iniciais)
  - ⚠️ Apenas letras minúsculas, números e hífens são permitidos

#### 2.2. Pricing and scale tier (Preço e Escala)

⚠️ **IMPORTANTE**: Escolha o tier baseado no seu orçamento:

**Opção A: F1 - Free (GRATUITO)** ⭐ **RECOMENDADO PARA TESTES**
- ✅ **GRATUITO** (até 8.000 mensagens/dia)
- ✅ Ideal para desenvolvimento e testes
- ✅ 500 dispositivos
- ⚠️ Limitação: 8.000 mensagens por dia
- ⚠️ Apenas 1 hub gratuito por subscription

**Opção B: S1 - Standard ($25-50 USD/mês)**
- ✅ 400.000 mensagens por dia
- ✅ Suporte para milhões de dispositivos
- ✅ Ideal para produção
- ⚠️ Custo mensal

**Opção C: S2 - Standard ($250+ USD/mês)**
- ✅ 6 milhões de mensagens por dia
- ✅ Para grandes volumes
- ⚠️ Custo alto

**Recomendação**: Use **F1 - Free** para testes e desenvolvimento.

- **Pricing and scale tier**: Selecione **"F1: Free tier"** ⭐

---

### 3. Aba "Networking" (Rede)

#### 3.1. Connectivity (Conectividade)
- **Public network access**: Selecione **"All networks"** ou **"Selected IP ranges"**
  - Para testes, use **"All networks"**
  - Para produção, use **"Selected IP ranges"** (mais seguro)

#### 3.2. Device-to-cloud partitions (Partições)
- Deixe o padrão (4 partições para F1)
- Isso define quantas partições usar para mensagens

---

### 4. Aba "Management" (Gerenciamento)

#### 4.1. Device-to-cloud settings
- **Device-to-cloud partitions**: Deixe o padrão (4 para F1)
- **Event Hub compatible name**: Será gerado automaticamente
- **Event Hub compatible endpoint**: Será gerado automaticamente

#### 4.2. Cloud-to-device settings
- **Max delivery count**: Deixe o padrão (10)
- **Default TTL**: Deixe o padrão (1 hora)

#### 4.3. Features
- **Device-to-cloud telemetry**: ✅ Habilitado (padrão)
- **Cloud-to-device messaging**: ✅ Habilitado (padrão)
- **Device identity registry**: ✅ Habilitado (padrão)

---

### 5. Aba "Tags" (Opcional)

- Pode deixar vazio ou adicionar tags para organização
- Exemplo: `Environment: Production`, `Project: E-commerce IoT`

---

### 6. Aba "Review + create" (Revisar e Criar)

1. **Revisar Configurações**:
   - Clique na aba "Review + create"
   - Revise todas as informações:
     - Nome do IoT Hub
     - Resource Group
     - Região
     - Pricing tier (F1 Free)
     - Configurações de rede

2. **Validar**:
   - Aguarde a validação (pode levar alguns segundos)
   - Se houver erros, corrija e tente novamente

3. **Criar**:
   - Clique em "Create" (Criar)
   - Aguarde a criação (pode levar 2-5 minutos)

---

### 7. Aguardar Criação

1. **Notificações**:
   - Você verá notificações no topo direito do portal
   - Aguarde até aparecer "Your deployment is complete"

2. **Ir para o Recurso**:
   - Clique em "Go to resource" quando aparecer
   - Ou vá em "IoT Hub" > clique no IoT Hub criado

---

## 📸 CAPTURA DE TELA 6 - O QUE CAPTURAR:

### Opção A: Captura Durante a Criação (Recomendado)

**Tela 6A: Formulário de Criação do IoT Hub**
- Capture a tela do formulário mostrando:
  - Nome do IoT Hub preenchido (`iothub-ecommerce-[seu-nome]`)
  - Resource Group selecionado (`rg-ecommerce-iot-prod`)
  - Região selecionada
  - Pricing tier selecionado (F1 Free)
  - Configurações de rede
  - Botão "Review + create" ou "Create" visível

### Opção B: Captura Após Criação

**Tela 6B: IoT Hub Criado com Sucesso**
- Capture a tela mostrando:
  - A página do IoT Hub criado
  - Nome do IoT Hub visível no topo (`iothub-ecommerce-[seu-nome]`)
  - Status "Active" ou "Running"
  - Resource Group (`rg-ecommerce-iot-prod`)
  - Região
  - Pricing tier (F1 Free)
  - Endpoint do IoT Hub visível
  - Métricas básicas (se disponível)

**Dica para captura:**
- Certifique-se de que o nome completo do IoT Hub está visível
- Mostre o status "Active"
- Se possível, mostre também o Resource Group e região
- Mostre o Pricing tier (F1 Free)

---

## ⚠️ IMPORTANTE:

### Custo
- **F1 Free**: **GRATUITO** ✅
  - 8.000 mensagens por dia
  - 500 dispositivos
  - Ideal para testes e desenvolvimento
  - ⚠️ Apenas 1 hub gratuito por subscription

### Informações para Anotar
- **IoT Hub Name**: `iothub-ecommerce-[seu-nome]`
- **Resource Group**: `rg-ecommerce-iot-prod`
- **Pricing Tier**: F1 Free
- **Connection String**: Você obterá depois (necessário para conectar dispositivos)
- **Endpoint**: Será gerado automaticamente

### Limitações do F1 Free
- ⚠️ 8.000 mensagens por dia (suficiente para testes)
- ⚠️ 500 dispositivos (suficiente para desenvolvimento)
- ⚠️ Apenas 1 hub gratuito por subscription
- ✅ Para produção, considere upgrade para S1

---

## 🔧 Próximos Passos Após Criação

### 1. Obter Connection String

1. **No IoT Hub criado**:
   - Vá em "Shared access policies" no menu lateral
   - Clique em "iothubowner"
   - Copie a **"Connection string - primary key"**
   - ⚠️ **ANOTE** essa connection string (você precisará depois)

### 2. Verificar Endpoints

1. **No IoT Hub**:
   - Vá em "Built-in endpoints"
   - Veja os endpoints disponíveis:
     - **Events**: Para receber mensagens dos dispositivos
     - **Messages/Events**: Endpoint compatível com Event Hub

### 3. Preparar para Registrar Dispositivos

- No próximo passo (3.2), você registrará dispositivos IoT
- Cada dispositivo terá sua própria connection string
- Os dispositivos enviarão dados para o IoT Hub

---

## 🎯 Resumo das Configurações

| Configuração | Valor Recomendado |
|-------------|-------------------|
| **Nome** | `iothub-ecommerce-[seu-nome]` |
| **Resource Group** | `rg-ecommerce-iot-prod` |
| **Region** | Mesma do Resource Group |
| **Pricing Tier** | **F1 Free** ⭐ (Gratuito) |
| **Public network access** | All networks (para testes) |
| **Device-to-cloud partitions** | 4 (padrão para F1) |

---

## ✅ Checklist de Criação

- [ ] Acessei "IoT Hub" no portal Azure
- [ ] Cliquei em "+ Create"
- [ ] Preenchi Subscription e Resource Group
- [ ] Defini nome único para o IoT Hub
- [ ] Selecionei a mesma região do Resource Group
- [ ] Selecionei "F1 Free" em Pricing tier
- [ ] Configurei Public network access
- [ ] Revisei todas as configurações
- [ ] Cliquei em "Create"
- [ ] Aguardei a criação completar
- [ ] Capturei a tela (Tela 6)
- [ ] Anotei o nome do IoT Hub
- [ ] Copiei a Connection String (iothubowner)
- [ ] Anotei a Connection String em local seguro

---

## ✅ Após capturar a tela, confirme aqui para continuarmos com o próximo passo!

**Próximo passo será:** PASSO 3.2 - Registrar Dispositivo IoT

---

## 💡 Dicas Adicionais

### Verificar Status do IoT Hub
- No portal Azure, vá em "IoT Hub"
- Procure pelo seu IoT Hub
- Status deve estar "Active"

### Métricas
- No IoT Hub, vá em "Metrics"
- Veja métricas como:
  - Mensagens enviadas
  - Dispositivos conectados
  - Erros

### Testar Conexão
- Você pode usar o Azure IoT Explorer (ferramenta desktop)
- Ou usar o portal Azure para testar dispositivos

### Connection String
- ⚠️ **MUITO IMPORTANTE**: Guarde a connection string em local seguro
- Você precisará dela para:
  - Conectar dispositivos
  - Configurar Stream Analytics
  - Configurar Azure Functions

---

## 🔗 Arquitetura

Após criar o IoT Hub, você terá:

```
Dispositivos IoT (Sensores)
  ↓ (enviam dados)
IoT Hub
  ↓ (processa)
Stream Analytics / Azure Functions
  ↓ (armazena)
SQL Database
```

**Nota**: Os sensores de estoque enviarão dados para o IoT Hub, que serão processados e armazenados no SQL Database.

---

**Próximo passo após resolver**: Continue com o PASSO 3.2 do guia principal (Registrar Dispositivo IoT)

