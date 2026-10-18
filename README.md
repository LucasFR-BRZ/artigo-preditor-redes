# Árvore, floresta ou boosting? — Grupo 10

Artigo técnico sobre Árvore de Decisão, Random Forest e XGBoost na classificação de latência alta em redes.

## Arquivos
- `index.html`: artigo público, estático e responsivo.
- `css/style.css`: estilos.
- `notebooks/experimento_com_resultados.ipynb`: experimento original executado e avaliação temporal.

## Como publicar
1. Substituir os campos `[inserir ...]` no `index.html` por informações autorizadas.
2. Colocar fotos autorizadas em `images/` e atualizar os cartões de autores.
3. Criar repositório público no GitHub, enviar os arquivos e pedir commits de todos os integrantes.
4. Em Settings > Pages, selecionar Deploy from a branch e publicar a branch principal a partir de `/ (root)`.
5. Abrir a URL no celular e testar links, imagens e notebook.

## Reproduzir o experimento
Abrir `notebooks/experimento_com_resultados.ipynb` no Google Colab e executar todas as células em ordem. Requer internet para baixar a base pública LocalNet-Dynamics e instalar bibliotecas. Bibliotecas usadas: Python 3, pandas, numpy, datasets, scikit-learn, xgboost, matplotlib e seaborn. **Registrar as versões exatas no Colab antes da entrega**, por exemplo com `import sklearn, xgboost, pandas, datasets; print(sklearn.__version__, xgboost.__version__, pandas.__version__, datasets.__version__)`.

Fonte dos dados: https://huggingface.co/datasets/ezharjan/LocalNetDynamics. Não redistribuir os dados sem conferir os termos de licença na fonte.

## Atenção à interpretação
Os rótulos foram derivados de regras. A avaliação temporal teve somente seis casos positivos no teste, com mais de mil falsos positivos por modelo. O estudo **não comprova previsão antecipada** nem valida implantação em produção.

## Autores
Pedro Gabriel Castro da Silva, Ricardo Aguilar Arapa, Lucas Felix Romero, Luiz Eduardo dos Reis e Rodrigo Camargo Vieira.

## Referências
Listadas ao final de `index.html`; figuras esquemáticas produzidas para esta página.
