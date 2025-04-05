# 🕹️ Hangman Game

Welcome to the **Hangman Game**, a classic word-guessing puzzle recreated in Python! This game challenges your vocabulary and logic as you attempt to guess a hidden word one letter at a time before the hangman is fully drawn.


![](https://github.com/psyccho00/hangman-game/blob/main/hangman_game.png)
---

## 📁 Repository Structure

```
hangman-game/
│
├── main.py            # Main driver of the game logic and user interaction
├── hangman_art.py     # ASCII art used for the hangman stages and game logo
└── hangman_words.py   # List of random words used in the game
```

---

## 🎮 How to Play

- You start with a word represented by underscores (one for each letter).
- Guess one letter per round.
- For each incorrect guess, a part of the hangman is drawn.
- The game ends if you guess all letters or the hangman is fully drawn (6 mistakes).

🧠 **Objective**: Guess the word before the drawing is complete!

---

## ⚙️ Requirements

- Python 3.x

---

## ▶️ Run the Game

```bash
git clone https://github.com/psyccho00/hangman-game.git
cd hangman-game
python main.py
```

---

## 🧠 Code Explained

### 📄 hangman_art.py

This file contains:

#### 🎨 Game Logo

```python
logo = r''' 
 _                                             
| |                                            
| |__   __ _ _ __   __ _ _ __ ___   __ _ _ __  
| '_ \ / _` | '_ \ / _` | '_ ` _ \ / _` | '_ \ 
| | | | (_| | | | | (_| | | | | | | (_| | | | |
|_| |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|
                    __/ |                      
                   |___/    '''
```

#### 💀 Hangman Stages

```python
stages = ['''
  +---+
  |   |
      |
      |
      |
      |
=========''', ..., '''final stage''']
```

Each stage corresponds to the number of remaining lives (6 to 0).

---

### 📄 hangman_words.py

This file includes:

```python
word_list = ["ardvark", "baboon", "camel", "python", "keyboard", "monitor"]
```

The game selects a word from this list using:

```python
chosen_word = random.choice(word_list)
```

---

### 📄 main.py

This is where the game logic lives. It includes:

#### 🔀 Random Word Selection

```python
chosen_word = random.choice(word_list)
```

#### 📉 Lives and Display Setup

```python
lives = 6
display = ["_"] * len(chosen_word)
```

#### 🎯 Game Loop

```python
while not end_of_game:
    guess = input("Guess a letter: ").lower()
```

#### ✅ Correct Guess Logic

```python
for position in range(len(chosen_word)):
    if chosen_word[position] == guess:
        display[position] = guess
```

#### ❌ Incorrect Guess Logic

```python
if guess not in chosen_word:
    print(f"You guessed {guess}, that's not in the word. You lose a life.")
    lives -= 1
    if lives == 0:
        end_of_game = True
        print("You lose.")
```

#### 🏁 Win Condition

```python
if "_" not in display:
    end_of_game = True
    print("You win.")
```

#### 🖼️ Showing Game Progress

```python
print(f"{' '.join(display)}")
print(stages[lives])
```

---

## 🌟 Features

✅ ASCII Art for immersive visuals  
✅ Random word generation  
✅ Simple and intuitive gameplay loop  
✅ Tracks user progress and provides instant feedback  
✅ Clean, beginner-friendly Python code  

---

## 🚧 Potential Improvements

- Add GUI using `tkinter` or `pygame`
- Show letters already guessed
- Allow for difficulty levels (easy, medium, hard)
- Track scores or stats across multiple games

---

## 📷 Screenshots

```
Guess a letter: a
_ a _ _ _ _
You guessed a, it's in the word!

+---+
|   |
O   |
    |
    |
    |
=========
```

---

## 🤝 Acknowledgements

This game was built as a fun Python project to practice programming fundamentals including:

- Loops and conditionals
- List manipulation
- Functions and imports
- ASCII art for user interaction

---

## 👨‍💻 Author

Developed by [psyccho00](https://github.com/psyccho00)

---

Enjoy playing, and may the hangman never hang! ☠️
