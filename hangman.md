# hangman
```py
import random

eng_words = ["puppy", "kitten", "happy"]

answer = random.choice(eng_words)
guess_letters=list("_"*len(answer))

life=3

game_over = False
while not game_over:
    print(f"남은 기회: {'*'*life}번")
    user_guess= input("한 글자씩 추측해 보세요 >>> ").lower()

    if len(user_guess) == 1 and user_guess.isalpha():
        for i in range(len(answer)):
            if answer[i] == user_guess:
                guess_letters[i]= user_guess
        print(guess_letters)

        if "_" not in guess_letters:
            game_over= True

            print("성공!!")

        if user_guess not in answer:
            life -= 1
            if life == 0 :
                game_over = True
                print(f"실패!! 정답은[answer] 입니다!")
    else:
        print("영문 한자씩 입력해 주세요")
```
    
# 결과
```py
남은 기회: ***번
한 글자씩 추측해 보세요 >>> p
['_', '_', 'p', 'p', '_']
남은 기회: ***번
한 글자씩 추측해 보세요 >>> u
['_', '_', 'p', 'p', '_']
남은 기회: **번
한 글자씩 추측해 보세요 >>> h
['h', '_', 'p', 'p', '_']
남은 기회: **번
한 글자씩 추측해 보세요 >>> a
['h', 'a', 'p', 'p', '_']
남은 기회: **번
한 글자씩 추측해 보세요 >>> y
['h', 'a', 'p', 'p', 'y']
성공!!
```