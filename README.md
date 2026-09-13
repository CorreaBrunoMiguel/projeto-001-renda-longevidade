# Projeto 001 — Renda e longevidade

Trajetórias na América do Sul, com referência global e aprofundamento nos quatro países fundadores do Mercosul, 2000–2023.

Contrato: 1.1.0 · Data: 2026-09-13

Status: contrato lido pelo usuário; recorte ajustado por acordo; T10 iniciada com aquisição de arquivos. Inspeção preliminar dos anexos realizada; implementação e diagnóstico completo ainda não revisados.

## Cenário, público e decisão

Uma equipe de pesquisa de um observatório de desenvolvimento humano precisa selecionar países e períodos para estudos posteriores. O cenário é fictício. A investigação examina como PIB per capita e expectativa de vida evoluem e se relacionam na América do Sul, identificando diferenças entre países e situando os resultados em uma referência global limitada.

A entrega apoia a priorização de casos para investigação, não a recomendação de políticas nem a atribuição de causas. Não há resultado esperado a ser confirmado.

## Objetivo e perguntas

Produzir uma investigação descritiva, reproduzível e tecnicamente defensável sobre desenvolvimento econômico e longevidade.

- P1 — Quais países sul-americanos e anos possuem cobertura suficiente, e qual conjunto global permite contextualização comparável?
- P2 — Como evoluíram PIB per capita, expectativa de vida e diferenças de longevidade entre países sul-americanos no período?
- P3 — Países sul-americanos com PIB per capita semelhante apresentam longevidade semelhante? Como a associação evolui e como os resultados se situam na distribuição global de países em anos selecionados?
- P4 — Como as trajetórias de Brasil, Argentina, Uruguai e Paraguai se comparam entre si e ao contexto sul-americano, incluindo 2019–2023?
- P5 — Quais casos merecem estudo posterior e quais conclusões permanecem fora do alcance dos dados?

## Dados, obtenção e verificação

Fonte: World Development Indicators (WDI), Banco Mundial.

| Série | Código | Unidade |
| --- | --- | --- |
| PIB per capita em paridade de poder de compra | NY.GDP.PCAP.PP.KD | Dólares internacionais constantes de 2021 |
| Expectativa de vida ao nascer, total | SP.DYN.LE00.IN | Anos |
| População total | SP.POP.TOTL | Pessoas; estimativa de meio de ano |

Páginas oficiais:

- https://data.worldbank.org/indicator/NY.GDP.PCAP.PP.KD
- https://data.worldbank.org/indicator/SP.DYN.LE00.IN
- https://data.worldbank.org/indicator/SP.POP.TOTL
- Metadados das economias: https://api.worldbank.org/v2/country?format=json
- Documentação de obtenção: https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structures
- Termos: https://data.worldbank.org/summary-terms-of-use

O usuário utiliza os CSVs distribuídos em ZIP nas três páginas oficiais dos indicadores. A aquisição manual é aceita: documentar o caminho de download e preservar os arquivos originais. Não é exigida programação de aquisição por API neste projeto. Os ZIPs incluem metadados de países e indicadores; sua adequação e consistência devem ser avaliadas. O JSON obtido separadamente é opcional e ainda não foi inspecionado. Deve registrar URLs efetivamente usadas, data de obtenção, atualização informada pela fonte e identificação dos arquivos obtidos. Deve preservar uma cópia local dos dados de entrada para reproduzir a análise mesmo após revisões da fonte.

Na preparação em 2026-09-13, páginas e API responderam sem cadastro, chave ou pagamento. Foram inspecionados metadados, pequenas amostras JSON e dados brasileiros de expectativa de vida de 2019–2023. As respostas indicaram atualização em 2026-07-13 e 6.360 registros por série no recorte: 19.080 no total, incluindo agregados e possíveis ausências. Estimativa de volume: poucos megabytes; não houve download integral nem auditoria de cobertura.

Campos observados: indicador, identificador e nome da economia, código de três letras, ano, valor, unidade e status da observação. O campo de unidade veio vazio nas amostras; as unidades devem ser documentadas pelos metadados. O catálogo de economias retornou 295 entradas, universo distinto do retornado pelas séries; não se deve presumir correspondência completa. Região e identificação de agregados estão disponíveis nos metadados.

