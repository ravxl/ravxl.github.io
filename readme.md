# NF-e Sebrae (Quick Fix)

  Depois da atualização do macOS Catalina o sistema de arquivos do S.O. passou a ser montado em modo somente leitura, fazendo com que o comando de mkdir não possa mais ser executado na raiz (/). Além disso, durante o processo de instalação da atualização do sistema operacional, o sistema movimentou os arquivos da raiz para dentro de um diretório novo na área de trabalho do usuário que iniciou a atualização do sistema. Esse tutorial está dividido em duas partes:
  
# Primeira Parte: Recuperando o NF-e para que ele volte a rodar:

  Ao iniciar o NF-e você vai receber uma tela de erro e no detalhamento do erro java uma menção a falha da conexão jdbc como a exibida abaixo:
   
![emissor nf-e sebrae](https://github.com/ravxl/nfe-sebrae/blob/master/emissor_falha.jpg)   

## Passo-a-passo para recuperar o nf-e

1. Você precisa criar um novo diretório para a base de dados;
2. Siga os seguintes passos:
  * Abra um terminal
  * sudo su -
  * mkdir /System/Volumes/Data/database
  * chmod -R 777 /System/Volumes/Data/database
  * echo "database System/Volumes/Data/database" | tee -a /etc/synthetic.conf
  * reboot
3. Quando o pc reiniciar, verifique a existência de uma nova pasta /database
4. Abra o emissor de notas fiscais do sebrae

  Provavelmente nesse momento você vai perceber que a base de dados está zerada. Se isso não for um problema para você, pode ignorar o restante dos passos.
  
# Segunda Parte: Recupebando a base de dados do NF-e depois que ele voltou a rodar

  A antiga base de dados provavelmente estará dentro do diretório:
  
  > /Users/Shared/Previously\ Relocated\ Items/Security/database
  
  ## Passo-a-passo para recuperar a base de dados do nf-e
  1. Feche o emissor de nf-e caso ele esteja aberto
  2. Abra um terminal
  3. sudo su -
  4. cp -Rv /Users/Shared/Previously\ Relocated\ Items/Security/database /System/Volumes/Data/database
  
  Assim que terminar a cópia, execute novamente o emissor de notas fiscais eletrônicas do Sebrae. Ele irá abrir e a base de dados estará recuperada. 
  
Att,
Ravel Leite

Ps.: Se você tiver dificuldade em criar o arquivo [synthetic.conf](https://github.com/ravxl/nfe-sebrae/blob/master/synthetic.conf), encontre um simples template dele no repositório 
