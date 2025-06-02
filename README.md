# Global Solution 2025.1 - Edge Computing

# Projeto: Simulador de Alerta de Enchentes para Estações de Metrô 

Durante chuvas fortes, é comum que estações de metrô e trem enfrentem alagamentos. Isso pode colocar em risco a segurança dos passageiros, além de causar atrasos e danos na estrutura das estações. O projeto propõe um sistema de detecção de enchentes com ESP32 e sensor ultrassônico, que monitora o nível de água em tempo real. As informações são enviadas via MQTT (Mosquitto) para um dashboard no Node-RED, que exibe alertas visuais sobre o risco de alagamento. Dessa forma, é possível agir rapidamente para evitar problemas maiores e garantir a segurança dos passageiros.

---

## 🧱 Arquitetura da Solução

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

---

## ⚙️ Componentes Utilizados

- **ESP32** (microcontrolador com Wi-Fi)
- **Sensor Ultrassônico HC-SR04**
- **Broker MQTT (Mosquitto)**
- **Node-RED com Dashboard**
- **Simulador Wokwi** 

---

## 📐 Lógica de Funcionamento

O sensor mede a distância entre ele e a superfície da água. Quanto menor a distância, maior o nível da água. A lógica usada é:

| Distância (cm)      | Alerta           |
|---------------------|------------------|
| > 50 cm             | 🟢 Nível normal   |
| 30 – 50 cm          | 🟡 Atenção        |
| < 30 cm             | 🔴 Risco de enchente |

---

## 🖥️ Fluxo de Dados

1. O ESP32 mede a distância da água e envia o status via MQTT.
2. O broker Mosquitto recebe e encaminha essa mensagem.
3. O Node-RED processa o dado e atualiza o painel com o alerta correspondente.

---

## 🧪 Testes

Durante a simulação no Wokwi:
- A distância pode ser ajustada manualmente para testar os três níveis de alerta.
- O status enviado aparece no painel do Node-RED com o emoji correspondente.
- Foi possível testar com diferentes distâncias e verificar mudanças em tempo real.

