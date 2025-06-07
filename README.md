# Global Solution 2025.1 - Edge Computing
#### Ana Luiza Santana da Rocha - RM 561194 - Turma 1ESPA

# Projeto: Simulador de Alerta de Enchentes para Estações de Metrô 

Durante chuvas fortes, é comum que estações de metrô e trem enfrentem alagamentos. Isso pode colocar em risco a segurança dos passageiros, além de causar atrasos e danos na estrutura das estações. O projeto propõe um sistema de detecção de enchentes com ESP32 e sensor ultrassônico, que monitora o nível de água em tempo real. As informações são enviadas via MQTT (Mosquitto) para um dashboard no Node-RED, que exibe alertas visuais sobre o risco de alagamento. Dessa forma, é possível agir rapidamente para evitar problemas maiores e garantir a segurança dos passageiros.

<br>

## Arquitetura da Solução

A arquitetura do sistema está dividida em três camadas principais:

### 1. 📶 Camada IoT
- **Dispositivo:** ESP32
- **Sensor:** Ultrassônico (HC-SR04)
- **Função:** Realiza a medição da altura da água (distância do sensor até o solo/nível da água)

### 2. 🔄 Camada Back-End
- **Broker MQTT:** Mosquitto (local ou online)
- **Função:** Intermedia a comunicação entre o ESP32 e o dashboard, transmitindo os dados capturados.

### 3. 📊 Camada de Aplicação
- **Plataforma:** Node-RED
- **Dashboard:** Interface web que recebe os dados, interpreta e exibe alertas visuais com emojis e mensagens.

<br>

## Componentes Utilizados

- **ESP32** (microcontrolador com Wi-Fi)
- **Sensor Ultrassônico HC-SR04**
- **Broker MQTT (Mosquitto)**
- **Node-RED com Dashboard**
- **Simulador Wokwi** 

<br>

## Funcionamento

1. O ESP32 mede a distância da água e envia o status via MQTT.
2. O broker Mosquitto recebe e encaminha essa mensagem.
3. O Node-RED processa o dado e atualiza o painel com o alerta correspondente.
   
O sensor mede a distância entre ele e a superfície da água. Quanto menor a distância, maior o nível da água. A lógica usada é:

| Distância (cm)      | Alerta           |
|---------------------|------------------|
| > 50 cm             | 🟢 Nível normal   |
| 30 – 50 cm          | 🟡 Atenção        |
| < 30 cm             | 🔴 Risco de enchente |

<br>

## 🚀 Como Executar o Projeto

### 1. 🔧 Requisitos

- Node.js instalado
- Node-RED instalado
- Mosquitto (Broker MQTT) instalado
- Wokwi

---

### 2. 💻 Instalar Node-RED

No terminal:

```bash
npm install -g --unsafe-perm node-red
```

Iniciar com:

```bash
node-red
```

Acesse: [http://localhost:1880](http://localhost:1880)

---

### 3. 📡 Instalar e Executar o Mosquitto



```bash
choco install mosquitto
```

Inicie o broker:

```bash
mosquitto
```

---

### 4. 🧩 Importar o Fluxo do Node-RED

1. Acesse `http://localhost:1880`
2. Menu (☰) > Import
3. Cole o conteúdo de `flows.json` que está no repositório
4. Clique em **Deploy**


### 5. 📊 Rodar Wokwi e acompanhar no Dashboard
Após executar no Wokwi, acesse:

```
http://localhost:1880/ui
```


