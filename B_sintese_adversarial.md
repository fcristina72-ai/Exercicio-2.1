# Síntese adversarial

> Confronto crítico entre dois relatórios sobre a jornada telefônica do Seguro-Desemprego (Caixa / MTE), horizonte 2024–2026.
> **A1 = `B_relatorio_assistente1.md`** (postura cética, fontes rastreáveis) · **A2 = `B_relatorio_assistente2.md`** (postura confiante, arquitetura completa).

---

## V1 — primeira leitura (data: 2026-06-03)

### Pontos de concordância
- **Cidadão / trabalhador** como usuário final.
- **Existência de automação no front-end** telefônico (URA / atendimento eletrônico).
- **Camada de atendente humano** acionada por transbordo.
- **Back-end integrado Caixa ↔ Dataprev ↔ MTE.**
- **Camada de retaguarda / recurso administrativo** no MTE.

### Divergências
- **Divergência 1 — Natureza da URA (DTMF vs. NLP/ASR):** A2 afirma que a URA migrou para interface cognitiva com NLP/ASR como **fato consolidado**; A1 afirma que **não há documentação técnica pública** e que isso deve ser tratado como **hipótese de trabalho**.
  - *Mais defensável:* A1. A2 dá como fato o que não consegue lastrear.
  - *Evidência que decide:* documentação técnica da Caixa/Serpro/Dataprev (inexistente no domínio público).
- **Divergência 2 — Regime de fontes:** A2 cita categorias genéricas (editais, relatórios de gestão) sem URL; A1 traz tabela com órgão, tipo e URL.
  - *Mais defensável:* A1. Fonte não rastreável equivale a fonte ausente.
- **Divergência 3 — Base de evidência sobre o gargalo:** A2 narra latência da API sem número citável; A1 traz dado da CGU (67,4% presencial × 18,6% online de deferimento).
  - *Mais defensável:* A1, com folga.

### Lacunas dos dois
- Camada de identidade/autenticação (gov.br / validação CPF-NIS).
- Empregador (Empregador Web) como ator a montante.
- Canais-app paralelos (CTPS Digital, Emprega Brasil).

### Perguntas em aberto que levarei ao /grill-me
- A URA usa NLP/ASR ou DTMF? Qual fornecedor/contrato?
- Onde e por qual sistema o cidadão é autenticado?
- Os 18,6% da CGU incluem recurso por telefone?

---

## V2 — após verificação externa de fontes (data: 2026-06-04)

### Mudanças nesta versão
- **Mudou (posição):** Divergência 2 (canais) deixa de ser tratada como empate. **Antes:** "ambos plausíveis". **Agora:** A2 errou uma afirmação positiva e verificável (o número "111" não é canal do Seguro-Desemprego); o canal oficial de teleatendimento é o **158 (MTE)**, conforme a página gov.br do serviço.
  **Gatilho:** verificação externa na página oficial gov.br/Solicitar o Seguro-Desemprego, que cita explicitamente o 158.
- **Divergência resolvida:** Divergência 3 (gargalo). **Antes:** A2 alegava gargalo sem número. **Agora:** o dado de A1 (67,4% × 18,6%) foi confirmado no Relatório de Avaliação da CGU (nº 1421234, base 2022). O dado de A1 vira evidência utilizável; a narrativa de A2 permanece sem lastro.
  **Gatilho:** leitura da fonte primária da CGU.
- **Mudou (rebaixamento):** Divergência 1 (NLP/ASR). **Antes:** "A2 provavelmente exagera". **Agora:** confirmada como **irresolúvel por fonte pública** — a busca não localizou documentação técnica da URA. A cautela de A1 está corroborada; a afirmação de A2 permanece hipótese.
  **Gatilho:** ausência de resultado nas buscas por arquitetura/fornecedor da URA.
- **Novo ator detectado:** camada de **identidade/autenticação gov.br**, promovida de "palpite" para "inferência ancorada por função" (consultar status exige autenticar CPF/NIS).
  **Gatilho:** necessidade de explicitar a base funcional da inferência.

### Estado atual da síntese (sobrescreve v1)
- Concordância: a de v1 + camada de identidade (inferida, ancorada).
- Divergências residuais: natureza da URA (irresolúvel sem LAI); granularidade do roteamento.
- Decisão para o mapa em C: separar o que entra como **fato** do que entra como **hipótese rotulada**.

---

## V3 — após sessão /grill-me e construção do mapa de atores (data: 2026-06-06)

### Mudanças nesta versão
- **Premissa derrubada:** "existe **uma** URA do Seguro-Desemprego". **Antes (v1/v2):** jornada única. **Agora:** "**jornada única do usuário sobre DUAS URAs distintas**" — URA-MTE/158 (requerimento e dúvidas) e canais da Caixa (consulta de parcelas e pagamento).
  **Gatilho:** pergunta do grill-me que apontou dois donos institucionais (158 = MTE; canais da Caixa) — não testei essa premissa antes e ela caiu.
- **Mudou (posição sobre o gargalo):** **Antes:** o gargalo seria sentido no atendente humano. **Agora:** o gargalo é propriedade do **barramento de integração** — a borda que transborda quando o back-end atrasa; cidadão e atendente são quem **sofre** o transbordo, não a causa.
  **Gatilho:** pergunta do grill-me — "o atendente *causa* ou apenas *recebe* o transbordo?"; ele apenas recebe, logo a âncora correta é o barramento.
- **Novo critério de fronteira (regra de inclusão):** adotada a **regra do primeiro salto** — entra quem o cidadão *encontra* ou *aciona diretamente*; o que o primeiro salto aciona por sua vez (Dataprev/eSocial/empregador) vira caixa-preta fechada.
  **Gatilho:** pergunta do grill-me que mostrou que "acionar pelo CPF" sem corte readmitiria o Estado inteiro.
- **Divergência resolvida (encaminhamento):** Divergência 1 (NLP). **Agora:** fechada como **"empate técnico — ninguém comprovou"**, com encaminhamento para LAI; no mapa de atores, a camada NLP/ASR entra explicitamente rotulada como hipótese.
  **Gatilho:** a sessão de grill-me não produziu nova evidência, apenas confirmou a impossibilidade de resolver sem documentação técnica.

### Estado atual da síntese (sobrescreve v2)
- Concordância: cidadão; duas URAs; atendente humano; barramento de integração; recurso administrativo no MTE; identidade gov.br (inferida).
- Divergências residuais: natureza da URA (NLP vs. DTMF) — empate técnico, pendente de LAI; granularidade do roteamento.
- Decisão para o mapa em C (consolidada): **7 atores + borda**, com gargalo ancorado no barramento, duas URAs como pontos de entrada distintos, e atores inferidos (NLP, roteamento, identidade) marcados com nível de confiança. Ver `C_mapa_atores.md`.
