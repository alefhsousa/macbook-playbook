# Atuin Role

Esta role instala e configura o Atuin, um gerenciador de histórico de comandos moderno e seguro.

## Funcionalidades

- Instala o Atuin via Homebrew
- Cria o diretório de configuração `~/.config/atuin`
- Inicializa o Atuin para zsh
- Adiciona a inicialização do Atuin ao `.zshrc`
- Configura o Atuin com opções otimizadas

## Variáveis

### Padrões (defaults/main.yml)

- `install_atuin`: Controla se o Atuin deve ser instalado (padrão: `yes`)
- `configure_atuin`: Controla se o Atuin deve ser configurado (padrão: `yes`)
- `atuin_config_path`: Caminho do arquivo de configuração (padrão: `~/.config/atuin/config.toml`)
- `add_to_shell_init`: Adiciona inicialização ao shell (padrão: `yes`)

## Uso

### Incluir no playbook

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - atuin
```

### Personalizar configuração

Você pode sobrescrever as variáveis no seu playbook:

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - role: atuin
      vars:
        configure_atuin: yes
        atuin_config_path: "~/.config/atuin/config.toml"
```

## Configurações Principais

### Modos de Busca
- **fuzzy**: Busca fuzzy (padrão)
- **prefix**: Busca por prefixo
- **fulltext**: Busca em texto completo
- **skim**: Busca rápida

### Modos de Filtro
- **global**: Histórico global
- **host**: Apenas comandos do host atual
- **session**: Apenas comandos da sessão atual
- **directory**: Apenas comandos do diretório atual
- **workspace**: Apenas comandos do workspace atual

### Sincronização
- Sincronização automática habilitada
- Servidor de sincronização: `https://api.atuin.sh`
- Frequência de sincronização: 10 minutos

## Comandos Úteis

### Buscar no histórico
```bash
# Busca interativa
atuin search

# Busca com filtro
atuin search --filter-mode session

# Busca por comando específico
atuin search git
```

### Listar histórico
```bash
# Listar comandos recentes
atuin history list

# Listar com formato personalizado
atuin history list --format "{time} - {command}"
```

### Estatísticas
```bash
# Ver estatísticas de comandos
atuin stats
```

## Segurança

O Atuin inclui filtros automáticos para:
- Chaves AWS
- Tokens GitHub
- Tokens Slack
- Chaves Stripe
- E outros dados sensíveis

## Integração com Shell

A role configura automaticamente:
- Inicialização do Atuin no zsh
- Atalhos de teclado (Ctrl+R para busca)
- Integração com zsh-autosuggestions (se instalado)

## Documentação

Para mais informações sobre o Atuin, consulte:
- [Documentação oficial](https://atuin.sh/)
- [GitHub](https://github.com/atuinsh/atuin) 