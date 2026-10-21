# Árvore, floresta ou boosting? — Grupo 10

Comparação de Árvore de Decisão, Random Forest e XGBoost na classificação contemporânea de latência alta. O experimento não demonstra previsão antecipada de falhas.

- Site: https://lucasfr-brz.github.io/artigo-preditor-redes/
- Repositório: https://github.com/LucasFR-BRZ/artigo-preditor-redes
- Autores: Pedro Gabriel Castro da Silva, Ricardo Aguilar Arapa, Lucas Felix Romero, Luiz Eduardo dos Reis e Rodrigo Camargo Vieira.

## Estrutura

- `index.html` e `css/style.css`: artigo estático, sem servidor.
- `images/`: fotos fornecidas e figuras extraídas das saídas do notebook.
- `notebooks/experimento_com_resultados.ipynb`: execução original e avaliação temporal; célula adicional de registro de ambiente ainda sem execução.
- `requirements.txt`: dependências diretas; ainda sem versões históricas verificadas.

## Reproduzir o experimento

1. Use um ambiente Python 3 com acesso à internet, preferencialmente Google Colab com runtime novo. A versão exata do Python da execução original não foi registrada.
2. Instale as dependências com `python -m pip install -r requirements.txt`, ou execute a célula de instalação do notebook no Colab.
3. Execute todas as células em ordem. A célula de ambiente grava `ambiente_execucao.json` e `requirements-execucao.txt` com versões reais de Python e bibliotecas. Guarde esses arquivos junto dos novos resultados. Para repetir esse novo ambiente, use a mesma versão do Python e instale `pip install -r requirements-execucao.txt`.
4. O notebook baixa a base pública com `load_dataset("ezharjan/LocalNetDynamics", split="train")`. Fonte: https://huggingface.co/datasets/ezharjan/LocalNetDynamics. Licença MIT informada na página, consultada em 21/10/2026; preserve os créditos e termos da fonte. Os dados brutos não são distribuídos neste repositório.
5. Entradas: `jitter_ms` e `packet_loss_pct`; alvo: `label_high_latency`. RTT não entra em X porque participa da geração do rótulo. Semente 42; quatro candidatos por modelo; três partes de validação cruzada. Imputação e ajuste ocorrem no treino.
6. Execute a avaliação aleatória e, em seguida, a temporal. Confira os CSVs de métricas e matrizes gerados. Tempos variam por máquina.

**Limite de reprodução:** as versões antigas e a revisão exata dos dados não foram registradas. Portanto, não é possível garantir números idênticos aos publicados. Antes da entrega, executar em ambiente limpo, registrar versões e revisão da base, comparar os resultados e atualizar o artigo se necessário. Não inventar versões nem substituir as métricas sem nova execução.

## Resultados e interpretabilidade

Maior F1: Random Forest (0,2713 aleatório; 0,0096 temporal). O teste temporal tem seis positivos e 1.236 falsos positivos na floresta. Isso não valida uso em produção. A árvore treinada e os três gráficos de importância publicados foram extraídos das saídas originais, sem novo treinamento. Importância não comprova causalidade.

## Referências, imagens e licenças

- Conceitos de árvores e florestas: documentação oficial do scikit-learn, citada no artigo.
- Boosting: documentação oficial e Chen e Guestrin (2016), citados no artigo.
- Quadro de observação: DataCamp — Ensemble Learning in Python; XGBoost — Introduction to Boosted Trees. Observação técnica da revisão; o grupo precisa ler e validar as decisões, sem atribuir leituras a quem não as realizou.
- Figuras 1 e 2: esquemas criados para o artigo. Gráficos e matrizes: resultados do notebook. Figuras 5–8: saídas originais exportadas do notebook.
- Fotos de Ricardo e Rodrigo: fornecidas para o site; não abrangidas automaticamente pela licença do texto. Autorizações devem ser guardadas privadamente pelo grupo.
- Texto e ilustrações originais: a página indica CC BY 4.0 como licença sugerida; o grupo deve confirmar a adoção. Código: licença ainda a definir. A licença MIT dos dados é independente dessas decisões.

## Publicação e pendências humanas

GitHub Pages: branch `main`, pasta raiz. Após cada commit, conferir a execução de Pages em Actions e a URL pública.

- Enviar fotos autorizadas de Pedro, Lucas e Luiz; completar mini-bios e LinkedIn pendentes. Não preencher com dados inferidos.
- Confirmar consentimento específico de cada autor e a licença do material original, fora do repositório público.
- Substituir o contato pendente apenas por canal institucional autorizado. E-mail pessoal retirado do site.
- Cada integrante deve fazer seus próprios commits; não fabricar participação.
- Validar o quadro de observação, testar no celular e ensaiar cinco minutos com participação de todos.
- Reexecutar o notebook do início ao fim em ambiente limpo e guardar ambiente/revisão dos dados. Essa reexecução não foi realizada nesta revisão editorial.
