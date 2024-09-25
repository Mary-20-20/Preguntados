# Preguntados
  
    #se importa el modulo random
    import random
    #pregunta al usuario el nombre
    nombre = input("Digite su nombre: ")
    print(f"Bienvenido {nombre}\n")
    #lista de las preguntas y opciones de respuestas de GEOGRAFÍA
    preguntas1 = [
    ("¿Cuál es el río más largo del mundo?", 'B', "A) Río Amazonas\nB) Río Nilo\nC) Río Yangtsé\nD) Río Misisipi"),
    ("¿Cuál es la capital de Australia?", 'C', "A) Sídney\nB) Melbourne\nC) Canberra\nD) Perth"),
    ("¿En qué continente se encuentra el desierto del Sahara?", 'C', "A) Asia\nB) América\nC) África\nD) Oceanía"),
    ("¿Cuál es el país más grande del mundo por área?", 'D', "A) Canadá\nB) China\nC) Estados Unidos\nD) Rusia"),
    ("¿Cuál es el país con más habitantes en el mundo?", 'C', "A) India\nB) Estados Unidos\nC) China\nD) Indonesia"),
    ("¿Cuál es la montaña más alta del mundo?", 'B', "A) K2\nB) Monte Everest\nC) Monte Kilimanjaro\nD) Mont Blanc"),
    ("¿Cuál es el océano más grande del mundo?", 'D', "A) Océano Atlántico\nB) Océano Índico\nC) Océano Ártico\nD) Océano Pacífico"),
    ("¿Cuál es el país más pequeño del mundo por área?", 'C', "A) Mónaco\nB) Nauru\nC) Ciudad del Vaticano\nD) San Marino"),
    ("¿En qué país se encuentra la Torre Eiffel?", 'C', "A) Alemania\nB) Italia\nC) Francia\nD) España"),
    ("¿Cuál es el idioma oficial de Brasil?", 'B', "A) Español\nB) Portugués\nC) Inglés\nD) Francés")
    ]
    #lista de las preguntas y opciones de respuestas de ENTRETENIMIENTO
    preguntas2 = [
    ("¿Cuál es el nombre del martillo de Thor en la mitología y el universo Marvel?", "B", "A) Stormbreaker\nB) Mjolnir\nC) Gungnir\nD) Excalibur"),
    ("¿Cuál es el nombre del protagonista de la serie 'Breaking Bad'?", "B", "A) Jesse Pinkman\nB) Walter White \nC) Saul Goodman\nD) Hank Schrader"),
    ("¿En qué año se lanzó la primera película de 'Harry Potter'?", "C", "A) 1999 \nB) 2000 \nC) 2001 \nD) 2002"),
    ("¿Cuál de los siguientes videojuegos es un juego de rol de mundo abierto lanzado en 2017?", "B", "A) The Witcher 3: Wild Hunt \nB) The Legend of Zelda: Breath of the Wild \nC) Dark Souls III \nD) Skyrim"),
    ("¿Quién dirigió la película 'Pulp Fiction'?", "C", "A) Martin Scorsese\nB) Christopher Nolan\nC) Quentin Tarantino\nD) Steven Spielberg"),
    ("¿Qué serie de televisión tiene un personaje llamado Sheldon Cooper?", "B", "A) Friends\nB) The Big Bang Theory\nC) How I Met Your Mother\nD) Parks and Recreation"),
    ("¿Cuál es la película de animación de Pixar que presenta a un ratón que quiere ser chef en París?", "B", "A) Finding Nemo\nB) Ratatouille\nC) Toy Story\nD) Up"),
    ("¿Qué cantante lanzó el álbum 'Thriller' en 1982?", "C", "A) Prince\nB) Madonna\nC) Michael Jackson\nD) David Bowie"),
    ("¿En qué franquicia de películas aparece el personaje de Katniss Everdeen?", "B", "A) Divergente\nB) Los Juegos del Hambre\nC) Crepúsculo\nD) Maze Runner"),
    ("¿Cuál es el nombre del dragón en la serie de libros 'Canción de Hielo y Fuego'?", "D", "A) Smaug\nB) Norbert\nC) Falkor\nD) Drogon")
    ]
    #lista que almacena las categorías 
    categorías = [0,1]
    #contador de respuestas correctas
    respuestas_c = 0
    #función que genera una pregunta de la categoría seleccionada aleatoriamente 
    def hacer_p(preguntas, categoría):
      print(f"la categoría es {categoría}")
      pregunta_azar = random.choice(preguntas)
      pregunta, respuesta, opciones = pregunta_azar
      print(f"{pregunta}\n{opciones}")
      respuesta_u = input("digite su respuesta(si quiere teriminar el juego digite 'salir'): ").upper()
        if respuesta_u == 'SALIR':
          print("has decidio terminar el juego")
          return None, pregunta_azar
        elif respuesta_u == respuesta:
          print(f"\nFELICIDADES, {respuesta} es la respuesa correcta\n")
          return True, pregunta_azar
        else:
          print("\nRepuesta incorrecta\n")
          return False, pregunta_azar
    #bucle para generar categorías aleatorias
    while preguntas1 or preguntas2:
        catelec = random.choice(categorías)
        if catelec == 0:
            respuesta, pregunta_azar = hacer_p(preguntas1, "GEOGRAFÍA")
        if respuesta == None:
            break
        if respuesta:
            respuestas_c += 1
        preguntas1.remove(pregunta_azar)
        
    if catelec == 1:
        respuesta, pregunta_azar = hacer_p(preguntas2, "ENTRETENIMIENTO")
        if respuesta == None:
            break
        if respuesta:
            respuestas_c += 1
        preguntas2.remove(pregunta_azar)

         if not preguntas1 and catelec == 0:
          categorías.remove(0)
        elif not preguntas2 and catelec == 1:
          categorías.remove(1)
        if not categorías:
          print("has respondido todas preguntas")
        break
    #muestra la puntuación del usuario 
    print(f"su puntuación es de {respuestas_c}/20")
