# [Hands-On] Usando GIT com Comandos

# Hands-On: Usando Git com Comandos no Azure Repos

Neste guia prático, você aprenderá a usar comandos Git para gerenciar um repositório no Azure Repos. Vamos cobrir desde a clonagem do repositório até a criação de branches, commits, pull requests, e a aplicação de políticas de branch.

# Pré-requisitos

- Conta no Azure DevOps
- Git instalado em seu sistema
- Repositório Git configurado no Azure Repos

# 1. Configuração Inicial

1. **Configurar Nome de Usuário e Email**:

    bash

    git config --global user.name "Seu Nome"
    git config --global user.email "seuemail@exemplo.com"

# 2. Clonando o Repositório:

1. **Obter a URL do Repositório**:
    - Na página de Repos no Azure DevOps, clique em "Clone" e copie a URL do repositório Git.

2. **Clonar o Repositório**:

    bash

    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

# 3. Criando e Alternando para uma Nova Branch

1. **Criar e Alternar para uma Nova Branch**:

    bash

    git checkout -b feature/nova-funcionalidade

# 4. Fazendo Alterações e Commitando

1. Adicionar ou Modificar Arquivos:
    - Por exemplo, crie ou edite um arquivo **main.py**:

    python

    # main.py
    def nova_funcionalidade():
        print("Nova Funcionalidade")

    if __name__ == "__main__":
        print("Hello, Azure Repos!")
        nova_funcionalidade()

2. **Adicionar as Alterações ao Stage**:

    bash

    git add main.py

3. **Commitar as Alterações**:

    bash

    git commit -m "Adicionada nova funcionalidade"

# 5. Enviando a Nova Branch para o Repositório Remoto

1. **Push da Branch para o Repositório Remoto**:

    bash
    git push origin feature/nova-funcionalidade

# 6. Criando um Pull Request no Azure DevOps

1. **Acessar a Seção de Pull Requests**:
    - No portal do Azure DevOps, vá para "Repos" > "Pull Requests".

2. **Criar um Novo Pull Request**:
    - Clique em "New Pull Request".
    - Selecione **feature/nova-funcionalidade** como a branch de origem e **main** como a branch de destino.
    - Adicione uma descrição detalhada do que foi alterado.
    - Clique em "Create".

# 7. Revisão de Código (Code Review)

1. **Revisar o Pull Request**:
    - Outros membros da equipe podem acessar o pull request criado, revisar o código, adicionar comentários e solicitar mudanças se necessário.

2. **Adicionar Comentários e Solicitar Mudanças**:
    - Durante a revisão, os revisores podem adicionar comentários diretamente nas linhas de código, indicando sugestões, problemas ou melhorias.
    - Se mudanças forem necessárias, os revisores podem solicitar alterações específicas antes de aprovar o pull request.

# 8. Resolvendo Comentários e Fazendo Novos Commits

1. **Responder e Resolver Comentários**:
    - O autor do pull request pode responder aos comentários e fazer os ajustes necessários no código.
    - Após fazer as alterações, adicione e comite as mudanças:

        bash

        git add .
        git commit -m "Corrige problemas apontados na revisão"
        git push origin feature/nova-funcionalidade

2. **Atualizar o Pull Request**:

    - As novas alterações serão automaticamente adicionadas ao pull request existente. Os revisores podem então revisar novamente.

# 9. Completar o Pull Request

1. **Aprovar e Completar o Pull Request**:
    - Após as revisões e aprovações necessárias, o pull request pode ser completado (merged).
    - No portal do Azure DevOps, clique em "Complete" para mesclar a branch **feature/nova-funcionalidade** na branch **main**.

2. **Deletar a Branch**:

    - Após o merge, a branch temporária pode ser deletada para manter o repositório limpo.

    bash

    git branch -d feature/nova-funcionalidade
    git push origin --delete feature/nova-funcionalidade

# 10. Aplicando Políticas de Branch

1. Configurar Políticas de Branch:
    - No Azure DevOps, vá para "Repos" > "Branches".
    - Clique no ícone de configurações ao lado da branch **main** e selecione "Branch policies".
    - Defina políticas como:
        - Exigir revisões de código.
        - Exigir builds bem-sucedidos antes do merge.
        - Bloquear pushes diretos para a branch **main**.
        - Exigir vínculo a work items.

# Resumo

Neste hands-on, você aprendeu a usar comandos Git para gerenciar um repositório no Azure Repos. Cobrimos desde a clonagem do repositório, criação de branches, commits, envio de branches para o repositório remoto, criação de pull requests, revisão de código, resolução de comentários e merge de pull requests. Também vimos como aplicar políticas de branch para garantir a qualidade do código e a conformidade com os padrões da equipe. Esses passos são fundamentais para um fluxo de trabalho colaborativo e organizado no desenvolvimento de software.