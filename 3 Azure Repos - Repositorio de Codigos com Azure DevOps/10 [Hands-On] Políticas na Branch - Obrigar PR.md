# [Hands-On] Políticas na Branch - Obrigar PR

# Hands-On: Aplicando Políticas de Branch no Azure Repos para Obrigar Pull Requests

Este guia prático irá orientá-lo na configuração de políticas de branch no Azure Repos para garantir que todas as mudanças passem por um Pull Request (PR) antes de serem integradas na branch principal.

# Pré-requisitos

- Conta no Azure DevOps
- Git instalado em seu sistema
- Repositório Git configurado no Azure Repos

# 1. Acessando o Projeto no Azure DevOps

1. Acesse o Azure DevOps:
    - Vá para o portal Azure DevOps.
    - Faça login com sua conta Microsoft.

2. **Selecione o Projeto**:
    - Selecione o projeto onde deseja configurar as políticas de branch.

# 2. Navegando para as Configurações de Branch

1. **Acesse Repos**:
    - No menu lateral, clique em "Repos".

2. **Selecione Branches**:
    - No menu superior, clique em "Branches".

3. **Configurar Políticas de Branch**:

    - Encontre a branch principal (main ou master) na lista de branches.
    - Clique no ícone de configurações (três pontos verticais) ao lado da branch e selecione "Branch policies".

# 3. Configurando Políticas de Branch

1. Habilitar Requisitos de Pull Request:
    - Na seção de políticas de branch, habilite a opção "Require a minimum number of reviewers" (Exigir um número mínimo de revisores).
    - Defina o número de revisores necessários, por exemplo, "2".
    - Habilite a opção "Check for linked work items" (Verificar itens de trabalho vinculados) para garantir que as mudanças estejam vinculadas a work items no Azure Boards.
    - Habilite a opção "Check for comment resolution" (Verificar resolução de comentários) para garantir que todos os comentários nos PRs sejam resolvidos antes do merge.

2. **Exigir Builds Bem-Sucedidos**:
    - Habilite a opção "Require a build to complete before merging" (Exigir a conclusão de um build antes do merge).
    - Selecione o pipeline de build que deve ser executado com sucesso antes de permitir o merge.

3. **Bloquear Pushes Diretos**:
    - Habilite a opção "Block direct pushes" (Bloquear pushes diretos) para impedir que mudanças sejam feitas diretamente na branch principal sem passar por um PR.

4. **Salve as Configurações**:
    - Clique em "Save changes" para aplicar as políticas de branch.

# 4. Testando as Políticas de Branch

1. Criar uma Nova Branch:
    - No terminal, crie uma nova branch para fazer alterações.

    bash

    git checkout -b feature/teste-politicas

2. **Fazer Alterações e Commitar**:

    Adicione ou modifique arquivos no repositório e faça um commit.

    bash

    echo "Testando políticas de branch" > teste.txt
    git add teste.txt
    git commit -m "Adiciona teste.txt para testar políticas de branch"

3. **Enviar a Branch para o Repositório Remoto**:

    - Envie a nova branch para o repositório remoto.

    bash

    git push origin feature/teste-politica

4. **Criar um Pull Request**:

    - No portal do Azure DevOps, vá para "Repos" > "Pull Requests" e clique em "New Pull Request".
    - Selecione **feature/teste-politicas** como a branch de origem e **main** como a branch de destino.
    - Adicione uma descrição detalhada do que foi alterado e clique em "Create".

5. **Revisar e Aprovar o Pull Request**:

    - Outros membros da equipe devem revisar o PR. Se configurado para exigir revisores, pelo menos o número mínimo de revisores deve aprovar o PR.
    - Se configurado para exigir builds, o pipeline de build deve ser executado e concluído com sucesso antes que o PR possa ser mesclado.

6. **Completar o Pull Request**:

    Após a aprovação e a conclusão do build, clique em "Complete" para mesclar a branch feature/teste-politicas na branch main.

# Resumo

Neste hands-on, configuramos políticas de branch no Azure Repos para garantir que todas as mudanças na branch principal passem por um Pull Request. Essas políticas ajudam a manter a qualidade do código, garantindo revisões de código, builds bem-sucedidos e resolução de comentários antes do merge. Este fluxo de trabalho é essencial para equipes que desejam manter um alto padrão de qualidade e colaboração em seus projetos de software.