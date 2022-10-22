# Infraestrutura como Código: Script de Criação de Estrutura de Usuários

## O que é?

Infraestrutura como código (IaC) é o gerenciamento e provisionamento da infraestrutura por meio de códigos, em vez de processos manuais.

Com a IaC, são criados arquivos de configuração que incluem as especificações da sua infraestrutura, facilitando a edição e a distribuição de configurações. Ela também assegura o provisionamento do mesmo ambiente todas as vezes.

## Controle de versão

O controle de versão é uma parte importante da IaC. Os arquivos de configuração devem pertencer à fonte como qualquer outro código-fonte de software. Ao implantar a infraestrutura como código, também é possível separá-la em módulos, que podem ser combinados de diferentes maneiras por meio da automação.

## Principal benefício

Ao automatizar o provisionamento da infraestrutura com a IaC, os desenvolvedores não precisam provisionar e gerenciar manualmente servidores, **sistemas operacionais, armazenamento** e outros componentes de infraestrutura sempre que criam ou implantam uma aplicação.

## Infraestrutura proposta

![Untitled](Infraestrutura%20como%20Co%CC%81digo%20Script%20de%20Criac%CC%A7a%CC%83o%20de%2018cb91baa4fb4dcf8cf508b348df36e2/Untitled.png)

## ****Definições****

- Excluir diretórios, arquivos, grupos e usuários criados anteriormente;
- Todo provisionamento deve ser feito em um arquivo do tipo Bash Script;
- O dono de todos os diretórios criados será o usuário root;
- Todos os usuários terão permissão total dentro do diretório **publico**;
- Os usuários de cada grupo terão permissão total dentro de seu respectivo diretório;
- Os usuários não poderão ter permissão de leitura, escrita e execução em diretórios de departamentos que eles não pertencem;
- Subir arquivo de script criado para a sua conta no GitHub.

## Passos realizados

- Como já tinha uma MV criada, exclui todos os diretórios, arquivos, grupos e usuários criados anteriormente;
    - Logado como root, no diretório raiz, exclui os diretórios já criados anteriormente:
        
        <aside>
        💡 rm -Rf /textos/
        
        </aside>
        
    - Excluir todos os usuários criados antes:
        
        <aside>
        💡 cat /etc/passwd  
        ****userdel -r gabriel
        
        </aside>
        
    - Excluir os grupos:
        
        <aside>
        💡 cat /etc/group
        groupdel GRP_ADM
        
        </aside>
        
    - Criando script:
        
        <aside>
        💡 cd /
        mkdir /script
        nano iacl.sh
        
        </aside>
        
        ![Untitled](Infraestrutura%20como%20Co%CC%81digo%20Script%20de%20Criac%CC%A7a%CC%83o%20de%2018cb91baa4fb4dcf8cf508b348df36e2/Untitled%201.png)
        
        ![Untitled](Infraestrutura%20como%20Co%CC%81digo%20Script%20de%20Criac%CC%A7a%CC%83o%20de%2018cb91baa4fb4dcf8cf508b348df36e2/Untitled%202.png)
        
    
    - Criando permissão de execução do script:
        
        <aside>
        💡 chmod +x iacl.sh
        
        </aside>
        
    - Testando script criado:
        
        <aside>
        💡 ./iacl.sh
        
        </aside>
        
        ![Untitled](Infraestrutura%20como%20Co%CC%81digo%20Script%20de%20Criac%CC%A7a%CC%83o%20de%2018cb91baa4fb4dcf8cf508b348df36e2/Untitled%203.png)
        

Tudo certo, agora iremos subir o projeto para um repositório no **GitHub:**

- Verificando se o Git está instalado na VM:

<aside>
💡 apt install git -y

</aside>

- Configurando o git:

<aside>
💡 git config —global [user.email](http://user.email) “[EMAIL]”
git config —global [user.](http://user.email)name “[NOME DO USUÁRIO]”

</aside>

- Subindo o projeto:

<aside>
💡 git init
git add .
git commit -m “Arquivos IaC v.1”
git branch -M main
git remote add origin [git@github.com](mailto:git@github.com):AndersonGabrielCalasans/LinuxProject-InfraAsACode.git
git push -u origin main

</aside>