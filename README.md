# Smart Home System 🏠

Este é um projeto desenvolvido para a placa de desenvolvimento **BitDogLab**, baseada no microcontrolador **Raspberry Pi Pico W**.  
O objetivo é simular um sistema de automação residencial, permitindo o controle de diversos dispositivos como iluminação, trava, alarme, display e ar-condicionado simulado via **servidor** acessado remotamente por um navegador.

---

## 📌 Sobre o Projeto

O Smart Home System foi criado como **projeto prático** da **2ª fase da residência tecnológica EmbarcaTech**.  
O projeto integra diversos periféricos da BitDogLab e demonstra na prática o uso de GPIOs, I2C, ADC, PIO, Wi-Fi e comunicação por servidor para simular uma residência conectada e controlável remotamente.

Essa é a **versão 2.0** do projeto, que adiciona novas funcionalidades ao sistema.

---

## 🧠 Como funciona

O sistema opera continuamente, aguardando comandos recebidos por um cliente TCP (por exemplo, um navegador conectado à mesma rede). Comandos reconhecidos ativam ou desativam dispositivos da casa inteligente:

- **Controle de LEDs** (simulam luzes de cômodos);
- **Trava de porta** (Matriz de LEDs simula trancado/destrancado);
- **Alarme sonoro** (Buzzer), ativado quando há movimentação simulada via joystick;
- **Matriz de LEDs WS2812B** (feedback visual da fechadura eletrônica e outros status);
- **Display OLED** (feedback visual de informações do sistema, incluindo status de A/C);
- **Joystick** (simula um sensor de movimento para ativação do alarme);
- **Sistema de Refrigeração Simulado**: (simula um sistema de ar-condicionado controlado remotamente, com controle de temperatura.

### 🔄 Comandos disponíveis

A interface web envia comandos simples como:
- `LIGAR LUZ`
- `DESLIGAR LUZ`
- `TRAVAR PORTA`
- `DESTRAVAR PORTA`
- `ATIVAR ALARME`
- `DESATIVAR ALARME`
- `AUMENTAR TEMP` (ajusta a variável `simulated_temp` para cima)
- `DIMINUIR TEMP` (ajusta a variável `simulated_temp` para baixo)
- `LIGAR A/C` / `DESLIGAR A/C` (alterna o estado de `cooling_state`)

Esses comandos são interpretados por um **servidor TCP** rodando na placa e executam ações locais instantaneamente, inclusive atualizando a página web com os novos valores de temperatura.

---

## 📁 Utilização

Atendendo aos requisitos de organização da 2º fase da residência, o arquivo CMakeLists.txt está configurado para facilitar a importação do projeto no Visual Studio Code.  
Segue as instruções:

1. Na barra lateral, clique em **Raspberry Pi Pico Project** e depois em **Import Project**.

![image](https://github.com/user-attachments/assets/4b1ed8c7-6730-4bfe-ae1f-8a26017d1140)

2. Selecione o diretório do projeto e clique em **Import** (utilizando a versão **2.1.1** do Pico SDK).

![image](https://github.com/user-attachments/assets/be706372-b918-4ade-847e-12706af0cc99)

3. **IMPORTANTE**! Para o código funcionar é necessário trocar os parâmetros de SSID e SENHA do Wi-Fi (Linha 25 e 26 do smart_home.c) para os da sua rede local.

   
4. Agora, basta **compilar** e **rodar** o projeto, com a placa **BitDogLab** conectada.

---
