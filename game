import pygame
import pyganim
import math
import time
import random
import os
from pygame.locals import *

#Initialize the game
os.environ['SDL_VIDEO_CENTERED'] = '1'
pygame.init()
pygame.mixer.init()

width, height = 640, 480

screen=pygame.display.set_mode((width, height))
keys = [False, False, False, False,False]

acc=[0,0]
laserbullets=[]
badguys=[]
badguys2=[]
playerpos=[350,217]
rocketypos = 160
badtimer=1000
badtimer2=1500
badtimer1=0
badtimer12=0
badmaxtime=500
badmaxtime2=500
healthvalue=194
rocketlaunch = False
rocketsound = True
player_shoot = False
countdown1 = True
countdown2 = True
countdown3 = True
player_facing = "RIGHT"
player_move = " "
    
#Load images
rocket = pygame.image.load("resources/images/rocket.png")
rocketl = pygame.image.load("resources/images/rocketl.png")
lbullet = pygame.image.load("resources/images/bullet.png")
grass = pygame.image.load("resources/images/grass.png")
sky = pygame.image.load("resources/images/sky.png")
healthbar = pygame.image.load("resources/images/healthbar.png")
health = pygame.image.load("resources/images/health.png")
gameover = pygame.image.load("resources/images/gameover.png")
youwin = pygame.image.load("resources/images/youwin.png")

player = pygame.image.load("resources/images/idle.png")
player2 = pygame.image.load("resources/images/idle2.png")
player3 = pygame.image.load("resources/images/idle3.png")
player4 = pygame.image.load("resources/images/idle4.png")
player5 = pygame.image.load("resources/images/idle5.png")
player6 = pygame.image.load("resources/images/idle6.png")
player7 = pygame.image.load("resources/images/idle7.png")
player8 = pygame.image.load("resources/images/idle8.png")

move1 = pygame.image.load("resources/images/move1.png")
move2 = pygame.image.load("resources/images/move2.png")
move3 = pygame.image.load("resources/images/move3.png")
move4 = pygame.image.load("resources/images/move4.png")
move5 = pygame.image.load("resources/images/move5.png")
move6 = pygame.image.load("resources/images/move6.png")

shoot1 = pygame.image.load("resources/images/shoot1.png")
shoot2 = pygame.image.load("resources/images/shoot2.png")
shoot3 = pygame.image.load("resources/images/shoot3.png")

bgm1 = pygame.image.load("resources/images/bgm1.png")
bgm2 = pygame.image.load("resources/images/bgm2.png")
bgm3 = pygame.image.load("resources/images/bgm3.png")
bgm4 = pygame.image.load("resources/images/bgm4.png")
bgm5 = pygame.image.load("resources/images/bgm5.png")
bgm6 = pygame.image.load("resources/images/bgm6.png")
bgm7 = pygame.image.load("resources/images/bgm7.png")
bgm8 = pygame.image.load("resources/images/bgm8.png")

#Flip images
playerf = pygame.transform.flip(player, True, False)
player2f = pygame.transform.flip(player2, True, False)
player3f = pygame.transform.flip(player3, True, False)
player4f = pygame.transform.flip(player4, True, False)
player5f = pygame.transform.flip(player5, True, False)
player6f = pygame.transform.flip(player6, True, False)
player7f = pygame.transform.flip(player7, True, False)
player8f = pygame.transform.flip(player8, True, False)

move1f = pygame.transform.flip(move1, True, False)
move2f = pygame.transform.flip(move2, True, False)
move3f = pygame.transform.flip(move3, True, False)
move4f = pygame.transform.flip(move4, True, False)
move5f = pygame.transform.flip(move5, True, False)
move6f = pygame.transform.flip(move6, True, False)

shoot1f = pygame.transform.flip(shoot1, True, False)
shoot2f = pygame.transform.flip(shoot2, True, False)
shoot3f = pygame.transform.flip(shoot3, True, False)

bgm1f = pygame.transform.flip(bgm1, True, False)
bgm2f = pygame.transform.flip(bgm2, True, False)
bgm3f = pygame.transform.flip(bgm3, True, False)
bgm4f = pygame.transform.flip(bgm4, True, False)
bgm5f = pygame.transform.flip(bgm5, True, False)
bgm6f = pygame.transform.flip(bgm6, True, False)
bgm7f = pygame.transform.flip(bgm7, True, False)
bgm8f = pygame.transform.flip(bgm8, True, False)

