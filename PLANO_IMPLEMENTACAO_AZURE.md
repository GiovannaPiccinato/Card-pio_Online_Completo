# Plano de Implementação - E-commerce com IoT na Azure

## Contexto do Projeto
Transformação do cardápio online estático em uma plataforma de e-commerce moderna com integração IoT para gestão de estoque em tempo real na Microsoft Azure.

## Requisitos do Projeto Acadêmico

### ✅ Checklist de Requisitos:
- [ ] Migração para Azure com arquitetura multi-camadas
- [ ] Integração IoT: Azure IoT Hub para sensores de estoque
- [ ] Escalabilidade: Azure Functions ou AKS para auto-scaling
- [ ] Segurança: Azure Security Center
- [ ] Governança: Azure Cost Management

### 📋 Documentação Necessária (PowerPoint):
- [ ] Capturas de tela detalhadas de cada etapa
- [ ] Explicações sobre desafios e soluções
- [ ] Proposta de melhorias contínuas
- [ ] Análise de custos estimada

---

## Arquitetura Proposta

### Camadas da Aplicação:
1. **Frontend**: Azure Static Web Apps (site estático migrado)
2. **Backend API**: Azure App Service (API REST)
3. **Banco de Dados**: Azure SQL Database
4. **IoT**: Azure IoT Hub + Azure Stream Analytics
5. **Processamento**: Azure Functions (serverless)
6. **Monitoramento**: Application Insights
7. **Segurança**: Azure Security Center
8. **Custos**: Azure Cost Management

---

## Passos de Implementação (com pontos de captura)

### FASE 1: Preparação e Configuração Inicial
**PASSO 1.1: Criar/Verificar Subscription Azure** ⏸️ **CAPTURA 1**
- Acessar portal.azure.com
- Verificar subscription ativa
- Capturar: Tela do portal Azure com subscription visível

**PASSO 1.2: Criar Resource Group** ⏸️ **CAPTURA 2**
- Criar novo Resource Group
- Nome: `rg-ecommerce-iot-prod`
- Região: Brazil South ou East US
- Capturar: Tela de criação do Resource Group

### FASE 2: Infraestrutura Base
**PASSO 2.1: Criar Azure SQL Database** ⏸️ **CAPTURA 3**
- Criar SQL Server e Database
- Configurar firewall rules
- Capturar: Tela de configuração do SQL Database

**PASSO 2.2: Criar Azure App Service** ⏸️ **CAPTURA 4**
- Criar App Service Plan
- Criar Web App
- Configurar deployment
- Capturar: Tela do App Service criado

**PASSO 2.3: Criar Azure Static Web Apps** ⏸️ **CAPTURA 5**
- Criar Static Web App
- Conectar ao repositório (opcional)
- Capturar: Tela de configuração do Static Web App

### FASE 3: Integração IoT
**PASSO 3.1: Criar Azure IoT Hub** ⏸️ **CAPTURA 6**
- Criar IoT Hub
- Configurar tier (S1 ou S2)
- Capturar: Tela do IoT Hub criado

**PASSO 3.2: Registrar Dispositivo IoT** ⏸️ **CAPTURA 7**
- Criar device identity
- Obter connection string
- Capturar: Tela com device registrado

**PASSO 3.3: Configurar Azure Stream Analytics** ⏸️ **CAPTURA 8**
- Criar Stream Analytics Job
- Configurar input (IoT Hub)
- Configurar output (SQL Database)
- Capturar: Tela de configuração do Stream Analytics

### FASE 4: Escalabilidade
**PASSO 4.1: Criar Azure Functions** ⏸️ **CAPTURA 9**
- Criar Function App
- Criar função para processar eventos IoT
- Configurar triggers
- Capturar: Tela da Function App e código

**PASSO 4.2: Configurar Auto-scaling** ⏸️ **CAPTURA 10**
- Configurar App Service Auto-scale
- Configurar métricas e regras
- Capturar: Tela de configuração de auto-scaling

### FASE 5: Segurança
**PASSO 5.1: Configurar Azure Security Center** ⏸️ **CAPTURA 11**
- Habilitar Security Center
- Configurar políticas de segurança
- Verificar recomendações
- Capturar: Dashboard do Security Center

**PASSO 5.2: Configurar Network Security** ⏸️ **CAPTURA 12**
- Configurar Network Security Groups
- Configurar firewall rules
- Capturar: Tela de configuração de segurança de rede

### FASE 6: Monitoramento e Custos
**PASSO 6.1: Configurar Application Insights** ⏸️ **CAPTURA 13**
- Criar Application Insights
- Conectar ao App Service
- Capturar: Dashboard do Application Insights

**PASSO 6.2: Configurar Azure Cost Management** ⏸️ **CAPTURA 14**
- Acessar Cost Management
- Configurar budgets
- Analisar custos estimados
- Capturar: Dashboard de custos e análise

### FASE 7: Testes e Validação
**PASSO 7.1: Testar Integração IoT** ⏸️ **CAPTURA 15**
- Simular envio de dados do sensor
- Verificar dados no banco
- Capturar: Dados recebidos e dashboard

**PASSO 7.2: Testar Escalabilidade** ⏸️ **CAPTURA 16**
- Simular carga alta
- Verificar auto-scaling
- Capturar: Métricas de performance e scaling

---

## Próximos Passos
Aguardar confirmação para iniciar o PASSO 1.1

