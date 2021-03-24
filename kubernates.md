- O que é ?
    - Open source
    - Framework de orquestração de containers
    - Desenvolvido pelo google
    - Ajuda gerenciar aplicações containizadas, em diferentes ambientes (fisicos, cloud e etc)
    - Contém deploy automático
    - Fornece serviços de escalonamento e load balancing

- O que uma ferramenta dessas oferece
  - Alta disponobilidade
  - Escalabilidade ou alta performance
  - Backup e restauração


- Componentes do kubernates
  - Cluster: MConsiste em um conjunto de um ou mais servidores de processamento, chamados de nós, nos quais executam aplicações containerizadas
  - Master: Controla o que cada node faz
  - node: Servidor de processamento, no qual hospeda os Pods.
  - Ambiente de processamento: Gerencia os nś de processamento e os pods no cluster
  - Pod: Abstração sobre um container, menor unidade do kubernates, ou seja, são componentes de uma aplicação
            - Geralmente roda-se uma aplicação principal por pod
            - Cada pod tem um endereço de IP, no qual um pode se comunicar com outro
                - Porém quando o pod é reiniciado um novo ip é atribuido

- Service:
    - Endereço de IP permanente, no qual pode ser atachado em um pod
    - Ciclo de vida de um pod e um service não são atrelados, ou seja se um pod cai, o service permanece, mantendo o endereçamento

- External service
    - Serviços que abrem a comunicação para fontes externas

- Internal service
    - Serviços privados (banco de dados)



 - Ambientes de produção e dev
    - Desenvolvimento:
        - Minicuke: Usado para setar clusters na máquina de desenvolvimento

    - Produção:
       - Em ambientes de produção, se usa algo chamado: Manage solutions
       - Manage solutions, são solução gerenciadas por cloud providers, nas quais já configuram todos os clusters para o dev
          - EKS (Aws manage solution)
          - GKE (GCP manage solution)

    - Minikube: Usado para cria clusters localmente, ele gerencia o node na máquinba
    - Kubectl: Usado para gerenciar os containers no node (usado para local e produção)




  - Objects: Coisas que serão criadas dentro do cluster, cada um contendo seu propósito
     - StatefulSet
     - ReplicaController
     - Pod
     - Service
          
         
  - apiVersion - Versões de cada api, onde estão separados os tipos (Pod, Kind e etc)
  cada api define um conjunto de objetos que nós podemos utilizar


  - Pod
    - Agrupamento de containers que tem o mesmo propósito
    - Containers sempre são deployados em pod

      - Coordenadas de configuração
         apiVersion: v1
         kind: Pod
         metadata: ~ Metada são dados sobre o pod
          name: name of pod
          
        spec: ~ especificações técnicas do pod

 - Service:
    - Configurações de rede (networking) em um cluster

     - Tipos de services:
        - ClusterIP
        - NodePort - Expoe um container to the out side world (Only for development purpose)
        - LoadBalancer
        - Ingress

  - Label selector
     - Um objeto NodePort, faz reconhecimento dos pods que ele tem que acessar através da label que esse pod apresenta
         - no arquivo pod:
             labels:
               componenet: nome da label

         - selector:
            component: nome da label - Nesse caso o component também faz parte, sendo a label um key value pair


    - Portas mapeadas no arquivo do objeto nodePort
         - port: Porta que outros pods vão acessar para acessar o pod em questão
         - targetPort: Porta dentro do Pod que queremos expor ao mundo
         - nodePort: Porta que o mundo (browser) irá acessar para acessar o serviço em questão
           (numero entre 30000 - 32726) (development only)
  - Kubeproxy
     - Todo node tem um proxy que filtra as requests chegadas no node e direciona para o serviço correto, esse proxy tem o nome de kube-proxy