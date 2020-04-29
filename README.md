# Atividade-caixa-eletronico
/*ATIVIDADE AC1 ADS – Construção de Algoritmos Caixa Eletrônico
Nesta atividade você deverá construir um programa na linguagem JAVA
Simulando um caixa eletronico,utilizando o git hub para guardar o código.
*/

package caixa_eletronico;
//@author Carlos

import java.util.Scanner;

import java.util.ArrayList;

public class Caixa_Eletronico {
    @SuppressWarnings("empty-statement")
    public static void main(String[] args) {
     Scanner ler = new Scanner(System.in);
       String cpf,senha,banco,agencia,conta,limpa;
       int
         principal=0,
         op,
         proximo = 0;
       boolean saida=true;
         
      double saldo=1000.0f,
             saque,
              deposito,
              transferencia;
      
      ArrayList<String> bancos = new ArrayList<String>();//LISTA DE BANCOS ACEITOS
        bancos.add("Itau");
        bancos.add("Santander");
        bancos.add("Bradesco");
        
      ArrayList<String> extrato = new ArrayList<String>();// SALVA AS TRANSAÇÕES
        
        do {//LOOP INFINITO
        
        System.out.println("=========================");
        System.out.println("BEM VINDO AO BANCO FACENS");
        System.out.println("=========================");
        
        System.out.println("Para efetuar o login siga os proximos passos");
        
        System.out.printf("Digite seu cpf:");
        cpf=ler.next();
          
        if ("123.456.789-00".equals(cpf) ) {
            System.out.println("CPF VALIDADO");
            System.out.printf("Digite sua senha:");
            senha=ler.next();
           if ("01020304".equals(senha)){
                System.out.println("Senha VALIDADA");
                System.out.println("Bem vindo senhor FULANO");
                do { 
                    System.out.println("O QUE DESEJA REALIZAR\n"
                            + "[1] SALDO\n"
                            + "[2] DEPOSITO\n"
                            + "[3] SAQUE\n"
                            + "[4] TRANSFERENCIA\n"
                            + "[5] EXTRATO\n"
                            + "[0] SAIR\n");

                    System.out.println("DIGITE A OPÇÃO DESEJADA:");
                    op=ler.nextInt();
                    switch (op) {
                        case 1:
                            System.out.printf("SEU SALDO ATUAL È DE R$ %.2f\n", saldo);
                            break;
                        case 2:
                            System.out.println("DIGITE O VALOR QUE DESEJA DEPOSITAR\n");
                            deposito=ler.nextDouble();
                            saldo=deposito+saldo;
                            System.out.printf("SEU SALDO ATUAL AGORA È DE R$ %.2f\n", saldo);
                            extrato.add("Você depositou R$ "+deposito);
                            break;
                        case 3:
                            System.out.printf("DIGITE QUANTO DESEJA SACAR :");
                            saque=ler.nextDouble();
                            
                            if (saque<saldo) {
                                saldo=saldo-saque;
                                System.out.printf("SEU SALDO ATUAL AGORA È DE R$ %.2f\n", saldo);
                                extrato.add("Você sacou R$ "+saque);
                            }else{
                                System.out.printf("SALDO INSUFICENTE PARA ESTE SAQUE.\n");
                            }
                            break;
                        case 4:
                            do {//CONTA
                                System.out.printf("Digite o numero da conta: ");
                                conta=ler.nextLine();
                                conta=ler.nextLine();
                                if ("12345678-9".equals(conta)) {
                                    proximo=1;
                                }else{
                                    System.out.println("Informação invalida");
                                }
                            } while (proximo==0);
                            proximo=0;
                            do {//AGENCIA
                                System.out.printf("Digte o numero da agencia: ");
                                agencia=ler.nextLine();
                                if ("1234".equals(agencia)) {
                                    proximo=1;
                                }else{
                                    System.out.println("Informação invalida");
                                }
                            } while (proximo==0);
                            proximo=0;
                            do {
                                System.out.printf("Digite o nome do banco: ");
                                banco=ler.nextLine();
                                if (bancos.contains(banco)) {
                                    System.out.printf("Digite o valor de transferencia: ");
                                    transferencia=ler.nextInt();
                                    if (transferencia>saldo) {
                                        System.out.println("SALDO INSUFICIENTE");
                                        proximo=1;
                                    }else{
                                        System.out.println("TRANSFERENCIA COMPLETA");
                                        saldo=saldo-transferencia;
                                        System.out.printf("Seu saldo atual agora é de R$ %.2f\n", saldo);
                                        extrato.add("Você transferiu R$ "+transferencia);
                                        
                                        proximo=1;
                                    }
                                }
                            } while (proximo==0);
                            
                            

                            break;
                        case 5://EXTRATO
                                System.out.printf("EXTRATO\n");
                            for (String extratos:extrato) {//For each
                                System.out.println(extratos);
                            }
                            break;
                        case 0:
                            saida=false;
                            break;
                        default :
                            System.out.println("NUMERO INVALIDO");
                            break;
                    }
                    
                } while (saida==true);
                
            }else{
                System.out.println("SENHA INVALIDA");
            }
        }else{
            System.out.println("Acesso negado");
          }
        } while (principal==0);
    }
    
}
