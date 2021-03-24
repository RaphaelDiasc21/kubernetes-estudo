   - Services: Objetos que agrupa os pods com endereços de IPs compatilhados, eles permitem acesso externo aos pods (que por default é apenas internal only)
      + Expondo pods de forma imperativa:
        - kubectl expose deployment <nome do deployment> --type=<tipo do servico> --port=<porta que o container escuta>

        - No caso de estiver usando minikube, o comando:
            minikube service <nome do servico>
        retorna uma url no qual se faz possível o acesso ao serviço em questão