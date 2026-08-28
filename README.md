# EC2 na Pratica. Do erro a Solucao.
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

### O aprendizado real:
Esse obstáculo foi uma aula prática excelente sobre governança e proteção contra interrupções acidentais em ambientes de nuvem!

## 2️⃣ Que medidas foram tomadas? Como foi Resolvido?

Depois de muito pensar, de analisar, resolvi investigar. Fui até as configurações avançadas da instância no console EC2 e encontrei a opção de proteção de interrupção (stop protection). A medida que tomei foi desativar essa proteção de forma controlada, já que o laboratório exigia que eu parasse a instância para redimensioná-la. 

* Para contornar a trava de segurança, naveguei até as configurações avançadas da instância e desativei a proteção de interrupção (*stop protection*).
* Com o caminho livre, consegui parar a máquina com segurança e alterei o seu tipo para uma capacidade maior de uso geral: o modelo **`m4.large`**.
* Reiniciei o servidor e aguardei o status mudar para **Executando** (*Running*).

Medidas tomadas: Desativei o atributo disableApiStop nas configurações avançadas da instância, redimensionei e reiniciei o servidor.


## 3️⃣ O que precisou ser feito?

Com a trava de segurança desativada, o caminho ficou livre. O que precisei fazer foi:
Parar a instância — com o disableApiStop desativado.
Alterar o tipo da instância — troquei de t3.micro para m4.large, que tem mais capacidade de processamento.
Iniciar a instância novamente — esperei o status mudar para Running.
Validar no Skill Builder — na etapa DIY (Do It Yourself), inseri o ID da instância para confirmar que tudo estava correto.

<p align="center">
  <img src="aws-simulearn-completed.png" width="600" alt="AWS SimuLearn Completed - You Did It">
</p>


## 4️⃣ A solução final

Depois de seguir todos os passos, inseri o ID da minha instância no formulário de validação do Skill Builder:

* Com a instância devidamente ajustada para o tipo `m4.large, 
* Fui até a última etapa (a seção *DIY - Do It Yourself*), 
* Inseri o ID exato da instância (**`i-05732bc48933151b2`**) no formulário de validação do Skill Builder e submeti a tarefa.

## O que levo disso

Esse laboratório me ensinou que na nuvem não é só sobre clicar nos botões certos. É sobre entender por que as coisas estão bloqueadas, como a AWS protege seus recursos e como agir com segurança dentro desse ecossistema. A trava disableApiStop não é um bug — é uma feature de governança. E saber lidar com isso faz toda diferença.


Sobre Eliana Diniz

Linkedin: www.linkedin.com/in/eliana-diniz
email: eliana.dinizsilva@gmail.com

