# EC2-na-Pratica.Do-Erro-a-Solucao.
Laboratório da trilha Fundamentos da Computação em Nuvem — AWS Skill Builder


<p align="center">
  <img src="eliana_diniz_cloud_computing.png" width="600" alt="Eliana Diniz - Cloud Computing">
</p>

## 1️⃣ O problema.

Precisa assumir o controle de um ambiente em nuvem, validar o funcionamento de servidores e redimensionar a capacidade de processamento de uma instância para garantir que ela suportasse os requisitos exigidos pelo projeto. O laboratório me colocou no console da AWS para gerenciar uma instância EC2. 

A missão era: 
Encontrar a instância que já estava rodando. 
Parar ela para poder mudar o tipo. Trocar de t3.micro para m4.large
Colocar pra rodar de novo
Validar no Skill Builder

Parece simples, né? Mas teve um detalhe que me segurou um tempinho, quando fui parar a instância.

* **O Ciclo de Vida Inicial:** Encontrei a instância padrão em execução (modelo `t3.micro`) e analisei o seu status.
  O Perrengue com a Trava de Segurança (`disableApiStop`).
  Quando tentei parar a instância para conseguir alterar o seu tipo de capacidade, o console me barrou com uma mensagem de bloqueio:
  > *"The instance may not be stopped. Modify its 'disableApiStop' instance attribute and try again."*

Tradução livre: "Você não pode parar essa máquina. Vai lá e desativa essa trava de segurança primeiro."
No começo fiquei meio perdida — nunca tinha visto esse atributo disableApiStop. Mas depois de procurar um pouco, entendi que é uma proteção da AWS para evitar que alguém pare uma máquina crítica sem querer.

### Resumo do problema: 
A instância EC2 tinha o atributo disableApiStop ativado, bloqueando qualquer tentativa de parada.

*O aprendizado real:* Esse obstáculo foi uma aula prática excelente sobre governança e proteção contra interrupções acidentais em ambientes de nuvem!
