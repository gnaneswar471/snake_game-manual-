# snake_game-manual-
# snake-game
import random

width=10
height=10

def print_board(snake,food):
    for y in range(height):
        for x in range(width):
            if [x,y]==food:
                print('🥚',end='')
            elif[x,y] in snake:
                print('🐛',end='')
            else:
                print('.',end=' ')
        print()
    print()  
def move_snake(snake,direction):
    head=snake[-1]
    if direction=='up':
        new_head=[head[0],head[1]-1]
    elif direction=='down':
        new_head=[head[0],head[1]+1]
    elif direction=='left':
        new_head=[head[0]-1,head[1]]
    elif direction=='right':
        new_head=[head[0]+1,head[1]]
    else:
        print("Invalid direction,use up/down/right/left.")
        return snake,False
        
#wall colide conditions
    if new_head[0]<0 or new_head[0]>=width or new_head[1]<0 or new_head[1]>=height:
        return snake,'wall'
#self colide conditions
    if new_head in snake:
        return snake,'self'
        
    snake.append(new_head)
    return snake,new_head
def place_food(snake):
    while True:
        x=random.randint(0,width-1)
        y=random.randint(0,height-1)
        if [x,y] not in snake:
            return[x,y]
            
def snake_game():
    snake=[[5,5]]
    food=place_food(snake)
    score=0
    while True:
        print_board(snake,food)
        print("Score:",score)
        direction=input("ENTER direction(up/down/left/right):")
        snake,result=move_snake(snake,direction)
        if result=='wall':
            print("You hit the wall,Game over!!!")
            break
        elif result=='self':
            print("You hit yourself....Game over!!!")
            break
        elif result==food:
            score+=1
            food=place_food(snake)
        else:
            snake.pop(0)
    print("Final score:",score)
snake_game()               
OUTPUT:
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . 🐛. . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . 🐛. . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . 🐛. . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . 🐛. . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛. . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛. . . . . . . .
. 🥚. . . . . . . .

Score: 0
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛. . . . . . . .
. 🐛. . . . . . . .

Score: 1
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
🐛🐛. . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
🐛. . . . . . . . .
🐛. . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
🐛. . . . . . . . .
🐛. . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
🐛. . . . . . . . .
🐛. . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
🐛. . . . . . . . .
🐛. . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
🐛. . . . . . . . .
🐛. . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . 🥚. . .
. . . . . . . . . .
🐛. . . . . . . . .
🐛. . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . 🥚. . .
🐛. . . . . . . . .
🐛. . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
🐛. . . . . 🥚. . .
🐛. . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
🐛🐛. . . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. 🐛🐛. . . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . 🐛🐛. . 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . 🐛🐛. 🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . 🐛🐛🥚. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 1
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . 🐛🐛🐛. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . 🐛🐛. . .
. . . . . . 🐛. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . 🐛. . .
. . . . . . 🐛. . .
. . . . . . 🐛. . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . 🐛. . .
. . . . . . 🐛. . .
. . . . . . 🐛. . .
. . . . . . . . . .
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . 🐛. . .
. . . . . . 🐛. . .
. . . . . . 🐛. . .
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):down
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . 🐛. . .
. . . . . . 🐛. . .
. 🥚. . . . 🐛. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . 🐛. . .
. 🥚. . . 🐛🐛. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. . 🐛🐛🐛. . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚. 🐛🐛🐛. . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🥚🐛🐛🐛. . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 2
ENTER direction(up/down/left/right):left
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . 🥚.
. 🐛🐛🐛🐛. . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛. . . . . . 🥚.
. 🐛🐛🐛. . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛🐛. . . . . 🥚.
. 🐛🐛. . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛🐛🐛. . . . 🥚.
. 🐛. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. 🐛🐛🐛🐛. . . 🥚.
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . 🐛🐛🐛🐛. . 🥚.
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . 🐛🐛🐛🐛. 🥚.
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . 🐛🐛🐛🐛🥚.
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 3
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . 🐛🐛🐛🐛🐛.
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 4
ENTER direction(up/down/left/right):up
. . . . . . . . . . 
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . 🐛.
. . . . . 🐛🐛🐛🐛.
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 4
ENTER direction(up/down/left/right):right
. . . . . . . . . . 
. 🥚. . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . 🐛🐛
. . . . . . 🐛🐛🐛.
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .
. . . . . . . . . .

Score: 4
ENTER direction(up/down/left/right):right
You hit the wall,Game over!!!
Final score: 4
