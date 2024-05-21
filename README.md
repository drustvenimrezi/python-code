# python-code
I made a fully functional flappy bird game using pygame in python


import random
import pygame.locals


pygame.init()



clock = pygame.time.Clock()
fps = 60

screen_width = 864
screen_height = 936
screen1 = pygame.display.set_mode((screen_width, screen_height))
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Flappy bird")

font = pygame.font.SysFont('Bauhaus 93', 60)
white = (255, 255, 255)

gr_scrl = 0
scrl_speed = 4
flying = False
game_over = False
pipe_gap = 185
pipe_freq = 1500
last_pipe = pygame.time.get_ticks() - pipe_freq
score = 0
pass_pipe = False
game_paused = False

bg = pygame.image.load('bg.png')
gr = pygame.image.load('gr.png')
bt_img = pygame.image.load('restart.png')
pause = pygame.image.load('pause.png')
menu = pygame.image.load('menu.png')

over = pygame.image.load('game over.png')
original_width = over.get_width()
original_height = over.get_height()
scale_factor = 5

start_button = pygame.image.load('start.png')
image_bird = pygame.image.load('bird1.png')
image = pygame.image.load('NASLOV.png')
gre = pygame.image.load('gr.png')
bge = pygame.image.load('bg.png')
screene = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Flappy bird")

original_widthe = image.get_width()
original_heighte = image.get_height()
original_width2 = image_bird.get_width()
original_height2 = image_bird.get_height()


scale_factore = 5
scale_factor2 = 1.5



font = pygame.font.SysFont('Bauhaus 93', 60)
text_col = (255, 255, 255)

def draw_bird(x, y):
    img = pygame.transform.scale(image, (original_widthe * scale_factore, original_heighte * scale_factore))
    screene.blit(img, (x, y))

def bird_menu(x, y):
    bird = pygame.transform.scale(image_bird, (original_width2 * scale_factor2, original_height2 * scale_factor2))
    screene.blit(bird, (x, y))

def  draw_text(text, font, text_col, x, y):
    img = font.render(text, True, text_col)
    screene.blit(img, (x, y))


class Play():
    def __init__(self, x, y, image):
        self.image = image
        self.rect = self.image.get_rect()
        self.rect.topleft = (x, y)
    def draw(self):
        action = False
        pos = pygame.mouse.get_pos()
        if self.rect.collidepoint(pos):
            if pygame.mouse.get_pressed()[0] == 1:
                action = True

        screen.blit(self.image, (self.rect.x, self.rect.y))

        return action

