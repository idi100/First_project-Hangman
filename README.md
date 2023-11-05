import random
import copy
def hangman(text):
    print('''Welcome to my first project! I have created the hangman game for my two younger siblings to play.They are twins, one loves soccer and the other loves word games.\n\n''')


    directory = input("Would you like to guess from a random set of words or soccer players?\n(Type: 'words' for random words and 'soccer' for random soccer players))")




    if directory == 'soccer':
        fp = open('soccer.docx')
        common_words = fp.read().split()
        fp.close()
        print('''  _________                                
 /   _____/ ____   ____  ____  ___________ 
 \_____  \ /  _ \_/ ___\/ ___\/ __ \_  __ \
 /        (  <_> )  \__\  \__\  ___/|  | \/
/_______  /\____/ \___  >___  >___  >__|   
        \/            \/    \/    \/       ''')

    #Randomly choose a word from words.txt and 
    # assign it to chosen_words.
    if directory == 'words': 
        fp = open('words.txt')
        common_words = fp.read().split()
        fp.close()
        print(''' __      __                .___                            
/  \    /  \___________  __| _/ _________    _____   ____  
\   \/\/   /  _ \_  __ \/ __ | / ___\__  \  /     \_/ __ \ 
 \        (  <_> )  | \/ /_/ |/ /_/  > __ \|  Y Y  \  ___/ 
  \__/\  / \____/|__|  \____ |\___  (____  /__|_|  /\___  >
       \/                   \/_____/     \/      \/     \/ ''')

    #check if length is more than 4
    chosen_word = random.choice(common_words)
    while len(chosen_word) <4:
        chosen_word = random.choice(common_words).lower()

    #check if user won or lost






    display = []

    word_length = len(chosen_word)


    for _ in range(len(chosen_word)):
        display += "_"
    print(f"{' '.join(display)}")



    lives = int(len(chosen_word))
    while '_' in display:
        guess = input("Guess a letter: ").lower()
        for position in range(word_length):
            letter = chosen_word[position]
            if letter == guess:
                display[position] = letter
        #print("Chosen word:", chosen_word) #Delete this later



        if guess not in chosen_word:
            lives -= 1
            if lives == 0:
                end_of_game = True
                print('You lose')
                break
        print(f"{' '.join(display)}")
    print("Chosen word:", chosen_word) #Delete this later


    if "_" not in display:
        end_of_game = True
        print("You win.")
    # Check of the letter the user guessed (text) is one of the 
    #letters in the chosen_word


    from hangman_drawing import HANGMANPICS
    print(f'{HANGMANPICS}\n')



if __name__ == '__main__':
    print(hangman('Text'))
    breakpoint()



