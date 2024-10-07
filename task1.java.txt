import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int score = 0;
        int round = 1;

        while (true) {
            // Generate a random number between 1 and 100
            int number = random.nextInt(100) + 1;

            // Limit the number of attempts to 10
            int attempts = 10;

            System.out.println("Round " + round + "!");
            System.out.println("I have generated a random number between 1 and 100.");
            System.out.println("You have 10 attempts to guess the number.");

            // Loop until the user has made 10 attempts
            for (int i = 0; i < attempts; i++) {
                System.out.print("Enter your guess (1-100): ");
                int guess = scanner.nextInt();

                // Compare the user's guess with the generated number
                if (guess < number) {
                    System.out.println("Too low!");
                } else if (guess > number) {
                    System.out.println("Too high!");
                } else {
                    System.out.println("Correct!");
                    score++;
                    break;
                }
            }

            // Ask the user if they want to play again
            System.out.print("Do you want to play again? (yes/no) ");
            String playAgain = scanner.next();

            // If the user wants to play again, restart the game
            if (playAgain.equalsIgnoreCase("yes")) {
                round++;
            } else {
                break;
            }
        }

        System.out.println("Thanks for playing! Your score is: " + score);
    }
}