button = Play(335, 620, start_button)
def main_game():
    clock = pygame.time.Clock()
    fps = 60

    screen_width = 864
    screen_height = 936
    screen1 = pygame.display.set_mode((screen_width, screen_height))
    screen = pygame.display.set_mode((screen_width, screen_height))
    pygame.display.set_caption("Flappy bird")

    font = pygame.font.SysFont('Bauhaus 93', 60)
    white = (255, 255, 255)

    gr_scrl = 0
    scrl_speed = 4
    flying = False
    game_over = False
    pipe_gap = 185
    pipe_freq = 1500
    last_pipe = pygame.time.get_ticks() - pipe_freq
    score = 0
    pass_pipe = False
    game_paused = False

    bg = pygame.image.load('bg.png')
    gr = pygame.image.load('gr.png')
    bt_img = pygame.image.load('restart.png')
    pause = pygame.image.load('pause.png')
    menu = pygame.image.load('menu.png')

    over = pygame.image.load('game over.png')
    original_width = over.get_width()
    original_height = over.get_height()
    scale_factor = 5

    def draw_text(text, font, text_col, x, y):
        img = font.render(text, True, text_col)
        screen.blit(img, (x, y))

    def menu_screen():
        start_button = pygame.image.load('start.png')
        image_bird = pygame.image.load('bird1.png')
        image = pygame.image.load('NASLOV.png')
        gre = pygame.image.load('gr.png')
        bge = pygame.image.load('bg.png')
        screene = pygame.display.set_mode((screen_width, screen_height))
        pygame.display.set_caption("Flappy bird")

        original_widthe = image.get_width()
        original_heighte = image.get_height()
        original_width2 = image_bird.get_width()
        original_height2 = image_bird.get_height()

        scale_factore = 5
        scale_factor2 = 1.5

        font = pygame.font.SysFont('Bauhaus 93', 60)
        text_col = (255, 255, 255)

        def draw_bird(x, y):
            img = pygame.transform.scale(image, (original_widthe * scale_factore, original_heighte * scale_factore))
            screene.blit(img, (x, y))

        def bird_menu(x, y):
            bird = pygame.transform.scale(image_bird,
                                          (original_width2 * scale_factor2, original_height2 * scale_factor2))
            screene.blit(bird, (x, y))

        def draw_text(text, font, text_col, x, y):
            img = font.render(text, True, text_col)
            screene.blit(img, (x, y))

        class Play():
            def __init__(self, x, y, image):
                self.image = image
                self.rect = self.image.get_rect()
                self.rect.topleft = (x, y)

            def draw(self):
                action = False
                pos = pygame.mouse.get_pos()
                if self.rect.collidepoint(pos):
                    if pygame.mouse.get_pressed()[0] == 1:
                        action = True

                screen.blit(self.image, (self.rect.x, self.rect.y))

                return action

        button = Play(335, 620, start_button)

        runn = True
        while runn:
            screene.blit(bge, (0, 0))
            screene.blit(gre, (0, 768))

            draw_text('Made by Marko Ivanovski', font, text_col, 96, 837)
            draw_bird(200, 100)
            bird_menu(390, 380)
            if button.draw() == True:
                screen.blit(main_game())
            pygame.display.flip()

            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    runn = False

    def reset_game():
        pipe_group.empty()
        flappy.rect.x = 100
        flappy.rect.y = int(screen_height / 2)
        score = 0
        return score

    class Bird(pygame.sprite.Sprite):
        def __init__(self, x, y):
            pygame.sprite.Sprite.__init__(self)
            self.images = []
            self.index = 0
            self.counter = 0
            for num in range(1, 4):
                img = pygame.image.load(f'bird{num}.png')
                self.images.append(img)
            self.image = self.images[self.index]
            self.rect = self.image.get_rect()
            self.rect.center = [x, y]
            self.vel = 0
            self.clicked = False

        def update(self):

            if flying == True:
                self.vel += 0.5
                if self.vel > 8:
                    self.vel = 8
                if self.rect.bottom < 768:
                    self.rect.y += int(self.vel)

            if game_over == False:
                if pygame.mouse.get_pressed()[0] == 1 and self.clicked == False:
                    self.clicked = True
                    self.vel = -10
                if pygame.mouse.get_pressed()[0] == 0:
                    self.clicked = False

                self.counter += 1
                flap_cooldown = 5

                if self.counter > flap_cooldown:
                    self.counter = 0
                    self.index += 1
                    if self.index >= len(self.images):
                        self.index = 0
                self.image = self.images[self.index]

                self.image = pygame.transform.rotate(self.images[self.index], self.vel * -2)
            else:
                self.image = pygame.transform.rotate(self.images[self.index], -90)

    class Pipe(pygame.sprite.Sprite):
        def __init__(self, x, y, position):
            pygame.sprite.Sprite.__init__(self)
            self.image = pygame.image.load('pipe.png')
            self.rect = self.image.get_rect()
            if position == 1:
                self.image = pygame.transform.flip(self.image, False, True)
                self.rect.bottomleft = [x, y - int(pipe_gap / 2)]
            if position == -1:
                self.rect.topleft = [x, y + int(pipe_gap / 2)]

        def update(self):
            self.rect.x -= scrl_speed
            if self.rect.right < 0:
                self.kill()

    class Button():
        def __init__(self, x, y, image):
            self.image = image
            self.rect = self.image.get_rect()
            self.rect.topleft = (x, y)

        def draw(self):
            action = False
            pos = pygame.mouse.get_pos()
            if self.rect.collidepoint(pos):
                if pygame.mouse.get_pressed()[0] == 1:
                    action = True

            screen.blit(self.image, (self.rect.x, self.rect.y))

            return action

    def game_over_screen(x, y):
        a = pygame.transform.scale(over, (original_width * scale_factor, original_height * scale_factor))
        screen.blit(a, (x, y))

    bird_group = pygame.sprite.Group()
    pipe_group = pygame.sprite.Group()

    flappy = Bird(100, int(screen_height / 2))

    bird_group.add(flappy)

    button = Button(screen_width / 2 - 50, screen_height / 2 - 100, bt_img)

    run = True
    while run:

        clock.tick(fps)
        screen.blit(bg, (0, 0))
        bird_group.draw(screen)
        bird_group.update()
        pipe_group.draw(screen)

        screen.blit(gr, (gr_scrl, 768))

        if len(pipe_group) > 0:
            if bird_group.sprites()[0].rect.left > pipe_group.sprites()[0].rect.left \
                    and bird_group.sprites()[0].rect.right < pipe_group.sprites()[0].rect.right \
                    and pass_pipe == False:
                pass_pipe = True
            if pass_pipe == True:
                if bird_group.sprites()[0].rect.left > pipe_group.sprites()[0].rect.right:
                    score += 1
                    pass_pipe = False
        draw_text(str(score), font, white, int(screen_width / 2), 20)

        if pygame.sprite.groupcollide(bird_group, pipe_group, False, False) or flappy.rect.top < 0:
            game_over = True

        if flappy.rect.bottom > 768:
            game_over = True
            flying = False

        if game_over == False and flying == True:

            time_now = pygame.time.get_ticks()
            pipe_height = random.randint(-100, 100)
            if time_now - last_pipe > pipe_freq:
                btm_pipe = Pipe(screen_width, int(screen_height / 2) + pipe_height, -1)
                top_pipe = Pipe(screen_width, int(screen_height / 2) + pipe_height, 1)
                pipe_group.add(btm_pipe)
                pipe_group.add(top_pipe)
                last_pipe = time_now

            gr_scrl -= scrl_speed
            if abs(gr_scrl) > 35:
                gr_scrl = 0

            pipe_group.update()

        if game_over == True:
            game_over_screen(200, 100)
            if button.draw() == True:
                screen.blit(menu_screen())
                score = reset_game()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                run = False
            if event.type == pygame.MOUSEBUTTONDOWN and flying == False and game_over == False:
                flying = True

        pygame.display.update()
