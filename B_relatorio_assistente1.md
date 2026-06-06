# Relatório — Assistente 1

- **Ferramenta:** Gemini 2.x 
- **Data:** 2026-05-29
- **Prompt usado:** ver `A_meta_prompt.md`

## 1. Escopo e postura metodológica

Este relatório mapeia os atores (humanos, de IA e automatizados) que participam da jornada telefônica do Seguro-Desemprego, do momento em que o trabalhador disca para um canal oficial até a resolução do pleito (autoatendimento) ou o encaminhamento (transbordo humano / abertura de recurso administrativo). O horizonte é o estado atual (2024–2026).

A postura adotada aqui é deliberadamente **cética e rastreável**: cada ator é classificado por nível de evidência — *confirmado* (fonte oficial direta), *inferido-ancorado* (função inescapável, ainda que sem documentação do sistema específico) ou *inferido-padrão* (presumido por ser arranjo típico do setor de contact center). O objetivo é não apresentar como fato o que é, na verdade, hipótese de trabalho. Essa disciplina importa porque a camada de telefonia do Seguro-Desemprego é uma **zona de baixa transparência documental**, e tratar inferência como evidência produziria um mapa bonito e falso.

## 2. Tabela de mapeamento de atores

| # | Ator | Tipo | Papel na jornada | Nível de evidência |
| :-- | :-- | :-- | :-- | :-- |
| 1 | Cidadão (trabalhador) | Humano | Usuário final; busca elegibilidade, calendário, parcelas, motivo de bloqueio. | Confirmado |
| 2 | Canal telefônico do serviço (Central 158 / Alô Trabalho) | IA/Automatizado | Porta de entrada de dúvidas e teleatendimento do Seguro-Desemprego, vinculado ao MTE. | Confirmado |
| 3 | URA receptiva / atendimento eletrônico | IA/Automatizado | Saudação, triagem e menu inicial. **A distinção entre atendimento eletrônico 24h e atendimento humano com janela horária é a única evidência pública direta de que há automação no front-end.** | Inferido-ancorado |
| 4 | Camada de reconhecimento de voz / NLP | IA | Suposta interpretação de fala/intenção. Não há documentação pública (fornecedor, versão, NLP vs. DTMF). | Inferido-padrão |
| 5 | Motor de roteamento / distribuição de chamadas | Automatizado | Distribui a chamada por regra de negócio e habilidade. | Inferido-padrão |
| 6 | Camada de autenticação de identidade (CPF/NIS) | Automatizado | Valida o cidadão antes de expor dados sensíveis; função inescapável. | Inferido-ancorado |
| 7 | Barramento de integração (consulta de status) | Automatizado | Consulta as bases de governo para retornar status/parcelas. | Confirmado-função |
| 8 | Atendente de teleatendimento (Nível 1) | Humano | Atendimento humanizado para casos complexos e orientação sobre recursos. | Confirmado |
| 9 | Operadora de pagamento (Caixa Econômica Federal) | Humano/Automatizado | Executa o pagamento do benefício concedido (conta, cartão cidadão, agência). | Confirmado |
| 10 | Backoffice / análise de recurso administrativo (MTE) | Humano | Analisa recursos quando o problema não se resolve por telefone. | Confirmado |
| 11 | Sistema de back-end de benefícios (Dataprev / eSocial / Serpro) | Automatizado | Processa elegibilidade e mantém as trilhas auditadas por TCU/CGU. | Confirmado (sistema) / Inferido (papel exato) |

## 3. Advertências sobre evidências

**Zonas de opacidade relevantes para pesquisa:**

- A Caixa não publicou documentação técnica sobre a arquitetura da URA (fornecedor, versão, capacidade de NLP/ASR vs. DTMF puro). A distinção entre atendimento eletrônico 24h e humano com janela horária é a única evidência pública direta de que há automação no front-end. Relatórios de TCU e CGU cobrem a cadeia de back-end (BGSD, eSocial, trilhas), não a camada de telefonia.

