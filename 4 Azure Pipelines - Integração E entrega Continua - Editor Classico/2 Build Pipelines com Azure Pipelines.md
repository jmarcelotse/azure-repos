# Build Pipelines com Azure Pipelines

Os pipelines de build com Azure Pipelines são uma parte fundamental do processo de Integração Contínua (CI), permitindo que você automatize a construção, teste e validação do seu código em várias plataformas. Aqui está uma explicação detalhada sobre como configurar e usar os pipelines de build no Azure Pipelines:

# Componentes Principais de um Pipeline de Build

1. **Repositório de Código**: O ponto de partida para qualquer pipeline de build é o repositório de código, que pode estar em Azure Repos, GitHub, Bitbucket, etc.

2. **Trigger**: Define quando o pipeline deve ser executado. Os gatilhos podem ser baseados em commits, pull requests, agendamentos ou manualmente.

3. **Agentes de Build**: Máquinas virtuais que executam as tarefas do pipeline. Você pode usar agentes hospedados pela Microsoft ou configurar seus próprios agentes auto-hospedados.

4. **Tarefas**: Passos individuais no pipeline que executam ações específicas, como restaurar pacotes, compilar código, executar testes, etc.

5. **Artefatos**: Produtos gerados pelo pipeline de build, como pacotes de aplicativos ou binários compilados, que podem ser usados em pipelines de liberação.

# Exemplo de Pipeline de Build com YAML

Aqui está um exemplo de um pipeline de build configurado usando um arquivo YAML para uma aplicação .NET:

    yaml

    #azure-pipelines.yml
    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    variables:
    buildConfiguration: 'Release'

    steps:
    - task: UseDotNet@2
    inputs:
        packageType: 'sdk'
        version: '5.x'
        installationPath: $(Agent.ToolsDirectory)/dotnet

    - task: NuGetToolInstaller@1

    - script: |
        dotnet restore
        dotnet build --configuration $(buildConfiguration)
    displayName: 'Restore and Build'

    - task: DotNetCoreCLI@2
    inputs:
        command: 'test'
        projects: '**/*Tests/*.csproj'
        arguments: '--configuration $(buildConfiguration) --no-build --verbosity normal'
    displayName: 'Run Tests'

    - task: PublishBuildArtifacts@1
    inputs:
        PathtoPublish: '$(Build.ArtifactStagingDirectory)'
        ArtifactName: 'drop'
        publishLocation: 'Container'

Os pipelines de build com Azure Pipelines são uma parte fundamental do processo de Integração Contínua (CI), permitindo que você automatize a construção, teste e validação do seu código em várias plataformas. Aqui está uma explicação detalhada sobre como configurar e usar os pipelines de build no Azure Pipelines:

# Componentes Principais de um Pipeline de Build

1. **Repositório de Código**: O ponto de partida para qualquer pipeline de build é o repositório de código, que pode estar em Azure Repos, GitHub, Bitbucket, etc.

2. **Trigger**: Define quando o pipeline deve ser executado. Os gatilhos podem ser baseados em commits, pull requests, agendamentos ou manualmente.

3. **Agentes de Build**: Máquinas virtuais que executam as tarefas do pipeline. Você pode usar agentes hospedados pela Microsoft ou configurar seus próprios agentes auto-hospedados.

4. **Tarefas**: Passos individuais no pipeline que executam ações específicas, como restaurar pacotes, compilar código, executar testes, etc.

5. **Artefatos**: Produtos gerados pelo pipeline de build, como pacotes de aplicativos ou binários compilados, que podem ser usados em pipelines de liberação.

# Exemplo de Pipeline de Build com YAML

Aqui está um exemplo de um pipeline de build configurado usando um arquivo YAML para uma aplicação .NET:

    yaml

    #azure-pipelines.yml
    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    variables:
    buildConfiguration: 'Release'

    steps:
    - task: UseDotNet@2
    inputs:
        packageType: 'sdk'
        version: '5.x'
        installationPath: $(Agent.ToolsDirectory)/dotnet

    - task: NuGetToolInstaller@1

    - script: |
        dotnet restore
        dotnet build --configuration $(buildConfiguration)
    displayName: 'Restore and Build'

    - task: DotNetCoreCLI@2
    inputs:
        command: 'test'
        projects: '**/*Tests/*.csproj'
        arguments: '--configuration $(buildConfiguration) --no-build --verbosity normal'
    displayName: 'Run Tests'

    - task: PublishBuildArtifacts@1
    inputs:
        PathtoPublish: '$(Build.ArtifactStagingDirectory)'
        ArtifactName: 'drop'
        publishLocation: 'Container'

