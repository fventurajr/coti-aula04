# coti-aula04
Aula 04 do Curso Java Web para o mercado de trabalho da Coti Informática

## Bônus
public Enum TipoFuncao(Double bonus) {

Enum de tipo de função, onde são estabelecidos bônus salariais para estagiários, testadores e programadores.

Map(seleciona partes do todo). Exemplo: Select nome, salario from Pessoa 
Filter(seleciona um elemento específico). Exemplo Select * from pessoa where Pessoa = '...';

stream().filter(a->a.getNome().equals("jose")).map(x->x.getPreco()).reduce(0.,Double::sum);

## Conceito 1
package conceito;

import java.util.ArrayList;
import java.util.List;

//Outher Classe
public class Conceito1 {
	
	  public static List<String> funcoes= new ArrayList<String>();	
	//atributo é variável da classe (global) 
	static {
		  funcoes.add("programador");
		  funcoes.add("arquiteto");
		  funcoes.add("test");
	}
	
	public static void verificaFuncao(Funcionario f) {
		//lista.contains("string")
		if (funcoes.contains(f.getFuncao())) {
			System.out.println("Existe essa Funcao :" + f.getFuncao());
		}else {
			System.out.println("Nao existe essa funcao ...");
			//quando nao existir (false)
			//ou lancar lanca o erro
		}
	}
	
	
	
	
	//Inner Classe
	public class Funcionario{

	private Integer id;
	private String nome;
	private Double salario;
	private String funcao;
	
	
	
	
	public Integer getId() {
		return id;
	}
	public void setId(Integer id) {
		this.id = id;
	}
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}
	public Double getSalario() {
		return salario;
	}
	public void setSalario(Double salario) {
		this.salario = salario;
	}
	public String getFuncao() {
		return funcao;
	}
	public void setFuncao(String funcao) {
		this.funcao = funcao;
	}
	
	}
	

	
	
	
	public static void main(String[] args) {
		Conceito1.Funcionario  f = new Conceito1().new Funcionario();
		  f.setNome("luis");
		  f.setId(100);
		  f.setSalario(2500.);
		  f.setFuncao("test");
	  System.out.println(Conceito1.funcoes);
		  
		  
		  Conceito1.verificaFuncao(f);
		  
		  
	}
  ## Conceito 2
  package conceito2;

public enum EnumTipoFuncao {
	//get somente, Construtor fechado ... (Execucacao  do Construtor)
	//Enum (Construtor (cada execucao do construtor
	//construtor fechado
	
	 PROGRAMADOR( 1500. ),
	 ESTAGIARIO( 500.),
	 TESTE( 900.);
	 
 
	private Double bonus;

	 EnumTipoFuncao( Double bonus) {
	
		this.bonus = bonus;
	}



	public Double getBonus() {
		return bonus;
	}
	
	
	
	
	
}
## Conceito3
package conceito2;
public class Funcionario {
	
	private Integer id;
	private String nome;
   private EnumTipoFuncao tipoFuncao;  //nao é String (ENUM)
	private Double bonus;
	private Double salario;
 
	
	public Funcionario() {
	}

	
	public Funcionario(Integer id, String nome, 
			EnumTipoFuncao  funcao, Double salario) {
		    this.id = id;
		   this.nome = nome;
		   this.tipoFuncao = funcao; 
		   this.bonus = funcao.getBonus();
		 this.salario = salario;
	}


	@Override
	public String toString() {
		return "Funcionario [id=" + id + ", nome=" + nome + ", tipoFuncao=" + tipoFuncao + ", bonus=" + bonus
				+ ", salario=" + salario + "]";
	}


	public Integer getId() {
		return id;
	}
	public void setId(Integer id) {
		this.id = id;
	}
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}
 
	public Double getBonus() {
		return bonus;
	}
	public void setBonus(Double bonus) {
		this.bonus = bonus;
	}
	public Double getSalario() {
		return salario;
	}
	public void setSalario(Double salario) {
		this.salario = salario;
	}


	public EnumTipoFuncao getTipoFuncao() {
		return tipoFuncao;
	}


	public void setTipoFuncao(EnumTipoFuncao tipoFuncao) {
		this.tipoFuncao = tipoFuncao;
	}
	
	
	public static void main(String[] args) {
		
		 Funcionario f = new Funcionario(10, "jose",EnumTipoFuncao.ESTAGIARIO, 900.);
		 f.setSalario(f.getSalario() + f.getBonus());
		 System.out.println(f);
		
	}

	

	
}
## Conceito 4
package conceito3;

public class Carro {
	 
	 private String fabricante;
	 private String nome;
	 private Double preco;
	 
	 public Carro() {
	}
	 
	
	public Carro(String fabricante, String nome, Double preco) {
		super();
		this.fabricante = fabricante;
		this.nome = nome;
		this.preco = preco;
	}


	@Override
	public String toString() {
		return "Carro [fabricante=" + fabricante + ", nome=" + nome + ", preco=" + preco + "]";
	}



	public String getFabricante() {
		return fabricante;
	}
	public void setFabricante(String fabricante) {
		this.fabricante = fabricante;
	}
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}
	public Double getPreco() {
		return preco;
	}
	public void setPreco(Double preco) {
		this.preco = preco;
	}
	 
	 
	 
	 

}

==============

package conceito3;

import java.util.ArrayList;
import java.util.List;

public class Pessoa {
	
	   private String nome;
	   private List<Carro> carros= new  ArrayList<Carro>();
	  //pessoa quer verificar o valor do total de carros
	   private Double total =0.;
	  
	  public Pessoa(String nome, List<Carro> carros) {
		this.nome = nome;
		this.carros = carros;
	}
	  
	  //select * from pessoa;
	  // select nome from pessoa; //map
	  //select * from pessoa whre nome ='UE'; //filtrar pelo nome
	  
	  //map  diferenca map  / filter
	  public void gerarTotal() {
		   this.total = this.carros.stream().
				   map(x->x.getPreco()).reduce(0.,Double::sum);
	  }
	  
	  public Pessoa() {
    }

  
	@Override
	public String toString() {
		return "Pessoa [nome=" + nome + ", carros=" + carros + "]";
	}
	
	public void adicionar(Carro c) {
		  carros.add(c);
	  }
	  


	public String getNome() {
		return nome;
	}

	public void setNome(String nome) {
		this.nome = nome;
	}

	public List<Carro> getCarros() {
		return carros;
	}

	public void setCarros(List<Carro> carros) {
		this.carros = carros;
	}


	public Double getTotal() {
		return total;
	}


	public void setTotal(Double total) {
		this.total = total;
	}

	
	 public static void main(String[] args) {
		   
	Pessoa p = new Pessoa();
	
	  p.setNome("jose");
	p.adicionar(new Carro("fiat","siena",22000.));
	 p.adicionar(new Carro("fiat","uno", 2000.));
	 p.adicionar(new Carro("fiat","147", 1000.));	 
	  p.gerarTotal();
	 System.out.println(p.getNome() + "," + p.getTotal() + "," +
				 p.getCarros());
		 
		 
		 
	}
	  
	  
	
	
	
	
	
	
}
