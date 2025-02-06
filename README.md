# gerador_senhas
import string
import random

def gerar_senha(tamanho=12):
    """
    Gera uma senha aleatória com letras, números e caracteres especiais.
    :param tamanho: Comprimento da senha (padrão: 12 caracteres)
    :return: Senha gerada
    """
    if tamanho <= 0:
        raise ValueError("O tamanho da senha deve ser maior que zero.")
    
    caracteres = string.ascii_letters + string.digits + string.punctuation
    senha = ''.join(random.choice(caracteres) for _ in range(tamanho))
    return senha

def obter_tamanho():
    """
    Obtém um tamanho válido para a senha inserido pelo usuário.
    """
    while True:
        entrada = input("Digite o tamanho da senha desejada: ")
        if entrada.isdigit():
            tamanho = int(entrada)
            if tamanho > 0:
                return tamanho
        print("Entrada inválida! Digite um número inteiro maior que zero.")

def main():
    """
    Função principal que executa o programa.
    """
    try:
        tamanho = obter_tamanho()
        senha_gerada = gerar_senha(tamanho)
        print(f"Sua senha gerada: {senha_gerada}")
    except ValueError as e:
        print(f"Erro: {e}")

if __name__ == "__main__":
    main()
