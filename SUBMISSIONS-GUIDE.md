# Submission Guide

Este documento define o padrão oficial de entrega das atividades do projeto **Computer Architecture Evolution**.

Cada atividade será publicada pelo professor em uma **Issue**. A equipe desenvolve a atividade em sua própria branch e realiza a entrega por meio de um **Pull Request (PR)** vinculado à Issue correspondente.

## Fluxo da entrega

**Issue da atividade → Branch da equipe → Alterações na pasta do grupo → Commit(s) → Push → Pull Request → Validação automática → Revisão do professor**

## 1. Issue da atividade

Antes de iniciar, leia a Issue publicada pelo professor. Ela contém o objetivo, os arquivos/conteúdos esperados e eventuais orientações específicas da entrega.

Anote o número da Issue. Ele será usado na descrição do Pull Request.

## 2. Branch

Nunca trabalhe diretamente na `main`.

Para cada entrega, utilize uma branch no padrão:

```text
team-XX/entrega-NN
```

Onde:

- `XX` = número da equipe com dois dígitos;
- `NN` = número da entrega com dois dígitos.

Exemplos:

```text
team-01/entrega-01
team-01/entrega-02
team-07/entrega-03
```

A equipe deve criar uma nova branch para cada entrega, sempre a partir da versão atualizada da `main`.

Exemplo:

```bash
git checkout main
git pull origin main
git checkout -b team-01/entrega-02
```

## 3. Onde a equipe pode trabalhar

Cada equipe pode modificar **somente a sua própria pasta**:

```text
groups/group-XX/
```

Exemplo: a equipe 03 pode trabalhar somente em:

```text
groups/group-03/
```

Dentro da pasta da própria equipe é permitido:

- editar um ou vários arquivos existentes;
- adicionar novos arquivos e subpastas quando necessários à atividade;
- excluir arquivos que não sejam mais necessários;
- renomear ou reorganizar arquivos;
- atualizar imagens, diagramas, referências e demais materiais do projeto.

Um mesmo Pull Request pode conter **quantos arquivos forem necessários**, desde que todas as alterações estejam dentro da pasta da própria equipe e estejam relacionadas à entrega.

Não modifique arquivos de outra equipe nem arquivos gerais da disciplina fora de `groups/group-XX/`.

## 4. Commits

Faça commits que representem alterações compreensíveis. Evite mensagens genéricas como `update`, `teste`, `alteração`, `final` ou `arquivo novo`.

Padrão recomendado:

```text
entrega-NN: descrição curta da alteração
```

Exemplos:

```text
entrega-02: adiciona análise dos barramentos
entrega-02: inclui diagrama de interconexões
entrega-02: revisa referências e comunicação com memória
```

A equipe pode realizar **mais de um commit** na mesma entrega. Não é necessário colocar tudo em um único commit.

Antes do `push`, confira os arquivos alterados:

```bash
git status
git add .
git commit -m "entrega-02: adiciona análise dos barramentos"
git push -u origin team-01/entrega-02
```

## 5. Pull Request

Ao finalizar a atividade, abra um Pull Request da branch da equipe para:

```text
main
```

Título recomendado:

```text
[ENTREGA NN] Grupo XX — descrição curta
```

Exemplo:

```text
[ENTREGA 02] Grupo 01 — Barramentos e interconexões
```

Na descrição do PR, informe obrigatoriamente:

```markdown
## Entrega
Entrega NN — Nome da atividade

## Grupo
Grupo XX

## O que foi realizado
- resumo das principais alterações;
- arquivos adicionados, modificados ou removidos;
- observações importantes, quando houver.

## Issue relacionada
Related to #NUMERO_DA_ISSUE
```

Também é aceito:

```text
Refs #NUMERO_DA_ISSUE
```

**Não use `Closes #...` ou `Fixes #...`**, salvo quando o professor solicitar, pois a Issue da atividade pode ser utilizada por várias equipes.

## 6. Validação automática

Ao abrir ou atualizar o Pull Request, o GitHub executará uma validação automática.

Ela verifica principalmente se:

- a branch segue `team-XX/entrega-NN`;
- o PR tem alterações;
- todas as alterações estão dentro de `groups/group-XX/` correspondente à equipe;
- o PR está vinculado à Issue da atividade.

A validação **permite múltiplos arquivos** e aceita arquivos **adicionados, modificados, renomeados ou excluídos** dentro da pasta da própria equipe.

Se a validação falhar, abra os detalhes da execução, corrija o problema na mesma branch e faça novo `push`. O mesmo Pull Request será atualizado automaticamente.

## 7. Correções após feedback

Se o professor solicitar ajustes, **não abra outro Pull Request** para a mesma entrega.

Faça as correções na mesma branch, crie novo(s) commit(s) e envie novamente:

```bash
git add .
git commit -m "entrega-02: corrige análise após revisão"
git push
```

O Pull Request será atualizado e a validação será executada novamente.

## Checklist antes de entregar

- [ ] Li a Issue da atividade.
- [ ] Atualizei a `main` antes de criar minha branch.
- [ ] Minha branch segue `team-XX/entrega-NN`.
- [ ] Alterei somente `groups/group-XX/` da minha equipe.
- [ ] Revisei todos os arquivos adicionados, modificados, renomeados ou excluídos.
- [ ] Usei mensagens de commit claras.
- [ ] Fiz `push` de todos os commits.
- [ ] Abri o PR para `main`.
- [ ] Usei o título `[ENTREGA NN] Grupo XX — descrição curta`.
- [ ] Incluí `Related to #NUMERO` ou `Refs #NUMERO` na descrição do PR.
- [ ] A validação automática passou.

A entrega estará pronta para avaliação quando o Pull Request estiver aberto, vinculado à Issue correta e com a validação automática concluída com sucesso.
