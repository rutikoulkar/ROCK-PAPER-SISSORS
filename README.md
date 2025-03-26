# ROCK-PAPER-SISSORS
//ROCK PAPER SISSORS
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int playerScore = 0;
int computerScore = 0;

void displayMenu();
void playGame();
void displayRules();
void displayScores();
string getComputerChoice();
string getPlayerChoice();
void determineWinner(string playerChoice, string computerChoice);

void displayMenu() {
    int choice;
    cout << "Welcome to Rock-Paper-Scissors!\n";
    cout << "1. Play Game\n";
    cout << "2. Display Rules\n";
    cout << "3. Display Scores\n";
    cout << "4. Exit\n";
    cout << "Enter your choice: ";
    cin >> choice;

    switch (choice) {
        case 1:
            playGame();
            break;
        case 2:
            displayRules();
            break;
        case 3:
            displayScores();
            break;
        case 4:
            cout << "Thank you for playing!\n";
            break;
        default:
            cout << "Invalid choice! Please try again.\n";
            displayMenu();
            break;
    }
}

void playGame() {
    string playerChoice, computerChoice;
    char playAgain;

    do {
        playerChoice = getPlayerChoice();
        computerChoice = getComputerChoice();
        cout << "Computer chose: " << computerChoice << endl;
        determineWinner(playerChoice, computerChoice);

        cout << "Do you want to play again? (y/n): ";
        cin >> playAgain;
    } while (playAgain == 'y' || playAgain == 'Y');

    displayMenu();
}

void displayRules() {
    cout << "\nRules of Rock-Paper-Scissors:\n";
    cout << "Rock beats Scissors\n";
    cout << "Scissors beats Paper\n";
    cout << "Paper beats Rock\n\n";
    displayMenu();
}

void displayScores() {
    cout << "\nScores:\n";
    cout << "Player: " << playerScore << endl;
    cout << "Computer: " << computerScore << endl << endl;
    displayMenu();
}

string getComputerChoice() {
    int choice = rand() % 3;
    if (choice == 0) return "Rock";
    if (choice == 1) return "Paper";
    return "Scissors";
}

string getPlayerChoice() {
    int choice;
    cout << "Enter your choice:\n";
    cout << "1. Rock\n";
    cout << "2. Paper\n";
    cout << "3. Scissors\n";
    cout << "Your choice: ";
    cin >> choice;

    while (choice < 1 || choice > 3) {
        cout << "Invalid choice! Please enter a number between 1 and 3.\n";
        cout << "Your choice: ";
        cin >> choice;
    }

    if (choice == 1) return "Rock";
    if (choice == 2) return "Paper";
    return "Scissors";
}

void determineWinner(string playerChoice, string computerChoice) {
    if (playerChoice == computerChoice) {
        cout << "It's a tie!\n";
    } else if ((playerChoice == "Rock" && computerChoice == "Scissors") ||
               (playerChoice == "Scissors" && computerChoice == "Paper") ||
               (playerChoice == "Paper" && computerChoice == "Rock")) {
        cout << "You win!\n";
        playerScore++;
    } else {
        cout << "Computer wins!\n";
        computerScore++;
    }
}

void addVisuals() {
    cout << "----------------------------------------\n";
    cout << "                SCORES                  \n";
    cout << "----------------------------------------\n";
    cout << " Player        |        Computer        \n";
    cout << "----------------------------------------\n";
    cout << "       " << playerScore << "        |        " << computerScore << "      \n";
    cout << "----------------------------------------\n";
    cout << endl;
}

void showWinningMessage(string winner) {
    cout << "\n----------------------------------------\n";
    cout << "Congratulations " << winner << "! You are the winner!\n";
    cout << "----------------------------------------\n";
}

void playMultipleRounds() {
    char playAgain;
    do {
        playGame();
        cout << "Do you want to play another round? (y/n): ";
        cin >> playAgain;
    } while (playAgain == 'y' || playAgain == 'Y');
    displayMenu();
}

void displayFinalScores() {
    cout << "\n----------------------------------------\n";
    cout << "              FINAL SCORES              \n";
    cout << "----------------------------------------\n";
    cout << "Player: " << playerScore << "  |  Computer: " << computerScore << endl;
    cout << "----------------------------------------\n";
}

void gameSummary() {
    cout << "\n----------------------------------------\n";
    cout << "              GAME SUMMARY              \n";
    cout << "----------------------------------------\n";
    cout << "Rounds Played: " << (playerScore + computerScore) << endl;
    cout << "Player Wins: " << playerScore << endl;
    cout << "Computer Wins: " << computerScore << endl;
    cout << "----------------------------------------\n";
}

void displayGreeting() {
    cout << "----------------------------------------\n";
    cout << " Welcome to Rock-Paper-Scissors Game!   \n";
    cout << "----------------------------------------\n";
    cout << endl;
}

void displayGoodbyeMessage() {
    cout << "----------------------------------------\n";
    cout << "  Thank you for playing! Goodbye!       \n";
    cout << "----------------------------------------\n";
}

int main() {
    srand(time(0)); 
    displayMenu();
    return 0;
}





