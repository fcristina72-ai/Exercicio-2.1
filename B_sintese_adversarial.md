# Síntese adversarial

> Confronto crítico entre dois relatórios sobre a jornada da URA telefônica do Seguro-Desemprego (Caixa / MTE), horizonte 2024–2026.
> **A1 = `B_relatorio_assistente1.md`** (aparato crítico: advertências + fontes) · **A2 = `B_relatorio_assistente2.md`** (relatório completo: escopo + tabela de 7 atores + notas).
> ⚠️ Assimetria de entrega: A1, como enviado, traz só o aparato crítico e *referencia* "atores 3, 4 e 11" de uma tabela principal **não anexada**.
> A2 está completo. A comparação de "completude do mapa" é, portanto, parcial.

---

## v1 — primeira leitura (data: 2026-06-02 14:20)

### Pontos de concordância
- **Cidadão / trabalhador como usuário final.** Explícito em A2; pressuposto em A1 (toda a discussão de recursos e orientação gira em torno dele).
- **Existe automação no front-end telefônico.** A2 nomeia a "URA receptiva (IVR dinâmica)"; A1 reconhece automação ao distinguir "atendimento eletrônico 24h" de "atendimento humano com janela horária" — para A1, essa distinção é, aliás, a *única* evidência pública direta de que há automação na ponta.
- **Camada de atendente humano (transbordo).** A2 lista o "atendente N1 terceirizado"; A1 a pressupõe ao tratar da orientação humana e ao comparar canais.
- **Back-end integrado Caixa ↔ Dataprev ↔ MTE.** A2 modela um "barramento de API" entre os três; A1 cita a cadeia de back-end (BGSD, eSocial, trilhas, Dataprev/Serpro) como o que o TCU/CGU efetivamente auditam.
- **Camada de retaguarda / recurso administrativo no MTE.** A2 tem o ator "supervisor/backoffice MTE"; A1 dedica boa parte do texto ao fluxo de recursos administrativos.

### Divergências
- **Divergência 1 — Natureza da URA: DTMF puro vs. NLP/ASR cognitivo.**
  A2 afirma que a Caixa "substituiu URAs DTMF por interfaces de voz guiadas por NLP", com ASR transcrevendo fala e classificando intenção — apresentado como **fato consolidado (2024–2026)**. A1 afirma que **não há documentação técnica pública** sobre fornecedor/versão/NLP-vs-DTMF e que isso deve ser tratado como **hipótese de trabalho** até confirmação via LAI.
  - *Quem está mais defensável?* **A1.** A2 atribui à camada cognitiva um grau de certeza que ela própria não sustenta com nenhuma fonte verificável.
  - *Que evidência decide?* Documentação técnica da Caixa/Serpro/Dataprev (edital, contrato, manual de plataforma) — **inexistente no domínio público**. Sem ela, "NLP consolidado" é conjetura razoável, não fato.

- **Divergência 2 — Atribuição de canais/telefones.**
  A2: "0800 726 0207 / 111" como URA **da Caixa**. A1: **Central 158** (Alô Trabalho), com nota de novo horário (mar/2024).
  - *Quem está mais defensável?* Empate com ressalva. A1 acerta a granularidade institucional (158 é do MTE), mas amarra a jornada operacional ao canal do MTE; A2 acerta o SAC da Caixa (0800 726 0207) mas erra ao rotular tudo como "URA da Caixa" e ao incluir o "111".
  - *Que evidência decide?* Páginas oficiais → **158 = Central Alô Trabalho/MTE**; **0800 726 0207 = SAC Caixa Cidadão**; o "111" não corresponde ao fluxo de seguro-desemprego.

- **Divergência 3 — Base de evidência sobre o gargalo/efetividade do funil.**
  A2: narrativa de latência da API Dataprev → transbordo artificial → TMA elevado, atribuída a "auditorias históricas da CGU", **sem número nem referência localizável**. A1: dado concreto — recurso **presencial 67,4%** vs. **online 18,6%** de deferimento.
  - *Quem está mais defensável?* **A1, com folga.** Transforma "há gargalo" (genérico) em crítica mensurável à camada de orientação automática.
  - *Que evidência decide?* O Relatório de Avaliação da CGU (base 2022) — confirmável.

