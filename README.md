# Rock-Paper-Scissors Model using Markov Chain

The `player` function implements a simple Rock-Paper-Scissors (RPS) strategy based on a Markov Chain model. In this strategy, the function uses the opponent's previous move and the player's previous move to predict the opponent's next move and chooses the counter move to that prediction. The model keeps track of the opponent's behavior and adjusts its prediction accordingly, aiming to outsmart the opponent and win the game.

## How the Model Works

1. The `player` function maintains three possible moves: "R" for Rock, "P" for Paper, and "S" for Scissors.

2. When the function is called for the first time, it randomly selects one of the moves as the initial guess.

3. On subsequent calls, the `player` function receives the opponent's previous move as `prev_play`, and it uses this information to update the opponent's move history.

4. The model uses a dictionary called `model` to keep track of the frequency of the opponent's next move given the previous round state (combination of the opponent's move and player's move).

5. The function keeps track of the opponent's move history and player's move history in lists called `opponent_history` and `player_history`, respectively. It also defines a `memory` variable to limit the history length.

6. The function loops through the opponent's move history and updates the `model` dictionary by counting the occurrences of each next move for a specific state.

7. The current state is calculated as `state = prev_play + player_history[-1]`, representing the opponent's previous move and the player's previous move.

8. The function predicts the opponent's next move by looking up the most frequent response to the current state in the `model` dictionary.

9. The function then selects the counter move to the opponent's predicted move. For example, if the prediction is "P" (Paper), the counter move is "S" (Scissors).

10. The selected move is returned as the function's output, and it is also added to the player's move history for future use.

## Usage and Strategy

The `player` function can be used as a strategy for playing Rock-Paper-Scissors against an opponent. The Markov Chain model analyzes the opponent's past moves and tries to anticipate the next move, allowing the player to choose a counter move. By doing so, the function aims to gain an advantage over the opponent and increase the chances of winning the game.

## Note

It's important to understand that this strategy is not foolproof, and its effectiveness may vary depending on the opponent's playing style. While Markov Chain models can offer reasonable predictions based on past behavior, they do not guarantee victory in every scenario. Winning at Rock-Paper-Scissors often involves a combination of strategies, psychology, and randomness.

## Assignment - Problem Statement

For this challenge, you will create a program to play Rock, Paper, Scissors. A program that picks at random will usually win 50% of the time. To pass this challenge your program must play matches against four different bots, winning at least 60% of the games in each match.

In the file `RPS.py` you are provided with a function called `player`. The function takes an argument that is a string describing the last move of the opponent ("R", "P", or "S"). The function should return a string representing the next move for it to play ("R", "P", or "S").

A player function will receive an empty string as an argument for the first game in a match since there is no previous play.

The file `RPS.py` shows an example function that you will need to update. The example function is defined with two arguments (`player(prev_play, opponent_history = [])`). The function is never called with a second argument so that one is completely optional. The reason why the example function contains a second argument (`opponent_history = []`) is because that is the only way to save state between consecutive calls of the `player` function. You only need the `opponent_history` argument if you want to keep track of the opponent_history.

*Hint: To defeat all four opponents, your program may need to have multiple strategies that change depending on the plays of the opponent.*

### Development

Do not modify `RPS_game.py`. Write all your code in `RPS.py`. For development, you can use `main.py` to test your code. 

`main.py` imports the game function and bots from `RPS_game.py`.

To test your code, play a game with the `play` function. The `play` function takes four arguments:
- two players to play against each other (the players are actually functions)
- the number of games to play in the match
- an optional argument to see a log of each game. Set it to `True` to see these messages.

```py
play(player1, player2, num_games[, verbose])
```
For example, here is how you would call the function if you want `player` and `quincy` to play 1000 games against each other and you want to see the results of each game:
```py
play(player, quincy, 1000, verbose=True)
```

Click the "run" button and `main.py` will run.

### Testing 

The unit tests for this project are in `test_module.py`. We imported the tests from `test_module.py` to `main.py` for your convenience. If you uncomment the last line in `main.py`, the tests will run automatically whenever you hit the "run" button.

### Submitting

Copy your project's URL and submit it to freeCodeCamp.
