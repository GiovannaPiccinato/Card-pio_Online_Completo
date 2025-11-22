# 🚀 Deploy do Frontend no App Service - Método Simples (Portal Azure)

## ✅ Método Mais Simples - Sem Instalar Nada!

Este método usa apenas o Portal Azure - não precisa instalar Azure CLI ou VS Code.

---

## Passo 1: Preparar Arquivo ZIP

1. **Navegar até a pasta do projeto**:
   - Abra o Windows Explorer
   - Vá até: `C:\Users\gabri\Card-pio_Online_Completo`

2. **Selecionar arquivos e pastas**:
   - Selecione os seguintes itens:
     - `index.html`
     - Pasta `CSS`
     - Pasta `JS`
     - Pasta `img`
     - Pasta `fonts`
   
   ⚠️ **NÃO selecione**: arquivos `.md`, `.zip`, ou outras pastas desnecessárias

3. **Criar ZIP**:
   - Clique com botão direito nos arquivos selecionados
   - Escolha: **"Enviar para"** > **"Pasta compactada (zip)"**
   - Renomeie para: `deploy.zip`
   - ⚠️ Certifique-se de que o ZIP está na pasta do projeto

---

## Passo 2: Acessar Kudu (Console do App Service)

1. **No Portal Azure**:
   - Vá até o App Service criado: `app-ecommerce-api-[seu-nome]`
   - No menu lateral, procure por **"Advanced Tools"** (Ferramentas Avançadas)
   - Clique em **"Go"** (ou "Ir")
   - Isso abrirá o **Kudu** em uma nova aba

2. **Acessar Debug Console**:
   - No Kudu, clique em **"Debug console"** no topo
   - Escolha **"CMD"** (não PowerShell)
   - Você verá um explorador de arquivos

---

## Passo 3: Navegar até a Pasta wwwroot

1. **No explorador de arquivos do Kudu**:
   - Clique na pasta **"site"**
   - Depois clique na pasta **"wwwroot"**
   - Esta é a pasta onde os arquivos do site ficam

2. **Limpar pasta (opcional)**:
   - Se houver arquivos antigos, você pode deletá-los
   - Ou apenas substitua com os novos arquivos

---

## Passo 4: Fazer Upload do ZIP

1. **Arrastar e Soltar**:
   - No Windows Explorer, localize o arquivo `deploy.zip`
   - **Arraste e solte** o arquivo ZIP na pasta `wwwroot` do Kudu
   - Aguarde o upload completar

2. **Ou usar o botão Upload**:
   - No Kudu, clique no ícone de **"upload"** (seta para cima)
   - Selecione o arquivo `deploy.zip`
   - Aguarde o upload

---

## Passo 5: Extrair o ZIP

1. **No Kudu, no console CMD**:
   - Clique no arquivo `deploy.zip` que você fez upload
   - Você verá opções, incluindo **"Extract"** (Extrair)
   - Clique em **"Extract"**
   - Ou use o comando no console:
     ```
     unzip deploy.zip
     ```

2. **Verificar arquivos**:
   - Após extrair, você deve ver:
     - `index.html`
     - Pasta `CSS`
     - Pasta `JS`
     - Pasta `img`
     - Pasta `fonts`

---

## Passo 6: Configurar Default Document

1. **Voltar ao Portal Azure**:
   - Feche o Kudu
   - Volte para o App Service no portal

2. **Configurar Default Document**:
   - No App Service, vá em **"Configuration"** (Configuração)
   - Clique na aba **"General settings"** (Configurações Gerais)
   - Role até **"Default documents"**
   - Certifique-se de que `index.html` está na lista
   - Se não estiver, clique em **"+ Add"** e adicione `index.html`
   - Clique em **"Save"** (Salvar) no topo
   - Aguarde a aplicação das configurações

---

## Passo 7: Testar o Site

1. **Acessar o site**:
   - No App Service, clique em **"Browse"** (Navegar) no topo
   - Ou acesse diretamente: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`
   - Seu site deve aparecer!

2. **Verificar se está funcionando**:
   - O site deve carregar normalmente
   - Imagens devem aparecer
   - JavaScript deve funcionar
   - Se algo não funcionar, verifique os logs

---

## ✅ Checklist de Deploy

- [ ] Criei arquivo ZIP com os arquivos do projeto
- [ ] Acessei o Kudu do App Service
- [ ] Naveguei até a pasta `site/wwwroot`
- [ ] Fiz upload do arquivo ZIP
- [ ] Extraí o arquivo ZIP
- [ ] Verifiquei que os arquivos estão na pasta wwwroot
- [ ] Configurei Default Document (`index.html`)
- [ ] Salvei as configurações
- [ ] Acessei o site no navegador
- [ ] Verifiquei que o site está funcionando
- [ ] Capturei tela do site funcionando (para PowerPoint)

---

## 🎉 Pronto!

Agora seu frontend está hospedado no App Service!

**URL do site**: `https://app-ecommerce-api-[seu-nome].azurewebsites.net`

---

## 🚨 Problemas Comuns e Soluções

### Site não carrega / Erro 404
- ✅ Verifique se `index.html` está configurado como Default Document
- ✅ Verifique se o `index.html` está na pasta `wwwroot` (não dentro de uma subpasta)
- ✅ Verifique os caminhos dos arquivos no HTML (devem ser relativos: `./css/main.css`)

### Imagens não aparecem
- ✅ Verifique se a pasta `img` foi incluída no ZIP
- ✅ Verifique os caminhos das imagens no HTML
- ✅ Verifique se os arquivos estão na pasta `wwwroot/img`

### CSS/JavaScript não funciona
- ✅ Verifique se as pastas `CSS` e `JS` foram incluídas no ZIP
- ✅ Verifique os caminhos no HTML
- ✅ Abra o Console do navegador (F12) para ver erros

### Arquivos não aparecem no Kudu
- ✅ Certifique-se de que fez upload na pasta correta (`site/wwwroot`)
- ✅ Recarregue a página do Kudu
- ✅ Verifique se o upload foi concluído

---

## 💡 Dica Extra

### Atualizar o Site (quando fizer mudanças)

Sempre que fizer alterações no código:

1. Crie um novo ZIP com os arquivos atualizados
2. Faça upload no Kudu (substitua o ZIP antigo)
3. Extraia novamente
4. O site será atualizado imediatamente!

---

**Próximo passo**: Continue com o PASSO 3.1 - Criar Azure IoT Hub

