# [Hands-On] Repositorios Git no Azure Repos

# Hands-On: Repositórios Git no Azure Repos

Este guia prático mostrará como configurar e usar repositórios Git no Azure Repos, parte do Azure DevOps. Vamos cobrir a criação de um projeto, inicialização de um repositório, clonagem, commits, criação de branches e pull requests.

# Pré-requisitos

 - Conta no Azure DevOps
 - Git instalado em seu sistema

 1. # Criando um Projeto no Azure DevOps

    1. **Acesse o Azure DevOps**:
        - Vá para o portal Azure DevOps.
        - Faça login com sua conta Microsoft.

    2. **Criar um Novo Projeto**:
        - Clique em "New Project".
        - Dê um nome ao projeto, adicione uma descrição, escolha a visibilidade (public ou private) e clique em "Create".

2. # Inicializando um Repositório Git

    1. **Acesse o Repositório**:
        - No seu projeto recém-criado, vá para a seção "Repos" no menu lateral.
        - Clique em "Initialize" para criar um novo repositório Git vazio.

3. # Clonando o Repositório para o Seu Computador

    1. **Obter a URL do Repositório**:
        - Na página de Repos, clique em "Clone" e copie a URL do repositório Git.

    2. **Executar o Clone no Terminal**:

        bash
        git clone <URL_DO_REPOSITORIO>
        cd <NOME_DO_REPOSITORIO>

4. # Adicionando e Commitando Código

    1. **Adicionar Arquivos**:
        - Crie um arquivo main.py no diretório clonado com o seguinte conteúdo:

        python
        # main.py
        print("Hello, Azure Repos!")

    2. **Adicionar, Commitar e Enviar para o Repositório**:

        bash
        git add .
        git commit -m "Initial commit with main.py"
        git push origin main

5. # Criando e Gerenciando Branches

    1. **Criar uma Nova Branch**:

        bash
        git checkout -b feature/nova-funcionalidade

    2. **Adicionar Código na Nova Branch**:

        - Edite o arquivo main.py:

        python
        # main.py
        def nova_funcionalidade():
            print("Nova Funcionalidade")

        if __name__ == "__main__":
            print("Hello, Azure Repos!")
            nova_funcionalidade()

    3. **Commitar e Push na Nova Branch**:

        bash
        git add .
        git commit -m "Adicionada nova funcionalidade"
        git push origin feature/nova-funcionalidade

6. # Criando um Pull Request

    1. **Criar Pull Request no Azure DevOps**:
        - No portal do Azure DevOps, vá para "Repos" > "Pull Requests" e clique em "New Pull Request".
        - Selecione a branch **feature/nova-funcionalidade** como fonte e **main** como destino.
        - Adicione uma descrição e clique em "Create".

    2. **Revisão de Código**:
        - Os membros da equipe podem adicionar comentários e sugerir alterações.
        - Após a revisão, o pull request pode ser aprovado.

    3. **Completar o Pull Request**:
        - Após a aprovação, clique em "Complete" para fazer o merge da branch **feature/nova-funcionalidade** na branch **main**.

7. # Aplicar Políticas de Branch

    1. Configurar Políticas de Branch:
        - Vá para "Repos" > "Branches".
        - Clique no ícone de configurações ao lado da branch main e selecione "Branch policies".
        - Defina políticas, como:
            - Exigir revisões de código.
            - Exigir builds bem-sucedidos.
            - Bloquear pushes diretos para a branch main.

8. # Integração com Azure Pipelines

    1. **Criar um Pipeline de Build**:
        - Vá para "Pipelines" e clique em "New Pipeline".
        - Selecione o repositório onde o código está armazenado.
        - Configure o pipeline utilizando o YAML. Exemplo para um projeto Python:

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

        2. **Commitar o Arquivo YAML**:
            - Adicione este arquivo ao seu repositório e faça o commit.
            - O pipeline será acionado automaticamente com base nas triggers configuradas.

# Resumo

Neste hands-on, configuramos um repositório Git no Azure Repos, clonamos o repositório, fizemos commits, criamos branches, gerenciamos pull requests e configuramos políticas de branch. Além disso, integramos nosso repositório com Azure Pipelines para automação de builds. Esses passos cobrem as operações básicas e essenciais para o uso de Git no Azure DevOps, permitindo uma colaboração eficiente e um fluxo de trabalho estruturado para desenvolvimento de software.
