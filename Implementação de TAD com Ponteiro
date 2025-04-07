#include <stdio.h>
#include <stdlib.h>

// Função para buscar um elemento por índice
int buscar_elemento(int *lista, int indice, int tamanho) {
    if (indice < 0 || indice >= tamanho) {
        printf("Índice inválido!\n");
        return -1; // Valor de erro
    }
    return *(lista + indice);
}

// Função para inserir um elemento por índice
void inserir_elemento(int **lista, int indice, int valor, int *tamanho) {
    // Realocar memória para acomodar o novo elemento
    *lista = (int *)realloc(*lista, sizeof(int) * (*tamanho + 1));
    
    if (indice < 0 || indice > *tamanho) {
        printf("Índice inválido!\n");
        return;
    }
    
    // Mover elementos para abrir espaço
    for (int i = *tamanho; i > indice; i--) {
        *(*lista + i) = *(*lista + i - 1);
    }
    
    // Inserir o novo valor
    *(*lista + indice) = valor;
    (*tamanho)++;
}

// Função para remover um elemento por índice
void remover_elemento(int **lista, int indice, int *tamanho) {
    if (indice < 0 || indice >= *tamanho) {
        printf("Índice inválido!\n");
        return;
    }
    
    // Mover elementos para preencher o espaço
    for (int i = indice; i < *tamanho - 1; i++) {
        *(*lista + i) = *(*lista + i + 1);
    }
    
    // Reduzir o tamanho e realocar memória
    (*tamanho)--;
    *lista = (int *)realloc(*lista, sizeof(int) * (*tamanho));
}

int main(void) {
    int *lista = NULL;
    int tamanho = 0;
    
    // Inserindo alguns elementos de exemplo
    inserir_elemento(&lista, 0, 10, &tamanho);
    inserir_elemento(&lista, 1, 20, &tamanho);
    inserir_elemento(&lista, 2, 30, &tamanho);
    
    // Mostrando a lista
    printf("Lista inicial:\n");
    for (int i = 0; i < tamanho; i++) {
        printf("%d ", *(lista + i));
    }
    printf("\n");
    
    // Buscando um elemento
    int indice_busca = 1;
    int valor = buscar_elemento(lista, indice_busca, tamanho);
    printf("Elemento no índice %d: %d\n", indice_busca, valor);
    
    // Inserindo um novo elemento
    inserir_elemento(&lista, 1, 15, &tamanho);
    printf("Lista após inserção:\n");
    for (int i = 0; i < tamanho; i++) {
        printf("%d ", *(lista + i));
    }
    printf("\n");
    
    // Removendo um elemento
    remover_elemento(&lista, 2, &tamanho);
    printf("Lista após remoção:\n");
    for (int i = 0; i < tamanho; i++) {
        printf("%d ", *(lista + i));
    }
    printf("\n");
    
    // Liberando a memória alocada
    free(lista);
    
    return 0;
}
