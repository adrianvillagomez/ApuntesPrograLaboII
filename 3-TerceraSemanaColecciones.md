# Colecciones Genericas
* **Ejemplo de array Bimendisional**

     * INdexadas = acceder al elemento atravez de un indice
```c#
#region Array Unidimensional
//Declaracion del array
string [] nombres = new string [4];
nombres [0] = "Ale";
nombres [1] = "Diego";
nombres [3] = "Pepe";
int [] edades = { 12, 45, 20, 50 };
Console.WriteLine($"Longitud del array {nombres.Length}");
for (int i = 0; i < nombres.Length; i++)
{
    if (nombres[i] is not null)
    {
        Console.WriteLine(nombres[i]);
    }
}
Console.WriteLine("Muestro con foreach");
foreach (string nombre in nombres)
{
​
        Console.WriteLine(nombre);
      
}
​
​
int indice = Array.IndexOf(nombres, "Pepe");//Me devuelve el indice donde se encuentra pepe.
​
 Array.Resize(ref nombres, 10);
​
nombres [8] = "Fede";
​
foreach (string item in nombres)
{
    Console.WriteLine(item);
}
#endregion
```
* **Ejemplo array Bimendisionales**
```c#
string [,] personas = new string [3, 2];
​
personas [0, 0] = "Ale";
personas [0, 1] = "123456";
personas [1, 0] = "diego";
personas [1, 1] = "456789";
​
int [,] numeros = { { 1, 2 },{ 3, 4 } }; 
​
Console.WriteLine($"Cantidad de dimensiones {personas.Rank}");
​
Console.WriteLine($"Length {personas.Length}");
​
for (int i = 0; i < personas.GetLength(0); i++)
{
    Console.WriteLine($"Nombre {personas[i,0]} DNI: {personas[i,1]}");
}
​
Console.ReadKey();
```

# **Listas**
* Agregar **using System.Collections.Generic**

 * Indexada por [1][2]..
```c#
#region List

List<string> listaDeNombres = new List<string>();
//Add para agregar elementos a mi lista
listaDeNombres.Add("Romeo");
listaDeNombres.Add("Julieta");
listaDeNombres.Add("Arturo");
listaDeNombres.Add("Pepe");

Console.WriteLine($"Tamaño de la lista { listaDeNombres.Count}");

listaDeNombres.Insert(1, "Ale");//Indice-Elemento que quiere agregar

listaDeNombres [3] = "Diego";//harcode Indice 3

foreach (string item in listaDeNombres)
{
    Console.WriteLine(item);
}

listaDeNombres.Remove("Julieta");

Console.WriteLine("Lista depues de borrar");

int index = listaDeNombres.IndexOf("Ale");//Devuelve el indice del parametro

listaDeNombres.RemoveAt(index);//Elimina con un parametro numerico

foreach (string item in listaDeNombres)
{
    Console.WriteLine(item);
}
#endregion
```
# **Diccionarios**
* Usar **using System.Linq**

    * Indexada por la key
```c#
#region Diccionario
            //<Tkey,TValue>
Dictionary<string, int> agenda = new Dictionary<string, int>();
//Tkey es unica y no se puede repetir Tvalue si.
agenda.Add("Ale Bongio", 12345665);
agenda.Add("Diego P", 456138);
agenda.Add("Esteban P", 456138);



Console.WriteLine("Valor maximo");
Console.WriteLine(agenda.Values.Max());


Console.WriteLine("--------------------");
Console.WriteLine("recorro solo la key");
foreach (string nombre in agenda.Keys)
{
    Console.WriteLine(nombre);
}


Console.WriteLine("recorro solo el value");
foreach (int numero in agenda.Values)
{
    Console.WriteLine(numero);
}

Console.WriteLine("Diccionario completo");
foreach (KeyValuePair<string,int> contacto in agenda)
{
    Console.WriteLine($"La clave es: {contacto.Key} y su valor es: {contacto.Value}");
}

if (agenda.ContainsKey("Ale Bongio"))
{
    Console.WriteLine("Contiene Ale Bongio");
}

if (agenda.ContainsValue(1))
{

}
else
{
    Console.WriteLine("No contiene el valor");
}

Console.WriteLine(agenda["Ale Bongio"]);

#endregion
```
# **Cola**
* Primero en llegar primero en irse FIFO
* No son orndenables

* No estan indexadas
```c#
#region Cola
Queue<string> colaDeAtencion = new Queue<string>();

//Agregar elemento al final
colaDeAtencion.Enqueue("Juan Perez");
colaDeAtencion.Enqueue("Fede Davila");
colaDeAtencion.Enqueue("Mauricio Davila");

foreach (string cliente in colaDeAtencion)
{
    Console.WriteLine(cliente);
}

Console.WriteLine("-----------------------");
Console.WriteLine("Elimino un elemento");

Console.WriteLine("Elimino a:");
Console.WriteLine(colaDeAtencion.Dequeue());
Console.WriteLine("-----------------------");
foreach (string cliente in colaDeAtencion)
{
    Console.WriteLine(cliente);
}

Console.WriteLine("-----------");

Console.WriteLine("Proximo por ser atendido");

Console.WriteLine(colaDeAtencion.Peek());

Console.WriteLine("lista de espera");

foreach (string cliente in colaDeAtencion)
{
    Console.WriteLine(cliente);
}

Console.WriteLine($"Cantidad de clientes en espera {colaDeAtencion.Count}");
Console.ReadKey();
```
# **Pila**
* Primero en llegar ultimo en irse .Analogia de platos al lavar. LIFO
*  No son orndenables

* No estan indexadas
```c#
#region Pila
Stack<char> letras = new Stack<char>();

letras.Push('H');
letras.Push('O');
letras.Push('L');
letras.Push('A');

foreach (char c in letras)
{
    Console.WriteLine(c);
}

Console.WriteLine("----Devuelve el siguiente sin eliminar -----");

Console.WriteLine(letras.Peek());

Console.WriteLine("--------------");
foreach (char c in letras)
{
    Console.WriteLine(c);
}

Console.WriteLine("-------elimino el elemento LIFO----");

Console.WriteLine(letras.Pop());

Console.WriteLine("----------------------");

foreach (char c in letras)
{
    Console.WriteLine(c);
}
#endregion
```
* **Sorted list**
```c#
#region SortedList
SortedList<string, string> profesores = new SortedList<string, string>();
profesores.Add("Ale", "Programacion II");
profesores.Add("Villegas", "Programacion I");
profesores.Add("Baus", "Labo IV");

foreach (KeyValuePair<string, string> prof in profesores)
{
    Console.WriteLine($"Profesor: {prof.Key} Materia: {prof.Value}");
}
#endregion
```
## FUNCION CRITIREO PARA ORDERNAR DE FORMA ASCENDENTE
```c#
 public static int OrdenDescendente(int n1, int n2)
        {
            return n2 - n1;
        }
```
