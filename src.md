def imprimir_sala_cine(lista):
    """
    Muestra visualmente la sala de cine.
    """
    letras = 'ABCDEFGHIJK'
    print('='*60)
    print("Cibercinema UdeA (O disponible, X ocupado)".center(60))
    print(' '*4, end='')

    for c in letras:
        print(c, end='    ')
    print()

    for i, fila in enumerate(lista):
        print(letras[i], fila)

    print('='*60)
