# Cidades

Tenha no banco de dados do seu projeto Laravel a tabela de cidades brasileiras

### Como usar

Adicione o package

    $ composer require laraerp/cidades

Importe migrations/seeds

    $ php artisan vendor:publish --provider="Laraerp\Providers\CidadesServiceProvider"
    
Execute

    $ php artisan migrate --seed="CidadesSeeder"
    
### Model Laraerp\Cidade

O model `Laraerp\Cidade` já está disponível para uso:

    <?php
    
    namespace Laraerp;
    
    use Illuminate\Database\Eloquent\Model;
    
    class Cidade extends Model{
    
        public $timestamps = false;
    
        protected $fillable = ['nome', 'uf'];
    }
     
### Rotas

As rotas abaixo já estão disponíveis para uso:

    <?php
    
    Route::get('/ufs/', function($uf = null){
        return response()->json(\Laraerp\Cidade::select('uf')->distinct('uf')->orderBy('uf')->get());
    });
    
    Route::get('/cidades/{uf}', function($uf = null){
        return response()->json(\Laraerp\Cidade::where('uf', $uf)->orderBy('nome')->get());
    });