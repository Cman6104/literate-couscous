quiz_game_feedback = input("Would you like to play? ").lower()

if quiz_game_feedback == "yes":
    subjects = ["Art", "History", "Science"]
    subject_selected = input("Ok let's get started! You can choose from 3 subjects: Art, History, or Science: ").capitalize()
    while subject_selected not in subjects:
        print("Please choose a subject from the provided list.")
        subject_selected = input("You can choose from: Art, History, or Science: ").capitalize()

    if subject_selected == "Art":
        print("Alrighty! Let's start our Art quiz!")
        art_questions = [
            ("What artist painted the Mona Lisa? ", "Leonardo Da Vinci"),
            ("What famous painter is known for cutting off his ear? ", "Vincent Van Gogh"),
            ("The Birth of Venus is a painting by which famous artist? ", "Sandro Botticelli")
        ]
        correct_answers = 0
        for question, answer in art_questions:
            user_answer = input(question)
            if user_answer.lower() == answer.lower():
                print("Correct!")
                correct_answers += 1
            else:
                print("Incorrect. The correct answer is:", answer)
        if correct_answers == len(art_questions):
            print("You got all questions in the Art Quiz right!")
        else:
            print("You got", correct_answers, "out of", len(art_questions), "questions correct.")

    elif subject_selected == "History":
        print("Alrighty! Let's start our History quiz!")
        history_questions = [
            ("What year was the Declaration of Independence signed? ", "1776"),
            ("What was the first known civilization? ", "Mesopotamia"),
            ("What year was slavery abolished? ", "1865")
        ]
        correct_answers = 0
        for question, answer in history_questions:
            user_answer = input(question)
            if user_answer.lower() == answer.lower():
                print("Correct!")
                correct_answers += 1
            else:
                print("Incorrect. The correct answer is:", answer)
        if correct_answers == len(history_questions):
            print("You got all questions in the History Quiz right!")
        else:
            print("You got", correct_answers, "out of", len(history_questions), "questions correct.")

    elif subject_selected == "Science":
        print("Alrighty! Let's start our Science quiz!")
        science_questions = [("What is the smallest unit of matter?", "Atom"),("What is the chemical symbol for water?", "H2O"),("What is the largest planet in our solar system?", "Jupiter")]
        correct_answers = 0
        for question, answer in science_questions:
            user_answer = input(question)
            if user_answer.lower() == answer.lower():
                print("Correct!")
                correct_answers += 1
            else:
                print("Incorrect. The correct answer is:", answer)
        if correct_answers == len(science_questions):
            print("You got all questions in the History Quiz right!")
        else:
            print("You got", correct_answers, "out of", len(science_questions), "questions correct.")
else:
    print("Why not!")

