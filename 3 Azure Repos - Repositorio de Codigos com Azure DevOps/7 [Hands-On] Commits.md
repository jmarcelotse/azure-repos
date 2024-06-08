# Hands-On: Trabalhando com Commits no Git

Este guia prático detalha como criar, visualizar e gerenciar commits em um repositório Git no Azure Repos. Commits são fundamentais para registrar o progresso e o histórico de mudanças no código-fonte.

# Pré-requisitos

 - Conta no Azure DevOps
 - Git instalado em seu sistema
 - Repositório Git configurado no Azure Repos

 1. # Clonando o Repositório

Se ainda não tiver o repositório clonado em sua máquina local, siga os passos abaixo:

    1. **Obter a URL do Repositório**:
        - Na página de Repos no Azure DevOps, clique em "Clone" e copie a URL do repositório Git.

 2. **Clonar o Repositório**:

    bash
    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

2. # Fazendo Alterações e Commitando

    1. **Adicionar ou Modificar Arquivos**:
        - Por exemplo, crie ou edite um arquivo main.py:

            python
            # main.py
            print("Hello, Azure Repos!")

    2. **Adicionar as Alterações ao Stage**:

        - Use o comando git add para adicionar os arquivos modificados ao stage.

            bash
            git add main.py

    3. **Commitar as Alterações**:

        - Use o comando git commit para registrar as mudanças no repositório.

            bash
            git commit -m "Adiciona arquivo main.py com uma mensagem de saudação"

3. # Fazendo Alterações em Vários Arquivos

    1. **Modificar Vários Arquivos**:

        - Crie ou edite mais arquivos, por exemplo, **utils.py**:

            python
            # utils.py
            def saudacao():
                return "Hello from utils!"

        - E também modifique main.py:

            python
            # main.py
            from utils import saudacao

            if __name__ == "__main__":
                print("Hello, Azure Repos!")
                print(saudacao())

    2. **Adicionar Todos os Arquivos Modificados ao Stage**:

        bash
        git add .

    3. **Commitar as Alterações**:

        bash
        git commit -m "Adiciona utils.py e integra com main.py"

4. # Visualizando o Histórico de Commits

    1. Ver o Histórico de Commits:
        - Use o comando **git log** para visualizar o histórico de commits.

            bash
            git log

    2. **Histórico Compacto**:
        - Use o comando **git log --oneline** para um histórico mais compacto.

            bash
            git log --oneline

5. # Editando Commits Recentes

    1. **Modificando o Último Commit**:
        - Se você precisar modificar o último commit (por exemplo, para corrigir uma mensagem de commit), use **git commit --amend**.

            bash
            git commit --amend -m "Mensagem de commit corrigida"

6. # Revertendo Commits

    1. **Reverter um Commit Específico**:
        - Use o comando git revert seguido pelo hash do commit que deseja reverter.

            bash
            git revert <HASH_DO_COMMIT>

    2. **Reverter para um Estado Anterior**:

        - Use o comando **git reset** para desfazer commits, movendo o ponteiro HEAD e, opcionalmente, mantendo as mudanças no stage.

            bash
            git reset --soft <HASH_DO_COMMIT> # Mantém as mudanças no stage
            git reset --hard <HASH_DO_COMMIT> # Desfaz as mudanças completamente

7. # Enviando Commits para o Repositório Remoto

    1. **Push dos Commits para o Repositório Remoto**:
        - Use o comando **git push** para enviar seus commits para o repositório remoto.

            bash
            git push origin <NOME_DA_BRANCH>

8. # Trabalhando com Pull Requests

    1. **Criar um Pull Request no Azure DevOps**:
        - No portal do Azure DevOps, vá para "Repos" > "Pull Requests" e clique em "New Pull Request".
        - Selecione a branch de origem e a branch de destino.
        - Adicione uma descrição e clique em "Create".

    2. **Revisar e Completar o Pull Request**:
        - Outros desenvolvedores podem revisar o código, adicionar comentários e sugerir alterações.
        - Após a revisão e aprovação, clique em "Complete" para fazer o merge das mudanças.

9. # Configurando um .gitignore

    1. **Criar um Arquivo .gitignore**:
        - O arquivo **.gitignore** especifica quais arquivos ou diretórios devem ser ignorados pelo Git. Crie um arquivo **.gitignore** na raiz do seu repositório com o seguinte conteúdo:

            bash
            # Ignora arquivos de log
            *.log

            # Ignora diretórios de build
            /build/
            /dist/

            # Ignora dependências do Node.js
            /node_modules/

    2. **Adicionar o .gitignore ao Stage e Commitar**:

            bash
            git add .gitignore
            git commit -m "Adiciona arquivo .gitignore"

# Resumo

Neste hands-on, cobrimos as operações básicas e essenciais de commits no Git, incluindo a criação e modificação de commits, visualização do histórico, reversão de commits e envio das mudanças para um repositório remoto. Também configuramos um arquivo .gitignore para gerenciar quais arquivos devem ser ignorados pelo Git. Esses passos são fundamentais para gerenciar eficientemente o desenvolvimento de código e colaborar com outros desenvolvedores em um ambiente de controle de versão.