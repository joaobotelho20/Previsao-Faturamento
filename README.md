# 📈 Predição de Metas de Faturamento com Séries Temporais

## 📌 Sobre o Projeto
Este repositório contém um código em Python que prevê metas de faturamento usando modelos de regressão em séries temporais. Integrado à API do Google Sheets para acesso e atualização de dados, o projeto analisa históricos de vendas para gerar projeções estratégicas que apoiam decisões de planejamento financeiro da empresa fictícia.

## 📂 Estrutura do Repositório
```
📦 Projeto-Previsao-Faturamento 
├── 📜 client_secret.json           # Chave de acesso do cliente google
├── 📜 token.json                   # Novo token iteravel
├── 📜 Faturamento.ipynb            # Código para acessar dados e desenvolver previsão temporal

```

## 1. Previsão de Séries Temporais com Decomposição STL e Modelo AR

Para prever valores futuros da série temporal, utilizamos a decomposição STL (Seasonal-Trend Decomposition using Loess), separando a sazonalidade entre dias de semana e sábados. A previsão é feita utilizando um modelo autoregressivo (AR) com tendência e resíduos.

### Passos da Modelagem

1. **Carregar e preparar os dados**: Extraímos a série temporal da planilha do Google Sheets e a transformamos em um DataFrame do pandas.

2. **Decomposição STL**:
   - Separamos a série temporal em componentes de *tendência*, *sazonalidade* e *resíduo*.
   - A sazonalidade foi dividida em dois grupos:
     - Um padrão para dias da semana.
     - Outro padrão para sábados.

3. **Previsão com modelo AR**:
   - Ajustamos um modelo AR nos resíduos da série temporal.
   - Prevemos os valores futuros sem a sazonalidade, apenas com a tendência mais o resíduo.
   - Reconstruímos a série previsão somando os componentes a ultima sazonalidade extraida.


## 2. Autenticação e Configuração
A conexão com o Google Sheets é feita utilizando credenciais do Google Cloud. Para isso, são utilizados dois arquivos principais, que você deve criar e adicioanar a pasta de código mudando o diretório dentro do código.

### 2.1 Configurações necessárias

2 arquivos são necessários alem de configurações para acesso via API Google.
- token.json
- client_secret.json

no video abaixo pode conseguir mais detalhes, foi um exemplo parecido com o que eu utilizei:
https://www.youtube.com/watch?v=zCEJurLGFRk

### 2.2. Conexão com Google Sheets
Para interagir com as planilhas do Google, utilizamos a biblioteca `gspread`. O fluxo de autenticação segue os seguintes passos:
1. Carregar o arquivo `client_secret.json`.
2. Autenticar o usuário e gerar o `token.json`.
3. Acessar a planilha desejada utilizando seu ID.


## 3. Considerações Finais
- Para rodar o script, certifique-se de que os arquivos `client_secret.json` e `token.json` estejam corretamente configurados.
- Ajuste os hiperparâmetros da decomposição STL e do modelo AR conforme necessário para melhorar a precisão da previsão.
- Caso a planilha do Google Sheets seja alterada, revise os nomes das colunas no script para evitar erros na leitura dos dados.