#initialize animation
boltAnim = pyganim.PygAnimation([(player, 150),(player2, 150),(player3, 150),(player4, 150)
                                ,(player5, 150),(player6, 150),(player7, 150),(player8, 150)])

boltAnimf = pyganim.PygAnimation([(playerf, 150),(player2f, 150),(player3f, 150),(player4f, 150)
                                ,(player5f, 150),(player6f, 150),(player7f, 150),(player8f, 150)])

boltAnim_m = pyganim.PygAnimation([(move1, 150),(move2, 150),(move3, 150),(move4, 150),(move5, 150),(move6, 150)])
boltAnim_mf = pyganim.PygAnimation([(move1f, 150),(move2f, 150),(move3f, 150),(move4f, 150),(move5f, 150),(move6f, 150)])

boltAnim_s = pyganim.PygAnimation([(shoot1, 150),(shoot2, 150),(shoot3, 150)])
boltAnim_sf = pyganim.PygAnimation([(shoot1f, 150),(shoot2f, 150),(shoot3f, 150)])

boltAnim_bg = pyganim.PygAnimation([(bgm1, 150),(bgm2, 150),(bgm3, 150),(bgm4, 150)
                                ,(bgm5, 150),(bgm6, 150),(bgm7, 150),(bgm8, 150)])

boltAnim_bgf = pyganim.PygAnimation([(bgm1f, 150),(bgm2f, 150),(bgm3f, 150),(bgm4f, 150)
                                ,(bgm5f, 150),(bgm6f, 150),(bgm7f, 150),(bgm8f, 150)])
boltAnim.play()
boltAnimf.play()
boltAnim_m.play()
boltAnim_mf.play()
boltAnim_s.play()
boltAnim_sf.play()
boltAnim_bg.play()
boltAnim_bgf.play()

#Load audio
hit = pygame.mixer.Sound("resources/audio/explode.wav")
enemy = pygame.mixer.Sound("resources/audio/enemy.wav")
shoot = pygame.mixer.Sound("resources/audio/shoot.wav")
laugh = pygame.mixer.Sound("resources/audio/laugh.wav")
robotvoice = pygame.mixer.Sound("resources/audio/robotvoice.wav")
countdown = pygame.mixer.Sound("resources/audio/countdown.wav")
launch = pygame.mixer.Sound("resources/audio/launch2.wav")
hit.set_volume(0.05)
enemy.set_volume(0.03)
shoot.set_volume(0.03)
laugh.set_volume(0.05)
robotvoice.set_volume(0.05)
countdown.set_volume(0.09)
launch.set_volume(0.07)
pygame.mixer.music.load('resources/audio/moonlight.wav')
pygame.mixer.music.play(-1, 0.0)
pygame.mixer.music.set_volume(0.25)


