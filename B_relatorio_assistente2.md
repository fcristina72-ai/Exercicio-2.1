# Mapeamento de Atores e Sistemas: Jornada da URA do Seguro-Desemprego (Caixa Econômica Federal / MTE)

## 1. Escopo e Horizonte Temporal
* **Serviço:** Atendimento ao Seguro-Desemprego.
* **Canal:** Atendimento telefônico do benefício — Central 158 (Alô Trabalho, vinculada ao Ministério do Trabalho e Emprego) para dúvidas e teleatendimento, e canais da Caixa Econômica Federal (SAC e Caixa Cidadão) para a etapa de pagamento e consulta de parcelas.
* **Jornada:** Do momento em que o cidadão disca e estabelece a conexão telefônica até a resolução do pleito (autoatendimento) ou o encaminhamento (transbordo para atendimento humano / abertura de recurso administrativo).
* **Horizonte Temporal:** Estado atual (2024–2026), caracterizado pela consolidação de interfaces cognitivas e pela integração de barramentos de API em tempo real entre Caixa, Dataprev e MTE.

---

## 2. Tabela de Mapeamento de Atores (Humanos e de Inteligência Artificial)

| Ator | Tipo (Humano/IA) | Papel na jornada | Ponto de entrada | Ponto de saída | Evidência/Fonte |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Cidadão (Trabalhador)** | Humano | Usuário final do serviço. Busca informações sobre elegibilidade, datas de pagamento, parcelas liberadas ou motivos de bloqueio/notificação do benefício. | Discagem para o canal telefônico oficial (Central 158 / canais da Caixa). | Resolução da dúvida via autoatendimento, transferência para operador humano ou desligamento. | Página oficial do serviço no gov.br, que indica o teleatendimento 158. |
| **URA Receptiva (IVR Dinâmica)** | IA / Automatizado | Saudação inicial, triagem de segurança eletrônica e apresentação do menu de opções estruturado por DTMF (teclado) ou comando de voz. | Conexão telefônica da chamada na plataforma de contact center. | Direcionamento para a árvore de autoatendimento específica do Seguro-Desemprego ou fila humana. | Sistema de Licitações da Caixa (pregões de teleatendimento). |
| **Modelo de Reconhecimento de Voz e NLP** | IA | Transcreve a fala do cidadão (ASR) e interpreta a intenção (ex.: "quero saber por que meu seguro está bloqueado") para evitar menus longos. | Interação inicial após a saudação da URA, quando ativado o modo cognitivo. | Classificação da intenção do usuário e envio do comando para o motor de roteamento. | Planos de transformação digital do setor de contact center; especificações de plataformas de IA conversacional contratadas. |
| **Motor de Regras de Roteamento (DAC / ACD)** | Automatizado / Algorítmico | Distribui a chamada com base em regras de negócio (ex.: indício de fraude vai para fila especializada) e em habilidades (skill-based routing) dos atendentes. | Conclusão da triagem dos dados ou solicitação explícita de falar com um atendente. | Entrega da chamada na tela e no headset do operador humano disponível e qualificado. | Boas práticas de operação de centrais de atendimento; relatórios de gestão de canais. |
| **Barramento de Integração API (Caixa ↔ Dataprev ↔ MTE)** | Automatizado | Realiza a consulta automatizada em tempo real nas bases do governo para verificar o status da habilitação e das parcelas do benefício. | Entrada do CPF/NIS validado pelo cidadão na URA ou digitado pelo atendente. | Retorno dos dados estruturados na URA (sintetizados em áudio) ou na tela do sistema do atendente. | Acordo de cooperação técnica entre MTE, Caixa e Dataprev para pagamento de benefícios. |
| **Atendente de Teleatendimento (Nível 1)** | Humano | Presta atendimento humanizado para esclarecer dúvidas complexas, erros de cruzamento de dados (ex.: percepção de renda própria) ou orientar sobre recursos. | Recebimento do transbordo da URA na fila de Seguro-Desemprego. | Registro do histórico do atendimento no sistema e encerramento da chamada. | Contratos de prestação de serviços de teleatendimento; perguntas frequentes da Caixa. |
| **Operadora de Pagamento (Caixa Econômica Federal)** | Humano / Automatizado | Disponibiliza o pagamento do benefício concedido (conta, cartão cidadão, agência ou lotérica). | Concessão do benefício pelo MTE e ordem de pagamento. | Crédito disponibilizado ao trabalhador. | Página da Caixa sobre o Seguro-Desemprego. |
| **Backoffice de Retaguarda (MTE / Dataprev)** | Humano | Analisa recursos administrativos quando o problema não pode ser resolvido por telefone (ex.: divergência cadastral). | Entrada do pedido de recurso ou contestação aberto via sistema. | Atualização do status do recurso, liberando ou indeferindo o pagamento. | Normas do MTE sobre o fluxo de recursos administrativos do Seguro-Desemprego. |

---

## 3. Notas Técnicas e Recomendações Operacionais

1. **Gargalo de Integração (Fricção na Jornada):** A maior fricção da jornada ocorre quando o barramento de integração apresenta latência ou instabilidade ao consultar as bases de governo. O sistema automatizado (URA) falha em ler o status real do benefício, gerando transbordo massivo e artificial para o atendimento humano e elevando o Tempo Médio de Atendimento (TMA). A causa-raiz costuma ser externa ao canal telefônico, residindo na disponibilidade das bases de back-end.

2. **Arquitetura Cognitiva (2024–2026):** No horizonte atual, o setor de teleatendimento público vem substituindo URAs puramente baseadas em árvore de discagem fixa (DTMF) por interfaces de voz guiadas por modelos de linguagem natural (NLP). O objetivo estratégico é reter o cidadão na camada automatizada para consultas recorrentes (como calendário de saques e liberação de parcelas), reservando o elemento humano para contestações complexas.

3. **Segurança e Validação de Identidade:** A URA opera como primeira camada de mitigação de fraudes, utilizando cruzamento de dados cadastrais (CPF/NIS) antes de expor dados sensíveis do Seguro-Desemprego, em conformidade com a LGPD.

4. **Distinção de canais:** É importante separar os papéis institucionais. A Central 158 (Alô Trabalho) é o canal de teleatendimento do Ministério do Trabalho e Emprego, indicado na própria página oficial do serviço para dúvidas, reclamações e sugestões. A Caixa Econômica Federal atua como operadora financeira do benefício — responsável pelo pagamento, pela consulta de parcelas e pelo atendimento ao correntista.

---

## 4. Fontes

| Fonte | Tipo | URL |
|-------|------|-----|
| gov.br — Solicitar o Seguro-Desemprego (canal 158) | Oficial | https://www.gov.br/pt-br/servicos/solicitar-o-seguro-desemprego |
| Caixa — Seguro-Desemprego (perguntas frequentes) | Oficial | https://www.caixa.gov.br/beneficios-trabalhador/seguro-desemprego/Paginas/perguntas-frequentes.aspx |
| Caixa — Portal Cidadão (benefícios ao trabalhador) | Oficial | https://cidadao.caixa.gov.br/ |
| Sistema de Licitações da Caixa (pregões de teleatendimento) | Oficial | http://www.licitacoes.caixa.gov.br |
