# Arquitetura de pastas do App Mobile Clude

```plaintext
/src
  /assets               # Imagens, fontes e outros recursos estáticos.
  /components           # Componentes modulares e reutilizáveis, feitos para serem globais.
  /hooks                # Hooks globais para facilitar a manipulação dos dados e lógicas de negócio.
    use-[nome-do-hook-global].ts # A nomenclatura de um hook sempre começa com "use", seguida do nome dele.
  /{models, services ou api}    # Gerenciamento dos dados vindos da API para a aplicação. 
                                # Devem ser colocadas nesta camada apenas as chamadas que serão feitas em diversos lugares do app.
  /screens              # Telas do aplicativo.
    /[nome-da-tela]
      /components       # Componentes locais, feitos para serem usados apenas nesta tela.
      /{models, services ou api} # Chamadas de API e manipulação de dados destinadas apenas para esta tela específica. 
                                 # Nunca devem incluir endpoints que possam ser utilizados em outros lugares.
      /interface ou dtos        # Tipagem dos dados.
      /view              # Pasta destinada apenas à visualização da tela.
        [nome-da-tela]-view.tsx # Arquivo destinado apenas à renderização da tela e seus componentes.
        styles.ts        # Arquivo destinado apenas à estilização (CSS).
      index.tsx          # Middleware usado para reduzir a quantidade de código em cada componente 
                         # e conectar a lógica à parte visual.
      use-[nome-da-tela].ts      # Hooks locais criados para facilitar a manipulação dos dados e lógicas de negócio.
  /store                # Pasta com as actions.
  /reducers             # Pasta que armazena todos os arquivos dos reducers e suas actions.
    [nome-da-tela]-reducer.ts
    ...
  index.ts             # Arquivo de configuração dos reducers de todo o app.
  /utils                # Utilidades e funções auxiliares.
    /async-storage      # Função para armazenamento local, utilizando a memória do celular.
    ...
app.tsx                # Arquivo raiz feito para compilar todo o aplicativo, também responsável por organizar a navegação entre telas do app.
