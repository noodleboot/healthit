<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>
 
<h1>Software Engineering and Project Management</h1>

<h2>HealthIT - Project</h2>
<br> <hr> <br>
<h3>1. Problem Description</h3> <br> 
HealthIT is an organisation that operates in healthcare projects management. HealthIT
wants to integrate a powerful but simple medical appointment’s tool in their Information
System. In order to provide the necessary comfort to its collaborators, the organization
demands that such tool is capable of performing simple features:<br><br>
1. Schedule Medical Appointment – This feature must allow helpdesk professionals to set up
appointments by registering the patients’ names, the appointment date and time with an
available doctor according to its medical proficiency;<br><br>
2. Reschedule Medical Appointment – This feature must allow helpdesk professionals to
change the appointments details or even cancel them if the appointments have not yet
occurred. Therefore, a search operation must be included in this feature; <br><br>
3. Add Doctor of Medicine - This feature must allow helpdesk professionals to register
doctors’ details by registering doctors’ names, proficiency (pediatrics, dermatology,
cardiology, radiology or infectology), and social security numbers, check in and check out
hours. Additionally, this feature must allow the management of medical proficiencies;<br><br>
4. Consult Patient - This feature must allow doctors to register consultation details by
registering the patients’ symptoms and the medical diagnoses during a medical
appointment. Additionally, this feature must include a search operation to select the
scheduled appointment;<br><br>
<h5>Restrictions:</h5> all features must guarantee the data’s consistency. For instance, data
duplication is not tolerated, appointments can’t be changed if they already occurred, a doctor can’t
have two or more appointments at the same time, a doctor can’t access another doctor’s
appointments, and a doctor can’t have an appointment outside his check in and check out hours.
<hr><br><br>
<h3>2. Goals</h3> <br><br>
The goal of this assignment is the development of a healthcare information system that
addresses the needs of the organization. Therefore, it is necessary to execute a software
development process (SDP) that considers the analysis, design, test and implementation. The
features to develop must address the requirements and challenges proposed by the organization.
<br><br>
2.1 Analysis<br>
● Use case diagrams: use case identification, actors and relations;<br>
● Domain model;<br>
● Use case descriptions: main path and alternative paths.<br>
● Robustness diagrams: one diagram per use case;<br>
<br><br>
2.2 Design<br>
● Sequence diagrams: one diagram per use case;<br>
● Class Diagram.<br>
<br><br>
2.3 Implementation<br>
● Unit tests;<br>
● Source code;<br>
● Architecture diagram: installation and components.<br>
____________________________________________________________________________
Manual de instalação
HealthIT App

# REQUISITOS DO SERVIDOR

Uma vez que a aplicação "HealthIT" utiiliza a framework "Laravel" será necessário satisfazer alguns requisitos de sistema.
É também necessário ligação à Internet.

Estes requisitos podem ser cumpridos pela máquina virtual "Laravel Homestead".
É altamente recomendado a utilização do Homestead.

No entanto, se por algum motivo não estiver a usar o Homestead, é necessário que o server cumpra os seguintes requisitos:
-> PHP >= 5.6.4
-> OpenSSL PHP Extension
-> PDO PHP Extension
-> Mbstring PHP Extension
-> Tokenizer PHP Extension
-> XML PHP Extension
____________________________________________________________________________
# INSTALAÇÃO

