# Projeto ESP32 MQTT - Monitoramento de Temperatura e Umidade

> **🌟 PROJETO BASE - GLOBAL SOLUTION 2025**
> 
> Este projeto serve como base para o desenvolvimento da Global Solution 2025.
> Os alunos devem utilizar esta estrutura como ponto de partida para implementar
> suas soluções inovadoras de IoT com ESP32.

## ⚠️ ATENÇÃO - IMPORTANTE PARA LABORATÓRIOS FIAP

> Para o correto funcionamento do projeto nos laboratórios da FIAP, é necessário:
> 
> 1. Solicitar ao professor a liberação das portas no firewall:
>    - Porta 1883 (MQTT Broker)
>    - Porta 1880 (Node-RED Dashboard)
> 2. Sem essa liberação, não será possível:
>    - Conectar ao broker MQTT
>    - Visualizar os dados no dashboard Node-RED
>    - Testar a comunicação do projeto

## 📝 Descrição

O projeto implementa um sistema IoT completo que:

**Conectividade**
- Conecta um ESP32 a uma rede Wi-Fi
- Estabelece comunicação com broker MQTT
- Gerencia reconexões automáticas

**Sensores e Dados**
- Leitura de temperatura e umidade (DHT22)
- Leitura de potenciômetro (controle analógico)
- Envio periódico de dados (10 segundos)
- Feedback visual por LED

**Identificação**
- ID do grupo
- ID do módulo
- Endereço IP
- Endereço MAC

## Recursos do Servidor

O projeto utiliza um servidor dedicado com:

- **Broker MQTT**: 
  - Endereço: `172.208.54.189`
  - Porta: `1883`
  - Usuário e senha já configurados

- **Node-RED**: 
  - Interface visual em `172.208.54.189:1880`
  - Dashboard para monitoramento em tempo real
  - Gráficos e indicadores personalizados

## ⚙️ Pré-requisitos

1. **Software**
   - Visual Studio Code
   - Extensão PlatformIO IDE
   - Git (para clonar o repositório)

2. **Simulação**
   - Conta Wokwi
   - Licença Wokwi Simulator
   - Extensão Wokwi no VS Code

## Instalação e Configuração

### 1. Clone o Repositório

```bash
git clone https://github.com/prof-atritiack/2TDS-GS2025.git
cd 2TDS-GS2025
```

### 2. Configuração do VS Code

1. Abra o VS Code
2. File > Open Folder
3. Selecione a pasta `2TDS-GS2025`
4. Aguarde o PlatformIO inicializar

### 3. Configuração do Wokwi

1. Instale a extensão Wokwi
2. Faça login na sua conta
3. Verifique a licença ativa

### 4. Dependências

O projeto utiliza as seguintes bibliotecas:
- ArduinoJson (JSON)
- DHT sensor library (Sensor)
- Adafruit Unified Sensor (Base)
- PubSubClient (MQTT)

> ⚠️ **Importante**: Aguarde a instalação completa das dependências antes de compilar!

### 5. Configuração do Código

Em `q1/src/main.cpp`, configure:
```cpp
const char* ID        = "ID_do_Grupo";     // Seu identificador
const char* moduleID  = "Meu_ESP32";       // Nome do seu ESP32
```

## Estrutura do Projeto

```
2TDS-GS2025/
├── q1/
│   └── src/
│       └── main.cpp          # Código principal
├── platformio.ini            # Configuração
└── README.md                 # Documentação
```

## Formato dos Dados

O JSON enviado segue este formato:
```json
{
    "ID": "ID_do_Grupo",          // Identificador do grupo
    "Sensor": "Meu_ESP32",        // Nome do dispositivo
    "IP": "xxx.xxx.xxx.xxx",      // IP local
    "MAC": "XX:XX:XX:XX:XX:XX",   // Endereço MAC
    "Temperatura": xx.xx,         // Em graus Celsius
    "Umidade": xx.xx,            // Em porcentagem
    "Potenciometro": xxxx        // Valor 0-4095
}
```

## Monitor Serial

O monitor serial (115200 baud rate) exibe informações detalhadas:

### Inicialização
```
Conectando ao Wi-Fi.....
Wi-Fi conectado!
IP: 192.168.1.100
MAC Address: A4:CF:12:BF:7A:E5
Conectando ao Broker MQTT...
Conectado ao Broker!
```

### Envio de Dados
```
{
    "ID": "2TDS",
    "Sensor": "ESP32_Lab1",
    "IP": "192.168.1.100",
    "MAC": "A4:CF:12:BF:7A:E5",
    "Temperatura": 25.40,
    "Umidade": 63.20,
    "Potenciometro": 2048
}
Mensagem publicada com sucesso!
```

