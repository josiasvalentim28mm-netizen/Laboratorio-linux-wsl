# Laboratório Linux com WSL (Ubuntu + Kali)

Laboratório de cibersegurança montado no próprio Windows com o **WSL (Windows Subsystem for Linux)**, com duas distribuições: **Ubuntu**, para aprender os comandos base, e **Kali Linux**, com ferramentas de segurança. Tudo feito pela linha de comandos, a partir do PowerShell.

## Porquê o WSL

O WSL permite correr um Linux real dentro do Windows, sem precisar de uma máquina virtual pesada. É oficial da Microsoft e muito usado por programadores e profissionais de segurança.

| | Detalhe |
| --- | --- |
| **Vantagens** | Leve, rápido de abrir, partilha ficheiros com o Windows, ótimo para aprender comandos |
| **Limitação** | Sem acesso direto ao Wi-Fi nem à rede física (fica numa rede virtual isolada) |
| **Quando usar uma VM** | Para testar malware ou ataques perigosos: isolamento total e snapshots |

## Passo 1: Instalar o WSL

```powershell
wsl --install
```

Ativa o motor do WSL. No fim, é preciso reiniciar o computador:

```powershell
Restart-Computer
```

## Passo 2: Instalar o Ubuntu

Depois de reiniciar, o Ubuntu costuma abrir sozinho. Se não abrir:

```powershell
wsl --install -d Ubuntu
```

Na primeira abertura, pede um **nome de utilizador** (minúsculas, sem espaços) e uma **palavra-passe**. Enquanto se escreve a palavra-passe não aparece nada no ecrã, o que é normal no Linux.

## Passo 3: Instalar o Kali Linux

O WSL permite várias distribuições ao mesmo tempo:

```powershell
wsl --install -d kali-linux
```

## Passo 4: Atualizar o sistema

```bash
cd ~
sudo apt update
sudo apt upgrade -y
```

| Comando | O que faz |
| --- | --- |
| `apt update` | Atualiza o catálogo de programas, sem instalar nada |
| `apt upgrade` | Instala as atualizações do que já existe |

## Passo 5: Instalar as ferramentas do Kali

O Kali no WSL vem quase vazio. Para instalar o conjunto de ferramentas de fábrica (Nmap, Metasploit, Wireshark, tcpdump e outras):

```bash
sudo apt install -y kali-linux-default
```

É um download grande, de 2 a 3 GB. Durante a instalação aparecem ecrãs de configuração:

| Ferramenta | Pergunta | Escolha |
| --- | --- | --- |
| Wireshark / dumpcap | Permitir a utilizadores normais capturar pacotes? | **Yes** |
| Kismet | Adicionar o utilizador ao grupo kismet | Nome de utilizador |
| macchanger | Mudar o MAC automaticamente? | **No** |

## Como abrir o Kali

1. Menu Iniciar → escrever **Kali**.
2. No PowerShell: `wsl -d kali-linux`
3. No Windows Terminal: seta ao lado do separador → **Kali Linux**.

## Conceitos aprendidos

- **WSL vs VM:** quando usar cada um.
- **sudo:** executar como superutilizador (root), aplicando o princípio do menor privilégio.
- **Grupos no Linux:** dar permissão a uma ferramenta (ex.: grupo wireshark) sem dar acesso a tudo.
- **Distribuições:** o kernel Linux é o mesmo "motor"; cada distro é um "veículo" diferente à volta dele.

## Resultado

Um laboratório Linux funcional dentro do Windows, com Ubuntu e Kali, pronto para praticar comandos e ferramentas de segurança.
