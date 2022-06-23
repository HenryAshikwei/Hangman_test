# HANGMAN PROJECT
    The hangman project was to create a game using python functions and coding where the user can interact with the python terminal to try and guess a random word picked from a given list. The aim is to try and guess the word within a number of tries, afte rrunning ouit of lives the game would end.
    
    
# Milestone 1
    The first milestone focuses on completing the ask_letter " function. This function foces on asking the user for a letter, part of the code requires the input of the user to be just a single letter otherwise the code has to ask the user to enter just one single character. The also checks for any letter that has already been enterred so the same letter cant be guessed multiple times. 
    This calls the check_letter function. 
    
    def ask_letter(self):

        
        while True:
            letter = input("Enter a single character: ")
            if len(letter) > 1: 
                print("Please, enter just one character")
            elif len(letter) == 1:
                if letter in self.list_letters:
                    print(letter, "was a ready tried")
                else:
                    self.check_letter(letter)
                pass
            else:
                print("Please enter a character")
      
# Milestone 2
    This milestone focuses on defining the class of the game. This is where all the attributes for the game are set. 
    
    def __init__(self, word_list, num_lives=5):
        self.word = random.choice(word_list)
        self.word_guessed = ['_'] * len(self.word)
        self.num_letters = len(self.word)
        self.num_lives = num_lives
        self.list_letters = []

        print("The mystery word has", len(self.word), "characters")
        print(self.word_guessed)
        print("You have", num_lives, "lives!")
        pass
        
  # Milestone 3
     THis milestone focuses on the check_letter() function. It checks if the letter is present in the word. The code works in conjucntion with the ask_letter() where a single letter is asked to be entered when the user inputs more than one.
     If the letter input is in the word then the then letter is replaced in the word that is to be guessed replacing '_'. 
     If the word guessed was incorrect then the number of lives is reduced by one, whilst printing the hangman picture graphic. 
     
     def check_letter(self, letter) -> None:

        if letter.lower() in self.word:
            for i, char in enumerate(self.word):
                if letter.lower() == char:
                    self.word_guessed[i] = letter.lower()
                    self.num_letters -= 1
                    print("Nice!", letter, "is in the word!")
                    self.list_letters.append(letter.lower())
                    continue
                else:
                    continue
            print(self.word_guessed)
        else:
            self.num_lives -= 1
            self.list_letters.append(letter.lower())
            print("Sorry" , letter , "is not in the word")
            print("You have", self.num_lives, "lives left")
            print(hangman_list[self.num_lives])
        pass
        
   # Milestone 4
       
       The fourth milestone focuses on completing the logic of the game. The final function loops the game until the condition  of wininig the game or running out of lives.
       
       def play_game(word_list):
    game = Hangman(word_list, num_lives=5)

    while game.num_lives >= 0:
        if game.num_lives > 0 and '_' in game.word_guessed:
            game.ask_letter()
        elif game.num_lives > 0 and '_' not in game.word_guessed:
            print("Congratulations! You have won!")
            print(f"The word was, {game.word}")
            break
        elif game.num_lives == 0:
            print("You have run out of lives")
            print(f"The word was, {game.word}")
            break
        pass