runn = True
while runn:
    screene.blit(bge, (0, 0))
    screene.blit(gre, (0, 768))

    draw_text('Made by Marko Ivanovski', font, text_col, 96, 837)
    draw_bird(200, 100)
    bird_menu(390, 380)
    if button.draw() == True:
        screen.blit(main_game())


    pygame.display.flip()

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            runn = False
pygame.quit()
def draw_text(text, font, text_col, x, y):
    img = font.render(text, True, text_col)
    screen.blit(img, (x, y))

def menu_screen():
    start_button = pygame.image.load('start1.png')
    image_bird = pygame.image.load('bird1.png')
    image = pygame.image.load('NASLOV.png')
    gre = pygame.image.load('gr.png')
    bge = pygame.image.load('bg.png')
    screene = pygame.display.set_mode((screen_width, screen_height))
    pygame.display.set_caption("Flappy bird")

    original_widthe = image.get_width()
    original_heighte = image.get_height()
    original_width2 = image_bird.get_width()
    original_height2 = image_bird.get_height()


    scale_factore = 5
    scale_factor2 = 1.5



    font = pygame.font.SysFont('Bauhaus 93', 60)
    text_col = (255, 255, 255)

    def draw_bird(x, y):
        img = pygame.transform.scale(image, (original_widthe * scale_factore, original_heighte * scale_factore))
        screene.blit(img, (x, y))

    def bird_menu(x, y):
        bird = pygame.transform.scale(image_bird, (original_width2 * scale_factor2, original_height2 * scale_factor2))
        screene.blit(bird, (x, y))

    def  draw_text(text, font, text_col, x, y):
        img = font.render(text, True, text_col)
        screene.blit(img, (x, y))


    class Play():
        def __init__(self, x, y, image):
            self.image = image
            self.rect = self.image.get_rect()
            self.rect.topleft = (x, y)
        def draw(self):
            action = False
            pos = pygame.mouse.get_pos()
            if self.rect.collidepoint(pos):
                if pygame.mouse.get_pressed()[0] == 1:
                    action = True

            screen.blit(self.image, (self.rect.x, self.rect.y))

            return action

    button = Play(335, 620, start_button)

    runn = True
    while runn:
        screene.blit(bge, (0, 0))
        screene.blit(gre, (0, 768))

        draw_text('Made by Marko Ivanovski', font, text_col, 96, 837)
        draw_bird(200, 100)
        bird_menu(390, 380)
        if button.draw() == True:
            screen.blit(main_game())
        pygame.display.flip()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                runn = False



def reset_game():
   pipe_group.empty()
   flappy.rect.x = 100
   flappy.rect.y = int(screen_height / 2)
   score = 0
   return score


