# ProjetoIntegrador_Unisenai

## Objetivo

Este projeto tem como objetivo realizar uma análise do banco de dados fornecido pela AWS, com foco no mapeamento estrutural das tabelas e de seus relacionamentos por meio da construção dos modelos conceitual e lógico.

## Estrutura do Projeto

### 📁 Banco_de_Dados_PII3_AWS/
Contém os arquivos CSV com os dados do banco de dados fornecido pela AWS:
- `avaliacoes.csv` - Reviews e avaliações de clientes
- `clientes.csv` - Dados dos clientes
- `geolocalizacao.csv` - Informações de geolocalização
- `itens_pedidos.csv` - Itens contidos em cada pedido
- `pagamentos.csv` - Registro de pagamentos
- `pedidos.csv` - Pedidos realizados
- `produtos.csv` - Catálogo de produtos
- `tabela_auxiliar.csv` - Dados auxiliares
- `vendedores.csv` - Informações dos vendedores

### 📁 Modelos/
Contém notebooks com análises e modelagem dos dados:
- `leIA.ipynb` - Análise de sentimentos usando LeIA (SentimentIntensityAnalyzer) nas avaliações de clientes, gerando a coluna `review_score_leia`

### 📁 Tratativas/
Contém funções de limpeza e transformação de dados:
- `tratativa.ipynb` - Notebook com funções utilitárias para:
  - Limpeza de texto (`limpar_avaliacoes`)
  - Remoção de linhas vazias (`remover_linhas_sem_review`)
  - Junção de campos (`juntar_titulo_mensagem`)
  - Remoção de colunas (`apagar_coluna`)
  - Conversão de tipos de dados (`converter_para_string`, `converter_para_datetime`)

#### ⚠️ Importante sobre Tratativas
**Não é necessário executar os arquivos de tratativas regularmente.** As funções definidas em `tratativa.ipynb` devem ser executadas **apenas quando há uma nova função de tratamento a ser implementada**. Após criar uma nova função, ela deve ser aplicada aos dados imediatamente e os dados salvos de volta na tabela original.
