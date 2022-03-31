# Sobrecarga

## Sobrecarga de metodos
```c#
public static int Sumar(int value1, int value2)
    {
            return Sumar(value1 , value2,0);
    }
public static int Sumar(int value1, int value2, int value3)
    {
            return value1 + value2+ value3;
    }

```
### Sobrecarga de constructores
```c#
public class Tiempo
    {
        //Sobrecarga de Constructores
        public int hora;
        public int minutos;
        public int segundos;
        public Tiempo(int hora,int minutos,int segundos)
        {
            this.hora = hora;
            this.minutos = minutos; 
            this.segundos = segundos;
        }
        //Invoca a otro constuctor (:)
        public Tiempo(int hora,int minutos):this(hora,minutos,1)
        {

        }
        public Tiempo(int hora) : this(hora,1)
        {
            
        }
```
* Ejemplo en main 
```c#
Tiempo tiempo4 = new Tiempo(21, 20, 20);
Tiempo tiempo2 = new Tiempo(25, 30);
Tiempo tiempo3 = new Tiempo(21);
```

#### Sobrecarga de operadores
```c#
Tiempo tiempo = new Tiempo(21, 20, 20);
Tiempo tiempo1 = tiempo;
Tiempo tiempo4 = new Tiempo(21, 20, 20);
Console.WriteLine(tiempo==tiempo1);
Console.WriteLine(tiempo==tiempo4);
```
* El  resultado por consola de esta comparacion normalmente arrojaria TRUE para tiempo==tiempo1 y FAlSE para tiempo==tiempo4. Esto ocurre porque el operando == compara dos direcciones de memoria
 
    * Al sobrecargar el operando queremos que solo nos compare los 2 valores por el valor de sus atributos
```c#
//Sobrecarga de operadores 
        public static bool operator == (Tiempo t1,Tiempo t2)
        {
            return t1.hora == t2.hora && t1.minutos == t2.minutos && t1.segundos == t2.segundos;
        }
        public static bool operator !=(Tiempo t1, Tiempo t2)
        {
            return !(t1 == t2);
        }
```
    * Ahora los resultados en consola arrojaran TRUE TRUE.

#### Sobrecarfa de operadores de conversion


* Ejemplo de conversion explicita e implicita 
```c#
 int entero;
float flotante = 5.5f;
//conversion Explicita- se nesecita poner (int)porque puede haber perdida de informacion.
entero = (int)flotante;
//conversion Implicita - Dato chico a un operador mas grande no se especifica nada.
int numero = 0;
float flotante2 = numero;
```
* Sobrecarga implicita 
```c#
//Quiero pasar los valores de mis atributos a segundos 
Tiempo tiempo = new Tiempo(21, 20, 20);
 int segundo = tiempo;
Console.WriteLine(segundo);
``` 
```c#
//Devuelve el valor de los atributos expresados en segundos
public static implicit operator int(Tiempo t)
{
    return (((t.hora * 60) + t.minutos) * 60) + t.segundos * 60;
}
``` 