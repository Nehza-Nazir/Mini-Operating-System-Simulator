#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <pthread.h>
#include <dirent.h>
#include <sys/stat.h>
#include <ctype.h>
#include <time.h>

// Function declarations
void play_song(), play_video(), create_directory(), create_file(), open_with_nano();
void read_file(), delete_file(), list_files(), calculator(), notepad();
void system_details(), bmi_calculator(), fahrenheit_to_celsius(), guess_game();
void copy_move_file(), show_kernel_specs(); void launch_in_new_terminal(const char *arg);

void handle_function(const char *func) {
    if (strcmp(func, "song") == 0) play_song();
    else if (strcmp(func, "video") == 0) play_video();
    else if (strcmp(func, "mkdir") == 0) create_directory();
    else if (strcmp(func, "mkfile") == 0) create_file();
    else if (strcmp(func, "nano") == 0) open_with_nano();
    else if (strcmp(func, "read") == 0) read_file();
    else if (strcmp(func, "delete") == 0) delete_file();
    else if (strcmp(func, "list") == 0) list_files();
    else if (strcmp(func, "copy") == 0) copy_move_file();
    else if (strcmp(func, "calc") == 0) calculator();
    else if (strcmp(func, "notepad") == 0) notepad();
    else if (strcmp(func, "sys") == 0) system_details();
    else if (strcmp(func, "bmi") == 0) bmi_calculator();
    else if (strcmp(func, "ftc") == 0) fahrenheit_to_celsius();
    else if (strcmp(func, "guess") == 0) guess_game();
    else printf("Invalid function command.\n");
}



void launch_in_new_terminal(const char *arg) {
    char cmd[256];
    snprintf(cmd, sizeof(cmd), "gnome-terminal -- bash -c './miniOS %s; exec bash'", arg);
    system(cmd);
}



int main(int argc, char *argv[]) {
    if (argc > 1) {
        handle_function(argv[1]);
        return 0;
    }
 printf("\n");
 printf("\n");
 printf("\n");
 printf("\n");
 printf("\n");
 printf("\n");
    printf("\n                         =====================================\n");
    printf("                          🖥️  Welcome to Mini OS Simulation 🧠\n");
    printf("                         =====================================\n");
    printf("                    Developed by: Amama and Nehza 23f-6014 and 23f-0822 \n");
    printf("\n");
    printf ("                   A wonderful realm of  : ⚙️  🖥️ 🌡️ 📝  🧮  🎮 🎵 📁 💻 ✨  \n");
    printf("\n");
    printf("           Features: Media Playback, File Management Utilities, Games and more!\n");
    printf("                       ========================================\n");
 printf("\n");
 printf("\n");
 printf("\n");
 printf("\n");
 printf("\n");
 printf("\n");
 printf("\n");
   
    sleep(5);
    char mode[20];
    printf("Choose mode (user/kernel): ");
    scanf("%s", mode);

    if (strcasecmp(mode, "kernel") == 0) {
        show_kernel_specs();
        return 0;
    }

    int choice;
    do {
        printf("\n                                  ============================\n");
        printf("                                     🌟 Mini OS - Main Menu 🌟\n");
        printf("                                  ============================\n");
        printf("1. 🎵 Play song\n2. 🎬 Play video\n3. 📁 Create directory\n4. 📄 Create file\n5. 📝 Open file with nano\n");
        printf("6. 📖 Read file\n7. ❌ Delete file\n8. 📂 List files\n9. 📄 Copy & Move File\n10. 🧮 Calculator\n");
        printf("11. 📝 Notepad\n12. 🖥️ System details\n13. ⚖️ BMI calculator\n14. 🌡️ Fahrenheit to Celsius\n15. 🎮 Word Guessing Game\n");
        printf("16. 🚪 Exit\nYour choice: ");

        if (scanf("%d", &choice) != 1) {
            printf("Invalid input! Please enter a number.\n");
            while(getchar() != '\n');
            continue;
        }

        switch (choice) {
            case 1: launch_in_new_terminal("song"); break;
            case 2: launch_in_new_terminal("video"); break;
            case 3: launch_in_new_terminal("mkdir"); break;
            case 4: launch_in_new_terminal("mkfile"); break;
            case 5: launch_in_new_terminal("nano"); break;
            case 6: launch_in_new_terminal("read"); break;
            case 7: launch_in_new_terminal("delete"); break;
            case 8: launch_in_new_terminal("list"); break;
            case 9: launch_in_new_terminal("copy"); break;
            case 10: launch_in_new_terminal("calc"); break;
            case 11: launch_in_new_terminal("notepad"); break;
            case 12: launch_in_new_terminal("sys"); break;
            case 13: launch_in_new_terminal("bmi"); break;
            case 14: launch_in_new_terminal("ftc"); break;
            case 15: launch_in_new_terminal("guess"); break;
            case 16: printf("\n          Thank you so much for using our OS Allah Hafiz See you next time.😊✨ \n\n                    shutting down.......\n\n")  ; break;
            default: printf("Invalid choice! Please select a number between 1 and 16.\n"); break;
        }
    } while (choice != 16);

    return 0;
}






















































































