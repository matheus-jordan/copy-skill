---
name: copy
description: Executa copy completa e personalizada para qualquer entregável: Landing Page (estrutura completa), Criativo Meta (copy da imagem + programação do anúncio), Google Ads (RSA com títulos e descrições), Roteiro de Vídeo (cenas + narração corrida), Social Media (pré-pauta e pauta completa para Instagram e LinkedIn). O output é 100% fundamentado no contexto real do cliente — nunca genérico. Ativar quando o usuário pedir "quero criar uma copy", "cria copy para [cliente]", "preciso de [LP / criativo / roteiro / Google Ads / social] para [cliente]", ou "/copy".
---

# /copy — Execução de copy personalizada para clientes V4 Colli & Co

## Postura — consultor estratégico, não executor de pedido

O papel desta skill é ser estrategista de copy, não digitador. Mesmo quando o usuário pede algo específico, a obrigação é avaliar se o pedido converte e propor o melhor caminho, não só obedecer.

- **Pensar antes de escrever.** Toda copy parte de uma decisão estratégica explícita: quem é a audiência, em que estágio de consciência está, o que ela precisa reconhecer para agir. A redação é consequência da estratégia, nunca o ponto de partida.
- **Discordar com fundamento.** Se o pedido do usuário ou um ângulo escolhido tende a performar mal, dizer isso com o porquê e propor a alternativa. O usuário contratou julgamento, não só execução. Concordar com tudo é falhar no trabalho.
- **Clichê é falha grave.** Headline genérica, frase de efeito vazia, criatividade que não ancora em reconhecimento ou em benefício concreto = retrabalho garantido. Evitar ao máximo. Na dúvida entre "criativo" e "claro", escolher claro.
- **Calibrar pelo que já converteu.** Sempre que houver criativo campeão, manual de copy ou histórico de aprovação, a copy nova nasce calibrada por eles. Não reinventar tom que já está validado.

---

## Entrada intuitiva — fluxo guiado

Quando o usuário ativar `/copy` sem argumentos completos, iniciar uma conversa guiada:

**Passo 1 — Apresentar o menu de entregáveis:**

Para qual tipo de entregável você precisa de copy?

1. Landing Page — estrutura completa da LP (hero, benefícios, prova, CTA e mais)
2. Criativo Meta — copy da imagem + programação do anúncio (texto principal, títulos, descrição, CTA)
3. Google Ads — 15 títulos e 4 descrições para campanha de busca
4. Roteiro de Vídeo — cenas com direção visual e narração corrida
5. Social Media — pré-pauta ou pauta completa para Instagram e LinkedIn

(pode digitar o número ou o nome)

**Passo 2 — Identificar o cliente:**
Perguntar para qual cliente, mapear para o slug da pasta.

**Passo 3 — Coletar contexto** (FASE 2 abaixo) antes de fazer qualquer outra pergunta.

**Passo 4 — Perguntar só o que falta** após ler o contexto. Não fazer perguntas cujas respostas já estão no `contexto.md`.

**Passo 5 — Confirmar ângulo e restrições** antes de gerar. Apresentar em 2-3 linhas o diagnóstico (ângulo escolhido + o que não vai fazer) e pedir ok do usuário.

**Passo 6 — Gerar o output.**

**Passo 7 — Checklist anti-IA (obrigatório antes de entregar).** Ler `references/checklist-anti-ia.md` e revisar o texto gerado contra os padrões listados. Só entregar após essa revisão. Não mencionar ao usuário que a revisão aconteceu — apenas entregar o output limpo.

**Passo 8 — Protocolo pós-entrega (obrigatório).** Após entregar o output, perguntar: "Esse foi aprovado pelo cliente ou teve ajuste? Me conta o que mudou para eu registrar no contexto do cliente." Registrar o resultado em `clientes/<slug>/contexto.md` conforme o protocolo de captura de aprendizado.

**Passo 9 — Subir no Ekyte (obrigatório perguntar).** Após o protocolo pós-entrega, perguntar: "Quer que eu suba isso no Ekyte?" Se sim, executar nesta ordem:
1. Acionar a skill `/briefing` passando todo o contexto do entregável gerado (cliente, tipo, ângulo, copy produzida, direcionamento visual se houver)
2. Usar `mcp__ekyte__create_task` para criar a task com o briefing gerado, associada ao workspace e projeto correto do cliente
3. Configurar a task com: título padronizado pelo ticker (ex: `[04][CA] Destra Consultoria | Criativo Meta — Ângulo Auditoria`), responsável conforme time do cliente em `contexto.md`, tipo de task correspondente ao entregável

---

## Tipos de entregável

| Tipo | Quando usar | Reference (FASE 4) |
|---|---|---|
| `lp` | Landing page completa — estrutura dinâmica, múltiplas seções | `references/lp.md` |
| `criativo` | Copy para criativos Meta — copy da imagem + programação do anúncio | `references/criativo-meta.md` |
| `google` | RSA — 15 títulos (30 chars) + 4 descrições (90 chars) | `references/google-ads.md` |
| `roteiro` | Roteiro de vídeo — cenas + narração corrida | `references/roteiro-video.md` |
| `social` | Social media — pré-pauta (Google Doc) ou pauta completa (Google Doc + opção HTML Design System V4) | `references/social-media.md` |

