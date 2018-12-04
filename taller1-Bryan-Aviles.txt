import java.util.List;

public class Main {

	public static void main(String[] args) {

		var rationals = List.of(
		        new Rational(1, 4),
		        new Rational(1, 8),
		        new Rational(3, 4),
		        new Rational(7, 8));
		
		//valores menores a 1/2:
		var medio = new Rational(1, 2);
		rationals.stream().filter(r -> r.isLessThan(medio)).forEach(System.out::println);
		
		//sumar todos los racionales
		var cero = new Rational(0,1);
		var resultado = cero;
		resultado = rationals.stream().reduce(cero,(x,y) -> x.plus(y));
		System.out.println("\nsuma es:"+resultado);
		
		//numero racional mayor
		var mayor = cero;
		mayor = rationals.stream().reduce(cero, (x,y) -> x.getGreater(y));
		System.out.println("\nEl mayor es:"+mayor);
		
		
		//sumar todos los numerados y obtener lo siguiente:
		
		//numero de elementos
		int numelment;
		numelment =  (int)rationals.stream().count();
		System.out.println("\nElementos:"+numelment);
		
		//sumar numeradores
		int resultsum;
		resultsum = rationals.stream().mapToInt(r -> r.getNumerator()).reduce(0, Integer::sum);
		System.out.println("\nSuma numeradores"+resultsum);
		
		//numerador menor
		System.out.println("\nNumerador menor:"+rationals.stream().mapToInt(Rational::getNumerator).min().getAsInt());
		
		//numerador mayor
		System.out.println("\nNumerador mayor:"+rationals.stream().mapToInt(Rational::getNumerator).max().getAsInt());
		
		//Promedio
		System.out.println("\nPromedio es:"+ resultsum / numelment);
		
		
		
		
		

	}

}