// Estrutura de Dados — Algoritmos de Ordenação

Este repositório contém um projeto desenvolvido durante a disciplina de Estrutura de Dados I, com o objetivo de estudar e 
implementar diferentes algoritmos de ordenação utilizando a linguagem C.
O projeto permite criar e manipular um vetor de números e comparar, na prática, diferentes métodos de ordenação:

* Bubble Sort
* Selection Sort
* Insertion Sort
* Quick Sort

Além dos algoritmos de ordenação, o programa possui um menu interativo que permite inserir valores manualmente, 
gerar valores aleatórios, visualizar o vetor e limpá-lo.
Objetivo do projeto

O principal objetivo foi compreender como funcionam diferentes algoritmos de ordenação e praticar conceitos fundamentais de 
Estruturas de Dados e Algoritmos. //


#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <time.h>

float vetor[1000];
int Qtd = 0;

int imprimeMenu() {
  system("cls");
  printf("\n ======= EXERCICIO DE ORDENACAO ======== ");
  printf("\n =  1: Preencher o Vetor               = ");
  printf("\n =  2: Limpar o Vetor                  = ");
  printf("\n =  3: Imprimir o Vetor                = ");
  printf("\n =  4: Ordenar Buble Sort              = ");
  printf("\n =  5: Ordenar Selection Sort          = ");
  printf("\n =  6: Ordenar Insertion Sort          = ");
  printf("\n =  7: Ordenar Quick Sort              = ");
  printf("\n =  8: Preencher Vetor Aleatoriamente  = ");
  printf("\n =  9: Sair                            = ");
  printf("\n ======================================= ");
  printf("\n Informe a opcao desejada: ");
  int resposta;
  scanf("%i", &resposta);
  return(resposta);
}

void vetorAleatorio(int Tamanho){
  for (int i=0; i<Tamanho; i++)
	vetor[i] = (rand() %100);                            // A função rand() "randomic" gera um número
  printf("\n %i numeros gerados com sucesso!",Tamanho);  // aleatório com base no DateTime do Sistema
  Qtd = Tamanho;                                         // (por isso, usar a biblioteca time.h)
  getch();
}

void bubbleSort() {
  float aux;
  for (int i=0; i<Qtd-1; i++)
    for (int j=0; j<Qtd-1 -i; j++)
      if (vetor[j] > vetor[j+1]) {
        aux = vetor[j];
        vetor[j] = vetor[j+1];
        vetor[j+1] = aux;
      }
}

void selectionSort() { 
float aux;
  for (int i=0; i<Qtd-1; i++)
    for (int j=i+1; j<Qtd; j++)
      if (vetor[j] < vetor[i]) {
        aux = vetor[j];
        vetor[j] = vetor[i];
        vetor[i] = aux;
      }
}

void insertionSort() {
int i, j;
float aux;
    for (i=1; i<Qtd; i++) {
        aux = vetor[i];
        j = i-1;
        while (j>=0 && vetor[j]>aux) {
            vetor[j+1] = vetor[j];
            j=j-1;
        }
        vetor[j+1] = aux;
    }
}

void quickSort(int esquerda, int direita){
int i, j;
float pivo, temp;
i = esquerda;
j = direita;
    pivo = vetor[(esquerda + direita) / 2];
    while(i <= j){
        while(vetor[i] < pivo && i < direita) i++;
        while(vetor[j] > pivo && j > esquerda) j--;
        if(i <= j){
            temp = vetor[i];
            vetor[i] = vetor[j];
            vetor[j] = temp;
            i++;
            j--;
        }
    }
    if(j > esquerda)
       quickSort(esquerda, j);
    if(i < direita)
       quickSort(i, direita);
}

void limparVetor() {
  for (int i=0; i<Qtd; i++)
    vetor[i] = 0;
  printf("\n Vetor zerado com sucesso! \n");
}

void imprimirVetor() {
  printf("\n Dados do Vetor: \n");
  for (int i=0; i<Qtd; i++)
	if (i==Qtd-1)
      printf("%.2f ", vetor[i]);
    else
      printf("%.2f, ", vetor[i]);
  getch();
}

int main() {
  char menu;
  int resposta;
  do {
	resposta = imprimeMenu();
		if (resposta == 1) {
	  do {
        printf("Insira o %i. valor no vetor: ", Qtd+1);
        scanf("%f", &vetor[Qtd]);
        Qtd+=1;
        printf("Deseja inserir mais um valor? (S/N): ");
        scanf("%s", &menu);
       } while (menu == 'S' || menu == 's'); }
	else if (resposta == 2)
	  limparVetor();
	else if (resposta == 3)
	  imprimirVetor();
	else if (resposta == 4)
      bubbleSort();
	else if (resposta == 5)
      selectionSort();
	else if (resposta == 6)
      insertionSort();
    else if (resposta == 7)
      quickSort(0, Qtd - 1);
	else if (resposta == 8) {
      printf("Informe o tamanho do vetor que deseja criar: ");
      int Tamanho;
      scanf("%i", &Tamanho);
      vetorAleatorio(Tamanho);
    }
  } while (resposta < 9);
}