running = 1
exitcode = 0
while 1:
    badtimer-=1
    badtimer2-=1
    
    #clear the screen before drawing it again
    screen.fill((0, 0, 0))
    #draw the screen elements

    for x in range(width//grass.get_width()+1):
        for y in range(2):
            screen.blit(grass,(x*100,(y+3)*100))
            
    for x in range(1):
        for y in range(1):
            screen.blit(sky,(x*100,(y)*100))
  
    if rocketlaunch == False:
        screen.blit(rocket,(270,180))
    else: 
        screen.blit(rocketl,(270,rocketypos))
        
    if player_move == "MOVE_RIGHT" and player_shoot == True:
        boltAnim_s.blit(screen, playerpos)
    elif player_move == "MOVE_LEFT" and player_shoot == True:
        boltAnim_sf.blit(screen, playerpos)
    elif  player_move == "MOVE_LEFT":
        boltAnim_mf.blit(screen, playerpos)
    elif player_move == "MOVE_RIGHT":
        boltAnim_m.blit(screen, playerpos)
    elif player_facing == "RIGHT" and player_shoot == True:
        boltAnim_s.blit(screen, playerpos)
    elif player_facing == "LEFT" and player_shoot == True:
        boltAnim_sf.blit(screen, playerpos)
    elif player_facing == "RIGHT":
        boltAnim.blit(screen, playerpos)
    elif player_facing == "LEFT":
        boltAnimf.blit(screen, playerpos)
    player_shoot
     
    #get player center point
    playerpos1 = (playerpos[0]-80/2, playerpos[1]-95/2)


    #Draw bullets
    for bullet in laserbullets:
        index=0
        valx=math.cos(bullet[0])*8
        #valy=math.sin(bullet[0])*10
        bullet[1]+=valx
        #bullet[2]+=valy
        if bullet[1]<-64 or bullet[1]>640: #or bullet[2]<-64 or bullet[2]>480:
            laserbullets.pop(index)
        index+=1
        for projectile in laserbullets:
            if player_facing == "LEFT":
                lbullet1 = pygame.transform.rotate(lbullet, 180)
                screen.blit(lbullet1, (projectile[1]+40, projectile[2]+40))
            else:    
                screen.blit(lbullet, (projectile[1]+40, projectile[2]+40))

                
    #Draw robots on the right side
    if badtimer==0:
        badguys.append([680, 223])
        badtimer=random.randint(101,badmaxtime)-(badtimer1*2)
        if badtimer1>=50:
            badtimer1=50
            badmaxtime=300
        else:
            badtimer1+=4
    index=0
    for badguy in badguys:
        if badguy[0]<-64:
            badguys.pop(index)
        badguy[0]-=random.uniform(0.5, 1.2)
        
        #check collide with rocket
        badrect= pygame.Rect(badguy[0]+15,200,50,80)
        badrect.top=badguy[1]
        badrect.left=badguy[0]
        rocketrect = pygame.Rect(rocket.get_rect())
        rocketrect.top=180
        rocketrect.left=307
        rocketrect.width=20
        if rocketlaunch == False:
            if badrect.colliderect(rocketrect):
                hit.play()
                healthvalue -= random.randint(30,65)
                badguys.pop(index)
            
        #check collide with bullets
        index1=0
        for bullet in laserbullets:
            bullrect=pygame.Rect(lbullet.get_rect())
            bullrect.left=bullet[1]+10
            bullrect.top=bullet[2]+40
            bullrect.width=30
            bullrect.height=30
            #pygame.draw.rect(screen, (100, 100, 255), bullrect,2)
            if badrect.colliderect(bullrect):
                enemy.play()
                if random.randint(0,10) == 1:
                    laugh.play()
                acc[0]+=1
                badguys.pop(index)
                laserbullets.pop(index1)
            index1+=1
            
        index+=1
    for badguy in badguys:
        boltAnim_bgf.blit(screen, badguy)
    
        
    #Draw robots on the left side    
    if badtimer2==0:
        badguys2.append([-40, 223])
        if random.randint(0,10) == 1:
            robotvoice.play()
        badtimer2=random.randint(101,badmaxtime2)-(badtimer12*2)
        if badtimer12>=50:
            badtimer12=50
            badmaxtime2=250
        else:
            badtimer12+=2
    index=0
    for badguy2 in badguys2:
        if badguy2[0]>680:
            badguys2.pop(index)
        badguy2[0]+=random.uniform(0.5, 1.2)
        
        #check collide with rocket
        badrect2= pygame.Rect(badguy2[0]+15,200,50,80)
        badrect2.top=badguy2[1]
        badrect2.left=badguy2[0]
        rocketrect = pygame.Rect(rocket.get_rect())
        rocketrect.top=180
        rocketrect.left=300
        rocketrect.width=20
        #pygame.draw.rect(screen, (100, 100, 255), rocketrect,2)
        if rocketlaunch == False:
            if badrect2.colliderect(rocketrect):
                hit.play()
                healthvalue -= random.randint(30,65)
                badguys2.pop(index)
        
        #check collide with bullets
        index1=0
        for bullet in laserbullets:
            bullrect=pygame.Rect(lbullet.get_rect())
            bullrect.left=bullet[1]+65
            bullrect.top=bullet[2]+40
            bullrect.width=30
            bullrect.height=30
            if badrect2.colliderect(bullrect):
                enemy.play()
                acc[0]+=1
                badguys2.pop(index)
                laserbullets.pop(index1)
            index1+=1
            
        index+=1
    for badguy2 in badguys2:
        boltAnim_bg.blit(screen, badguy2)
        
    #Draw timer
    font = pygame.font.Font(None, 24)
    survivedtext = font.render(str(int((67000-pygame.time.get_ticks())/60000))+":"+str(int((67000-pygame.time.get_ticks())/1000%60)).zfill(2), True, (0,0,0))
    if (pygame.time.get_ticks()>64000 and pygame.time.get_ticks()<64100) and countdown1:
        pygame.mixer.music.stop()
        countdown1 = False
        countdown.play()
    if (pygame.time.get_ticks()>65000 and pygame.time.get_ticks()<65100) and countdown2:
        countdown2 = False
        countdown.play()
    if (pygame.time.get_ticks()>66000 and pygame.time.get_ticks()<66100) and countdown3:
        countdown3 = False
        countdown.play()
        
    textRect = survivedtext.get_rect()
    textRect.topright=[635,5]
    screen.blit(survivedtext, textRect)
   
    #Draw healthbar
    screen.blit(healthbar, (5,5))
    for health1 in range(healthvalue):
        screen.blit(health, (health1+8,8))
        
    

    #update the screen
    pygame.display.flip()
    #loop through the events
    for event in pygame.event.get():
        #check if the event is the X button 
        if event.type==pygame.QUIT:
            pygame.quit() 
            exit(0) 
        
        #Check keyboard button pressed
        if event.type == pygame.KEYDOWN:
            if event.key==K_UP:
                keys[0]=False
            elif event.key==K_LEFT:
                keys[1]=True
                player_move = "MOVE_LEFT"
                player_facing = "LEFT"
            elif event.key==K_DOWN:
                keys[2]=False
            elif event.key==K_RIGHT:
                keys[3]=True
                player_move = "MOVE_RIGHT"
                player_facing = "RIGHT"
            elif event.key==K_x:
                shoot.play()
                acc[1]+=1
                player_shoot = True
                if player_facing == "RIGHT" or  player_move == "MOVE_RIGHT":
                    laserbullets.append([0.0,playerpos1[0]+35,playerpos1[1]+32])
                elif player_facing == "LEFT" or  player_move == "MOVE_LEFT":
                    laserbullets.append([3.1324854372626767,playerpos1[0]+20,playerpos1[1]+32])
        
        #Check keyboard button released
        if event.type == pygame.KEYUP:
            if event.key==pygame.K_UP:
                keys[0]=False
            elif event.key==pygame.K_LEFT:
                keys[1]=False       
                player_move = ""
            elif event.key==pygame.K_DOWN:
                keys[2]=False
            elif event.key==pygame.K_RIGHT:
                keys[3]=False
                
                player_move = ""
            elif event.key==pygame.K_x:
                
                keys[4]=False
                player_shoot = False
             
    #Move player depending on keyboard keys pressed
    if keys[0]:
        playerpos[1]-=1 
    elif keys[2]:
        playerpos[1]+=1
    if keys[1]:
        playerpos[0]-=1
    elif keys[3]:
        playerpos[0]+=1

    #Check winning or losing
    if pygame.time.get_ticks()>=67000:
        running=0
        exitcode=1
    if healthvalue<=0:
        running=0
        exitcode=0
    if acc[1]!=0:
        accuracy=int(acc[0]*1.0/acc[1]*100)
    else:
        accuracy=0
        
        
    #losing display        
    if exitcode == 0 and running==0:
        pygame.font.init()
        font = pygame.font.Font(None, 24)
        text = font.render("Accuracy: "+str(accuracy)+"%", True, (255,255,255))
        textRect = text.get_rect()
        textRect.centerx = screen.get_rect().centerx
        textRect.centery = screen.get_rect().centery+24
        screen.blit(gameover, (0,0))
        screen.blit(text, textRect)
        
        while 1:
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    pygame.quit()
                    exit(0)
            pygame.display.flip()
    #winning display      
    if exitcode == 1 and running==0: 
        rocketlaunch = True
        rocketypos -=0.5        
        if rocketsound:
            launch.play()
            rocketsound = False
        if rocketypos < 10:   
            pygame.font.init()
            font = pygame.font.Font(None, 24)
            text = font.render("Accuracy: "+str(accuracy)+"%", True, (255,255,255))
            textRect = text.get_rect()
            textRect.centerx = screen.get_rect().centerx
            textRect.centery = screen.get_rect().centery+24
            screen.blit(youwin, (0,0))
            screen.blit(text, textRect)

            while 1:
                for event in pygame.event.get():
                    if event.type == pygame.QUIT:
                        pygame.quit()
                        exit(0)
                pygame.display.flip()


 

