 1. Instrução enviada pelo kubectl para o nó mestre
 2. No nó mestre o scheduler vai analizar os pod rodando atualmente e achará o melhor node para que se rode o novo pod]
 3. Agora o fluxo para para o worker node encontrado pelo scheduler, comunicando através do kubelet.
 4. O kubelete vai gerenciar a criação ou a operação que irá ser realizada