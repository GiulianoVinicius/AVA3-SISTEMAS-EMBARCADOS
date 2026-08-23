# AVA3-SISTEMAS-EMBARCADOS
AVA3 DE SISTEMAS EMBARCADOS

## 📋 Explicação do Código

Este código implementa um sistema de controle de LED e buzzer usando uma placa microcontroladora (Arduino/ESP8266).

### 🔧 Definições de Pinos

```cpp
#define BUZZER D3      // Buzzer conectado ao pino D3
#define LED D2         // LED conectado ao pino D2
#define PORTA D5       // Sensor de porta conectado ao pino D5
#define BOTAO D6       // Botão conectado ao pino D6
```

### ⚙️ Função Setup()

```cpp
void setup() {
  Serial.begin(115200);  // Inicializa comunicação serial a 115200 baud
  
  pinMode(BUZZER, OUTPUT);      // Configura buzzer como saída
  pinMode(LED, OUTPUT);         // Configura LED como saída
  pinMode(PORTA, INPUT_PULLUP); // Configura sensor de porta como entrada com pull-up
  pinMode(BOTAO, INPUT_PULLUP); // Configura botão como entrada com pull-up
}
```

**O que faz:**
- Inicia a comunicação serial para debug/monitoramento
- Define os pinos como entrada ou saída
- Os pinos com INPUT_PULLUP usam resistor interno do microcontrolador

### 🔄 Função Loop()

```cpp
void loop() {
  // Verifica se o botão foi pressionado (sinal LOW)
  if (digitalRead(BOTAO) == 0) {
    digitalWrite(LED, HIGH);      // Acende LED
    digitalWrite(BUZZER, HIGH);   // Ativa buzzer
    delay(3000);                  // Mantém ligado por 3 segundos
    digitalWrite(BUZZER, LOW);    // Desativa buzzer
  }
  
  // Verifica se a porta foi aberta (sinal LOW)
  if (digitalRead(PORTA) == 0) {
    digitalWrite(LED, LOW);       // Apaga LED
  }
}
```

**Lógica de funcionamento:**

1. **Quando o botão é pressionado** (D6 = LOW):
   - LED acende
   - Buzzer ativa por 3 segundos
   - Após 3s, buzzer desativa
   - LED permanece aceso

2. **Quando a porta é aberta** (D5 = LOW):
   - LED apaga

### 📌 Caso de Uso

Este sistema pode ser usado para:
- **Alarme com ativação manual** - Botão ativa LED + buzzer
- **Sensor de porta** - Detecta abertura e desativa o LED
- **Sistema de alerta** - Combinação de feedback visual (LED) e sonoro (buzzer)

### 🎯 Componentes Necessários

- 1x Microcontrolador (Arduino/ESP8266)
- 1x LED
- 1x Buzzer
- 1x Botão (push button)
- 1x Sensor de porta (reed switch ou sensor magnético)
- Resistores apropriados (conforme necessário)

