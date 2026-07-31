
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
| Instrução | Descrição |
| :---: | :--- |
| `LDR` | Carrega valor da memória para o banco de registrador. |
| `MOV` | Move o valor de um registrador para outro. |
| `STR` | Salva o valor de um registrador para um endereço de memória. |
| `HlT` | Para o clock do processador. |

### Instruções aritméticas
| Instrução | Descrição |
| :---: | :--- |
| `ADD` | Soma o valor de dois registradores e salva em um registrador. |
| `SUB` | Subtrai o valor de dois registradores e salva em um registrador. |
| `AND` | Operação booleana AND entre o valor de dois registradores e salva em um registrador. |
| `MUL` | multiplica o valor de dois registradores e salva em um registrador. |
| `OR` | Operação booleana OR entre o valor de dois registradores e salva em um registrador. |
| `SHR` | Desloca o valor de um registrador para a direita, dividindo-o por 2. |
| `SHL` | Desloca o valor de um registrador para a esquerda, multiplicando-o por 2. |

### Instruções de 
| Instrução | Descrição |
| :---: | :--- |
| `JMP` | Realiza um "pulo" sem condição para o endereço especificado. |
| `JZ` | Realiza um "pulo" com condição; registrador especificado igual a 0, para o endereço especificado. |
| `JN` | Realiza um "pulo" com condição; registrador especificado negativo, para o endereço especificado. |
| `JOF` | Realiza um "pulo" com condição; Flag de overflow ligada, para o endereço especificado. |
| `JEQ` | Realiza um "pulo" com condição; registrador A `igual` a registrador B, para o endereço especificado. |
| `JBT` | Realiza um "pulo" com condição; registrador A `maior` que registrador B, para o endereço especificado. |
| `JST` | Realiza um "pulo" com condição; registrador A `menor` que registrador B, para o endereço especificado. |
| `SBR` | Salva o endereço atual na memória e realiza um "pulo" sem condição para o endereço da subrotina especificado. |


### Instruções de periféricos
| Instrução | Descrição |
| :---: | :--- |
| `INP` | Carrega o valor do registrador de input para o banco de registrador. |
| `OUT` | Salva um valor da memória na matriz de pixel. |
| `RDM` | Carrega o valor do contador interno para o banco de registrador. |




