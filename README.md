# DailyPlanner
//  main.c
//  DailyPlanner
//
//
#include <string.h>
#include <stdio.h>
#include <stdbool.h>
#define MAX_LINE 1024

const char* about()
{
    char *intro = "This program is to plan your days.\nSign up at first and you can\nadd plans of your days.\nThis would append this information\ninto a newly generatedtext file\non your computer. Have fun!\n";
    return intro;
}
int main(int argc, const char * argv[]) {
    int menu;
    int input;
    char username[20];
    char password[20];
    char mid[50];
    char sep[2] = ":";
    char date[100];
    char time[20];
    char things[100];
    char answer[5];
    char buffer[MAX_LINE];
    
    
    do
    {
        
        printf("---------------------------------------\n");
        printf("------------ Daily Planner ------------\n");
        printf("\n");
        printf("Welcome to Daily Planner!\n");
        printf("\n");
        printf("<1> ABOUT\n");
        printf("<2> SIGN UP\n");
        printf("<3> MAKE A PLAN\n");
        printf("<4> VIEW A PLAN\n");
        printf("<5> DELETE\n");
        printf("\n");
        printf("ENTER YOUR CHOICE: ");
        input = scanf("%d",&menu);
        if (menu > 8 || menu < 1) {
        printf("This is a wrong selection.\nPlease try with a given number.\n");
            do{
                printf("ENTER YOUR CHOICE: ");
                input = scanf("%d",&menu);
            } while (menu > 8 || menu < 1);
        }
        printf("\n");
        printf("Processing...\n");
        switch(menu)
        {
            case 1:
                printf("\n");
                printf("\n");
                printf("---------------------------------------\n");
                printf("------------ Daily Planner ------------\n");
                printf("ABOUT\n");
                printf("%s", about());
                printf("\n");
                printf("Go back to main menu? Y/N?   ");
                scanf("%s", answer);
                printf("\n");
                printf("\n");
                break;
            case 2:
                printf("\n");
                printf("\n");
                printf("---------------------------------------\n");
                printf("------------ Daily Planner ------------\n");
                printf("SIGN UP\n");
                printf("\n");
                printf("Enter your information to make an account.\n");
                printf("\n");
                printf("UserName: ");
                scanf("%s", username);
                printf("Password: ");
                scanf("%s", password);
                strcat(username, sep);
                strcpy(mid, username);
                strcat(mid, password);
                FILE *open;
                open = fopen("accountinfo.txt", "w");
                fprintf(open, "%s", mid);
                fprintf(open, "\n");
                fclose(open);
                printf("Succeed to make an account\n");
                printf("Go back to main menu? Y?N   ");
                scanf("%s", answer);
                break;
                
            case 3:
                printf("\n");
                printf("\n");
                printf("---------------------------------------\n");
                printf("------------ Daily Planner ------------\n");
                printf("Make a plan\n");
                printf("\n");
                printf("Please type with a given format.\n");
                printf("ENTER DATE [MM/DD/YYYY]: ");
                scanf("%s", date);
                printf("ENTER TIME [HH:MM]: ");
                scanf("%s", time);
                printf("Note: (Space is not allowed)\n");
                scanf("%s", things);
                FILE *edit;
                edit = fopen("accountinfo.txt", "a");
                char line[5] = "\n";
                strcat(date, line);
                strcat(date, time);
                strcat(date, line);
                strcat(date, things);
                strcat(date, line);
                strcpy(buffer, date);
                fputs(buffer, edit);
                fclose(edit);
                printf("\n");
                printf("Succeed to make a plan.\n");
                printf("Go back to main menu? Y?N   ");
                scanf("%s", answer);
                printf("\n");
                printf("\n");
                break;
            case 4:
                printf("\n");
                printf("\n");
                printf("---------------------------------------\n");
                printf("------------ Daily Planner ------------\n");
                printf("View an plan\n");
                printf("\n");
                FILE *r;
                r = fopen("accountinfo.txt", "r");
                if (NULL == r) {
                        printf("File can't be opened \n");
                    }
                 
                //printf("Content of this file are \n");
                int c;
                if (r) {
                    while ((c = getc(r)) != EOF)
                        putchar(c);
                    fclose(r);
                }
                //fclose(r);
                printf("\n");
                printf("Go back to main menu? Y?N   ");
                scanf("%s", answer);
                printf("\n");
                printf("\n");
                break;
            case 5:
                fclose(fopen("accountinfo.txt", "w"));
                printf("Delected all the contents.\n");
                printf("Go back to main menu? Y?N   ");
                scanf("%s", answer);
                printf("\n");
                printf("\n");

                
        }
    } while (strcmp(answer, "Y") == 0);
    // when the condition of while is true, keep looping

    return 0;
    
    
}


