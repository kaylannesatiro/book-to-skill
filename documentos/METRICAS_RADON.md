# Reprodução das métricas do Radon

As métricas do relatório foram reproduzidas com o Radon 6.0.1 em dois estados fixos do repositório:

- antes: `e180fc46365e8c1aab0120778cc8a40b9515324b`;
- depois: `10107083b15b529b8642cbb030fa8b8dfe7d18e7`.

O commit `1010708` representa a árvore acadêmica final com as 40 refatorações e os mesmos 49 arquivos Python presentes no estado inicial. O SHA `5aacc33` continua sendo o SHA final publicado no PR, mas inclui sincronizações posteriores do projeto original; por isso ele não foi usado na comparação acadêmica controlada.

## Escopo e método

- Foram analisados recursivamente todos os arquivos `*.py` sob `tests/`.
- O SLOC de cada arquivo foi obtido com `radon.raw.analyze`.
- A complexidade foi obtida com `radon.complexity.cc_visit`.
- A média de complexidade considera funções, métodos e closures e exclui os blocos-resumo de classes, reproduzindo as médias históricas de 2,6935 e 2,6806.
- O índice de manutenibilidade foi obtido com `radon.metrics.mi_visit(..., multi=True)` e calculado como a média dos arquivos.

## Resultados reproduzidos

| Métrica | Antes | Depois | Variação |
|---|---:|---:|---:|
| Arquivos Python | 49 | 49 | 0 |
| SLOC | 5.879 | 5.921 | +42 (+0,71%) |
| Blocos funcionais | 744 | 742 | -2 |
| Complexidade média | 2,6935483871 | 2,6805929919 | -0,0129553952 |
| Complexidade máxima | 15 | 15 | 0 |
| Manutenibilidade média | 57,2468632843 | 57,1502266677 | -0,0966366166 |

Os arquivos `summary.csv`, `radon-raw.csv`, `radon-complexity.csv` e `radon-maintainability.csv` estão nas pastas `metrics-before-radon/` e `metrics-after-radon/`. A linha `TOTAL` de cada `radon-raw.csv`, filtrada por `origem = teste`, contém o SLOC utilizado no relatório.
