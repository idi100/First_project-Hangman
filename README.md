# First_project-Hangman
This is a two-player guessing game, where only a certain amount of guesses are allowed. One player thinks of a phrase and the other player guesses

'''
Purpose:
Parameters:
Return Value:

1. Readable 2. Concise 3. Efficient 
'''
import random
import copy
def hangman(text):
    text = input('''Welcome to my first project! I have created the hangman game
for my two younger siblings to play but you can play too. A random word has been chosen.

Enter a letter: ''').lower()
    

    #Randomly choose a word from words.txt and 
    # assign it to chosen_words.
    fp = open('words.txt')
    common_words = fp.read().split()
    fp.close()

#check if length is more than 4
    chosen_word = random.choice(common_words)
    while len(chosen_word) <4:
        chosen_word = random.choice(common_words)

     
#correctly guessed letters
    under_scored_letters = copy.deepcopy(chosen_word)
    
    def underscored_word():
        for ch in under_scored_letters:
            under_scored_letters.replace(ch,'_')
    
    correctly_guessed = []

#Incorrectly guessed letters
    
    count = 0
    def incorrect_letters():
        global count  # You need to specify that you're using the count variable from the outer scope
    for letter in text:
        if letter not in chosen_word:
            count += 1
        
    
       
    


    

    display = []

    word_length = len(chosen_word)

    for _ in range(len(chosen_word)):
        display += "_"
    print(display)
    
    guess = input("Guess a letter: ").lower()
    

    for position in range(word_length):
        letter = chosen_word[position]
        if letter == guess:
            display[position] = letter
    print(display)


    
        
    


    print("Chosen word:", chosen_word.capitalize()) #Delete this later

    # Check of the letter the user guessed (text) is one of the 
    #letters in the chosen_word





    
if __name__ == '__main__':
    print(hangman("Believe"))
    breakpoint()