void play_song() {
    char filename[100];
    printf("\n🎵 Enter the name of the song file (e.g., havana.mp3): ");
    scanf("%s", filename);
    char cmd[256];
    snprintf(cmd, sizeof(cmd), "mpg123 /home/ns3/Music/%s", filename);
    system(cmd);
}

void play_video() {
    char filename[100];
    printf("\n🎬 Enter the name of the video file (e.g., video.mp4): ");
    scanf("%s", filename);
    char cmd[256];
    snprintf(cmd, sizeof(cmd), "mpv /home/ns3/Videos/%s", filename);
    system(cmd);
}

void create_directory() {
    char dirname[100];
    printf("\n📁 Enter directory name: ");
    scanf("%s", dirname);
    if (mkdir(dirname, 0777) == 0)
        printf("Directory '%s' created successfully.\n", dirname);
    else
        perror("Error creating directory");
}

void create_file() {
    char filename[100];
    printf("\n📄 Enter file name to create: ");
    scanf("%s", filename);
    FILE *fp = fopen(filename, "w");
    if (fp) {
        printf("File '%s' created successfully.\n", filename);
        fclose(fp);
    } else {
        perror("Error creating file");
    }
}

void open_with_nano() {
    char filename[100];
    printf("\n📝 Enter file name to open with nano: ");
    scanf("%s", filename);
    char cmd[150];
    snprintf(cmd, sizeof(cmd), "nano %s", filename);
    system(cmd);
}

void read_file() {
    char filename[100];
    printf("\n📖 Enter file name to read: ");
    scanf("%s", filename);
    FILE *fp = fopen(filename, "r");
    if (!fp) {
        perror("Unable to open file");
        return;
    }
    char ch;
    while ((ch = fgetc(fp)) != EOF) putchar(ch);
    fclose(fp);
}

void delete_file() {
    char filename[100];
    printf("\n❌ Enter file name to delete: ");
    scanf("%s", filename);
    if (remove(filename) == 0)
        printf("File '%s' deleted successfully.\n", filename);
    else
        perror("Error deleting file");
}

void list_files() {
    DIR *d;
    struct dirent *dir;
    d = opendir(".");
    if (d) {
        printf("\n📂 Listing files in current directory:\n");
        while ((dir = readdir(d)) != NULL) {
            if (dir->d_type == DT_REG)
                printf("- %s\n", dir->d_name);
        }
        closedir(d);
    }
}

