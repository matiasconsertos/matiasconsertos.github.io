**Documento de Contexto: Projeto "Matias Consertos" - Revitalização e Marketing Digital**

**1. Visão Geral do Projeto:**

O objetivo deste projeto é revitalizar a empresa de serviços autônomos "Matias Consertos", localizada em Luziânia-GO, que enfrenta perda de clientes para novos técnicos. O foco é melhorar a presença online, otimizar a captação de leads e estruturar campanhas de marketing digital eficazes. Matias é experiente e já foi referência na cidade.

**2. Serviços Oferecidos:**

*   Manutenção corretiva e preventiva em:
    *   Máquinas de lavar roupas
    *   Máquinas lava e seca
    *   Geladeiras

**3. Estado Atual e Desafios (Resumo da Análise Inicial):**

*   **Forças:** Reputação passada, experiência técnica de Matias, serviços essenciais.
*   **Fraquezas:** Perda de clientes, possível falta de atualização em marketing digital e gestão, estrutura autônoma.
*   **Oportunidades:** Forte potencial com marketing digital (Google Ads, Redes Sociais), foco em manutenção preventiva, parcerias.
*   **Ameaças:** Novos concorrentes com melhor presença digital, mudanças tecnológicas nos aparelhos.
*   **Diagnóstico Principal:** Perda de clientes provavelmente devido à concorrência mais adaptada digitalmente e possível estagnação nas práticas de marketing/gestão de Matias.

**4. Ativos Digitais Desenvolvidos/Planejados:**

*   **Website/Landing Pages:**
    *   Hospedagem: GitHub Pages.
    *   Domínio Personalizado: `matiasconsertos.com.br`.
    *   **Landing Page V1 (Máquina de Lavar):**
        *   Localização: `matiasconsertos.com.br/maquina-de-lavar-v1/`
        *   Foco: Converter clientes para contato via WhatsApp para agendar serviço de conserto de máquina de lavar.
        *   Design: Mobile-first, tema claro e escuro (via `prefers-color-scheme`), logo com fundo branco no header, animações com AOS.js, slider de depoimentos reais com Swiper.js.
        *   Rastreamento: Cliques nos botões de WhatsApp e ligação são rastreados como conversões no Google Ads via Google Tag Manager (GTM).
    *   **Landing Page V2 (Máquina de Lavar - Teste A/B):**
        *   Localização: `matiasconsertos.com.br/maquina-de-lavar-v2/`
        *   Objetivo: Testar copywriting e pequenas variações visuais (ex: posição e estilo da garantia) contra a V1.
        *   Estrutura e funcionalidades (AOS, Swiper, Dark Mode, GTM) similares à V1.
    *   **Landing Page Geral (Campanha Smart/PMax - Todos os Serviços):**
        *   Localização: `matiasconsertos.com.br/conserto-geral/` (sugestão)
        *   Foco: Capturar leads através de um formulário detalhado.
        *   Formulário: Campos (nome, email, whatsapp, endereço, marca, modelo, descrição do problema).
        *   Backend do Formulário: Google Apps Script, salvando dados em uma Planilha Google. CORS tratado via `doOptions` e `HtmlService` com `setXFrameOptionsMode(ALLOWALL)` no `doPost`. JavaScript no cliente faz o `fetch` e redireciona para página de obrigado.
        *   Botão Flutuante: Botão de WhatsApp fixo para contato direto opcional.
        *   Validação: Validação de email e telefone no lado do cliente via JavaScript.
    *   **Página de Obrigado (para Formulário):**
        *   Localização: `matiasconsertos.com.br/obrigado-contato/` (sugestão)
        *   Objetivo: Confirmar o envio do formulário e permitir o rastreamento de conversão de "Envio de Formulário" no Google Ads via GTM (visualização de página).

**5. Google Tag Manager (GTM) - ID: `GTM-WZQRMCWM` (Exemplo)**

*   **Rastreamento Configurado:**
    *   Cliques em links `wa.me` (WhatsApp) como conversão.
        *   Gatilho: "Cliques - Todos os elementos" com condição `Click URL contém wa.me`.
        *   Tag: "Google Ads - Conversão Clique WhatsApp".
    *   Cliques em links `tel:` (Ligação) como conversão.
        *   Gatilho: "Cliques - Todos os elementos" com condição `Click URL começa com tel:`.
        *   Tag: "Google Ads - Conversão Clique Ligação".
    *   Envio de formulário (via visualização da página `/obrigado-contato/`) como conversão.
        *   Gatilho: "Visualização de página" com condição `Page Path contém /obrigado-contato/`.
        *   Tag: "Google Ads - Conversão Formulário Enviado".
*   **Variáveis Integradas de Clique:** Todas ativadas (`Click Element`, `Click Classes`, `Click ID`, `Click Target`, `Click URL`, `Click Text`).

**6. Google Ads:**

*   **Campanha de Pesquisa (Máquina de Lavar - V1 e V2 para Teste A/B):**
    *   Grupo de Anúncios 1 (V1): Anúncios direcionando para `/maquina-de-lavar-v1/`.
        *   Títulos (Exemplos): "Conserto Máq. Lavar Rápido", "Técnico Máq. Lavar Luziânia".
        *   Descrições (Exemplos): "Máquina parada em Luziânia? Matias Consertos resolve rápido! Orçamento fácil via WhatsApp."
    *   Grupo de Anúncios 2 (V2): Anúncios direcionando para `/maquina-de-lavar-v2/`.
    *   Palavras-chave: Foco em termos de "conserto", "manutenção", "técnico", "reparo" para máquinas de lavar, com correspondência de frase. Lista de negativas extensa para filtrar buscas de compra, peças, DIY, etc.
    *   Conversões Primárias: Cliques no WhatsApp e Ligações.
*   **Campanha Smart/PMax (Todos os Serviços - Landing Page Geral):**
    *   Anúncios direcionando para `/conserto-geral/`.
    *   Conversão Primária: Envios de formulário (rastreados pela página de obrigado).
    *   Conversões Secundárias: Cliques no botão flutuante de WhatsApp e ligações (se houver).
*   **ID de Conversão Google Ads (Exemplo):** `AW-16829680127` (Substituir pelo ID real).
*   **Rótulos de Conversão:** Específicos para cada ação (clique whats, clique ligação, formulário).

**7. Scripts e Tecnologias Utilizadas nas Landing Pages:**

*   HTML5, CSS3 (com variáveis CSS para tema claro/escuro).
*   JavaScript (para validação de formulário, envio AJAX para Apps Script, inicialização de bibliotecas).
*   Font Awesome (para ícones).
*   Swiper.js (para slider de depoimentos).
*   AOS.js (Animate On Scroll - para animações de rolagem).
*   Google Tag Manager (para gerenciamento de tags e rastreamento).
*   Google Apps Script (para backend do formulário de contato geral).

**8. Próximos Passos / Áreas para Desenvolvimento Futuro (Sugestões):**

*   Criação de landing pages específicas para "Lava e Seca" e "Geladeira", seguindo o modelo das de "Máquina de Lavar".
*   Desenvolvimento de conteúdo para redes sociais.
*   Otimização SEO básica para as landing pages.
*   Configuração do Google Analytics 4 via GTM para análise de tráfego detalhada.
*   Monitoramento contínuo e otimização das campanhas Google Ads.