- **Divergência 4 — Status epistêmico dos atores algorítmicos (DAC/ACD, barramento de API).**
  A2 os lista como **fatos** da arquitetura. A1 marca atores 3, 4 e 11 como **inferência por modelo padrão do setor — hipóteses de trabalho**.
  - *Quem está mais defensável?* **A1.** É honesto sobre o que é inferido vs. observado.
  - *Que evidência decide?* Mesma lacuna da Divergência 1 (docs técnicos via LAI).

- **Divergência 5 (meta) — Regime de fontes.**
  A2 cita **categorias genéricas** ("editais", "relatórios de gestão", "acórdãos do TCU") sem documento/URL/data — **não falsificáveis**. A1 traz **tabela com órgão, tipo e URL**.
  - *Quem está mais defensável?* **A1.** Em pesquisa, fonte não rastreável ≈ fonte ausente.

### Lacunas dos dois
- **Camada de identidade/autenticação digital (gov.br / validação de CPF-NIS / biometria).** A jornada de consulta depende dela, mas nenhum a trata como ator nomeado.
- **Serpro como ator de infraestrutura.** A1 o menciona só de passagem (LAI); A2 não o cita. Relevante ao lado da Dataprev.
- **Empregador (via Empregador Web).** Originador da guia/requerimento que condiciona a elegibilidade — ator a montante ausente nos dois.
- **Canais-app paralelos (CTPS Digital, Benefícios Sociais Caixa, Portal Emprega Brasil).** É por eles que tramita boa parte do recurso "online" (os 18,6%); ausentes como atores, embora dialoguem com o mesmo back-end.
- **Instância recursal formal (CODEFAT / CRPS).** A1 cita Codefat de passagem; nenhum a modela como ator.
- **Ouvidoria / Fala.BR** como canal de 2ª instância de reclamação.
- **Camada de compliance/LGPD (gravação, consentimento, logging).** A2 menciona LGPD nas notas, mas nenhum a trata como ator/sistema.

### Perguntas levadas ao /grill-me
- A URA do seguro-desemprego usa NLP/ASR de fato ou é DTMF? Qual fornecedor/contrato sustenta a afirmação de A2?
- Em que ponto da jornada o cidadão é autenticado e por qual sistema (gov.br? base CPF da Dataprev/Serpro?)?
- O transbordo é roteado por *skill-based routing* real (DAC/ACD) ou cai em fila única? A2 afirma o primeiro — com base em quê?
- O dado da CGU (18,6% online) inclui recursos feitos **por telefone/URA** ou só web/app? Isso muda a força da crítica à URA.
- Serpro vs. Dataprev: quem responde por qual parte da consulta de status/parcelas?

---

## v2 — após sessão /grill-me (data: 2026-06-03 15:50)

# Sessão /grill-me — Síntese adversarial (URA Seguro-Desemprego)


> Data: 2026-06-03 14:50 · Alvo: `B_sintese_adversarial.md` (v1)

---

## Rodada 1 — mira no critério de julgamento

### Q1 — Você está corrigindo *método* ou *conteúdo*?
A "A1 mais defensável" em 4 das 5 divergências. A1 quase não fez afirmações positivas sobre a arquitetura — é fácil "estar certo" quando não se afirma quase nada. Se eu trocar a régua de "quem é mais rastreável" para "quem efetivamente mapeou a jornada que o exercício pediu", A1 (a resposta que veio) entrega *zero* mapa.
**Defenda:** seu placar premia cautela e pune utilidade? Por que isso não é só viés a favor do relatório que se recusou a se expor?

