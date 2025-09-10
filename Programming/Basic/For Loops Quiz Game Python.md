---
Created: 2025-06-05T06:34
---
```Python
questions = ("How many elements are in the periodic table? : ",
             "Which nimal lays the larges eggs? : ",
             "What is the nost abundant gas in the Earth's atmosphere? : ",
             "How many bones are in the human body? : ",
             "Which planet in the solar system is the hottest? : ")

options = (("A. 116", "B. 117" ,"C. 118", "D. 119"),
           ("A. Whale", "B. Crocodile" ,"C. Elephant", "D. Ostrich"),
           ("A. Nitrogen", "B. Oxygen" ,"C. Carbon-Dioxide", "D. Hydrogen"),
           ("A. 206", "B. 207" ,"C. 208", "D. 209"),
           ("A. Mercury", "B. Venus" ,"C. Earth", "D. Mars"))

answers = ("C", "D", "A","A","B")

guesses = []

score = 0

questionNumber= 0

for question in questions:
    print("\n----------------------------------------")
    print(question)
    for option in options[questionNumber]:
        print(option)
    
    guess = input("Enter (A, B, C, D) : ").upper()
    guesses.append(guess)
    if guess == answers[questionNumber]:
        score+=1
        print("CORRECT")
    else:
        print("INCORRECT")
        print(f"{answers[questionNumber]} is the correct answer")
    questionNumber+=1

print("\n----------------------------------------")
print("---------------RESULTS------------------")
print("----------------------------------------\n")

print("Answers : ", end="")
for answer in answers:
    print(answer, end=" ")
print()

print("Guesses : ", end="")
for guess in guesses:
    print(guess, end=" ")
print()

score = int(score / len(questions) * 100)
print(f"Your score is : {score}%")
```