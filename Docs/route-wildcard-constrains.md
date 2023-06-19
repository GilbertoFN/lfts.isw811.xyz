[<Volver](README.pdf)

# Episodio 9 - Route Wildcard Constrains

Nos enseñan a agregar restricciones a las rutas.

    Route::get('posts/{post}', function ($slug) {
        $path = __DIR__ . "/../resources/post/{$slug}.html";

        if (! file_exists($path)) {
            return redirect('/');
        }

        $post = file_get_contents($path);

        return view('post, ['post' => $post]);
    })->where('post', '[A-z_\-]+');