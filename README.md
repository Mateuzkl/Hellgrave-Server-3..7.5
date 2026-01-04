# Hellgrave Exodus Server v3.7.5

Servidor MMORPG baseado em The Forgotten Server, customizado para Hellgrave Exodus.

---

## 📋 Requisitos

- **Windows 10/11** (64-bit)
- **Visual Studio 2022 ou 2026** (Community, Professional ou Enterprise)
  - Instale com "Desenvolvimento para Desktop com C++"
  - ✅ Testado e funcionando em ambas as versões
- **vcpkg** (gerenciador de pacotes C++)

---

## 🚀 Instalação Rápida

### 1. Baixar e Configurar vcpkg

O vcpkg já vem pré-configurado com todas as dependências necessárias para compilar o servidor.

**Download do vcpkg pré-configurado:**
- 📦 [Baixar vcpkg.rar](https://www.mediafire.com/file/ipd4qzohe9jwji3/vcpkg.rar/file)

**Instalação:**

1. Extraia o arquivo `vcpkg.rar` para `C:\vcpkg\`
   - O caminho final deve ser: `C:\vcpkg\vcpkg.exe`

2. O vcpkg já está configurado e pronto para uso!
   - Todas as dependências (Boost, MySQL, Crypto++, Lua, etc.) serão baixadas automaticamente durante a compilação

> ⚠️ **Importante:** Mantenha o vcpkg em `C:\vcpkg\` pois o projeto está configurado para este caminho.

---

### 2. Compilar o Servidor

1. Abra o arquivo `vc17/Hellgrave_Exodus.sln` no Visual Studio (2022 ou 2026)

2. Selecione a configuração:
   - **Release x64** (recomendado para produção)
   - **Debug x64** (para desenvolvimento)

3. Clique em **Build > Build Solution** (ou pressione `Ctrl+Shift+B`)

4. Na primeira compilação, o vcpkg irá:
   - Detectar as dependências do `vcpkg.json`
   - Baixar e compilar automaticamente todas as bibliotecas necessárias
   - Isso pode levar de 10 a 30 minutos dependendo do seu PC

5. O executável será gerado em:
   - Release: `vc17/x64/Release/Hellgrave_Exodus-x64.exe`
   - Debug: `vc17/x64/Debug/Hellgrave_Exodus-x64.exe`

> ✅ **Compatibilidade:** Funciona perfeitamente no Visual Studio 2022 e 2026!

---

## 🎮 Cliente e Map Editor

### Download Completo (Cliente + Servidor + Map Editor)

📦 **[Baixar Hellgrave Client, Server & Map Editor v3.7.5](https://www.mediafire.com/file/ygzgbbv74y068a4/hellgraveClient_Server_MapEditor_v3.7.5.zip/file)**

Este pacote inclui:
- ✅ **Cliente Hellgrave** - Para jogar
- ✅ **Servidor Compilado** - Pronto para usar
- ✅ **RME (Remere's Map Editor)** - Para editar mapas

### Configuração do Cliente

1. Extraia o arquivo baixado
2. Execute o cliente Hellgrave
3. Configure o IP do servidor (padrão: localhost ou 127.0.0.1)
4. Crie uma conta e divirta-se!

### Usando o Map Editor (RME)

1. Abra o Remere's Map Editor incluído no pacote
2. Carregue o mapa da pasta `data/world/`
3. Edite o mapa conforme necessário
4. Salve e reinicie o servidor para aplicar as mudanças

---

## 📁 Estrutura do Projeto

```
Hellgrave-Server/
├── data/                    # Scripts Lua, configurações, dados do jogo
│   ├── actions/            # Scripts de ações (alavancas, baús, etc)
│   ├── creaturescripts/    # Scripts de criaturas
│   ├── globalevents/       # Eventos globais
│   ├── items/              # Definições de itens
│   ├── monster/            # Definições de monstros
│   ├── movements/          # Scripts de movimento (tiles, teleports)
│   ├── npc/                # NPCs e diálogos
│   ├── spells/             # Magias
│   ├── talkactions/        # Comandos de chat
│   ├── weapons/            # Armas e munições
│   └── world/              # Arquivos do mapa
├── src/                     # Código-fonte C++
├── vc17/                    # Projeto Visual Studio 2022
├── vcpkg.json              # Dependências do vcpkg
└── README.md               # Este arquivo
```

---

## ⚙️ Configuração do Servidor

### Arquivo de Configuração

Edite `config.lua` para configurar:
- Porta do servidor
- Conexão com banco de dados MySQL
- Rates de experiência, loot, spawn
- Configurações de PvP
- E muito mais...

### Banco de Dados

1. Instale o **MySQL Server** ou **MariaDB**
2. Importe o schema do banco de dados:
   ```sql
   mysql -u root -p < schema.sql
   ```
3. Configure as credenciais em `config.lua`:
   ```lua
   mysqlHost = "127.0.0.1"
   mysqlUser = "root"
   mysqlPass = "sua_senha"
   mysqlDatabase = "hellgrave"
   ```

---

## 🔧 Dependências (Gerenciadas pelo vcpkg)

O projeto utiliza as seguintes bibliotecas, todas instaladas automaticamente:

- **Boost** (ASIO, Beast, Filesystem, IOStreams, Locale, Lockfree, System, Variant, JSON)
- **Crypto++** - Criptografia RSA
- **fmt** - Formatação de strings moderna
- **libmariadb** - Conector MySQL/MariaDB
- **Lua 5.4** - Engine de scripts
- **OpenSSL** - Segurança e criptografia
- **pugixml** - Parser XML
- **zlib** - Compressão

---

## 🐛 Solução de Problemas

### Erro: "vcpkg não encontrado"
- Verifique se o vcpkg está em `C:\vcpkg\`
- Certifique-se de que `C:\vcpkg\vcpkg.exe` existe

### Erro: "Não é possível abrir arquivo incluir"
- Limpe a solução: **Build > Clean Solution**
- Recompile: **Build > Rebuild Solution**
- O vcpkg irá reinstalar as dependências

### Servidor não inicia
- Verifique se o MySQL está rodando
- Confirme as credenciais em `config.lua`
- Verifique os logs em `data/logs/`

### Porta já em uso
- Altere a porta em `config.lua` (padrão: 7172)
- Ou feche o processo que está usando a porta

---

## 📝 Scripts Customizados

O servidor inclui scripts customizados na pasta `CUSTOM_SCRIPTS/`:
- **Cooldown Potions** - Sistema de cooldown para poções
- Leia `CUSTOM_SCRIPTS/READ_ME_IMPORTANT.txt` para mais informações

---

## 🎯 Recursos Adicionais

### Arquivos Úteis
- `ADD_DEPOT_BOXES_NEW_PLAYERS.txt` - Como adicionar depot boxes para novos jogadores
- `ENABLE_FULL_OPEN_PVP.txt` - Ativar PvP aberto completo
- `Check_console_not_starting.bat` - Diagnóstico se o servidor não iniciar
- `restarter.bat` - Script para reiniciar o servidor automaticamente

### Comandos Úteis (God Account)
```
/attr <atributo> <valor>  - Modificar atributos
/i <item>                 - Criar item
/m <monster>              - Criar monstro
/goto <player>            - Teleportar para jogador
/t <x>,<y>,<z>           - Teleportar para coordenadas
```

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Se você encontrar bugs ou tiver sugestões:
1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

---

## 📄 Licença

Este projeto é baseado no The Forgotten Server, que é licenciado sob GPL v2.

---

## 🌟 Créditos

- **The Forgotten Server Team** - Servidor base
- **OTLand Community** - Suporte e recursos
- **Hellgrave Team** - Customizações e conteúdo

---

## 📞 Suporte

Para suporte e discussões:
- Visite o fórum da comunidade
- Reporte bugs através das Issues do GitHub
- Junte-se ao Discord da comunidade

---

**Versão:** 3.7.5  
**Protocolo:** Tibia 10.98+  
**Última Atualização:** Janeiro 2026

---

## 🚀 Quick Start (Resumo)

1. ✅ Baixe e extraia o vcpkg para `C:\vcpkg\`
2. ✅ Abra `vc17/Hellgrave_Exodus.sln` no Visual Studio (2022 ou 2026)
3. ✅ Compile em **Release x64**
4. ✅ Configure o MySQL e importe o schema
5. ✅ Edite `config.lua` com suas configurações
6. ✅ Baixe o cliente do link acima
7. ✅ Execute o servidor e conecte-se!

**Divirta-se jogando Hellgrave Exodus! 🎮⚔️**
