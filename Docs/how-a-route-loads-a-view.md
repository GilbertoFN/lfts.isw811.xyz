[<Volver](README.pdf)

# Episodio 5 - How a Route Loads a View

Se enseña como cargar las rutas de las vistas.

Primero con un hola mundo:

    Route::get('/', function(){
        return 'Hello World';
    });

Segundo con un Json:

    Route::get('/', function(){
        return ['foo' => 'bar'];
    });