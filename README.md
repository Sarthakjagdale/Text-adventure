# Text-adventure
"""
Created on Thu oct 17 15:14:36 2019
@author: Sarthak.Jagdale


"""
"""
DocString:
A) Introduction:
    This game is based on a story that is fictional as well as factual,
    using the ASCII Tags taught during the class. It consists of three stages, 
    and also has defined functions for start, win, and lose. This game requires 
    honesty in the Trivia which is not graded, and having a small amount of 
    knowledge about the geography will be helpful.There are widgets in the game
    (Lose, Win, dropdowns)
    
    This game has a 5 parts
    1> Guess the Jumbled word.
    2> Read the question carefully.
    3> Guess the jumbled word
    4> Story combining the first three questions
    5> Infomative Trivia (element of surprise) 

B) Bugs : 
    ->  Just in case the drop down for question 1 doesn't work,
        kindly input for the dropdown.value which is assigned to
        user_guess1

"""

#Importing important packages(eg: widget etc).
import ipywidgets as ipw
from ipywidgets import *
import numpy as np
import time 
import sys


progress = ipw.IntProgress(
    value=0,
    min=0,
    max=8,
    step=1,
    description='Win:',
    bar_style='success', # 'success', 'info', 'warning', 'danger' or ''
    orientation='horizontal'
) 
lose = ipw.IntProgress(
    value=0,
    min=0,
    max=8,
    step=1,
    description='Lose:',
    bar_style='danger', # 'success', 'info', 'warning', 'danger' or ''
    orientation='horizontal'
) 

#Represent HTML variavbles for good effects:
correct_ans = HTML("<b><h1 style= 'color:GREEN'> Thats right! You're Smart... </h1></b>")
wrong_ans = HTML("<b><h1 style= 'color:RED'> Thats not right! </h1></b>")
correct_ans_1 = HTML("<b><h1 style= 'color:GREEN'> OOH! Thats right! </h1></b>")
wrong_ans_1 = HTML("<b><h1 style= 'color:RED'> That is indeed incorrect! </h1></b>")
correct_ans_geo = HTML("<b><h1 style= 'color:GREEN'> Thats awesome! You seem really good at geography. You just made the New President. Congrats! </h1></b>")
wrong_ans_geo = HTML("<b><h1 style= 'color:RED'>Looks like you're having geographical challanges. Nevertheless, try again! </h1></b>")
final_msg = HTML("<b><h1 style= 'color:GREEN'> You Win! but...</h1><b>")
#questions:
ques_1 = HTML("<b><h1 style= 'color:BLACK'> >>> Guess the 1st jumbled word(adjective). </h1></b>")
ques_2 = HTML("<b><h1 style= 'color:BLACK'> >>> Count and type the 2nd most recurring letter. </h1></b>")
ques_3 = HTML("<b><h1 style= 'color:BLACK'> >>> Type the correct jumbled name. </h1></b>")

#instructions:
intructions = HTML("<b><h1 style= 'color:BLUE'> Can you guess, what's in the box? </h1></b>")


intruction1 = HTML("<b><h1 style= 'color:BLACK'> Enter your Name, Age and Gender.</h1></b>")
intruction2 = HTML("<b><h1 style= 'color:BLUE'> Do give us a feedback to improve, Thank you!</h1></b>")
intruction3 = HTML("<b><h1 style= 'color:BLACK'> There are 3 levels of complexity, which goes Easy to Hard. </h1></b>")
intruction3a = HTML("<b><h1 style= 'color:BLACK'>   a) Level 1 consists of finding the jumbled words.</h1></b>")
intruction3b = HTML("<b><h1 style= 'color:BLACK'>   b) Level 2 consists of guessing the distance. </h1></b>")
intruction3c = HTML("<b><h1 style= 'color:BLACK'>   c) Level 3 has complex trivia questions. </h1></b>")
intruction4 = HTML("<b><h1 style= 'color:BLACK'> Most importantly, enjoy the game! </h1></b>")
display(intructions)
#display(intruction1)
#display(intruction2)
#display(intruction3)
#display(intruction3a)
#display(intruction3b)
#display(intruction3c)
#display(intruction4)
time.sleep(0.2)
input(prompt="< Press enter to start the game >\n")
print("-----------------------------------------------------------------")
#Use of Name as input and age slider widget(pre-defined value of range of 100 ) 
display(intruction1)
name = input(" Please enter your name:\n")
age = int(input(" Enter your age: \n"))
gender = input (" please enter your gender:\n ")
print("-----------------------------------------------------------------")
input(prompt=" < Press Enter to continue > ")
time.sleep(0.3)

