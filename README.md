import random
def hangman():
    words = ["python", "java", "hangman", "computer", "programming"]
    word = random.choice(words)
    guessed = []
    incorrect_guesses = 0
    max_incorrect_guesses = 6
    print("Welcome to Hangman!")
    print("Try to guess the word one letter at a time!")
    print()
    while incorrect_guesses < max_incorrect_guesses:
        display_word = ''.join([letter if letter in guessed else '_' for letter in word])
        print(f"Word: {display_word}")
        print(f"Guessed letters: {', '.join(sorted(guessed)) if guessed else 'None'}")
        print(f"Incorrect guesses left: {max_incorrect_guesses - incorrect_guesses}")
        print()
        guess = input("Enter a letter: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print("❌ Please enter a single valid letter.\n")
            continue
        if guess in guessed:
            print("❌ You've already guessed that letter.\n")
            continue
        guessed.append(guess)
        if guess in word:
            print("✓ Good guess!\n")
        else:
            incorrect_guesses += 1
            print("✗ Incorrect guess!\n")
        if all(letter in guessed for letter in word):
            print(f"🎉 Congratulations! You've guessed the word: {word}")
            return
    print(f"😞 Sorry, you've run out of guesses. The word was: {word}")
if __name__ == "__main__":
    hangman()
