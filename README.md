import random

def get_random_word():
    words = ["apple", "banana", "cherry", "orange", "grape", "kiwi", "pear", "watermelon"]
    return random.choice(words)

def hide_word(word, guessed_letters):
    return ''.join(c if c in guessed_letters else '*' for c in word)

def play_game():
    word_to_guess = get_random_word()
    attempts_left = int(input("Введіть кількість спроб вгадати слово: "))
    guessed_letters = set()

    while attempts_left > 0:
        guess = input("Введіть букву або слово: ").lower()

        if len(guess) > 1:
            if guess == word_to_guess:
                print("Вітаю, ви вгадали слово!")
                return
            else:
                print("Слово не правильне.")
                return

        if guess in guessed_letters:
            print("Ви уже вгадали цю літеру.")
            continue

        guessed_letters.add(guess)
        hidden_word = hide_word(word_to_guess, guessed_letters)

        if hidden_word == word_to_guess:
            print(f"Вітаю, ви вгадали слово: {word_to_guess}")
            return
        else:
            print(hidden_word)

        if guess not in word_to_guess:
            attempts_left -= 1
            print("Такої літери немає.")

    print(f"Кількість спроб закінчилась. Ви програли. Загадане слово: {word_to_guess}")

if __name__ == "__main__":
    play_game()
