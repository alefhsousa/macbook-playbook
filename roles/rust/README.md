# Rust Role

Esta role instala e configura o Rust e rustup com ferramentas essenciais para desenvolvimento.

## Funcionalidades

- Instala o rustup (gerenciador oficial do Rust)
- Configura o toolchain stable como padrão
- Instala toolchains adicionais (nightly)
- Adiciona componentes essenciais (rust-src, rust-analysis, etc.)
- Instala ferramentas populares do ecossistema Rust
- Configura o Cargo com otimizações
- Adiciona o Cargo ao PATH

## Variáveis

### Padrões (defaults/main.yml)

- `install_rust`: Controla se o Rust deve ser instalado (padrão: `yes`)
- `configure_rust`: Controla se o Rust deve ser configurado (padrão: `yes`)
- `rust_toolchains`: Lista de toolchains para instalar (padrão: `[stable, nightly]`)
- `rust_components`: Componentes do Rust para instalar
- `rust_tools`: Ferramentas Cargo para instalar

## Toolchains Instalados

- **stable**: Versão estável do Rust (padrão)
- **nightly**: Versão nightly para recursos experimentais

## Componentes Instalados

- **rust-src**: Código fonte do Rust (necessário para rust-analyzer)
- **rust-analysis**: Dados de análise para IDEs
- **rust-std**: Biblioteca padrão
- **rustc-dev**: Compilador de desenvolvimento

## Ferramentas Instaladas

### Desenvolvimento
- `cargo-edit`: Editar dependências diretamente
- `cargo-watch`: Executar comandos quando arquivos mudam
- `cargo-expand`: Expandir macros
- `cargo-generate`: Gerar projetos de templates

### Testes e Qualidade
- `cargo-audit`: Auditoria de segurança
- `cargo-tarpaulin`: Cobertura de código
- `cargo-nextest`: Runner de testes alternativo
- `cargo-llvm-cov`: Cobertura com LLVM

### Análise e Debugging
- `cargo-bloat`: Analisar tamanho do binário
- `cargo-geiger`: Detectar uso de unsafe
- `cargo-tree`: Visualizar árvore de dependências
- `cargo-asm`: Ver assembly gerado

### Utilitários
- `cargo-update`: Atualizar dependências
- `cargo-outdated`: Verificar dependências desatualizadas
- `cargo-license`: Listar licenças
- `cargo-release`: Automatizar releases

### WebAssembly
- `wasm-pack`: Empacotar para WebAssembly
- `trunk`: Build tool para aplicações web

### Cross-compilation
- `cross`: Compilar para outras plataformas

## Uso

### Incluir no playbook

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - rust
```

### Personalizar configuração

```yaml
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - role: rust
      vars:
        rust_toolchains:
          - stable
          - nightly
          - beta
        rust_tools:
          - cargo-edit
          - cargo-watch
```

## Comandos Úteis

### Gerenciar toolchains
```bash
# Listar toolchains
rustup toolchain list

# Mudar toolchain padrão
rustup default nightly

# Usar toolchain específico
rustup run nightly cargo build
```

### Gerenciar componentes
```bash
# Listar componentes
rustup component list

# Adicionar componente
rustup component add rust-src
```

### Atualizar Rust
```bash
# Atualizar toolchains
rustup update

# Verificar versões
rustup show
```

### Ferramentas Cargo
```bash
# Adicionar dependência
cargo add serde

# Remover dependência
cargo remove serde

# Ver dependências desatualizadas
cargo outdated

# Auditoria de segurança
cargo audit
```

## Configuração do Cargo

A role configura automaticamente:

### Otimizações
- Compilação paralela baseada no número de cores
- Otimizações específicas para Apple Silicon
- Configurações de debug e release otimizadas

### Perfis
- **dev**: Otimizado para desenvolvimento
- **release**: Otimizado para produção
- **test**: Otimizado para testes
- **bench**: Otimizado para benchmarks

### Linker
- Configuração para usar LLD (linker mais rápido)
- Suporte para Apple Silicon (aarch64)

## Integração com IDEs

### VS Code
- Instale a extensão "rust-analyzer"
- O componente `rust-src` é necessário

### IntelliJ IDEA
- Instale o plugin "Rust"
- Configure o caminho do rustup

## Performance

### Compilação
- Usa LLD como linker (mais rápido que o padrão)
- Compilação paralela habilitada
- Incremental compilation habilitada

### Debugging
- Debug info otimizado para desenvolvimento
- Assertions habilitadas em modo debug

## Documentação

Para mais informações sobre o Rust, consulte:
- [Documentação oficial](https://doc.rust-lang.org/)
- [Rust Book](https://doc.rust-lang.org/book/)
- [Cargo Book](https://doc.rust-lang.org/cargo/)
- [Rustup Book](https://rust-lang.github.io/rustup/) 