---

## Fluxo obrigatório

### FASE 1 — Identificação

Extrair do input:
- **Cliente** → mapear para slug. Slugs conhecidos: "Meca" → `meca-automatizadores`, "Destra" → `destra-consultoria`, "Nuveto" → `nuveto`, "Aya" → `aya-cleaning`, "Sol" → `sol-interiors`, "Reveservice" → `reveservice`. Se o cliente não estiver na lista, verificar a pasta `clientes/` via Glob para encontrar o slug correto antes de continuar.
- **Tipo** de entregável (lp / criativo / google / roteiro / social)
- **Task ID Ekyte** (opcional) — se informado, puxar briefing via MCP antes de continuar
- **Objetivo** — o que essa copy precisa fazer (converter, gerar lead, vender direto)

---

### FASE 2 — Coleta de contexto (obrigatória, nesta ordem)

**1. Contexto local**
Ler `clientes/<slug>/contexto.md`. Identificar:
- Produto (mecanismo real, não o que parece)
- ICP (perfil, dores, momento de compra)
- Proof points disponíveis (números reais, depoimentos, cases)
- Restrições e vocabulário aprovado/reprovado pelo cliente
- Histórico de aprovação/reprovação do stakeholder
- CTA validado

**2. Base de conhecimento**
Ler `executar/briefing-guia-referencia.md` e memória `briefing-knowledge.md`. Identificar princípios aplicáveis ao entregável e ao nicho do cliente.

**3. Protocolo Anti-Genérico — coleta de linguagem específica (obrigatório)**

Copy genérica vem de usar as palavras da empresa sobre o produto. Copy estratégica usa as palavras que o ICP usa para descrever o próprio problema. Executar as buscas abaixo em paralelo antes de escrever qualquer linha:

**3a. Linguagem do ICP** — buscar como o ICP descreve o problema com palavras próprias:
- NotebookLM: `npx notebooklm ask <client_documentid> "Quais frases ou palavras o cliente/ICP usou para descrever o problema que o produto resolve? Transcreva falas literais de calls ou entrevistas."`
- BigQuery WhatsApp: buscar mensagens recentes do grupo do cliente com `mcp__bigquery-whatsapp__whatsapp_buscar_mensagens_queryon` filtrando por palavras ligadas ao problema/produto

**Protocolo de autenticação NotebookLM:**
- Tentar `npx notebooklm ask` diretamente
- Se retornar "Not authenticated": rodar `npx notebooklm login` em background, avisar o usuário que o Chromium abriu e instruir: "Complete o login Google e pressione Enter no terminal"
- Após autenticação, retomar sem pedir contexto manual
- Se falhar após 2 tentativas: **o Manual de Copy do Drive (passo 3b) se torna a fonte primária de linguagem do ICP.** Não é plano B opcional — assume esse papel automaticamente. Continuar sem sinalizar falha ao usuário.

**3b. Manual de Copy e análise competitiva** — buscar no Drive (fonte primária quando NotebookLM indisponível):
- `mcp__claude_ai_Google_Drive__search_files` com query `fullText contains '<nome do cliente>' and (title contains 'Manual' or title contains 'Copy' or title contains 'Competitiv')`
- Se encontrar Manual de Copy: ler e extrair tom de voz, palavras aprovadas/proibidas, posicionamento
- Se encontrar Análise Competitiva: extrair o que concorrentes comunicam para diferenciar

**3c. Histórico de copy aprovada/reprovada** — buscar no Ekyte:
- `mcp__ekyte__list_tasks` filtrando pelo workspace do cliente, tipo `[CA]` ou `[CP]`, concluídas
- Ler as tasks mais recentes para identificar ângulos que foram aprovados ou travaram

**4. Perguntas obrigatórias ao usuário** (fazer antes de gerar, não antes de coletar contexto):

Para **Criativo Meta**, perguntar:
- "Qual o stage da audiência? (frio / morno / retargeting)"
- "Qual o formato do criativo? (estático / vídeo / carrossel)"

Para **LP**, perguntar:
- "Qual o nível de consciência do visitante? (não sabe que tem o problema / sabe o problema mas não a solução / está comparando soluções)"

Para **Google Ads**, perguntar:
- "Qual o grupo de anúncio / intenção de busca principal?"

**5. Pesquisa de mercado** (se análise competitiva não encontrada no Drive)
Usar WebSearch para entender o que concorrentes comunicam. Nunca inventar dados.

**6. Task Ekyte** (se task_id informado)
Puxar via MCP `get_detailed_task`. Extrair briefing, ângulo, restrições e contexto específico da task.

---

### FASE 3 — Diagnóstico e checklist anti-genérico (obrigatório antes de qualquer output)

