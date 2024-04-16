# ProjetoAWS

# Sobre o pipe.yaml

Instruções para Configurar um Pipeline de Implantação usando CodePipeline
Este modelo de CloudFormation cria um pipeline de implantação para uma aplicação usando CodePipeline. O pipeline é configurado para buscar o código do repositório CodeCommit, construir o código usando CodeBuild e implantar a aplicação usando CodeDeploy.

Passos para Configuração:
Execute o Modelo CloudFormation:

Use este arquivo YAML para criar o stack no CloudFormation.
Configuração do Pipeline:

O pipeline consiste em três estágios: Source, Build e Deploy.
No estágio Source, o pipeline busca o código do repositório CodeCommit.
No estágio Build, o pipeline constrói o código usando CodeBuild.
No estágio Deploy, a aplicação é implantada usando CodeDeploy.
Artefatos e Implantação:

O pipeline usa um bucket S3 para armazenar os artefatos gerados durante a compilação e a implantação.
CodeBuild e CodeDeploy têm papéis IAM associados para permitir que eles executem as ações necessárias.
Configuração Adicional:

É necessário configurar os nomes do aplicativo e do grupo de implantação em CodeDeploy de acordo com sua aplicação.
Além disso, revise as políticas IAM associadas aos papéis para garantir que tenham as permissões necessárias para suas operações.
Acesso ao Pipeline:

Após a criação do pipeline, você pode acessá-lo na console da AWS CodePipeline para monitorar e gerenciar suas implantações.
Criação do Stack via AWS CLI:

Use o seguinte comando AWS CLI para criar o stack usando o arquivo YAML fornecido:
aws cloudformation create-stack --stack-name CreatePipe --template-url https://s3.amazonaws.com/infra-742601030847/pipe.yaml --region us-east-1 --capabilities CAPABILITY_IAM

# Sobre template.yaml

Instruções para Configurar uma Instância EC2 com Nginx usando CloudFormation
Este modelo CloudFormation cria uma instância EC2 e configura um servidor Nginx para hospedar uma página web estática.

Passos para Configuração:
Execute o Modelo CloudFormation:

Use este arquivo YAML para criar o stack no CloudFormation.
Configuração da VPC e Subnet:

O template cria uma VPC e uma subnet pública na região us-east-1 (substitua conforme necessário).
Uma tabela de roteamento e uma regra de rota são configuradas para permitir o tráfego de saída para a internet.
Configuração do Security Group:

Um security group é configurado para permitir o tráfego HTTP (porta 80) e SSH (porta 22) de qualquer lugar (0.0.0.0/0).
Criação da Instância EC2:

Uma instância EC2 do tipo t2.micro é criada na subnet pública.
A instância é inicializada com o sistema operacional Ubuntu 20.04 LTS e o serviço Nginx é instalado.
Uma página HTML básica é criada no diretório /var/www/html/, exibindo o endereço IP público da instância EC2.
Acesso à Página Web:

Após a criação da instância EC2 e a conclusão do processo de inicialização, você pode acessar a página web estática hospedada na instância usando o endereço IP público fornecido.
Customização Adicional:

Personalize o conteúdo da página HTML conforme necessário, editando o script UserData no template.
Certifique-se de revisar as configurações de segurança, como as regras de ingresso do security group, para garantir a segurança da sua instância.
Com esses passos, você deve ter uma instância EC2 configurada com Nginx e pronta para hospedar sua página web estática. Certifique-se de monitorar e gerenciar sua instância conforme necessário, e personalize conforme as necessidades específicas do seu projeto.

# Mais

Claro que foi feito de um forma com o CI/CD com serviço de repositório da AWS codecommit, mas poderia ser feito com o github, gitlab por exemplo.
Além que poderia ser feito de outra forma, com uma regra do eventbridge e lambda, que ao ver alterações do repositório, trigasse a lambda para update da stack.
Mais um ponto que poderia usar o github actions ou jenkins para pipeline.
Foi utilizado o cloudformation como IaC, mas poderia também usar o terraform.
