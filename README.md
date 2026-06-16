# /copy — Documentação da Skill

Skill de produção de copy estratégica para performance (Meta Ads, Google Ads, Landing Pages, Roteiros de Vídeo e Social Media). Age como consultora de copy, não como executora de pedido: avalia o que converte, propõe o ângulo certo e só escreve depois de ter contexto real do cliente e da audiência.

---

## Pré-requisitos

Para usar esta skill você precisa de:

1. **Claude Code** — CLI da Anthropic. [Instalar](https://docs.anthropic.com/pt/docs/claude-code)
2. **Repositório clonado** — a pasta `clientes/` com `contexto.md` preenchido para o cliente em questão. Quanto mais rico o contexto (produto, ICP, histórico de aprovação, vocabulário do cliente), mais precisa a copy.
3. **MCPs (opcional)** — você pode conectar Google Drive (para buscar Manual de Copy e análise competitiva), Ekyte (histórico de tasks aprovadas/reprovadas) e BigQuery/WhatsApp (linguagem do ICP em calls e mensagens). Sem eles a skill funciona, mas pede mais contexto no prompt.

---

## Ativação

No chat do Claude Code, basta digitar:

```
/copy
```

A skill apresenta um menu interativo para guiar o processo. Ou acione direto com contexto:

```
/copy Destra Consultoria — criativo Meta para diagnóstico gratuito, audiência fria
```

```
/copy Aya Cleaning — LP de captação de leads para limpeza residencial
```

```
/copy Nuveto — Google Ads para campanha de busca, intenção "software de RH"
```

A skill identifica o cliente, o tipo de entregável e o estágio da audiência. Quando falta informação crítica, ela pergunta antes de escrever.

---

## Como o contexto do cliente funciona

Antes de escrever qualquer linha, a skill lê `clientes/<slug>/contexto.md`. Esse arquivo contém:

- Produto e mecanismo real (o que transforma a vida do cliente)
- ICP com dores específicas e momento de compra
- Proof points disponíveis (números, cases, depoimentos)
- Restrições e vocabulário aprovado/reprovado pelo stakeholder
- Histórico de copy aprovada e reprovada
- CTA validado e tom de voz

**Se o contexto estiver incompleto:** a skill sinaliza o que falta e pede no prompt. Nunca fabrica dados ou suposições.

---

## Tipos de entregável disponíveis

| Tipo | Quando usar | Como pedir |
|---|---|---|
| `criativo` | Copy para criativos Meta — copy da imagem + programação do anúncio | "criativo Meta para [cliente]" |
| `lp` | Landing page completa — hero, benefícios, prova, CTA e mais | "LP de captação para [cliente]" |
| `google` | RSA — 15 títulos (30 chars) + 4 descrições (90 chars) | "Google Ads para [campanha]" |
| `roteiro` | Roteiro de vídeo — cenas com direção visual e narração corrida | "roteiro de vídeo UGC para [cliente]" |
| `social` | Pré-pauta ou pauta completa para Instagram/LinkedIn | "pauta de social media para [cliente]" |

---

## Exemplos de uso

**Criativo Meta:**
```
/copy Destra Consultoria — criativo estático para audiência fria, ângulo ISO para PMEs
```

**Landing Page:**
```
/copy Meca Automatizadores — LP para captação de leads de automação de processos
```

**Google Ads:**
```
/copy Aya Cleaning — RSA para campanha de busca "limpeza residencial Los Angeles"
```

**Roteiro de vídeo:**
```
/copy Nuveto — roteiro UGC com hook sobre rotatividade de funcionários, 60s
```

**Social Media:**
```
/copy Sol Interiors — pauta de Instagram, tema: antes e depois de reforma residencial
```

---

## Postura estratégica — o que esperar

A skill age como consultora, não como digitadora:

- **Diagnostica antes de escrever.** Articula o ângulo escolhido, o que não vai fazer e por quê.
- **Discorda quando necessário.** Se o pedido tende a performar mal, sinaliza e propõe alternativa.
- **Calibra pelo que já converteu.** Usa histórico de copy aprovada do cliente como baseline.
- **Sem clichê.** Headline genérica ou frase de efeito vazia é retrabalho garantido — a skill evita e avisa.

---

## Princípios que guiam a copy

- Ângulo estratégico sempre explícito: quem é a audiência, em que estágio está, o que ela precisa reconhecer para agir.
- Proof points reais: números, dados verificáveis, casos concretos. Nunca promessas vazias.
- Linguagem do ICP: usa as palavras que o cliente usa para descrever o próprio problema, não o jargão da empresa.
- Sem travessão (—) em nenhum output. É o marcador mais reconhecível de texto gerado por IA.
- Especificidade sempre bate generalidade.

---

## Protocolo pós-entrega

Após gerar qualquer copy, a skill pergunta se foi aprovada ou ajustada. A resposta alimenta o `contexto.md` do cliente — ângulos aprovados viram baseline, ângulos reprovados são registrados para nunca se repetir. Sem esse feedback, a assertividade degrada.

---

## Estrutura de arquivos

```
.claude/
  skills/
    copy/
      SKILL.md                        ← instrução do agente (carregada automaticamente)
      README.md                       ← este arquivo
      references/
        criativo-meta.md              ← campos do Ads Manager, formato de output
        lp.md                         ← estrutura e regras para Landing Page
        google-ads.md                 ← estrutura RSA (títulos e descrições)
        roteiro-video.md              ← estrutura de cenas e narração corrida
        social-media.md               ← fluxo pré-pauta/pauta completa
        checklist-anti-ia.md          ← checklist obrigatório antes de qualquer entrega
clientes/
  <slug>/
    contexto.md                       ← dossiê do cliente (essencial para personalização)
```

---

## Dúvidas frequentes

**A skill funciona sem o `contexto.md` do cliente?**
Funciona, mas pede os dados no prompt (produto, ICP, proof points, restrições). A personalização fica limitada ao que você fornecer. Para uso recorrente, vale criar o contexto persistente.

**O que é "programação do anúncio" no criativo Meta?**
É o texto que vai no Ads Manager: texto principal, títulos, descrição e CTA. A skill entrega os dois blocos — copy da imagem (headline + sub + selo) e programação do anúncio — separadamente e em sequência.

**A skill pode gerar copy para um cliente novo sem histórico?**
Sim. Sem histórico de aprovação, a skill usa o contexto do prompt e sinaliza o que está sendo assumido. A partir da primeira aprovação, alimenta o baseline automaticamente.

**Como funciona o checklist anti-IA?**
Antes de entregar qualquer output, a skill revisa internamente contra uma lista de padrões reconhecíveis de texto gerado por IA (travessão, frases genéricas, promessas sem âncora, etc). Você recebe o output já revisado — não precisa pedir.

**Preciso de MCPs específicos para usar?**
Não obrigatoriamente. Google Drive, Ekyte e BigQuery/WhatsApp ampliam o que a skill busca automaticamente (Manual de Copy, histórico de tasks, linguagem do ICP em calls). Sem eles, tudo que estiver no `contexto.md` e no prompt é suficiente.