- O TCU abriu questionário em outubro/2025 especificamente para mapear a jornada digital do seguro-desemprego — resultado ainda não publicado como acórdão até o horizonte coberto (2024–2026).

- A CGU constatou que recursos presenciais têm taxa de deferimento quase quatro vezes maior (67,4%) do que recursos online (18,6%), o que sugere falhas na camada de informação/orientação automática — dado relevante para criticar a efetividade dos atores de IA no funil. [eaud.cgu.gov.br/relatorios/download/1421234, mai/2024]

- Papéis dos atores 3, 4 e 11 são inferidos por evidências indiretas e modelo arquitetural padrão do setor; **devem ser tratados como hipóteses de trabalho** até confirmação por documentação técnica da Caixa ou Serpro/Dataprev obtida via LAI (Lei de Acesso à Informação).

- Não há confirmação pública de que a URA do Seguro-Desemprego utilize chatbot de transbordo cognitivo ou roteamento por habilidade (skill-based). Esses elementos foram mantidos no mapa apenas como inferência-padrão, explicitamente rotulada.

## 4. Fontes utilizadas

| Fonte | Tipo | URL |
|-------|------|-----|
| gov.br — Solicitar o Seguro-Desemprego (confirma canal 158) | Oficial | https://www.gov.br/pt-br/servicos/solicitar-o-seguro-desemprego |
| Caixa Econômica Federal — Seguro-Desemprego (perguntas frequentes) | Oficial | https://www.caixa.gov.br/beneficios-trabalhador/seguro-desemprego/Paginas/perguntas-frequentes.aspx |
| Portal FAT/MTE — Seguro-Desemprego | Oficial | https://portalfat.mte.gov.br |
| CGU — Relatório de Avaliação Seguro-Desemprego (mar/2024) | Auditoria oficial | https://eaud.cgu.gov.br/relatorios/download/1421234 |
| TCU — Auditorias sobre o Seguro-Desemprego e fragilidades eSocial/Dataprev | Auditoria oficial | https://portal.tcu.gov.br |
| IBGE/CES — Metadados Seguro-Desemprego/MTE | Oficial | https://ces.ibge.gov.br |

## 5. Análise crítica do funil de atendimento

A leitura conjunta das auditorias disponíveis sugere que o ponto mais frágil da jornada não está na interface com o cidadão, e sim na dependência do front-end em relação ao back-end de benefícios. Quando a consulta de status precisa atravessar as bases de governo e essas bases apresentam latência ou indisponibilidade, a camada automatizada perde a capacidade de responder e tende a transferir a chamada para o atendimento humano. Esse transbordo, frequentemente, não decorre da complexidade real do caso, mas da incapacidade momentânea do sistema de recuperar a informação — um transbordo artificial que infla a fila humana e eleva o tempo médio de atendimento.

A estatística da CGU reforça essa hipótese por analogia: se os canais de autosserviço e orientação automática (web e aplicativo) produzem taxas de deferimento de recurso muito inferiores às do contato presencial, é plausível que a camada de orientação automática como um todo — incluindo a telefônica — falhe em conduzir o cidadão à informação correta. Essa inferência, contudo, deve ser tratada com cautela: o dado da CGU mede recursos protocolados por web, aplicativo e presencialmente, e não menciona explicitamente a URA telefônica. Usá-lo como prova direta contra a URA de voz seria um salto indevido entre camadas distintas de automação.

## 6. Recomendação de fechamento

O mapa só deve ser considerado validado após uma consulta via LAI à Caixa e à Dataprev/Serpro que esclareça (a) se a URA usa NLP/ASR ou DTMF puro, (b) qual sistema autentica o CPF/NIS na ligação e (c) se os recursos contabilizados pela CGU incluem protocolos feitos por telefone. Até lá, os atores 3, 4 e 11 permanecem como hipóteses de trabalho — úteis para desenhar a jornada, insuficientes para afirmá-la. A honestidade epistêmica, neste caso, é parte do método: um mapa que sinaliza as próprias incertezas é mais útil para auditoria e pesquisa do que um mapa que as esconde sob aparência de completude.