As três páginas declaram CC BY 4.0. Uso, adaptação e redistribuição devem atribuir crédito ao Banco Mundial e aos provedores identificados, referenciar licença e termos e indicar alterações. A licença dos dados não licencia automaticamente o código do projeto. Uma página complementar de licenças retornou 403; a licença foi confirmada nas páginas individuais e no resumo oficial. A obtenção de CSV em ZIP pelo usuário foi evidenciada pelos três anexos abertos na revisão preliminar. Excel não foi testado.

### Inspeção dos arquivos fornecidos

Foram abertos os três ZIPs enviados pelo usuário: PIB per capita (93.808 bytes), população (89.654 bytes) e expectativa de vida (90.461 bytes). Cada pacote contém três CSVs: dados, metadados de países e metadados do indicador. Os dados estão em formato largo, com nomes/códigos, anos de 1960 a 2025 e linhas preliminares de identificação/atualização. Todos informam atualização em 2026-07-13. Existem campos vazios. A presença de uma coluna anual não comprova dados disponíveis nesse ano.

Esta é uma inspeção de estrutura e amostras pelo assistente; não substitui o diagnóstico de cobertura, integridade, seleção territorial e consistência a ser realizado pelo usuário em T10. O usuário informou uso dos links do README; a data exata de download e o procedimento ainda devem ser documentados por ele. Preservar os arquivos de metadados ao extrair os pacotes.

## Escopo e limitações

Obrigatório: três indicadores anuais, 2000–2023; América do Sul como universo principal, com lista de países e regra de inclusão territorial documentadas; referência global limitada à distribuição de países elegíveis em anos selecionados e justificados; cinco perguntas; aprofundamento fixo em Brasil, Argentina, Uruguai e Paraguai; SQL e análise Python; comunicação acessível com evidências inspecionáveis.

Os quatro países foram escolhidos previamente pelo usuário por interesse no grupo fundador do Mercosul, não por desempenho observado. A denominação não representa toda a composição atual do bloco nem um teste dos efeitos de sua participação. Fonte histórica: https://www.mercosur.int/pt-br/documentos/textos-fundacionais

A referência global contextualiza a região; não abre uma segunda investigação completa. O agrupamento regional amplo disponível nos metadados não deve ser presumido como equivalente à América do Sul. Proximidade geográfica não garante condições homogêneas.

Excluído: ML, previsão, inferência causal, dashboard, aplicação web, infraestrutura adicional, indicadores explicativos extras, comparação com outras regiões consideradas semelhantes, aquisição programática por API e estudos detalhados de políticas públicas.

Cuidados analíticos:

- Separar economias de agregados e declarar como territórios e mudanças de cobertura são tratados.
- Comparar períodos equivalentes, documentar ausências e exclusões e avaliar seus efeitos. Não escolher silenciosamente o último ano disponível de cada país.
- PIB per capita não mede distribuição de renda; PPC e preços constantes não eliminam todas as diferenças metodológicas.
- Expectativa de vida ao nascer é uma medida baseada nos padrões de mortalidade do período, não a idade média dos falecidos nem uma previsão individual.
- Diferenciar associação entre países de evidência sobre indivíduos ou causalidade. O intervalo da pandemia não autoriza atribuir todas as mudanças à COVID.
- Identificar estimativas e revisões conhecidas. Não aplicar classificação econômica atual como classificação histórica.
- Distinguir ponderação por população de peso igual por país. Uma média das expectativas nacionais não equivale automaticamente à expectativa de vida mundial.

Contingência: problemas de cobertura podem justificar reduzir para 2000, 2010, 2019 e 2023 e economias comparáveis. Se necessário, negociar comparação em um ano comum e retirar perguntas temporais. Mudanças devem registrar motivo, perda de cobertura e critérios afetados antes de prosseguir. Em falha do download, utilizar os ZIPs originais preservados e identificados, cuja abertura foi verificada. Se os arquivos forem inadequados e não houver cópia válida nem acesso à fonte, negociar a redução ou pausa; não existe fonte independente alternativa validada.

