import java.util.Random;
import java.util.Scanner;

public class GuessTheNumber 
{
    public static void main(String[] args) 
    {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int minRange = 1;
        int maxRange = 100;
        int maxAttempts = 10;
        int score = 0;

        System.out.println("Welcome to the Guess the Number game!");

        while (true) 
        {
            int secretNumber = random.nextInt(maxRange - minRange + 1) + minRange;
            int attempts = 0;

            System.out.println("\nI've selected a number between " + minRange + " and " + maxRange + ". Try to guess it!");

            while (attempts < maxAttempts) {
                System.out.print("\nEnter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;

                if (userGuess == secretNumber) 
                {
                    System.out.println("Congratulations! You guessed the number " + secretNumber + " in " + attempts + " attempts!");
                    score++;
                    break;
                } else if (userGuess < secretNumber) 
                {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }

            if (attempts >= maxAttempts) 
            {
                System.out.println("\nSorry, you've reached the maximum number of attempts. The secret number was " + secretNumber + ".");
            }

            System.out.print("\nYour current score is: " + score);
            System.out.print("\nDo you want to play again? (yes/no): ");
            String playAgain = scanner.next().toLowerCase();
            
            if (!playAgain.equals("yes")) 
            {
                break;
            }
        }

        System.out.println("Thanks for playing!");
        scanner.close();
    }
}

