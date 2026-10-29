# Árvore, floresta ou boosting? — Grupo 10

Comparação de Árvore de Decisão, Random Forest e XGBoost na classificação contemporânea de latência alta. O experimento não demonstra previsão antecipada de falhas.

- Site: [https://lucasfr-brz.github.io/artigo-preditor-redes/](http://preditor-redes.lucasromerofelix.workers.dev/)
- Repositório: https://github.com/LucasFR-BRZ/artigo-preditor-redes
- Autores: Pedro Gabriel Castro da Silva, Ricardo Aguilar Arapa, Lucas Felix Romero, Luiz Eduardo dos Reis e Rodrigo Camargo Vieira.

## Estrutura

- `index.html` e `css/style.css`: artigo estático, sem servidor.
- `images/`: fotos fornecidas e figuras extraídas das saídas do notebook.
- `notebooks/experimento_com_resultados.ipynb`: execução original e avaliação temporal; histórico preservado. A reexecução completa está no notebook datado de 21/10/2026.
- `requirements.txt`: dependências diretas fixadas nas versões da reexecução.

## Reproduzir o experimento

Reexecução completa realizada em 21/10/2026 em ambiente virtual novo, Python 3.12.14, sem saídas ou variáveis antigas. Usado `n_jobs=1` devido à restrição de criação de processos. Todas as células terminaram sem erro.

1. Crie ambiente virtual com Python 3.12.14 e instale `python -m pip install -r requirements.txt`.
2. Abra `notebooks/experimento_reexecutado_20261021.ipynb` e execute todas as células em ordem. A célula de download fixa a revisão dos dados.
3. Confira `reproducao/20261021/RELATORIO.md`, os CSVs, `ambiente_execucao.json` e `dataset_revision.json`. O arquivo `requirements-lock.txt` registra também dependências transitivas e ferramentas do ambiente Linux.
4. Fonte dos dados: https://huggingface.co/datasets/ezharjan/LocalNetDynamics, licença MIT informada pela fonte. Não distribuímos os dados brutos.

Entradas: `jitter_ms`, `packet_loss_pct`; alvo: `label_high_latency`; semente 42; quatro candidatos por modelo; três partes de validação cruzada. O teste final não participa do ajuste.

As versões da execução original não foram registradas. O notebook anterior permanece como histórico. A floresta mantém o maior F1, mas a nova execução tem F1 aleatório 0,2693 e 1.242 FP temporais (antes: 0,2713 e 1.236). Os tempos não são diretamente comparáveis entre ambientes.

## Resultados e interpretabilidade

Maior F1: Random Forest (0,2713 aleatório; 0,0096 temporal). O teste temporal tem seis positivos e 1.236 falsos positivos na floresta. Isso não valida uso em produção. A árvore treinada e os três gráficos de importância publicados foram extraídos das saídas originais, sem novo treinamento. Importância não comprova causalidade.

## Referências, imagens e licenças

- Conceitos de árvores e florestas: documentação oficial do scikit-learn, citada no artigo.
- Boosting: documentação oficial e Chen e Guestrin (2016), citados no artigo.
- Quadro de observação: DataCamp — Ensemble Learning in Python; XGBoost — Introduction to Boosted Trees. Observações e decisões revisadas e validadas pelo grupo em 21/10/2026.
- Figuras 1 e 2: esquemas criados para o artigo. Gráficos e matrizes: resultados do notebook. Figuras 5–8: saídas originais exportadas do notebook.
- Fotos de Pedro, Ricardo, Lucas, Luiz e Rodrigo: fornecidas para o site; não abrangidas automaticamente pela licença do texto. Autorizações devem ser guardadas privadamente pelo grupo.
- Texto e ilustrações originais: a página indica CC BY 4.0 como licença sugerida; o grupo deve confirmar a adoção. Código: licença ainda a definir. A licença MIT dos dados é independente dessas decisões.

## Publicação e pendências humanas

GitHub Pages: branch `main`, pasta raiz. Após cada commit, conferir a execução de Pages em Actions e a URL pública.

- Completar a mini-bio de Ricardo com semestre e área de interesse fornecidos pelo integrante.
- Confirmar consentimento específico de cada autor e a licença do material original, fora do repositório público.
- Substituir o contato pendente apenas por canal institucional autorizado. E-mail pessoal retirado do site.
- Cada integrante deve fazer seus próprios commits; não fabricar participação.
- Testar no celular e ensaiar cinco minutos com participação de todos.
- Reexecução em ambiente limpo concluída; ambiente, revisão dos dados e evidências estão em `reproducao/20261021/`. Testar também o notebook no ambiente de apresentação do grupo.

