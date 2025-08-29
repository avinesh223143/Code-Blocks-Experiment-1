# Code-Blocks-Experiment-1
Implementation of Go-Back-N Protocol – Sliding Window

🎯 Aim

To write and execute a program for the Go-Back-N protocol using the sliding window technique.

🛠️ Equipments Required

• 	Personal Computer

• 	Turbo C Compiler

📋 Procedure
1. 	Connect two computers in a Wired/Wireless LAN.
2. 	Ensure both machines are on the same network and can ping each other.
3. 	Open a new C file in Code::Blocks or any C IDE and type the program.
4. 	Navigate to:
Project -> Properties -> Project Build Options -> Linker Settings
Add: netproto and pthread
5. 	Execute the program on both server and client machines.
6. 	Enter:
• 	IP address of the remote machine
• 	Port address of both local and remote machines
• 	Error rate
7. 	Choose the file and verify the Go-Back-N protocol operation.

💻 Program
~~~
#include <stdio.h>

#define window_size 4 // fixed sliding window size

int main() {
    int i, window_start = 1, ack, n;

    printf("SLIDING WINDOW PROTOCOL\n");
    printf("GO BACK N ARQ\n");

    printf("Enter the number of frames: ");
    scanf("%d", &n);

    char frame[n + 1][10]; // frame storage (1-indexed)

    for (i = 1; i <= n; i++) {
        printf("Content for frame %d: ", i);
        scanf("%s", frame[i]);
    }

    while (window_start <= n) {
        // send all frames in current window
        printf("\nSending frames: ");
        for (i = window_start; i < window_start + window_size && i <= n; i++) {
            printf("Frame %d(%s) ", i, frame[i]);
        }
        printf("\n");

        // ask for ack
        printf("Enter frame number with NO ACK (or 0 if all ACKs received): ");
        scanf("%d", &ack);

        if (ack == 0) {
            printf("All frames acknowledged. Moving window forward.\n");
            window_start += window_size; // slide window
        } else if (ack >= window_start && ack < window_start + window_size && ack <= n) {
            printf("No acknowledgement for frame %d...\n", ack);
            printf("Resending frames starting from frame %d.\n", ack);
            window_start = ack; // restart from unacked frame
        } else {
            printf("Invalid input, try again.\n");
        }
    }

    printf("\nAll frames sent successfully.\n");

    // pause before closing
    printf("Press Enter to exit...");
    getchar();  // consume leftover newline
    getchar();  // wait for user to press Enter

    return 0;
}
~~~

🖥️ Sample Output
<img width="1920" height="1080" alt="Screenshot 2025-08-29 092807" src="https://github.com/user-attachments/assets/aee782c9-e125-41f1-a025-d97fbca0afbe" />

✅ Result

Thus, the Go-Back-N protocol using the sliding window technique was successfully implemented and verified.

Github link : https://github.com/Rlokeshwar/Code-Blocks-Experiment-1/blob/main/README.md
