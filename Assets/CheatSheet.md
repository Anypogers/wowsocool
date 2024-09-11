# README.MD
*(aka, the CheatSheet)*

**NOTE: ANYTHING BETWEEN §THESE CHARACTERS§ MUST BE REPLACED BY SOMETHING ELSE!!!§**
___
# postman
### POST
```text
localhost:8080/§tabela§
Body (Raw --- JSON):
	{
		"§campo§": §VALOR§
	}
```
### GET
#### *Todos*
```text
localhost:8080/§tabela§/todas
```
#### *Unico*
```text
localhost:8080/§tabela§/§id§
```
### DELETE
```text
localhost:8080/§tabela§/§id§
```
___
# File Structure
```text
main
|
+>java
| +>br.com.§NOME§.§NOMEPROGRAMA§
| | +>controller
| | +>model
| | +>repositories
| |   +>§tabela§
| |   +>filters
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
```Java
@RestController
@RequestMapping("/§tabela§")
public class §tabela§Controller {

    @Autowired
    private §tabela§Service §tabela§Service;

    @Autowired
    private §Tabela§Repository §tabela§Repository;
    
    @GetMapping("/todas")
    public List<§Tabela§> listarTodas§Tabela§() {
        return §tabela§Repository.findAll(Sort.by("§campo§").ascending());
    }
    @GetMapping("/{id}")
    public ResponseEntity<§Tabela§> buscarPeloCodigo(@PathVariable int id){
        Optional<§Tabela§> §tabela§ = §tabela§Repository.findById(id);
        return §tabela§.isPresent() ? ResponseEntity.ok(§tabela§.get()) : ResponseEntity.notFound().build();
    }
    @PostMapping()
    public ResponseEntity<§Tabela§> inserir(@RequestBody §Tabela§ §tabela§) {
        §Tabela§ §tabela§Salva = §tabela§Service.salvar(§tabela§);
        return ResponseEntity.status(HttpStatus.CREATED).body(§tabela§Salva);
    }
    @DeleteMapping("/{id}")
    @ResponseStatus(HttpStatus.NO_CONTENT) // Retorna 204 : No Content
    public void remover(@PathVariable §Tipo§ id){
        §tabela§Repository.deleteById(id);
    }
}
```
___
# model
#### *Java Class*
```Java
@Entity
@Table(name = "§tabela§")
public class §Tabela§ {
	@Id
	@GeneratedValue(Strategy = GenerationType.IDENTITY);
	private §type§ §campoID§;
	
	private §type§ §campo§;
	
	private §type§ §campo§;
	
	@JsonIgnore
	@OneToMany(mappedBy = "§tabelaPAI§")
	private List<§TabelaFILHO§> §tabelaFILHO§Lista = new ArrayList<>();;
	
	@ManyToOne
    @JoinColumn(name = "§tabelaPAI§_§campoID§")
	private §TabelaPAI§ §tabelaPAI§;
	
	//GETTERS AND SETTERS
	
	//EQUALS AND HASHCODE
}
```
___
# repositories
#### *Interface*
```Java
@Repository
public interface §Tabela§Repository extends JpaRepository<§Tabela§, §campoID§> {

}
```
___
# repositories . filter
### *Java Class*
```Java
public class §Tabela§Filter{
    
    private §tipo§ §campo§;
    
    // GETTERS AND SETTERS
}
```
___
# repositories . §tabela§
### *Interface*
```Java
public interface §Tabela§RepositoryQuery{
    public Page<§Tabela§> filtrar(§Tabela§Filter §tabela§Filter, Pageable pageable);
}
```
### *Java Class*
```java
public class §Tabela§RepositoryImpl implements §Tabela§RepositoryQuery{
    @PersistenceContext
    private EntityManager manager;
    @Override
    public Page<§Tabela§> filtrar(§Tabela§Filter §tabela§Filter, Pageable pageable) {
        CriteriaBuilder builder = manager.getCriteriaBuilder();
        CriteriaQuery<Categorias> criteria = builder.createQuery(Categorias.class);
        Root<Categorias> root = criteria.from(Categorias.class);
        return null;
    }
}
```
___
# services
#### *Java Class*
```Java
@Service
public class §Tabela§Service {

    @Autowired
    private §Tabela§Repository §tabela§Repository;

    public §tabela§ salvar(§Tabela§ §tabela§){
        return §tabela§Repository.save(§tabela§);
    }
}
```
___
# properties
```properties
spring.application.name=§NOMEPROGRAMA§

# Configuracao banco de dados MySQL
spring.jpa.database=MYSQL
spring.datasource.url=jdbc:mysql://localhost:3306/§NOMEPROGRAMA§?createDatabaseIfNotExist=true&useSSL=false&ServerTimezone=America/Sao_Paulo
spring.datasource.username=root
spring.datasource.password=
spring.flyway.baseline-on-migration=true

# Configuracao do Hibernate
spring.jpa.show-sql=true
```
