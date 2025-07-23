# provaUC3
me passa, por favor
algoritmo "Compras_AFSS"

var
    i, qtdCarros, qtdCompras, escolha : inteiro

    // Vetor com até 50 carros cadastrados
    carros : vetor[1..50] de registro
        modelo : caractere
        ano : inteiro
        preco : real
        estoque : inteiro
    fimregistro

    // Armazena os índices dos carros comprados
    compras : vetor[1..50] de inteiro

inicio
    escreval("=== CADASTRO DE CARROS ===")

    repita
        escreva("Quantos carros deseja cadastrar (máx 50)? ")
        leia(qtdCarros)
    ate qtdCarros >= 1 e qtdCarros <= 50

    para i de 1 ate qtdCarros faca
        escreval()
        escreval("Carro ", i)
        escreva("Modelo: ")
        leia(carros[i].modelo)

        repita
            escreva("Ano (>= 1990): ")
            leia(carros[i].ano)
        ate carros[i].ano >= 1990

        repita
            escreva("Preço (mínimo R$10.000): ")
            leia(carros[i].preco)
        ate carros[i].preco >= 10000

        escreva("Estoque disponível: ")
        leia(carros[i].estoque)
    fimpara

    escreval()
    escreval("=== COMPRAS ===")
    qtdCompras <- 0

    enquanto verdadeiro faca
        escreval()
        escreval("Escolha o número do carro que deseja comprar:")
        para i de 1 ate qtdCarros faca
            escreval(i, " - ", carros[i].modelo, " | Ano: ", carros[i].ano, " | R$ ", carros[i].preco:0:2, " | Estoque: ", carros[i].estoque)
        fimpara

        escreval("Digite 0 para encerrar a compra.")
        escreva("Escolha: ")
        leia(escolha)

        se escolha = 0 entao
            pare
        fimse

        se escolha >= 1 e escolha <= qtdCarros entao
            se carros[escolha].estoque > 0 entao
                qtdCompras <- qtdCompras + 1
                compras[qtdCompras] <- escolha
                carros[escolha].estoque <- carros[escolha].estoque - 1
                escreval("Carro adicionado à compra.")
            senao
                escreval("Este carro está esgotado.")
            fimse
        senao
            escreval("Escolha inválida.")
        fimse
    fimenquanto

    // Exibir os carros comprados
    escreval()
    escreval("=== RELATÓRIO DE COMPRAS ===")
    para i de 1 ate qtdCompras faca
        escreval("Carro ", i, ": ", carros[compras[i]].modelo, " | R$ ", carros[compras[i]].preco:0:2)
    fimpara

    escreval("Quantidade de carros comprados: ", qtdCompras)
fimalgoritmo






algoritmo "CadastroCliente_AFSS"
// Disciplina   : [Linguagem e Lógica de Programação] 
// Professor   : Antonio Carlos Nicolodi 

var
    nome : caractere
    cpf : caractere
    email : caractere

// Função para validar CPF (11 dígitos numéricos)
funcao logico isValidCPF(texto cpf)
    inteiro i
    logico valido <- verdadeiro

    se comprimento(cpf) <> 11 entao
        retorne falso
    fimse

    para i de 1 ate comprimento(cpf) faca
        se nao (cpf[i] >= '0' e cpf[i] <= '9') entao
            valido <- falso
        fimse
    fimpara

    retorne valido
fimfuncao

// Função para validar email (deve conter @)
funcao logico isValidEmail(texto email)
    inteiro i
    logico temArroba <- falso

    para i de 1 ate comprimento(email) faca
        se email[i] = '@' entao
            temArroba <- verdadeiro
        fimse
    fimpara

    retorne temArroba
fimfuncao

inicio
    escreval("=== CADASTRO DO CLIENTE ===")

    escreva("Nome: ")
    leia(nome)

    repita
        escreva("CPF (11 números): ")
        leia(cpf)
    ate isValidCPF(cpf)

    repita
        escreva("E-mail: ")
        leia(email)
    ate isValidEmail(email)

    escreval()
    escreval("Cliente cadastrado com sucesso!")
    escreval("Nome: ", nome)
    escreval("CPF: ", cpf)
    escreval("E-mail: ", email)
fimalgoritmo



algoritmo "CadastroCarros_AFSS"
// Disciplina   : [Linguagem e Lógica de Programação] 
// Professor   : Antonio Carlos Nicolodi 

var
    i, qtdCarros : inteiro

    carros : vetor[1..50] de registro
        modelo : caractere
        ano : inteiro
        preco : real
        estoque : inteiro
    fimregistro

inicio
    escreval("=== CADASTRO DE CARROS ===")

    repita
        escreva("Quantos carros deseja cadastrar (máx 50)? ")
        leia(qtdCarros)
    ate qtdCarros >= 1 e qtdCarros <= 50

    para i de 1 ate qtdCarros faca
        escreval()
        escreval("Carro ", i)

        escreva("Modelo: ")
        leia(carros[i].modelo)

        repita
            escreva("Ano (>= 1990): ")
            leia(carros[i].ano)
        ate carros[i].ano >= 1990

        repita
            escreva("Preço (>= R$10.000): ")
            leia(carros[i].preco)
        ate carros[i].preco >= 10000

        escreva("Estoque: ")
        leia(carros[i].estoque)
    fimpara

    escreval()
    escreval("Carros cadastrados com sucesso:")
    para i de 1 ate qtdCarros faca
        escreval("Modelo: ", carros[i].modelo)
        escreval("Ano: ", carros[i].ano)
        escreval("Preço: R$ ", carros[i].preco:0:2)
        escreval("Estoque: ", carros[i].estoque)
        escreval("------------------------")
    fimpara
fimalgoritmo
