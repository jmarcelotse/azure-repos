# Editor Clássico no Azure Pipelines

O Editor Clássico no Azure Pipelines é uma interface gráfica que permite criar e gerenciar pipelines de build e release sem precisar escrever YAML manualmente. Ele é útil para quem prefere uma abordagem visual ou está começando a usar o Azure DevOps.

# Criando um Pipeline de Build com o Editor Clássico

Aqui está um guia passo a passo para criar um pipeline de build usando o Editor Clássico:

1. **Acesse o Azure DevOps**:
    - Faça login na sua conta do Azure DevOps.
    - Navegue até o projeto onde você deseja criar o pipeline.

2. **Acesse Pipelines**:
    - No menu lateral, clique em **Pipelines**.

3. **Crie um Novo Pipeline**:
    - Clique em **New Pipeline**.
    - Escolha **Use the classic editor** para usar o Editor Clássico.

4. **Selecione o Repositório**:
    - Escolha o repositório de código que você deseja usar. Pode ser Azure Repos Git, GitHub, Bitbucket, etc.
    - Clique em **Continue**.

5. **Escolha um Template**:
    - O Azure DevOps oferece vários templates para diferentes tipos de projetos (por exemplo, .NET, Node.js, Python).
        Selecione um template que melhor se adeque ao seu projeto ou escolha **Empty job** para começar do zero.

6. **Configure as Tarefas do Pipeline**:
    - Na tela de configuração do pipeline, você verá uma lista de fases e tarefas.
    - Clique em + para adicionar tarefas à fase.

Por exemplo, para um projeto .NET:
 - Adicione uma tarefa **Use .NET Core SDK**.
 - Adicione uma tarefa **Restore** para restaurar pacotes NuGet.
 - Adicione uma tarefa **Build** para compilar o projeto.
 - Adicione uma tarefa **Test** para executar testes unitários.

7. **Configurar Detalhes das Tarefas**:
    - Para cada tarefa adicionada, configure os detalhes necessários, como a versão do SDK, o caminho do projeto, os argumentos de build, etc.
    - Salve as configurações de cada tarefa.

8. **Salvar e Executar o Pipeline**:
    - Após configurar todas as tarefas, clique em **Save & queue** para salvar e executar o pipeline imediatamente.
    - Você pode também salvar sem executar clicando em **Save** e, em seguida, executar o pipeline manualmente mais tarde.

# Exemplo de Pipeline Clássico para um Projeto .NET

Aqui está um exemplo de configuração de um pipeline de build para um projeto .NET usando o Editor Clássico:

1. **Adicionar Tarefas ao Pipeline**:
    - **Use .NET Core SDK**: Configure a versão do .NET Core SDK (por exemplo, 5.x).
    - **NuGet Restore**: Configure para restaurar os pacotes NuGet do projeto.
    - **Build**: Configure para compilar o projeto com o comando dotnet build.
    - **Test**: Configure para executar testes unitários com o comando dotnet test.

