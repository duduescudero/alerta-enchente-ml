# Registro de uso de IA · AlertaEnchente (IA & Machine Learning)

> Global Solution 2026.2 · FIAP · Engenharia de Software (3º ano)
> Conforme os combinados da GS, a IA generativa foi usada como **copiloto**: para aprender, estruturar e revisar. As decisões, a execução e a validação final foram da equipe, e todos os integrantes sabem explicar cada etapa do notebook.

## Visão geral

| Item | Detalhe |
|---|---|
| Ferramenta | Claude (Anthropic) |
| Papel da IA | Apoio na organização do notebook, na revisão da metodologia (vazamento de dados, validação temporal, métricas para classes raras) e na escrita do relatório |
| Papel da equipe | Definir a pergunta de ML, escolher a fonte de dados e as estações, decidir o modelo, executar o notebook, conferir os resultados e escrever as conclusões |
| Dados usados nas conversas | Somente dados públicos do INMET. Nenhum dado pessoal |
| IA dentro do produto | O modelo de ML (Random Forest) é o próprio produto desta disciplina; não há IA generativa dentro dele |

Como ler as tabelas: a coluna **Prompt** traz um resumo fiel do que foi pedido, e a coluna **Resultado e validação** mostra o que a equipe fez com a resposta.

---

## Etapa 1 · Desenvolvimento do projeto

| # | Objetivo | Prompt (resumo fiel) | Resultado e validação pela equipe |
|---|---|---|---|
| 1 | Organizar o projeto | Ajuda para organizar o projeto, montar uma primeira versão do notebook e revisar a documentação, usando dados reais do INMET, com Random Forest, testes de parâmetros, gráficos e relatório. | Primeira versão do notebook com a estação A701, divisão temporal 80/20, 12 combinações de hiperparâmetros e relatório inicial. |
| 2 | Preparar os dados | Orientação para carregar os arquivos históricos do INMET, organizar as informações meteorológicas, tratar valores ausentes e selecionar as variáveis necessárias para prever a ocorrência de chuva. | Dados meteorológicos organizados em formato adequado para o treinamento, com tratamento inicial de inconsistências e conferência das variáveis utilizadas. |
| 3 | Definir a metodologia | Revisão da metodologia de treinamento do Random Forest, incluindo separação entre treino e teste em ordem cronológica e cuidados para evitar vazamento de dados durante a preparação das variáveis. | Primeira estratégia de divisão temporal implementada e variáveis organizadas para que o modelo utilize informações disponíveis antes da previsão. |
| 4 | Treinar e avaliar o modelo | Apoio na implementação do Random Forest e na configuração de diferentes combinações de hiperparâmetros, além da escolha de métricas adequadas para avaliar a previsão de eventos de chuva. | Modelo treinado com diferentes configurações, resultados comparados por métricas de classificação e gráficos gerados para análise do desempenho. |
| 5 | Interpretar os resultados | Ajuda para interpretar os resultados obtidos pelo modelo, analisar erros de previsão, identificar limitações e organizar as conclusões em uma linguagem compreensível para o relatório. | Primeiras análises de desempenho e limitações do modelo documentadas, com gráficos e conclusões preliminares revisados pela equipe. |

---

## Etapa 2 · Revisão final antes da entrega (19/11/2026)

| # | Objetivo | Prompt (resumo fiel) | Resultado e validação pela equipe |
|---|---|---|---|
| 1 | Auditar a entrega | Avaliação do projeto contra os 6 critérios de IA & ML da GS (dados reais, escolha do modelo, preparação, hiperparâmetros, resultados e conclusão). | Lista de pontos: `dados/README.md` incompleto, escolha do modelo pouco justificada, sem análise exploratória, comparação só com "sempre não chove", sobreajuste discutido em uma frase, conclusão técnica demais e ZIPs brutos grandes demais para o GitHub. |
| 2 | Reescrever com rigor | Pedido para reescrever o notebook mantendo dados reais, Random Forest e divisão temporal. | Notebook refeito: segunda estação do INMET (A771 Interlagos), variáveis só com informação do passado, análise exploratória, 24 combinações de 3 hiperparâmetros com validação cruzada temporal só no treino, limiares do farol escolhidos só com o treino, comparação com regras simples e importância por permutação. |
| 3 | Comprovar | Execução completa do notebook do zero, a partir dos ZIPs oficiais do INMET. | Notebook executado sem erros; números do relatório conferidos com as saídas e com `resultados/metricas.json`. Conferido que o teste foi usado uma única vez. |
| 4 | Traduzir para o cidadão | Como explicar o resultado para um morador, sem termos técnicos. | Leitura dia a dia do período de teste (dias de chuva forte avisados e alarmes falsos) e o papel do modelo dentro do farol do AlertaEnchente. |

---

## Compromissos da equipe

- Nenhum dado simulado: tudo vem dos arquivos oficiais do INMET.
- O conjunto de teste foi usado uma única vez, no fim; nenhuma escolha foi feita olhando o teste.
- Todo número do relatório sai das saídas do notebook executado.
- Nenhum código foi aceito sem leitura e entendimento por parte da equipe.
