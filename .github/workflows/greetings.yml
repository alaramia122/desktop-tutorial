import pygame
import random
import copy
# # инициализация Pygame:
class Board:
    # создание поля
    def __init__(self, width, height):
        self.width = width
        self.height = height
        self.board = []
        self.boarda1 = []
        self.boardnew = []
        self.move = ''
        self.y = 0
        b = 0
        while b != 2:
            for i in range(height):
                a = []
                a1 = []
                for j in range(width):
                    e = random.randint(0, 2)
                    if e == 2 and b < 2:
                        b += 1
                        a.append(2)
                    else:
                        a.append(0)
                    a1.append(0)
                self.boarda1.append(a1)
                self.board.append(a)
        # значения по умолчанию
        self.left = 10
        self.top = 10
        self.colors = {2:pygame.Color('red'),
                       4:pygame.Color('blue'),
                       8:pygame.Color('purple'),
                       16:pygame.Color('orange'),
                       32:pygame.Color('pink'),
                       64:pygame.Color('green'),
                       128:(200, 200, 200),
                       256:(100, 200, 200),
                       512:(200, 100, 200),
                       1024:(200, 200, 100),
                       2048:(0, 200, 200)}
        self.cell_size = 100



    def render(self, a):
        for i in range(self.width):
            for j in range(self.height):
                pygame.draw.rect(screen, pygame.Color('white'), [(i * self.cell_size + self.left, j * self.cell_size + self.top), (self.cell_size, self.cell_size)], 2)




                if self.board[j][i] != 0:
                    pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                     [(i * self.cell_size + self.left + 2, j * self.cell_size + self.top + 2),
                                      (self.cell_size - 3, self.cell_size - 3)], 0)
                    text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                    screen.blit(text, (i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2,
                                       j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2))




    def checkendleft(self):
        self.move = 'left'
        save = []
        for i in range(self.height):
            for j in range(self.width):
                if self.board[i][j] == 0:
                    for t in range(j + 1, self.width):
                        if self.board[i][t] != 0:
                            self.boarda1[i][t] += 100
                else:
                    for t in range(j + 1, self.width):
                        if self.board[i][t] != self.board[i][j] and self.board[i][t] != 0:
                            break
                        if self.board[i][t] == self.board[i][j] and (i, j) not in save:
                            save.append((i, t))
                            for tg in range(t, self.width):
                                if self.board[i][tg] != 0:
                                    self.boarda1[i][tg] += 100
                            break


    def checkendright(self):
        self.move = 'right'
        save = []
        for i in range(self.height):
            for j in range(self.width - 1, -1, -1):
                if self.board[i][j] == 0:
                    for t in range(j, -1, -1):
                        if self.board[i][t] != 0:
                            self.boarda1[i][t] += 100
                else:
                    for t in range(j - 1, -1,-1):
                        if self.board[i][t] != self.board[i][j] and self.board[i][t] != 0:
                            break
                        if self.board[i][t] == self.board[i][j] and (i, j) not in save:
                            save.append((i, t))
                            for tg in range(t, -1, -1):
                                if self.board[i][tg] != 0:
                                    self.boarda1[i][tg] += 100
                            break

    def checkenup(self):
        self.move = 'up'
        save = []
        for j in range(self.width):
            for i in range(self.height):
                if self.board[i][j] == 0:
                    for t in range(i + 1, self.height):
                        if self.board[t][j] != 0:
                            self.boarda1[t][j] += 100
                else:
                    for t in range(i + 1, self.height):
                        if self.board[t][j] != self.board[i][j] and self.board[t][j] != 0:
                            break
                        if self.board[t][j] == self.board[i][j] and (i, j) not in save:
                            save.append((t, j))
                            for tg in range(t, self.height):
                                if self.board[tg][j] != 0:
                                    self.boarda1[tg][j] += 100
                            break


    def checkendown(self):
        self.move = 'down'
        save = []
        for j in range(self.width):
            for i in range(self.height - 1, -1, -1):
                if self.board[i][j] == 0:
                    for t in range(i, -1, -1):
                        if self.board[t][j] != 0:
                            self.boarda1[t][j] += 100
                else:
                    for t in range(i - 1, -1,-1):
                        if self.board[t][j] != self.board[i][j] and self.board[t][j] != 0:
                            break
                        if self.board[t][j] == self.board[i][j] and (i, j) not in save:
                            save.append((t, j))
                            for tg in range(t, -1, -1):
                                if self.board[tg][j] != 0:
                                    self.boarda1[tg][j] += 100
                            break


    def move1(self):
        t = False
        self.y += 1
        for i in range(self.width):
            for j in range(self.height):
                if self.boarda1[j][i] - self.y > 0:
                    t = True
        if t:
            if self.move == 'left':
                for i in range(self.width):
                    for j in range(self.height):
                        pygame.draw.rect(screen, pygame.Color('white'), [(i * self.cell_size + self.left, j * self.cell_size + self.top), (self.cell_size, self.cell_size)], 2)

                        if self.boarda1[j][i] - self.y > 0:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2 - self.y, j * self.cell_size + self.top + 2),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2 - self.y,
                                                   j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2))


                        else:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2 - self.boarda1[j][i],
                                                   j * self.cell_size + self.top + 2),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (
                                i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2 - self.boarda1[j][i],
                                j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2))




            elif self.move == 'right':
                for i in range(self.width):
                    for j in range(self.height):
                        pygame.draw.rect(screen, pygame.Color('white'), [(i * self.cell_size + self.left, j * self.cell_size + self.top), (self.cell_size, self.cell_size)], 2)

                        if self.boarda1[j][i] - self.y > 0:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2 + self.y, j * self.cell_size + self.top + 2),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2 + self.y,
                                                   j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2))


                        else:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2 + self.boarda1[j][i],
                                                   j * self.cell_size + self.top + 2),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (
                                i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2 + self.boarda1[j][i],
                                j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2))




            elif self.move == 'down':
                for i in range(self.width):
                    for j in range(self.height):
                        pygame.draw.rect(screen, pygame.Color('white'), [(i * self.cell_size + self.left, j * self.cell_size + self.top), (self.cell_size, self.cell_size)], 2)

                        if self.boarda1[j][i] - self.y > 0:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2, j * self.cell_size + self.top + 2 + self.y),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2,
                                                   j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2 + self.y))


                        else:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2,
                                                   j * self.cell_size + self.top + 2 + self.boarda1[j][i]),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (
                                i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2,
                                j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2 + self.boarda1[j][i]))


            elif self.move == 'up':
                for i in range(self.width):
                    for j in range(self.height):
                        pygame.draw.rect(screen, pygame.Color('white'), [(i * self.cell_size + self.left, j * self.cell_size + self.top), (self.cell_size, self.cell_size)], 2)

                        if self.boarda1[j][i] - self.y > 0:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2, j * self.cell_size + self.top + 2 - self.y),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2,
                                                   j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2 - self.y))


                        else:
                            if self.board[j][i] != 0:
                                pygame.draw.rect(screen, self.colors[self.board[j][i]],
                                                 [(i * self.cell_size + self.left + 2,
                                                   j * self.cell_size + self.top + 2 - self.boarda1[j][i]),
                                                  (self.cell_size - 3, self.cell_size - 3)], 0)
                                text = font.render(str(self.board[j][i]), 1, (pygame.Color("white")))
                                screen.blit(text, (
                                i * self.cell_size + self.left + 2 + (100 - text.get_width()) // 2,
                                j * self.cell_size + self.top + 2 + (100 - text.get_height()) // 2 - self.boarda1[j][i]))



            return False
        else:
            self.y = 0
            print(self.boarda1)
            self.boardnew = [[0 for i in range(self.width)] for j in range(self.height)]
            if self.move == 'left':
                for i in range(self.height):
                    for j in range(0, self.width):
                        if self.boarda1[i][j] != 0:
                            print(self.boardnew[i][j - self.boarda1[i][j] // 100])
                            if self.boardnew[i][j - self.boarda1[i][j] // 100] == self.board[i][j]:
                                self.boardnew[i][j - self.boarda1[i][j] // 100] = self.board[i][j] * 2
                            else:
                                self.boardnew[i][j - self.boarda1[i][j] // 100] = self.board[i][j]
                        else:
                            self.boardnew[i][j] = self.board[i][j]
            elif self.move == 'right':
                for i in range(self.height):
                    for j in range(self.width - 1, -1, -1):
                        if self.boarda1[i][j] != 0:
                            print(self.boardnew[i][j + self.boarda1[i][j] // 100])
                            if self.boardnew[i][j + self.boarda1[i][j] // 100] == self.board[i][j]:
                                self.boardnew[i][j + self.boarda1[i][j] // 100] = self.board[i][j] * 2
                            else:
                                self.boardnew[i][j + self.boarda1[i][j] // 100] = self.board[i][j]
                        else:
                            self.boardnew[i][j] = self.board[i][j]
            elif self.move == 'up':
                for i in range(self.height):
                    for j in range(self.width):
                        if self.boarda1[i][j] != 0:
                            print(self.boardnew[i - self.boarda1[i][j] // 100][j])
                            if self.boardnew[i - self.boarda1[i][j] // 100][j] == self.board[i][j]:
                                self.boardnew[i - self.boarda1[i][j] // 100][j] = self.board[i][j] * 2
                            else:
                                self.boardnew[i - self.boarda1[i][j] // 100][j] = self.board[i][j]
                        else:
                            self.boardnew[i][j] = self.board[i][j]

            elif self.move == 'down':
                for i in range(self.height - 1, -1, -1):
                    for j in range(self.width):
                        if self.boarda1[i][j] != 0:
                            print(self.boardnew[i + self.boarda1[i][j] // 100][j])
                            if self.boardnew[i + self.boarda1[i][j] // 100][j] == self.board[i][j]:
                                self.boardnew[i + self.boarda1[i][j] // 100][j] = self.board[i][j] * 2
                            else:
                                self.boardnew[i + self.boarda1[i][j] // 100][j] = self.board[i][j]
                        else:
                            self.boardnew[i][j] = self.board[i][j]
            self.board = copy.deepcopy(self.boardnew)
            self.boarda1 = [[0 for i in range(self.width)] for j in range(self.height)]

            ty = True
            for i in range(self.width):
                for j in range(self.height):
                    if self.board[i][j] == 0:
                        ty = False
            if ty:
                return True

            i = random.randint(0, 3)
            j = random.randint(0, 3)
            while self.board[i][j] != 0:
                i = random.randint(0, 3)
                j = random.randint(0, 3)

            self.board[i][j] = 2

            return True






# screen — холст, на котором нужно рисовать:
# размеры окна:





b = 0
pygame.init()
font = pygame.font.Font(None, 50)
screen = pygame.display.set_mode((500, 500))
clock = pygame.time.Clock()
fps = 1150
board = Board(4, 4)
running = True
a = (0, 0)
f = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if event.type == pygame.KEYDOWN and f:
            if event.key == pygame.K_LEFT:
                board.checkendleft()
                f = False
            elif event.key == pygame.K_RIGHT:
                board.checkendright()
                f = False

            elif event.key == pygame.K_UP:
                board.checkenup()
                f = False

            elif event.key == pygame.K_DOWN:
                board.checkendown()
                f = False
    screen.fill((0, 0, 0))
    if f:
        board.render(a)
    else:
        f = board.move1()

    clock.tick(fps)
    pygame.display.flip()
