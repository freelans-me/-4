# 1 zadanie 
def generator(n):
    for i in range(1, n+1):
        yield i
        gen = generator(5)

for i in gen:
    print(i)

# або

gen = generator(5)

print(next(gen))
print(next(gen))
print(next(gen))
print(next(gen))
print(next(gen))
# 2 zadanie
import traceback
import math

def calculator(func):
    def wrapper(expression):
        try:
            result = func(expression)
            return result
        except Exception:
            traceback.print_exc()
            return "Error: invalid expression"
    return wrapper

@calculator
def calculate(expression):
    return eval(expression)

print(calculate("2+2")) # 4
print(calculate("2/0")) # Error: invalid expression
# dodatkove zavdanna
class Student:
    def __init__(self, name):
        self.name = name
        self.day = 1

    def __iter__(self):
        return self

    def __next__(self):
        if self.day <= 5:
            result = f"Day {self.day}: {self.name} is studying"
            self.day += 1
            return result
        else:
            raise StopIteration

student = Student("John")

for day in student:
    print(day)
