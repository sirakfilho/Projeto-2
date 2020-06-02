# Métodos Avançados de Programação

## UNIESP Faculdades

### Professora

* Drª Alana Morais ([alanamm.prof@gmail.com](mailto:alanamm.prof@gmail.com))

### Aluno

* Sirak Leite da Silva Filho ([sirakiesp@gmail.com](mailto:sirakiesp@gmail.com))


### Padrão Comportamental: 

COMMAND


## Padrão COMMAND

### Problema: 

- Encapsular uma solicitação como um objeto, permitindo parametrizar clientes com diferentes solicitações, enfileirar ou fazer registro (log) de solicitações e suportar operações que podem ser desfeitas (undo).


### Solução: 

- Especificar, enfileirar e executar solicitações em tempos diferentes;
- Registar e eventualmente desfazer operações realizadas;
- Parametrizar as ações a serem executadas pelos objetos;
- Estruturar um sistema com base em operações de alto nível construídas sobre operações básicas.


### Consequências: 

- Desacopla o objeto que invoca a operação daquele que sabe como executá-lo
- São objetos que podem ser manipulados e estendidos como qualquer outro objeto
- É possível juntar comandos formando um comando composto podendo-se usar o padrão COMPOSITE.
- É fácil acrescentar novos COMMANDS  porque não é necessário mudar classes existentes


### Exemplo: 

IMPLEMENTANDO INTERFACE COMMAND
public interface Command {

	public void execute();

}

IMPLEMENTANDO O COMMAND
public class LightOnCommand implements Command { 

	Light light;

	public LightOnCommand(Light light) {
		this.light = light;
	}

public void execute() {
		light.on();
	}
}

IMPLEMENTANDO CONTROLE REMOTO QUE INVOCARÁ O COMMAND
public class ControleRemoto { 

	Command slot;
  
	public ControleRemoto() {
	}

public void setCommand(Command command) {
		slot = command;
	}
  
public void botaoPressionado() {
		slot.execute();
	}

}


