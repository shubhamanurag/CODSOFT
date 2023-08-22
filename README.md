import java.util.Scanner;
import java.util.Random;

public class GuessingGame 
{

    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
        Random rand = new Random();
        int secretNumber;
        int userGuess; 
        int maxGuesses = 10; 
        int numGuesses = 0; 
        int score = 0; 
        int rounds = 0; 
        boolean playAgain = true;

        while (playAgain) 
        {
            secretNumber = rand.nextInt(100) + 1;
            numGuesses = 0;
            rounds++;
            System.out.println("Round " + rounds + ": Guess a number between 1 and 100.");
            do 
            {
                System.out.print("Enter your guess: ");
                userGuess = sc.nextInt();
                numGuesses++;
                if (userGuess == secretNumber)
                 {
                    System.out.println("You got it! The number was " + secretNumber + ".");
                    score += maxGuesses - numGuesses + 1; 
                    System.out.println("Your score is " + score + ".");
                    break; 
                }
                 else if (userGuess < secretNumber)
                  {
                    System.out.println("Your guess is too low.");
                    if (numGuesses == maxGuesses) 
                    {
                        System.out.println("You have no more guesses left. The number was " + secretNumber + ".");
                        break; 
                    }
                } 
                else 
                {
                    System.out.println("Your guess is too high.");
                    if (numGuesses == maxGuesses) 
                    {
                        System.out.println("You have no more guesses left. The number was " + secretNumber + ".");
                        break; 
                    }
                }
            } while (true);
            System.out.print("Do you want to play another round? (Y/N): ");
            char choice = sc.next().charAt(0); 
            if (choice == 'Y' || choice == 'y') 
            {
                playAgain = true;
            }
             else if (choice == 'N' || choice == 'n') 
             {
                playAgain = false; 
                System.out.println("Thank you for playing. Your final score is " + score + ".");
            } 
            else 
            {
                System.out.println("Invalid input. Ending the game.");
                playAgain = false;
            }
        } 

        sc.close(); 

    } 

} 
