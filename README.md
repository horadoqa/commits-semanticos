# **Commits semânticos** 

São uma forma padronizada de escrever mensagens de commit para deixar claro **o que mudou e por quê**.

O padrão mais usado é o **Conventional Commits**:

```text
tipo: descrição
```

Por exemplo:

```text
feat: adiciona login com Google
fix: corrige validação do formulário
docs: atualiza documentação da API
refactor: simplifica serviço de autenticação
test: adiciona testes para usuários
```

### Os principais tipos

| Tipo       | Significado                         | Exemplo                            |
| ---------- | ----------------------------------- | ---------------------------------- |
| `feat`     | Nova funcionalidade                 | `feat: adiciona login`             |
| `fix`      | Correção de bug                     | `fix: corrige erro no cadastro`    |
| `docs`     | Documentação                        | `docs: atualiza README`            |
| `refactor` | Refatoração sem mudar comportamento | `refactor: reorganiza serviços`    |
| `test`     | Criação/alteração de testes         | `test: adiciona testes de login`   |
| `chore`    | Manutenção                          | `chore: atualiza dependências`     |
| `perf`     | Melhoria de performance             | `perf: otimiza consulta ao banco`  |
| `ci`       | CI/CD                               | `ci: adiciona pipeline de testes`  |
| `build`    | Build/dependências                  | `build: atualiza versão do Node`   |
| `revert`   | Reversão de alteração               | `revert: remove nova autenticação` |

### Por que usar?

O principal benefício é que o histórico do Git fica **organizado e fácil de entender**.

Em vez de:

```text
ajustes
mudanças
correção
coisas novas
final
arrumei
```

Você tem:

```text
feat: adiciona recuperação de senha
fix: corrige expiração do token
refactor: separa serviço de autenticação
test: adiciona testes de recuperação de senha
docs: documenta endpoint de autenticação
```

Isso também permite **automatizar coisas**. Por exemplo, ferramentas podem analisar os commits e gerar automaticamente um `CHANGELOG`, determinar versões e até identificar alterações que quebram compatibilidade.

### Também existem `BREAKING CHANGE`

Quando uma alteração quebra a compatibilidade com a versão anterior, você pode indicar isso:

```text
feat!: altera formato da resposta da API
```

O `!` significa que existe uma **breaking change**.

Por exemplo:

```text
feat!: remove suporte ao endpoint /users/old
```

Ou usando o corpo do commit:

```text
feat: altera autenticação

BREAKING CHANGE: o token agora deve ser enviado no header Authorization.
```
