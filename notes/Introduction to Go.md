---
title: Introduction to Go
tags: [Notebooks, Notebooks/Cmput 496]
---

**[Introduction to Go](https://webdocs.cs.ualberta.ca/~mmueller/courses/496-current/slides/lecture1.pdf)**

### Blocks
  ![Blocks](@attachment/cmput496/blocks.png)
  * Connected stones of the same color are called blocks
  * A is a single steong block
  * Two stones B are connected by a line. They are one block.
  * C is a single block of 5 white stones.
  * D is a block of 9 black stones.
  * A and C are not in the same block
    * No connection diagonally

### Liberties
  ![Liberties](@attachment/cmput496/liberties.png)
  * Empty points adjacent to a block are called liberties
  * The single marked white stone has four Liberties A B C D
  * The block of two marked black stones has two liberties, E and F
  * After White plays on 1, the black stones have only one liberty left
  * A bloc that loses its last liberty is captured
  
  
### Capture
  ![Capture](@attachment/cmput496/capture.png)
  * The block of four white stones has only one liberty at A
  * Black can play there
  * Effect: the four stones are captured
  * Removed from the board
  
### Suicide
![Suicide](@attachment/cmput496/suicide.png)
* White at A would be suicide
* White would take its own last liberty
* Suicide is **forbidden**
* Capturing always takes **precedence** over suicide


### Basic Ko
  ![Basic_Ko](@attachment/cmput496/basic_ko.png)
  * White can capture one black stone by playing A
  * Now if Black captures back one white stone
  * The position would repeat, infinite loop
  * Go rules **forbid** such repetition
  
  
### Resolve Ko situation
  ![Resolve Ko](@attachment/cmput496/resolve_ko.png)
  * Ko rule: after white captured black cannot re-capture right away
  * Black must play somewhere else
  * Now white has a chance to connect
  * If white also plays elsewhere, then black can capture
  
### Legal Moves
  ![Legal Move](@attachment/cmput496/legal_move.png)
  * Legal move:
    * play on any empty intersection, except points forbidden by:
      * repetition(ko rule)
      * suicide
  * Example:
    * legal moves for black, after white captured a ko
      * A4 forbidden by repetition(ko rule)
      * B3 forbidden by suicide
  
 ### Pass Move
   * Pass move is always allowed
     * Board does not change
     * It is now the other player's turn to play
   * Usually, there are some moves better than Pass
   * Competent players only pass at end of game
   
### Eyes
  ![Eyes](@attachment/cmput496/eyes.png)
  * An eye is a point that is surrounded by one color
  * An eye makes stones safter
  * Opponent cannot play in eyes A, B, C
    * Suicide,illegal to play there
  * One eye is not enought
    * Move inside eye becomes legal if it is a capture
  * Two eyes are safe
    
### End of Game and Scoring
  ![End of Game](@attachment/cmput496/end_scoring.png)
  * Game ends after two successive passes
  * Next, count the score for each player-stones plus territory
  * Add the komi
  * The winner is the player with higher
  * **Draws are possible** if the komi is integer
