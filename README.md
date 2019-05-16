# SimplePythonProjectGame
Bubble sort learning game


import pygame
import random
import sys
import copy

class column:
    def __new__(cls, *args, **kwargs):
        return object.__new__(cls)
    def __init__(self,surface, x, y,number,r,g,b):
        self.number = number
        self.x = x
        self.y = y
        self.surface = surface
        self.r = r
        self.g = g
        self.b = b
    def col_dis(self):
        pygame.draw.rect(self.surface, (self.r,self.g,self.b), pygame.Rect(self.x, self.y, 25, -15*self.number))
        return self.surface
    def get_number(self):
        return self.number
    def set_number(self, a):
        self.number = a
    def set_col(self, r, g ,b):
        self.r = r
        self.g = g
        self.b = b



            
        
screen = pygame.display.set_mode([1000,200])
cursor = pygame.cursors.compile(pygame.cursors.textmarker_strings)
pygame.mouse.set_cursor(*pygame.cursors.broken_x)

def intro(obj):
    global screen
    a = 1
    for passnum in range(len(obj)-1,0,-1):
        
        for i in range(passnum):
            pygame.time.wait(500)
            screen.fill((200, 200, 200))
            for x in range(len(objlist)):
                screen = obj[x].col_dis()
            pygame.display.flip()
            pygame.time.wait(50)
            screen.fill((230, 230, 230))
            for x in range(len(objlist)):
                obj[x].set_col(0,0,0)
                screen = obj[x].col_dis()
            pygame.display.flip()
            obj[i].set_col(150,0,0)
            obj[i+1].set_col(150,0,0)
            if obj[i].get_number() > obj[i+1].get_number():
                
                temp = obj[i].get_number()
                obj[i] .set_number(obj[i+1].get_number())
                obj[i+1].set_number (temp)

objlist = []
intrList = []
for x in range(28):
        a = x
        rand = random.randrange(1,10)
        x = column(screen,30* a + 90, 180, rand , 10, 10 ,10)
        z = column(screen,30* a + 90, 180, rand , 10, 10 ,10)
        objlist.append(x)
        intrList.append(z)

pygame.display.flip()

intro(intrList)



while 1:
    pygame.time.wait(100)
    screen.fill((200, 200, 200))
    for x in range(len(objlist)):
        screen = objlist[x].col_dis()
    for event in pygame.event.get():
        if event.type == pygame.QUIT: sys.exit()
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_ESCAPE: sys.exit()
    pygame.display.flip()
