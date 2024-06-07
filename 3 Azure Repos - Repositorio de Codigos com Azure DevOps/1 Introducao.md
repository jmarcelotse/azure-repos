# azure-repos

Azure Repos é uma das funcionalidades do Azure DevOps, a plataforma de DevOps da Microsoft. Ele fornece repositórios de código-fonte que facilitam a colaboração, a gestão e o versionamento de código. Aqui estão alguns pontos principais sobre Azure Repos:

# Principais Funcionalidades:

1. **Repositórios Git**:
    - **Git**: Azure Repos oferece repositórios Git, que são sistemas de controle de versão distribuído amplamente utilizados. Isso permite que múltiplos desenvolvedores colaborem de forma eficiente.
    - **Branches**: Suporte completo a branches para que os desenvolvedores possam trabalhar em diferentes funcionalidades ou correções de bugs simultaneamente.

2. **Repositórios TFVC**:
    - **Team Foundation Version Control (TFVC)**: Também é oferecido para projetos que preferem um controle de versão centralizado.

3. **Pull Requests**:
    - **Código e Revisões**: Os desenvolvedores podem criar pull requests para discutir e revisar alterações de código antes de integrá-las ao branch principal. Isso ajuda a garantir a qualidade do código.

    - **Revisões e Comentários**: Ferramentas integradas para revisão de código, onde revisores podem adicionar comentários, sugerir alterações e aprovar o código.

4. **Branch Policies**:
    - **Políticas de Branch**: Permite definir políticas para branches específicos, como exigir revisões de código, builds bem-sucedidos, e outras validações antes de permitir merges.

5. **Histórico e Rastreabilidade**:
    - **Histórico de Commits**: Visibilidade completa sobre o histórico de commits, permitindo rastrear mudanças e entender a evolução do código.
    - **Links de Work Items**: Integração com Azure Boards para vincular commits a work items, facilitando a rastreabilidade entre código e tarefas/problemas.

6. **CI/CD Integration**:
    - **Continuous Integration/Continuous Deployment (CI/CD)**: Integração com Azure Pipelines para automação de builds e deployments, facilitando a entrega contínua de software.

7. **Segurança e Permissões**:
    - **Controles de Acesso**: Definição de permissões detalhadas para acesso a repositórios, branches e recursos específicos, garantindo que somente usuários autorizados possam realizar determinadas ações.

# Benefícios do Azure Repos:

 - **Colaboração Melhorada**: Ferramentas robustas para revisão de código e colaboração, ajudando equipes a manterem padrões de qualidade.
 - **Flexibilidade**: Suporte tanto a Git quanto a TFVC, permitindo que equipes escolham o sistema de controle de versão que melhor se adapta às suas necessidades.
 - **Integração Completa**: Parte do ecossistema Azure DevOps, permitindo uma integração perfeita com outros serviços como Azure Boards, Azure Pipelines e Azure Artifacts.
 - **Escalabilidade**: Projetado para suportar desde pequenos projetos até grandes organizações com múltiplos repositórios e desenvolvedores.

# Uso no Ciclo de Vida de Desenvolvimento:

1. **Desenvolvimento**:
    - Criação de branches para novas funcionalidades.
    - Commit e push de mudanças para o repositório remoto.

2. **Revisão e Integração**:
    - Criação de pull requests para revisões de código.
    - Implementação de políticas de branch para garantir qualidade.

3. **Entrega**:
    - Integração com Azure Pipelines para CI/CD.
    - Automação de builds e deployments.

# Como Começar:

1. Criar um Projeto no Azure DevOps: Se ainda não tiver, crie um projeto no Azure DevOps.
2. Adicionar um Repositório: No projeto, adicione um repositório Git ou TFVC.
3. Clone o Repositório: Clone o repositório para sua máquina local e comece a trabalhar.
4. Commits e Pushes: Faça commits das suas alterações e envie para o repositório remoto.
5. Pull Requests e Revisões: Utilize pull requests para revisão e integração de código.

Azure Repos é uma ferramenta poderosa que suporta a colaboração e a gestão de código de forma eficiente, integrando-se perfeitamente com outras ferramentas do Azure DevOps para um ciclo de vida de desenvolvimento completo e contínuo.

