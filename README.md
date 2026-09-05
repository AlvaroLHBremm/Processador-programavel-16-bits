
# Processador programavel 16 bits - (imcompleto/Em desenvolvimento)

[![Protocolo](https://img.shields.io/badge/linguagem-Assembly-green.svg)](https://www.iso.org/standard/63648.html)
[![Controlador](https://img.shields.io/badge/Arquitetura-software_e_hardware-orange.svg)](#)
[![Controlador](https://img.shields.io/badge/Simulador-Deeds-purple.svg)](#)


## 1	Descrição do projeto

O `Processador programavel de 16 bits` é a continuação do projeto processador programavel de 8 bits, avançando tópicos de arquitetura de processador e de software

O projeto foi inicialmente baseado em microprocessadores hipotéticos como o Neander e Ahmes, os quais foram utilizados como base para a construção do primeiro processador de 8 bits. A sua continuação, o processador de 16 bits, possui como base arquiteturas de componentes reais como o intel 8008. Deste modo, o projeto se assimilaria com os desafios de hardware e software presentes ao longo do desenvolvimento das tecnologias.

## 2	Objetivo do projeto

O objetivo deste projeto é Criar uma arquitetura capáz de executar diversas instruções complexas presentes nos computadores atuais, afim der posibilitar a criação de códigos dinamicos, como um sistema operacional basico, miniaturizado. Alocação dinamica de memória, chamada de subrotina, recursividade de função

### Objetivos:
* Instruction set de 16 bits para suportar  mais códigos.
* Alocação dinamica de memória.
* Chamada de subrotina com retorno e recursividade por software.
* Suporte para periféricos de entrada e saida

Com esses dois objetivos integrados será possivel criar códigos mais complexos, como simular um disk operating system (DOS) para gerenciar arquivos e programas. Contudo, não será possivel salvar qualquer arquivo na ROM pois devido a limitação do Deeds, não há um bloco de armazenamento de memória. 

## Estrutura geral

Abaixo está uma comparação entre as arquiteturas do processador de 16 bits (Dentro do bloco azul) e o processador de 8 bits (Dentro do bloco vermelho). 

Atualmente o processador de 16 bits ainda está em desenvolvimento, e portanto, diversas estruturas cruciais estão faltando incluindo o roteamento dos barramentos. 

## 3 Arquitetura e blocos computacionais 

### 3.1 - Memórias

O barramento de 16 bits permite endereçar 64Kb de memória, contudo nem Aamemória ROM nem a RAM possuem modulos de 64kb no simulador Deeds. Como o intuito deste projeto é criar códigos em assembly mais complexos e de realizar carregamentos entre a a ROM e a RAM...

Para atingir os 64kb foi utilizado a técnica de extensão de chip set ateravés do mapeamento de memória.

### 3.2 - Fluxo de dados

| Sigla | Nome | Descrição | 
| :--- | :--- | :--- |
| PL | Program Loader | Contador  |
| PC | Program Counter | Varre/busca por instruções nos endereços da memória RAM. |
| SP | Stack Pointer | Salva o ultimo endereço da pilha de memória. |
| LR | Link Register | Registrador de endereço de retorno de função para subrotinas `Leaf`, isto é, subrotinas que não possuem nenhuma subrotina ninhada dentro de seu código/escopo. Não existe na arquitetura mas pode ser acessado pelos registradores da ULA. |

### Unidade de lógica aritmética
| Registradores | Registradores|
| :--- | :--- |
| 8 registradores de 8 bits | `RAH, RAL`, `RBH, RBL`, `RCH , RCL`, `RDH, RDL` |
| 4 registradores de 16 bits | `RA`, `RB`, `RC`, `RD` |

O banco de registradores da ULA é composto por 8 registradores de 8 bits, os quais podem ser utilizados como registradores de 16 bits. 

A nomenclatura caracteriza a posição e utilidade do registrador. A letra `R` explica que é um registrador, a letra `A/B/C/D` é o agrupamento de registador de 16 bits e as letras `H/L` denotam sua posição, Com o byte MSB sendo descrito pela letra H de High e o byte lSB descrito pela letra L de Low.


o que está contido dentro de seu bloco são estruturas desenvolvidas especificamente pare este projeto, como: Decodificador de instrução, display 64x64, modulo de memória RAM e ROM e ULA com banco de registradores. 

<p align="center"> <img src="figs/CPU_view.png" alt="diagrama" width="100%"></p>
<p align="center"><b>Arquitetura</b></p>
<br><br>

## 3	  Arquitetura de conjunto de instruções - ISA

### 3.1 - Instruções de alocação de memória
| Mnemônico | Código | Nome | Descrição |
| :---: | :---: | :--- | :--- |
| `LDR` | 0x0R | Load register | Carrega valor da memória para o banco de registradores. |
| `LDI` | 0x1R | Load immediate | Carrega valor constante da memória imediatamente para o um de registradores. |
| `STR` | 0x2R | Store register | Salva o valor de um registrador para um endereço de memória. |
| `STI` | 0x3R | Store immediate | Armazena valor do registrador imediatamente para o endereço atual. |
| `LDM` | 0x40 | Load Multiple | Carrega 8 valores de memória em todos os registradors do banco de registradores |
| `STM` | 0x41 | Store Multiple | Armazena o valor de todos os 8 registradores em um endereço de memória |
| `MOV` | 0x42 | Move | Move o valor de um registrador para outro. |
| `LDM` | 0x43 | Load Memory | Carrega um bloco de memória da ROM para um endereço na RAM. |


O segundo nibble, caso for `R`, denota a parte reservada para denominar o registrador escolhido para realizar a instrução.

Se o valor do registrador escolhido estiver entre [0...7], a instrução lidará com endereços e registradores de 8 bits. Caso o valor esteja entre [A...F], a instrução lidará com endereços e registradores de 16 bits.

<!-- Should LDB and STB load an store imediately like LDI and STI ? -->

### 3.2 - Instruções aritméticas
| Mnemônico | Código | Nome | Descrição |
| :---: | :---: | :--- | :--- | 
| `ADD` | 0x44 | Addition |  Soma o valor de dois registradores. |
| `SUB` | 0x45 | Subtraction | Subtrai o valor de dois registradores. |
| `MUL` | 0x46 | Multiplication | multiplica o valor de dois registradores. |
| `AND` | 0x47 | AND | Operação booleana AND entre o valor de dois registradores. |
| `OR`  | 0x48 | OR | Operação booleana OR entre o valor de dois registradores. |
| `NOT` | 0x49 | NOT | Operação booleana NOT entre o valor de dois registradores. |
| `XOR` | 0x4A | XOR | Operação booleana XOR entre o valor de dois registradores. |
| `SHR` | 0x5R | Shift Right | Desloca o valor de um registrador, dividindo-o por 2. |
| `SHL` | 0x6R | Shift Left | Desloca o valor de um registrador, multiplicando-o por 2. |
| `INC` | 0x7R | Increment | Incrementa o valor de um registrador por 1. |
| `DEC` | 0x8R | Decrement | Decrementa o valor de um registrador por 1. |

O segundo byte da instrução reserva dois nibbles pare denominar os registradores os quais iram realizar a operação. O registrador escolhido do primeiro nibble irá funcionar como acumulador, armazenando o valor da operação em si mesmo, exemplo:| 0x61 | 0x12 | --> R1 = R1 + R2;

Seguindo a mesma lógica das instruções de alocação de memória, se os registradores selecionados pela instrução forem de 8 bits a instrução lidará com valores de 8 bits, e o mesmo para registradores de 16 bits.

### 3.3 - Instruções de pulos de memória
| Mnemônico | Código | Nome | Descrição |
| :---: | :---: | :--- | :--- |
| `JMP` | 0x9R | Jump | Realiza um "pulo" sem condição para o endereço especificado. |
| `JZ`  | 0xAR | Jump zero | Realiza um "pulo" com condição; registrador especificado igual a 0, para o endereço especificado. |
| `JN`  | 0xBR | Jump negative | Realiza um "pulo" com condição; registrador especificado negativo, para o endereço especificado. |
| `JOF` | 0xCR | Jump overflow | Realiza um "pulo" com condição; Flag de overflow ligada, para o endereço especificado. |
| `JEQ` | 0xD0 | Jump equivalent | Realiza um "pulo" com condição; registrador A `igual` a registrador B, para o endereço especificado. |
| `JLT` | 0xD1 | Jump larger than | Realiza um "pulo" com condição; registrador A `maior` que registrador B, para o endereço especificado. |
| `JST` | 0xD2 | Jump smaller than | Realiza um "pulo" com condição; registrador A `menor` que registrador B, para o endereço especificado. |
| `SBR` | 0xD3 | Subroutine | Salva o endereço atual em um registrador e realiza um "pulo" sem condição para o endereço da sub-rotina especificado. |
| `RET` | 0xD4 | Return | Retorna da subroutina para o ultimo endereço de onde foi chamado  |

<!-- Search where to do return instruction by software or by hardware. By software would probably be more dynamic and would allow for software recursion. -->


### 3.4 - Instruções de periféricos
| Mnemônico | Código | Nome |  Descrição |
| :---: | :---: | :--- | :---: | 
| `INP` | 0xE0 | Input | Carrega o valor do registrador de input para o banco de registrador. |
| `OUT` | 0xE1 | Output | Salva um valor da memória no display matriz. |
| `RDM` | 0xE2 | Random | Carrega o valor do contador interno para o banco de registrador. |
| `HLT` | 0xE3 | Halt | Para o clock do processador. |




