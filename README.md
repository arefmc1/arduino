# arduino

Mao maoEsq; 
  Mao maoDir;  
Mao maoGarra;   
  Mao maoBraco;  
  Mao maoBraco2;
 
  int posicaoBraco = 0;
  int posicaoGarra = 80;
  int ladodir=20;
  int ladoesq=20;
  int maoDir;
  int maoEsq;
 
void setup() 
{
  
 maoGarra.attach(3);
  maoBraco.attach(5);
  maoBraco2.attach(6);
  maoEsq.attach(9);
  maoDir.attach(10);
  Serial.begin(9600);
}

void parado() 
{
    maoDir.write(87);
    maoEsq.write(90);
}
void direita() 
{
    maoEsq.write(0);
    maoDir.write(0);
    delay(1300); 
    parado();
}

void esquerda()  
{
    maoEsq.write(180);
    maoDir.write(180);
    delay(1300);   
    parado();
}

void sobeBraco() 
{
  int i;
  for( i = posicaoBraco;i<90;i++)
  {
      maoBraco.write(180-i);
      maoBraco2.write(i);
      delay(45);
  }
  posicaoBraco = i;
}

void baixaBraco() 
{
  int i;
  for(i = posicaoBraco; i > 0;i--)
  {
      maoBraco.write(180-i);
      maoBraco2.write(i);
      delay(45);
  }
  posicaoBraco = i;
}

void abre() 
{
   int i;
  for(i = posicaoGarra; i < 160;i++)
  {
      maoGarra.write(i);
      delay(40);
  }
  posicaoGarra = i;
}

void fecha()  
{
   int i;
  for(i = posicaoGarra; i > 80;i--)
  {
      maoGarra.write(i);
      delay(40);
  }
  posicaoGarra = i;
}


void loop()
{
    char tecla = Serial.read(); 
    if(tecla == 'x' || tecla == 'X')
    {
      direita();
    }
    else if(tecla == 'o' || tecla == 'O') 
    {
      esquerda();
    }
   
    else if (tecla == 'y' || tecla == 'Y') 
    {
       abre();
    }
    else if(tecla == 'b' || tecla == 'B') 
    {
      fecha();
    }
    else if (tecla == 'r' || tecla == 'R') 
    {
        sobeBraco();
    }
    else if (tecla == 'l' || tecla == 'L') 
    {
       baixaBraco();
    }
   
    else 
    {
        parado();
    }
}

caminho do robo, ele vai seguir uma linha para utilizar os braços.

int E1=5;
int E2=6;
int M1=4;
int M2 =7;

int sensorCantoesq=A1;
int sensorCantoesq=A2;
int sensorCantoesq=A3;
int sensorCantoesq=A4;

int ValorCorte =700;

int velocidade = 200;



int valorlinhaesq, valorlinhadir,valorcantesq,valorcantdir=0;

void setup(){

  pinMode(4,OUTPUT);
  pinMode(5,OUTPUT);
  pinMode(6,OUTPUT);
  pinMode(7,OUTPUT);

  void setup (){
    valorlinhaesq=analogRead(sensorlinhaesq);
    valorlinhadir=analogRead(sensorlinhadir);
    valorcantoesq-analogRead(sensorcantesq);

    if(valorlinhaesq>valorCorte)&&(valorlinhadir>valorcorte)){
      analogWrite(E1,velocidade);
      analogWrite(E2,velocidade);
      digitalWrite(M1,LOW);
      digitalWrite(M2,LOW);
    }
    if (valorlinhaEsq<valorCorte)&&(valorlinhadir>valorcorte)){
       analogWrite(E1,velocidade);
      analogWrite(E2,velocidade);
      digitalWrite(M1,HIGH);
      digitalWrite(M2,LOW);
    }
    if (valorlinhaEsq>valorCorte)&&(valorlinhaDir<valorCorte)){
      analogWrite(E1,velocidade);
      analogWrite(E2,velocidade);
      digitalWrite(M1,LOW);
      digitalWrite(M2,HIGH);
    }
  }
}