# Vou fornecer alguns exemplos práticos de como você pode usar o Azure Repos no ciclo de vida de desenvolvimento de software.

# Exemplo 1: Criando um Repositório Git

1. **Criar um Projeto no Azure DevOps**:
    - Acesse o portal do Azure DevOps e crie um novo projeto.

2. **Adicionar um Repositório**:
    - Dentro do projeto, navegue até a seção "Repos" e crie um novo repositório Git.
    - Você pode nomear seu repositório e adicionar uma descrição.

# Exemplo 2: Clonando e Adicionando Código ao Repositório

1. **Clonar o Repositório**:
    - Copie a URL do repositório Git que você acabou de criar.
    - No seu terminal ou Git Bash, clone o repositório para a sua máquina local:

    bash
    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

2. **Adicionar Código**:

    - Crie ou adicione seus arquivos de código ao diretório clonado.
    - Por exemplo, você pode adicionar um arquivo main.py:

    python
    # main.py
    print("Hello, Azure Repos!")

3. **Commit e Push**:

    - Adicione os arquivos ao stage e faça um commit:

    bash
    git add .
    git commit -m "Initial commit with main.py"
    git push origin main

# Exemplo 3: Criando e Gerenciando Pull Requests

1. **Criar uma Nova Branch**:
    - Crie uma nova branch para adicionar uma nova funcionalidade:

    bash
    git checkout -b feature/nova-funcionalidade

2. **Adicionar Código na Nova Branch**:

    - Faça as alterações no código. Por exemplo, adicione uma nova função ao main.py:

    python
    # main.py
    def nova_funcionalidade():
        print("Nova Funcionalidade")

    if __name__ == "__main__":
        print("Hello, Azure Repos!")
        nova_funcionalidade()

3. **Commit e Push na Nova Branch**:

    Adicione, comite e envie suas alterações para a branch remota:

    bash
    git add .
    git commit -m "Adicionada nova funcionalidade"
    git push origin feature/nova-funcionalidade

4. **Criar um Pull Request**:

    - No portal do Azure DevOps, vá para a seção "Repos" > "Pull Requests" e clique em "New Pull Request".
    - Selecione a branch feature/nova-funcionalidade como a fonte e a branch main como o destino.
    - Adicione uma descrição para o pull request e clique em "Create".

5. **Revisão de Código**:

    - Os membros da equipe podem revisar o pull request, adicionar comentários e sugestões.
    Após a revisão, os revisores podem aprovar o pull request.

6. **Completar o Pull Request**:

    - Uma vez aprovado, o pull request pode ser completado (merge) na branch main.

# Exemplo 4: Aplicando Políticas de Branch

1. **Definir Políticas de Branch**:
    - No Azure DevOps, navegue até "Repos" > "Branches".
    - Clique no ícone de configurações ao lado da branch main e selecione "Branch policies".
    - Configure políticas como:
        - Exigir revisões de pelo menos dois revisores.
        - Requerer que o código passe por builds bem-sucedidos.
        - Enforce política de merge commit para garantir histórico limpo.

# Exemplo 5: Integração com CI/CD usando Azure Pipelines

1. Criar um Pipeline de Build:
    - Navegue até "Pipelines" e clique em "New Pipeline".
    - Selecione o repositório onde o código está armazenado.
    - Configure o pipeline utilizando o YAML ou o assistente de configuração. Um exemplo de arquivo YAML para Python pode ser:

    yaml
    trigger:
    branches:
        include:
        - main
        - feature/*

    pool:
    vmImage: 'ubuntu-latest'

    steps:
    - task: UsePythonVersion@0
        inputs:
        versionSpec: '3.x'
        addToPath: true

    - script: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
        python -m unittest discover
        displayName: 'Install dependencies and run tests'

2. **Executar o Pipeline**:
    - Commit o arquivo YAML no repositório e o pipeline será acionado automaticamente com base nas regras de trigger definidas.

Esses exemplos mostram como configurar um repositório, gerenciar branches e pull requests, aplicar políticas de branch e integrar com pipelines de CI/CD no Azure DevOps usando Azure Repos.
