# Dicas-PSA

Esse é um conteúdo baseado na experiência de desenvolvimento de um jogo utilizando o Pygame, apesar disso a maioria das dicas aqui apresentadas serviram para qualquer linguagem ou biblioteca escolhida.

### Repositório do Jogo: https://github.com/luisbrasil/dirtyMotorsPy

## Dica 1: Quantidade de Movimento 

Vídeo Explicativo:

### https://drive.google.com/file/d/1wZyB0PnZJd-YieUKnIUX-hbkGAor18Tt/view?usp=sharing

Um conceito interessante que foi aplicado no jogo é de quantidade de movimento para resolver a colisão entre os carros:

A conservação da quantidade de movimento é um dos mais importantes princípios da Física. De acordo com esse princípio, na ausência de forças dissipativas, a quantidade de movimento total de um sistema deve manter-se constante. Isso indica que, em situações em que ocorrem colisões, por exemplo, o produto da massa pela velocidade dos corpos deve ser igual antes e após o contato entre eles – nestes casos, dizemos que a colisão foi perfeitamente elástica.

![image](https://github.com/user-attachments/assets/1e85674d-35e9-4e1b-bb4f-577e114cf611)

mA e mB – massas dos corpos A e B

vA e vB – velocidades dos corpos A e B antes da colisão

v'A e v'B – velocidades dos corpos A e B após a colisão

        qt_mov_obj1 = Vector(obj1.mass * obj1.speed.x, obj1.mass * obj1.speed.y)
        qt_mov_obj2 = Vector(obj2.mass * obj2.speed.x, obj2.mass * obj2.speed.y)

        if abs(qt_mov_obj1.x) + abs(qt_mov_obj1.y) > 0:
            obj2.direction.x = qt_mov_obj1.x / obj2.mass
            obj2.direction.y = qt_mov_obj1.y / obj2.mass
            obj2.vel = obj2.direction.module()
            obj2.direction.normalize()

        if abs(qt_mov_obj2.x) + abs(qt_mov_obj2.y) > 0:
            obj1.direction.x = qt_mov_obj2.x / obj1.mass
            obj1.direction.y = qt_mov_obj2.y / obj1.mass
            obj1.vel = obj1.direction.module()
            obj1.direction.normalize()


Esse código, extraído do nosso jogo Dirty Motors, é um exemplo da implementação pratica em python da resolução da quantidade de movimento.

## Dica 2: Assets

Vídeo Explicativo:

### https://drive.google.com/file/d/1Ee-7UdvC8s4O-yWhg5JAVv0ZI_qBoavx/view?usp=sharing

Uma das dificuldades do jogo é a criação dos sprites, onde obtê-los, etc. Um bom website que utilizamos na criação do Dirty Motors foi o itch.io, ele é um site de jogos indies onde qualquer um pode publicar seu jogo e receber apoio financeiro de quem se interessar pelo projeto. Mas além disso, para o nosso foco, no site os usuários disponibilizam diversos sprites, sendo eles 2D ou 3D, gratuitos ou pagos. É atualmente o site da internet com o maior acervo de sprites disponíveis para uso, uma parte interessante é a opção de filtrar pelo tema do sprite, por exemplo no caso do nosso jogo, pesquisamos pela tag Car, para encontrar sprites de carro.

![image](https://github.com/user-attachments/assets/dfc33fe0-0c86-421a-a415-542813f0f68f)

Essa imagem é um exemplo de pesquisa por sprites feita com os seguintes parâmetros: Free(Gratuito), 2D(duas dimensões) e Car(carro).

Link do site: https://itch.io/game-assets

## Dica 3: Tela Infinita

Vídeo Explicativo:

### https://drive.google.com/file/d/1U4bEL4gybppjynSg-cPC_x1aHE0wZQly/view?usp=sharing

A tela infinita, é o conceito onde um objeto ao sair da tela apareça no lado oposto dela, simulando um ambiente contínuo, um exemplo muito conhecido é o jogo da cobrinha, onde quando a cobrinha saia de um lado da tela seu corpo ia aparecendo no lado oposto, esse conceito é especialmente popular em jogos onde a mecânica de movimento e a exploração são centrais, já que elimina barreiras artificiais e incentiva o jogador a usar toda a tela como campo de jogo, assim como é o caso do nosso jogo.

1. Aumentar a Imersão
        Em jogos com temática espacial, como Asteroids, o espaço contínuo simula o efeito de um universo infinito, onde não há limites "visíveis". Isso torna o ambiente mais envolvente e realista.
2. Facilitar a Navegação
        Em um espaço contínuo, os jogadores não ficam "presos" em bordas da tela. Em vez disso, ao ultrapassá-las, retornam para o outro lado. Isso permite uma movimentação fluida, útil em jogos de combate ou exploração.
3. Criação de Estratégias Únicas
        Jogadores podem planejar estratégias que envolvem sair de uma borda da tela para surpreender inimigos ou escapar de situações perigosas, como em jogos de ação ou de combate.
4. Manutenção de Objetos em Movimento
        Para jogos com projéteis, veículos ou personagens rápidos, o espaço contínuo permite que esses objetos reapareçam e mantenham sua dinâmica sem precisar de restrições artificiais, como colisões invisíveis nas bordas.
5. Simplicidade de Design
        Do ponto de vista técnico, essa abordagem pode simplificar a lógica de certos elementos. Em vez de parar um objeto nas bordas, o jogo apenas reposiciona sua coordenada, reduzindo a complexidade de tratamento.

```
    def check_teleport(self):
        if self.position.x > self.screen_width + 0.03 * self.screen_width:
            self.position.x = 0 - 0.03 * self.screen_width
        elif self.position.x < 0 - 0.03 * self.screen_width:
            self.position.x = self.screen_width
        if self.position.y > self.screen_height + 0.03 * self.screen_height:
            self.position.y = 0 - 0.03 * self.screen_height
        elif self.position.y < 0 - 0.03 * self.screen_height:
            self.position.y = self.screen_height
```

Essa função é um exemplo em pyhton, que foi utilizado na nossa implementação, ela faz o objeto reaparecer do lado oposto da tela quando sai dos limites, simulando um espaço contínuo. Se o objeto ultrapassa as bordas (horizontal ou vertical), ele é reposicionado no lado oposto, considerando uma pequena margem de tolerância.

## Dica 4: Vetores

Vídeo Explicativo:

### https://drive.google.com/file/d/1NGUUn5bh8cg7BxB7zV1p4X5dKoSEOz18/view?usp=sharing

Para quem está um pouco perdido de por onde iniciar seu jogo, está naquela primeiro momento mais lento e confuso, que é o de definição de entidades, uma entidade importantissima de se considerar a implementação é a classe Vetor. No nosso jogo toda a física foi vetorizada, ou seja grandezas vetoriais como velocidade e posição foram consideradas um Vetor no nosso trabalho. Essa implementação permite uma maior liberdade no controle da física e uma implementação da física mais semelhante ao conceito físico teórico.

A seguir esta o código em Python de uma classe Vetor genérica, a implementada no nosso jogo, note que não há nenhum vínculo com um jogo em si é apenas uma classe genérica que pode até ser reutilizada por quem estiver desenvolvendo em python também:

```
import math

class Vector:
    def __init__(self, x:float, y:float):
        self.x = x
        self.y = y
        
    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __mul__(self, scalar: float):
        self.x = self.x * scalar
        self.y = self.y * scalar
            
    def __div__(self, scalar: float):
        self.x = self.x/scalar
        self.y = self.y/scalar
        
    def __str__(self):
        return "x: "+str(self.x)+" y: "+str(self.y)
        
    def length(self):
        return math.sqrt(self.x**2 + self.y**2)
    
    def normalize(self):
        length = self.length()
        if length != 0:
            self.x /= length
            self.y /= length
    
    def set_module(self, mod: float):
        self.__div__(self.module())
        self * mod        
    
    def module(self):
        return math.sqrt(Vector.prod_int(self, self))
    
    def dot(self, other):
        return self.x * other.x + self.y * other.y
    
    @staticmethod
    def prod_int(v1, v2):
        return v1.x * v2.x + v1.y * v2.y
```

O código define uma classe Vector para representar vetores 2D e realizar operações comuns relacionadas a eles, como adição, subtração, multiplicação por escalar, normalização e cálculo de módulo (comprimento). Ele inclui métodos para operações básicas, como __add__ e __sub__, que permitem somar e subtrair vetores diretamente, e __mul__ e __div__, para escalar o vetor por multiplicação ou divisão. Além disso, há métodos como length e module para calcular o tamanho do vetor, e normalize para ajustá-lo ao comprimento 1, preservando sua direção. A classe também suporta o cálculo do produto escalar (dot) e inclui uma função estática para calcular o produto interno entre dois vetores. Essa implementação é útil para aplicações como simulação de física ou jogos, onde manipulações de vetores são comuns.

## Animations

Vídeo Explicativo:

### https://drive.google.com/file/d/1XQchM5BWZ4x3Xy1wkjC7uUisckUltm5-/view?usp=sharing

Código apresentado no vídeo:

```
import pygame

from systems.image_rendering import blit_rotate_center


class CollisionAnimation:
    def __init__(self, frames, position):
        self.frames = frames
        self.position = position
        self.current_frame = 0
        self.last_update = pygame.time.get_ticks()
        self.frame_rate = 100  # milliseconds between frames

    def update(self):
        now = pygame.time.get_ticks()
        if now - self.last_update > self.frame_rate:
            if self.current_frame < len(self.frames) - 1:
                self.current_frame += 1
            self.last_update = now

    def draw(self, surface):
        blit_rotate_center(surface, self.frames[self.current_frame], (self.position.x, self.position.y), 0)
```
