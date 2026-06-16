# Output — Social Media (tipo `social`)

**Fluxo obrigatório em 2 estágios — nunca pular etapas:**

**Estágio 1: Pré-pauta**
Gerada primeiro. Apresentada via Google Doc (HTML no Drive). Só avança para pauta completa após confirmação explícita de aprovação do cliente.

**Estágio 2: Pauta completa**
Gerada após aprovação confirmada da pré-pauta. Ao final, perguntar ao usuário o formato de entrega:
- **Google Doc** — HTML no Drive, instrução para abrir com Google Docs
- **HTML com Design System V4** — apresentação visual completa usando a skill `/frontend-design` com o template em `Usersmathev4-design-system/`

---

**Perguntas obrigatórias antes de gerar a pré-pauta (nesta ordem):**

1. **Plataforma:** Instagram, LinkedIn ou ambos
2. **Pilares de conteúdo:** buscar no `contexto.md` do cliente. Se não existir, definir antes do volume. Sugestão padrão: Educativo, Posicionamento, Dor e consequência, Prova social, Bastidores.
3. **Volume e período:** quantos posts, para qual semana ou mês
4. **Datas sazonais:** mapear dois níveis antes de apresentar:
   - Nível 1: datas comemorativas do nicho — buscar via `WebSearch` e garantir veracidade antes de apresentar. Nunca inventar datas.
   - Nível 2: contexto cultural e sazonal do mês (Copa do Mundo, Carnaval, férias escolares, datas nacionais) — apresentar ao usuário para decidir se e como usar
5. **Mix de formatos:** sugerir com base nos pilares (estático para produto e dor, carrossel para educativo, reels para bastidores e hook). Usuário ajusta.

**Gate obrigatório:** não gerar pauta completa sem confirmação explícita de aprovação da pré-pauta pelo cliente. Se o usuário não confirmar, perguntar antes de avançar.

---

**Nomenclatura de documentos:**

Antes de criar qualquer documento no Drive, buscar o ticker do cliente via `mcp__ekyte__list_short_workspaces` com o nome do cliente. Extrair do campo `name` (ex: "[BILLIONS] [DEST1] Destra Consultoria" → ticker = `DEST1`).

Formato: `[TICKER] Nome do Cliente | Tipo do Documento MÊS ANO`

Exemplos:
- `[DEST1] Destra Consultoria | Pré-pauta Social JULHO 2026`
- `[MECA] Meca Automatizadores | Pauta Social AGOSTO 2026`

---

**Formato de output — Pré-pauta:**

Entregar no chat em markdown e criar documento HTML no Drive.

Para cada post:

**Post [N] · [Formato] · [Semana]**
Pilar: [pilar]
Tópico: [assunto em 1 linha]
Ângulo: [tensão central em 1 linha]
Referência sazonal: [se aplicável]

Ao criar o documento HTML no Drive:
- Usar `mcp__claude_ai_Google_Drive__create_file` com `contentMimeType: text/html`
- Formatar com `<h1>`, `<h2>`, `<strong>`, `<hr>` para hierarquia visual
- Ao entregar o link, incluir instrução obrigatória em negrito:

**Importante: abra o link, clique em "Abrir com" e selecione Google Docs para visualizar com formatação correta.**

---

**Formato de output — Pauta completa:**

Para cada post, entregar em markdown no chat:

**Post [N] · [Formato] · [Semana]**
Pilar: [pilar]

**Headline (imagem)**
[chamada principal com seta: "→ Leia a legenda" ou "→ Arraste para o lado"]

**Legenda**
[copy completa com emojis como marcadores (👉), fechamento com pergunta ou CTA, hashtags ao final]

**Direcionamento visual**
[instrução para o designer: fundo, tipografia, elementos, clima visual]

Ao finalizar todos os posts, perguntar: **"Como prefere o documento final: Google Doc ou apresentação HTML com Design System V4?"**

Se Google Doc: criar HTML no Drive com instrução de abertura.
Se HTML: acionar a skill `/frontend-design` com o template `Usersmathev4-design-system/` para gerar apresentação visual completa. Salvar em `clientes/<slug>/` com nomenclatura padronizada pelo ticker.

---

**Padrão de copy validado para social:**
- Headline na imagem: ideia coesa + seta direcionando ("→ Leia a legenda" / "→ Arraste para o lado")
- Legenda: emojis como marcadores visuais (👉), não como decoração. Fecha com pergunta ou CTA direto. Hashtags ao final.
- Sem travessão (—) — regra universal
- Checklist anti-IA aplicado antes de entregar
