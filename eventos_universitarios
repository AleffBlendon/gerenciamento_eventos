### banco de dados ###
banco_eventos = []
inscricoes = []
### pausa entre as ações ###
def pausar():
    input('Pressione ENTER para continuar...')
### visualizar eventos cadastrados e contagem dos eventos ###
def mostrar_eventos():
    if not banco_eventos:
        print('Não há eventos cadastrados.')
    else:
        contador = 1
        for evento in banco_eventos:
            print(f'{contador} - Nome: {evento["nome"]}, Data: {evento["data"]}, Descrição: {evento["descricao"]}, Vagas restantes: {evento["vagas"]}')
            contador += 1
### incrição em eventos cadastrados ###
def registrar_inscricao():
    if not banco_eventos:
        print('Não há eventos disponíveis para inscrição.')
        return
    mostrar_eventos()
    numero_evento = int(input('Digite o número do evento que deseja se inscrever: '))
    if 1 <= numero_evento <= len(banco_eventos):
        evento = banco_eventos[numero_evento - 1]
        if evento["vagas"] > 0:
            nome_aluno = input('Digite seu nome: ')
            evento["vagas"] -= 1
            inscricao = {'evento': evento['nome'], 'aluno': nome_aluno}
            inscricoes.append(inscricao)
            print(f'Inscrição realizada com sucesso para o evento "{evento["nome"]}"!')
        else:
            print('Não há vagas disponíveis para este evento.')
    else:
        print("Número de evento inválido.")
    pausar()
### visualizar inscrições ###
def mostrar_inscricoes():
    if not inscricoes:
        print('Não há inscrições registradas.')
    else:
        print("Histórico de Inscrições:")
        for inscricao in inscricoes:
            print(f'Evento: {inscricao["evento"]}, Aluno: {inscricao["aluno"]}')
    pausar()
### seleções do menu ###
def selecionar_menu(opcao):
    if opcao == '1':  ### adicionar evento ###
        nome = input('Digite o nome do evento: ')
        evento_existente = False
        for evento in banco_eventos:
            if evento['nome'] == nome:
                evento_existente = True ### nao permite duplicar eventos ###
                break
        if evento_existente:
            print(f'O evento "{nome}" já está cadastrado.')
        else:
            data = input('Digite a data do evento: ')
            descricao = input('Digite a descrição do evento: ')
            vagas = int(input('Digite o número de vagas disponíveis: '))
            evento = {'nome': nome, 'data': data, 'descricao': descricao, 'vagas': vagas}
            banco_eventos.append(evento)
            print(f'Evento "{nome}" cadastrado com sucesso!')
    elif opcao == '2':  ### visualizar eventos ###
        mostrar_eventos()
        pausar()
    elif opcao == '3':  ### excluir evento ###
        if not banco_eventos:
            print("Não há eventos para excluir.")
        else:
            mostrar_eventos()
            numero_evento = int(input('Digite o número do evento para excluir: '))
            if 1 <= numero_evento <= len(banco_eventos):
                del banco_eventos[numero_evento - 1]
                print("Evento excluído com sucesso!")
            else:
                print("Número de evento inválido.")
        pausar()
    elif opcao == '4':  ### atualizar evento ###
        if not banco_eventos:
            print("Não há eventos para atualizar.")
        else:
            mostrar_eventos()
            numero_evento = int(input('Digite o número do evento para atualizar: '))
            if 1 <= numero_evento <= len(banco_eventos):
                evento = banco_eventos[numero_evento - 1]
                print('O que você deseja atualizar?')
                print('1 - Nome')
                print('2 - Data')
                print('3 - Descrição')
                print('4 - Vagas')
                opcao_atualizar = input('Escolha uma opção: ')
                if opcao_atualizar == '1':  ### atualizar nome ###
                    novo_nome = input('Digite o novo nome do evento: ')
                    evento['nome'] = novo_nome
                    print(f'Nome atualizado para "{novo_nome}".')
                elif opcao_atualizar == '2':  ### atualizar data ###
                    nova_data = input('Digite a nova data do evento: ')
                    evento['data'] = nova_data
                    print(f'Data atualizada para "{nova_data}".')
                elif opcao_atualizar == '3':  ### atualizar descrição ###
                    nova_descricao = input('Digite a nova descrição do evento: ')
                    evento['descricao'] = nova_descricao
                    print(f'Descrição atualizada para "{nova_descricao}".')
                elif opcao_atualizar == '4':  ### atualizar vagas ###
                    novas_vagas = int(input('Digite o novo número de vagas disponíveis: '))
                    evento['vagas'] = novas_vagas
                    print(f'Número de vagas atualizado para {novas_vagas}.')
                else:
                    print('Opção inválida.')
            else:
                print("Número de evento inválido.")
        pausar()
    elif opcao == '5':  ### registrar inscrição ###
        registrar_inscricao()
    elif opcao == '6':  ### mostrar inscrições ###
        mostrar_inscricoes()
    elif opcao == '0':  ### air do sistema ###
        print('Saindo do sistema...')
        exit(0)
    else:
        print('Opção incorreta, tente novamente!')
### menu principal ###
def exibir_menu():
    print('---> MENU <---')
    print('1 - Adicionar evento')
    print('2 - Visualizar eventos')
    print('3 - Excluir evento')
    print('4 - Atualizar evento')
    print('5 - Registrar inscrição')
    print('6 - Histórico de inscrições')
    print('0 - Sair do sistema')
    opcao = input('Escolha uma opção: ')
    selecionar_menu(opcao)
    if opcao != '0':
        exibir_menu()
### exibição ###
exibir_menu()
