# new
def arithmetic_arranger(problems, show_answers=False):
    if len(problems) > 5:
        return "Error: Too many problems."

    arranged_problems = []

    for problem in problems:
        num1, operator, num2 = problem.split()
        
        if operator not in ['+', '-']:
            return "Error: Operator must be '+' or '-'."
        
        if not num1.isdigit() or not num2.isdigit():
            return "Error: Numbers must only contain digits."
        
        if len(num1) > 4 or len(num2) > 4:
            return "Error: Numbers cannot be more than four digits."
        
        width = max(len(num1), len(num2)) + 2
        arranged_problems.append((num1.rjust(width), operator + num2.rjust(width - 1)))
        
    arranged = []

    for i in range(len(arranged_problems[0])):
        line = "    ".join([problem[i] for problem in arranged_problems])
        arranged.append(line)

    if show_answers:
        answers = []
        for problem in problems:
            num1, operator, num2 = problem.split()
            if operator == '+':
                answer = str(int(num1) + int(num2))
            else:
                answer = str(int(num1) - int(num2))
            width = max(len(num1), len(num2)) + 2
            answers.append(answer.rjust(width))
        arranged.append("    ".join(answers))
        
    arranged = "\n".join(arranged)
    return arranged

# Example usage
problems = ["32 + 8", "1 - 3801", "9999 + 9999", "523 - 49"]
result = arithmetic_arranger(problems, True)
print(result)
