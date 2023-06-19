[<Volver](README.pdf)

# Episodio 7 - Make a Route and Link to it

Se enseña a crear una ruta y a poder utilizarla.

Esto en las rutas:

    Route::get('post', function(){
        return view('post');
    });

Esto en la vista:

    <h1><a href="/post">My First Post</a></h1>