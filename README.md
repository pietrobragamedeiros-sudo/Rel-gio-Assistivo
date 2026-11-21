# ⌚ Relógio Assistivo (Comunica+) — TCC

Sistema vestível de **Comunicação Aumentativa e Alternativa (CAA)** de baixo custo, desenvolvido como Trabalho de Conclusão de Curso (TCC). O projeto auxilia pessoas com **Transtorno do Espectro Autista (TEA)** ou com limitações na fala funcional a comunicarem necessidades básicas e pedidos de ajuda em tempo real para seus pais, responsáveis ou cuidadores.

---

## 🎯 Como Funciona

O sistema funciona de maneira 100% autônoma, sem depender de internet externa ou servidores pagos:

1. **Rede Própria (Access Point):** Ao ligar, o relógio (**ESP32-S3**) cria sua própria rede Wi-Fi local (`Relogio-TCC`) e hospeda internamente o site do responsável.
2. **Pareamento por Código:** A tela circular do relógio exibe um código numérico aleatório de 4 dígitos.
3. **Conexão via IP:** O responsável conecta o celular ou computador no Wi-Fi do relógio, acessa o endereço IP `http://192.168.4.1` no navegador e digita o código exibido no visor.
4. **Menu de Necessidades:** Assim que conectado, a tela do relógio libera automaticamente os botões coloridos de acesso rápido (**Água**, **Comer**, **Banheiro** e **Ajuda**).
5. **Alertas em Tempo Real:** Quando o usuário solicita algo no relógio, o painel web do responsável emite imediatamente um alerta visual e sonoro, registrando o chamado no histórico de atendimento.

---

## 🛠️ Tecnologias e Hardware Utilizados

* **Placa Integrada:** Waveshare ESP32-S3-Touch-LCD-1.28
* **Microcontrolador:** ESP32-S3 (Dual-Core Xtensa LX7 240 MHz, Wi-Fi 2.4 GHz integrado)
* **Display:** LCD TFT IPS Circular de 1,28" (Controlador **GC9A01** via SPI, resolução 240×240 px)
* **Touchscreen:** Sensor capacitivo **CST816S** (via I²C)
* **Firmware (C/C++):** Desenvolvido na Arduino IDE utilizando `Arduino_GFX_Library` (v1.4.6), `WiFi.h` e `ESPAsyncWebServer`
* **Painel Web (Front-end Embarcado):** HTML5, CSS3 e JavaScript puro (armazenados na memória Flash via `PROGMEM`, com alertas sonoros via *Web Audio API*)

---

## 📌 Mapeamento de Pinos (ESP32-S3-Touch-LCD-1.28)

| Periférico | Sinal | GPIO | Função |
| :--- | :--- | :---: | :--- |
| Display GC9A01 | SCLK / MOSI | 10 / 11 | Clock e Dados SPI |
| Display GC9A01 | CS / DC | 9 / 8 | Chip Select e Data/Command |
| Display GC9A01 | RST / BL | 14 / 2 | Reset e Luz de Fundo (Backlight) |
| Touch CST816S | SDA / SCL | 6 / 7 | Barramento I²C do Touch |
| Touch CST816S | INT / RST | 5 / 13 | Interrupção e Reset do Touch |
| Bateria | VBAT_SENS | 1 | Leitura de tensão (ADC) |

---

## 🚀 Como Executar o Projeto

1. Baixe o código-fonte deste repositório (ou acesse o backup no [Google Drive](COLE_AQUI_O_LINK_DO_SEU_DRIVE)).
2. No **Arduino IDE**, instale o pacote da placa **ESP32** (versão 2.0.17) e as bibliotecas:
   * `GFX Library for Arduino` (versão **1.4.6**)
   * `ESPAsyncWebServer` e `AsyncTCP`
3. Selecione a placa **ESP32S3 Dev Module** e carregue o código (`.ino`) no dispositivo.
4. Ligue o relógio, conecte-se à rede Wi-Fi **`Relogio-TCC`** pelo celular ou computador e acesse **`http://192.168.4.1`** no navegador.
5. Digite o código exibido no visor do relógio para iniciar o monitoramento.

---

## 👨‍💻 Autor

Desenvolvido por **Pietro Braga Medeiros** como Trabalho de Conclusão de Curso (TCC).
