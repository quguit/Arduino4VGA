# Projeto: Relógio Digital com Exibição VGA

## Descrição
Esse projeto consiste em um relógio digital que exibe a hora atual em um monitor VGA conectado ao Arduino. O relógio terá a opção de alternar entre diferentes modos de exibição, como formato 12 horas ou 24 horas, e também exibirá a data atual.

## Requisitos
- Arduino Uno ou compatível
- Módulo VGA (como o módulo VGA666)
- Monitor VGA ou TV com entrada VGA
- Módulo de Tempo Real (RTC) (como o DS3231)
- Protoboard
- Jumpers
- Fontes de alimentação adequadas

## Passo a Passo

### 1. Configurar o hardware
- Conecte o módulo VGA ao Arduino de acordo com as instruções do fabricante.
- Conecte o módulo RTC ao Arduino usando a interface I2C.
- Conecte o monitor VGA ou a TV ao módulo VGA.

### 2. Instalar as bibliotecas necessárias
- Instale a biblioteca "VGA" para controlar o módulo VGA.
- Instale a biblioteca "RTClib" para controlar o módulo RTC.

### 3. Escreva o código

```arduino
// Incluir bibliotecas
#include <VGA.h>
#include <RTClib.h>

// Criar instâncias dos objetos
VGA vga;
RTC_DS3231 rtc;

// Variáveis para armazenar a hora e a data
DateTime now;

void setup() {
  // Inicializar o monitor VGA
  vga.begin();

  // Inicializar o módulo RTC
  rtc.begin();

  // Definir a hora inicial do RTC (apenas na primeira vez)
  // rtc.adjust(DateTime(2023, 5, 17, 12, 0, 0));
}

void loop() {
  // Obter a hora e data atuais do RTC
  now = rtc.now();

  // Limpar a tela
  vga.clear();

  // Desenhar a hora e a data na tela
  vga.setCursor(10, 10);
  vga.print(now.hour());
  vga.print(":");
  vga.print(now.minute());
  vga.print(":");
  vga.print(now.second());
  vga.setCursor(10, 30);
  vga.print(now.day());
  vga.print("/");
  vga.print(now.month());
  vga.print("/");
  vga.print(now.year());

  // Atualizar o buffer do VGA
  vga.flush();

  // Atraso de 1 segundo
  delay(1000);
}
``` 
 

### 4. Carregar o código no Arduino.

### 5. Ajustar a hora e a data no módulo RTC, se necessário.

### 6. Ligar o monitor VGA ou a TV e observar o relógio digital em funcionamento.

## Recursos Adicionais (Opcionais):

  - Adicionar botões para alternar entre modo de 12 horas e 24 horas.
  - Implementar alarme com som.
  - Exibir a temperatura atual usando um sensor de temperatura.
  - Personalizar a aparência do relógio (fontes, cores, etc.).
  

Esse projeto permitirá que você aprenda a controlar um módulo VGA usando Arduino, trabalhar com um módulo RTC para obter a hora e a data, e exibir informações em um monitor VGA. É um projeto relativamente simples, mas abrange conceitos importantes, como manipulação de bibliotecas, controle de hardware e exibição de informações gráficas.
