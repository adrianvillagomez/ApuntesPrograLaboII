# Lectura y Escritura de archivos con StremReader y StreamWriter
* main
```c#
///Escribo en mi archivo prueba txt si no esxiste se crea uno.
Archivo.Escribir("Prueba.txt", "Hola Mundo 30", true);
Console.WriteLine("Ya escribi y se me agrego al final de la linea");

Console.WriteLine(Archivo.Leer("Prueba.txt"));
```
* Escritura con StreamWriter
```c#
 public static class Archivo
    {
        static string CrearRutaBase;
        /// <summary>
        /// La clase  Environment.GetFolderPath(Environment.SpecialFolder.Desktop) Nos devuelve la ruta de nuestro escritorio
        /// </summary>
        static Archivo()
        {
            Archivo.CrearRutaBase = Environment.GetFolderPath(Environment.SpecialFolder.Desktop);
        }
        /// <summary>
        /// Escribimos en un texto el contenido pasado por parametro si la ruta no existe se crea uno nuevo si ya existe sobreescribimos.
        /// si quiero pasarle un array solo tengo q modifica el contenido adentro del using y hacerle un for each.
        /// </summary>
        /// <param name="ruta">Se especifica la ruta</param>
        /// <param name="contenido"></param>
        /// <param name="append">True para agregar el elemento al final de la linea</param>
        /// <returns></returns>
        /// <exception cref="Exception"></exception>
        public static bool Escribir(string ruta, string contenido, bool append)
        {
            string nuevaRuta = $"{Archivo.CrearRutaBase}\\{ruta}";//Añadimos nuestra ruta de ecritorio a la ruta del parametro de la funcion y se crea ese archivo de texto.

            try
            {
                using (StreamWriter stremWriter = new StreamWriter(nuevaRuta, append))
                {
                    stremWriter.WriteLine(contenido);
                }
            }
            catch (Exception ex)
            {
                throw new Exception($"Error al escribir el archivo{ex.Message}", ex);
            }
            return true;
        }
    }

```

* si la ruta no es especifica la guarda en el proyecto /bin/debug/net5

* Lectura con StreamReader

* Leer archivos
```c#
        /// <summary>
        /// Lee un archivo en una ruta especifica
        /// </summary>
        /// <param name="ruta"></param>
        /// <returns></returns>
        /// <exception cref="ArchivoException"></exception>
        public static string Leer(string ruta)
        {
            string retorno = String.Empty;
            try
            {
                using (StreamReader streamReader = new StreamReader($"{Archivo.CrearRutaBase}\\{ruta}"))
                {

                    retorno = streamReader.ReadToEnd();
                }
            }
            catch (Exception ex)
            {
                throw new Exception("Error al leer una archivo", ex);
            }

            return retorno;
        }
```
# Lectura y Escritura de archivos con La clase File

* Escritura con File.writeAllText
```c#
        /// <summary>
        /// Escribimos un archivo pero con la Clase File
        /// </summary>
        /// <param name="ruta"></param>
        /// <param name="contenido"></param>
        /// <returns></returns>
        /// <exception cref="Exception"></exception>
        public static bool EscribirConFile(string ruta, string contenido)
        {
            try
            {
                string nuevaRuta = $"{Archivo.CrearRutaBase}\\{ruta}";
                File.AppendAllText(nuevaRuta, contenido + "\n");

            }
            catch (Exception ex)
            {
                throw new Exception("Error al escribir una archivo", ex);
            }
            return true;
        }
```

* Lectura con File.ReadAllText y con validacion si la ruta no existe 

```c#
       /// <summary>
        /// leo un archivo de texto y si no existe la ruta especificada creo una nueva
        /// </summary>
        /// <param name="ruta"></param>
        /// <returns></returns>
        /// <exception cref="Exception"></exception>
        public static string LeerConFile(string ruta)
        {
            string retorno = String.Empty;
            string nuevaRuta = $"{Archivo.CrearRutaBase}\\{ruta}";
            try
            {
                if (!File.Exists(nuevaRuta))
                {
                    // Crea un nuevo archivo para leer
                    string textoCreado = "Hello and Welcome\n";
                    File.WriteAllText(nuevaRuta, textoCreado);
                }
                retorno =File.ReadAllText(nuevaRuta);
            }
            catch (Exception ex)
            {
                throw new Exception("Error al leer una archivo", ex);
            }
            return retorno;
        }  
```
* Main
```c#
Archivo.EscribirConFile("Prueba.txt", "Hola mundo 3234");
Console.WriteLine("Ya escribi y se me agrego al final de la linea");


Console.WriteLine(Archivo.LeerConFile("Pruebas.txt"));
```