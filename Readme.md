# **Começo de tudo**
Decidi começar com arduino depois de uma aventura em um veleiro com pessoas maravilhosas onde o dono usou arduino em algumas coisas, isso aconteceu no dia 02/04/2022, então resolvi dar uma garimpada na internet sobre arduinos pra ver como funciona tudo, depois de uma semana pensando, estou pesquisando qual circuito comprar em relação custo benefício, até que achei um kit legalzinho para começar no Mercado Livre de R$200.

Uma das minhas motivações além dessa citada acima é achar um hobbie, como eu sou uma pessoa que gosta de muita coisa manual e eletronicos em geral, creio que vou me dar bem, um dos meus projetos futuros é um tanque de guerra que atira bolinhas de papel.

<br />

## **Iniciando**
Bom, não tem segredo de inicio, vamos precisar de um kit básico como já citei acima e de uma IDE como a própria do [arduino](https://www.arduino.cc/en/software) para escrever os códigos para ser interpretado pelo arduino.
> Uma curiosidade, a IDE não tem autocomplete haha

<br />

---

<br />


### **Primeiro desafio - Acender um LED**
Meu primeiro desafio vai ser acender um LED, acho que todos que começam com arduino tem esse desafio básico, é como se fosse o `Hello World` da programação, ainda não cheguei a fazer, mas logo que fizer, postarei uma foto e os códigos aqui mesmo.

Bom, depois que meu kit chegou, fui logo testar e olha só, consegui ascender meu primeiro LED. Não foi tão dificil como pensava, mas depois no projeto do Semaforo que o bixo pegou pra mim.

<img src="./img/first-led.png" width="200" />
<br />
<br />

**Código do projeto**
```cpp
void setup() {
    pinMode(12, OUTPUT); // Seleciona a porta no arduino como saída
}

void loop() {
    // Seleciona um pino e valor, sendo o valor HIGH ou LOW
    digitalWrite(12, HIGH);
    delay(100);
    digitalWrite(12, LOW);
    delay(100);
}
```

<br />

---

<br />

### **Segundo desafio - Semáforo**
Esse é mais complicado, mas é fazer um esquema de semáfaro, vou precisar de uns LED's e resistores a mais, acho que por enquanto, esse deve bem interessante a se fazer. Tive uma certa dificuldade em fazer, conectei uns pinos errados, resitores fora do lugar e etc, mas ao que tudo indica isso faz parte do aprendizado, tive uma pequena ajudinha da minha namorada nesse aqui mas o resultado final é muito satisfatório.

<br />

<img src="./img/semaforo-red.jpeg" width="200" />
<img src="./img/semaforo-yellow.jpeg" width="200" />
<img src="./img/semaforo-green.jpeg" width="200" />

<br />

**Código do projeto**
```cpp
// dando um "nome" para as portas
int vermelho = 10;
int amarelo = 9;
int verde = 8;

void setup() {
    pinMode(vermelho, OUTPUT);
    pinMode(amarelo, OUTPUT);
    pinMode(verde, OUTPUT);
}

void loop() {
    digitalWrite(vermelho, LOW);
    digitalWrite(amarelo, HIGH);
    digitalWrite(verde, LOW);

    // esperamos 2s com o sinal no amarelo
    delay(2000);

    // apagamos o amarelo e ligamos o vermelho
    digitalWrite(amarelo, LOW);
    digitalWrite(vermelho, HIGH);


    // esperamos 5s com o sinal fechado
    delay(5000);

    // para finalizar, apagamos o vermelho e ligamos o verde
    digitalWrite(verde, HIGH);
    // não precisa desse pois o amarelo já estava apagado
    // digitalWrite(amarelo, LOW);
    digitalWrite(vermelho, LOW);

    // esperamos 5s com o sinal aberto
    delay(5000);
}
```

<br />

---

<br />

### **Terceiro Projeto**
Bom, esse projetinho até que foi relativamente desafiador, como tinha dito anteriormente, conectar leds, resistores e até mesmo declarar variaveis erradas faz parte do processo de aprendizagem, e nesse aqui não foi muito diferente, inicialmente dava uns erros na porta e etc, algo que não estava compreendendo mas de algum jeito tudo se resolveu, apenas aperto o botão e o led acende, e tiro o dedo o led apaga.


<br />

<img src="./img/botão-led.png" width="200" />
<img src="./img/botão-led-aceso.jpeg" width="200" />
<img src="./img/botão-led-apagado.jpeg" width="200" />

**Código do projeto**

```cpp
int buttonPin = 7;
int ledPin = 10;
int buttonState = 0;

void setup() {
    // put your setup code here, to run once:
    pinMode(ledPin, OUTPUT);
    pinMode(buttonPin, INPUT);
}

void loop() {
    // put your main code here, to run repeatedly:
    buttonState = digitalRead(buttonPin);

    if (buttonState == HIGH) {
        digitalWrite(ledPin, HIGH);
        delay(100);
    }
    else {
        digitalWrite(ledPin, LOW);
    }
}
```
