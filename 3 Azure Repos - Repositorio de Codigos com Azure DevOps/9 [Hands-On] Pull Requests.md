# [Hands-On] Pull Requests

# Hands-On: Criando e Gerenciando Pull Requests no Azure Repos

Este guia prático irá orientá-lo no processo de criação de pull requests e integração de mudanças no código principal através de revisões de código no Azure Repos, parte do Azure DevOps.

# Pré-requisitos

- Conta no Azure DevOps
- Git instalado em seu sistema
- Repositório Git configurado no Azure Repos

# 1. Clonando o Repositório

Se ainda não tiver o repositório clonado em sua máquina local, siga os passos abaixo:

1. **Obter a URL do Repositório**:
    - Na página de Repos no Azure DevOps, clique em "Clone" e copie a URL do repositório Git.

2. **Clonar o Repositório**:

    bash
    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

# 2. Criando uma Nova Branch

1. **Criar e Alternar para uma Nova Branch**:

    bash
    git checkout -b feature/nova-funcionalidade

*Isso cria uma nova branch chamada **feature/nova-funcionalidade** e alterna para ela.*

# 3. Fazendo Alterações na Nova Branch

1. **Adicionar ou Modificar Arquivos**:
    - Por exemplo, edite ou crie um arquivo **main.py**:

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

# 4. Enviando a Nova Branch para o Repositório Remoto

1. **Push da Branch para o Repositório Remoto**:

    bash
    git push origin feature/nova-funcionalidade

# 5. Criando um Pull Request no Azure DevOps

1. **Acessar a Seção de Pull Requests**:
    - No portal do Azure DevOps, vá para "Repos" > "Pull Requests".

2. **Criar um Novo Pull Request**:
    - Clique em "New Pull Request".
    - Selecione **feature/nova-funcionalidade** como a branch de origem e **main** como a branch de destino.
    - Adicione uma descrição detalhada do que foi alterado.
    - Clique em "Create".

# 6. Revisão de Código (Code Review)

1. **Revisar o Pull Request**:
    - Outros membros da equipe podem acessar o pull request criado, revisar o código, adicionar comentários e solicitar mudanças se necessário.

2. **Adicionar Comentários e Solicitar Mudanças**:
    - Durante a revisão, os revisores podem adicionar comentários diretamente nas linhas de código, indicando sugestões, problemas ou melhorias.
    - Se mudanças forem necessárias, os revisores podem solicitar alterações específicas antes de aprovar o pull request.

# 7. Resolvendo Comentários e Fazendo Novos Commits

1. **Responder e Resolver Comentários**:
    - O autor do pull request pode responder aos comentários e fazer os ajustes necessários no código.
    - Após fazer as alterações, adicione e comite as mudanças:

    bash
    git add .
    git commit -m "Corrige problemas apontados na revisão"
    git push origin feature/nova-funcionalidade

2. **Atualizar o Pull Request**:

    As novas alterações serão automaticamente adicionadas ao pull request existente. Os revisores podem então revisar novamente.

# 8. Completar o Pull Request

1. **Aprovar e Completar o Pull Request**:
    - Após as revisões e aprovações necessárias, o pull request pode ser completado (merged).
    - No portal do Azure DevOps, clique em "Complete" para mesclar a branch **feature/nova-funcionalidade** na branch **main**.

2. **Deletar a Branch**:
    - Após o merge, a branch temporária pode ser deletada para manter o repositório limpo.

    bash
    git branch -d feature/nova-funcionalidade
    git push origin --delete feature/nova-funcionalidade

# 9. Aplicando Políticas de Branch

1. **Configurar Políticas de Branch**:
    - No Azure DevOps, vá para "Repos" > "Branches".
    - Clique no ícone de configurações ao lado da branch main e selecione "Branch policies".
    - Defina políticas como:
        - Exigir revisões de código.
        - Exigir builds bem-sucedidos antes do merge.
        - Bloquear pushes diretos para a branch main.

# Resumo

Neste hands-on, abordamos a criação e gestão de pull requests no Azure Repos. Aprendemos a criar uma nova branch, fazer commits, enviar a branch para o repositório remoto, criar pull requests, realizar revisões de código e completar o merge das mudanças. Também vimos como configurar políticas de branch para garantir a qualidade do código e a conformidade com os padrões da equipe. Esses passos são essenciais para um fluxo de trabalho colaborativo e organizado no desenvolvimento de software.