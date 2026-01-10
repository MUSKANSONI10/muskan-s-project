#include <stdio.h>

struct Pet {
    char name[20];
    int hunger;
    int happiness;
    int energy;
};

void showStatus(struct Pet p);
void feed(struct Pet *p);
void play(struct Pet *p);
void rest(struct Pet *p);

int main() {
    struct Pet p;
    int choice;

    printf("Enter pet name: ");
    scanf("%s", p.name);

    p.hunger = 50;
    p.happiness = 50;
    p.energy = 50;

    while (1) {
        printf("\n--- MY PET GAME ---\n");
        printf("1. Show Status\n");
        printf("2. Feed Pet\n");
        printf("3. Play with Pet\n");
        printf("4. Rest Pet\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        if (choice == 1)
            showStatus(p);
        else if (choice == 2)
            feed(&p);
        else if (choice == 3)
            play(&p);
        else if (choice == 4)
            rest(&p);
        else if (choice == 5)
            break;
        else
            printf("Invalid choice\n");
    }

    return 0;
}

void showStatus(struct Pet p) {
    printf("\nName: %s", p.name);
    printf("\nHunger: %d", p.hunger);
    printf("\nHappiness: %d", p.happiness);
    printf("\nEnergy: %d\n", p.energy);
}

void feed(struct Pet *p) {
    p->hunger -= 10;
    if (p->hunger < 0) p->hunger = 0;
    printf("Pet is fed.\n");
}

void play(struct Pet *p) {
    p->happiness += 10;
    p->energy -= 5;
    printf("You played with pet.\n");
}

void rest(struct Pet *p) {
    p->energy += 10;
    printf("Pet is resting.\n");
}