## Requisitos e critérios de aceitação

Não há aplicação com requisitos funcionais próprios. O contrato possui requisitos analíticos, técnicos e de reprodutibilidade.

| ID | Classe | Requisito e evidência verificável |
| --- | --- | --- |
| A01 | Analítico | Responder P1 com cobertura por indicador e período, critérios de inclusão/exclusão e dimensão populacional coberta quando calculável, explicitando denominador e limitações. |
| A02 | Analítico | Responder P2 com evolução e medida justificada das diferenças entre países, sem confundir mudanças de composição com mudanças do fenômeno. |
| A03 | Analítico | Responder P3 com comparação econômica coerente, associação sem linguagem causal e referência global limitada; justificar anos, universo elegível e significado de níveis semelhantes. Não confundir distribuição de países com experiência da população mundial. |
| A04 | Analítico | Responder P4 aprofundando Brasil, Argentina, Uruguai e Paraguai com critérios comparáveis e limitações explícitas; eventual inviabilidade por cobertura exige acordo antes de substituição ou redução. |
| A05 | Analítico | Responder P5 com síntese para o público, casos prioritários e limites; vincular afirmações a consultas, tabelas ou figuras identificáveis. |
| T01 | Técnico | Usar PostgreSQL para persistência, integridade, integração e consultas analíticas com função real. Entregar SQL executável e documentar o grão e as relações dos dados. |
| T02 | Técnico | Usar Python e Pandas para processamento/validação e Matplotlib para figuras legíveis com unidades, períodos e fontes. Evitar duplicação sem propósito entre SQL e Python. |
| T03 | Técnico | Apresentar verificações pertinentes de chaves, duplicidades, ausências, tipos, domínios, correspondências entre fontes e cardinalidade de junções; demonstrar que erros não contaminam resultados. |
| R01 | Reprodutibilidade | Documentar ambiente e dependências efetivamente utilizados, configuração sem segredos e sequência completa da aquisição à entrega. |
| R02 | Reprodutibilidade | Identificar entradas e suas versões por data e checksum ou mecanismo equivalente; documentar transformações e decisões. |
| R03 | Reprodutibilidade | Demonstrar execução completa a partir de ambiente/sessão limpa e entradas identificadas; notebooks, se utilizados, devem executar em ordem sem estado oculto. |
| R04 | Reprodutibilidade | Manter atribuição e termos dos dados; não versionar credenciais, ambientes virtuais ou arquivos grandes sem necessidade justificada. |

Validações devem abordar riscos reais; não há meta arbitrária de quantidade de testes ou gráficos. Métodos e resultados são documentados pelo usuário.

## Ferramentas e ambiente

- PostgreSQL: único banco exigido; persistência, integridade, integração e consultas.
- Python 3.12 em ambiente isolado: referência recomendada para aquisição e execução reproduzível. Registrar versão e dependências efetivas.
- Pandas: inspeção, validação e preparação analítica.
- Matplotlib: comunicação gráfica das respostas.
- JupyterLab: exploração e narrativa, se adotado; não substitui reprodutibilidade.
- Git/GitHub: autoria, histórico e revisões.

Linux, Core i5 e 8 GB de RAM são compatíveis com o volume estimado. Não há necessidade de MySQL adicional, Docker, Colab ou CI. Disponibilidade declarada: 2–3 horas diárias, sem prazo final imposto.

## Entregáveis

1. Registro de fontes, obtenção, dicionário e critérios de cobertura — A01, R02, R04.
2. Estrutura de dados, SQL e processamento executáveis — T01, T02, R01.
3. Evidências de validação com problemas encontrados e tratamento — T03, R03.
4. Análise documentada, tabelas e figuras vinculadas às perguntas — A02–A04, T02.
5. Síntese conclusiva acessível e limites — A05.
6. Instruções de reprodução e acompanhamento curto de revisões — R01–R04.

O usuário decide a organização técnica dos arquivos com justificativa proporcional. Não há obrigação de relatório acadêmico, pacote Python ou pastas vazias.

## Tasks por dependência e checkpoints

