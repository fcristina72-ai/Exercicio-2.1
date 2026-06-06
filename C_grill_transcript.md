# C_grill_transcript — Sessão /grill-me (íntegra)

> Entrevista adversarial, uma pergunta por vez, para validar o mapa de atores da jornada telefônica do Seguro-Desemprego. Objetivo: distinguir atores reais de inferidos, fixar fronteira de entrada/saída, classificar natureza (humano/IA) e identificar relações que importam. Avaliador (A) questiona; Pesquisador (P) defende.

---

## Rodada 1 — Critério de julgamento da síntese

**A:** Você deu "A1 mais defensável" em 4 das 5 divergências. Está corrigindo método ou conteúdo? A1 quase não se expôs — é fácil acertar quando não se afirma nada. Seu placar premia cautela e pune utilidade?

**P:** Concedo que nas Divergências 1 e 4 (NLP, roteamento) o ponto a A1 é quase tautológico — ela "venceu" por não afirmar. Mas o placar era por afirmação, não global: eu já separava "A2 melhor entregável / A1 melhor método". E na Divergência 2 a A2 fez afirmação positiva e errada (o "111"), então não foi só prêmio à omissão. Rebaixo 1 e 4 para "empate técnico".

---

## Rodada 2 — Padrão duplo na inferência

**A:** Você condenou A2 por afirmar NLP sem fonte, mas você mesmo postula uma camada de identidade gov.br que ninguém citou e para a qual também não tem fonte. Qual é a regra consistente?

**P:** A regra não é "inferir é proibido", é onde e com que rótulo. A2 pôs a inferência na tabela-fato; eu pus a minha sob "Lacunas — suspeito". Concedo que preciso explicitar a base: a consulta de status exige autenticar CPF/NIS, logo a identidade é inferência ancorada por função, não palpite. Vou criar níveis de confiança para a inferência.

---

## Rodada 3 — O salto do dado da CGU

**A:** Você ancorou a crítica ao funil no 67,4% × 18,6%. Mas esse dado é de recursos web/app e presencial, base 2022 — ele menciona a URA telefônica? Se não, você importou uma estatística de outro canal.

**P:** Esse ataque acerta. Concedo: o dado não menciona a URA telefônica; usá-lo como prova direta contra a IVR de voz foi um salto de camada. O que sobra é analogia sobre autosserviço, não prova sobre a URA. Rebaixo o dado de "âncora" para "evidência análoga; nexo com a URA = pergunta aberta".

---

## Rodada 4 — A fronteira da jornada

**A:** O título diz "URA da Caixa", mas 158 é do MTE (requerimento) e 0800 é da Caixa (parcelas). A jornada que você vai mapear começa e termina onde? Inclui o requerimento, ou só pós-concessão?

**P:** Todos entram no mapa.

---

## Rodada 5 — Critério de inclusão (não a lista)

**A:** "Todos entram" responde quem, não até onde. Se "tocou, entra", você mapeia o Estado inteiro (empregador, eSocial, CODEFAT). Me dê a regra de inclusão, não a lista.

**P:** Recorte de canal: entra quem o cidadão encontra ou aciona durante uma ligação telefônica. Assim empregador e eSocial ficam fora — o cidadão não os toca pelo telefone.

---

## Rodada 6 — Como ter clareza sobre atores reais

**A:** Boa pergunta de método. Use três testes: existência (confirmado / inferido-ancorado / inferido-padrão), pertinência (dentro da fronteira?) e distinção (ator ou função de outro?). Note que dois desses testes dependem da fronteira que você acabou de fixar.

**P:** Entendido. Aplico o recorte de canal como Teste 2 e carimbo cada ator pelo nível de evidência no Teste 1.

---

## Rodada 7 — O que "aciona" significa

**A:** Sua regra diz "encontra ou aciona". O "aciona" arrasta para dentro o roteamento, o barramento e a identidade — que o cidadão nunca percebe. Você inclui os sistemas invisíveis disparados pelo CPF, ou só o que ele percebe?

**P:** Sim, incluo o que é acionado pelo CPF.

---

## Rodada 8 — O corte da corrente (primeiro salto)

**A:** "Acionar pelo CPF" é uma corrente: URA → barramento → Dataprev → eSocial → empregador. Se "acionou, entra", você readmite tudo o que expulsou. Onde corta?

**P:** Aceito a regra do primeiro salto: entra o que a URA aciona diretamente (barramento, identidade); o que esses acionam por sua vez vira caixa-preta única ("back-end governamental"). Sete atores + uma borda, sem regresso infinito.

---

## Rodada 9 — Onde mora o gargalo

**A:** A relação mais carregada é URA → barramento → [borda] → atendente. A falha mais importante nasce na caixa-preta que você fechou. No mapa, o gargalo é propriedade de qual ator dentro do mapa?

**P:** No atendente.

---

## Rodada 10 — Causa vs. sintoma

**A:** Não. O atendente é o último a receber — ele não decide o transbordo, só o recebe. Se você o ancora como causa, a recomendação vira "contratar mais atendentes", que trata o sintoma. Quem decide transbordar é o barramento, que sente a latência e não tem fallback. O atendente também fica esperando a Dataprev?

**P:** Sim, ele também fica na mão da Dataprev. Então ele é a segunda vítima, não a causa. Movo o gargalo para o barramento; cidadão e atendente sofrem o transbordo, do mesmo lado da falha.

---

## Síntese da sessão (resultado)

- **Premissa derrubada:** "uma URA" → duas URAs distintas (158/MTE e 0800/Caixa), jornada única do ponto de vista do cidadão.
- **Regra de fronteira:** recorte de canal + primeiro salto.
- **Gargalo:** ancorado no barramento de integração; causa-raiz externa (caixa-preta).
- **Atores inferidos rotulados:** NLP/ASR e roteamento como inferido-padrão; identidade como inferido-ancorado.
- **Mapa final:** 7 atores + borda + caixa-preta (ver C_mapa_atores.md).
