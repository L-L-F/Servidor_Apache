# Instalação Servidor Apache Ubunto

Material de referência.

## Preparando Sistema

Primeiramente atualizaremos os repositorios do Ubunto pra isso você deve abrir o terminal e digitar o comando abaixo:

`$ sudo apt-get update`

Ao digitar "sudo" o terminal pedira a senha do administrador*

## Instalação

Depois de Atualizar os repositorios, patiremos agora para a instalaçâo do apache2. Com o termminal aberto digitaremos o codigo abaixo:

`$ sudo apt-get install apache2`

Depois disso, confirma para continuar a instalção.

Pronto Apache instalado.

## Configurando Firewall

Depois de concluir todo o processo de instalação do Apache para habilitar o firewall UFW. Você certifique-se de que seu firewall permite tráfego HTTP e HTTPS. Para isso deve seguir alguns passos.

Insira os codigos abaixo para verificar se o Aplicativo Apache Full está acessível:

`$ sudo ufw app list`

Depois de verificado o perfil, inserindo:

`$ sudo ufw app info "Apache Full"`

Aparecerá as Portas 80,443/tcp. Agora permita o tráfego HTTP e HTTPS.

`sudo ufw allow in "Apache Full"`

Pronto Firewall configurado.

## Acessando Página Padrão do Apache

Para fazer a verificação do funcionamento do Servidor Apache digite o endereço http://localhost/ em seu navegado e confira a página web padrão do Apache, que está lá para fins de teste e informação.

## Adicionando Páginas HTML, CSS e JavaScript no Servidor Apache

Para adicionar uma pagina Web no Servidor Apache è muito simples. Procure o local onde sua pasta onde seu site está armazenado você vai mover ou copiar a pasta para dentro da pasta do Servidor Apache utilizando. Para isso, utilizará o terminal para acessar a pasta do Site.

`$ cd /home/<NomedoUsuario>/Downloads`

Depois de está no destino absoluto da pasta, agora só mover ou copiar o arquivo usando o comando sudo para ter permissão de colar a pasta no destino onde se encotra o Apache. Os Comandos são:

Para MOVER*

`sudo mv <NomeDaPasta> /var/www/html/`

Para COPIAR*

`sudo cp <NomeDaPasta> /var/www/html/`

Pronto. Agora só acessar digitando o enderço no navegador onde ele esta hopedado pelo Servidor Apache.

## Acessando Páginas hospedadas do Apache

Em seu navegador digite http://localhost/"<NomeDaPasta>" o endereço da pagina padrão do Servidor Apache mais o nome da pasta onde se encontra o HTML, CSS e o JavaScript e pronto agora é só selecionar o Arquivo desejado.
  
# Configurando Hosts Virtuais no Apache

Material de referência.

## Verificando Status do Apache

Primeiramente verificaremos o status do Apache para proceguirmos, insira o codigo abaixo no terminal:

`$ sudo service apache2 status`

Ao digitar "sudo" o terminal pedira a senha do administrador*

O status deve estar "verde" com a mensagem active (running).

## Configurando Hosts Virtuais Apache

Depois de ter verificado o Status. Proceguiremos com as configurações para adicionar os Hosts.

### Criando Estrutura de Diretórios

A estrutra que utilizaremos como ponto de partida o diretorio padrão do apache. para criar o diretorio utilize o comando:

`$ sudo mkdir /var/www/<Nome_do_Host>`

### Concedendo Permissões dos Diretorios

Concederemos totais permiçoes dos diretorios para que o usuário comum possa realizar alterações necessarias. Utilize o comando:

`$ sudo chown –R $USER:$USER /var/www/<Nome_do_Hosts>
$ sudo chmod –R 755 /var/www/<Nome_do_Host>`

### Criando Arquivo Teste ou Ultilize um Aquivo Pronto

Crie um arquivo no formato .html para teste ou ultilize um HTML pronto para testar, você pode usar o aplicativo Sublime para fazer o HTML. Segue um exemplo:

<!DOCTYPE html>
<html>
<head>
	<title>Teste</title>
</head>
<body>
<h1>Olá Mundo</h1>
</body>
</html>

### Criando Arquivo de Host Virtual

Adicionaremos um arquivo de configuração para o diretorio host criado. Crie Crie um arquivo em /etc/apache2/sites-available/.
Ultilizaremos como exemplo o nome do diretorio do hosts <Nome_do_Host>.conf. Você pode ultlizar o editor qualquer pelo terminal. Exmplo nano ou vim. Utilize o comando:

`$ cd /etc/apache2/sites-available/
$ sudo nano <Nome_do_Host>.conf`

Dentro desse arquivo insira os dados abaixo e salve.

<VirtualHost *:80>
`
        ServerAdmin <Nome_do_Host>@gmail.com
        ServerName <Nome_do_Host>.com
        ServerAlias www.<Nome_do_Host>.com
        DocumentRoot /var/www/<Nome_do_Host>
        ErrorLog ${APACHE_LOG_DIR}/erro.log
        Customlg ${APACHE_LOG_DIR}/access.log combined
`	
</VirtualHost>

### Ativando Host Virtual

Continunado no diretorio /etc/apache2/sites-available/. Para ativar o host virtual utilize o comando:

`$ sudo a2ensite <Nome_do_Host>.conf`

Caso queira desabilitar utilize o comando:

`$ sudo a2dissite <Nome_do_Host>.conf`

### Configurando arquivo de host local (contornando a falta de um DNS)

(Atualizando...)
