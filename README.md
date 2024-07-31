import java.util.Scanner;

public class LAB_4 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter the number of elements (n): ");
        int n = input.nextInt();
        int[] weights = new int[n];

        System.out.println("Enter the weights:");
        for (int i = 0; i < n; i++) {
            weights[i] = input.nextInt();
        }

        int minDifference = Integer.MAX_VALUE;

        for (int i = 0; i < (1 << n); i++) {
            int sumA = 0, sumB = 0;
            for (int j = 0; j < n; j++) {
                if ((i & (1 << j)) > 0) {
                    sumA += weights[j];
                } else {
                    sumB += weights[j];
                }
            }
            int difference = Math.abs(sumA - sumB);
            if (difference < minDifference) {
                minDifference = difference;
            }
        }

        System.out.println("The minimum difference is: " + minDifference);
        input.close();
    }
}