class Bird(pygame.sprite.Sprite):
    def __init__(self, x, y):
        pygame.sprite.Sprite.__init__(self)
        self.images = []
        self.index = 0
        self.counter = 0
        for num in range(1, 4):
            img = pygame.image.load(f'bird{num}.png')
            self.images.append(img)
        self.image = self.images[self.index]
        self.rect = self.image.get_rect()
        self.rect.center = [x, y]
        self.vel = 0
        self.clicked = False



    def update(self):

        if flying == True:
            self.vel += 0.5
            if self.vel > 8:
                self.vel = 8
            if self.rect.bottom < 768:
                self.rect.y += int(self.vel)

        if game_over == False:
            if pygame.mouse.get_pressed()[0] == 1 and self.clicked == False:
                self.clicked = True
                self.vel = -10
            if pygame.mouse.get_pressed()[0] == 0:
                self.clicked = False

            self.counter += 1
            flap_cooldown = 5

            if self.counter > flap_cooldown:
                self.counter = 0
                self.index += 1
                if self.index >= len(self.images):
                    self.index = 0
            self.image = self.images[self.index]

            self.image = pygame.transform.rotate(self.images[self.index], self.vel * -2)
        else:
            self.image = pygame.transform.rotate(self.images[self.index], -90)



class Pipe(pygame.sprite.Sprite):
    def __init__(self, x, y, position):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load('pipe.png')
        self.rect = self.image.get_rect()
        if position == 1:
            self.image = pygame.transform.flip(self.image, False, True)
            self.rect.bottomleft = [x, y - int(pipe_gap / 2)]
        if position == -1:
            self.rect.topleft = [x, y + int(pipe_gap / 2)]

    def update(self):
        self.rect.x -= scrl_speed
        if self.rect.right < 0:
            self.kill()


class Button():
    def __init__(self, x, y, image):
        self.image = image
        self.rect = self.image.get_rect()
        self.rect.topleft = (x, y)
    def draw(self):
        action = False
        pos = pygame.mouse.get_pos()
        if self.rect.collidepoint(pos):
            if pygame.mouse.get_pressed()[0] == 1:
                action = True


        screen.blit(self.image, (self.rect.x, self.rect.y))

        return action

def game_over_screen(x, y):
    a = pygame.transform.scale(over, (original_width * scale_factor, original_height * scale_factor))
    screen.blit(a, (x, y))





bird_group = pygame.sprite.Group()
pipe_group = pygame.sprite.Group()

flappy = Bird(100, int(screen_height / 2))

bird_group.add(flappy)

button = Button(screen_width / 2 - 50, screen_height / 2 - 100, bt_img)


run = True
while run:

    clock.tick(fps)
    screen.blit(bg, (0,0))
    bird_group.draw(screen)
    bird_group.update()
    pipe_group.draw(screen)

    screen.blit(gr, (gr_scrl, 768))

    if len(pipe_group) > 0:
        if bird_group.sprites()[0].rect.left > pipe_group.sprites()[0].rect.left\
            and bird_group.sprites()[0].rect.right < pipe_group.sprites()[0].rect.right\
            and pass_pipe == False:
            pass_pipe = True
        if pass_pipe == True:
            if bird_group.sprites()[0].rect.left > pipe_group.sprites()[0].rect.right:
                score += 1
                pass_pipe = False
    draw_text(str(score), font, white, int(screen_width / 2), 20)



    if pygame.sprite.groupcollide(bird_group, pipe_group, False, False) or flappy.rect.top < 0:
        game_over = True

    if flappy.rect.bottom > 768:
        game_over = True
        flying = False


    if game_over == False and flying == True:

        time_now = pygame.time.get_ticks()
        pipe_height = random.randint(-100, 100)
        if time_now - last_pipe > pipe_freq:
            btm_pipe = Pipe(screen_width, int(screen_height / 2) + pipe_height, -1)
            top_pipe = Pipe(screen_width, int(screen_height / 2) + pipe_height, 1)
            pipe_group.add(btm_pipe)
            pipe_group.add(top_pipe)
            last_pipe = time_now


        gr_scrl -= scrl_speed
        if abs(gr_scrl) > 35:
            gr_scrl = 0





        pipe_group.update()

    if game_over == True:
        game_over_screen(200, 100)
        if button.draw() == True:
            screen.blit(menu_screen())
            score = reset_game()



    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        if event.type == pygame.MOUSEBUTTONDOWN and flying == False and game_over == False:
            flying = True

    pygame.display.update()

pygame.quit()

