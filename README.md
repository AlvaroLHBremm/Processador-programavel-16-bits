
# Nexus - Website

[![Protocolo](https://img.shields.io/badge/linguagem-Assembly-green.svg)](https://www.iso.org/standard/63648.html)
[![Controlador](https://img.shields.io/badge/Arquitetura-software_e_hardware-orange.svg)](#)
[![Controlador](https://img.shields.io/badge/Simulador-Deeds-purple.svg)](#)


## 1	Descrição do projeto

O `Processador programavel de 16 bits` é a continuação do projeto de mesmo nome, avançando tópicos de arquitetura de processador,

## 2	Objetivo do projeto

Criar uma arquitetura capáz de executar diversas instruções complexas presentes nos computadores atuais, afim der posibilitar a criação de códigos dinamicos, como um sistema operacional basico, miniaturizado.



<p align="center"> <img src="figs/CPU_view.png" alt="diagrama" width="100%"></p>
<p align="center"><b>Arquitetura</b></p>
<br><br>


### Instruções de fluxo de memória
| Mnemonico | código | Descrição |
| :---: | :---: | :--- |
| `LDR` | 0x10 | Carrega valor da memória para o banco de registrador. |
| `MOV` | 0x10 | Move o valor de um registrador para outro. |
| `STR` | 0x10 | Salva o valor de um registrador para um endereço de memória. |
| `HlT` | 0x10 | Para o clock do processador. |

### Instruções aritméticas
| Mnemonico | código | Descrição |
| :---: | :---: | :--- |
| `ADD` | 0x10 | Soma o valor de dois registradores e salva em um registrador. |
| `SUB` | 0x10 | Subtrai o valor de dois registradores e salva em um registrador. |
| `AND` | 0x10 | Operação booleana AND entre o valor de dois registradores e salva em um registrador. |
| `MUL` | 0x10 | multiplica o valor de dois registradores e salva em um registrador. |
| `OR`  | 0x10 | Operação booleana OR entre o valor de dois registradores e salva em um registrador. |
| `SHR` | Desloca o valor de um registrador para a direita, dividindo-o por 2. |
| `SHL` | Desloca o valor de um registrador para a esquerda, multiplicando-o por 2. |

### Instruções de 
| Mnemonico | código | Descrição |
| :---: | :---: | :--- |
| `JMP` | 0x10 | Realiza um "pulo" sem condição para o endereço especificado. |
| `JZ` | 0x10 | Realiza um "pulo" com condição; registrador especificado igual a 0, para o endereço especificado. |
| `JN` | 0x10 | Realiza um "pulo" com condição; registrador especificado negativo, para o endereço especificado. |
| `JOF` | 0x10 | Realiza um "pulo" com condição; Flag de overflow ligada, para o endereço especificado. |
| `JEQ` | 0x10 | Realiza um "pulo" com condição; registrador A `igual` a registrador B, para o endereço especificado. |
| `JBT` | 0x10 | Realiza um "pulo" com condição; registrador A `maior` que registrador B, para o endereço especificado. |
| `JST` | 0x10 | Realiza um "pulo" com condição; registrador A `menor` que registrador B, para o endereço especificado. |
| `SBR` | 0x10 | Salva o endereço atual na memória e realiza um "pulo" sem condição para o endereço da subrotina especificado. |


### Instruções de periféricos
| Mnemonico | código | Descrição |
| :---: | :---: | :--- |
| `INP` | 0x10 | Carrega o valor do registrador de input para o banco de registrador. |
| `OUT` | 0x10 | Salva um valor da memória na matriz de pixel. |
| `RDM` | 0x10 | Carrega o valor do contador interno para o banco de registrador. |




