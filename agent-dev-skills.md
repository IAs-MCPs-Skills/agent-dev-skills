# agent-dev-skills

Skills e workflows que guiam agentes de IA pelo ciclo completo de desenvolvimento de software: brainstorming, planejamento, TDD, debugging, code review, execução paralela e finalização de branch. Suporta Claude Code, Cursor, Codex, OpenCode e Gemini CLI.

> Mirror privado de [obra/superpowers](https://github.com/obra/superpowers)

---

## Como funciona

Assim que o agente detecta que você quer construir algo, ele **não** sai escrevendo código. Ele para, faz perguntas, extrai uma spec da conversa e só avança depois da sua aprovação.

Com a spec aprovada, monta um plano de implementação claro o suficiente para qualquer engenheiro seguir — com TDD estrito, YAGNI e DRY. Depois, executa tarefas via subagentes, revisa o trabalho e segue em frente autonomamente por horas sem sair do plano.

As skills disparam automaticamente. Você não precisa fazer nada especial.

---

## Workflow básico

1. **brainstorming** — Refina ideias via perguntas, explora alternativas, apresenta o design em seções para validação. Salva documento de spec.
2. **using-git-worktrees** — Cria workspace isolado em nova branch, configura o projeto, verifica baseline de testes.
3. **writing-plans** — Quebra o trabalho em tarefas de 2-5 minutos, com caminhos de arquivo exatos, código completo e passos de verificação.
4. **subagent-driven-development** ou **executing-plans** — Despacha subagente por tarefa com revisão em dois estágios (conformidade com spec, depois qualidade de código), ou executa em lotes com checkpoints.
5. **test-driven-development** — Ciclo RED-GREEN-REFACTOR: escreve teste com falha, vê falhar, escreve código mínimo, vê passar, commita. Deleta código escrito antes dos testes.
6. **requesting-code-review** — Revisa contra o plano, reporta issues por severidade. Issues críticos bloqueiam o progresso.
7. **finishing-a-development-branch** — Verifica testes, apresenta opções (merge/PR/manter/descartar), limpa worktree.

---

## Skills disponíveis (14 no total)

### Design & Planejamento
| Skill | O que faz |
|-------|-----------|
| `brainstorming` | Refinamento colaborativo de design via diálogo socrático — explora intenção, propõe abordagens, salva specs antes de implementar. |
| `writing-plans` | Converte designs aprovados em planos de implementação detalhados com tarefas de 2-5 minutos cada. |

### Execução de Desenvolvimento
| Skill | O que faz |
|-------|-----------|
| `subagent-driven-development` | Executa planos usando subagentes frescos por tarefa, com revisão em dois estágios (spec e qualidade de código). |
| `executing-plans` | Alternativa de execução sequencial com checkpoints humanos para plataformas sem suporte a subagentes. |
| `using-git-worktrees` | Cria git worktrees isolados para desenvolvimento paralelo com seleção inteligente de diretório e verificação de segurança. |

### Qualidade & Testes
| Skill | O que faz |
|-------|-----------|
| `test-driven-development` | Ciclo RED-GREEN-REFACTOR estrito — obriga teste falhar primeiro, depois implementação mínima. Inclui referência de anti-patterns de teste. |
| `systematic-debugging` | Investigação de causa raiz em 4 fases antes de qualquer correção. Inclui root-cause-tracing, defense-in-depth e condition-based-waiting. |
| `verification-before-completion` | Exige evidências reais (comandos rodados, output verificado) antes de declarar que algo está funcionando. |

### Code Review
| Skill | O que faz |
|-------|-----------|
| `requesting-code-review` | Despacha subagente revisor com categorização de issues (Critical/Important/Suggestions). Issues críticos bloqueiam o progresso. |
| `receiving-code-review` | Recebe feedback com rigor técnico — obriga verificação e raciocínio antes de implementar sugestões. Evita implementação cega. |

### Operações Paralelas
| Skill | O que faz |
|-------|-----------|
| `dispatching-parallel-agents` | Coordena execução concorrente de tarefas independentes — um agente por domínio, contextos isolados. |

### Conclusão de Trabalho
| Skill | O que faz |
|-------|-----------|
| `finishing-a-development-branch` | Guia finalização: verifica testes, determina branch base, apresenta opções (merge/PR/manter/descartar) e limpa worktree. |

### Meta / Sistema
| Skill | O que faz |
|-------|-----------|
| `writing-skills` | TDD aplicado à documentação de processos — cria novas skills com metodologia de teste via subagentes. |
| `using-superpowers` | Skill de entrada — ensina como descobrir e invocar as outras skills. Carregada automaticamente no início de cada sessão. |

### Agente Especializado
| Agente | O que faz |
|--------|-----------|
| `code-reviewer` | Subagente sênior para revisão de alinhamento ao plano, qualidade de código, arquitetura e padrões. Categoriza issues e orienta correções. |

---

## Instalação

### Claude Code (Marketplace oficial)

```bash
/plugin install superpowers@claude-plugins-official
```

### Claude Code (via Marketplace alternativo)

```bash
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```

### Cursor

No chat do Cursor Agent:

```text
/add-plugin superpowers
```

### Codex

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

### OpenCode

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

### GitHub Copilot CLI

```bash
copilot plugin marketplace add obra/superpowers-marketplace
copilot plugin install superpowers@superpowers-marketplace
```

### Gemini CLI

```bash
gemini extensions install https://github.com/obra/superpowers
```

---

## Sincronização do mirror

Este repositório é um mirror privado do [obra/superpowers](https://github.com/obra/superpowers). Para manter sincronizado com o original, siga os passos abaixo em qualquer máquina.

> **Importante:** O sync sobrescreve o README com o original em inglês. O passo final restaura o README customizado automaticamente. Para isso, mantenha uma cópia local do README em `README-agent-dev-skills.md` na mesma pasta onde está o `superpowers.git`.

### Nova máquina (do zero)

```bash
# 1. Clone o repositório original como mirror
git clone --mirror https://github.com/obra/superpowers.git

# 2. Entre na pasta criada
cd superpowers.git

# 3. Remove a flag de mirror para permitir push seletivo
git config --unset remote.origin.mirror

# 4. Aponte o push para o repositório privado
git remote set-url --push origin https://github.com/IAs-MCPs-Skills/agent-dev-skills.git

# 5. Envie somente a branch main
git push origin refs/heads/main:refs/heads/main

# 6. Restaure o README customizado (volte para a pasta pai)
cd ..
git clone https://github.com/IAs-MCPs-Skills/agent-dev-skills.git _temp_sync
cp README-agent-dev-skills.md _temp_sync/README.md
cd _temp_sync
git add README.md
git commit -m "chore: restore custom README"
git push
cd ..
rm -rf _temp_sync
```

### Máquina que já tem a pasta superpowers.git

```bash
# 1. Sincroniza do original
cd superpowers.git
git fetch origin
git push origin refs/heads/main:refs/heads/main

# 2. Restaura o README customizado (volte para a pasta pai)
cd ..
git clone https://github.com/IAs-MCPs-Skills/agent-dev-skills.git _temp_sync
cp README-agent-dev-skills.md _temp_sync/README.md
cd _temp_sync
git add README.md
git commit -m "chore: restore custom README"
git push
cd ..
rm -rf _temp_sync
```

> A pasta `superpowers.git` pode ser recriada do zero a qualquer momento com o passo 1 acima. Não é necessário guardá-la.
> O arquivo `README-agent-dev-skills.md` deve ser mantido localmente — é ele que protege o README customizado a cada sync.

---

## Filosofia

- **Test-Driven Development** — Testes primeiro, sempre
- **Sistemático sobre ad-hoc** — Processo sobre suposição
- **Redução de complexidade** — Simplicidade como objetivo principal
- **Evidência sobre afirmações** — Verificar antes de declarar sucesso

---

## Licença

MIT License — veja o arquivo LICENSE para detalhes.
