# GerenciamentoDeNumeros
```java
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
```
