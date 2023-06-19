[<Volver](README.pdf)

# Episodio 13 - Collection Sorting and Caching Refresher

Nos enseñan a ordenar los posts y a clasificarlos dependiendo de las variables que se necesiten, en este caso se usa la fecha de publicación de cada post:

En el modelo **Post** se agrega lo siguiente a la función **all()**:

    return cache()->rememberForever('posts.all', function(){

        return collect(File::files(resource_path('posts')))
            ->map(fn($file) => YamlFrontMatter::parseFile($file));
            ->map(fn($document) => new Post(
                $document->title,
                $document->excerpt,
                $document->date,
                $document->body(),
                $document->slug
            ));

        ->sortBy('date');
    });