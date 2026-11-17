# 🚗 Estacionamento Inteligente (Arduino + Python)

Sistema de automação e monitoramento de estacionamento em tempo real que integra hardware baseado em **Arduino** com uma interface gráfica desktop desenvolvida em **Python (Tkinter)** por meio de comunicação serial.

## 📋 Funcionalidades

- **Monitoramento em Tempo Real:** Interface gráfica exibe a quantidade de vagas disponíveis, vagas ocupadas, capacidade máxima e o status individual de cada vaga (`LIVRE` ou `OCUPADA`).
- **Controle Automatizado de Cancela:** Acionamento automático de servo motor para abertura (`ABERTA`) quando há vagas disponíveis e bloqueio (`FECHADA`) quando o estacionamento atinge a lotação máxima.
- **Sinalização Visual por LEDs:** Atualização instantânea dos LEDs indicadores de cada vaga (verde para livre, vermelho para ocupada) sincronizada com a interface.
- **Gestão de Fluxo (Entrada e Saída):** Detecção de veículos por sensores ultrassônicos, com alocação de vagas livres e controle de saída baseado em fila (FIFO).
- **Indicador de Conexão Serial:** Feedback visual contínuo do estado de comunicação entre o computador e a placa Arduino.

## 🛠️ Hardware Utilizado

- 1x Placa Arduino (Uno / Mega)
- 1x Protoboard
- 2x Sensores Ultrassônicos HC-SR04 (sensor de entrada e sensor de saída)
- 1x Micro Servo Motor SG90 (atuador da cancela)
- LEDs indicadores (verdes e vermelhos) e resistores
- Cabos jumper e cabo USB para comunicação serial

## 💻 Tecnologias e Bibliotecas

- **Python 3**
- **Tkinter** (interface gráfica nativa)
- **PySerial** (`serial` — comunicação UART com o Arduino)
- **Collections (`deque`)** (controle da ordem de saída dos veículos)

## 🔌 Protocolo de Comunicação Serial

A comunicação ocorre a **9600 bps**:

- **Arduino ➔ Python:**
  - `ENTRADA` (ou `CARRO DETECTADO NA ENTRADA`): registra a entrada de um veículo e ocupa uma vaga disponível.
  - `SAIDA` (ou `CARRO DETECTADO NA SAIDA`): registra a saída de um veículo e libera a vaga correspondente.

- **Python ➔ Arduino:**
  - `VAGAS,<vaga1>,<vaga2>` (ex.: `VAGAS,1,0`): atualiza o estado dos LEDs de cada vaga (`0` = livre, `1` = ocupada).
  - `CANCELA,ABRIR`: aciona o servo motor para abrir a cancela.
  - `CANCELA,FECHAR`: aciona o servo motor para fechar a cancela quando não há vagas livres.

## 🚀 Como Executar

1. **Clone o repositório:**
   ```bash
   git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
   cd seu-repositorio
