# Síntese adversarial

> Confronto crítico entre dois relatórios sobre a jornada da URA telefônica do Seguro-Desemprego (Caixa / MTE), horizonte 2024–2026.
> **A1 = `B_relatorio_assistente1.md`** (aparato crítico: advertências + fontes) · **A2 = `B_relatorio_assistente2.md`** (relatório completo: escopo + tabela de 7 atores + notas).
> ⚠️ Assimetria de entrega: A1, como enviado, traz só o aparato crítico e *referencia* "atores 3, 4 e 11" de uma tabela principal **não anexada**. A2 está completo. A comparação de "completude do mapa" é, portanto, parcial.

---

## v1 — primeira leitura (data: 2026-06-03 HH:MM)

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

### Perguntas em aberto que levarei ao /grill-me
- A URA do seguro-desemprego usa NLP/ASR de fato ou é DTMF? Qual fornecedor/contrato sustenta a afirmação de A2?
- Em que ponto da jornada o cidadão é autenticado e por qual sistema (gov.br? base CPF da Dataprev/Serpro?)?
- O transbordo é roteado por *skill-based routing* real (DAC/ACD) ou cai em fila única? A2 afirma o primeiro — com base em quê?
- O dado da CGU (18,6% online) inclui recursos feitos **por telefone/URA** ou só web/app? Isso muda a força da crítica à URA.
- Serpro vs. Dataprev: quem responde por qual parte da consulta de status/parcelas?

---

## v2 — após sessão /grill-me (data: 2026-MM-DD HH:MM)

### Mudanças nesta versão
- **Mudou:** [posição X que eu defendia em v1 → posição Y agora]
  **Gatilho:** [pergunta N do grill-me / nova evidência / resposta que
  contradisse premissa em v1]
- **Novo ator detectado:** [ator Z que não estava em v1]
  **Gatilho:** [como apareceu]
- **Divergência resolvida:** [Divergência 1 de v1 → fechada porque ...]

### Estado atual da síntese (sobrescreve v1)
- Concordância: ...
- Divergências residuais: ...
- Decisão para o mapa em C: ...

---

## v3 — (opcional) após follow-up no assistente 1/2

### Mudanças nesta versão
- ...

