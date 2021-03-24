 # Arquitetura e componentes do Kuberbetes
 
 - Principios para um design do Kubernetes
    - Segurança: Seguir as práticas de segurança
    - Fácil de usar: Poucos comandos para operar
    - Extensível: ele não deve favorecer um fornecedor e precisa ser personalizável por meio de um arquivo de configuração.


 - Componentes de um cluster Kubernetes
    - A implantação do kubernetes é chamada de cluster
         - Cluster: 
             - Definição de cluster: Conjunto de computadores que trabalham juntos proporcionando melhor desempenho de trabalho
             - Divide-se em duas partes:
                - Plano de controle e as máquinas de computação (nós)

                - Plano de controle:
                Tem a função de controlar o cluster através de seus componentes internos, esses componentes garantem que a quantidade de container exigida seja executada com os recursos necessários

                - Componentes do Plano de controle (master node):
                  - master node: Gerencia os pods através dos worker nodes
                  - Kube-apiserver: API que fornece a interação com o cluster, processando as solicitações através da linha de comando kubectl e outras ferramentas
                  - kube-scheduler: Responsável por análisar os recursos que um pod necessita e programa o mesmo para ser erguido no node apropriado
                  - etcd: Banco de dados de chave e valor que armazena informações sobre o estado atual do cluster
                  - kube-controller-manager: Assiste e controle os worker nodes, corrigo o número de pods rodando e etc

                - Componentes do nó
                  + Os nós são máquinas físicas ou virtuais nas quais executam os objetos kubernetes, são conhecidas também com 'worker nodes', nas quais são controlados pela master node (CONTROL PLANE)

                  - Pods: Unidade que representa a instância de uma aplicação, formada por um ou mais containers com forte acoplamento entre eles.
                  
                  + Mecanismo de execução dos containers
                   - Kubelet: Aplicação contidade dentro do node que faz a comunicação com o plano de controle do kubernetes, assegurando que os pods são executados. Quando o plano de controle precisa que algo aconteça no node, o kubelet faz a determinada ação
                   - kube-proxy: Proxy que facilita os serviços de rede do kubernetes. é ele que faz o gerenciamento das comunições de rede debtri e fora do cluster. Filtrando e encaminhando requisições




        ## Fluxo de comunicação entre os comunicações
        ![fluxo de arquitetura](https://d33wubrfki0l68.cloudfront.net/d35c2b375b43b4fa374ae834f95224975418e33f/6b47b/images/blog/2018-06-05-11-ways-not-to-get-hacked/kubernetes-control-plane.png)