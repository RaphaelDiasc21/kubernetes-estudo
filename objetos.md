 - Kubernetes trabalha em conjunto com objetos para realizar todo o funcionamento do sistema, esse objetos vão desde um simples pod até um deployment


 - Tipos de Objetos
   - Pod: Contém um ou mais containers rodando, é a menor unidade na qual o Kubernete interage, esse objeto contem recursos compartilhados (volumes) para todos os containers rodando dentro dele, além disso cada pod tem um IP interno por padrão (containers dentro de um pod podem se comunicar uns com os outros através do 'localhost')
        - Pods são desenhados para serem efêmeros, o Kubernetes starta, para e substitui eles conforme a necessidade, da mesma forme que containers não mantém dados, os pods também não mantêm. O kubernete que vai gerenciar os pods e não o administrador e para isso precisa-se de um objeto contralador na qual vai criar e gerenciar os pods para nós

   - Deployment: Objeto que controla um ou multiplos PODS. A ideia por trás desse objeto é que nós declaramos um estado desejado para o cluster (define quais pods e containers serão rodados, bem como o número de instâncias). Esses objetos podem escalar dinamincamente ou automáticamente.

      + Criando um objeto deloyment de forma imperativa
        - kubectl create deployment <nome do deployment> --image=<nome da imagem>

      + Escalando o deployment de forma imperativa
        - kubectl scale deployment/<nome do deployment> --replicas=<Numero de replicas>
      
      + Atualizando a imagem utilizada no deployment:
        - kubectl set image deployment/<nome do deployment> <nome do container atual>=<nome da nova imagem>

        - Rollback um update de imagem
         - kubectl rollout undo deployment<nome do deployment>
           - Esse comando desfaz o ultimo deployment

        - Checando o histórico de rollouts de um deployment
          - kubectl rollout history deployment/<nome do deployment>
          - kubectl rollout history deployment/<nome do deployment> --to-revision=<numero de revisao>

   - Services: Objetos que agrupa os pods com endereços de IPs compatilhados, eles permitem acesso externo aos pods (que por default é apenas internal only)
      + Expondo pods de forma imperativa:
        - kubectl expose deployment <nome do deployment> --type=<tipo do servico> --port=<porta que o container escuta>

        - No caso de estiver usando minikube, o comando:
            minikube service <nome do servico>
        retorna uma url no qual se faz possível o acesso ao serviço em questão