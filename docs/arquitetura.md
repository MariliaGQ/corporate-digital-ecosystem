# 🏗️ Arquitetura e Decisões Técnicas

> Documento focado exclusivamente nas decisões arquiteturais, critérios adotados e trade-offs considerados durante a construção do ecossistema.

## 🎯 Problema de Origem

O ecossistema surgiu a partir de um conjunto de problemas recorrentes no contexto corporativo:

* alto volume de demandas sem controle estruturado
* ausência de governança formal e rastreável
* inexistência de critérios claros de priorização
* baixa visibilidade do trabalho da área de processos
* retrabalho frequente e perda de histórico
* aumento do risco operacional e dificuldades em auditorias

Esses problemas impactavam diretamente a previsibilidade, a transparência e a eficiência da área.

---

## 🔍 Alternativas Avaliadas

Antes da definição da arquitetura final, diferentes abordagens foram analisadas:

### Ferramentas externas de mercado

Foram consideradas soluções prontas, porém descartadas por não atenderem de forma integrada a todas as necessidades do ecossistema. Para cobrir entrada de ideias, priorização, backlog, projetos, tarefas, inventário e documentação automatizada, seria necessário contratar múltiplas ferramentas, elevando significativamente o custo e a complexidade de integração.

### Desenvolvimento de sistema do zero

A construção de uma solução customizada em código puro foi descartada devido:

* à complexidade de desenvolvimento
* ao tempo elevado para entrega
* à equipe enxuta disponível
* aos processos internos de homologação, que aumentariam custo e prazo

Essa abordagem não seria compatível com a urgência do problema.

### Ferramenta interna de workflow

A ferramenta interna existente permitiria apenas a entrada de demandas em fila, sem suporte a priorização estruturada, backlog executivo, gestão de projetos, inventário ou documentação automatizada.

### Jira

Apesar de ser uma ferramenta robusta, não atendia de forma integrada todas as funcionalidades necessárias ao ecossistema e exigiria adaptações e processos paralelos.

---

## ✅ Critérios de Decisão

Os principais critérios considerados na tomada de decisão foram:

* agilidade de desenvolvimento
* custo reduzido
* facilidade de manutenção
* modularidade
* adaptação ao contexto corporativo existente

---

## 🧱 Decisão Arquitetural

A solução adotada utiliza predominantemente o stack Microsoft 365, com:

* SharePoint como base de dados e estrutura
* Power Apps para formulários e interfaces
* Power Automate para automações orientadas a eventos
* Microsoft Teams e Outlook como canais de interação

Quando necessário, o ecossistema é estendido por meio de:

* Microsoft Graph API
* RPA em Python
* integrações externas pontuais

Os fluxos foram desenhados com **responsabilidade única**, escopos pequenos e desacoplados, permitindo evolução incremental e fácil manutenção.

---

## ⚙️ Limites Técnicos e Mitigações

Foram considerados conscientemente os limites do SharePoint e do Power Automate (volume de dados, paralelismo e disparos). Esses limites não representam risco para o contexto do ecossistema, que é interno e não massivo.

A mitigação ocorre por meio de:

* divisão de responsabilidades em múltiplos fluxos
* desacoplamento entre listas
* extensões externas quando necessário

---

## 🔗 Escalabilidade e Ponto de Quebra

O ecossistema é escalável dentro do seu propósito. Caso funcionalidades mais complexas sejam necessárias, os dados podem ser consumidos via API e processados externamente.

Não há, no contexto atual, um ponto de quebra claro identificado para a arquitetura.

---

## 🧠 Considerações Finais

A arquitetura adotada é pragmática, sustentável e adequada à realidade corporativa, priorizando entrega de valor, governança e manutenção simples, sem dependência excessiva de conhecimento técnico especializado.