| Task | Depende de | O que entregar | Checkpoint |
| --- | --- | --- | --- |
| T00 — Abertura | Proposta aceita | Repositório próprio, contrato e acompanhamento inicial; registrar dúvidas de entendimento antes da execução. | C0: bootstrap confirmado e contrato compreendido. |
| T10 — Aquisição e diagnóstico | T00 | Entradas identificadas, documentação de fonte/unidades e diagnóstico de cobertura; critérios propostos de elegibilidade. | C1: fonte, cobertura e viabilidade revisadas; redução negociada se necessária. |
| T20 — Integração | T10/C1 | Dados persistidos em PostgreSQL, documentação do grão/relações, SQL e processamento de integração; evidências das validações pertinentes. | C2: integridade e integração revisadas. |
| T30 — Investigação | T20/C2 | Respostas a P1–P4, métodos e escolhas documentados, figuras e aprofundamento nos quatro países definidos. | C3: cálculos, comparabilidade e interpretação revisados. |
| T40 — Conclusão e reprodução | T30/C3 | Resposta a P5, síntese, limitações e evidência de execução integral reproduzível. | C4: conclusão técnica avaliada. |
| T50 — Avaliação para portfólio | T40/C4 | Apresentação final, autoria/assistência transparentes e condições de publicação verificadas. | C5: prontidão para portfólio avaliada separadamente. |

O assistente conduz prioridades, tasks e checkpoints e mantém contrato, requisitos e acompanhamento. Cada task deve ter objetivo, entrega e critério verificável; não pressupõe implementação pelo assistente. Ajustes durante o projeto são permitidos mediante acordo e registro de motivo, impacto e critérios afetados, sem expansão automática ou cobrança retroativa.

As tasks especificam resultados, não a solução. Submissões podem ser pequenas dentro de cada task. Questões conceituais e bloqueios podem ser discutidos antes da submissão.

## Submissão, revisão e governança Git

O usuário informa repositório, branch, task/checkpoint e preferencialmente commit, resumo das alterações, como executou as verificações e dúvidas. O assistente consulta o SHA quando possível e pede somente evidência ausente necessária. Estado remoto não comprova estado local; comandos sugeridos não comprovam execução.

Bootstrap documental pode ocorrer na main vazia. Depois, main estável e branches para mudanças substanciais, com integração após revisão. O assistente conduz nomes de branches, unidades de commit e integração a partir de status/diffs realmente disponíveis. Não há Git Flow, issues, PRs ou CI obrigatórios. Não reescrever histórico, descartar alterações ou forçar push sem autorização específica.

Cada revisão identifica referência e alcance: inspeção estática, execução própria e/ou evidência fornecida. Achados distinguem erro conceitual, implementação, decisão insuficientemente justificada, melhoria opcional e expansão de escopo. Correções obrigatórias indicam requisito ou consequência demonstrável, evidência e condição de resolução. Não implementar a correção pelo usuário nem entregar exemplos equivalentes à solução.

O acompanhamento.md é mantido pelo assistente: etapa, checkpoint, referência revisada, decisões, pendências por impacto e próximo passo. Diferenciar implementado, revisado e aprovado. Registrar pausas relevantes sem transcrever conversas.

## Conclusão e autoria

Conclusão técnica exige atendimento verificável aos requisitos aplicáveis e resolução dos achados que invalidem resultados. Existência de testes não comprova sucesso. Limitações de revisão devem ser declaradas.

Prontidão para portfólio será avaliada depois, considerando clareza, valor demonstrado, autoria, assistência utilizada, reprodução e condições de publicação. Concluir tecnicamente não garante aprovação para portfólio nem empregabilidade.

Assistente: contexto, verificação inicial das fontes, contrato, mentoria, revisão e governança. Bruno: aquisição e integração, SQL/código, análises, validações e documentação dos métodos, decisões e resultados. Competência é registrada com evidência revisada, não presumida pela experiência declarada.

Há apenas um projeto técnico ativo na jornada. A jornada de desafios Python é independente. Ideias extras ficam fora da entrega obrigatória até acordo explícito. O procedimento de boot permanece em teste, sem alteração das regras permanentes.

