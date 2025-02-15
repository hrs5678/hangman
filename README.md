# hangman
A simple Hangman game implemented in  Python. This project includes word selection, user input handling, and a win/loss condition. Great for learning basic programming concepts like loops, conditionals, and string manipulation.

import random

def choose_word():
    words = ["python", "hangman", "computer", "programming", "developer"]
    return random.choice(words)

def display(word, guessed_letters):
    return " ".join(letter if letter in guessed_letters else "_" for letter in word)

def hangman():
    word = choose_word()
    guessed_letters = set()
    attempts = 6

    print("Welcome to Hangman!")
    
    while attempts > 0:
        print("\nWord:", display(word, guessed_letters))
        guess = input("Guess a letter: ").lower()

        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single valid letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter!")
            continue

        guessed_letters.add(guess)

        if guess in word:
            print("Good guess!")
            if all(letter in guessed_letters for letter in word):
                print("\nCongratulations! You guessed the word:", word)
                return
        else:
            attempts -= 1
            print(f"Wrong guess! Attempts left: {attempts}")

    print("\nGame over! The word was:", word)

if __name__ == "__main__":
    hangman()

