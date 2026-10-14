<div align="center">

🤖 ZzzClawz Básico

Um bot de WhatsApp simples, leve e direto ao ponto.

Comandos úteis, perfil de usuário, recompensa diária e funções básicas para grupos — feito com Node.js e Baileys.






































</div>


Sobre o projeto: uma base educacional e enxuta para experimentar um bot de WhatsApp. Não inclui inteligência artificial, loja, RPG avançado nem integrações externas.




✨ O que ele tem

•
📋 Menu de ajuda e comando de status (.menu, .ajuda, .ping, .info).

•
👤 Cadastro e perfil básico (.cadastro, .perfil, .eu).

•
🪙 Saldo e recompensa diária: 100 moedas + 10 XP (.saldo, .carteira, .diaria).

•
🎲 Diversão rápida: dado configurável e cara ou coroa (.dado, .moeda, .coinflip).

•
👥 Utilitários para grupos: marcar participantes, enviar mensagem com menções e consultar o link do grupo (.marcar, .hidetag, .linkgp).

•
📙 Exibição de regras básicas (.regras).

•
💾 Dados dos usuários salvos localmente em database/users.json.

•
🔐 Conexão por QR Code e sessão local em assets/auth/.

•
⚙️ Prefixo e nome do bot configuráveis pelas variáveis PREFIX e BOT_NAME.

O que não está implementado

Este projeto não tem IA, loja, pagamentos, sistema de níveis com evolução automática, painel web, banco de dados remoto, comando para editar regras ou recursos avançados de RPG. O XP é registrado, mas o nível permanece no valor inicial nesta versão.




🧾 Comandos

O prefixo padrão é .. Ele pode ser alterado pela variável PREFIX.

Comando
O que faz
Onde funciona
.menu / .ajuda
Mostra a lista de comandos
Conversa ou grupo
.ping
Confirma que o bot está online
Conversa ou grupo
.info
Mostra informações básicas do bot
Conversa ou grupo
.cadastro <nome>
Salva seu nome (até 40 caracteres)
Conversa ou grupo
.perfil / .eu
Mostra nome, nível, XP e moedas
Conversa ou grupo
.saldo / .carteira
Consulta suas moedas
Conversa ou grupo
.diaria
Recebe 100 moedas e 10 XP uma vez por dia
Conversa ou grupo
.dado [lados]
Rola um dado; por padrão, de 6 lados (máximo 100)
Conversa ou grupo
.moeda / .coinflip
Joga cara ou coroa
Conversa ou grupo
.marcar [texto]
Envia texto mencionando os participantes
Grupo; somente administradores
.hidetag [texto]
Envia texto com menções aos participantes
Grupo; somente administradores
.linkgp
Obtém o link de convite do grupo
Grupo; somente administradores
.regras
Exibe as regras padrão definidas no código
Conversa ou grupo





⚠️ Use .marcar e .hidetag com cuidado: eles podem notificar muitas pessoas de uma só vez.




🧰 Requisitos

•
Node.js 20 ou superior — o npm é instalado junto com o Node.js.

•
Um telefone com WhatsApp para vincular a sessão por QR Code.

•
Internet disponível durante a execução.

•
Para hospedagem contínua: um servidor com processo persistente e armazenamento que não seja apagado ao reiniciar.




🚀 Executar localmente

1. Baixe o projeto

Clone o repositório (depois de publicá-lo) ou extraia o arquivo ZIP:

Bash






2. Instale as dependências

Bash


npm install



3. Configure as variáveis opcionais

O padrão é PREFIX=. e BOT_NAME=Bot Básico. Para usar outros valores no terminal:

Linux/macOS:

Bash


export PREFIX="."
export BOT_NAME="ZzzClawz"



Windows PowerShell:

Plain Text


$env:PREFIX = "."
$env:BOT_NAME = "ZzzClawz"



O arquivo .env.example é apenas um modelo: o projeto não carrega arquivos .env automaticamente. Configure as variáveis no terminal ou no painel do serviço de hospedagem.

4. Inicie o bot e vincule o WhatsApp

Bash


npm start



O QR Code aparecerá no terminal. No celular, abra o WhatsApp, acesse Dispositivos conectados → Conectar dispositivo e escaneie o código. Após a conexão, a sessão será gravada em assets/auth/.

Para encerrar localmente, use Ctrl+C.




☁️ Hospedar em um VPS Linux

Para deixar o bot online continuamente, uma opção simples é um VPS Ubuntu/Debian com Node.js 20+, acesso de saída à internet e disco persistente. O GitHub armazena o código, mas não mantém o bot rodando. Plataformas gratuitas que suspendem processos ou apagam arquivos podem desconectar o WhatsApp ou perder a sessão.