def user(name, age): 
    """USER DETAILS"""
    usr_name = name 
    usr_age = age  
    if usr_age < 18:
        return name + f", you're {usr_age}? You are really young! grow up.. "
    elif usr_age < 29 and age > 17:
        return name + f", {usr_age} is the age to find your true soul mate. If you already have, then you're in good hands!!"
    else:
        return name + ", You are beautiful at heart. Keep spreading your wisdom. "
user_det = user(name, age)
print (user_det)
print("-----------------------------------------------------------------")
time.sleep(1)    
display(intruction4)

display(ques_1)
print("""      \nHint: Check the jumbled letters and select the best options possible. 
            
            
     | |                 | |         / _|                          
   __| |  _   _    ___   | |   ___  | |_   _ __   __      __  _ __ 
  / _` | | | | |  / _ \  | |  / _ \ |  _| | '_ \  \ \ /\ / / | '__|
 | (_| | | |_| | | (_) | | | |  __/ | |   | | | |  \ V  V /  | |   
  \__,_|  \__,_|  \___/  |_|  \___| |_|   |_| |_|   \_/\_/   |_|    
  
  """)
print("\t\tGuess the right word!\n")
drpdown1 = ipw.Dropdown(options = ['Select one', 'Owner', 'Fulldoner', 'Doner', 'Wonderful'], description = "Options:")
display(drpdown1)
time.sleep(3)
input(prompt="< Press Enter >" )

drpdown1.value = 'Wonderful'
user_guess1 = drpdown1.value
user_guess1



optn1 = True
while optn1 == True: 
    if user_guess1 != "Wonderful":
        display(wrong_ans)
        optn1 = False
    else: 
        display(correct_ans)
        optn1 = False
    
progress.value = 2
display(progress)


print("-------------------------------------------------------------------------------------------------------------------------")
display(ques_2)
print("""
Hint: Check the spelling twice.

 /$$$$$$$$ /$$   /$$ /$$$$$$$$ /$$$$$$$  /$$$$$$$$ /$$$$$$$  /$$$$$$$  /$$$$$$$$ /$$   /$$ /$$$$$$$$ /$$   /$$ /$$$$$$$ 
| $$_____/| $$$ | $$|__  $$__/| $$__  $$| $$_____/| $$__  $$| $$__  $$| $$_____/| $$$ | $$| $$_____/| $$  | $$| $$__  $$
| $$      | $$$$| $$   | $$   | $$  \ $$| $$      | $$  \ $$| $$  \ $$| $$      | $$$$| $$| $$      | $$  | $$| $$  \ $$
| $$$$$   | $$ $$ $$   | $$   | $$$$$$$/| $$$$$   | $$$$$$$/| $$$$$$$/| $$$$$   | $$ $$ $$| $$$$$   | $$  | $$| $$$$$$$/
| $$__/   | $$  $$$$   | $$   | $$__  $$| $$__/   | $$____/ | $$__  $$| $$__/   | $$  $$$$| $$__/   | $$  | $$| $$__  $$
| $$      | $$\  $$$   | $$   | $$  \ $$| $$      | $$      | $$  \ $$| $$      | $$\  $$$| $$      | $$  | $$| $$  \ $$
| $$$$$$$$| $$ \  $$   | $$   | $$  | $$| $$$$$$$$| $$      | $$  | $$| $$$$$$$$| $$ \  $$| $$$$$$$$|  $$$$$$/| $$  | $$
|________/|__/  \__/   |__/   |__/  |__/|________/|__/      |__/  |__/|________/|__/  \__/|________/ \______/ |__/  |__/                                                                                                                      
""")                                                                                                                        

#drpdown2 = ipw.Dropdown(options = ['Select one', 'Three', 'One', 'Four', 'Six'], description = "Options:")
#display(drpdown2)
time.sleep(0.2)



#user_guess2 = drpdown2.value
optn2 = 3
while optn2 > 0:
    user_sel2 = input('please type you answer! ')
    optn2 -= 1
    if user_sel2 == 'Three' or user_sel2 == '3' or user_sel2 == 'three' or user_sel2 == 'R' or user_sel2 == 'r':
        display(correct_ans_1)
        print("Nice Work")
        progress.value += 2
        display(progress)
        break
    else: 
        display(wrong_ans_1)
        lose.value += 2.9
        display(lose)
        print ("Restart the game" + f"chances left {optn2 - 1}")
        if optn2 == 0 or lose.value >= 8: 
            sys.exit(0)
        

