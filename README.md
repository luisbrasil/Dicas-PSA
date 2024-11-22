# Dicas-PSA

Esse é um conteúdo baseado na experiência de desenvolvimento de um jogo utilizando o Pygame, apesar disso a maioria das dicas aqui apresentadas serviram para qualquer linguagem ou biblioteca escolhida.

### Repositório do Jogo: https://github.com/luisbrasil/dirtyMotorsPy

## Dica 1: Quantidade de Movimento 

### https://drive.google.com/file/d/1wZyB0PnZJd-YieUKnIUX-hbkGAor18Tt/view?usp=sharing

A conservação da quantidade de movimento é um dos mais importantes princípios da Física. De acordo com esse princípio, na ausência de forças dissipativas, a quantidade de movimento total de um sistema deve manter-se constante. Isso indica que, em situações em que ocorrem colisões, por exemplo, o produto da massa pela velocidade dos corpos deve ser igual antes e após o contato entre eles – nestes casos, dizemos que a colisão foi perfeitamente elástica.

![image](https://github.com/user-attachments/assets/1e85674d-35e9-4e1b-bb4f-577e114cf611)

mA e mB – massas dos corpos A e B
vA e vB – velocidades dos corpos A e B antes da colisão
v'A e v'B – velocidades dos corpos A e B após a colisão

A implementação prática está no arquivo collision.py do repositório do jogo, nas linhas 50 até a 64;
