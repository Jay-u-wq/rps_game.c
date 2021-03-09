/**
    This program implements the game Rock Paper Scissors. 
**/
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include "cs50.h"

// this function is used to determine the winner
string determine_winner(computer,human) {
    string winner = NULL;
    if (computer == 0) {            	// computer chose rock
        if (human == 1) {           	// human chose paper - win
            winner = "You win!";
        } else if (human == 0) {    	// human chose rock - tie
            winner = "The game is a tie.";
        } else {                    	// human chose scissors - lose
            winner = "Computer wins!"; 
        }
    } else if (computer == 1) {     	// computer chose paper
        if (human == 2) {           	// human chose scissors - win
            winner = "You win!";
        } else if (human == 1) {    	// human chose paper - tie
            winner = "The game is a tie.";
        } else {                    	// human chose rock - lose
            winner = "Computer wins!"; 
        }
    } else if (computer == 2) {     	// computer chose scissors
        if (human == 0) {           	// human chose rock - win
            winner = "You win!";
        } else if (human == 2) {    	// human chose scissors - tie
            winner = "The game is a tie.";
        } else {                    	// human chose paper - lose
            winner = "Computer wins!"; 
        }
    }
    return winner;
}

// this is the function that gets executed when the program starts
int main() {
    // randomly pick computer gesture
    srand(time(NULL)); 
    int computer = (rand() / ((double) RAND_MAX + 1)) * 3;

    // ask human for their gesture
    printf("Please enter your gesture\n");
    int human = get_int("Enter 0 for rock, 1 for paper, 2 for scissors: ");
    
    // determine winner (calls determine_winner function described above)
    string winner = determine_winner(computer,human);

    // show outcome of game
    printf("The computer chose %d and you chose %d. %s\n",computer,human,winner);

    return 0;
}
