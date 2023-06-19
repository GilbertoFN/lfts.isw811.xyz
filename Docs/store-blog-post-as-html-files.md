[<Volver](README.pdf)

# Episodio 8 - Store a Blog Post as HTML Files

Nos enseñan a almacenar distinta información en archivos html distintos para después cargarlos en una misma vista.

Utilizan una ruta con parámetros para escoger cual archivo mostrar:

    Route::get('posts/{post}', function ($slug) {
        $path = __DIR__ . "/../resources/post/{$slug}.html";

        if (! file_exists($path)) {
            return redirect('/');
        }

        $post = file_get_contents($path);

        return view('post, ['post' => $post]);
    });