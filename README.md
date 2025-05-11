import java.util.Scanner;

public class RockPaperScissorsGame {
    public static void main(String[] args) {
        // 가위, 바위, 보를 배열로 저장
        String[] choices = {"가위", "바위", "보"};
        
        // Scanner 객체 생성
        Scanner sc = new Scanner(System.in);

        // 게임을 계속할지 여부를 판단하는 변수
        boolean playAgain = true;

        while (playAgain) {
            // 사용자로부터 선택을 입력받음
            System.out.print("가위, 바위, 보 중 하나를 선택하세요: ");
            String userInput = sc.next();

            // 사용자 입력을 숫자로 변환할 수 있도록 매핑 (가위: 0, 바위: 1, 보: 2)
            int userChoice = -1;
            if (userInput.equals("가위")) {
                userChoice = 0;
            } else if (userInput.equals("바위")) {
                userChoice = 1;
            } else if (userInput.equals("보")) {
                userChoice = 2;
            }

            // if문으로 입력값 검증
            if (userChoice == -1) {
                System.out.println("잘못된 입력입니다. '가위', '바위', '보' 중 하나를 입력하세요.");
                continue; // 잘못된 입력시 다시 입력받기
            }

            // 컴퓨터의 선택을 랜덤으로 생성
            int computerChoice = (int) (Math.random() * 3);

            // 사용자의 선택과 컴퓨터의 선택 출력
            System.out.println("당신: " + choices[userChoice]);
            System.out.println("컴퓨터: " + choices[computerChoice]);

            // 결과 판별 (0: 비김, 1: 이김, 2: 짐)
            int result = (3 + userChoice - computerChoice) % 3;

            // switch-case문으로 결과 처리
            switch (result) {
                case 0:
                    System.out.println("결과: 비겼습니다.");
                    break;
                case 1:
                    System.out.println("결과: 당신이 이겼습니다!");
                    break;
                case 2:
                    System.out.println("결과: 당신이 졌습니다.");
                    break;
            }

            // 게임을 계속할지 여부 묻기
            System.out.print("다시 하시겠습니까? (y/n): ");
            char playAgainInput = sc.next().charAt(0);

            // 'y'이면 게임을 다시 시작, 아니면 종료
            if (playAgainInput == '네' || playAgainInput == '네') {
                playAgain = true;
            } else {
                playAgain = false;
                System.out.println("게임을 종료합니다. 감사합니다!");
            }
        }

        sc.close();
    }
}