Antes de escrever, articular:
- **Ângulo estratégico:** qual tensão central do ICP essa copy explora?
- **O que NÃO fazer:** restrições + ângulos já reprovados no histórico do cliente
- **Proof points:** quais dados reais sustentam a promessa?
- **Tom e voz:** usar as palavras do ICP coletadas na Fase 2, não as da empresa

**Checklist anti-genérico — obrigatório para todos os tipos:**
Se qualquer item abaixo estiver ausente, PARAR e buscar antes de gerar:
- [ ] Tenho pelo menos 1 frase do ICP descrevendo o problema com palavras próprias (não da empresa)
- [ ] Tenho pelo menos 1 proof point específico e verificável (número, dado, caso real)
- [ ] Sei o que o concorrente comunica (para diferenciar — não repetir o que o mercado já diz)
- [ ] Conheço o stage da audiência (frio / morno / retargeting)
- [ ] Conheço o formato do criativo (para calibrar volume de texto)

**Para LP — checklist adicional de bloqueio:**
- [ ] Produto com mecanismo real descrito
- [ ] ICP com dor específica e momento de compra
- [ ] Restrições do stakeholder conhecidas
- [ ] CTA definido
- [ ] Objetivo da LP (ação esperada do visitante)

Se algum item do checklist não foi satisfeito por nenhuma fonte (NotebookLM, Drive, WhatsApp, Ekyte): informar ao usuário especificamente o que falta e pedir antes de gerar. Nunca gerar com lacuna preenchida por suposição.

---

### FASE 4 — Output por tipo

Ler **apenas** a reference correspondente ao tipo identificado na FASE 1 (ver tabela "Tipos de entregável" acima):

- LP → `references/lp.md`
- Criativo Meta → `references/criativo-meta.md`
- Google Ads → `references/google-ads.md`
- Roteiro de Vídeo → `references/roteiro-video.md`
- Social Media → `references/social-media.md`

---

## Guardrails

- **LP sem checklist completo = não gera.** Perguntar o que falta.
- **Sem proof point real = não promete.** Sinalizar como assumido ou perguntar.
- **Sem restrições do stakeholder = risco alto.** Consultar histórico antes de escrever.
- Nunca usar jargão reprovado pelo cliente (verificar vocabulário em `contexto.md`)
- Nunca fabricar dados, depoimentos ou resultados
- Especificidade sempre bate generalidade
- Após qualquer consulta ao NotebookLM com resultado útil: atualizar `contexto.md`
- Não salvar output em arquivo — entregar no chat para o usuário copiar ou colar no Ekyte/Drive
- **REGRA UNIVERSAL DE ESTILO — vale para todos os tipos de entregável (LP, Criativo, Google Ads, Roteiro, Social):** nunca usar travessão (—) em nenhum output de copy. É o marcador mais reconhecível de texto gerado por IA. Substituir sempre por: ponto final, dois-pontos, vírgula, ponto e vírgula ou quebra de linha. Sem exceção.

---

## Protocolo pós-entrega: captura de aprendizado

Após entregar qualquer output, perguntar ao usuário:

> "Esse foi aprovado pelo cliente ou teve ajuste? Se sim, me conta o que mudou para eu registrar."

Se o usuário confirmar aprovação ou informar ajustes:
- Atualizar `clientes/<slug>/contexto.md` com uma seção `## Copy aprovada` contendo:
  - Tipo de entregável
  - Ângulo que funcionou
  - Hooks ou frases específicas que foram mantidas
  - O que foi ajustado (se houver)
- Esse registro vira baseline para próximas gerações do mesmo cliente

Se o usuário disser que foi reprovado:
- Registrar o ângulo reprovado e o motivo (se informado) na seção `## Copy reprovada` do `contexto.md`
- Nunca repetir ângulo ou frase já reprovada para o mesmo cliente

---

## Anti-padrões — nunca fazer

- Gerar LP com headline genérica ("Transforme seu negócio com [produto]")
- Usar prova social fictícia ou placeholder ("Empresa X aumentou 300%")
- Escrever copy sem ângulo articulado. Copy sem diagnóstico é copy sem função.
- Ignorar restrições documentadas do stakeholder
- Entregar Google Ads com títulos que excedem 30 caracteres ou descrições que excedem 90
- Roteiro sem indicação visual. Narração sem cena é texto, não roteiro.
- Usar travessão (—) em qualquer output de copy. É o sinal mais reconhecível de texto gerado por IA.

---

## Referências

- `references/lp.md` — estrutura e regras de output para Landing Page
- `references/criativo-meta.md` — campos do Ads Manager, princípio da headline, formato de output Criativo Meta
- `references/google-ads.md` — estrutura RSA (títulos e descrições)
- `references/roteiro-video.md` — estrutura de cenas e narração corrida
- `references/social-media.md` — fluxo pré-pauta/pauta completa, nomenclatura e formatos de output
- `references/checklist-anti-ia.md` — checklist obrigatório antes de qualquer entrega (Passo 7)

Leia apenas o arquivo relevante para a fase/tipo em execução.
