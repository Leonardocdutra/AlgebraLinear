# AlgebraLinear
#include <iostream>
#include <stack>
#include <string>

using namespace std;

// Função para calcular o resultado da expressão pós-fixada
double calcularExpressaoPosfixada(string expressao) {
    stack<double> pilha;

    for (char& c : expressao) {
        if (isdigit(c)) {
            pilha.push(c - '0'); // Converter caractere numérico para número
        } else {
            double num2 = pilha.top();
            pilha.pop();
            double num1 = pilha.top();
            pilha.pop();

            switch (c) {
                case '+':
                    pilha.push(num1 + num2);
                    break;
                case '-':
                    pilha.push(num1 - num2);
                    break;
                case '*':
                    pilha.push(num1 * num2);
                    break;
                case '/':
                    pilha.push(num1 / num2);
                    break;
            }
        }
    }

    return pilha.top();
}

int main() {
    string expressao = "53+2*";
    cout << "Resultado da expressao 53+2*: " << calcularExpressaoPosfixada(expressao) << endl;

    return 0;
}
