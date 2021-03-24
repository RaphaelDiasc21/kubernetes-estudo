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
        
      + Deletando objetos deployment
          - kubectl delete -f=<nome do arquivo de deployment>