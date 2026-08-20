# Alias

Você pode criar um alias para facilitar commits semânticos no Git. Por exemplo:

```bash
git config --global alias.c 'commit'
git config --global alias.ca 'commit --amend'
```

Mas, se a ideia é ter atalhos para os tipos de **Conventional Commits**, como `feat`, `fix`, `docs`, etc., você pode usar:

```bash
git config --global alias.feat '!f() { git commit -m "feat: $*"; }; f'
git config --global alias.fix '!f() { git commit -m "fix: $*"; }; f'
git config --global alias.docs '!f() { git commit -m "docs: $*"; }; f'
git config --global alias.refactor '!f() { git commit -m "refactor: $*"; }; f'
git config --global alias.test '!f() { git commit -m "test: $*"; }; f'
git config --global alias.chore '!f() { git commit -m "chore: $*"; }; f'
```

Aí você pode fazer:

```bash
git feat "adiciona autenticação"
git fix "corrige validação do token"
git docs "atualiza README"
git refactor "simplifica serviço de usuários"
git test "adiciona testes para autenticação"
git chore "atualiza dependências"
```

O resultado será, por exemplo:

```text
feat: adiciona autenticação
fix: corrige validação do token
```

**Uma alternativa mais prática** é criar um único alias interativo:

```bash
git config --global alias.cc '!f() { git commit -m "$1: ${*:2}"; }; f'
```

Uso:

```bash
git cc feat "adiciona autenticação"
git cc fix "corrige login"
```

Se quiser, também posso montar um alias que **mostra um menu (`feat`, `fix`, `docs`, `refactor`...) e pergunta a mensagem do commit**.
