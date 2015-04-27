# Cidades

Tenha no banco de dados do seu projeto Laravel a tabela de cidades brasileiras

### Como usar

Adicione o package

    $ composer require laraerp/cidades

Importe migrations/seeds

    $ php artisan vendor:publish --provider="Laraerp\Providers\CidadesServiceProvider"
    
Execute

    $ php artisan migrate --seed="CidadesSeeder"

O model `Laraerp\Cidade` já está disponível:

    <?php
    
    namespace Laraerp;
    
    use Illuminate\Database\Eloquent\Model;
    
    class Cidade extends Model{
    
        public $timestamps = false;
    
        protected $fillable = ['nome', 'uf'];
    }