void copy_move_file() {
    char src[100], dest[100];
    printf("\n📄 Enter source file name: ");
    scanf("%s", src);
    printf("Enter destination file name: ");
    scanf("%s", dest);

    FILE *fsrc = fopen(src, "r");
    FILE *fdest = fopen(dest, "w");
    if (!fsrc || !fdest) {
        perror("Error");
        return;
    }
    char ch;
    while ((ch = fgetc(fsrc)) != EOF) fputc(ch, fdest);
    fclose(fsrc);
    fclose(fdest);
    printf("File copied to %s.\n", dest);
}

void calculator() {
    double a, b;
    char op;
    printf("\n🧮 Enter expression (e.g., 2 + 3): ");
    scanf("%lf %c %lf", &a, &op, &b);
    switch (op) {
        case '+': printf("Result: %.2lf\n", a + b); break;
        case '-': printf("Result: %.2lf\n", a - b); break;
        case '*': printf("Result: %.2lf\n", a * b); break;
        case '/': if (b != 0) printf("Result: %.2lf\n", a / b);
                  else printf("Cannot divide by zero!\n");
                  break;
        default: printf("Invalid operator.\n");
    }
}

void notepad() {
 system("nano");
}

void system_details() {
    printf("\n🖥️ System Information:\n");
    system("uname -a");
}

void bmi_calculator() {
    float weight, height;
    printf("\n⚖️ Enter your weight (kg): ");
    scanf("%f", &weight);
    printf("Enter your height (m): ");
    scanf("%f", &height);
    float bmi = weight / (height * height);
    printf("Your BMI is: %.2f\n", bmi);
    if (bmi < 18.5) printf("You are underweight.\n");
    else if (bmi < 24.9) printf("You are healthy.\n");
    else if (bmi < 29.9) printf("You are overweight.\n");
    else printf("You are obese.\n");
}

void fahrenheit_to_celsius() {
    float f;
    printf("\n🌡️ Enter temperature in Fahrenheit: ");
    scanf("%f", &f);
    float c = (f - 32) * 5 / 9;
    printf("Temperature in Celsius: %.2f\n", c);
}

void guess_game() {
    char p1name[50], p2name[50];
    printf("\n🎮 Welcome to the Word Guessing Game!\n");
    printf("Enter Player 1 name: ");
    scanf("%s", p1name);
    printf("Enter Player 2 name: ");
    scanf("%s", p2name);

    const char *words[] = {"intelligent", "osproject", "amama", "nehza", "coding", "terminal", "linux", "compile", "function", "computer"};
    int guessed[10] = {0};
    int p1 = 0, p2 = 0, turn = 0, round = 0;
    srand(time(NULL));

    while (p1 < 4 && p2 < 4 && round < 10) {
        int idx;
        do { idx = rand() % 10; } while (guessed[idx]);
        guessed[idx] = 1;
        const char *word = words[idx];
        int len = strlen(word);
        printf("\n%s's turn!\n", turn == 0 ? p1name : p2name);
        if (rand() % 2 == 0) {
            printf("Guess the word that starts with '%.*s': ", len/2, word);
        } else {
            printf("Guess the word that ends with '%.*s': ", len - len/2, word + len/2);
        }
        char guess[100];
        scanf("%s", guess);
        if (strcmp(guess, word) == 0) {
            printf("Correct!\n");
            if (turn == 0) p1++; else p2++;
        } else {
            printf("Incorrect. The correct word was: %s\n", word);
        }
        printf("%s score: %d | %s score: %d\n", p1name, p1, p2name, p2);
        turn = 1 - turn;
        round++;
    }
    if (p1 >= 4) printf("%s wins!\n", p1name);
    else if (p2 >= 4) printf("%s wins!\n", p2name);
    else printf("Game over! No winner.\n");
}

void show_kernel_specs() {
    printf("\n🧠 Kernel Mode Specifications:\n");
    printf("🧬 CPU Cores:\n");
    system("nproc");

    printf("💾 RAM Info (in GB):\n");
    system("free -g | awk '/Mem:/ {print $2 \" GB RAM\"}'");

    printf("🖴 HDD Info:\n");
    system("lsblk -o NAME,SIZE,TYPE | grep disk");
}


