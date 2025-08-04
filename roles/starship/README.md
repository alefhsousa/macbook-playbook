# Starship Role

Esta role instala e configura o Starship, um prompt shell moderno e rápido escrito em Rust.

## Funcionalidades

- Instala o Starship via Homebrew
- Cria o diretório de configuração `~/.config`
- Configura o Starship com um tema moderno e funcional
- Adiciona a inicialização do Starship ao `.zshrc` e `.bash_profile`
- Inclui módulos para Git, Node.js, Python, Rust, bateria, tempo e mais

## Variáveis

### Padrões (defaults/main.yml)

- `install_starship`: Controla se o Starship deve ser instalado (padrão: `yes`)
- `configure_starship`: Controla se o Starship deve ser configurado (padrão: `yes`)
- `starship_config_path`: Caminho do arquivo de configuração (padrão: `~/.config/starship.toml`)
- `add_to_shell_init`: Adiciona inicialização ao shell (padrão: `yes`)

## Uso

### Incluir no playbook

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - starship
```

### Personalizar configuração

Você pode sobrescrever as variáveis no seu playbook:

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - role: starship
      vars:
        configure_starship: yes
        starship_config_path: "~/.config/starship.toml"
```

## Módulos Incluídos

- **character**: Símbolos de sucesso/erro
- **directory**: Navegação de diretórios
- **git_branch**: Branch atual do Git
- **git_status**: Status do repositório Git
- **git_state**: Estado do repositório (merge, rebase, etc.)
- **nodejs**: Versão do Node.js
- **python**: Versão do Python
- **rust**: Versão do Rust
- **helm**: Versão do Helm
- **time**: Hora atual
- **cmd_duration**: Duração de comandos longos
- **battery**: Status da bateria
- **hostname**: Nome do host
- **username**: Nome do usuário
- **jobs**: Jobs em background

## Personalização

Para personalizar a configuração do Starship, edite o template `templates/starship.toml.j2` ou sobrescreva as variáveis conforme necessário.

## Documentação

Para mais informações sobre o Starship, visite: https://starship.rs/ 