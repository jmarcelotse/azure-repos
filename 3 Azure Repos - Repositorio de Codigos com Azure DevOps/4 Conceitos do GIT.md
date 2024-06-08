# Conceitos do GIT

Git é um sistema de controle de versão distribuído amplamente utilizado que permite a desenvolvedores rastrear mudanças no código-fonte durante o desenvolvimento de software. A seguir, apresento os conceitos fundamentais do Git:

1. #Repositório (Repo)

Um repositório é um local onde o histórico completo do código-fonte é armazenado. Existem dois tipos de repositórios:

 - **Repositório Local**: Armazenado no computador do desenvolvedor.
 - **Repositório Remoto**: Armazenado em um servidor e acessível por vários desenvolvedores.

2. # Clone

O comando **git clone** é usado para criar uma cópia de um repositório remoto em sua máquina local. Isso permite que você trabalhe com uma cópia completa do repositório.

    bash
    git clone <URL_DO_REPOSITORIO>

3. # Commit

Um commit é um instantâneo do seu repositório. Ele salva o estado atual dos arquivos no repositório e cria um ponto de verificação no histórico de versões.

    bash
    git add <ARQUIVO>
    git commit -m "Mensagem do commit"

4. **Branch**

Uma branch é uma linha paralela de desenvolvimento que permite isolar mudanças até que estejam prontas para serem mescladas (merged) com a branch principal. A branch padrão é geralmente chamada de **main** ou **master**.

    bash
    git branch <NOME_DA_BRANCH>
    git checkout <NOME_DA_BRANCH>
    # ou
    git checkout -b <NOME_DA_BRANCH> # Cria e alterna para a nova branch

5. # Merge

Merge é o processo de integrar mudanças de uma branch em outra. Isso é frequentemente usado para trazer novas funcionalidades ou correções de bugs para a branch principal.

    bash
    git checkout <BRANCH_DE_DESTINO>
    git merge <BRANCH_A_SER_MESCLADA>

6. # Pull Request (PR)

Um pull request é uma maneira de solicitar que as mudanças feitas em uma branch sejam revisadas e mescladas em outra branch. Ele é comumente usado em plataformas de hospedagem de repositórios como GitHub, GitLab e Azure DevOps.

7. # Fetch e Pull

    - **Fetch**: Baixa as mudanças do repositório remoto para o repositório local, mas não aplica essas mudanças à sua branch de trabalho.

        bash
        git fetch

    - **Pull**: Combina o fetch e o merge, baixando as mudanças do repositório remoto e aplicando-as à sua branch de trabalho.

8. # Push

O comando **git push** é usado para enviar suas mudanças (commits) do repositório local para o repositório remoto.

        bash
        git push origin <NOME_DA_BRANCH>

9. # Stash

O comando **git stash** salva temporariamente as mudanças não commitadas para que você possa trabalhar em outra coisa, e posteriormente recuperá-las.

        bash
        git stash
        git stash pop # Recupera as mudanças stashed

10. # Tag

Tags são usadas para marcar pontos específicos no histórico do repositório como importantes, geralmente para marcar versões de releases.

        bash
        git tag -a v1.0 -m "Versão 1.0"
        git push origin --tags

11. # Rebase

O **git rebase** re-aplica commits de uma branch sobre outra. Isso pode ser útil para manter um histórico linear.

        bash
        git rebase <BRANCH_BASE>

12. # Configuração Inicial

Antes de começar a usar Git, é importante configurar seu nome de usuário e email, que serão associados aos seus commits.

        bash
        git config --global user.name "Seu Nome"
        git config --global user.email "seuemail@exemplo.com"

13. # Arquivo .gitignore

O arquivo .gitignore especifica quais arquivos ou diretórios devem ser ignorados pelo Git. Isso é útil para evitar que arquivos temporários ou de configuração local sejam adicionados ao repositório.

        bash
        # Exemplo de .gitignore
        *.log
        *.tmp
        node_modules/
        dist/

14. # Comandos Básicos do Git

Aqui estão alguns dos comandos básicos do Git:

 - **git init**: Inicializa um novo repositório Git.
 - **git status**: Exibe o estado atual do repositório.
 - **git diff**: Mostra as mudanças entre o estado do repositório e o último commit.
 - **git log**: Mostra o histórico de commits.
 - **git rm <ARQUIVO>**: Remove um arquivo do repositório e da área de stage.

# Conclusão

Git é uma ferramenta poderosa que facilita o controle de versão e a colaboração em projetos de software. Entender seus conceitos e comandos básicos é essencial para gerenciar eficientemente o desenvolvimento de código e colaborar com outros desenvolvedores.