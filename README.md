## Sintaxes Javascript

Conteúdo da Live do Erick Wendel - Os segredos da Sintaxe Javascript

[https://www.youtube.com/watch?v=DiqLe0nDekA](https://www.youtube.com/watch?v=DiqLe0nDekA)

**Variáveis Privadas -** quando tem # as variáveis de uma classe não acessadas por fora - Encapsulamento - 22/01 - Ainda não está funcionando em todos os browsers e a partir do node 14

    class EntityBase {
        #name
        #gender
        #age
        constructor({ name, age, gender }) {
    
            this.#gender = gender
            this.#age = age
            this.#name = name
        }
    
        get name() {
            const preffix = this.#gender === "male" ? "Mr." : "Ms."
            return `${preffix} ${this.#name}`
        }
    
        get birthYear() {
            if (!this.#age) throw new Error('you must define age first!')
    
            return new Date().getFullYear() - this.#age
        }
    
        set age(value) {
            this.#age = value
        }
    
    }

    module.exports = EntityBase

**static** - static utilizado para acessar uma variável de uma classe sem utilizar o this

**Mokar Valor**

const CURRENT_YEAR = 2021
Date.prototype.getFullYear = () => CURRENT_YEAR

**Formatação de Valor**

    static #defaultFormat = new Intl.NumberFormat("pt-br", { currency: 'BRL', style: "currency" })

**Executar o Projeto** 

    node index.js

**Resultados**

    ----employee----
    employee.name Ms. Mariazinha
    employee.gender undefined
    employee.age undefined
    employee.birthYear 1941
    employee.grossPay R$ 5.000,40
    employee.netPay R$ 4.000,32
        
    ----manager----
    manager.name Mr. Juninho
    manager.gender undefined
    manager.age undefined
    manager.birthYear 2003
    manager.grossPay R$ 5.000,40
    manager.netPay R$ 6.000,32
    manager.bonuses R$ 2.000,00

