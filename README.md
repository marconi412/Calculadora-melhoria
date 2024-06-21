import ipywidgets as widgets
from IPython.display import display

def soma(a, b):
    return a + b

def subtrai(a, b):
    return a - b

def multiplica(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Erro: divisão por zero"
    return a / b

def calcular_operacao(op, n1, n2):
    if op == 'somar':
        resultado.value = f"O resultado da soma é: {soma(n1, n2)}"
    elif op == 'subtrair':
        resultado.value = f"O resultado da subtração é: {subtrai(n1, n2)}"
    elif op == 'multiplicar':
        resultado.value = f"O resultado da multiplicação é: {multiplica(n1, n2)}"
    elif op == 'dividir':
        resultado.value = f"O resultado da divisão é: {divide(n1, n2)}"

operacoes = widgets.Dropdown(
    options=['somar', 'subtrair', 'multiplicar', 'dividir'],
    description='Operação:'
)

n1 = widgets.IntText(
    value=0,
    description='Primeiro número:'
)

n2 = widgets.IntText(
    value=0,
    description='Segundo número:'
)

calcular = widgets.Button(description='Calcular')
resultado = widgets.Label(value='')

def on_calcular_clicked(b):
    calcular_operacao(operacoes.value, n1.value, n2.value)

calcular.on_click(on_calcular_clicked)

display(operacoes, n1, n2, calcular, resultado)
