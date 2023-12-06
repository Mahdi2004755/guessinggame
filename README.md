import random

def number_guessing_game():
    # Difficulty settings
    difficulty_settings = {
        'Easy': {'range': (1, 50), 'attempts': 10},
        'Medium': {'range': (1, 100), 'attempts': 7},
        'Hard': {'range': (1, 200), 'attempts': 5}
    }

    # Choose difficulty
    print("Welcome to PrinceM's Enhanced Number Guessing Game!")
    print("Select Difficulty: Easy, Medium, Hard")
    while True:
        difficulty = input("Enter difficulty: ").capitalize()
        if difficulty in difficulty_settings:
            break
        print("Invalid difficulty. Please choose Easy, Medium, or Hard.")

    settings = difficulty_settings[difficulty]
    correct_number = random.randint(*settings['range'])
    attempts = 0

    print(f"Guess a number between {settings['range'][0]} and {settings['range'][1]}.")

    # Main game loop
    while attempts < settings['attempts']:
        try:
            guess = int(input("Enter your guess: "))
            attempts += 1

            # Check guess
            if guess == correct_number:
                score = settings['attempts'] - attempts + 1
                print(f"Congratulations! You guessed the correct number in {attempts} attempts. Your score: {score}")
                break
            elif guess < correct_number:
                print("Too low!")
            else:
                print("Too high!")

            # Provide a hint
            if attempts < settings['attempts']:
                hint = "even" if correct_number % 2 == 0 else "odd"
                print(f"Hint: The number is {hint}.")

        except ValueError:
            print("Please enter a valid integer.")

    if attempts >= settings['attempts']:
        print(f"Sorry, you've exceeded the maximum attempts. The correct number was {correct_number}.")

    # Play again
    if input("Do you want to play again? (yes/no): ").lower() == "yes":
        number_guessing_game()

# Start the game
number_guessing_game()
