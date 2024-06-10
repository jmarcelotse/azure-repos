#  Comandos GIT

# Comandos Git para Trabalhar com Azure Repos

Quando você trabalha com Azure Repos, a maioria dos comandos Git que você usa são os mesmos que em qualquer outro repositório Git. No entanto, existem algumas operações específicas e práticas recomendadas para integração com Azure DevOps. A seguir, estão listados os comandos Git mais comuns usados em Azure Repos, juntamente com suas descrições e exemplos.

# Configuração Inicial

1. **Configurar Nome de Usuário e Email**:

    bash

    git config --global user.name "Seu Nome"
    git config --global user.email "seuemail@exemplo.com"

# Clonando o Repositório

1. **Clonar um Repositório**:
    - Para clonar um repositório existente do Azure Repos:

    bash

    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

# Criando e Gerenciando Branches

3. **Criar e Alternar para uma Nova Branch**:

    bash

    git checkout -b feature/nova-funcionalidade

4. **Listar Branches**:

    bash

    git branch

5. **Alternar para uma Branch Existente**:

    bash

    git checkout main

6. **Deletar uma Branch**:

    bash

    git branch -d feature/nova-funcionalidade

# Fazendo Alterações e Commitando

7. Adicionar Arquivos ao Stage:
    - Adicionar um arquivo específico:

    bash

    git add <ARQUIVO>

 - Adicionar todos os arquivos modificados:

    bash

    git add .

8. **Commitar Alterações**:

    bash

    git commit -m "Mensagem do commit explicando as alterações"

# Enviando e Atualizando o Repositório Remoto

9. **Enviar Commits para o Repositório Remoto**:

    bash

    git push origin feature/nova-funcionalidade

10. **Atualizar a Branch Local com Mudanças do Repositório Remoto**:

    bash

    git pull origin main

# Trabalhando com Pull Requests

11. Criar um Pull Request:
    - Pull requests são geralmente criados através do portal do Azure DevOps. No entanto, você pode abrir um pull request usando a interface da web após enviar suas mudanças para o repositório remoto.

# Revisão de Código e Merge

12. Revisar Pull Requests:
    - No portal do Azure DevOps, vá para "Repos" > "Pull Requests" e selecione o pull request que deseja revisar.
    - Adicione comentários, aprove ou solicite mudanças.

13. Mesclar um Pull Request:
    - Após a revisão e aprovação, clique em "Complete" no pull request para mesclar as mudanças na branch principal.

# Revertendo Alterações

14. **Reverter um Commit**:

    bash

    git revert <HASH_DO_COMMIT>

15. **Resetar para um Commit Anterior**:

    - Reset suave (mantém as mudanças no stage):

    bash

    git reset --soft <HASH_DO_COMMIT>

    - Reset duro (descarta todas as mudanças):

    bash

    git reset --hard <HASH_DO_COMMIT>

# Trabalhando com Tags

16. **Criar uma Tag**:

    bash

    git tag -a v1.0 -m "Versão 1.0"

17. **Enviar Tags para o Repositório Remoto**:

    bash

    git push origin --tags

# .gitignore

18. Usar o Arquivo .gitignore:
    - Adicione um arquivo **.gitignore** na raiz do repositório para especificar quais arquivos ou diretórios o Git deve ignorar.

    bash

    #Exemplo de .gitignore
    *.log
    /build/
    /dist/
    /node_modules/

# Exemplo Completo de Workflow

1. **Configurar Nome e Email**:

    bash

    git config --global user.name "Seu Nome"
    git config --global user.email "seuemail@exemplo.com"

2. **Clonar o Repositório**:

    bash

    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

3. **Criar uma Nova Branch**:

    bash

    git checkout -b feature/nova-funcionalidade

4. **Fazer Alterações, Adicionar e Commitar**:

    bash

    echo "Nova funcionalidade" > funcionalidade.txt
    git add funcionalidade.txt
    git commit -m "Adiciona nova funcionalidade"

5. **Enviar para o Repositório Remoto**:

    bash

    git push origin feature/nova-funcionalidade

6. **Criar um Pull Request no Azure DevOps**:

    - No portal do Azure DevOps, vá para "Repos" > "Pull Requests" e clique em "New Pull Request".
    - Selecione a branch feature/nova-funcionalidade como origem e main como destino.
    - Adicione uma descrição e clique em "Create".

7. **Revisar, Aprovar e Mesclar o Pull Request**:

    - Outros membros da equipe revisam o pull request.
    - Após a revisão e aprovação, clique em "Complete" para mesclar as mudanças.

8. **Atualizar a Branch Local**:

    bash

    git checkout main
    git pull origin main

9. **Deletar a Branch Local**:

    bash

    git branch -d feature/nova-funcionalidade

# Resumo

Esses comandos Git, quando combinados com as práticas de Pull Requests e Code Reviews no Azure Repos, fornecem um fluxo de trabalho poderoso e eficiente para o desenvolvimento de software colaborativo. Azure Repos se integra perfeitamente com o Git, permitindo que você use os comandos Git que já conhece, enquanto aproveita as funcionalidades adicionais oferecidas pelo Azure DevOps.