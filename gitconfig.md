# Menu

Uma forma bem prática é criar um alias `git cm` que abre um menu, você escolhe o tipo e depois digita a mensagem.

Adicione ao `~/.gitconfig`:

```ini
[alias]
    cm = "!f() { \
        echo 'Escolha o tipo do commit:'; \
        echo '1) feat - nova funcionalidade'; \
        echo '2) fix - correção de bug'; \
        echo '3) docs - documentação'; \
        echo '4) refactor - refatoração de código'; \
        echo '5) test - testes'; \
        echo '6) chore - tarefas de manutenção'; \
        echo '7) perf - melhoria de performance'; \
        echo '8) ci - integração contínua'; \
        echo '9) build - build e dependências'; \
        echo '10) revert - reverte um commit'; \
        printf 'Opção: '; \
        read option; \
        case $option in \
            
            1) type=feat ;; \
            2) type=fix ;; \
            3) type=docs ;; \
            4) type=refactor ;; \
            5) type=test ;; \
            6) type=chore ;; \
            7) type=perf ;; \
            8) type=ci ;; \
            9) type=build ;; \
            10) type=revert ;; \
            *) echo 'Opção inválida.'; return 1 ;; \
        esac; \
        printf 'Mensagem: '; \
        read message; \
        if [ -z \"$message\" ]; then \
            echo 'A mensagem não pode ser vazia.'; \
            return 1; \
        fi; \
        git commit -m \"$type: $message\"; \
    ; f"
```

Depois é só executar:

```bash
git cm
```

Você verá:

```text
Escolha o tipo do commit:
1) feat - nova funcionalidade
2) fix - correção de bug
3) docs - documentação
4) refactor - refatoração de código
5) test - testes
6) chore - tarefas de manutenção
7) perf - melhoria de performance
8) ci - integração contínua
9) build - build e dependências
10) revert - reverte um commit
Opção:
```

Se escolher `1`:

```text
Opção: 1
Mensagem: adiciona autenticação com JWT
```

E o Git criará:

```text
feat: adiciona autenticação com JWT
```

### Versão ainda melhor

Eu recomendo colocar o script em `~/.git-commit.sh` em vez de manter esse código enorme dentro do `.gitconfig`. Fica muito mais fácil adicionar tipos, emojis, `scope`, validações etc.

Por exemplo, poderíamos chegar a algo como:

```text
$ git cm

╭────────────────────────────╮
│     Conventional Commit    │
├────────────────────────────┤
│ 1  feat      ✨             │
│ 2  fix       🐛             │
│ 3  docs      📝             │
│ 4  refactor  ♻️             │
│ 5  test      🧪             │
│ 6  chore     🔧             │
│ 7  perf      ⚡             │
│ 8  ci        👷             │
╰────────────────────────────╯

Tipo: 1
Scope (opcional): auth
Mensagem: adiciona login com Google

Commit:
feat(auth): adiciona login com Google

Confirmar? [Y/n]
```

Essa versão fica bem mais agradável para uso diário.
