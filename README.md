Projeto 1 — Montar um Laboratório Linux com WSL (Ubuntu + Kali)
Ficheiro README.md pronto para publicar no GitHub. Copia este conteúdo para o teu repositório.
Objetivo
Montar um laboratório de cibersegibertrança no próprio Windows, usando o WSL (Windows Subsystem for Linux), com duas distribuições: Ubuntu (para aprender os comandos base) e Kali Linux (com ferramentas de segurança). Tudo feito pela linha de comandos, a partir do PowerShell.
Porquê o WSL
O WSL permite correr um Linux real dentro do Windows, sem precisar de uma máquina virtual pesada. É oficial da Microsoft e muito usado por programadores e profissionais de segurança.
• Vantagem: leve, rápido de abrir, partilha ficheiros com o Windows, ótimo para aprender comandos.
• Limitação: não tem acesso direto ao Wi-Fi nem à rede física (fica numa rede virtual isolada), por isso scans reais à rede e ataques de Wi-Fi exigem o Kali numa VM em modo bridge ou instalado direto no disco.
• Quando usar VM em vez de WSL: para testar malware ou ataques perigosos, a VM dá isolamento total e snapshots (fotografias do sistema para voltar atrás).
Passo 1 — Instalar o WSL
No PowerShell:
wsl --install
Isto ativa o motor do WSL. No fim pede para reiniciar o computador.
Restart-Computer
Passo 2 — Instalar o Ubuntu
Após reiniciar, o Ubuntu costuma abrir sozinho. Se não abrir:
wsl --install -d Ubuntu
Na primeira abertura, pede um nome de utilizador (minúsculas, sem espaços) e uma palavra-passe (não aparece nada no ecrã enquanto se escreve — é normal no Linux).
Passo 3 — Instalar o Kali Linux
O WSL permite várias distribuições ao mesmo tempo. Para adicionar o Kali:
wsl --install -d kali-linux
Pede de novo nome de utilizador e palavra-passe para o Kali.
Passo 4 — Atualizar o sistema
Dentro do Kali, ir para a pasta pessoal e atualizar:
cd ~
sudo apt update
sudo apt upgrade -y
• apt update — atualiza o catálogo de programas (não instala nada).
• apt upgrade — instala as atualizações do que já existe.
Passo 5 — Instalar as ferramentas do Kali
O Kali no WSL vem quase vazio. Para instalar o conjunto de ferramentas de fábrica (Nmap, Metasploit, Wireshark, tcpdump, etc.):
sudo apt install -y kali-linux-default
É um download grande (2–3 GB). Durante a instalação aparecem ecrãs de configuração:
• Wireshark / dumpcap — permitir a utilizadores normais capturar pacotes? Yes
• Kismet — adicionar o utilizador ao grupo kismet: escrever o nome de utilizador.
• macchanger (mudar MAC automaticamente) — No.
Como abrir o Kali depois
1.  Menu Iniciar → escrever Kali.
2.  No PowerShell: wsl -d kali-linux.
3.  No Windows Terminal: setinha ao lado do separador → Kali Linux.
Conceitos aprendidos
• WSL vs VM: quando usar cada um.
• sudo: executar como superutilizador (root); aplica o princípio do menor privilégio.
• Grupos no Linux: dar permissão a uma ferramenta (ex.: grupo wireshark) sem dar acesso a tudo.
• Distribuições: o kernel Linux é o mesmo (o "motor"); cada distro é um "veículo" diferente à volta dele.
Resultado
Um laboratório Linux funcional dentro do Windows, com Ubuntu e Kali, pronto para praticar comandos e ferramentas de segurança.
