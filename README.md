#Task-3

import string
import random

def generate_password(length):
    if length < 4:
        return "Password length should be at least 4 characters."

    # Define the character sets
    lower = string.ascii_lowercase
    upper = string.ascii_uppercase
    digits = string.digits
    special = string.punctuation

    # Combine all the character sets
    all_chars = lower + upper + digits + special

    # Ensure the password contains at least one character from each set
    password = [
        random.choice(lower),
        random.choice(upper),
        random.choice(digits),
        random.choice(special)
    ]

    # Fill the rest of the password length with random characters
    password += random.choices(all_chars, k=length-4)

    # Shuffle the password list to ensure randomness
    random.shuffle(password)

    # Convert the list to a string and return
    return ''.join(password)

def main():
    print("Password Generator")

    while True:
        try:
            length = int(input("Enter the desired length for the password: "))
            if length <= 0:
                print("Please enter a positive number.")
                continue
        except ValueError:
            print("Invalid input. Please enter a number.")
            continue

        password = generate_password(length)
        print(f"Generated password: {password}")

        choice = input("Do you want to generate another password? (yes/no): ").strip().lower()
        if choice != 'yes':
            print("Exiting...")
            break

if __name__ == "__main__":
    main()
