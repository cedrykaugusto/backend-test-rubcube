# Quake log parser

## Task 1

Construa um parser para o arquivo de log games.log.

O arquivo games.log é gerado pelo servidor de quake 3 arena. Ele registra todas as informações dos jogos, quando um jogo começa, quando termina, quem matou quem, quem morreu pq caiu no vazio, quem morreu machucado, entre outros.

O parser deve ser capaz de ler o arquivo, agrupar os dados de cada jogo, e em cada jogo deve coletar as informações de morte.

### Exemplo

  	21:42 Kill: 1022 2 22: <world> killed Isgalamido by MOD_TRIGGER_HURT
  
  O player "Isgalamido" morreu pois estava ferido e caiu de uma altura que o matou.

  	2:22 Kill: 3 2 10: Isgalamido killed Dono da Bola by MOD_RAILGUN
  
  O player "Isgalamido" matou o player Dono da Bola usando a arma Railgun.
  
Para cada jogo o parser deve gerar algo como:

    game_1: {
	    total_kills: 45;
	    players: ["Dono da bola", "Isgalamido", "Zeh"]
	    kills: {
	      "Dono da bola": 5,
	      "Isgalamido": 18,
	      "Zeh": 20
	    }
	  }

### Observações

1. Quando o `<world>` mata o player ele perde -1 kill.
2. `<world>` não é um player e não deve aparecer na lista de players e nem no dicionário de kills.
3. `total_kills` são os kills dos games, isso inclui mortes do `<world>`.

## Task 2

Após construir o parser construa um script que imprima um relatório de cada jogo contento
- Quantidade de mortes por causa
- Quantidade de mortes pelo `<world>`
- O ranking geral de kills por jogador.

Exemplo:

	"game-1": {
		kills_by_means: {
			"MOD_SHOTGUN": 10,
			"MOD_RAILGUN": 2,
			"MOD_GAUNTLET": 1,
			"XXXX": N
		},
		general_ranking: {
			"Dono da bola": 15,
	      "Isgalamido": 10,
	      "Zeh": 5
		},
		killed_by_world: {
			"Dono da bola": 5,
	      "Isgalamido": 2,
	      "Zeh": 0
		}
	}

## Task 3

Construir uma API em Node.JS Linguagem que busque o resultado do Game por ID e retorne a saída exemplo da `<Task 3>`. **Envie junto com o teste uma collection do postman para testes.**


Causas de morte (retirado do [código fonte](https://github.com/id-Software/Quake-III-Arena/blob/master/code/game/bg_public.h))

	// means of death
	typedef enum {
		MOD_UNKNOWN,
		MOD_SHOTGUN,
		MOD_GAUNTLET,
		MOD_MACHINEGUN,
		MOD_GRENADE,
		MOD_GRENADE_SPLASH,
		MOD_ROCKET,
		MOD_ROCKET_SPLASH,
		MOD_PLASMA,
		MOD_PLASMA_SPLASH,
		MOD_RAILGUN,
		MOD_LIGHTNING,
		MOD_BFG,
		MOD_BFG_SPLASH,
		MOD_WATER,
		MOD_SLIME,
		MOD_LAVA,
		MOD_CRUSH,
		MOD_TELEFRAG,
		MOD_FALLING,
		MOD_SUICIDE,
		MOD_TARGET_LASER,
		MOD_TRIGGER_HURT,
	#ifdef MISSIONPACK
		MOD_NAIL,
		MOD_CHAINGUN,
		MOD_PROXIMITY_MINE,
		MOD_KAMIKAZE,
		MOD_JUICED,
	#endif
		MOD_GRAPPLE
	} meansOfDeath_t;



# Requisitos

1. Desenvolva o teste utilizando Node.JS com framework de sua preferência
2. Crie um projeto no github, use git e tente fazer commits específicos e bem descritos.
3. Faça o README do projeto explicando como fazer o setup, uma explicação da solução proposta, o mínimo de documentação para outro desenvolvedor entender seu código
4. Siga o que considera boas práticas de programação, coisas que um bom desenvolvedor olhe no seu código e não ache "feio" ou "ruim".
5. Após concluir o teste nos envie o link do projeto para o email de contato

HAVE FUN :)
