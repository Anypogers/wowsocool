# File Structure
```
main
|
+>java
| +>br.com.§NOME§.§NOMEPROGRAMA§
| | +>controller
| | +>model
| | +>repositories
| | +>services
| | +>§NOMEPROGRAMA§Application
|
+>resources
  +>db
  | +>migration
  |   +>V001__§NOME§.sql
  |
  +>application.properties
```
___
# controllers
#### *Java Class*
```
@RestController
@RequestMapping("/__tabela__")
public class __tabela__Controller {

    @Autowired
    private __tabela__Service __tabela__Service;

    @Autowired
    private __Tabela__Repository __tabela__Repository;
    
    @GetMapping
    public List<__Tabela__> listarTodas__Tabela__() {
        return __tabela__Repository.findAll(Sort.by("__campo__").ascending());
    }
    @GetMapping("/{id}")
    public ResponseEntity<__Tabela__> buscarPeloCodigo(@PathVariable int id){
        Optional<__Tabela__> __tabela__ = __tabela__Repository.findById(id);
        return __tabela__.isPresent() ? ResponseEntity.ok(__tabela__.get()) : ResponseEntity.notFound().build();
    }
    public ResponseEntity<__Tabela__> inserir(@RequestBody __Tabela__ __tabela__) {
        __Tabela__ __tabela__Salva = __tabela__Service.salvar(__tabela__);
        return ResponseEntity.status(HttpStatus.CREATED).body(__tabela__Salva);

    }
}
```
___
# model
#### *Java Class*
```
@Entity
@Table(name = "__tabela__")
public class __Tabela__ {
	@Id
	@GeneratedValue(Strategy = GenerationType.IDENTITY)
	private __type__ __campo id__
	
	private __type__ __campo__
	
	private __type__ __campo__
	
	@JsonIgnore
	@OneToMany(mappedBy = "__tabela PAI__")
	private List<__Tabela FILHO__> ^tabela FILHO^Lista = new ArrayList<>();
	
	@ManyToOne
    @JoinColumn(name = "__tabela PAI_____campo ID__")
	private __Tabela PAI__ __tabela PAI__
	
	//GETTERS AND SETTERS
	
	//EQUALS AND HASHCODE
}
```
___
# repositories
#### *Interface*
```
@Repository
public interface __Tabela__Repository extends JpaRepository<__Tabela__, __campo ID__> {

}
```
___
# services
#### *Java Class*
```
@Service
public class __Tabela__Service {

    @Autowired
    private __Tabela__Repository __tabela__Repository;

    public __tabela__ salvar(__Tabela__ __tabela__){
        return __tabela__Repository.save(__tabela__);
    }
}
```
___
# postman
### POST

`localhost:8080/__tabela__`

`Body (Raw --- JSON):`
```
{
    "__campo__": __VALOR__
}
```
### GET
```
localhost:8080/__tabela__
```
```
localhost:8080/__tabela__/__id__
```
___
# properties
```
spring.application.name=orcamento

# Configuracao banco de dados MySQL
spring.jpa.database=MYSQL
spring.datasource.url=jdbc:mysql://localhost:3306/orcamento?createDatabaseIfNotExist=true&useSSL=false&ServerTimezone=America/Sao_Paulo
spring.datasource.username=root
spring.datasource.password=
spring.flyway.baseline-on-migration=true


# Configuracao do Hibernate
spring.jpa.show-sql=true
```
