# Proyecto de organizar música en Spotify
El proyecto consiste de tres partes, la primera es la extracción de datos de Spotify, que son las características de las canciones por playlist, tales como cuanta cantidad de palabras tiene o su volumen promedio. El segundo es la selección del mejor modelo, en donde con ayuda de la función GridSearchCV, no solo para revisar entre los mejores parámetros sino también entre el mejor método. Y finalmente la selección de las playlists a las que pertenece o es más afín.

## Extracción de datos
En esta fase se utilizó tanto la documentación de Spotify (https://developer.spotify.com/), en donde fue necesario crear una aplicación a partir de la página, este nos daba una información para poder acceder a la aplicación y por lo tanto a los datos de Spotify. Esto con ayuda de la librería Spotipy.

Es necesario ingresar las credenciales del usuario las primeras veces que se utiliza una nueva IP, y cada hora es necesario entrar a la página que solicita Spotipy. lo primero que hace es extraer las listas del usuario, y a partir de estas, se sacan los datos de todas las canciones que haya en ella, dejando los nombres de las listas como la etiqueta, después de generar este dataframe, se sacan todas las canciones del usuario, así como los nombres, el artista y el id, y así poder organizarlas.

## Mejor modelo
Para la revisión del mejor modelo, se hizo el típico desarrollo de datos, en utilizando train_test_split, y un escalamiento, Despues empleando una lista, en donde la primera columna son los modelos, la segunda los valores a iterar y la tercera el nombre del modelo, se va buscando cual es el mejor modelo para los datos, y una vez encontrado, se hace otro entrenamiento, con los todos los datos, y se vuelve a evaluar.

## Afinidad
Finalmente, para la afinidad se desarrolló una técnica, para poder encontrar las listas con mayor afinidad por medio de la predicción de probabilidad por etiquetas, la idea en este, es que la suma de las mayores probabilidades, de lo justo para pasar un umbral, por ejemplo si el umbral es del 70% y una lista es del 80% solo se guarde esa lista, pero si las mayores probabilidades son del 35%, 34% y 20%, entonces se guardan esas tres playlists.

Además de la implementación de este sistema, también se evalúa si dentro de las listas sacadas está la que es correcta utilizando el f1_score. Finalmente se entrega un dataframe, que tiene las tres primeras columnas los datos de identificación de las canciones, las siguientes columnas las playlists afines, y después las probabilidades de esas playlists, claramente va a haber el numero de columnas acorde a la canción que más afín sea a varias canciones, y algunos datos quedarán vacíos.
