# Instalação Servidor Apache Ubunto

Material de referência.

## Preparando Sistema

Primeiramente atualizaremos os repositorios do Ubunto pra isso você deve abrir o terminal e digitar o comando abaixo:

`$ sudo apt-get update`

*Ao digitar "sudo" o terminal pedira a senha do administrador.

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
*Para MOVER

`sudo mv Site /var/www/html/`

*Para COPIAR

`sudo cp Site /var/www/html/`

Pronto. Agora só acessar digitando o enderço no navegador onde ele esta hopedado pelo Servidor Apache.

## Acessando Páginas hospedadas do Apache

Em seu navegador digite http://localhost/<NomeDaPasta> o endereço da pagina padrão do Servidor Apache mais o nome da pasta onde se encontra o HTML, CSS e o JavaScript e pronto.
