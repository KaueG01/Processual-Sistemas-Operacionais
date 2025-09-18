# Processual-Sistemas-Operacionais

Exercícios Teóricos – Processos

1 - Qual a diferença entre programa e processo?

Resposta: Um programa é um conjunto estático de instruções (como um arquivo executável), enquanto um processo é uma instância ativa e dinâmica de um programa em execução. Para facilitar o entendimento, um programa é como uma receita de bolo, e um processo é o ato de preparar o bolo seguindo essa receita. Vários processos podem ser criados a partir de um único programa.


2 - Quais são os estados de um processo e quando ocorrem as transições?

Resposta: Os estados de um processo em um sistema operacional, de acordo com um modelo comum, são: Novo (criação), Pronto (aguardando a CPU), Em Execução (sendo processado pela CPU), Bloqueado/Em Espera (aguardando um evento externo) e Encerrado/Terminado. As transições entre esses estados ocorrem quando o processo é selecionado pela CPU (do Pronto para Execução), solicita uma operação de E/S (de Execução para Bloqueado), ou um evento esperado é concluído (de Bloqueado para Pronto).


3 - O que contém um Process Control Block (PCB)?

Resposta: contém todas as informações necessárias para o sistema operacional gerenciar um processo, incluindo seu identificador único (PID), estado atual, registradores da CPU (como o contador de programa), uso de memória, prioridade e informações de agendamento, além de ponteiros para arquivos abertos e dispositivos de E/S.


4 - O que acontece com os recursos de um processo quando ele termina?

Resposta: Quando um processo termina no computador, o sistema operativo recupera todos os recursos que estavam a ser utilizados por ele, como memória RAM, acesso ao disco e threads, libertando-os para que possam ser usados por outros processos. Este processo de terminação é acionado pelo sistema operativo, que sinaliza ao programa para que ele encerre as suas atividades, garantindo que não fiquem "resíduos" de processos que poderiam causar instabilidade no sistema. 

5 - Qual a diferença entre fork() e exec() no UNIX?

Resposta: No sistema UNIX, fork() duplica o processo atual, criando um processo filho idêntico que continua a executar o mesmo código, enquanto exec() substitui a imagem do processo atual por um novo programa a partir de um ficheiro executável, essencialmente "sobrescrevendo" o código original para que o processo execute um programa completamente diferente. A combinação fork() seguida por exec() é o método padrão para iniciar novos programas, onde o filho criado pelo fork() é então modificado pelo exec() para carregar e executar o novo programa

6 - Como funciona a rotina de processos em UNIX?

Resposta: No UNIX, um processo é a instância em execução de um programa, gerida pelo sistema operativo através de identificadores únicos (PID e PPID) e de um estado (pronto, a correr, em espera). A criação de novos processos ocorre geralmente através do comando fork(), que duplica o processo existente criando um processo pai e um processo filho. Os processos comunicam-se e interagem com o hardware do sistema através de chamadas ao sistema (system calls), utilizando um modelo de comunicação baseado em pipes e descritores de ficheiro. 

7 - Compare memória compartilhada e troca de mensagens (IPC).

Resposta: A memória compartilhada permite que processos acessem e modifiquem diretamente a mesma região de memória, oferecendo alta velocidade e eficiência para grandes quantidades de dados, mas exigindo sincronização cuidadosa para evitar corrupção. A troca de mensagens (passagem de mensagens), por outro lado, envolve a cópia de dados entre os espaços de endereço dos processos por meio de mensagens, sendo mais flexível, com o sistema operacional gerenciando a entrega de dados, mas introduzindo maior latência e sobrecarga devido às cópias e ao processamento. 

8 - Cite exemplos de chamadas de sistema usadas no IPC.

Resposta: Existem vários exemplos de chamadas de sistema usadas em Comunicação Inter-Processos (IPC), como as usadas para criar pipes (pipe()), para criar processos (fork(), exec()), e para gerir memória compartilhada (mmap()), as quais são essenciais para a comunicação entre diferentes processos no sistema operacional. 

9 - Por que é importante que o sistema operacional faça o gerenciamento de processos?

Resposta: O gerenciamento de processos pelo sistema operacional é vital porque garante a execução eficiente e ordenada de múltiplos programas, alocando os recursos do hardware de forma justa e controlada entre eles. Isso assegura que programas não interfiram uns nos outros, que haja uma comunicação segura entre eles, que o sistema não trave (deadlock) e que todo o sistema opere de maneira estável e confiável, otimizando o desempenho geral do computador. 

10 - Explique a diferença entre processos independentes e processos cooperativos.

Resposta: A principal diferença é que processos independentes não afetam nem são afetados por outros processos e não compartilham dados, enquanto processos cooperativos podem afetar e ser afetados por outros processos e compartilham informações e recursos. Essa distinção afeta a forma como os processos interagem e a necessidade de mecanismos de comunicação entre eles. 

11 - O que é um processo zumbi em UNIX/Linux?

Resposta: Um processo zumbi no UNIX/Linux é um processo que já terminou a sua execução, mas que ainda mantém uma entrada na tabela de processos do sistema. Esta entrada é necessária para que o processo pai possa ler o status de saída e outras informações do processo filho, utilizando para isso a chamada de sistema wait(). Se o processo pai não executar esta chamada, o processo filho torna-se "morto" mas "vivo" na tabela de processos, ocupando um pequeno espaço de memória, mas sem consumir recursos de CPU. 

12 - Explique a diferença entre chamadas bloqueantes e não bloqueadoras em IPC.

Resposta: Em Comunicação entre Processos (IPC), uma chamada bloqueante faz com que o processo que a realiza espere que a operação seja concluída antes de prosseguir, enquanto uma chamada não bloqueante permite que o processo continue a executar outras tarefas sem esperar pelo resultado da operação de IPC. O modelo bloqueante sincroniza as operações e pode causar ineficiência, já que um processo fica inativo, enquanto o não bloqueante permite a execução simultânea, aumentando a responsividade e escalabilidade da aplicação. 

13 - Qual a diferença entre processo pesado (processo) e thread (processo leve)?

Resposta: A principal diferença é que um processo (pesado) é um programa em execução com seu próprio espaço de memória isolado, enquanto uma thread (leve) é uma unidade de execução menor que opera dentro de um processo e compartilha seu espaço de memória e recursos com outras threads do mesmo processo. Isso torna a comunicação e a troca de contexto entre threads mais rápidas e eficientes que entre processos, mas os processos oferecem maior isolamento e estabilidade para tarefas distintas. 

14 - Por que sistemas operacionais multiprogramados precisam de troca de contexto (context switch)?

Resposta: A troca de contexto é necessária porque: Ele permite que vários programas sejam executados em uma única CPU, criando a ilusão de multitarefa. Ele ajuda a gerenciar recursos de forma eficiente, garantindo que a CPU não fique ociosa enquanto aguarda operações lentas (como leitura de disco).

15 - Cite vantagens e vantagens da comunicação via memória compartilhada.

Resposta: A comunicação via memória compartilhada oferece a vantagem da alta velocidade e eficiência de transferência de dados, sem a necessidade de cópias, mas apresenta as desvantagens da complexidade no gerenciamento de acesso e sincronização, que pode levar a erros e condições de corrida, e o risco de vulnerabilidades de segurança que permitem o acesso não autorizado a dados sensíveis. 
