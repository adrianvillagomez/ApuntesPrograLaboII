# Crear nueva clase en  c#

* Click derecho en la solucion

* Opcion C# /Windows / Biblioteca de clase
 
    *biblioteca de clase

## Vincular la clase a la aplicacion de consola

* Click derecho en la aplicacion de consola

* Opcion agregar
    
    * Referencia del proyecto

* Check en el nombre de la clase y aceptar

* Agregar el namespace de la clase en la aplicacion de consolo usando USING + nombre del namespace de la clase

### Clases
```c#
using System;
//Proyecto de biblioteca de clase - agrupa funcionalidades
//contiene metodos y atributos
//funcionens == metodos
namespace LogicaNegocio
{
    public class ConversorDeTemperatura// si la clase lleva static todo lo que contenga tiene que ser static
    {
        /// <summary>
        /// convierte temperatura celsius a kelvin
        /// </summary>
        /// 
        private const float ceroAbsoluto = 273.15f;//las constantes son tratadas como static- los privates solo dentro de la misma clase ES UN ATRIBUTO DE LA CLASE
        public static string texto = "hola mundo";
        public static float ConvertirCelsiusAKelvin(float temperaturaEnCelsius)// Esa funcion es un METODO
        {
            return temperaturaEnCelsius + ConversorDeTemperatura.ceroAbsoluto;
        }
        public static float ConvertirKelvinACelsius(float temperaturaEnKelvin)
        {
            return temperaturaEnKelvin - ConversorDeTemperatura.ceroAbsoluto;
        }
    }
}


```
#### STRINGS

```c#
using System;
using System.Text;
namespace String
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string nombre = "Esteban";
            StringBuilder stringBuilder = new StringBuilder();
            stringBuilder.Append("Hola");//Agrega informacion final del stringbuilder actual
            stringBuilder.Append(Environment.NewLine);
            stringBuilder.AppendLine("Estamos en la clase de labo");//Agrega información al final del StringBuilder actual con un salto de línea
            stringBuilder.AppendLine("Curso  2 E");
            stringBuilder.AppendFormat($"Mi nombre es {nombre}");
            //Reemplaza de formato pasado en un string con texto formateado.
            Console.WriteLine(stringBuilder.ToString());
        }
    }
}

```





