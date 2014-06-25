import java.util.Random;
import java.util.Scanner;

public class Game {

	public static void main(String[] args) {

		Scanner inputs = new Scanner(System.in);
		String color = "";
		String[] answer = { "", "", "", "" };
		
	    Random randomGenerator = new Random();
	    for (int idx = 0; idx <= 3; ++idx){
	    	int randomInt = randomGenerator.nextInt(6);
	    	//System.out.println(randomInt);
	    	if (randomInt==0){
	    		color = "black";
	    	}
	    	if (randomInt==1){
	    		color = "blue";
	    	}
	    	if (randomInt==2){
	    		color = "orange";
	    	}
	    	if (randomInt==3){
	    		color = "yellow";
	    	}
	    	if (randomInt==4){
	    		color = "pink";
	    	}
	    	if (randomInt==5){
	    		color = "green";
	    	}
	    	answer[idx] = color;
	    	//System.out.println(randomInt);
	    }
		String[] guess = new String[4];
		System.out.println("MASTERMIND"
						+ "\nEnter four colors out of black, blue, orange , yellow, pink, and green. "
						+ "\nAn output of red means correct placement and correct color. "
						+ "\nAn output of white means correct color but wrong placement. "
						+ "\nRed will take precendance over white. "
						+ "\nIf there are duplicates of x in answer and you only put one x in guess, "
						+ "\nit will only give you one red or one white.");

		for (int chances = 0; chances < 12; chances++) {
			guess[0] = inputs.nextLine();
			guess[1] = inputs.nextLine();
			guess[2] = inputs.nextLine();
			guess[3] = inputs.nextLine();
			String[] outputs = { "", "", "", "" };

			int red = 0;
			int white = 0;

			if (guess[0].equals(answer[0])) {
				outputs[0] = "red";
				red++;
			} else if (guess[0].equals(answer[1])) {
				outputs[1] = "white";
				white++;
			} else if (guess[0].equals(answer[2])) {
				outputs[2] = "white";
				white++;
			} else if (guess[0].equals(answer[3])) {
				outputs[3] = "white";
				white++;
			}

			if (guess[1].equals(answer[1])) {
				if (outputs[1].equals("white"))
					white--;
				outputs[1] = "red";
				red++;
			} else if (guess[1].equals(answer[0]) && outputs[0] != "red") {
				outputs[0] = "white";
				white++;
			} else if (guess[1].equals(answer[2]) && outputs[2].equals("")) {
				outputs[2] = "white";
				white++;
			} else if (guess[1].equals(answer[3]) && outputs[3].equals("")) {
				outputs[3] = "white";
				white++;
			}

			if (guess[2].equals(answer[2])) {
				if (outputs[2].equals("white"))
					white--;
				outputs[2] = "red";
				red++;
			} else if (guess[2].equals(answer[0]) && outputs[0].equals("")) {
				outputs[0] = "white";
				white++;
			} else if (guess[2].equals(answer[1]) && outputs[1].equals("")) {
				outputs[1] = "white";
				white++;
			} else if (guess[2].equals(answer[3]) && outputs[3].equals("")) {
				outputs[3] = "white";
				white++;
			}

			if (guess[3].equals(answer[3])) {
				if (outputs[3].equals("white"))
					white--;
				outputs[3] = "red";
				red++;
			} else if (guess[3].equals(answer[0]) && outputs[0].equals("")) {
				outputs[0] = "white";
				white++;
			} else if (guess[3].equals(answer[1]) && outputs[1].equals("")) {
				outputs[1] = "white";
				white++;
			} else if (guess[3].equals(answer[2]) && outputs[2].equals("")) {
				outputs[2] = "white";
				white++;
			}

			System.out.println("White: " + white);
			System.out.println("Red: " + red);

			if (red == 4) {
				System.out.println("You Win!");
				System.out.println("Chances left: " + (11 - chances));
				System.out.println(""
						+ "\n★░░░░░░░░░░░████░░░░░░░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░███░██░░░░░░░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░██░░░█░░░░░░░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░██░░░██░░░░░░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░░██░░░███░░░░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░░░██░░░░██░░░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░░░██░░░░░███░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░░░░██░░░░░░██░░░░░░░░░░░░★"
						+ "\n★░░░░░░░███████░░░░░░░██░░░░░░░░░░░★"
						+ "\n★░░░░█████░░░░░░░░░░░░░░███░██░░░░░★"
						+ "\n★░░░██░░░░░████░░░░░░░░░░██████░░░░★"
						+ "\n★░░░██░░████░░███░░░░░░░░░░░░░██░░░★"
						+ "\n★░░░██░░░░░░░░███░░░░░░░░░░░░░██░░░★"
						+ "\n★░░░░██████████░███░░░░░░░░░░░██░░░░★"
						+ "\n★░░░░██░░░░░░░░████░░░░░░░░░░░██░░░★"
						+ "\n★░░░░███████████░░██░░░░░░░░░░██░░░░★"
						+ "\n★░░░░░░██░░░░░░░████░░░░░██████░░░░★"
						+ "\n★░░░░░░██████████░██░░░░███░██░░░░░░★"
						+ "\n★░░░░░░░░░██░░░░░████░███░░░░░░░░░░★"
						+ "\n★░░░░░░░░░█████████████░░░░░░░░░░░░░★"
						+ "\n★░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░★");
				break;
			}

			System.out.println("Chances left: " + (11 - chances));

			if (chances == 11 && red != 4){
				System.out.println("The correct answer was: ");
				for (String correct: answer){
					System.out.println(correct);
				}
				System.out.println();
				System.out.println("Game Over!"
						+ "\n░░░░░░░░░░░█████████████░░░░░░░░"
						+ "\n░░░░░░░░░███░███░░░░░░██░░░░░░░░"
						+ "\n███░░░░░██░░░░██░██████████░░░░░░"
						+ "\n████████░░░░░░████░░░░░░░██░░░░░░"
						+ "\n████░░░░░░░░░░██░░██████████░░░░░"
						+ "\n████░░░░░░░░░░░███░░░░░░░░░██░░░"
						+ "\n████░░░░░░░░░░░██░░██████████░░░░"
						+ "\n████░░░░░░░░░░░░████░░░░░░░░█░░░"
						+ "\n████░░░░░░░░░░░░░███░░████░░█░░░"
						+ "\n█████████░░░░░░░░░░████░░░░░█░░░░"
						+ "\n███░░░░░██░░░░░░░░░░░░░█████░░░░"
						+ "\n░░░░░░░░░███░░░░░░░██████░░░░░░░"
						+ "\n░░░░░░░░░░░██░░░░░░██░░░░░░░░░░"
						+ "\n░░░░░░░░░░░░███░░░░░██░░░░░░░░░"
						+ "\n░░░░░░░░░░░░░░██░░░░██░░░░░░░░░"
						+ "\n░░░░░░░░░░░░░░░███░░░██░░░░░░░░"
						+ "\n░░░░░░░░░░░░░░░░░██░░░█░░░░░░░░"
						+ "\n░░░░░░░░░░░░░░░░░░█░░░█░░░░░░░░"
						+ "\n░░░░░░░░░░░░░░░░░░██░██░░░░░░░░"
						+ "\n░░░░░░░░░░░░░░░░░░░███░░░░░░░░░");
			}
		}

	}

}

