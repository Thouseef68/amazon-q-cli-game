# 🎯 Number Guessing Game (Built with Amazon Q CLI Guidance)

This is a simple **Python terminal game** where the player tries to guess a randomly chosen number. It includes multiple difficulty levels and a score tracker.

🛠️ **Built using AI prompts in Amazon Q CLI!**

## 🚀 Features
- Three difficulty levels: Easy, Medium, Hard
- Real-time hints: "Too high" or "Too low"
- Tracks total games and total attempts
- Fully interactive and runs in terminal

## 📦 Requirements
- Python 3.x

## ▶️ How to Run

```bash
python3 number_guess_game.py
import random

def choose_level():
    print("Choose a level:")
    print("1. Easy (1-10)")
    print("2. Medium (1-100)")
    print("3. Hard (1-1000)")
    choice = input("Enter level number: ")
    if choice == '1':
        return 1, 10
    elif choice == '2':
        return 1, 100
    elif choice == '3':
        return 1, 1000
    else:
        print("Invalid choice, defaulting to Medium.")
        return 1, 100

def play_game():
    low, high = choose_level()
    secret_number = random.randint(low, high)
    attempts = 0

    print(f"\n🎯 Guess the number between {low} and {high}!")

    while True:
        try:
            guess = int(input("Your guess: "))
            attempts += 1
            if guess < secret_number:
                print("Too low! 📉")
            elif guess > secret_number:
                print("Too high! 📈")
            else:
                print(f"🎉 Correct! You guessed it in {attempts} attempts.")
                break
        except ValueError:
            print("❗ Please enter a valid number.")

    return attempts

def main():
    print("🧠 Welcome to the Number Guessing Game!")
    total_games = 0
    total_attempts = 0

    while True:
        attempts = play_game()
        total_games += 1
        total_attempts += attempts

        again = input("\nDo you want to play again? (y/n): ")
        if again.lower() != 'y':
            break

    print(f"\n🏁 You played {total_games} games with a total of {total_attempts} attempts.")
    print("Thanks for playing! ✨")

if __name__ == "__main__":
    main()
