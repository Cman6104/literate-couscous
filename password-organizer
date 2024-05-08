print("Welcome to my password organizer!")
print("Here you can store your password using a key that corresponds to the password.")
feedback = input("Would you like to store or search for a password today? ")
password_lib = {}

# Load existing passwords from file or create new file if not found
try:
    with open("passwords.txt", "r") as file:
        for line in file:
            key, password = line.strip().split(":")
            password_lib[key] = password
except FileNotFoundError:
    open("passwords.txt", "a").close()

if feedback == "store":
    key_word = input("Enter a keyword for your password: ")
    password = input("Enter the password: ")
    print("Password saved")
    password_lib[key_word] = password
    # Save updated passwords to file
    with open("passwords.txt", "a") as file:
        file.write(f"{key_word}:{password}\n")
    print("Password library:")
    for keyword, password in password_lib.items():
        print(f"Keyword: {keyword}, Password: {password}")
elif feedback == "search":
    search_keyword = input("Enter the keyword to retrieve the password: ")
    if search_keyword in password_lib:
        print(f"The password for '{search_keyword}' is '{password_lib[search_keyword]}'")
    else:
        print("Keyword not found.")
