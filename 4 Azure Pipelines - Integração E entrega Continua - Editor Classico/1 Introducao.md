# Azure Pipeline

Azure Pipelines é um serviço no Azure DevOps que permite a automação do processo de compilação, teste e implantação de aplicações. Ele oferece suporte a uma ampla gama de linguagens de programação e tipos de projetos, incluindo .NET, Java, Node.js, Python, entre outros.

Aqui estão os principais componentes e conceitos do Azure Pipelines:

1. **Pipeline**: Um pipeline é uma definição de um conjunto de tarefas que são executadas em sequência. Pode incluir fases de compilação, teste e implantação. Os pipelines podem ser configurados usando YAML (um formato de arquivo de texto) ou através da interface gráfica do Azure DevOps.

2. **Agent**: Um agente é uma VM ou contêiner que executa as tarefas no pipeline. Existem agentes hospedados pela Microsoft, que são gerenciados pelo Azure, e agentes auto-hospedados, que são configurados e mantidos pelo próprio usuário.

3. **Stages, Jobs e Steps**:
    - **Stage**: Uma fase do pipeline que pode incluir uma ou mais etapas de trabalho.
    - **Job**: Um conjunto de tarefas que são executadas em um agente.
    - **Step**: Uma tarefa individual dentro de um job. Pode ser um script, uma ação de compilação, um teste, etc.

4. **Triggers**: São eventos que iniciam a execução do pipeline. Podem ser configurados para disparar a partir de mudanças no repositório de código (por exemplo, quando uma nova alteração é enviada ao branch principal), em um horário específico, ou manualmente.

5. **Artifacts**: São os resultados produzidos por um pipeline, como pacotes de código compilado, binários, ou pacotes de instalação. Esses artifacts podem ser armazenados e usados em fases posteriores do pipeline.

6. **Deployments**: Azure Pipelines permite a configuração de implantações contínuas, onde o código é automaticamente implantado em ambientes de teste, staging ou produção após passar por todas as fases de compilação e teste.

Exemplo de um pipeline YAML básico:

    yaml

    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    steps:
    - script: echo Hello, World!
    displayName: 'Run a one-line script'

    - script: |
        echo Add other tasks to build, test, and deploy your project.
        echo See https://aka.ms/yaml
    displayName: 'Run a multi-line script'

Esse exemplo básico ilustra um pipeline que é acionado por mudanças no branch main e executa algumas tarefas simples em um agente com a imagem ubuntu-latest.

Azure Pipelines é uma ferramenta poderosa para implementar práticas de DevOps, facilitando a entrega contínua e a integração contínua (CI/CD) de software, melhorando a eficiência e a qualidade do desenvolvimento de software.

Azure Pipeline é uma ferramenta da Microsoft Azure que facilita a integração contínua (CI) e a entrega contínua (CD) de software.

# Integração Contínua (CI)

Integração contínua é uma prática de desenvolvimento de software onde os desenvolvedores regularmente mesclam suas mudanças de código em um repositório central, após o qual são executadas construções automáticas e testes. Os principais benefícios da CI incluem:

1. **Detecção Precoce de Erros**: Ao integrar mudanças de código com frequência, os erros podem ser identificados e corrigidos mais rapidamente.
2. **Melhoria da Qualidade do Código**: Com testes automáticos executados em cada integração, a qualidade do código melhora consistentemente.
3. **Automação**: Processos automáticos reduzem o esforço manual e aumentam a eficiência.

# Entrega Contínua (CD)

Entrega contínua é uma abordagem onde o código é sempre implantável em produção. Vai além da integração contínua ao implantar automaticamente as mudanças de código em ambientes de teste e produção. Os benefícios incluem:

1. **Implantação Rápida e Segura**: Automação das implantações reduz os riscos associados a mudanças manuais e acelera o processo.
2. **Feedback Contínuo**: A automação permite um feedback mais rápido sobre as mudanças de código.
3. **Menor Tempo de Recuperação**: Em caso de falhas, é mais fácil reverter para um estado anterior estável.

# Azure Pipelines

Azure Pipelines oferece uma solução robusta para CI/CD com as seguintes funcionalidades:

1. **Pipeline de Construção**: Define como o código será construído e testado. Pode ser configurado para diferentes plataformas, como Windows, Linux, e macOS.
2. **Pipeline de Liberação**: Define como o código será implantado em diferentes ambientes (desenvolvimento, teste, produção).
3. **Suporte a Repositórios Diversos**: Funciona com vários repositórios de código, incluindo GitHub, Azure Repos, e Bitbucket.
4. **Agentes Hospedados e Auto-Hospedados**: Oferece agentes na nuvem para executar tarefas de CI/CD ou permite o uso de agentes personalizados.
5. **Integração com Ferramentas de Teste**: Suporta diversas ferramentas de teste para garantir que o código seja testado exaustivamente antes da implantação.
6. **Monitoramento e Relatórios**: Fornece ferramentas para monitorar e relatar o status das construções e implantações.

# Fluxo de Trabalho

