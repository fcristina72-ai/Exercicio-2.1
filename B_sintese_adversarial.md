# Síntese Adversarial — Comparação de Relatórios sobre a Jornada da URA do Seguro-Desemprego (Caixa/MTE)

> **Objeto:** confronto crítico entre dois relatórios independentes que mapeiam atores humanos e de IA na jornada da URA telefônica do Seguro-Desemprego (Caixa Econômica Federal / MTE), horizonte 2024–2026.
> **Método:** *síntese adversarial* — os dois textos são tratados como peças concorrentes. Em vez de somar conteúdos, cada relatório é usado para interrogar e estressar as afirmações do outro; em seguida, afirmações factuais decisivas são checadas em fontes externas, e só então se propõe um quadro consolidado mais robusto.
> **Artefatos comparados:** `B_relatorio_assistente1.md` (doravante **R1**) e `B_relatorio_assistente2.md` (doravante **R2**).

---

## 0. Nota metodológica e de atribuição

**Atribuição de autoria (Gemini vs. Claude).** O enunciado informa que um relatório foi gerado pelo Gemini e outro pelo Claude, mas os arquivos chegam rotulados apenas como `assistente1` e `assistente2`. Não é possível determinar com certeza, **só pelo conteúdo**, qual modelo produziu qual texto. Por isso, esta síntese se refere a eles por **R1** e **R2** (= ordem dos arquivos), e não por nome de modelo. Há "impressões digitais" estilísticas observáveis (ver §6), mas elas são *indícios*, não prova — a correspondência final cabe a quem conhece a origem de cada arquivo.

**Assimetria de escopo — leitura obrigatória.** Os dois artefatos **não estão no mesmo estágio de entrega**:

- **R2 é um relatório completo:** escopo, horizonte temporal, tabela de mapeamento com 7 atores (entrada/saída/evidência) e notas técnicas com recomendações.
- **R1, tal como enviado, é apenas o aparato crítico:** contém somente as seções "Advertências sobre evidências" e "Fontes utilizadas". O próprio texto faz referência a *"papéis dos atores 3, 4 e 11"*, o que confirma que existe uma **tabela principal de atores que não foi incluída no arquivo**.

Consequência: comparar "completude do mapeamento" entre os dois seria injusto, pois compararíamos um relatório inteiro (R2) com o anexo metodológico de outro (R1). Onde a comparação for afetada por isso, o ponto vem marcado com ⚠️.

---

## 1. Quadro comparativo de alto nível

| Dimensão | R1 (`assistente1`) | R2 (`assistente2`) |
| :--- | :--- | :--- |
| Tipo de entrega | Aparato crítico (advertências + fontes) ⚠️ incompleto | Relatório completo (escopo + tabela + notas) |
| Postura epistêmica | Cética; separa fato de inferência; marca hipóteses | Assertiva; apresenta arquitetura como consolidada |
| Tabela de atores | Ausente no arquivo (referida, não anexada) ⚠️ | Presente, 7 atores, colunas bem definidas |
| Rastreabilidade das fontes | Alta — URLs, datas, órgão emissor | Baixa — categorias genéricas, sem URL/data |
| Tratamento da incerteza | Explícito (zonas de opacidade, LAI, "hipóteses de trabalho") | Implícito/ausente (afirmações categóricas) |
| Dado empírico citável | Sim (estatística da CGU sobre recursos) | Não (nenhum número verificável) |
| Utilidade imediata como produto | Baixa isolada; alta como camada de validação | Alta como entregável pronto |
| Risco de erro não sinalizado | Baixo | Elevado (alegações sem lastro público) |

---

## 2. Eixo central da divergência: completude assertiva vs. ceticismo rastreável

A diferença essencial entre os textos **não é de conteúdo factual**, e sim de **regime de verdade**.

- **R2 opera no registro da entrega:** produz um artefato fechado, taxonomicamente limpo, que "parece pronto". Nomeia subsistemas (DAC/ACD, ASR, NLP, barramento de API Caixa↔Dataprev↔MTE) e afirma uma trajetória — a "consolidação de interfaces cognitivas" em 2024–2026 — como se fosse fato estabelecido.
- **R1 opera no registro da auditoria:** recusa-se a afirmar o que não pode lastrear. Declara explicitamente que a Caixa **não publicou documentação técnica** sobre a arquitetura da URA (fornecedor, versão, NLP/ASR vs. DTMF puro) e que a única evidência pública direta de automação no front-end é a distinção entre atendimento eletrônico 24h e atendimento humano com janela horária.

É exatamente aqui que os dois se atacam.

---

## 3. Confronto direto (cross-examination)

### Round 1 — A "arquitetura cognitiva" da URA

