import java.util.Scanner;
public class EmpresaEstoque {
    public static void main(String[] args) {
        Scanner dados = new Scanner(System.in);
        int acao , escolhaEmpresa;
        double estoqueIn_J = 100, estoqueIn_P = 50;
        double estoqueEJ = estoqueIn_J , estoqueEP = estoqueIn_P ;
        double estoqueSJ =0,estoqueSP =0;
        double transferenciaJ=0,transferenciaP=0;
        double estoqueFinalJ=estoqueIn_J,estoqueFinalP=estoqueIn_P;

        do {
            System.out.println(">> ESCOLHA UMA OPCAO <<");
            System.out.println("1 - entrada de estoque");
            System.out.println("2 - saida de estoque");
            System.out.println("3 - transferencia de estoque");
            System.out.println("4 - consultar estoque");
            System.out.println("5 - sair");
            acao = dados.nextInt();

            if(acao==1){
                do {
                    System.out.println("1 - Jatiboca");
                    System.out.println("2 - Pontal");
                    System.out.println("5 - Voltar");
                    escolhaEmpresa = dados.nextInt();

                    if (escolhaEmpresa == 1) {
                        System.out.println("Informe a quantidade de acucar de entrada para Jatiboca:");
                        double entrada = dados.nextDouble();
                        estoqueEJ += entrada;

                    } else if (escolhaEmpresa == 2) {
                        System.out.println("Informe a quantidade de acucar de entrada para Pontal:");
                        double entrada = dados.nextDouble();
                        estoqueEP += entrada;

                    } else if (escolhaEmpresa == 5)
                        System.out.println("Voltar");
                    else
                        System.out.println("Numero Invalido");
                } while (escolhaEmpresa != 5);

            } else if (acao == 2) {
                do {
                    System.out.println("1 - Jatiboca");
                    System.out.println("2 - Pontal");
                    System.out.println("5 - voltar");
                    escolhaEmpresa = dados.nextInt();

                    if (escolhaEmpresa == 1) {
                        System.out.println("Informe a quantidade de saida/acucar Jatiboca:");
                        double saida = dados.nextDouble();

                        if(estoqueFinalJ>=estoqueSJ){
                             estoqueSJ+=saida;
                             estoqueFinalJ= estoqueEJ-estoqueSJ+transferenciaJ-transferenciaP;;

                        }
                        else {
                            System.out.println("Nao ha estoque suficiente para fazer a saida");
                        }
                    } else if (escolhaEmpresa == 2) {
                        System.out.println("Informe a quantidade de saida/acucar Pontal:");
                        double saida = dados.nextDouble();

                        if(estoqueFinalP>=saida) {
                            estoqueSP += saida;
                            estoqueFinalP = estoqueEP - estoqueSP + transferenciaP - transferenciaJ;

                        } else {
                            System.out.println("Nao ha estoque suficiente para fazer a saida");
                        }

                    } else if (escolhaEmpresa == 5){
                        System.out.println("Voltar");
                    } else
                        System.out.println("numero invalido");
                } while (escolhaEmpresa != 5);

            } else if (acao == 3) {
                do {
                    System.out.println(">> TRANSFERENCIA <<");
                    System.out.println("1 - Tranferir de Jatiboca para Pontal");
                    System.out.println("2 - Transferir de Pontal para Jatiboca");
                    System.out.println("5 - Voltar");
                    escolhaEmpresa = dados.nextInt();

                    if (escolhaEmpresa == 1) {
                        System.out.println("Informe a quantidade de acucar que sera transferido para Pontal:");
                        double transferencia = dados.nextDouble();

                        if(estoqueFinalJ>=transferencia){
                           transferenciaJ+=transferencia;
                           estoqueFinalJ-=transferencia;
                           estoqueFinalP+=transferencia;
                        }
                        else {
                            System.out.println("Nao ha estoque suficiente para fazer a transferencia");
                        }

                    } else if (escolhaEmpresa == 2) {
                        System.out.println("Informe a quantidade de acucar que sera transferido para Jatiboca:");
                        double transferencia = dados.nextDouble();

                        if(estoqueFinalP>=transferencia){
                            transferenciaP+=transferencia;
                            estoqueFinalP-=transferencia;
                            estoqueFinalJ+=transferencia;
                        }
                        else {
                            System.out.println("Nao ha estoque suficiente para fazer a transferencia");
                        }
                    } else if (escolhaEmpresa == 5) {
                        System.out.println("Voltar");
                    }
                    else
                        System.out.println("numero invalido");
                }while (escolhaEmpresa != 5);

            } else if (acao == 4) {
                do {
                    System.out.println(" >> CONSULTA DE ESTOQUE <<");
                    System.out.println("1 - Jatiboca");
                    System.out.println("2 - Pontal");
                    System.out.println("5 - voltar");
                    escolhaEmpresa = dados.nextInt();

                    if (escolhaEmpresa == 1) {
                        estoqueFinalJ = (estoqueEJ - estoqueSJ) + (transferenciaP - transferenciaJ);
                        if(estoqueFinalJ<=0)
                            System.out.println("Estoque zerado");
                        else
                            System.out.println("O estoque de Jatiboca e: " + estoqueFinalJ);

                    } else if (escolhaEmpresa == 2) {
                        estoqueFinalP = estoqueEP - estoqueSP + transferenciaJ -transferenciaP;
                        if(estoqueFinalP<=0)
                            System.out.println("Estoque zerado");
                        else
                            System.out.println("O estoque de Pontal e: " + estoqueFinalP);

                    } else if (escolhaEmpresa == 5) {
                        System.out.println("Voltar");
                    }
                } while (escolhaEmpresa != 5);
            } else if (acao == 5)
                System.out.println("Sair");
            else
                System.out.println("Numero Invalido");
        }while (acao != 5);
    }
}
