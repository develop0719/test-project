import java.util.Scanner;

public class RockPaperScissorsGame3 {
    public static void main(String[] args) {
        String[] choices = {"가위", "바위", "보"};
        Scanner sc = new Scanner(System.in);

        System.out.print("가위, 바위, 보 중 하나를 선택하세요: ");
        String userInput = sc.next();

        int userChoice = -1;
        if (userInput.equals("가위")) {
            userChoice = 0;
        } else if (userInput.equals("바위")) {
            userChoice = 1;
        } else if (userInput.equals("보")) {
            userChoice = 2;
        }

        if (userChoice == -1) {
            System.out.println("잘못된 입력입니다.");
            sc.close();
            return;
        }

        int computerChoice = (int) (Math.random() * 3);
        System.out.println("당신: " + choices[userChoice]);
        System.out.println("컴퓨터: " + choices[computerChoice]);

        // 승패 배열: 0은 비김, 1은 사용자 승리, 2는 컴퓨터 승리
        int[][] resultMatrix = {
            {0, 2, 1}, // 가위 (0)
            {1, 0, 2}, // 바위 (1)
            {2, 1, 0}  // 보 (2)
        };

        int result = resultMatrix[userChoice][computerChoice];

        if (result == 0) {
            System.out.println("결과: 비겼습니다.");
        } else if (result == 1) {
            System.out.println("결과: 당신이 이겼습니다!");
        } else {
            System.out.println("결과: 당신이 졌습니다.");
        }

        sc.close();
    }
}
