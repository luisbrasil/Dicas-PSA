# Dicas-PSA

Esse é um conteúdo baseado na experiência de desenvolvimento de um jogo utilizando o Pygame, apesar disso a maioria das dicas aqui apresentadas serviram para qualquer linguagem ou biblioteca escolhida.

### Repositório do Jogo: https://github.com/luisbrasil/dirtyMotorsPy

## Dica 1: Quantidade de Movimento 

Vídeo Explicativo:

### https://drive.google.com/file/d/1wZyB0PnZJd-YieUKnIUX-hbkGAor18Tt/view?usp=sharing

A conservação da quantidade de movimento é um dos mais importantes princípios da Física. De acordo com esse princípio, na ausência de forças dissipativas, a quantidade de movimento total de um sistema deve manter-se constante. Isso indica que, em situações em que ocorrem colisões, por exemplo, o produto da massa pela velocidade dos corpos deve ser igual antes e após o contato entre eles – nestes casos, dizemos que a colisão foi perfeitamente elástica.

![image](https://github.com/user-attachments/assets/1e85674d-35e9-4e1b-bb4f-577e114cf611)

mA e mB – massas dos corpos A e B

vA e vB – velocidades dos corpos A e B antes da colisão

v'A e v'B – velocidades dos corpos A e B após a colisão

A implementação prática está no arquivo collision.py do repositório do jogo, nas linhas 50 até a 64;

## Dica 2: Assets

Vídeo Explicativo:

### https://drive.google.com/file/d/1Ee-7UdvC8s4O-yWhg5JAVv0ZI_qBoavx/view?usp=sharing

Link do site: https://itch.io/game-assets

## Dica 3: Tela Infinita

Vídeo Explicativo:

### https://drive.google.com/file/d/1U4bEL4gybppjynSg-cPC_x1aHE0wZQly/view?usp=sharing

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

Essa função faz o objeto reaparecer do lado oposto da tela quando sai dos limites, simulando um espaço contínuo. Se o objeto ultrapassa as bordas (horizontal ou vertical), ele é reposicionado no lado oposto, considerando uma pequena margem de tolerância.
