haskell-2048-4D-MP
============
A client server implementation of a 2048 game 4D multiplayer variant in Haskell, modified just for fun!

The original one from which this is forked is [mmcguill/haskell-2048](https://github.com/mmcguill/haskell-2048).

I appreciate the original idea by [gabrielecirulli](https://github.com/gabrielecirulli) and nice Haskell implementation by [mmcguill](https://github.com/mmcguill). 

I've added these concepts:
  * Tile - Subgrid - Grid board structure, and real and virtual axes:
    1. For the size factor n, each subgrid has n columns and n rows of tiles, and the grid has n columns and n rows of subgrids.
    2. There are two kinds of subgrids and each kind has its corresponding kind of axes:
      - real subgrid \[ R<sub>x y</sub>(i, j) \] : This is visualized as a matrix, and has X and Y real axes.
      - virtual subgrid \[ V<sub>x y</sub>(i, j) \] = \[ R<sub>i j</sub>(x, y) \] : This is NOT visualized but can be understood as a matrix, and has X\' and Y\' virtual axes.
  * The new rule based on allocation decision by player, instead of randomly allocating new tile by computer:
    1. Do a Rock-Scissor-Paper or any other minigame.
    2. The first-ranked player of the minigame above minigame should decide which tile to put into which place.
    3. The next player should decide in which axis(either X, Y, X\', or Y\') and direction he or she moves tiles, and tile merging just as the same as that in [the original 2048](https://gabrielecirulli.github.io/2048) happens if possible. Then, that player decide which tile to put into which place. Then the next player does so too, ...until no tile can be moved
    4. If any tile cannot be moved, the game ends and the player who has the highest score wins!
