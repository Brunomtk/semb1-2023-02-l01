# QUESTIONARIO SISTEMAS EMBARCADOS - BRUNO MENDES DA SILVA 11921EAU016



## 1. Compilação Cruzada
A compilação cruzada, ou **cross-compiling**, refere-se ao processo de compilar o código-fonte em um sistema de desenvolvimento diferente daquele em que será executado. Isso é útil quando há discrepâncias na arquitetura de hardware ou no sistema operacional entre os ambientes de compilação e execução. O objetivo principal é possibilitar o desenvolvimento de software para plataformas incompatíveis com o sistema de desenvolvimento original. Essa prática é especialmente benéfica em sistemas embarcados, onde os recursos podem ser limitados.

## 2. Código de Inicialização ou Startup
O código de inicialização, também conhecido como código de boot, consiste em um conjunto de instruções que executa imediatamente após a inicialização de um sistema embarcado. Sua função principal é configurar o ambiente necessário para carregar e executar outras partes do software. Isso inclui a inicialização e configuração do hardware, definição de pilha e heap, configuração do ambiente de execução e carregamento do código principal. Garante uma inicialização ordenada e prepara o sistema para a execução efetiva do software.

## 3. Utilitário Make e Makefile
### a) Makefile
O **Makefile** é uma ferramenta de automação de compilação que coordena componentes de software para criar executáveis finais ou artefatos de construção. Simplifica e automatiza o processo de compilação, gerenciando dependências entre os arquivos-fonte.

### b) Processo do Make
O processo do **make** envolve leitura do Makefile, análise de dependências, execução dos comandos de compilação, vinculação dos objetos compilados e conclusão da compilação. A sintaxe para criar um novo target envolve especificar o nome do alvo, suas dependências e os comandos associados.

### c) Sintaxe para Novo Target
A sintaxe para criar um novo target é especificar `nome_do_alvo: dependências comandos`.

### d) Dependências
As dependências são listadas para que o **make** determine se o alvo precisa ser reconstruído com base na data de modificação das dependências em relação ao próprio alvo. Isso garante uma compilação eficiente e consistente.

### e) Regras do Makefile
Em um **Makefile**, as regras explícitas têm comandos diretos, enquanto as implícitas são padrões integrados ao **make** para compilar tipos específicos de arquivos.

## 4. Arquitetura ARM Cortex-M
### a) Conjunto de Instruções Thumb
O conjunto de instruções **Thumb** é uma extensão otimizada da arquitetura ARM, oferecendo instruções mais condensadas para economizar espaço de memória. A arquitetura ARM Cortex-M é compatível com Thumb e ARM, permitindo escolher a opção adequada.

### b) Diferenças entre Load/Store e Register/Register
As arquiteturas Load/Store e Register/Register diferem na interação com a memória. Load/Store usa instruções específicas para acesso à memória, enquanto Register/Register permite operações diretas entre registradores, sem acesso à memória.

### c) Níveis de Acesso e Modos de Operação
Os processadores ARM Cortex-M têm dois níveis de acesso (Thread Mode e Handler Mode) e modos de operação (User Mode e modos privilegiados) para facilitar o desenvolvimento de sistemas RTOS mais robustos.

### d) Tratamento de Exceções e Interrupções
O tratamento de exceções e interrupções envolve diversos tipos de exceções e uma tabela de vetores para mapear endereços de tratadores. O NVIC prioriza exceções e utiliza group priority e sub-priority para determinar a sequência de atendimento.

### e) Diferença entre Registradores CPSR e SPSR
O CPSR mantém o estado atual do processador, enquanto o SPSR temporariamente armazena o estado durante exceções. Esses registros são cruciais para uma transição suave entre o código principal e o tratamento de exceções.

### f) Finalidade do Link Register (LR)
O LR preserva o endereço de retorno durante chamadas de sub-rotina, facilitando a continuidade do fluxo de execução após a conclusão da sub-rotina.

### g) Finalidade do Program Status Register (PSR)
O PSR armazena informações sobre o estado do processador, como flags de condição, modo de operação e controle de interrupções.

### h) Tabela de Vetores de Interrupção
A tabela de vetores de interrupção mapeia endereços para tratadores de interrupção, permitindo direcionar corretamente as interrupções para o código apropriado.

### i) Nested Vectored Interrupt Controller (NVIC)
O NVIC é essencial para sistemas de tempo real, proporcionando aninhamento de interrupções para uma resposta rápida a eventos críticos.

### j) Retorno de Interrupção
Durante uma interrupção, o valor EXC_RETURN no LR contém informações para um retorno adequado. A instrução BX LR interpreta esse valor para executar ações como ajuste de pilha e mudança de modo de execução.

### k) Salvamento de Contexto e Lazy Stacking
A diferença no salvamento de contexto entre Cortex-M3 e Cortex-M4F está no suporte a ponto flutuante. O Cortex-M4F salva e restaura registradores de ponto flutuante, aumentando o tempo de resposta e o uso da pilha. O "lazy stacking" adia o salvamento dos registradores até ser necessário, otimizando o desempenho.


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
