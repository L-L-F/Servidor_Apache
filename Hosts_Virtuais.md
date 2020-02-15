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

`<!DOCTYPE html>
<html>
<head>
	<title>Teste</title>
</head>
<body>
<h1>Olá Mundo</h1>
</body>
</html>`

### Criando Arquivo de Host Virtual

Adicionaremos um arquivo de configuração para o diretorio host criado. Crie Crie um arquivo em /etc/apache2/sites-available/.
Ultilizaremos como exemplo o nome do diretorio do hosts <Nome_do_Host>.conf. Você pode ultlizar o editor qualquer pelo terminal. Exmplo nano ou vim. Utilize o comando:

`$ cd /etc/apache2/sites-available/
$ sudo nano <Nome_do_Host>.conf`

Dentro desse arquivo insira os dados abaixo e salve.

`<VirtualHost *:80>
        ServerAdmin <Nome_do_Host>@gmail.com
        ServerName <Nome_do_Host>.com
        ServerAlias www.<Nome_do_Host>.com
        DocumentRoot /var/www/<Nome_do_Host>
        ErrorLog ${APACHE_LOG_DIR}/erro.log
        Customlog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>`

### Ativando Host Virtual

Continunado no diretorio /etc/apache2/sites-available/. Para ativar o host virtual utilize o comando:

`$ sudo a2ensite <Nome_do_Host>.conf`

Caso queira desabilitar utilize o comando:

`$ sudo a2dissite <Nome_do_Host>.conf`

### Configurando arquivo de host local (contornando a falta de um DNS)

(Atualizando...)
