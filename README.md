# Gehirn

Python Tetris with a twist.

-using relu activation function

-initially ran the training while also rendering UI for one member in population
this slowed generation time tremendously
-built a training file that didnt render any ui and wasn't based on any clock ticks and the traing time per generation decreased from about 3 minutes to 6 seconds

-poor fitness for a model that only got current and next piece info (4 inputs)
added the status of all squares on the grid (200 squares on a 10x20 grid each given a val 0 if the tile was not occupied 1 if it was). This improved the fitness from the best model of 920 to 1011 (addition of 2 hidden nodes)

-the training for the model was using randomly generated next pieces with no seed constraint so a seed was set to ensure all
trianing used the same random seed for piece generation. this furthermore improved the fitness from 1011 to 1182

-adding hidden nodes severly increase the run time

-to further improveme the model, the fitness function was re-evaluated
    -how old fitness was decided
        -1 fitness point for every move the player makes without losing/causing game to end
        -(-1) fitness for ending the game
        -5 points for placing a piece without losing
        - lines_cleared * level_multiplier points for a line clear using the following dict where key = lines cleared and value = points awarded
        dict = {1:40,
                2:100,
                3:300,
                4:1200,}
        -20 * level_multiplier for a sucessful piece placement

    -new fitness
        -1 point for every move without ending the game
        -(-10) points for losing game
        -5 * level_multiplier points for every sucessful piece placement
        -lines_cleared * level_multiplier points for a line clear using the following dict where key = lines cleared and value = points awarded
            dict = {1:40,
                    2:100,
                    3:300,
                    4:1200,}


