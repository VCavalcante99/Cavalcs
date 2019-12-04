•	Descrição do projeto

	Consiste em fazer dois dispositivos que tenham uma comunicação entre si.
	Cada mesa do restaurante terá um dispositivo de chamada com um endereçamento único mantendo a conectividade 
	com o dispositivo do garçom, para que o mesmo vá atender o cliente. 
O desenvolvimento do projeto consiste na comunicação de diversos dispositivos, com diferentes endereçamentos e que mantenham-se conectados com um dispositivo individual, esse dispositivo individual será a plataforma de saída para que o cliente possa chamar o garçom.
A ideia é que cada mesa tenha um dispositivo de chamada, cada um com seu endereçamento (isso é necessário para que todos os dispositivos possam se comunicar com o do garçom), com um botão e um led, já o dispositivo que ficará na posse do garçom será um terminal com leds e indicações de mesa, mostrando exatamente em qual das mesas é necessária a ida dele.

Com Luzes de comando:
- Vermelho: Cancelar o pedido após ser atendido;
- Verde: Fazer o pedido;
- Amarela: Pedir a conta.



•	Código do projeto:
from machine import Pin
from time import sleep
import network


led1 = Pin(2, Pin.OUT)
led2 = Pin(0, Pin.OUT)
led3 = Pin(4, Pin.OUT)
entrada1 = Pin(14, Pin.IN, Pin.PULL_UP)
entrada2 = Pin(12, Pin.IN, Pin.PULL_UP)
entrada3 = Pin(13, Pin.IN, Pin.PULL_UP)
entrada4 = Pin(15, Pin.IN, Pin.PULL_UP)

wlan = network.WLAN(network.STA_IF)
wlan.active(True)
wlan.scan()
wlan.connect('essid' , 'password')


while True:
  if entrada1.value() == False:
    led1.value(1)
    led2.value(0)
    led3.value(0)
  if entrada2.value() == False:
    led1.value(0)
    led2.value(1)
    led3.value(0)
  if entrada3.value() == False:
    led1.value(0)
    led2.value(0)
    led3.value(0)  
  if entrada4.value() == False:
    led1.value(0)
    led2.value(0)
    led3.value(1)  