- **R2 afirma:** a Caixa "intensificou a substituição de URAs DTMF por interfaces de voz guiadas por NLP", com ASR transcrevendo a fala e classificando intenção.
- **R1 contesta:** não há documentação técnica pública que confirme NLP/ASR; isso deve ser tratado como **hipótese de trabalho** até confirmação via LAI junto à Caixa/Serpro/Dataprev.
- **Veredito da checagem externa:** a verificação independente **não localizou** documentação técnica da Caixa descrevendo a pilha de IA conversacional da URA do Seguro-Desemprego. As fontes oficiais (Caixa, MTE/Alô Trabalho) confirmam apenas que *"o atendimento eletrônico será automatizado ou por meio de um atendente"* — formulação que não distingue DTMF de NLP. **R1 vence o round:** a afirmação central de R2 é plausível, mas apresentada como fato sem o lastro que ela própria não possui.

### Round 2 — Os canais e números de telefone

- **R2 cita:** "0800 726 0207 / 111" como canal da URA da Caixa.
- **R1 cita:** Central 158 (Alô Trabalho), com nota sobre novo horário (mar/2024).
- **Checagem externa:** ambos tocam canais **reais, porém distintos**. O `0800 726 0207` é o SAC/Caixa Cidadão; a **Central 158 (Alô Trabalho) é do MTE**, não da Caixa, e cobre seguro-desemprego, abono salarial, CAGED etc. O "111" é o canal da Caixa para correntistas via celular, não o fluxo de seguro-desemprego — **R2 conflaciona canais**. Já R1, ao tratar o 158 como o canal principal, mistura a porta de entrada do MTE com a jornada operacional da Caixa (pagamento/consulta de parcelas), que de fato passa pelo SAC da Caixa. **Empate com ressalva:** R2 erra ao rotular tudo como "URA da Caixa"; R1 acerta a granularidade institucional, mas (na parte enviada) não amarra o canal correto a cada etapa.

### Round 3 — Evidência empírica sobre a efetividade do funil automatizado

- **R2 oferece:** uma narrativa de gargalo (latência da API Dataprev → transbordo artificial → TMA elevado), atribuída a "auditorias históricas da CGU", **sem número nem referência localizável**.
- **R1 oferece:** dado concreto e citável — recursos **presenciais** têm taxa de deferimento de **67,4%** contra **18,6%** dos recursos **online**, sugerindo falha na camada de informação/orientação automática.
- **Checagem externa:** o dado de R1 **confere** com o Relatório de Avaliação da CGU (base 2022; 228,7 mil recursos online a 18,6% de deferimento vs. 202,6 mil presenciais a 67,4%). **R1 vence com folga:** transforma uma crítica genérica ("há gargalo") numa crítica mensurável e ancorada, exatamente o tipo de evidência que torna o argumento utilizável em auditoria ou trabalho acadêmico.

### Round 4 — Fontes

- **R2:** lista categorias ("Editais de Licitação", "Relatórios de Gestão", "Acórdãos do TCU") **sem identificar documento, número ou URL**. São fontes *plausíveis* mas **não falsificáveis** — não há como o leitor checar.
- **R1:** tabela com **órgão emissor, tipo e URL**, incluindo a data do relatório da CGU e a menção ao questionário do TCU de out/2025 (com a ressalva honesta de que ainda não virou acórdão).
- **Veredito:** **R1 vence sem disputa.** Em trabalho de pesquisa, fonte não rastreável equivale a fonte ausente.

---

## 4. Auditoria de exatidão factual (com checagem externa)

| Afirmação | Origem | Status após checagem |
| :--- | :--- | :--- |
| Recurso presencial 67,4% vs. online 18,6% (base 2022) | R1 | ✅ Confere com Relatório CGU 1421234 |
| Caixa não publicou arquitetura técnica da URA | R1 | ✅ Não foi encontrada documentação pública que a contrarie |
| TCU abriu questionário sobre jornada digital do SD (out/2025), sem acórdão publicado | R1 | ⚠️ Plausível e coerente; tratar como pendente de confirmação |
| URA da Caixa migrou para NLP/ASR (consolidado 2024–2026) | R2 | ⚠️ Não confirmado por fonte pública; apresentado como fato |
| Número "0800 726 0207 / 111" como URA do seguro-desemprego | R2 | ⚠️ Parcial: 0800 726 0207 = SAC Caixa; 158 = MTE; "111" não é o fluxo correto |
| Gargalo por latência da API Dataprev gera transbordo | R2 | ⚠️ Mecanismo verossímil, porém sem fonte citável |

Leitura: **nenhuma afirmação de R1 foi refutada**; várias de R2 são razoáveis como modelo, mas circulam **sem o lastro que as sustente** e com pelo menos um erro de atribuição de canal.

---

## 5. Forças e fraquezas (placar)

