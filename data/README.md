# Dados — Projeto 001

## Fonte e obtenção

Fonte: World Development Indicators (WDI), Banco Mundial.

Os três pacotes ZIP foram baixados manualmente pelas páginas oficiais
dos indicadores abaixo.

- Data exata do download: não informada.
- Atualização indicada nos CSVs: 2026-07-13.
- Recorte previsto para a análise: 2000–2023.

| Indicador | Código | Página de origem |
| --- | --- | --- |
| PIB per capita em PPC, dólares internacionais constantes de 2021 | NY.GDP.PCAP.PP.KD | <https://data.worldbank.org/indicator/NY.GDP.PCAP.PP.KD> |
| Expectativa de vida ao nascer, total, em anos | SP.DYN.LE00.IN | <https://data.worldbank.org/indicator/SP.DYN.LE00.IN> |
| População total | SP.POP.TOTL | <https://data.worldbank.org/indicator/SP.POP.TOTL> |

## Organização

| Caminho | Conteúdo |
| --- | --- |
| original/ | Três pacotes ZIP originais |
| extracted/ | Nove CSVs extraídos, com os nomes originais |
| provisional/ | JSON de metadados obtido separadamente, ainda não revisado |

### Pacotes originais

- API_NY.GDP.PCAP.PP.KD_DS2_en_csv_v2_349558.zip
- API_SP.DYN.LE00.IN_DS2_en_csv_v2_330385.zip
- API_SP.POP.TOTL_DS2_en_csv_v2_350115.zip

Cada pacote contém:

- API_...csv: dados do indicador por economia e ano;
- Metadata_Country_...csv: metadados das economias;
- Metadata_Indicator_...csv: definição e fontes do indicador.

Os nove CSVs estão diretamente em extracted/. Seus nomes permitem
identificar o pacote e o indicador de origem.

O arquivo provisional/metadados.json foi obtido pelo endereço:
<https://api.worldbank.org/v2/country?format=json>

Sua completude não foi verificada. Seu uso não é obrigatório,
pois os ZIPs já contêm arquivos de metadados.

## Preservação e reprodução

Os ZIPs em original/ devem permanecer sem alterações. Os CSVs de
extracted/ devem preservar o conteúdo recebido; transformações
posteriores devem gerar arquivos separados.

Para repetir a obtenção, acessar cada página de origem e selecionar
o download em CSV. Novos downloads podem conter revisões e nomes
diferentes. Para reproduzir esta análise, utilizar os pacotes
preservados e registrar seus identificadores de integridade.

Checksums dos arquivos locais: ainda não registrados.

## Estado da verificação

O assistente abriu os três ZIPs fornecidos e inspecionou sua estrutura,
metadados e amostras. Os indicadores correspondem aos previstos
no contrato.

Os CSVs principais apresentam anos em colunas, de 1960 a 2025.
A existência de uma coluna não comprova disponibilidade de valores
para todas as economias naquele ano.

Permanecem pendentes:

- diagnóstico de cobertura no recorte de 2000–2023;
- verificação de ausências, duplicidades e correspondência entre arquivos;
- identificação de países, territórios e agregados;
- definição documentada dos universos sul-americano e global;
- conferência da integridade dos arquivos locais.

Nenhuma conclusão analítica decorre desta inspeção preliminar.

## Licença e atribuição

As páginas dos três indicadores informam licença CC BY 4.0.
O uso e a redistribuição devem atribuir crédito ao Banco Mundial
e aos provedores identificados nos metadados, indicar alterações
e observar os termos aplicáveis.

Referência: Banco Mundial — World Development Indicators (WDI).

Termos:
<https://data.worldbank.org/summary-terms-of-use>

## Autoria deste registro

Redação assistida por IA, baseada na organização informada pelo
usuário e na inspeção dos anexos. A aquisição foi realizada pelo
usuário; métodos, decisões e resultados da análise serão
documentados por ele.
