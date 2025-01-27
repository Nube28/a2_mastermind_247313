data class Evaluacion(val posicionExacta: Int, val posicionIncorrecta: Int)

/**
 * Práctica 1 - MasterMind
 * Nombre: Alejandro Gómez Vega
 * ID: 00000247313
 */
fun main(args: Array<String>) {
    println(evaluar("ABCD", "ABCD") == Evaluacion(4,0))
    println(evaluar("ABCD", "CDBA") == Evaluacion(0,4))
    println(evaluar("ABCD", "ABDC") == Evaluacion(2,2))
    println(evaluar("AABC", "ADFE") == Evaluacion(1,0))
    println(evaluar("AABC", "DEAA") == Evaluacion(0,2))
   
}

fun evaluar(secret: String, guess:String) : Evaluacion{
    var posicionExacta = 0
    var posicionIncorrecta = 0
    
    var guesse = guess
    
    for(i in 0..3){
        for(j in 0..3){
            if (secret[i] == guesse[j] && i == j){
                posicionExacta++
                guesse = reemplazar(guesse, j)
            }
            if(secret[i] == guesse[j] && i != j){
                posicionIncorrecta++
                guesse = reemplazar(guesse, j)
            }
        }
    }
    
    return Evaluacion(posicionExacta, posicionIncorrecta)
    
}

// por que kotlin se complica tanto para reemplazar??? 
// los strings[] deberian tener un metodo que te permita 
// reemplazar sin problemas o hacer un metodo tu
fun reemplazar(arreglo: String, posicion: Int): String{
    var chars = arreglo.toCharArray() 
    chars[posicion] = '0'
    return String(chars)          
}