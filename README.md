import pygame


LEFT = 0
RIGHT = 1
UP = 2
DOWN = 3
SPACE = 4
W = 5

class player:
    def __init__(self):


        self.xpos = 450
        self.ypos = 415
        self.vx = 0
        self.vy = 0
        self.direction = RIGHT

    def draw(self,screen):
        pygame.draw.rect(screen, (255, 0, 255), (self.xpos, self.ypos, 30, 30))

    def move(self, keys, map):

        #left right movement
        if keys[LEFT] == True:
            self.vx = -3
            self.direction = LEFT

        elif keys[RIGHT] == True:
            self.vx = 3
            self.direction = RIGHT

        else:
            self.vx = 0

        #up down movement
        if keys[UP] == True:
            self.vy = -3
            self.direction = UP

        elif keys[DOWN] == True:
            self.vy = 3
            self.direction = DOWN
        else:
            self.vy = 0

        print("player direction is ", self.direction)
        #left collision
        if map[int((self.ypos) / 50)][int((self.xpos - 10) / 50)] == 2 :
            self.xpos+=3

        #right collision
        if map[int((self.ypos) / 50)][int((self.xpos +30 + 5) / 50)] == 2 :
            self.xpos-=3

        #up colision
        if map[int((self.ypos-10) / 50)][int((self.xpos) / 50)] == 2 :
            self.ypos+=3

        #down collision
        if map[int((self.ypos+35) / 50)][int((self.xpos) / 50)] == 2 :
            self.ypos-=3
        

        self.xpos+=self.vx  #updates x position with x velocity
        self.ypos+=self.vy