# Explicação do YAML

1. **trigger**: Define que o pipeline será acionado por commits na branch **main**.

2. **pool**: Especifica o uso de uma máquina virtual Ubuntu para executar o pipeline.

3. **variables**: Define variáveis para o pipeline, como **buildConfiguration** que é usada para configurar a build como **Release**.

4. **steps**:
    - **UseDotNet@2**: Instala o SDK .NET necessário.
    - **NuGetToolInstaller@1**: Instala a ferramenta NuGet para gerenciamento de pacotes.
    - **script**: Executa comandos de script para restaurar pacotes e compilar o código.
    - **DotNetCoreCLI@2**: Executa testes de unidade no projeto.
    - **PublishBuildArtifacts@1**: Publica os artefatos gerados pela build.

# Configuração de um Pipeline de Build no Portal do Azure DevOps

1. **Criação do Pipeline**:
    - Acesse o portal do Azure DevOps.
    - Vá para **Pipelines** > **Builds**.
    - Clique em **New Pipeline**.
    - Selecione o repositório de código onde seu projeto está hospedado.

2. **Escolha de um Template**:
    - Azure DevOps oferece vários templates de pipeline. Você pode escolher um template pré-configurado ou começar com um pipeline vazio e adicionar as tarefas conforme necessário.

3. **Configuração das Tarefas**:
    - Adicione e configure as tarefas necessárias para seu pipeline, como restauração de pacotes, build, testes e publicação de artefatos.

4. **Execução do Pipeline**:
    - Salve e execute o pipeline. O Azure DevOps executará as tarefas configuradas, mostrando o progresso e os resultados de cada etapa.

5. **Monitoramento e Logs**:
        Após a execução, você pode monitorar os logs para cada tarefa, verificar os resultados dos testes e analisar os artefatos gerados.

# Benefícios dos Pipelines de Build

1. **Automatização**: Reduz o esforço manual e aumenta a eficiência, garantindo que cada alteração de código seja validada.
2. **Consistência**: Garante que o código seja construído de maneira consistente em diferentes ambientes.
3. **Detecção Precoce de Erros**: Ao executar testes automaticamente, os erros são detectados e corrigidos mais cedo.
4. **Feedback Rápido**: Os desenvolvedores recebem feedback imediato sobre as alterações de código, permitindo iterações rápidas.

# Boas Práticas

1. **Versionamento**: Utilize versionamento semântico para os artefatos gerados.
2. **Testes Automatizados**: Inclua uma ampla cobertura de testes automatizados para garantir a qualidade do código.
3. **Análise de Código**: Incorpore ferramentas de análise de código estático para detectar problemas de qualidade e segurança no código.
4. **Feedback do Pipeline**: Configure notificações para falhas no pipeline para que os desenvolvedores sejam alertados imediatamente.

Os pipelines de build no Azure Pipelines são uma ferramenta poderosa para automatizar o processo de construção e validação de código, promovendo práticas de desenvolvimento ágeis e de alta qualidade.

**Aqui estão exemplos de pipelines de build com Azure Pipelines, cobrindo diferentes linguagens e cenários. Vou mostrar exemplos para aplicações .NET, Node.js, e Python. Cada exemplo usa um arquivo YAML para definir o pipeline.**