### Possíveis Erros
```
Reconectando Wi-Fi...     // Perda de conexão
Erro na leitura do DHT    // Falha no sensor
Falha na conexão. Estado: -2   // Problema MQTT
```

O LED onboard (GPIO2) pisca após cada envio bem-sucedido!

## Visualização dos Dados

1. **Node-RED**
   - Acesse: `172.208.54.189:1880`
   - Visualização em tempo real
   - Gráficos interativos

2. **Monitor Serial**
   - Debug local
   - Verificação de erros
   - Teste de funcionamento

## Personalização do Node-RED ⚡

O Node-RED é uma ferramenta poderosa que permite expandir significativamente as capacidades do seu projeto. Recomenda-se fortemente que você desenvolva seus próprios fluxos para atender às necessidades específicas do seu projeto.

### Possibilidades de Expansão

1. **Integração com APIs Externas**
   - Conexão com serviços de previsão do tempo
   - Integração com APIs de notificação
   - Webhooks para sistemas externos
   - Automação com serviços em nuvem

2. **Banco de Dados**
   - Armazenamento histórico de leituras
   - Análise de tendências
   - Backup de dados
   - Consultas personalizadas
   
3. **Dashboards Personalizados**
   - Gráficos em tempo real
   - Indicadores personalizados
   - Painéis de controle interativos
   - Visualizações específicas para seu caso de uso

4. **Lógica de Negócio**
   - Processamento de dados
   - Filtros e transformações
   - Regras de negócio
   - Alertas condicionais

### Dicas de Implementação

- Comece com fluxos simples e incremente gradualmente
- Use nodes de debug para verificar o processamento dos dados
- Documente seus fluxos com nodes de comentário
- Faça backup regular dos seus fluxos
- Considere implementar autenticação para seus endpoints

### Recursos para Node-RED

- [Node-RED Library](https://flows.nodered.org/)
- [Documentação Oficial](https://nodered.org/docs/)
- [Guia de Boas Práticas](https://nodered.org/docs/user-guide/writing-flows)

## Créditos

Este projeto é baseado no trabalho original do Professor Arnaldo Viana:
[Repositório Original](https://github.com/arnaldojr/iot-esp32-wokwi-vscode.git)

## Suporte

Precisa de ajuda?
1. Verifique as issues no repositório
2. Consulte a documentação das bibliotecas
3. Contate o professor ou monitores

## Referências e Recursos

### Documentação Técnica
- [Documentação ESP32](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/)
- [Biblioteca PubSubClient](https://pubsubclient.knolleary.net/)
- [ArduinoJson](https://arduinojson.org/)
- [Wokwi](https://docs.wokwi.com/)

### Desenvolvimento Assistido por IA
Este projeto foi desenvolvido com auxílio de IA Generativa:
- **Modelo**: Claude 3.5 Sonnet
- **Plataforma**: Cursor IDE
- **Aplicação**: 
  - Geração e revisão de código
  - Documentação técnica
  - Debugging assistido
  - Otimização de código

### Recursos Educacionais
- [ESP32 - Primeiros Passos](https://randomnerdtutorials.com/getting-started-with-esp32/)
- [MQTT Essentials](https://www.hivemq.com/mqtt-essentials/)

## Uso com Placas Físicas

Para grupos que optarem por usar uma placa ESP32 física:

1. **Arquivo para Arduino**
   - Use o arquivo `q1/esp32_mqtt_dht22.ino`
   - Contém o mesmo código e funcionalidades do projeto

2. **Bibliotecas Necessárias**
   - `PubSubClient`
   - `ArduinoJson`
   - `DHT sensor library`
   - `Adafruit Unified Sensor`

3. **Configuração do Código**
   - Configure suas credenciais Wi-Fi:
     ```cpp
     const char* ssid = "SUA_REDE_WIFI";
     const char* password = "SUA_SENHA_WIFI";
     ```
   - Ajuste os identificadores:
     ```cpp
     const char* ID = "ID_do_Grupo";
     const char* moduleID = "Meu_ESP32";
     ```

4. **Conexões Físicas**
   - DHT22:
     - VCC → 3.3V
     - GND → GND
     - DATA → GPIO12
   - Potenciômetro:
     - VCC → 3.3V
     - GND → GND
     - SIGNAL → GPIO34
   - LED onboard está no GPIO2

> ⚠️ **Importante**: Verifique todas as conexões antes de energizar a placa e use resistores pull-up quando necessário. 