1. **Código é Commitado**: Os desenvolvedores fazem commit do código no repositório.
2. **Trigger de Pipeline**: O commit aciona o pipeline de CI, que constrói e testa o código automaticamente.
3. **Build e Testes**: Se a build e os testes forem bem-sucedidos, o pipeline de CD é acionado.
4. **Implantação**: O código é implantado automaticamente nos ambientes configurados (teste, homologação, produção).
5. **Monitoramento**: O pipeline é monitorado para garantir que tudo esteja funcionando conforme esperado.

Azure Pipelines, portanto, simplifica e automatiza o processo de desenvolvimento e implantação de software, permitindo que as equipes entreguem valor mais rapidamente e com maior qualidade.

# Aqui estão exemplos de como configurar pipelines de integração contínua (CI) e entrega contínua (CD) no Azure Pipelines:

# Exemplo de Pipeline de Integração Contínua (CI)

1. Arquivo YAML para CI

    yaml

    #azure-pipelines.yml
    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    steps:
    - task: UseDotNet@2
    inputs:
        packageType: 'sdk'
        version: '5.x'
        installationPath: $(Agent.ToolsDirectory)/dotnet

    - script: dotnet build --configuration Release
    displayName: 'Build project'

    - script: dotnet test --configuration Release
    displayName: 'Run tests'

*Este exemplo configura um pipeline que é acionado por commits na branch **main**. Ele usa uma máquina virtual Ubuntu, instala o SDK .NET, constrói o projeto e executa testes.*

# Exemplo de Pipeline de Entrega Contínua (CD)

1. **Pipeline de Liberação no Azure Pipelines**

Para criar um pipeline de liberação no portal do Azure DevOps, siga os passos:

- Vá para Pipelines > Releases.
- Clique em New pipeline.
- Selecione uma template, como Azure App Service deployment.
- Configure os Artifacts (artefatos) que serão liberados. Por exemplo, o artefato da build de CI anterior.
- Adicione Stages (estágios), como Desenvolvimento, Teste, Produção.
- Configure Tasks (tarefas) em cada estágio para realizar as implantações.

# Exemplo de YAML para CD

Um pipeline de CD em YAML pode ser mais complexo, dependendo do ambiente e do tipo de aplicação. Aqui está um exemplo simples para uma aplicação web:

    yaml

    trigger:
    - main

    pool:
    vmImage: 'ubuntu-latest'

    steps:
    - task: UseDotNet@2
    inputs:
        packageType: 'sdk'
        version: '5.x'
        installationPath: $(Agent.ToolsDirectory)/dotnet

    - script: dotnet publish -c Release -o $(Build.ArtifactStagingDirectory)
    displayName: 'Publish project'

    - task: PublishBuildArtifacts@1
    inputs:
        PathtoPublish: '$(Build.ArtifactStagingDirectory)'
        ArtifactName: 'drop'
        publishLocation: 'Container'

    stages:
    - stage: Deploy
    jobs:
    - deployment: DeployWebApp
        environment: 'production'
        strategy:
        runOnce:
            deploy:
            steps:
            - task: DownloadBuildArtifacts@0
                inputs:
                buildType: 'current'
                downloadType: 'single'
                artifactName: 'drop'
                downloadPath: '$(System.ArtifactsDirectory)'

            - task: AzureWebApp@1
                inputs:
                azureSubscription: '<sua-suscrição-azure>'
                appType: 'webApp'
                appName: '<nome-do-seu-app>'
                package: '$(System.ArtifactsDirectory)/drop'

Neste exemplo:

- O pipeline é acionado por commits na branch main.
- Uma máquina virtual Ubuntu é usada.
- O SDK .NET é instalado.
- O projeto é publicado e os artefatos são armazenados.
- Um estágio de implantação é configurado, que baixa os artefatos e os implanta em um serviço de Aplicativo Web no Azure.

# Configuração Detalhada no Portal Azure DevOps

1. **Configurar Pipeline de Build**:
    - Acesse o portal do Azure DevOps.
    - Vá para Pipelines > Builds.
    - Clique em New Pipeline.
    - Selecione o repositório de código.
    - Escolha Starter pipeline ou use um template específico.
    - Edite o arquivo YAML conforme necessário e salve.

2. **Configurar Pipeline de Liberação**:
    - Vá para Pipelines > Releases.
    - Clique em New pipeline.
    - Adicione um artefato, selecionando a build que foi configurada anteriormente.
    - Configure os estágios de implantação (Desenvolvimento, Teste, Produção).
    - Adicione tarefas aos estágios, como tarefas de implantação no Azure App Service.

# Observações

- **Credenciais e Conexões**: Certifique-se de que as conexões com o Azure estão configuradas corretamente no Azure DevOps, usando Service Connections.
- **Testes Automatizados**: É recomendável adicionar testes automatizados em várias etapas para garantir a qualidade do código antes da implantação.
- **Monitore e Ajuste**: Monitore os pipelines regularmente e ajuste conforme necessário para otimizar o desempenho e a confiabilidade.

Esses exemplos demonstram como configurar pipelines básicos de CI e CD no Azure Pipelines. Dependendo das necessidades do seu projeto, você pode adicionar etapas adicionais, configurar mais estágios de implantação e personalizar ainda mais as configurações.
