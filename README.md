# CodeAlpha_Hangman_segs
The Hangman Game 
import random

stages = ['''
  +---+
  |   |
      |
      |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
      |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
  |   |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
 /|   |
      |
      |
=========''', r'''
  +---+
  |   |
  O   |
 /|\  |
      |
      |
=========''', r'''
  +---+
  |   |
  O   |
 /|\  |
 /    |
      |
=========''', r'''
  +---+
  |   |
  O   |
 /|\  |
 / \  |
      |
=========''']



word_list = ["naruto", "sasuke", "hinata", "neji", "shikamaru", "gaara",
             "itachi", "minato", "orochimaru", "zetsu"]
chosen_word = random.choice(word_list)
lives = 6

display = []
word_length = len(chosen_word)
for _ in range(word_length):
    display += "_"
print(display)


end_of_game = False
while not end_of_game:
    guess = input("guess a letter:").lower()

    if guess in display:
        print(f"you've already guessed {guess}")

    for position in range(word_length):
        letter = chosen_word[position]
        if letter == guess:
            display[position] = letter
    if guess not in chosen_word:
        print(f"you guessed {guess}, that's not in the word. you lose a life.")
        lives -= 1
        if lives == 0:
            end_of_game = True
            print("You lose.")



    print(f"{''.join(display)}")

    if "_" not in display:
        end_of_game = True
        print("you win")
    print(stages[lives])
