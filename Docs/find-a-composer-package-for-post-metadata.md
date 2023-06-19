[<Volver](README.pdf)

# Episodio 12 - Find a Composer Package for Post Metadata

Nos enseñan a como utilizar metadatos y también como usar composer para poder analizarlos.

Primero se instala lo siguiente:

    composer require spatie/yaml-front-matter

Luego se llama en el archivo de rutas:

    Route::get('/', function () {
        return view('posts, [
            'posts' => Post::all()
        ]);         
    });

La función **all()** tiene lo siguiente:

    public static function all() {
        return collect(File::files(resource_path('posts')))
            ->map(fn($file) => YamlFrontMatter::parseFile($file));
            ->map(fn($document) => new Post(
                $document->title,
                $document->excerpt,
                $document->date,
                $document->body(),
                $document->slug
            ));
    }

La función **find()** se cambia a esto:

    public static function find($slug) {
        return static::all()->firstWhere('slug', $slug);
    }