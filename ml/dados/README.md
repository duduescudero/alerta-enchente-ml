# Dados usados: INMET (reais e públicos)

## Fonte

| Item | Detalhe |
|---|---|
| Instituição | Instituto Nacional de Meteorologia (INMET), órgão do Ministério da Agricultura e Pecuária |
| Portal | https://portal.inmet.gov.br/dadoshistoricos |
| Arquivos baixados | `https://portal.inmet.gov.br/uploads/dadoshistoricos/2022.zip`, `2023.zip`, `2024.zip` e `2025.zip` |
| Formato original | Um CSV por estação automática, separado por `;`, decimal com vírgula, codificação Latin-1, 8 linhas de cabeçalho com os metadados da estação |
| Frequência | Horária, em UTC |
| Período usado | 01/01/2022 00h UTC a 31/12/2025 23h UTC (35.064 horas) |
| Acesso | Público e gratuito, sem cadastro |
| Dados simulados | **Nenhum** |

## Estações

| Código | Nome | Local | Latitude, longitude | Altitude | Uso no projeto |
|---|---|---|---|---|---|
| A701 | São Paulo - Mirante | Mirante de Santana, Zona Norte | -23,496; -46,620 | 785,6 m | Alvo (chuva das próximas 24 h) e variáveis principais |
| A771 | São Paulo - Interlagos | Interlagos, Zona Sul | -23,724; -46,677 | 771 m | Variáveis de apoio: chuva, umidade e pressão em outro ponto da cidade |

São as duas estações automáticas do INMET dentro do município de São Paulo. Nenhuma fica na Zona Leste (Jardim Helena), o que está registrado como limitação no relatório.

## Colunas extraídas (de cada estação)

| Coluna no projeto | Coluna original do INMET | Unidade | Faixa aceita |
|---|---|---|---|
| `chuva_mm` | PRECIPITAÇÃO TOTAL, HORÁRIO | mm | 0 a 150 |
| `pressao_hpa` | PRESSAO ATMOSFERICA AO NIVEL DA ESTACAO, HORARIA | hPa (mB) | 850 a 1100 |
| `temperatura_c` | TEMPERATURA DO AR - BULBO SECO, HORARIA | °C | -5 a 45 |
| `orvalho_c` | TEMPERATURA DO PONTO DE ORVALHO | °C | -15 a 35 |
| `umidade_pct` | UMIDADE RELATIVA DO AR, HORARIA | % | 1 a 100 |
| `vento_dir_graus` | VENTO, DIREÇÃO HORARIA | graus | 0 a 360 |
| `rajada_ms` | VENTO, RAJADA MAXIMA | m/s | 0 a 60 |
| `vento_ms` | VENTO, VELOCIDADE HORARIA | m/s | 0 a 40 |

O INMET marca falha de sensor com `-9999`. Esses valores e qualquer valor fora da faixa aceita viram **ausentes**. Nada é inventado: o preenchimento acontece só dentro do pipeline do modelo, com a mediana do treino.

## Arquivos desta pasta

| Arquivo | Vai para o Git? | O que é |
|---|---|---|
| `inmet_sp_a701_a771_2022_2025.csv` | Sim (cerca de 4 MB) | As colunas acima das duas estações, uma linha por hora, gerado pelo notebook a partir dos ZIPs oficiais. Colunas com prefixo `a701_` e `a771_` |
| `brutos/2022.zip` ... `brutos/2025.zip` | Não (cerca de 390 MB, e dois passam do limite de 100 MB do GitHub) | ZIPs originais do INMET |

## Como reproduzir do zero

1. Baixe os quatro ZIPs pelos links acima (ou deixe o notebook baixar sozinho) e salve em `ml/dados/brutos/` com os nomes `2022.zip` a `2025.zip`.
2. Rode o notebook. Com os ZIPs presentes, ele **refaz** o CSV a partir deles; sem os ZIPs, usa o CSV que já está no repositório.
