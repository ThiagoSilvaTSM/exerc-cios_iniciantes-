python

````
def calcular_media (total_gols,total_partidas):
    if total_partidas > 0:
        media = total_gols/total_partidas
    else:
        media = 0.0
    return media

def classificar_jogador(media_gols):
    if media_gols >= 0.8:
        return 'Super Craque!'
    elif 0.4 <= media_gols < 0.8:
        return 'Bom desempenho'
    else:
        return 'treinar mais '

def gerar_relatorio_jogador(nome,gols,partidas):
    media = calcular_media(gols,partidas)
    status1 = classificar_jogador(media)
    info_jogador = {'nome':nome.title(),
                'gols': gols,
                'partidas': partidas,
                'media_gols':media,
                'classificacao': status1}
    return info_jogador

while True:
    try:
        import datetime
        agora = datetime.datetime.now()
        hora_formatada = agora.strftime('%H:%M:%S')
        if agora.hour < 12:
           manha = input('Bom dia. Deseja cadastrar um novo jogador, [1]Sim/[2]Não: ').strip()
        elif agora.hour < 18:
             manha = input('Boa tarde. Deseja cadastrar um novo jogador, [1]Sim/[2]Não: ').strip()
        else:
             manha = input('Boa noite. Deseja cadastrar um novo jogador, [1]Sim/[2]Não: ').strip()

        if manha == '1':
            try:
                nomej = input('Por favor, digite o nome do jogador: ').title()
                t_jstr = input(f'Por favor , digite o total de gols do jogador {nomej}: ')
                t_j = int(t_jstr)
                t_pstr = input(f'Por favor , digite o total de partidas do jogador {nomej}: ')
                t_p = int(t_pstr)
                relatorio = gerar_relatorio_jogador(nomej,t_j,t_p)
                print(f'Nome: {relatorio['nome']}\n'
                      f'Gols: {relatorio['gols']}\n'
                      f'Partidas: {relatorio['partidas']}\n'
                      f'Média de gols: {relatorio['media_gols']:.2f}\n'
                      f'Classificação: {relatorio['classificacao']}\n')

            except ValueError:
                       print('Por favor , digite um número válido de gols e partidas.')
                       continue
        elif manha =='2':
            print('Análise de jogadores finalizada.\n'
                  'Até a próxima!')
            break
        else:
            print('Opção inválida. Por favor, escolha [1] ou [2]')

    except Exception as e:
        print(f'ocorreu um erro inesperado {e} , por favor tente novamente!!!')