# Exemplo 1: Aplicação .NET

    yaml

    #azure-pipelines.yml
    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    variables:
    buildConfiguration: 'Release'

    steps:
    - task: UseDotNet@2
    inputs:
        packageType: 'sdk'
        version: '5.x'
        installationPath: $(Agent.ToolsDirectory)/dotnet

    - script: |
        dotnet restore
        dotnet build --configuration $(buildConfiguration)
    displayName: 'Restore and Build'

    - task: DotNetCoreCLI@2
    inputs:
        command: 'test'
        projects: '**/*Tests/*.csproj'
        arguments: '--configuration $(buildConfiguration) --no-build --verbosity normal'
    displayName: 'Run Tests'

    - task: PublishBuildArtifacts@1
    inputs:
        PathtoPublish: '$(Build.ArtifactStagingDirectory)'
        ArtifactName: 'drop'
        publishLocation: 'Container'

# Exemplo 2: Aplicação Node.js

    yaml

    #azure-pipelines.yml
    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    steps:
    - task: NodeTool@0
    inputs:
        versionSpec: '14.x'
        checkLatest: true

    - script: |
        npm install
        npm run build
    displayName: 'Install and Build'

    - script: npm test
    displayName: 'Run Tests'

    - task: PublishBuildArtifacts@1
    inputs:
        PathtoPublish: 'dist'
        ArtifactName: 'drop'
        publishLocation: 'Container'

# Exemplo 3: Aplicação Python

    yaml
    #azure-pipelines.yml
    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    steps:
    - task: UsePythonVersion@0
    inputs:
        versionSpec: '3.x'
        addToPath: true

    - script: |
        python -m venv venv
        source venv/bin/activate
        pip install -r requirements.txt
    displayName: 'Setup Python Environment'

    - script: |
        source venv/bin/activate
        python setup.py build
    displayName: 'Build'

    - script: |
        source venv/bin/activate
        pytest
    displayName: 'Run Tests'

    - task: PublishBuildArtifacts@1
    inputs:
        PathtoPublish: 'dist'
        ArtifactName: 'drop'
        publishLocation: 'Container'

# Explicação dos Exemplos

1. **Trigger**: Cada pipeline é acionado por commits na branch main.
2. **Pool**: Usa uma máquina virtual Ubuntu para executar as tarefas do pipeline.
3. **Variables** (opcional): Define variáveis para configurar o pipeline (exemplo do .NET).
4. **Steps**: Conjunto de tarefas a serem executadas no pipeline.

# Passos Detalhados:

1. **Instalação de Ferramentas**:
    - **.NET**: Usa a tarefa **UseDotNet** para instalar o SDK .NET.
    - **Node.js**: Usa a tarefa **NodeTool** para instalar o Node.js.
    - **Python**: Usa a tarefa **UsePythonVersion** para instalar o Python.

2. **Construção e Testes**:

    - **.NET**: Executa **dotnet restore**, **dotnet build** e **dotnet test**.
    - **Node.js**: Executa **npm install**, **npm run build** e **npm test**.
    - **Python**: Configura um ambiente virtual, instala dependências com **pip**, compila com **python setup.py build** e executa testes com **pytest**.

3. **Publicação de Artefatos**:

    - Todos os exemplos usam a tarefa **PublishBuildArtifacts** para publicar os artefatos gerados durante a build.

# Configuração no Portal do Azure DevOps

1. **Criar o Pipeline**:
    - Acesse o portal do Azure DevOps.
    - Vá para Pipelines > Builds.
    - Clique em New Pipeline.
    - Selecione o repositório de código.
    - Escolha a opção de configuração YAML e adicione o conteúdo do arquivo YAML correspondente.

2. **Execução e Monitoramento**:

    - Salve e execute o pipeline.
    - Monitore a execução em tempo real, verificando logs e resultados de cada tarefa.
    - Após a execução, verifique os artefatos publicados e os resultados dos testes.

# Dicas e Boas Práticas

- **Use Variáveis**: Utilize variáveis para tornar o pipeline mais flexível e fácil de configurar.
- **Automatize Testes**: Sempre inclua etapas de testes automatizados para garantir a qualidade do código.
- **Monitoramento e Notificações**: Configure notificações para falhas no pipeline para que a equipe seja alertada imediatamente.
- **Documentação**: Documente cada etapa do pipeline para que a equipe entenda o fluxo de trabalho e possa fazer ajustes conforme necessário.

Esses exemplos fornecem uma base sólida para começar a configurar pipelines de build no Azure Pipelines para diferentes tipos de projetos.
