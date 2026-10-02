# Hangman Game — Python

A classic **Hangman word-guessing game built with Python** and played directly in the terminal.

The game randomly selects a word from a predefined word list. The player guesses the word one letter at a time while trying to avoid losing all **6 lives**.

The project uses separate Python modules for the **word list** and **ASCII artwork**, keeping the main game logic clean and easy to understand.

---

## Game Features

* Randomly selects a word from a large word list
* Player starts with **6 lives**
* Guess the word one letter at a time
* Reveals correctly guessed letters
* Loses a life for an incorrect guess
* Detects already-guessed correct letters
* Displays Hangman ASCII-art stages based on remaining lives
* Displays a winning message when the complete word is guessed
* Reveals the word when all lives are lost
* Displays a Hangman logo when the game starts

---

## Project Structure

```text
HangmanGame/
│
├── hangman.py          # Main game logic
├── hangman_words.py    # Collection of words used by the game
├── hangman_art.py      # Hangman logo and ASCII-art stages
└── README.md           # Project documentation
```

### `hangman.py`

Contains the main game logic, including:

* Random word selection
* Initializing lives
* Accepting player input
* Checking guessed letters
* Building the displayed word
* Managing game state
* Determining win/loss conditions
* Displaying Hangman stages

### `hangman_words.py`

Contains the `word_list` used by the game.

The game randomly selects one word using:

```python
chosen_word = random.choice(word_list)
```

### `hangman_art.py`

Contains the visual elements used by the game:

* `logo` — displayed when the game starts
* `stages` — ASCII-art representations of the Hangman at different life stages

---

## How the Game Works

### 1. Game starts

The Hangman logo is displayed and the game initializes with:

```python
lives = 6
```

### 2. A random word is selected

The program randomly chooses a word from `word_list`.

```python
chosen_word = random.choice(word_list)
```

### 3. Word is hidden

If the selected word contains five letters, the player initially sees:

```text
Word to guess: _____
```

### 4. Player guesses a letter

The player enters a letter:

```text
Guess a letter: a
```

The input is converted to lowercase so that uppercase and lowercase guesses are treated consistently.

### 5. Correct guess

If the guessed letter exists in the word, its position is revealed.

For example:

```text
Word to guess: _ a _ a _
```

Previously discovered letters remain visible.

### 6. Incorrect guess

If the guessed letter isn't present in the word, the player loses one life:

```text
You guessed z, that's not in the word. You lose a life.
```

The Hangman artwork is then updated according to the remaining lives.

### 7. Repeated correct guesses

If a previously discovered letter is guessed again, the game displays:

```text
You've already guessed a
```

The game continues afterward.

### 8. Winning the game

The player wins when there are no underscores remaining in the displayed word:

```text
****************************YOU WIN****************************
```

### 9. Losing the game

The player loses when all 6 lives are used.

The game reveals the selected word:

```text
*********************** The correct word is python! YOU LOSE**********************
```

---

## How to Run

### Prerequisites

Make sure **Python 3** is installed.

Check your Python version:

```bash
python --version
```

or:

```bash
python3 --version
```

### Run the game

Navigate to the `HangmanGame` directory:

```bash
cd HangmanGame
```

Then run:

```bash
python hangman.py
```

On systems where Python 3 is invoked using `python3`:

```bash
python3 hangman.py
```

---

## Python Concepts Practiced

This project focuses on fundamental Python programming concepts, including:

* Variables
* Strings
* Lists
* `for` loops
* `while` loops
* `if / elif / else`
* Functions and modules
* Importing from custom Python modules
* User input with `input()`
* String manipulation
* List operations
* Random selection with the `random` module
* Boolean variables
* Formatted strings (f-strings)
* Game-state management

---

## 🔍 Core Game Logic

The game maintains a list of correctly guessed letters:

```python
correct_letters = []
```

For every guess, the program loops through the selected word and determines whether each letter should be displayed or hidden.

```python
for letter in chosen_word:
    if letter == guess:
        display += letter
        correct_letters.append(guess)
    elif letter in correct_letters:
        display += letter
    else:
        display += "_"
```

This allows the player to gradually reveal the hidden word.

---

## Hangman Artwork

The game uses ASCII artwork stored separately in `hangman_art.py`.

The appropriate Hangman stage is displayed based on the number of remaining lives:

```python
print(stages[lives])
```

This keeps the visual artwork separate from the game logic.

---

## Possible Future Improvements

Potential improvements I could add in future versions:

* Validate that the player enters exactly one alphabetic character
* Prevent duplicate entries from being added to `correct_letters`
* Track incorrectly guessed letters separately
* Display previously incorrect guesses
* Add difficulty levels
* Add word categories
* Add score tracking
* Add a replay option
* Add a maximum number of guesses
* Improve input validation
* Add unit tests
* Create a graphical version using Tkinter
* Add a larger/customizable word database

---

## Learning Goal

This project was created as part of my journey to learn **Python programming** and strengthen my understanding of programming fundamentals through a practical project.

Building Hangman helped me understand how individual Python concepts can be combined to create an interactive application.

---

## Author

**Pratyush Kashyap**

Python Learning Project
GitHub: `pratyushkas/learnPython`

---