Primeiros Passos:
● Se tiver uma máquina Windows, instale a aplicação Git for Windows (https://git-scm.com/download/win).
● Antes de começar a instalar o ambiente de desenvolvimento "Homestead", precisa de instalar o VirtualBox 5.1 (https://www.virtualbox.org/wiki/Downloads) e também o Vagrant (https://www.vagrantup.com/downloads.html).
● Inicie a aplicação Git Bash.




Instalar o Homestead Vagrant Box:
● Depois do VirtualBox e o Vagrant instalados, é preciso adicionar a box Homestead ao Vagrant usando o seguinte comando no Git Bash:
vagrant box add laravel/homestead


Instalar o Homestead:
● É possível instalar o Homestead clonando simplesmente o repositório para a directoria "home":
cd ~
git clone https://github.com/laravel/homestead.git Homestead

● Quando estiver terminada a clonagem, é preciso criar o ficheiro Homestead.yaml com o seguinte comando:
init.bat


Configurar o Homestead:
● Aceda à pasta Homestead e abra o ficheiro Homestead.yaml.
● Edite o campo provider:
provider: virtualbox

● Edite as pastas partilhadas e os sites de acesso à aplicação a seu gosto, como por exemplo:
folders:
- map: ~/Projetos
to: /home/vagrant/Projetos

sites:
- map: healthit.app
to: /home/vagrant/Projetos/HealthIT/Laravel/public




O Ficheiro Hosts:
● É necessário adicionar domínios para os sites no ficheiro hosts da sua máquina.
● No Windows está localizado em C:\Windows\System32\drivers\etc\hosts
● Adicione a seguinte linha ao ficheiro hosts:
192.168.10.10  healthit.app

● Verifique que o endereço IP é o mesmo do ficheiro Homestead.yaml


Acesso ao site:
● Execute o seguinte comando no Git Bash para iniciar a Vagrant Box:
vagrant up

● Quando quiser terminar a Vagrant Box:
vagrant halt

● Sempre que alterar os sites no ficheiro Homestead.yaml execute este comando para fazer a atualização dos mesmos:
vagrant reload --provision

● Para aceder ao site no seu browser escreva:
http://healthit.app


Aceder à aplicação HealthIT na sua máquina:
● Vamos agora clonar a aplicação HealthIT para a diretoria ~/Projetos com o seguinte comando:
git clone https://github.com/rezken1/healthit

● Na diretoria Homestead, execute este comando para aceder à maquina virtual de forma segura:
vagrant ssh

● É necessário ainda instalar as dependências da aplicação.

● Para isso, na maquina virtual, execute este comando na diretoria ~/Projetos/healthit
composer install

● De seguido será preciso gerar uma chave aleatória da aplicação com o comando:
php artisan key:generate

● Neste momento já poderá aceder à página inicial da aplicação através do link:
http://healthit.app


Configuração da base de dados:
● É possível gerir uma base de dados com um único ficheiro graças ao Adminer(https://www.adminer.org/).
● Faça o download do ficheiro adminer.php e mude o nome para index.php
● Crie a diretoria ~/Projetos/Adminer e mova o index.php para essa mesma diretoria.
● Adicione um novo site ao ficheiro Homestead.yaml:
- map: adminer.app
to: /home/vagrant/Projetos/Adminer

● Reinicie a sua máquina virtual no Git Bash, na diretoria Homestead:
vagrant reload --provision

● Insira esta linha ao ficheiro hosts:
192.168.10.10 adminer.app

● Já terá acesso ao servidor da base de dados através do link:
http://adminer.app

● Para criar a base de dados utilize as credenciais:
Username = Homestead
Password = secret

● Selecione a opção "Criar base de dados", dê o nome "healthit" à base de dados e no separador collation escolha "utf8_general_ci"
● No Git Bash volte a aceder à maquina virtual com o comando vagrant ssh, entre na diretoria ~/Projetos/healthit e faça a migração das tabelas com o seguinte comando:
php artisan migrate --seed

● As credenciais da base de dados da aplicação HealthIT são, por defeito:
Base de dados = healthit
Username = homestead
Password = secret


Fazer o login na aplicação:
● A HealthIT tem dois tipos de usuários: Helpdesk e Doctor
● Para fazer login como Helpdesk use:
Username = admin@healthit.com
Password = secret

● Para fazer login como Doctor
Username = doctor@healthit.com
Password = secret

A aplicação HealthIT está agora instalada e funcional na sua máquina !