time.sleep(0.2)
print("--------------------------------------------------------------------------------------")
display(ques_3)
print("""
                                    Hint: It is a famous name, however it’s also a duck!.

           _     _ _             
          | |   | | |            
  __ _  __| | __| | | ___  _ __  
 / _` |/ _` |/ _` | |/ _ \| '_ \ 
| (_| | (_| | (_| | | (_) | | | |
 \__,_|\__,_|\__,_|_|\___/|_| |_|
                                               

""")

    

word3 = 3
 

while word3 > 0:
    print("lets see how you perform\n")
    user_guess2 = input('please type you answer! ')
    word3 -= 1 
    if user_guess2 == 'DONALD' or user_guess2 == 'donald' or user_guess2 == 'Donald':
        display(correct_ans_1)
        print(f" You played well {name}, Congratulations!" )
        progress.value += 2
        display(progress)
        break 
        #final_msg.layout.visibility = "visible"
    else:
        display(wrong_ans_1)
        lose.value += 2.5
        display(lose)
        print(f" {name}, You have",(word3-1),"chances left" + "Also this time try with caps lock ON")
        if word3 == 0 or lose.value >= 8:
            print("You lost, Better Luck Next Time")
            sys.exit(0)
        

time.sleep(2)
input("< press enter to continue >")

print("---------------------------------------------------------------------------------------------------")
story = HTML("<b><h1 style= 'color:GREEN'> Donald who is a wonderful Entrepreneur had a divorce and wants to go as far as possible from San Fran.</h1></b>")
display(story)
#making dictionaries of dictionaries
major_city = {'Newyork' : {'distance in M': 2905},  'Atlanta': {'distance in M': 2465}, 'Washington D.C.': {'distance in M': 2825}, 'Tampa' : {' distance in M': 2909}} 

print("\n Now empathize with Donald and pick a city that’s the farthest in the US.\n")

Newyork, Atlanta,Washington D.C.

time.sleep(0.5)
sel4 = 2
while sel4 > 0:
    user_sel4 = input(" Select a City: ")
    sel4 -= 1

    if user_sel4 == '2' or user_sel4 == '' or user_sel4 == 'WASHINGTON D.C' or user_sel4 == 'Washington D.C' or user_sel4 == 'washington d c':
        display(correct_ans_geo)
        print("Washington D.C is one of the farthest but not the farthest. Reason you won: Because, Why not?  ")
        progress.value += 2
        break

    else:
        display(wrong_ans_geo)
        lose.value += 2.5 
        display(lose)
        print(" try again!")
        print(f" You have",(sel4-1),"chance left")
        if sel4 == 0 or lose.value >= 8:
            sys.exit("You lost, Better Luck Next Time")
        
        
print (major_city['Tampa'])
print (f" Wow {name}! you have helped Donald persoanally! ")

display(progress)
display(final_msg) 

print("Answer question below to know intresting facts! (This is not have any points!)\n") 

# final questions age and gender based!
if age <= 25:
    print(f"{name}, What color pant/dress are you wearing?")
    time.sleep(0.2)
    Tri_in1 = input()
    print(f"Did you know {Tri_in1} Color Can Trigger Deep Childhood Memories")
    if gender == 'female' or gender == 'Female' or gender == 'FEMALE' or gender == 'F' or gender == 'f':
        print("The average woman will eat 4 lb of lipstick in her lifetime.")
    else:
        print("""\n Did you know, You don’t have to necessarily possess a degree or a Ph.D. 
        Data science requires you to know the fundamentals of analytics.""")
elif age < 35 and age > 25 :
    print(f"\n {name} What is the amount of cash(USD) in your Wallet?")
    time.sleep(0.2)
    Tri_in2 = int(input()) 
    print(f"\n If you have ${Tri_in2} without any debt you're richer than 25% of the Americans")
    if gender == 'female' or gender == 'Female' or gender == 'FEMALE' or gender == 'F' or gender == 'f':
        print(f"\n {name}  Did you know, 1 in 3 married women earn more money each year than their husbands do.")
    else:
        print(f"\n {name} Did you know, of all the currency in the world, roughly eight percent of it is actual physical money. The other 92% of money only exists digitally.")
else:
    print(f"\n{name} what color socks are you wearing? If not wearing please enter your shoe color! ")
    time.sleep(0.2)
    Tri_in3 = input()
    print(f"\n Lost {Tri_in3} socks can cost you £240 a year.")
    if gender == 'female' or gender == 'Female' or gender == 'FEMALE' or gender == 'F' or gender == 'f':
        print(f"\n {name} Did you know, 45% of all U.S. millionaires are women.")
        
    
display(intruction2)
