# NumberGuessing-Game

import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int startRange = 1;
        int endRange = 100;
        int maxAttempts = 10;
        int score = 0;
        String playAgain = "yes";
        
        while (playAgain.equalsIgnoreCase("yes") || playAgain.equalsIgnoreCase("y")) {
            int numberToGuess = random.nextInt(endRange - startRange + 1) + startRange;
            int attempts = 0;
            boolean guessedCorrectly = false;
            
            System.out.println("\nGuess the number between " + startRange + " and " + endRange + ". You have " + maxAttempts + " attempts.");
            
            while (attempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Enter your guess: ");
                int guess;
                try {
                    guess = Integer.parseInt(scanner.nextLine());
                } catch (NumberFormatException e) {
                    System.out.println("Please enter a valid number.");
                    continue;
                }
                attempts++;
                
                if (guess < numberToGuess) {
                    System.out.println("Too low.");
                } else if (guess > numberToGuess) {
                    System.out.println("Too high.");
                } else {
                    System.out.println("Correct! You've guessed the number in " + attempts + " attempts.");
                    guessedCorrectly = true;
                    score++;
                }
            }
            
            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all " + maxAttempts + " attempts. The correct number was " + numberToGuess + ".");
            }
            
            System.out.print("Do you want to play again? (yes/no): ");
            playAgain = scanner.nextLine();
        }
        
        System.out.println("\nYour score: " + score + " round(s) won.");
        scanner.close();
    }
}
