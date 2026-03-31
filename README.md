# GerenciamentoDeNumeros
```java

//MAIN

import java.util.Scanner;

public class TestaNumero {

    public static void main(String[] args) {
        Scanner ler = new Scanner(System.in);
        Numero numeros = new Numero();
        int opcao;

        do {
            exibirMenu();
            opcao = ler.nextInt();
            ler.nextLine(); 

            switch (opcao) {
                case 1: 
                    System.out.print("Digite o número a ser adicionado: ");
                    int num = ler.nextInt();
                    numeros.adicionarNumero(num);
                    break;

                case 2: 
                    numeros.listarNumeros();
                    break;

                case 3: 
                    numeros.listarPares();
                    break;

                case 4: 
                    numeros.listarImpares();
                    break;

                case 5: 
                    numeros.listarNumeros();
                    if (numeros.tamanhoLista() > 0) {
                        System.out.print("Digite o índice que deseja atualizar: ");
                        int indice = ler.nextInt();
                        System.out.print("Digite o novo número: ");
                        int novoNum = ler.nextInt();
                        numeros.atualizarNumero(indice, novoNum);
                    }
                    break;

                case 6: 
                    numeros.listarNumeros();
                    if (numeros.tamanhoLista() > 0) {
                        System.out.print("Digite o índice que deseja excluir: ");
                        int idx = ler.nextInt();
                        numeros.removerNumero(idx);
                    }
                    break;

                case 7: 
                    System.out.print("Digite o número que deseja buscar: ");
                    int busca = ler.nextInt();
                    numeros.buscarNumero(busca);
                    break;

                case 8: 
                    numeros.exibirMedia();
                    break;

                case 9: 
                    numeros.exibirMaxMin();
                    break;

                case 10: 
                    System.out.println("Escolha a ordem:");
                    System.out.println("1 - Crescente");
                    System.out.println("2 - Decrescente");
                    int ordem = ler.nextInt();
                    numeros.ordenarLista(ordem == 1);
                    break;

                case 0:
                    System.out.println("Saindo do programa... Até logo!");
                    break;

                default:
                    System.out.println("Opção inválida! Tente novamente.");
            }

            System.out.println("-----------------------------------");

        } while (opcao != 0);

        ler.close();
    }

    private static void exibirMenu() {
        System.out.println("\n=== GERENCIAMENTO DE NÚMEROS INTEIROS ===");
        System.out.println("1 - Adicionar Número");
        System.out.println("2 - Listar Números");
        System.out.println("3 - Listar Pares");
        System.out.println("4 - Listar Ímpares");
        System.out.println("5 - Atualizar Número");
        System.out.println("6 - Excluir Número");
        System.out.println("7 - Buscar Número");
        System.out.println("8 - Exibir Média dos Números");
        System.out.println("9 - Exibir Número Máximo e Mínimo");
        System.out.println("10 - Ordenar Lista");
        System.out.println("0 - Sair");
        System.out.print("Escolha uma opção: ");
    }
}





import java.util.ArrayList;
import java.util.Collections;

//JAVA

public class Numero {

    private ArrayList<Integer> listaNumeros;

    public Numero() {
        this.listaNumeros = new ArrayList<>();
    }

    public void adicionarNumero(int numero) {
        listaNumeros.add(numero);
        System.out.println("Número " + numero + " adicionado com sucesso!");
    }

    public void listarNumeros() {
        if (listaNumeros.isEmpty()) {
            System.out.println("A lista está vazia.");
            return;
        }
        System.out.println("Números na lista:");
        for (int i = 0; i < listaNumeros.size(); i++) {
            System.out.println("[" + i + "] = " + listaNumeros.get(i));
        }
    }

    public void listarPares() {
        if (listaNumeros.isEmpty()) {
            System.out.println("A lista está vazia.");
            return;
        }
        System.out.println("Números pares:");
        boolean temPar = false;
        for (int num : listaNumeros) {
            if (num % 2 == 0) {
                System.out.println(num);
                temPar = true;
            }
        }
        if (!temPar) {
            System.out.println("Não há números pares na lista.");
        }
    }

    public void listarImpares() {
        if (listaNumeros.isEmpty()) {
            System.out.println("A lista está vazia.");
            return;
        }
        System.out.println("Números ímpares:");
        boolean temImpar = false;
        for (int num : listaNumeros) {
            if (num % 2 != 0) {
                System.out.println(num);
                temImpar = true;
            }
        }
        if (!temImpar) {
            System.out.println("Não há números ímpares na lista.");
        }
    }

    public void atualizarNumero(int indice, int novoNumero) {
        if (indice < 0 || indice >= listaNumeros.size()) {
            System.out.println("Índice inválido!");
            return;
        }
        int antigo = listaNumeros.get(indice);
        listaNumeros.set(indice, novoNumero);
        System.out.println("Número na posição " + indice + " alterado de " + antigo + " para " + novoNumero);
    }

    public void removerNumero(int indice) {
        if (indice < 0 || indice >= listaNumeros.size()) {
            System.out.println("Índice inválido!");
            return;
        }
        int removido = listaNumeros.remove(indice);
        System.out.println("Número " + removido + " removido com sucesso!");
    }

    public void buscarNumero(int numero) {
        if (listaNumeros.contains(numero)) {
            System.out.println("O número " + numero + " está presente na lista.");
        } else {
            System.out.println("O número " + numero + " NÃO foi encontrado na lista.");
        }
    }

    public void exibirMedia() {
        if (listaNumeros.isEmpty()) {
            System.out.println("A lista está vazia. Não é possível calcular a média.");
            return;
        }
        double soma = 0;
        for (int num : listaNumeros) {
            soma += num;
        }
        double media = soma / listaNumeros.size();
        System.out.printf("Média dos números: %.2f%n", media);
    }

    public void exibirMaxMin() {
        if (listaNumeros.isEmpty()) {
            System.out.println("A lista está vazia.");
            return;
        }
        int max = Collections.max(listaNumeros);
        int min = Collections.min(listaNumeros);
        System.out.println("Maior número: " + max);
        System.out.println("Menor número: " + min);
    }

private boolean ordemCrescente = true;

public void ordenarLista(boolean crescente) {
    if (listaNumeros.isEmpty()) {
        System.out.println("A lista está vazia.");
        return;
    }

    ordemCrescente = crescente;

    if (ordemCrescente) {
        Collections.sort(listaNumeros);
        System.out.println("Lista ordenada em ordem crescente.");
    } else {
        listaNumeros.sort(Collections.reverseOrder());
        System.out.println("Lista ordenada em ordem decrescente.");
    }

    listarNumeros();
}

    public int tamanhoLista() {
        return listaNumeros.size();
    }
}

```