2. **Detalhes das Tarefas**:
    - **Use .NET Core SDK**:
        - Version: 5.x
    - **NuGet Restore**:
        - Command: **dotnet restore**
        - Path to project(s): ****/*.csproj**
    - **Build**:
        - Command: **dotnet build**
        - Arguments: **--configuration Release**
        - Path to project(s): ****/*.csproj**
    - Test:
        - Command: **dotnet test**
        - Arguments: **--configuration Release**
        - Path to project(s): ****/*.Tests.csproj**

# Monitoramento e Análise

 - Após executar o pipeline, você pode monitorar o progresso e os logs de cada tarefa em tempo real.
 - Verifique os resultados dos testes e os artefatos gerados.
 - Configure notificações para receber alertas sobre o status do pipeline.

# Vantagens do Editor Clássico

 - **Interface Visual**: Ideal para quem prefere configurar pipelines de maneira visual.
 - **Templates Predefinidos**: Facilita a configuração inicial com templates predefinidos para diferentes tipos de projetos.
 - **Flexibilidade**: Permite adicionar e configurar tarefas detalhadamente sem precisar conhecer YAML.

# Considerações Finais

O Editor Clássico no Azure Pipelines é uma ferramenta poderosa para criar e gerenciar pipelines de build de forma visual e intuitiva. É uma excelente opção para equipes que estão começando com DevOps ou que preferem uma abordagem visual para configurar seus processos de CI/CD.

# Exemplo de Pipeline Clássico para um Projeto Java

Para configurar um pipeline clássico para um projeto Java no Azure Pipelines, siga os passos abaixo:

1. **Acesse o Azure DevOps**:
    - Faça login na sua conta do Azure DevOps.
    - Navegue até o projeto onde você deseja criar o pipeline.

2. **Acesse Pipelines**:
    - No menu lateral, clique em Pipelines.

3. **Crie um Novo Pipeline**:
    - Clique em **New Pipeline**.
    - Escolha **Use the classic editor** para usar o Editor Clássico.

4. **Selecione o Repositório**:
    - Escolha o repositório de código que você deseja usar. Pode ser Azure Repos Git, GitHub, Bitbucket, etc.
    - Clique em **Continue**.

5. **Escolha um Template**:
    - Selecione o template **Maven** ou **Gradle**, dependendo da ferramenta de build que você está usando. Neste exemplo, vamos usar **Maven**.

6. **Configure as Tarefas do Pipeline**:

    - Na tela de configuração do pipeline, você verá uma lista de fases e tarefas.

    - Adicione as seguintes tarefas:

    **Use a Maven Task**:

    - Task: **Maven**
    - Display name: **Build with Maven**
    - POM file: **pom.xml**
    - Goals and options: **clean install**

    **Run Unit Tests**:

    - Task: **Maven**
    - Display name: **Run Unit Tests**
    - POM file: **pom.xml**
    - Goals and options: **test**

7. **Salvar e Executar o Pipeline**:

 - Após configurar todas as tarefas, clique em **Save & queue** para salvar e executar o pipeline imediatamente.
 - Você pode também salvar sem executar clicando em **Save** e, em seguida, executar o pipeline manualmente mais tarde.

# Exemplo de Pipeline Clássico para um Projeto Python

Para configurar um pipeline clássico para um projeto Python no Azure Pipelines, siga os passos abaixo:

1. **Acesse o Azure DevOps**:
    - Faça login na sua conta do Azure DevOps.
    - Navegue até o projeto onde você deseja criar o pipeline.

2. **Acesse Pipelines**:
    - No menu lateral, clique em **Pipelines**.

3. **Crie um Novo Pipeline**:
    - Clique em **New Pipeline**.
    - Escolha **Use the classic editor** para usar o Editor Clássico.

4. **Selecione o Repositório**:
    - Escolha o repositório de código que você deseja usar. Pode ser Azure Repos Git, GitHub, Bitbucket, etc.
    - Clique em Continue.

5. **Escolha um Template**:
    - Selecione o template **Python Package**.

6. **Configure as Tarefas do Pipeline**:

    - Na tela de configuração do pipeline, você verá uma lista de fases e tarefas.

    - **Adicione as seguintes tarefas**:

    **Use Python Version**:

     - Task: **Use Python Version**
     - Display name: **Use Python 3.x**
     - Version Spec: **3.x**

    **Install Dependencies**:

     - Task: **Command Line**
     - Display name: **Install dependencies**
     - Script: **pip install -r requirements.txt**

    Run Unit Tests:
        Task: **Command Line**
        Display name: **Run Unit Tests**
        Script: **pytest**

7. **Salvar e Executar o Pipeline**:

    - Após configurar todas as tarefas, clique em **Save & queue** para salvar e executar o pipeline imediatamente.
    - Você pode também salvar sem executar clicando em **Save** e, em seguida, executar o pipeline manualmente mais tarde.

# Resumo das Configurações

**Pipeline Java com Maven**

1. **Use a Maven Task**:
     - **Task**: Maven
     - **Display name**: Build with Maven
     - **POM file**: pom.xml
     - **Goals and options**: clean install

2. **Run Unit Tests**:
     - **Task**: Maven
     - **Display name**: Run Unit Tests
     - **POM file**: pom.xml
     - **Goals and options**: test

# Pipeline Python

1. **Use Python Version**:
     - **Task**: Use Python Version
     - **Display name**: Use Python 3.x
     - **Version Spec**: 3.x

2. **Install Dependencies**:
     - **Task**: Command Line
     - **Display name**: Install dependencies
     - **Script**: pip install -r requirements.txt

3. **Run Unit Tests**:
     - **Task**: Command Line
     - **Display name**: Run Unit Tests
     - **Script**: pytest

Esses exemplos mostram como configurar pipelines clássicos para projetos Java e Python, utilizando o Editor Clássico no Azure DevOps. Cada pipeline é configurado para realizar tarefas comuns, como instalação de dependências, construção do projeto e execução de testes.