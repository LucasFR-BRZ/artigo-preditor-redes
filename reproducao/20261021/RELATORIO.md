# Reexecução em ambiente limpo — 21/10/2026

Notebook executado do início ao fim em processo Python novo, com todas as saídas antigas apagadas, em ambiente virtual criado sem pacotes do sistema. Cache de dados separado. As tentativas preliminares com kernel e multiprocessamento falharam; a execução final completa usou IPython em processo único, sem kernel TCP, com `n_jobs=1`. Os ajustes de execução não alteraram entradas, rótulos, grades ou divisões.

Python: 3.12.14 (main, Aug 25 2026, 14:00:49) [Clang 22.1.3 ].
Revisão da base: `25fa86bc199935c3a745e70a1e11e48c9f676082`.

## Resultado

| Avaliação | Modelo | Precisão | Recall | F1 | Acurácia | FP | FN | Treino + ajuste (s) | Predição (s) |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Aleatória | Random Forest | 0.157162 | 0.939641 | 0.269285 | 0.713841 | 3089 | 37 | 26.518052 | 0.087793 |
| Aleatória | Árvore de Decisão | 0.156225 | 0.947798 | 0.268236 | 0.709813 | 3138 | 32 | 0.493499 | 0.002309 |
| Aleatória | XGBoost | 0.154949 | 0.934747 | 0.265832 | 0.710271 | 3125 | 40 | 2.218990 | 0.024197 |
| Temporal | Árvore de Decisão | 0.004498 | 1.000000 | 0.008955 | 0.878433 | 1328 | 0 | 0.412642 | 0.001988 |
| Temporal | Random Forest | 0.004808 | 1.000000 | 0.009569 | 0.886305 | 1242 | 0 | 19.921450 | 0.034031 |
| Temporal | XGBoost | 0.004338 | 1.000000 | 0.008639 | 0.873947 | 1377 | 0 | 1.565005 | 0.008147 |

## Comparação com a execução anterior

- Random Forest: F1 aleatório de 0,2713 para 0,2693; melhor número de árvores de 100 para 200.
- Random Forest temporal: F1 continua 0,0096 com quatro casas; FP de 1.236 para 1.242; VN de 9.682 para 9.676.
- Árvore e XGBoost mantiveram as métricas com quatro casas decimais.
- A Random Forest mantém o maior F1 nas duas avaliações. A conclusão de que nenhum modelo está validado para produção permanece.
- As versões originais não foram registradas; não podemos atribuir com certeza a diferença a uma versão específica. Tempos variam com a máquina e o paralelismo e não devem ser comparados como ganho algorítmico.

## Bibliotecas

- datasets: 5.1.0
- xgboost: 3.4.1
- scikit-learn: 1.9.1
- pandas: 3.0.6
- numpy: 2.5.4
- matplotlib: 3.11.2
- seaborn: 0.13.2

## Reproduzir

Use Python 3.12.14 em ambiente virtual novo e instale `python -m pip install -r requirements.txt` na raiz do repositório. Abra o notebook reexecutado e execute todas as células em ordem. Para reconstruir também as dependências transitivas e ferramentas desta execução Linux, use `reproducao/20261021/requirements-lock.txt`. A biblioteca `socksio` é uma dependência de conexão deste ambiente e não um atributo do modelo. A célula de download fixa a revisão da base.

## Verificação

Todas as células de código foram executadas com contagem sequencial, sem saídas de erro. As duas divisões usam 43.693 linhas de treino e 10.924 de teste; o teste temporal contém seis positivos. A saída pública mostra apenas atributos necessários na prévia, sem identificadores de rede. Resultados da execução original continuam no notebook anterior e nas tabelas históricas do artigo.
