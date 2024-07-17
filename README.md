# Como usar java Doc

/**
 * Controlador de API para realizar operações aritméticas simples.
 * 
 * <p>Esta API permite que os usuários realizem operações aritméticas básicas
 * como soma, subtração, multiplicação, divisão e exponenciação.</p>
 * 
 * @author Mateus Elias Vieira
 * @version 1.0
 */
@RestController
@RequestMapping(path = "/api")
public class ApiController {
	
    /**
     * Construtor padrão para ApiController.
     * 
     * <p>Este construtor é utilizado pelo framework Spring para instanciar
     * o controlador e gerenciar suas dependências.</p>
     */
    public ApiController() {
        // TODO Auto-generated constructor stub
    }
    
    /**
     * Realiza uma operação aritmética entre dois valores inteiros.
     * 
     * @param v1 O primeiro valor.
     * @param v2 O segundo valor.
     * @param operation A operação a ser realizada (sum, sub, mult, div, expo).
     * @return A string que descreve a operação e o resultado, encapsulada em um {@link ResponseEntity}.
     * @throws IllegalArgumentException Se a operação especificada for desconhecida.
     */
    @GetMapping(path = "/calc/{v1}/{v2}/{operation}")
    public ResponseEntity<?> getCalc(
    		@PathVariable("v1") int v1, 
    		@PathVariable("v2") int v2, 
    		@PathVariable("operation") String operation) 
    {
        switch (operation) {
            case "sum":
                return new ResponseEntity<>(v1 + " + " + v2 + " = " + (v1 + v2), HttpStatus.OK);
            case "sub":
                return new ResponseEntity<>(v1 + " - " + v2 + " = " + (v1 - v2), HttpStatus.OK);
            case "mult":
                return new ResponseEntity<>(v1 + " x " + v2 + " = " + (v1 * v2), HttpStatus.OK);
            case "div":
                return new ResponseEntity<>(v1 + " / " + v2 + " = " + (v1 / v2), HttpStatus.OK);
            case "expo":
                return new ResponseEntity<>(v1 + " ^ " + v2 + " = " + Math.pow(v1, v2), HttpStatus.OK);
            default:
                throw new IllegalArgumentException("Operação desconhecida: " + operation);
        }
    }
}
