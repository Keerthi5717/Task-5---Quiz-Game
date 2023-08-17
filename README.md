# Task-5---Quiz-Game
import random

class QuizGame:
    def __init__(self):
        self.questions = []
        self.score = 0

    def load_questions(self):
        # Load quiz questions from a file or database
        self.questions = [
            {
                "question": "What is the capital city of Spain?",
                "answer": "Madrid"
            },
            {
                "question": "Who is the author of the Harry Potter series?",
                "answer": "J.K. Rowling"
            },
            {
                "question": "What is the chemical symbol for gold?",
                "answer": "Au"
            }
        ]


    def display_welcome_message(self):
        print("Welcome to the Quiz Game!")
        print("Answer trivia questions and test your knowledge.")

    def present_question(self, question):
        print(question["question"])

    def evaluate_answer(self, question, user_answer):
        if user_answer.lower() == question["answer"].lower():
            return True
        else:
            return False

    def display_feedback(self, is_correct):
        if is_correct:
            print("Correct!")
            self.score += 1
        else:
            print("Incorrect!")
            print("The correct answer is: ", question["answer"])

    def display_final_results(self):
        print("Quiz Completed!")
        print("Your final score is", self.score, "out of", len(self.questions))

    def play_again(self):
        response = input("Do you want to play again? (yes/no): ")
        return response.lower() == "yes"

    def run(self):
        self.load_questions()
        self.display_welcome_message()

        while True:
            random.shuffle(self.questions)
            self.score = 0

            for question in self.questions:
                self.present_question(question)
                user_answer = input("Enter your answer: ")

                is_correct = self.evaluate_answer(question, user_answer)
                self.display_feedback(is_correct)

            self.display_final_results()

            if not self.play_again():
                break

        print("Thank you for playing the Quiz Game!")

game = QuizGame()
game.run()
