# Hands-On: Trabalhando com Branches no Git

Este guia prático detalha como criar, gerenciar e trabalhar com branches em um repositório Git no Azure Repos. Branches são fundamentais para isolar e organizar diferentes linhas de desenvolvimento, como novas funcionalidades, correções de bugs ou experimentos.

# Pré-requisitos

    - Conta no Azure DevOps
    - Git instalado em seu sistema
    - Repositório Git configurado no Azure Repos

1. # Clonando o Repositório

Se ainda não tiver o repositório clonado em sua máquina local, siga os passos abaixo:

1. **Obter a URL do Repositório**:

    Na página de Repos no Azure DevOps, clique em "Clone" e copie a URL do repositório Git.

2. **Clonar o Repositório**:

    bash
    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

2. # Criando uma Nova Branch

    1. **Criar e Alternar para uma Nova Branch**:

    bash
    git checkout -b feature/nova-funcionalidade

    *Isso cria uma nova branch chamada **feature/nova-funcionalidade** e alterna para ela.*

3. # Fazendo Alterações na Nova Branch

    1. Adicionar ou Modificar Arquivos:
        - Por exemplo, edite o arquivo **main.py**:

        python
        # main.py
        def nova_funcionalidade():
            print("Nova Funcionalidade")

        if __name__ == "__main__":
            print("Hello, Azure Repos!")
            nova_funcionalidade()

    2. **Adicionar as Alterações ao Stage**:

        bash
        git add .

    3. **Commitar as Alterações**:

        bash
        git commit -m "Adicionada nova funcionalidade"

4. # Enviando a Nova Branch para o Repositório Remoto

    1. Push da Branch para o Repositório Remoto:

        bash

        git push origin feature/nova-funcionalidade

5. # Criando um Pull Request no Azure DevOps

    1. Acessar a Seção de Pull Requests:
        - No portal do Azure DevOps, vá para "Repos" > "Pull Requests".

    2. **Criar um Novo Pull Request**:
        - Clique em "New Pull Request".
        - Selecione **feature/nova-funcionalidade** como a branch de origem e **main** como a branch de destino.
        - Adicione uma descrição e clique em "Create".

6. # Revisão e Merge do Pull Request

    1. **Revisar o Código**:
        - Outros desenvolvedores podem revisar o pull request, adicionar comentários e sugerir alterações.

    2. **Completar o Pull Request**:
        - Após a revisão e aprovação, clique em "Complete" para fazer o merge da branch **feature/nova-funcionalidade** na branch **main**.

7. # Aplicando Políticas de Branch

    1. **Configurar Políticas de Branch**:
        - No Azure DevOps, vá para "Repos" > "Branches".
        - Clique no ícone de configurações ao lado da branch **main** e selecione "Branch policies".
        - Defina políticas, como:
            - Exigir revisões de código.
            - Exigir builds bem-sucedidos.
            - Bloquear pushes diretos para a branch **main**.

8. # Sincronizando a Branch Local com o Repositório Remoto

    1. **Alternar para a Branch main**:
        bash
        git checkout main

    2. **Atualizar a Branch main com as Últimas Alterações**:

        bash
        git pull origin main

    3. **Deletar a Branch Local que Não é Mais Necessária**:

        bash
        git branch -d feature/nova-funcionalidade

# Resumo

Neste hands-on, abordamos a criação e o gerenciamento de branches em um repositório Git no Azure Repos. Aprendemos a criar uma nova branch, fazer commits, enviar a branch para o repositório remoto, criar pull requests e aplicar políticas de branch. Esses passos são essenciais para um fluxo de trabalho organizado e colaborativo, permitindo que múltiplas linhas de desenvolvimento ocorram simultaneamente sem conflitos.