# Output — Criativo Meta (tipo `criativo`)

**Antes de gerar — pedir criativo campeão:**
Perguntar ao usuário: "Você tem um print do criativo que melhor performou na campanha? Se sim, manda que eu calibro o volume de texto e o ângulo com base no que já funcionou."
- Se tiver: ler o print, identificar extensão do texto de apoio, tom e estrutura que performou
- Se não tiver: seguir com o contexto do cliente e as melhores práticas do nicho

**Campos do criativo Meta — refletem os campos reais do Gerenciador de Anúncios (Ads Manager):**

```
TEXTO PRINCIPAL
[Campo obrigatório — aparece acima do criativo na maioria dos posicionamentos]
Limite técnico: sem limite rígido. Recomendação Meta: até 125 chars.
Na prática: B2C fica em 1-3 linhas; B2B aceita 4-8 linhas sem penalidade.
Pode usar @ para marcar perfis ou Páginas do Facebook diretamente no texto.
Estrutura recomendada:
  - Linha 1: hook que para o scroll (dor / dado / provocação / pergunta)
  - Linhas 2-4: desenvolvimento — problema → solução → prova
  - Linha final: CTA textual antes do botão
Formatação permitida: emojis para organização visual, quebras de linha para escaneabilidade.
Se o usuário quiser versão com emojis: usar ícones como marcadores (▶ ✅ ⚠️ 🔧) para substituir bullets,
destacar proof points e quebrar blocos de texto. Nunca usar emojis apenas como decoração.

TÍTULO
[Campo opcional — aparece abaixo da imagem/vídeo, complementa o criativo]
Limite: até 255 chars por título. Podem ser cadastrados até 5 títulos (Meta roda testes automáticos).
Uso recomendado: reforçar o diferencial central ou o CTA com linguagem direta.
Exemplo: "42 anos. Laudo técnico em 100% dos projetos." ou "Diagnóstico técnico em até 4 horas."

DESCRIÇÃO
[Campo opcional — exibida em alguns posicionamentos abaixo do título]
Limite: sem limite rígido. Recomendação: 1-2 linhas curtas.
Uso: prova social, garantia, detalhe adicional que reforça a decisão de clique.
Exemplo: "Portfólio: Bayer, Syngenta, Hitachi, Vigor."

CHAMADA PARA AÇÃO (botão)
[Dropdown — escolher a opção mais próxima da intenção do anúncio]
Opções disponíveis: Saiba mais | Pedir cotação | Obter oferta | Ver detalhes | Agendar agora | Cadastre-se | Assinar | Baixar
Regra: usar "Pedir cotação" ou "Saiba mais" para B2B com ticket alto e funil longo.
Evitar "Comprar agora" ou "Assinar" para serviços industriais — cria atrito.
```

**Contexto de uso:** a skill substitui o copywriter na íntegra. O output é consumido por dois perfis diferentes — designer (que produz o criativo) e gestor de tráfego (que programa o anúncio).

**Estrutura do output quando há vários criativos para a mesma campanha (padrão):** entregar uma **Copy da imagem por criativo** (cada variação tem headline, sub e CTA próprios) e **uma única Programação do anúncio que serve todos os criativos** (texto principal, títulos, descrição e CTA do botão). Não repetir programação por criativo — no Meta os textos do anúncio são compartilhados pelas variações de imagem do conjunto. Só gerar programação separada se o usuário pedir campanhas/conjuntos distintos por criativo.

**Princípio da headline — reconhecimento antes de criatividade (calibrar pelo estágio da audiência):**
A função da headline depende de quem vê o criativo. Decidir isso antes de escrever:
- **Audiência fria mas com busca ativa pelo produto (problema/solução-aware, procurando a categoria):** a headline tem que ser RECONHECÍVEL na primeira fração de segundo. Usar o nome do produto na linguagem que o ICP usa pra buscar (ex: "Motor para porta de enrolar que não te deixa na mão", "Kit de motor para porta de enrolar"). O diferencial/ângulo (durabilidade, garantia, etc.) vai no subtítulo, não na headline. O cara precisa pensar "é isso que eu procuro", não decifrar.
- **Audiência fria sem busca (não sabe que tem o problema):** headline pode liderar pela dor ou provocação, porque ainda não há intenção a capturar.
- **Morno / retargeting:** headline pode assumir o reconhecimento e liderar por diferencial, objeção ou oferta.
- **Proibido neste contexto:** headline abstrata ou "de efeito" de 1-2 palavras que obriga o leitor a decifrar (ex: "NÃO QUEIMA", "COBRE PURO"). Mata o reconhecimento e perde o scroll. Frase de efeito não é headline de performance.

**Bloco 1 — Copy da imagem** (para o designer)
O que vai escrito dentro do criativo. Entregar:
- Headline: chamada principal em destaque na imagem (curta, direta, impactante)
- Corpo: texto de apoio dentro da imagem (1-2 frases, reforça o ângulo da headline)
- CTA da imagem: texto do botão ou chamada visual dentro do criativo (ex: "Fale com um especialista")

**Bloco 2 — Programação do anúncio** (para o gestor de tráfego) — **uma só para todos os criativos**
O que vai nos campos do Ads Manager, compartilhado por todas as variações de imagem. Entregar uma única vez:
- Texto principal: aparece acima do criativo no feed. Hook + desenvolvimento + CTA textual. B2B aceita 4-6 linhas. Escrever de forma que funcione com qualquer uma das variações de imagem (não amarrar a um criativo específico).
- Títulos: até 5 opções — Meta testa automaticamente e distribui verba para o melhor
- Descrição: 1-2 linhas curtas — aparece em alguns posicionamentos abaixo do título
- CTA (botão): opção do dropdown (Saiba mais / Pedir cotação / Ver detalhes / Agendar agora)

**Formato de output — 100% Markdown, sem blocos de código:**

Todo output deve ser entregue em markdown puro — sem usar ``` code blocks ```. Usar headers `##`, `###`, negrito `**`, listas `-` e `→` para organização visual.

---

## CRIATIVO 1 — [Nome | Ângulo central]

**Headline**
[chamada principal — vai em destaque na imagem]

**Sub**
[diferencial / ângulo — 1 frase de apoio na imagem]

**Corpo / selo de apoio**
[detalhe ou prova curta dentro da imagem, se houver]

**CTA da imagem**
[texto do botão ou chamada visual]

**Direção de imagem**
[orientação visual para o designer]

---

## CRIATIVO 2 — [Nome | Ângulo central]
[mesma estrutura de Copy da imagem]

---

(repetir Copy da imagem para cada criativo)

---

## Programação do anúncio (serve para todos os criativos acima)

**Texto principal**
[corpo do anúncio — funciona com qualquer uma das variações de imagem]

**Títulos**
1. [título 1]
2. [título 2]
3. [título 3]
4. [título 4]
5. [título 5]

**Descrição**
[1-2 linhas]

**CTA (botão)**
[opção do dropdown]

---

Regras de output:
- Uma Copy da imagem por criativo; uma única Programação do anúncio para o conjunto inteiro
- A Programação do anúncio vem ao final, depois de todas as Copies da imagem, e nunca se repete por criativo
- Só gerar programação separada por criativo se o usuário pedir conjuntos/campanhas distintos
- Se o usuário pedir variação com emojis: gerar segunda versão do Texto principal apenas, mantendo o restante igual
- Não numerar etapas nem adicionar explicações após o output — entregar limpo para copiar direto
- NUNCA usar blocos de código (```) no output — sempre markdown puro
