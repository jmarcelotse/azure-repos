# Azure Repos - Repositorio GIT do Azure DevOps

Azure Repos é a solução de repositório Git do Azure DevOps que oferece suporte ao controle de versão, permitindo que equipes de desenvolvimento colaborem e gerenciem o código de forma eficiente. A seguir, detalho como usar os recursos principais do Azure Repos com exemplos práticos.

1. # Criar um Repositório Git
Passo a Passo:

 1. **Acesse o Azure DevOps**:
    - Vá para o portal Azure DevOps.
    - Crie um novo projeto ou selecione um projeto existente.

 2. **Adicionar um Repositório Git**:
    - Dentro do seu projeto, vá para "Repos" no menu lateral.
    - Clique em "Initialize" para criar um novo repositório Git vazio.

2. # Clonar o Repositório e Adicionar Código

**Clonar o Repositório**:

 1. **Obter a URL do Repositório**:
    - Na página de Repos, clique em "Clone" e copie a URL do repositório Git.

 2. **Executar o Clone no Terminal**:

        bash
        git clone <URL_DO_REPOSITORIO>
        cd <NOME_DO_REPOSITORIO>

# Adicionar e Commitar Código:

  1. Adicionar Arquivos:
    - Crie ou adicione arquivos no diretório clonado. Por exemplo:

        python
        # main.py
        print("Hello, Azure Repos!")

  2. **Commitar e Push**:

        bash
        git add .
        git commit -m "Initial commit with main.py"
        git push origin main

  3. # Criar e Gerenciar Pull Requests

**Criar uma Nova Branch**:

  1. **Criar e Alternar para uma Nova Branch**:

        bash
        git checkout -b feature/nova-funcionalidade

  2. **Adicionar Código na Nova Branch**:

        python
        # main.py
        def nova_funcionalidade():
            print("Nova Funcionalidade")

        if __name__ == "__main__":
            print("Hello, Azure Repos!")
            nova_funcionalidade()

  3. **Commitar e Push**:

        bash
        git add .
        git commit -m "Adicionada nova funcionalidade"
        git push origin feature/nova-funcionalidade

**Criar um Pull Request**:

  1. **Criar Pull Request no Portal do Azure DevOps**:
    - Vá para "Repos" > "Pull Requests" e clique em "New Pull Request".
    - Selecione a branch feature/nova-funcionalidade como fonte e main como destino.
    - Adicione uma descrição e clique em "Create".

**Revisão e Merge**:

  1. **Revisar o Código**:
    - Os membros da equipe podem adicionar comentários e sugerir alterações.
    - Após a revisão, o pull request pode ser aprovado.

  2. **Completar o Pull Request**:

    - Após aprovação, clique em "Complete" para fazer o merge da branch **feature/nova-funcionalidade** na branch **main**

4. # Aplicar Políticas de Branch

**Definir Políticas de Branch**:

  1. **Configurar Políticas**:
    - Vá para "Repos" > "Branches".
    - Clique no ícone de configurações ao lado da branch main e selecione "Branch policies".
    - Defina políticas, como:
        - Exigir revisões de código.
        - Exigir builds bem-sucedidos.
        - Bloquear pushes diretos para a branch main.

5. # Integração com Azure Pipelines

**Criar um Pipeline de Build**:

  1. Configurar o Pipeline:
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

Azure Repos é uma ferramenta poderosa que facilita a gestão de código-fonte com suporte a Git, proporcionando uma colaboração eficiente entre desenvolvedores. Com recursos como pull requests, políticas de branch, e integração com pipelines de CI/CD, o Azure Repos oferece uma solução completa para o ciclo de vida de desenvolvimento de software.