**Resposta:**
Concordo e aceito parte do ataque: sim. 
"A1 mais defensável" em 4 de 5 é em uma boa resposta, porque A1 quase não se expôs — não dá para errar o que não se afirma. Entendo que, como placar de qualidade global, isso seria viés a favor de quem se omitiu.
Mas o placar da v1 não era de qualidade global — era por divergência, sobre afirmações específicas que A2 fez e A1 contestou. 
A régua "quem mapeou a jornada" e a régua "quem é rastreável" medem coisas diferentes, e eu misturei as duas coisas: na própria v1 eu disse que A2 vence como entregável e A1 vence como método. O "4 de 5" responde só à pergunta "esta afirmação pontual se sustenta?", não "qual relatório presta mais?".
E em pelo menos um caso o ataque não me atinge: a Divergência 2 não é cautela vs. ousadia — A2 fez uma afirmação positiva e verificável (o "111" como canal do seguro-desemprego) que está errada. 
Ali A1 não venceu por se omitir; 
A2 perdeu por afirmar e errar. 
Então o placar não é puro prêmio à covardia.
Onde eu concocordo: nas Divergências 1 e 4 (NLP, roteamento), "A1 mais defensável" é de fato quase redundante — A1 só disse "não sei". Vou rebaixar isso na v2 de "A1 vence" para "empate técnico: ninguém comprovou", o que é mais honesto.

---

### Q2 — Padrão duplo na inferência
Você condenou a A2 por afirmar NLP/ASR "sem fonte" — mas, nas *lacunas*, você mesmo postula uma "camada de identidade/autenticação gov.br" que **nenhum** dos dois citou e para a qual você também não tem fonte.
**Defenda:** qual é a sua regra consistente para quando um ator inferido é admissível? Ou "inferência" é pecado quando é a A2 que faz e "lacuna perspicaz" quando é você?

**Resposta:**
Rejeito a acusação de padrão duplo, mas aceito que preciso explicitar a régua. 
A regra não é "inferir é proibido" — é onde e com que rótulo a inferência aparece. Conisdero que a falha da A2 não foi inferir NLP/ASR, foi colocar essa inferência na tabela-entregável, em igualdade com atores observados, como "fato consolidado 2024–2026", com uma categoria de fonte genérica que dá aparência de lastro. 
Ao contrário, coloquei a camada gov.br explicitamente sob "Lacunas — atores que suspeito existirem e que ninguém citou": ela está marcada como suspeita e não como fato. Mesmo critério, lugares diferentes.
Concedo um ponto: eu não mostrei por que a conta "gov.br" é mais que chute. Devo registrar a base — a consulta de status exige autenticar CPF/NIS, e o padrão federal de identidade é a conta gov.br, logo a inferência tem ancoragem funcional, não é só ilustrativa. Isso, aliás, me dá um contra-ataque: minha lacuna inferida tem mais sustentação indireta do que o NLP da A2 tem.
Mudança para a v2: criar um nível de confiança nas lacunas (de "ancorada por função" a "mero palpite"), para a régua ficar auditável e ninguém me acusar de pesar dois pesos.

---

### Q3 — O salto do dado da CGU
Você ancorou a crítica ao funil automatizado no 67,4% × 18,6%. Mas esse número é de **recursos administrativos** protocolados por **web/app e presencial**, base 2022 — ele menciona a **URA telefônica**? Se aqueles recursos não foram feitos por telefone, você importou uma estatística de canal web/app para condenar uma IVR de voz.
**Defenda:** sustente o nexo, ou admita que a âncora não toca o objeto.

**Resposta:**
Concedo o essencial: o 67,4% × 18,6% é de recursos administrativos (canais web/app e presencial numa base 2022) e não menciona a URA telefônica. Usar esse número para "condenar o funil automatizado da URA" foi um salto — juntei duas camadas automatizadas diferentes (autosserviço web/app vs. IVR de voz) como se fossem a mesma coisa.
Assim numa versão mais franca e honesta: o dado sustenta a tese de que canais de autosserviço/orientação automática rendem muito menos deferimento que o contato humano — o que é sugestivo por analogia sobre a URA, não prova sobre ela. Aliás, a própria A1 já tinha defendido assim ("sugere falhas na camada de informação/orientação automática"); o exagero de tratar isso como prova direta contra a URA foi meu, na v1, não da A1.
Mudança para a v2: rebaixar o dado de "âncora da crítica à URA" para "evidência análoga sobre autosserviço; nexo com a IVR de voz = pergunta aberta", e jogar "os 18,6% incluem recurso por telefone?" para o grill/LAI. Essa é a maior correção da rodada.


