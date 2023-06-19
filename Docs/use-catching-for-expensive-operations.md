[<Volver](README.pdf)

# Episodio 10 - Use Catching for Expensive Operations

Nos enseñan a guardar datos en la memoria caché para mejorar el rendimiento.

    Route::get('posts/{post}', function ($slug) {
        if (! file_exists($path = __DIR__ . "/../resources/post/{$slug}.html")) {
            return redirect('/');
        }

        $post = cache()->remember("post.{$slug}", 1200, fn() => file_get_contents($path));

        return view('post, ['post' => $post]);
    })->where('post', '[A-z_\-]+');