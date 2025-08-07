# Development Setup Role

Esta role configura um ambiente de desenvolvimento completo com diretórios organizados, aliases úteis e scripts de produtividade.

## Funcionalidades

- Cria estrutura de diretórios para desenvolvimento
- Configura aliases úteis para Git, Docker, Kubernetes, etc.
- Define variáveis de ambiente para diferentes linguagens
- Cria scripts de produtividade
- Configura Git com configurações otimizadas
- Organiza projetos por linguagem/tecnologia

## Estrutura de Diretórios Criada

```
~/github/          # Repositórios do GitHub
~/projects/        # Projetos pessoais
~/workspace/       # Projetos ativos de desenvolvimento
├── rust/          # Projetos Rust
├── node/          # Projetos Node.js
├── python/        # Projetos Python
├── go/            # Projetos Go
├── java/          # Projetos Java
├── docker/        # Projetos Docker
└── kubernetes/    # Projetos Kubernetes
~/dev-tools/       # Ferramentas de desenvolvimento
├── bin/           # Binários customizados
├── config/        # Configurações
└── templates/     # Templates de projeto
~/scripts/         # Scripts de produtividade
├── dev/           # Scripts de desenvolvimento
├── utils/         # Utilitários
└── backup/        # Backups de projetos
```

## Variáveis

### Padrões (defaults/main.yml)

- `setup_dev_environment`: Controla se o setup deve ser executado
- `home_dir`: Diretório home do usuário
- `dev_directories`: Lista de diretórios para criar
- `git_config`: Configurações do Git
- `dev_env_vars`: Variáveis de ambiente
- `dev_aliases`: Aliases de desenvolvimento

## Aliases Criados

### Git
- `g` - git
- `gs` - git status
- `ga` - git add
- `gc` - git commit
- `gp` - git push
- `gl` - git log --oneline
- `gd` - git diff

### Navegação
- `dev` - cd ~/workspace
- `gh` - cd ~/github
- `proj` - cd ~/projects
- `tools` - cd ~/dev-tools
- `scripts` - cd ~/scripts

### Docker
- `d` - docker
- `dc` - docker-compose
- `dps` - docker ps
- `dpsa` - docker ps -a

### Kubernetes
- `k` - kubectl
- `kg` - kubectl get
- `kd` - kubectl describe
- `kl` - kubectl logs

### Rust
- `c` - cargo
- `cb` - cargo build
- `cr` - cargo run
- `ct` - cargo test
- `cf` - cargo fmt
- `cc` - cargo check

### Node.js
- `n` - npm
- `nr` - npm run
- `ni` - npm install
- `nid` - npm install --save-dev

### Python
- `p` - python
- `p3` - python3
- `pip` - pip3
- `venv` - python3 -m venv
- `activate` - source venv/bin/activate

## Scripts Criados

### setup-workspace.sh
Configura a estrutura de diretórios do workspace.

### create-project.sh
Cria novos projetos com templates pré-configurados.

**Uso:**
```bash
./scripts/create-project.sh my-project rust
./scripts/create-project.sh my-webapp react
./scripts/create-project.sh my-api node
```

### dev-utils.sh
Utilitários de desenvolvimento.

**Funções principais:**
- `check_dev_env` - Verifica ambiente de desenvolvimento
- `list_projects` - Lista todos os projetos
- `backup_project` - Faz backup de um projeto
- `restore_project` - Restaura um projeto
- `git_status_all` - Status de todos os repositórios
- `docker_clean` - Limpa recursos Docker

## Configurações

### Git
- Editor configurado para VS Code
- Branch padrão: main
- Pull com rebase
- Aliases úteis configurados

### Variáveis de Ambiente
- `EDITOR` - VS Code
- `DEV_HOME` - Diretório home
- `GITHUB_DIR` - Diretório GitHub
- `PROJECTS_DIR` - Diretório de projetos
- `WORKSPACE_DIR` - Diretório de workspace

## Uso

### Incluir no playbook

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - dev-setup
```

### Personalizar configuração

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - role: dev-setup
      vars:
        git_config:
          user_name: "Seu Nome"
          user_email: "seu.email@exemplo.com"
```

## Comandos Úteis

### Navegação
```bash
dev      # Ir para workspace
gh       # Ir para GitHub
proj     # Ir para projetos
tools    # Ir para ferramentas
scripts  # Ir para scripts
```

### Criação de Projetos
```bash
./scripts/create-project.sh meu-projeto rust
./scripts/create-project.sh meu-app react
./scripts/create-project.sh minha-api node
```

### Verificação do Ambiente
```bash
check_dev_env  # Verificar ambiente
list_projects  # Listar projetos
dev_help       # Ver ajuda
```

## Integração com Outras Roles

Esta role trabalha em conjunto com:
- **atuin**: Histórico de comandos
- **rust**: Ambiente Rust
- **starship**: Prompt personalizado
- **oh-my-zsh**: Shell configurado

## Documentação

Para mais informações sobre desenvolvimento, consulte:
- [Git Documentation](https://git-scm.com/doc)
- [Docker Documentation](https://docs.docker.com/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Rust Documentation](https://doc.rust-lang.org/) 