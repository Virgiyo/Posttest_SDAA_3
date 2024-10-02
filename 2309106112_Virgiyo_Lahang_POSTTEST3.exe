#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Node {
    char namaPelanggan[50];
    int jumlahToken;
    float hargaToken;
    struct Node *next;
} Node;

void tambahTopUp(Node **head);
void tampilkanTopUp(Node *head);
void updateTopUp(Node *head);
void hapusTopUp(Node **head);
void freeList(Node **head);

int main() {
    Node *headNode = NULL;
    int menuOption;

    do {
        printf("\n--- Menu Top-Up Token Game ---\n");
        printf("1. Nambah Top up\n");
        printf("2. Tampilkan Data Top-Up\n");
        printf("3. Update Data Top-Up\n");
        printf("4. Hapus Data Top-Up\n");
        printf("5. Keluar\n");
        printf("Pilih opsi: ");
        scanf("%d", &menuOption);

        switch (menuOption) {
            case 1:
                tambahTopUp(&headNode);
                break;
            case 2:
                tampilkanTopUp(headNode);
                break;
            case 3:
                updateTopUp(headNode);
                break;
            case 4:
                hapusTopUp(&headNode);
                break;
            case 5:
                printf("Keluar dari program.\n");
                break;
            default:
                printf("Pilihan tidak valid.\n");
                break;
        }
    } while (menuOption != 5);

    freeList(&headNode);
    return 0;
}

void tambahTopUp(Node **head) {
    Node *newNode = (Node *)malloc(sizeof(Node));
    if (newNode == NULL) {
        printf("Memory tidak cukup!\n");
        return;
    }

    printf("Masukkan nama pelanggan: ");
    scanf("%s", newNode->namaPelanggan);
    printf("Masukkan jumlah token: ");
    scanf("%d", &newNode->jumlahToken);
    printf("Masukkan harga token: ");
    scanf("%f", &newNode->hargaToken);

    newNode->next = *head;
    *head = newNode;
    printf("Data top-up berhasil ditambahkan!\n");
}

void tampilkanTopUp(Node *head) {
    if (head == NULL) {
        printf("Tidak ada data top-up.\n");
        return;
    }

    Node *currentNode = head;
    int dataCount = 1;
    while (currentNode != NULL) {
        printf("\nData Top-Up ke-%d\n", dataCount++);
        printf("Nama Pelanggan: %s\n", currentNode->namaPelanggan);
        printf("Jumlah Token: %d\n", currentNode->jumlahToken);
        printf("Harga Token: %.2f\n", currentNode->hargaToken);
        currentNode = currentNode->next;
    }
}

void updateTopUp(Node *head) {
    int dataIndex, dataCount = 1;
    Node *currentNode = head;

    printf("Masukkan nomor data top-up yang ingin diupdate (1-%d): ", dataCount);
    
    while (currentNode != NULL) {
        currentNode = currentNode->next;
        dataCount++;
    }
    
    scanf("%d", &dataIndex);

    if (dataIndex < 1 || dataIndex > dataCount - 1) {
        printf("Nomor top-up tidak valid.\n");
        return;
    }

    currentNode = head;
    for (int i = 1; i < dataIndex; i++) {
        currentNode = currentNode->next;
    }

    printf("Masukkan nama pelanggan baru: ");
    scanf("%s", currentNode->namaPelanggan);
    printf("Masukkan jumlah token baru: ");
    scanf("%d", &currentNode->jumlahToken);
    printf("Masukkan harga token baru: ");
    scanf("%f", &currentNode->hargaToken);

    printf("Data top-up berhasil diperbarui!\n");
}

void hapusTopUp(Node **head) {
    int dataIndex;
    printf("Masukkan nomor data top-up yang ingin dihapus: ");
    scanf("%d", &dataIndex);

    if (dataIndex < 1 || *head == NULL) {
        printf("Nomor top-up tidak valid.\n");
        return;
    }

    Node *currentNode = *head;

    if (dataIndex == 1) {
        *head = currentNode->next;
        free(currentNode);
        printf("Data top-up berhasil dihapus!\n");
        return;
    }

    for (int i = 1; currentNode != NULL && i < dataIndex - 1; i++) {
        currentNode = currentNode->next;
    }

    if (currentNode == NULL || currentNode->next == NULL) {
        printf("Nomor top-up tidak valid.\n");
        return;
    }

    Node *nextNode = currentNode->next->next;
    free(currentNode->next);
    currentNode->next = nextNode;

    printf("Data top-up berhasil dihapus!\n");
}

void freeList(Node **head) {
    Node *currentNode = *head;
    Node *nextNode;

    while (currentNode != NULL) {
        nextNode = currentNode->next;
        free(currentNode);
        currentNode = nextNode;
    }
    *head = NULL;
}

