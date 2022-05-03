# :information_desk_person: :computer: assistente-laboratorio-esp32

  ### Assistente de laboratório com ponto de acesso Wi-Fi utilizando ESP32

## Conteúdo

1. [Objetivo](https://github.com/nairamouras/assistente-laboratorio-esp32/blob/main/README.md#objetivo)
2. [Ideia do projeto](https://github.com/nairamouras/assistente-laboratorio-esp32/blob/main/README.md#ideia-do-projeto)
3. [Materiais utilizados](https://github.com/nairamouras/assistente-laboratorio-esp32/blob/main/README.md#materiais-utilizados)
4. [Etapa 1: ligando a ESP32-CAM](https://github.com/nairamouras/assistente-laboratorio-esp32/blob/main/README.md#etapa-1-ligando-a-esp32-cam)
5. [Etapa 2: criando um roteador com o ESP32-WROOM](https://github.com/nairamouras/assistente-laboratorio-esp32/blob/main/README.md#etapa-2-criando-um-roteador-com-o-esp32-wroom)
6. [Etapa 3: unindo os dois microcontroladores](https://github.com/nairamouras/assistente-laboratorio-esp32/blob/main/README.md#etapa-3-unindo-os-dois-microcontroladores)
7. [Referências](https://github.com/nairamouras/assistente-laboratorio-esp32/blob/main/README.md#referências)

## Objetivo

  O objetivo deste projeto é desenvolver um protótipo capaz de realizar a transmissão em tempo real de um vídeo para outros dispositivos conectados em uma mesma rede Wi-Fi, mesmo que não haja conexão com a internet.

## Ideia do projeto

  A ideia por trás deste projeto surgiu com a volta às aulas após a pandemia de COVID-19 nos últimos dois anos. Dessa forma, esse projeto é uma alternativa capaz de auxiliar o professor orientador a atender os alunos à distância durante uma aula prática e presencial, sem comprometer a eficiência das atividades desenvolvidas em sala e a saúde dos envolvidos.
  
## Materiais utilizados

- 2 cabos USB
- 1 ESP32-WROOM
- 1 ESP32-CAM + Módulo MB
- 2 protoboards
- 1 luminária USB
- 1 fonte de 5V com duas entradas USB
- 1 tomada
- 1 plug de tomada macho
- 1 fio de extensão
- 1 tábua de madeira
- 2 parafusos
- 2 LEDs
- 2 resistors de 330 ohms
- 3 fios de ligação

## Etapa 1: ligando a ESP32-CAM

  A primeira coisa a ser feita para dar início ao projeto é a ligação da ESP32-CAM. Para isso, é necessário utilizar o ambiente de desenvolvimento do Arduino.  
  
  [Link para o passo a passo da instalação da IDE no Windows.](https://youtu.be/FoaDfe5b-_Q)
  
  Feita a instalação, o próximo passo é selecionar a placa para a câmera nas ferramentas do ambiente:
  
    Ferramentas >> Placas >> ESP32 Arduino >> AI Thinker ESP32-CAM
  
  Em seguida, siga o seguinte caminho para importar a biblioteca da câmera e o código de configuração:
  
    Exemplos >> ESP32 >> Camera >> CameraWebServer
    
  Selecione a porta de conexão:
  
    Ferramentas >> Porta >> porta USB em que a ESP32-CAM está conectada no seu computador
    
  Agora, insira nesse trecho do código o **nome** e a **senha** da **rede local em que seu computador está conectado**:
  
    const char* ssid = "ESP32-Access-Point";
    const char* password = "123456789";
   
  Descomente o seguinte *#define* do cabeçalho:
   
    #define CAMERA_MODEL_AI_THINKER // Has PSRAM
  
  Finalizando a execução desses passos, compile, carregue o código e abra o monitor serial, cujo ícone está no canto superior direito da IDE.
  
   ![](https://blogmasterwalkershop.com.br/wp-content/uploads/2016/12/img01_arduino_exibindo_e_lendo_dados_da_serial.jpg)
  
   [Fonte: MasterWalker - Arduino, 2022.](https://blogmasterwalkershop.com.br/arduino/arduino-exibindo-e-lendo-dados-da-serial)
  
   Por fim, copie o endereço IP gerado e cole no seu navegador. Com a aba aberta, escolha uma resolução e aperte para iniciar a captura do vídeo em *Start Stream*. 
  
## Etapa 2: criando um roteador com o ESP32-WROOM

  A segunda etapa consiste em criar e rotear uma rede Wi-Fi com o ESP32-WROOM. O código desenvolvido pode ser encontrado neste [link.](https://randomnerdtutorials.com/esp32-access-point-ap-web-server/)
  
  Novamente, escolha a placa a ser utilizada:
  
    Ferramentas >> Placas >> ESP32 Arduino >> ESP32 Dev Module
    
  Logo após, a porta de conexão:
  
    Ferramentas >> Porta >> porta USB em que a ESP32-CAM está conectada no seu computador
  
  Nesse caso, insira o nome e a senha que deseja para a sua rede:
  
    const char* ssid = "ESP32-Access-Point";
    const char* password = "123456789";
    
  *Uma observação importante:* alguns ESP32-WROOM necessitam que o botão de **boot** esteja pressionado durante todo o processo de carregamento do código.
  
  O processo de execução do código do roteador é igual ao da câmera, mas lembre-se de conectar o seu computador na rede que você criou:
  
  ![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2018/07/ESP32-access-point.jpg?w=600&quality=100&strip=all&ssl=1)
  
  [Fonte: Random Nerd Tutorials, 2022.](https://randomnerdtutorials.com/esp32-access-point-ap-web-server/)

## Etapa 3: unindo os dois microcontroladores

  Nesta etapa ao invés de utilizar a rede local definida no código da câmera, utiliza-se a rede criada pelo ESP32-WROOM no código do roteador. 

## Referências

RANDOM NERD TUTORIALS. ***How to Set an ESP32 Access Point (AP) for Web Server***. Disponível em: <<https://randomnerdtutorials.com/esp32-access-point-ap-web-server/>>

TUTORIAIS TECNOLOGIAS TENDÊNCIAS. **Instalando ESP32 no Arduino IDE: Método fácil.** Disponível em: <<https://www.fernandok.com/2018/09/instalando-esp32-no-arduino-ide-metodo.html>>

KENJI MARCOS SUZUKI. **Como Instalar IDE do Arduino no Windows.** Disponível em: <<https://youtu.be/FoaDfe5b-_Q>>