Passo a passo usando PM2

1.
Instale Node.js 20+ e Git no servidor. Confira as versões:

Bash


node --version
npm --version
git --version





2.
Clone o seu repositório e instale as dependências:

Bash


git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
cd SEU-REPOSITORIO
npm install





3.
Instale o gerenciador de processos PM2:

Bash


sudo npm install -g pm2





4.
Defina as variáveis e inicie uma única instância do bot:

Bash


export PREFIX="."
export BOT_NAME="ZzzClawz"
pm2 start src/index.js --name zzzclawz
pm2 save





5.
Veja os logs para encontrar o QR Code e escaneie-o no WhatsApp:

Bash


pm2 logs zzzclawz





6.
Para iniciar o PM2 automaticamente após reinicializações do VPS, execute:

Bash


pm2 startup



O comando mostrará uma instrução adicional. Copie e execute a instrução exibida pelo próprio PM2 com as permissões indicadas; depois rode pm2 save novamente.



Comandos úteis:

Bash


pm2 status                 # Ver o estado do processo
pm2 logs zzzclawz          # Ver os logs
pm2 restart zzzclawz       # Reiniciar o bot
pm2 stop zzzclawz          # Parar o bot
pm2 save                   # Salvar a lista de processos do PM2



⚠️ Persistência e sessão

•
Preserve assets/auth/ e database/users.json entre reinicializações e atualizações do servidor.

•
Faça cópias de segurança privadas desses dados; eles contêm a sessão e os dados dos usuários.

•
Nunca publique assets/auth/, .env, credenciais ou um banco real no GitHub.

•
Não execute duas cópias do bot usando a mesma sessão ao mesmo tempo.

•
Se o WhatsApp desconectar a sessão, pode ser necessário apagar assets/auth/ no servidor e vincular novamente pelo QR Code. Isso encerra a sessão anterior.

•
O bot não precisa receber tráfego HTTP externo; ele precisa conseguir se conectar à internet para comunicar-se com o WhatsApp.




📤 Como publicar no GitHub

Opção A — pelo site do GitHub

1.
Entre no 

GitHub e crie um repositório novo.

2.
Escolha um nome, por exemplo zzzclawz-basico.

3.
Se for enviar estes arquivos locais, crie o repositório sem adicionar outro README, .gitignore ou licença — assim evita conflitos.

4.
Use Add file → Upload files e envie os arquivos do projeto. Não envie node_modules/, .env, assets/auth/ nem dados reais de database/.

5.
Escreva uma mensagem de commit, por exemplo docs: adiciona apresentação do projeto, e confirme o envio.

Opção B — pelo terminal

Dentro da pasta do projeto:

Bash


git init -b main
git add .
git status                 # Confira os arquivos antes de publicar
git commit -m "feat: publica bot básico de WhatsApp"
git remote add origin https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
git push -u origin main



Antes de git push, confira git status e confirme que nenhum arquivo de sessão, segredo ou banco de dados real será enviado. As regras de .gitignore deste projeto ajudam a proteger esses arquivos.

Texto pronto para o campo “About” do repositório


🤖 Bot básico de WhatsApp em Node.js com comandos essenciais, perfil, recompensa diária e ferramentas simples para grupos. Feito com Baileys.

Sugestões de tópicos: whatsapp-bot · nodejs · javascript · baileys · whatsapp




🗂️ Estrutura do projeto

Plain Text


zzzclawz-basico/
├── database/
│   ├── .gitkeep
│   └── users.example.json   # exemplo vazio; não contém dados reais
├── src/
│   └── index.js             # conexão, comandos e lógica do bot
├── .env.example             # modelo das variáveis opcionais
├── .gitignore               # exclui dependências, sessão e dados locais
├── package.json
└── README.md



Em execução, o bot cria assets/auth/ e database/users.json automaticamente. Esses arquivos locais não devem ser publicados.




🔒 Privacidade e uso responsável

Este projeto utiliza Baileys, uma biblioteca de terceiros para conexão com o WhatsApp Web; não é um produto oficial nem afiliado ao WhatsApp/Meta. O uso de automações pode estar sujeito aos termos e limites da plataforma. Use uma conta apropriada, evite spam e respeite a privacidade e o consentimento dos participantes.

A sessão em assets/auth/ permite acesso à conta vinculada: trate-a como uma credencial secreta. Se ela for exposta, desconecte os dispositivos vinculados no WhatsApp e gere uma sessão nova.




🧪 Tecnologias

•


Node.js

•


Baileys

•


Pino — logger

•


qrcode-terminal — QR Code no terminal