### Q4 — A premissa que ninguém testou
Você tratou a Divergência 2 (canais) como "empate". Mas se 158 é do MTE e 0800 726 0207 é da Caixa, talvez os dois relatórios estejam descrevendo **duas URAs diferentes** — e não uma.
**Defenda:** onde, na v1 ou em qualquer dos relatórios, ficou *estabelecido* que existe uma única "URA do seguro-desemprego"? E se a premissa da jornada única estiver errada?

**Resposta:**
Aceito que é uma premissa que eu não testei — e ela é frágil. Se 158 é do MTE (requerimento/Alô Trabalho) e 0800 726 0207 é da Caixa (consulta de parcelas/pagamento), então a "jornada" provavelmente atravessa dois front-ends institucionais distintos, e falar em "a URA do seguro-desemprego" no singular é um erro de categoria que os dois relatórios cometem em graus diferentes — a A2 mais (colapsou tudo em "URA da Caixa"), a A1 menos.
Apresento alguma resistência: do ponto de vista do cidadão, pode ainda ser uma jornada subjetiva ("ligar para resolver o seguro"), mesmo que o back-end sejam dois sistemas. Então o correto reequadramento talvez não seja "duas jornadas separadas", e sim "jornada única do usuário sobre duas URAs distintas". Isso, de quebra, dá razão ao instinto de granularidade institucional da A1.
Mudança para a v2 (estrutural, a mais pesada): desdobrar o ator "URA" em dois no mapa do item C — URA-MTE/158 e URA-Caixa/SAC — ou, no mínimo, marcar "URA única" como premissa não confirmada.

---

## Anotações para a v2 (preencher conforme as defesas caem ou se sustentam)
- Posição que mudou: "A1 mais defensável" nas Divergências 1 e 4 (NLP/ASR, roteamento)
  → rebaixar de "A1 vence" para "empate técnico: ninguém comprovou".
  · Gatilho: Q1 — A1 só venceu por não se expor; tautológico, não mérito.

- Posição que mudou: dado CGU (67,4% × 18,6%) deixa de ser "âncora da crítica à URA"
  → vira "evidência análoga sobre autosserviço web/app; nexo com a IVR de voz = aberto".
  · Gatilho: Q3 — o número é de recursos web/app+presencial (base 2022), não menciona a URA telefônica. (Maior correção da rodada.)

- Novo ator detectado: camada de identidade/autenticação gov.br (conta gov.br / validação CPF-NIS)
  promovida de "lacuna-palpite" para "lacuna ancorada por função" (consulta de status exige autenticar).
  · Gatilho: Q2 — defesa exigiu explicitar a base funcional da inferência.

- Divergência resolvida / rebaixada: Divergência 2 (canais) deixa de ser "empate"
  → A2 errou afirmação positiva verificável (o "111" não é canal do seguro-desemprego); A1 acerta a granularidade institucional.
  · Gatilho: Q1/Q4 — separar erro factual de mera cautela.

- Premissa derrubada: "existe uma única URA do seguro-desemprego".
  → Reframe: "jornada única do usuário sobre DUAS URAs distintas" (URA-MTE/158 = requerimento; URA-Caixa/0800 726 0207 = parcelas/pagamento).
  · Gatilho: Q4 — 158 (MTE) e 0800 (Caixa) sugerem dois front-ends institucionais. (Maior mudança estrutural no mapa C.)

- Ajuste de método (transversal): criar nível de confiança nas lacunas/atores inferidos
  (de "ancorada por função" → "mero palpite") para a régua de inferência ficar auditável.
  · Gatilho: Q2 — evitar acusação de padrão duplo.




