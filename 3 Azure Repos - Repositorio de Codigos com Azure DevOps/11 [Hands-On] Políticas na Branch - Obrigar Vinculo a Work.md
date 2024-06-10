# [Hands-On] Políticas na Branch - Obrigar Vinculo a Work

# Hands-On: Configurando Políticas de Branch para Obrigar Vínculo a Work Items no Azure Repos

Neste guia, vamos configurar políticas de branch no Azure Repos para garantir que todas as mudanças sejam vinculadas a um work item antes de serem integradas na branch principal. Isso ajuda a manter o rastreamento das tarefas e funcionalidades implementadas.

# Pré-requisitos

- Conta no Azure DevOps
- Git instalado em seu sistema
- Repositório Git configurado no Azure Repos

# 1. Acessando o Projeto no Azure DevOps

1. Acesse o Azure DevOps:
    - Vá para o portal Azure DevOps.
    - Faça login com sua conta Microsoft.

2. Selecione o Projeto:
    - Selecione o projeto onde deseja configurar as políticas de branch.

# 2. Navegando para as Configurações de Branch

1. **Acesse Repos**:
    - No menu lateral, clique em "Repos".

2. **Selecione Branches**:
    - No menu superior, clique em "Branches".

3. **Configurar Políticas de Branch**:
        Encontre a branch principal (**main** ou **master**) na lista de branches.
        Clique no ícone de configurações (três pontos verticais) ao lado da branch e selecione "Branch policies".

# 3. Configurando Políticas de Branch

1. **Exigir Vínculo a Work Items**:
    - Na seção de políticas de branch, habilite a opção "Check for linked work items" (Verificar itens de trabalho vinculados). Isso garante que cada PR tenha um work item associado antes de ser mesclado.

2. **Habilitar Requisitos de Pull Request**:
    - Habilite a opção "Require a minimum number of reviewers" (Exigir um número mínimo de revisores).
    - Defina o número de revisores necessários, por exemplo, "1" ou "2".

3. **Exigir Builds Bem-Sucedidos**:
    - Habilite a opção "Require a build to complete before merging" (Exigir a conclusão de um build antes do merge).
    - Selecione o pipeline de build que deve ser executado com sucesso antes de permitir o merge.

4. **Bloquear Pushes Diretos**:
    - Habilite a opção "Block direct pushes" (Bloquear pushes diretos) para impedir que mudanças sejam feitas diretamente na branch principal sem passar por um PR.

5. **Salve as Configurações**:
    - Clique em "Save changes" para aplicar as políticas de branch.

# 4. Criando um Work Item no Azure Boards

1. **Acesse Boards**:
    - No menu lateral, clique em "Boards".

2. **Criar um Novo Work Item**:
    - Clique em "New Work Item" e selecione "Task", "Bug", "User Story" ou o tipo de item que você deseja criar.
    - Preencha os detalhes do work item, como título e descrição.
    - Clique em "Save" para criar o work item.

# 5. Testando as Políticas de Branch

1. **Criar uma Nova Branch**:
    - No terminal, crie uma nova branch para fazer alterações.

    bash

    git checkout -b feature/teste-vinculo-workitem

2. **Fazer Alterações e Commitar**:

    - Adicione ou modifique arquivos no repositório e faça um commit.

    bash

    echo "Testando vínculo a work items" > teste.txt
    git add teste.txt
    git commit -m "Adiciona teste.txt para testar políticas de vínculo a work items"

3. **Enviar a Branch para o Repositório Remoto**:

    - Envie a nova branch para o repositório remoto.

    bash

    git push origin feature/teste-vinculo-workitem

4. **Criar um Pull Request**:

    - No portal do Azure DevOps, vá para "Repos" > "Pull Requests" e clique em "New Pull Request".
    - Selecione **feature/teste-vinculo-workitem** como a branch de origem e **main** como a branch de destino.
    - Adicione uma descrição detalhada do que foi alterado.
    - **Vincular um Work Item**: Na seção "Work items to link", selecione o work item criado anteriormente.
    - Clique em "Create".

5. **Revisar e Aprovar o Pull Request**:

    - Outros membros da equipe devem revisar o PR. Se configurado para exigir revisores, pelo menos o número mínimo de revisores deve aprovar o PR.
    - Se configurado para exigir builds, o pipeline de build deve ser executado e concluído com sucesso antes que o PR possa ser mesclado.

6. **Completar o Pull Request**:

    - Após a aprovação e a conclusão do build, clique em "Complete" para mesclar a branch **feature/teste-vinculo-workitem** na branch **main**.

# Resumo

Neste hands-on, configuramos políticas de branch no Azure Repos para garantir que todas as mudanças na branch principal sejam vinculadas a um work item. Essas políticas ajudam a manter o rastreamento das tarefas e funcionalidades implementadas, além de garantir a qualidade do código através de revisões e builds bem-sucedidos antes do merge. Este fluxo de trabalho é essencial para equipes que desejam manter um alto padrão de qualidade e organização em seus projetos de software.