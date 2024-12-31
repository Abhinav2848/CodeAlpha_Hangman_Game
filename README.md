import random

def select_random_word():
    words = ['python', 'hangman', 'simple', 'game']
    return random.choice(words)

def play_hangman():
    word = select_random_word()
    guessed_letters = []
    tries = 6
    guessed_word = ["_"] * len(word)

    print("Let's play Hangman!")
    print("Word: " + " ".join(guessed_word))

    while tries > 0 and "_" in guessed_word:
        guess = input("Guess a letter: ").lower()

        if guess in guessed_letters:
            print("You already guessed that letter.")
        elif guess in word:
            print(f"Good guess! {guess} is in the word.")
            for i, letter in enumerate(word):
                if letter == guess:
                    guessed_word[i] = guess
        else:
            print(f"Sorry, {guess} is not in the word.")
            tries -= 1

        guessed_letters.append(guess)
        print("Word: " + " ".join(guessed_word))
        print(f"Tries left: {tries}")

    if "_" not in guessed_word:
        print("Congratulations! You guessed the word!")
    else:
        print(f"Game over! The word was {word}.")

if __name__ == "__main__":
    play_hangman()
