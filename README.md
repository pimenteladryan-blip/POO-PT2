#Atividade 1

***TypeScript***
```typescript

class Pessoa {
    nome: string;

    constructor(nome: string) {
        this.nome = nome;
    }
}

class Aluno extends Pessoa {
    estudar(): string {
        return `${this.nome} está estudando.`;
    }
}

class Professor extends Pessoa {
    lecionar(): string {
        return `O professor ${this.nome} está dando aula.`;
    }
}

const aluno = new Aluno("Carlos");
const professor = new Professor("Ana");
console.log(aluno.estudar());
console.log(professor.lecionar());

```
#Atividade 2

***TypeScript***
```typescript
class ContaBancaria {
    protected saldo: number;

    constructor(saldoInicial: number = 0) {
        this.saldo = saldoInicial;
    }

    depositar(valor: number): void {
        if (valor > 0) {
            this.saldo += valor;
        }
    }

    sacar(valor: number): void {
        if (valor > 0 && valor <= this.saldo) {
            this.saldo -= valor;
        }
    }

    consultarSaldo(): number {
        return this.saldo;
    }
}

const conta = new ContaBancaria(1000);
conta.depositar(500);
conta.sacar(200);
console.log(`Saldo atual: R$ ${conta.consultarSaldo().toFixed(2)}`);


```
#Atividade 3

***TypeScript***
```typescript

class Animal {
    emitirSom(): string {
        return "Som genérico de animal";
    }
}

class Cachorro extends Animal {
    emitirSom(): string {
        return "Au Au!";
    }
}

class Gato extends Animal {
    emitirSom(): string {
        return "Miau!";
    }
}

const cachorro = new Cachorro();
const gato = new Gato();
console.log(cachorro.emitirSom());
console.log(gato.emitirSom());

```
#Atividade 4

***TypeScript***
```typescript
abstract class Forma {
    abstract calcularArea(): number;
}

class Retangulo extends Forma {
    largura: number;
    altura: number;

    constructor(largura: number, altura: number) {
        super();
        this.largura = largura;
        this.altura = altura;
    }

    calcularArea(): number {
        return this.largura * this.altura;
    }
}

class Circulo extends Forma {
    raio: number;

    constructor(raio: number) {
        super();
        this.raio = raio;
    }

    calcularArea(): number {
        return Math.PI * Math.pow(this.raio, 2);
    }
}

const retangulo = new Retangulo(5, 4);
const circulo = new Circulo(3);
console.log(`Área Retângulo: ${retangulo.calcularArea()}`);
console.log(`Área Círculo: ${circulo.calcularArea().toFixed(2)}`);

```
#Atividade 5

***TypeScript***
```typescript
abstract class UsuarioSistema {
    abstract obterDados(): string;
}

class Pessoa extends UsuarioSistema {
    nome: string;

    constructor(nome: string) {
        super();
        this.nome = nome;
    }

    obterDados(): string {
        return `Nome: ${this.nome}`;
    }
}

class Aluno extends Pessoa {
    matricula: string;
    private _nota: number = 0;

    constructor(nome: string, matricula: string) {
        super(nome);
        this.matricula = matricula;
    }

    get nota(): number {
        return this._nota;
    }

    set nota(valor: number) {
        if (valor >= 0 && valor <= 10) {
            this._nota = valor;
        }
    }

    obterDados(): string {
        return `[ALUNO] Matrícula: ${this.matricula} | Nome: ${this.nome} | Nota: ${this._nota}`;
    }
}

class Professor extends Pessoa {
    idProfessor: string;
    private _salario: number = 0;

    constructor(nome: string, idProfessor: string) {
        super(nome);
        this.idProfessor = idProfessor;
    }

    get salario(): number {
        return this._salario;
    }

    set salario(valor: number) {
        if (valor > 0) {
            this._salario = valor;
        }
    }

    obterDados(): string {
        return `[PROFESSOR] ID: ${this.idProfessor} | Nome: ${this.nome} | Salário: R$ ${this._salario.toFixed(2)}`;
    }
}

const alunoP = new Aluno("Lucas Ribeiro", "20261001");
const profP = new Professor("Dr. Rodrigo", "9945");
alunoP.nota = 8.5;
profP.salario = 4500;

console.log(alunoP.obterDados());
console.log(profP.obterDados());
