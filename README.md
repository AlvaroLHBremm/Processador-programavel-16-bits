
# Processador programavel 16 bits - (imcompleto/Em desenvolvimento)

[![Protocolo](https://img.shields.io/badge/linguagem-Assembly-green.svg)](https://www.iso.org/standard/63648.html)
[![Controlador](https://img.shields.io/badge/Arquitetura-software_e_hardware-orange.svg)](#)
[![Controlador](https://img.shields.io/badge/Simulador-Deeds-purple.svg)](#)


## 1	Descrição do projeto

O `Processador programavel de 16 bits` é a continuação do projeto processador programavel de 8 bits, avançando tópicos de arquitetura de processador e de software

## 2	Objetivo do projeto

O objetivo deste projeto é Criar uma arquitetura capáz de executar diversas instruções complexas presentes nos computadores atuais, afim der posibilitar a criação de códigos dinamicos, como um sistema operacional basico, miniaturizado. Alocação dinamica de memória, chamada de subrotina, recursividade de função

### Objetivos:
* Alocação dinamica de memória.
* Chamada de subrotina com retorno e recursividade por software.

Com esses dois objetivos integrados será possivel criar códigos mais complexos, como simular um disk operating system (DOS) para gerenciar arquivos e programas. Contudo, não será possivel salvar qualquer arquivo na ROM pois devido a limitação do Deeds, não há um bloco de armazenamento de memória. 

## Estrutura

Abaixo está uma comparação entre as arquiteturas do processador de 16 bits (Dentro do bloco azul) e o processador de 8 bits (Dentro do bloco vermelho). 

Atualmente o processador de 16 bits ainda está em desenvolvimento, e portanto, diversas estruturas cruciais estão faltando incluindo o roteamento dos barramentos. 


o que está contido dentro de seu bloco são estruturas desenvolvidas especificamente pare este projeto, como: Decodificador de instrução, display 64x64, modulo de memória RAM e ROM e ULA com banco de registradores. 

<p align="center"> <img src="figs/CPU_view.png" alt="diagrama" width="100%"></p>
<p align="center"><b>Arquitetura</b></p>
<br><br>

## 3	Conjunto de instruções

### Instruções de alocação de memória
| Mnemônico | Código | Nome | Descrição |
| :---: | :---: | :---: | :--- |
| `LDR` | 0x10 | Load register | Carrega valor da memória para o banco de registradores. |
| `LDI` | 0x20 | Load immediate | Carrega valor constante da memória imediatamente para o um de registradores. |
| `MOV` | 0x30 | Move | Move o valor de um registrador para outro. |
| `STR` | 0x40 | Store register | Salva o valor de um registrador para um endereço de memória. |
| `STI` | 0x50 | Store immediate | Armazena valor do registrador imediatamente para o endereço atual. |

### Instruções aritméticas
| Mnemônico | Código | Nome | Descrição |
| :---: | :---: | :--- |
| `ADD` | 0x61 | Addition |  Soma o valor de dois registradores e salva em um registrador. |
| `SUB` | 0x62 | Subtraction | Subtrai o valor de dois registradores e salva em um registrador. |
| `MUL` | 0x63 | Multiplication | multiplica o valor de dois registradores e salva em um registrador. |
| `AND` | 0x64 | AND | Operação booleana AND entre o valor de dois registradores e salva em um registrador. |
| `OR`  | 0x65 | OR | Operação booleana OR entre o valor de dois registradores e salva em um registrador. |
| `SHR` | 0x66 | Shift right | Desloca o valor de um registrador, dividindo-o por 2. |
| `SHL` | 0x67 | Shift left | Desloca o valor de um registrador, multiplicando-o por 2. |
| `INC` | 0x68 | Increment | Incrementa o valor de um registrador por 1. |
| `DEC` | 0x69 | Decrement | Decrementa o valor de um registrador por 1. |

### Instruções de pulos de memória
| Mnemonico | código | Descrição |
| :---: | :---: | :--- |
| `JMP` | 0x70 | Realiza um "pulo" sem condição para o endereço especificado. |
| `JZ`  | 0x71 | Realiza um "pulo" com condição; registrador especificado igual a 0, para o endereço especificado. |
| `JN`  | 0x72 | Realiza um "pulo" com condição; registrador especificado negativo, para o endereço especificado. |
| `JOF` | 0x73 | Realiza um "pulo" com condição; Flag de overflow ligada, para o endereço especificado. |
| `JEQ` | 0x74 | Realiza um "pulo" com condição; registrador A `igual` a registrador B, para o endereço especificado. |
| `JLT` | 0x75 | Realiza um "pulo" com condição; registrador A `maior` que registrador B, para o endereço especificado. |
| `JST` | 0x76 | Realiza um "pulo" com condição; registrador A `menor` que registrador B, para o endereço especificado. |
| `SBR` | 0x77 | Salva o endereço atual em um registrador e realiza um "pulo" sem condição para o endereço da sub-rotina especificado. |


### Instruções de periféricos
| Mnemonico | código | Descrição |
| :---: | :---: | :--- |
| `INP` | 0xB0 | Carrega o valor do registrador de input para o banco de registrador. |
| `OUT` | 0xC0 | Salva um valor da memória no display matriz. |
| `RDM` | 0xD0 | Carrega o valor do contador interno para o banco de registrador. |
| `HLT` | 0xE0 | Para o clock do processador. |




