# Input of my game 

## Name Input(Input Player(s) Name(s):)
arbitrary number of players' names, separated by a blank space. For instance: **Lily Anna Joe**

## Word, Location and Direction input(Input your word, row, col and direction:)
four elements in total: word(only lowercase accepted), row number, col number and direction(across or down), separated by a blank space. For instance: **at 7 7 down**


# Class Structure of my game

## Initialization
The game can have one or more players. At the game's initialization, you will be asked to input an arbitrary number of players' names, with a blank space among each for separation. Then the method  **start** inside **Game** would be called, and the game starts.

## Board
Based on the Board class skeleton, the board can be updated by the newly added **boardupdate** method, which takes four arguments: word, row, col and direction based on players' input, and updates the board by putting the word on the board according to the location and direction specified.

## Player
Player takes two arguments, respectively individual name and one LetterBag:bag, which is in the background for rack updating. Name, score and rack are stored and can be get, and the latter two can be updated as well. Name is stored in the attribute and can be get by **get_name** method. Score is stored in the score attribute, can be get from the **get_score** method, and can be updated through the **updatescore** method. This method takes a word as argument and adds points based on the word’s letters. The principle for adding comes from the dictionary built on **letter_points.csv**. The dictionary takes letters as keys and corresponding points as values. Rack is a list, initialized by **initialize_rack** method, taking seven randomized letters from the bag, and gets updated through **updaterack** method, which is the combination of **remove_from_rack** method to remove the tiles played by the player and the **replenish_rack** method to replenish the current rack to 7 letters as long as there are enough tiles in the bag, with the help of  **get_rack_length** method to detect number of tiles in rack. You can also get the rack from **get_rack** method. 

## LetterBag
LetterBag stores a collection of letters for rack updating. It is initialized by **initialize_bag** method, which first turns the **letter_counts.csv** into a dictionary, with letters as key, counts as value, and then turns the dictionary into a list of 98 letters, with each different letter appearing for times of their corresponding value. Then I randomize the list by the **shuffle** method. The **take_from_bag** method helps pop out letters to the rack, used for **initialize_rack** and **replenish_rack** methods in **Player**. The **get_bag_length** method helps detecting if there are enough tiles remaining for the **replenish_rack** method in **Player**.

## Game
Game has a Board (15 rows, and 15 columns, both numbered from 0 to 14)，a LetterBag taken as the second argument for all Players, a list of Players constructed by names inputted and the shared LetterBag, an initial roundnumber set as 1 to make sure the first turn can place the word in a blank spot on the board, a running statement set as default False, used to cycle through the players list. The game starts when calling the **start** method. Then the **self.running** statement will be changed to True for player cycling. In each turn, the player would be presented with the board, a rack with 7 letters, and be required to input four elements: word(created from the available letters in the rack), row number, col number and direction(across or down), separated by a blank space. If the input is not **EXIT**, it will become the argument of the **checking** method, which is used for input checking based on the **You must handle the following errors** requirement(you can refer to my code comment for information regarding each test inside). If the input is not valid, the player would be asked to input again. On the other hand, if all tests pass and the **checking** method returns **True**, the board, score, rack and roundnumber would all be updated. The player's updated score, as well as the updated board would be displayed, commencing the turn of the next player. However, if the player input is **EXIT**, the game ends, and all player's scores will be displayed.