**R1 — forças:** honestidade epistêmica; separação explícita entre fato e inferência; fontes rastreáveis; o único dado quantitativo verificável de toda a comparação; consciência das "zonas de opacidade" e caminho prático (LAI) para fechá-las.
**R1 — fraquezas:** ⚠️ entrega incompleta (a tabela de atores não veio no arquivo); isolado, não serve como produto final; pouco útil para quem precisa do mapeamento operacional pronto.

**R2 — forças:** entregável completo e bem estruturado; taxonomia de atores clara e didática (entrada/saída/papel); cobre a cadeia ponta a ponta (cidadão → URA → NLP → roteamento → API → atendente → backoffice); bom como **andaime** inicial.
**R2 — fraquezas:** excesso de confiança; arquitetura especulativa apresentada como fato; fontes não falsificáveis; erro de atribuição de canal; ausência de qualquer número verificável; nenhuma sinalização de incerteza — o leitor desavisado tomaria hipóteses por evidência.

---

## 6. Impressões digitais estilísticas (indício, não prova)

Sem afirmar autoria, observam-se dois "temperamentos" de redação:

- **R1** exibe o padrão de *pesquisa cautelosa*: hedging explícito, vocabulário de auditoria ("hipóteses de trabalho", "zonas de opacidade"), recomendação de instrumento legal (LAI), e fontes com URL/data. Prioriza **não errar** sobre **parecer completo**.
- **R2** exibe o padrão de *entrega confiante*: tabela exaustiva e simétrica, terminologia técnica densa, narrativa fechada e fontes em categorias genéricas. Prioriza **completude e fluência** sobre **rastreabilidade**.

Quem conhece a origem dos arquivos pode mapear esses perfis aos modelos; aqui ficam apenas como observação de estilo.

---

## 7. Síntese consolidada (o quadro mais robusto)

Os dois relatórios são **complementares, não substitutos**. O produto ideal combina o **esqueleto de R2** com o **rigor probatório de R1**:

1. **Manter a taxonomia de atores de R2** (cidadão, URA receptiva, camada de NLP/ASR, roteamento DAC/ACD, barramento de API Caixa↔Dataprev↔MTE, atendente N1, backoffice/recurso) **como modelo arquitetural padrão do setor** — porém **reclassificando** os atores não confirmados (NLP/ASR, roteamento algorítmico, barramento) de "fato" para **"inferência — hipótese de trabalho"**, conforme R1 já recomenda para os atores 3, 4 e 11.
2. **Corrigir a atribuição de canais:** Central **158 = MTE/Alô Trabalho** (porta de entrada e requerimento); **0800 726 0207 = SAC Caixa** (consulta de parcelas/pagamento). Não tratar tudo como "URA da Caixa".
3. **Substituir a evidência genérica de R2 pela evidência ancorada de R1:** o gargalo do funil deve ser sustentado pelo dado da CGU (67,4% vs. 18,6%), que aponta falha na **camada de orientação automática** — crítica direta à efetividade dos atores de IA no autoatendimento.
4. **Adotar a tabela de fontes de R1** (com URL/data) como padrão de rastreabilidade para todo o documento.
5. **Incorporar o plano de redução de incerteza de R1:** pedido via LAI à Caixa/Serpro/Dataprev sobre a pilha tecnológica da URA, e acompanhamento do resultado do questionário do TCU (out/2025).

---

## 8. Recomendações para o exercício

- **Não escolher "um vencedor".** Em termos de *método*, **R1 é superior** (rastreável, honesto, com dado verificável). Em termos de *entregável*, **R2 é mais útil como ponto de partida**. A nota mais alta vai para quem **fundir os dois**.
- **Reabrir o arquivo de R1:** recuperar a tabela principal de atores (a que menciona os atores 3, 4 e 11) — sem ela, a comparação de mapeamento fica incompleta.⚠️
- **Aplicar a regra de ouro da síntese adversarial:** toda afirmação arquitetural de R2 só "promove" a fato quando passar pelo crivo de fonte rastreável de R1. Até lá, permanece hipótese.

---

### Apêndice — Fontes consultadas nesta síntese (verificação externa)

- CGU — Relatório de Avaliação do Seguro-Desemprego (deferimento de recursos presencial vs. online, base 2022): `eaud.cgu.gov.br/relatorios/download/1421234`
- Caixa — Seguro-Desemprego / canais de atendimento: `caixa.gov.br/beneficios-trabalhador/seguro-desemprego`
- MTE/Agência Gov — Central 158 Alô Trabalho (escopo e horário): `gov.br/trabalho-e-emprego` e `agenciagov.ebc.com.br`
- SAC Caixa Cidadão (0800 726 0207): confirmado em fontes de atendimento ao cidadão.

> Observação de método: a verificação externa serviu para **arbitrar** as afirmações em conflito entre R1 e R2, não para reescrever os relatórios. Onde a evidência pública é silenciosa (arquitetura da URA), a síntese preserva a incerteza em vez de resolvê-la artificialmente.

