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

### 📁 Tratativas/
Contém funções de limpeza e transformação de dados operando apenas em DataFrames em memória (sem gravar sobre os dados originais):
- `tratativas.ipynb` - Notebook com funções utilitárias para processamento de dados, ideal para uso em Google Colab.

Funções de tratamento disponíveis:
  - Limpeza de texto (`limpar_avaliacoes`)
  - Remoção de linhas vazias (`remover_linhas_sem_review`)
  - Junção de campos (`juntar_titulo_mensagem`)
  - Remoção de colunas (`apagar_coluna`)
  - Conversão de tipos de dados:
    - `converter_para_string` - Converte coluna para tipo string
    - `converter_para_datetime` - Converte coluna para tipo datetime
    - `converter_categorias` - Converte colunas categóricas (cidades, estados, categorias de produto, tipo de pagamento e status de pedido)
    - `converter_datas` - Converte todas as colunas de data para tipo datetime

## 🛠️ Bibliotecas e Tecnologias Utilizadas

### 📊 Manipulação e Análise de Dados
- **🐼 Pandas** - Manipulação e processamento de DataFrames
- **🔢 NumPy** - Operações matemáticas e manipulação de arrays
- **🔍 Regex (re)** - Limpeza e processamento de textos

### 📈 Visualização de Dados
- **📉 Matplotlib** - Criação de gráficos estáticos
- **🎨 Seaborn** - Visualizações estatísticas aprimoradas
- **🔷 Plotly** - Gráficos interativos e dinâmicos

### 🤖 Análise de Sentimentos
- **💬 vaderSentiment** - Análise de sentimentos em textos
- **🇧🇷 LeIA** - Análise de sentimentos otimizada para português brasileiro
- **☁️ TextBlob** - Processamento de linguagem natural e análise de sentimentos

### 🧠 Deep Learning e IA
- **🤗 Transformers** - Modelos de IA pré-treinados (BERT multilíngue)
- **🔥 PyTorch** - Framework de deep learning
- **⚙️ SentencePiece** - Tokenização de textos
- **📊 tqdm** - Barras de progresso para loops

## Modelos de Análise de Sentimentos

Foram avaliados e comparados três modelos diferentes para análise de sentimentos das avaliações:

### 🇧🇷 LeIA
O modelo LeIA possui como método a leitura do comentário e classificação por palavras como positivo, negativo e neutro, que podem ser modificadas para scores. Sua grande vantagem é que foi projetada para o português do Brasil, portanto seu resultado está mais de acordo com nosso objetivo, tendo em vista que ela compreende melhor gírias, abreviações e emojis, que são símbolos clássicos da comunicação no Brasil. Seu ponto forte também é a velocidade de processamento e leitura dos dados. As limitações do LeIA estão relacionadas principalmente ao idioma, tendo em vista que foi criada para entender a língua portuguesa, ela possui maiores dificuldades ao reconhecer uma língua estrangeira, perdendo assim a precisão do resultado.

### 💬 Vader
O Vader possui grande similaridade com o modelo LeIA, no entanto ela apresenta melhores resultados para textos na língua estrangeira, e para textos curtos na internet. Possui maior facilidade para compreender a intenção das pessoas ao utilizar letras maiúsculas como grito, ou exageros na pontuação como forma de demonstrar indignação. Suas vantagens estão associadas à velocidade que realiza a análise e na simplicidade de implementação no código, todavia as desvantagens estão relacionadas ao fato principal do idioma, tendo dificuldade de assimilar os textos em português, além de não possuir recursos que compreendem sentimentos mais complexos como a ironia.

### ☁️ TextBlob
O TextBlob trouxe métricas relevantes à pesquisa, mesmo apresentando resultados de acurácia inferiores aos demais, tornou-se possível com esse modelo medir a subjetividade do comentário, separando assim as opiniões puramente emocionais dos fatos racionais. Porém, por ter um padrão de reconhecimento de textos em inglês, fez-se necessário a utilização de bibliotecas externas para a tradução dos textos em português, resultando em uma maior complexidade na utilização do modelo. Além do TextBlob possuir uma maior rigidez, não compreendendo a linguagem informal da internet.

### 🤗 Transformers
O Transformers, é um dos modelos mais utilizados e com melhores resultado da análise. O modelo funciona realizando a leitura da frase completa, ao invés de palavra por palavra, assim compreendendo melhor contxto, ordem da gramática e o significado real por trás do comentário. Sua vantagem é ser capaz de compreender sentimentos mais complexos relacionados ao ser humano, identificando ironias, duplo sentido e sentimentos ocultos. Além de que possui familiaridade com a língua inglesa e portuguesa, funcionando da mesma forma para ambas as traduções. Também contendo diversas bibliotecas que geram diferentes resultados e análises do projeto. As desvantagens relacionadas a esse modelo é sua maior complexidade e robustez, com um processamento mais lento em comparação aos outros modelos.

#### ⚠️ Importante sobre Tratativas
**Não é necessário executar os arquivos de tratativas regularmente.** As funções definidas em `tratativas.ipynb` devem ser executadas **apenas quando há uma nova função de tratamento a ser implementada**.

**Sobre as Branches:**
- Na branch `main` (padrão), o arquivo `tratativas.ipynb` está disponível com todas as funções implementadas. A tabela `avaliacoes.csv` já está totalmente tratada.
- Na branch `tratativa-original`, estão disponíveis dois arquivos adicionais:
  - Um que **altera os dados originais** nos arquivos CSV
  - Um que **não altera** (versão segura para desenvolvimento)
- Na branch `dataset-original`, todas as tabelas permanecem no estado de origem (dados não tratados).