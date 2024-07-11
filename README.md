# codsoft
import java.util.Random;
import java.util.Scanner;
public class NumberGuessingGame 
{
    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
        Random random = new Random();
        int min = 1;
        int max = 100;
        System.out.println("Enter the number of attempts per round: ");
        int maxAttempts = sc.nextInt();
        int totalRounds = 0;
        int totalAttempts = 0;
        boolean playAgain = true;
        while (playAgain) 
        {
            totalRounds++;
            int genNo = random.nextInt(max - min + 1) + min;
            int attempts = 0;
            boolean guessedCorrectly = false;
            System.out.println("Round " + totalRounds + ": Guess the number between 1 and 100");
            while (attempts < maxAttempts) 
            {
                System.out.print("Enter your guess: ");
                int userGuess = sc.nextInt();
                attempts++;
                if (userGuess == genNo) 
                {
                    System.out.println("Congratulations! You guessed correctly.");
                    guessedCorrectly = true;
                    break;
                } 
                else if (userGuess > genNo) 
                {
                    System.out.println("Too high. Try again.");
                } 
                else 
                {
                    System.out.println("Too low. Try again.");
                }
            }
            if (!guessedCorrectly) 
            {
                System.out.println("Sorry, you've used all attempts. The correct number was " + genNo);
            }
            totalAttempts += attempts;
            System.out.print("Do you want to play another round? (yes/no): ");
            String response = sc.next();
            playAgain = response.equalsIgnoreCase("yes");
        }
        System.out.println("User's Score:");
        System.out.println("Total attempts taken: " + totalAttempts);
        System.out.println("Total rounds played: " + totalRounds);
        sc.close();
    }
}
