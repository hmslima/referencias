**Autor:** Henrique Matheus da Silva Lima

# Introdução<span id="intro"></span>

Leia o [README](README.md).

# XAMPP

XAMPP é um pacote que instala de forma simples os principais servidores web como Apache, banco de dados MariaDB e FTP junto com suporte a linguagens como PHP e Perl.

## Instalação

Aqui está o [link](https://www.apachefriends.org/) para download.

### No Windows

Não há muito mistério, execute o instalador e Next NeXT Next

### No Linux

Você pode encontrar dificuldades se você tentar executar o arquivo .run dentro da pasta `Downloads`. Mova o arquivo para outra pasta e rode o comando `sudo ./<nome_do_arquivo>.run`, substituindo *"<nome_do_arquivo>.run"* pelo nome do arquivo.

## Configuração (resolução de problemas)

Computador de desenvolvedor tem muita coisa instalada que pode usar uma da sportas utuilizadas pelo Xampp, então se algo der problema, tente mudar a pasta.

### Mudando a pasta do XAMPP no Linux

O servidor Apache roda os arquivos que se encontram dentro da pasta `/opt/lampp/htdocs/`. Não é nada conveniente estudar com a paste dentro do diretório `/`. Vamos colocar dentro do `/home`.

Crie a pasta onde você quer guardar seus arquivos. No meu exemplo, usarei o usuário fictício `carlos` e criarei a pasta ~/htdocs. Para não ter possíveis problemas, vamos mudar as permissões dessa pasta:

    sudo chmod 777 -R /home/carlos/htdocs/

*Adeque o código acima para o endereço que você escolher!* 

Feche o XAMPP:

    sudo /opt/lampp/lampp stop

Abra o arquivo de configuração do XAMPP, para editar usarei o **nano**, mas você pode usar o editor de texto da sua preferência:

    sudo nano /opt/lampp/etc/httpd.conf

Haverá 4 linhas de código que você precisará editar, elas se encontrarão em 2 lugares.

Vá descendo até encontrar...

    User daemon
    Group daemon

Substitua "daemon" por seu nome de usuário. Você usa seu nome de usuário em `Group` também porque o grupo do seu usuário normalmente tem o mesmo nome do nome do usuário. Vamos dizer que o nome do meu usuário é `carlos`, eu deixaria assim:

    User carlos
    Group carlos

*Adeque o código acima para o seu nome de usuário!* 

Depois procure por:

    DocumentRoot "/opt/lampp/htdocs"
    <Directory "/opt/lampp/htdocs">

Mude o endereço `"/opt/lampp/htdocs"` para o local onde você quer guardar seus arquivos. Vamos dizer que que quero que seja a pasta ~/htdocs na minha própria pasta de usuário, cujo nome no nosso exemplo é `carlos`. Ficaria assim:

    DocumentRoot "/home/carlos/htdocs"
    <Directory "/home/carlos/htdocs">

*Adeque o código acima para o endereço que você escolher!*

Salve e feche o arquivo e inicie o XAMPP pra ver se tudo deu certo:

    sudo /opt/lampp/lampp start

Se por algum motivo você quiser abrir o painel de controle do XAMPP, use o comando abaixo:

    sudo /opt/lampp/manager-linux-x64.run

Assumo que você esteja usando a versão 64bit do Linux, se você estiver na versão 32bit, o comando é `sudo /opt/lampp/manager-linux.run`

## Considerações finais

Sim, essa configuração definitiamente não deixa o sistema seguro, mas o objetivo é estudo, realisticamente ninguém vai invadir seu computador por causa disso.

Boa sorte nos estudos!