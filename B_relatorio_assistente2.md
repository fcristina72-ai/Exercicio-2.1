# Mapeamento de Atores e Sistemas: Jornada da URA do Seguro-Desemprego (Caixa Econômica Federal)

## 1. Escopo e Horizonte Temporal
* **Serviço:** Atendimento ao Seguro-Desemprego
* **Canal:** URA Telefônica da Caixa Econômica Federal (ex: 0800 726 0207 / 111)
* **Jornada:** Do momento em que o cidadão disca e estabelece a conexão telefônica até a resolução do pleito (autoatendimento) ou encaminhamento (transbordo para atendimento humano / abertura de recurso).
* **Horizonte Temporal:** Estado Atual (2024–2026), caracterizado pela consolidação de interfaces cognitivas e integração de barramentos de API em tempo real.

---

## 2. Tabela de Mapeamento de Atores (Humanos e de Inteligência Artificial)

| Ator | Tipo (Humano/IA) | Papel na jornada | Ponto de entrada | Ponto de saída | Evidência/Fonte |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Cidadão (Trabalhador)** | Humano | Usuário final do serviço. Busca informações sobre elegibilidade, datas de pagamento, parcelas liberadas ou motivos de bloqueio/notificação do benefício. | Discagem para o canal telefônico oficial da Caixa. | Resolução da dúvida via autoatendimento, transferência para operador humano ou desligamento. | Manuais de Atendimento ao Cidadão (MTE/gov.br); Relatórios de Ouvidoria da Caixa Econômica Federal. |
| **URA Receptiva (IVR Dinâmica)** | IA / Automatizado | Saudação inicial, triagem de segurança eletrônica e apresentação do menu de opções estruturado por DTMF (teclado) ou comando de voz. | Conexão telefônica da chamada na plataforma de contact center da Caixa. | Direcionamento para a árvore de autoatendimento específica do Seguro-Desemprego ou fila humana. | Editais de Licitação de Teleatendimento da Caixa Econômica Federal; Relatórios de Gestão da CEF. |
| **Modelo de Reconhecimento de Voz e NLP (Processamento de Linguagem Natural)** | IA | Transcreve a fala do cidadão (ASR) e interpreta a intenção (ex: "quero saber por que meu seguro está bloqueado") para evitar menus longos. | Interação inicial após a saudação da URA (quando ativado o modo cognitivo). | Classificação da intenção do usuário e envio do comando para o motor de roteamento. | Planos de Transformação Digital da CEF (2024-2026); Especificações técnicas de plataformas de IA conversacional contratadas. |
| **Motor de Regras de Roteamento Algorítmico (DAC / ACD)** | Automatizado / Algorítmico | Distribui a chamada com base em regras de negócio (ex: CPF com indício de fraude vai para fila especializada) e habilidades (skill-based routing) dos atendentes. | Conclusão da triagem dos dados ou solicitação explícita de falar com um atendente. | Entrega da chamada na tela e no headset do operador humano disponível e qualificado. | Relatórios de Auditoria do TCU sobre a eficiência dos canais de atendimento e contratação de consórcios de contact center pela CEF. |
| **Barramento de Integração API (Caixa ↔ Dataprev ↔ MTE)** | Automatizado | Realiza a consulta automatizada em tempo real nas bases do governo para verificar o status da habilitação e parcelas do benefício. | Entrada do CPF/NIS validado pelo cidadão na URA ou digitado pelo atendente. | Retorno dos dados estruturados na URA (sintetizados em áudio) ou na tela do sistema do atendente. | Acordo de Cooperação Técnica MTE/Caixa/Dataprev; Relatórios de fiscalização da CGU sobre o pagamento de benefícios sociais. |
| **Atendente de Teleatendimento (Nível 1 / Terceirizado)** | Humano | Presta atendimento humanizado para esclarecer dúvidas complexas, erros de cruzamento de dados (ex: percepção de renda própria) ou orientar sobre recursos. | Recebimento do transbordo da URA na fila de Seguro-Desemprego. | Registro do histórico do atendimento no CRM/Sistema da Caixa e encerramento da chamada. | Contratos de prestação de serviços de telesserviço ativos da Caixa (Portal de Compras Governamentais); Acórdãos do TCU sobre a qualidade do atendimento terceirizado. |
| **Supervisor / Backoffice de Retaguarda (MTE / Dataprev)** | Humano | Analisa recursos administrativos de Seguro-Desemprego inseridos no sistema quando o problema não pode ser resolvido por telefone (ex: divergência no Codefat). | Entrada do pedido de recurso ou contestação aberto via sistema (orientado pelo atendente ou app). | Atualização do status do recurso no sistema do MTE, liberando ou indeferindo o pagamento. | Portarias Normativas do MTE sobre o fluxo de análise de Recursos Administrativos do Seguro-Desemprego. |

---

## 3. Notas Técnicas e Recomendações Operacionais

1. **Gargalo de Integração (Fricção na Jornada):** A maior fricção na jornada (identificada em auditorias históricas da CGU) ocorre quando a API da Dataprev apresenta latência ou instabilidade. O sistema automatizado (URA) falha em ler o status real do benefício, gerando um transbordo massivo e artificial para o atendimento humano (Atendente Nível 1), sobrecarregando a operação e elevando o Tempo Médio de Atendimento (TMA).
2. **Arquitetura Cognitiva (2024–2026):** No horizonte atual, a Caixa Econômica Federal intensificou a substituição de URAs puramente baseadas em árvore de discagem fixa (DTMF) por interfaces de voz guiadas por Modelos de Linguagem Natural (NLP). O objetivo estratégico é reter o cidadão na camada automatizada para consultas recorrentes (como calendário de saques e liberação de parcelas), reservando o elemento humano para contestações complexas.
3. **Segurança e Validação de Identidade:** A URA opera como primeira camada de mitigação de fraudes, utilizando cruzamento algorítmico de dados cadastrais antes de expor dados sensíveis do Seguro-Desemprego, em estrita conformidade com a LGPD e normativas do TCU.
